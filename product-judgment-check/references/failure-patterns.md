# Failure Patterns

Use these patterns to deepen product and domain review before implementation. They are intentionally generic, but they reflect the kinds of failures that show up in real systems once a feature leaves the happy path.

## State predicate drift

Risk:
- One reader treats a row or object as inactive, but another writer, index, or UI action still treats it as active.

Ask:
- What exact predicate means usable?
- Do readers, writers, indexes, list endpoints, and UI actions all use the same predicate?
- If a row is hidden from users, can it still block create, retry, or reinvite?

## Preview check differs from final mutation

Risk:
- A lookup or preview endpoint says an action is available, but the final mutation rejects it.

Ask:
- Which endpoint is only a preview, and which one is the final gate?
- Do both enforce the same authorization, status, expiry, and binding rules?
- Should the preview hide data until the final user binding is proven?

## Multiple paths to the same outcome

Risk:
- One path enforces a business rule while another bypasses it.

Ask:
- List every path that can produce the outcome.
- For each path, compare status, expiry, revoke, ownership, and permission checks.
- Should any legacy path be deprecated, hidden, or explicitly preserved?

## Token possession versus authorization

Risk:
- A hard-to-guess token is treated as permission to see or mutate everything about the target.

Ask:
- Is token possession enough, or must the current user also match an account, email, or role?
- What state can be shown before user binding is proven?
- Are sensitive fields hidden for invalid, mismatched, expired, or already-used tokens?

## Token leakage through operational surfaces

Risk:
- Token-bearing URLs or request bodies appear in logs, browser history, error traces, analytics, or support screenshots.

Ask:
- Is this token equivalent to a bearer credential?
- Does the page make other API requests while the token is still in the browser URL?
- Are query params, POST bodies, headers, and referrer values redacted globally enough?

## External side effect and DB commit ordering

Risk:
- Email, webhook, or API side effects and DB writes disagree, leaving users with an invalid link, duplicate state, or false success.

Ask:
- If the side effect fails after the DB write, what should the user or admin see?
- If the side effect succeeds but the DB write fails, what did the external party receive?
- Is there an outbox, restore path, retry path, or safe no-op?

## Failed cleanup under cancellation

Risk:
- Cleanup or failure markers use the canceled request context, so cleanup fails exactly when the request times out or the client disconnects.

Ask:
- Should cleanup be best effort even after request cancellation?
- Would a skipped cleanup block retries or leave misleading state?
- Is the cleanup idempotent and bounded?

## Concurrency and stale restore

Risk:
- Overlapping requests snapshot old state, then a failed later request restores stale state over a successful earlier request.

Ask:
- What happens with two simultaneous resend, accept, update, or retry requests?
- Can a failed request undo a successful request?
- Does the restore or update guard compare both the expected current value and the original snapshot?

## Legacy data versus new invariants

Risk:
- A new unique index, non-null rule, expiry rule, or status invariant is valid for new rows but false for existing rows.

Ask:
- Can existing production data violate the new invariant?
- Is there a backfill, dedupe, or compatibility path?
- Does deployment order matter for migrations, generated code, or app rollout?

## Route guard blocks the pre-permission user

Risk:
- The route or API needed to gain permission is itself protected by the permission the user does not have yet.

Ask:
- What permissions does the real user have before the feature succeeds?
- Can that user reach the documented route before the feature grants access?
- Are runtime routes, generated clients, and API docs aligned?

## Canonicalization policy hidden as implementation detail

Risk:
- Email, slug, ID, or external-key comparison behavior changes without an explicit product or auth decision.

Ask:
- Is exact match, trimmed match, normalized match, or case-insensitive match intended?
- Does this align with DB constraints, auth provider behavior, and existing records?
- Should tests document the policy instead of merely following the implementation?
