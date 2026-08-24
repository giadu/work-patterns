# Task Template

```md
## overview

<why this task exists>

## goal

<what should be true after this task is completed>

## requirements

### 1. <backend / api / batch / frontend / integration requirement>

- <concrete requirement>
- <concrete requirement>

### 2. <next requirement>

- <concrete requirement>
- <concrete requirement>

## implementation notes

- expected files:
  - <path>
  - <path>
- follow the existing pattern from:
  - <reference path or PR>

## acceptance criteria

- <observable outcome>
- <observable outcome>
- <test expectation>

## optional learning checkpoints

- <which exact existing files or endpoints will you follow as references, and why these instead of other similar ones?>
- <what alternative approach did you consider and reject, and why?>
- <walk through the expected request/response or UI behavior step by step, including failure handling>
- <which tests will you add, and what bug or regression will each one catch?>

## out of scope

- <not part of this task>
- <not part of this task>
```

## Notes

- use `requirements` for real implementation tasks, not review commentary
- if the task spans multiple layers, split by layer instead of mixing backend, frontend, and integration details together
- if a decision is already made, do not present options
- use learning checkpoints only when coaching or guided reasoning is part of the goal
- do not use learning checkpoints to hide non-negotiable requirements
- prefer prompts that force explanation, comparison, and prediction, not generic design text
