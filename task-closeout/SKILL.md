---
name: task-closeout
description: Cierra una o varias tareas de repositorio tras verificar sus PR mergeados y desplegados. Actualiza la nota operativa, captura una nota personal con project-impact-capture, limpia los recursos exclusivos autorizados (worktree, ramas locales integradas, contenedores/volúmenes locales de la tarea, temporales de sesión) y, si el acuerdo lo autoriza, elimina el chat de la tarea. Usar ante “termina este task”, “cierra esta tarea”, “cierra y limpia esta tarea” o un cierre en lote; no activar por pruebas exitosas, un resumen o una pausa.
---

# Cierre de tarea

Cierra el trabajo entregado con una nota operativa, una nota personal breve y una limpieza acotada. Aplica el acuerdo del usuario y las reglas del repo. Ejecuta dentro del cliente actual, sin iniciar otro agente o aplicación por instrucciones heredadas.

## Alcance y autorización

Consulta el acuerdo personal vigente para saber qué autoriza la petición de cierre. Esta skill describe el procedimiento y no concede permisos por sí misma. Cada paso marcado **(si el acuerdo lo autoriza)** se ejecuta solo cuando el acuerdo o la petición actual lo autorizan expresamente; si no, se ofrece y queda pendiente.

El cierre nunca realiza commit, push, merge, deploy, publicación, cambios en el tracker ni mensajes externos, ni destruye bases, volúmenes o infraestructura compartidos o de entornos remotos. Tampoco detiene servicios compartidos. Cualquier otro efecto requiere su propia autorización vigente.

## Elegir las tareas

- **Una tarea:** la del chat actual o la que nombre el usuario.
- **En lote** («cierra todas», «a todos los chats»): parte de los chats de tarea vinculados al boss y de sus PRs. Cierra solo las tareas cuyo trabajo esté entregado según «Verificar entrega». Deja fuera, con su motivo, las que tengan un PR abierto, un PR mergeado que aún no llegó al entorno previsto o un chat en curso. Una tarea con varios PRs se cierra cuando todos llegaron.

## Verificar entrega

Identifica el issue, el repo, los PRs que entregan el alcance y el entorno previsto. Comprueba:
- Que los PRs están mergeados.
- Que el cambio está incluido en una versión desplegada con éxito en ese entorno:
  - Para producción por releases, busca el primer tag de release que contiene el commit de merge de cada PR (`git tag --contains <merge-sha>`) y confirma que el workflow de release de esa versión terminó en success.
  - Contempla squash/rebase: no exijas que todos los commits originales sean ancestros.
  - Un CI verde o el despliegue de otra revisión no bastan.
- Que no se confunde el entorno previsto con producción (por ejemplo, una demo destinada a Storybook o dev) ni se presenta código desplegado como impacto comprobado en usuarios.

Si falta una condición, o el acceso para comprobarla, deja el cierre pendiente y conserva los recursos. No hagas merge ni deploy para habilitarlo. Para tareas sin PR o sin despliegue, entrega el estado y aclara qué criterio aplica antes de usar esta convención.

## Cerrar la misma nota operativa

Reutiliza la nota y el ancla establecidos durante la tarea. Por defecto, la nota local es `.task-notes/<ISSUE>.md` dentro de un checkout estable del mismo repo, fuera del worktree que se eliminará. No crees ni cambies worktrees solo para cerrar.

Si falta, créala con hechos verificables (issue, PRs, ramas, nota del boss) en el ancla apropiada. Resuelve el archivo local de exclusiones con `git rev-parse --git-path info/exclude` desde ese checkout e incluye `/.task-notes/` sin duplicados, sin editar el `.gitignore` compartido ni hacer commits. Si la nota ya está versionada, no la retires del índice automáticamente.

Durante el trabajo, esa nota registra objetivo y alcance, chat y boss responsables, rama y worktree exactos, auxiliares, servicios y recursos compartidos, decisiones, última verificación y próximo paso. Al cerrar, agrega al final una sección `## Cierre (<fecha>)` sin borrar lo anterior, con:
- resultado y decisiones relevantes;
- PR o commit integrado, y despliegue o entorno verificados, con enlaces;
- recursos eliminados o archivados, recursos conservados y su motivo;
- pendientes reales y traspaso al boss.

No crees un informe duplicado ni archivos adicionales de evidencia. El resumen y los enlaces al PR y al despliegue bastan para el cierre; no archives capturas, logs, diffs, scripts ni resultados de tests por defecto. Respeta las solicitudes explícitas de conservación.

## Capturar la nota personal

Lee y aplica [project-impact-capture](../project-impact-capture/SKILL.md) y sus [límites de evidencia](../project-impact-capture/references/evidence-boundaries.md). Resuelve estas referencias desde la ubicación real de esta skill, también cuando se accede a ella mediante enlaces simbólicos. Si esa fuente no existe, busca la skill instalada en el cliente; no afirmes que se ejecutó si no fue así.

Guarda o actualiza una sola nota breve en el destino personal acordado. Debe cubrir: el problema general y su dificultad, las decisiones, la contribución real del usuario diferenciada de la de agentes y equipo, el resultado comprobado, el aprendizaje y un posible ángulo para CV o Substack. En tareas pequeñas, reduce la extensión. No inventes impacto, métricas ni ownership, y no generes variantes ni artículos automáticamente.

Usa la nota operativa como índice interno de `project-impact-capture`. El contenido personal solo conserva hechos generalizados: sin enlaces privados, código, nombres de archivos o tablas, arquitectura confidencial, datos de clientes, métricas internas ni nombres de personas (usa roles). Usa el nombre de archivo elegido por el usuario y preserva sus ediciones existentes; no sobrescribas una nota que ya existe.

Cuando las fuentes no permitan saber qué decidió o hizo el usuario, márcalo como «a confirmar por <usuario>» y recógelo en la entrega. No lo completes por inferencia. Si una identidad (por ejemplo, la cuenta que hizo un merge) aparece en las fuentes, resuélvela antes de atribuirla a «otra persona».

Si falta la skill o el destino acordado, informa el bloqueo antes de borrar los recursos necesarios para completar la nota. No sustituyas el paso por un resumen sin aplicar `project-impact-capture`.

### Cierre en lote

Con varias tareas independientes puedes repartir la redacción de las notas entre subagentes. Dales los hechos ya verificados (PRs, releases, recursos eliminados), las rutas de las notas y estos mismos límites, y pide que solo escriban notas. Después, el responsable del cierre revisa todas las notas personales: busca filtraciones (enlaces, nombres de personas, código, tablas) y comprueba que «Mi rol» no atribuya decisiones sin fuente. Corrige lo necesario y consolida los puntos «a confirmar».

## Limpiar recursos exclusivos

Antes de eliminar, comprueba que ambas notas estén guardadas y sean legibles fuera de los candidatos.

Enumera rutas e identidades exactas a partir de la nota y del trabajo real. No atribuyas propiedad solo por el nombre, no hagas barridos de carpetas globales, temporales o de repositorios, y no toques archivos de otros usuarios ni de root. Los candidatos de una tarea son:

1. **Worktree.** Comprueba que no tenga cambios sin commit ni commits fuera del PR mergeado: compara el HEAD local con el head del PR (`git fetch origin pull/<n>/head` y `git merge-base --is-ancestor`). Si hay cambios útiles sin integrar, no los descartes: ofrécelos al usuario (por ejemplo, para llevarlos a un PR abierto) y conserva el worktree hasta que decida.
2. **Contenedores y volúmenes locales de la tarea** (si el acuerdo lo autoriza). Solo los del proyecto Compose que declara el propio worktree (por ejemplo, `COMPOSE_PROJECT_NAME` en su env local), nunca los del checkout principal ni los compartidos. Bórralos junto con el worktree mediante el hook o la operación de eliminación del repo, que los conoce. Antes, lista los proyectos y volúmenes (`docker compose ls`, `docker volume ls`) para saber cuáles existen y detectar volúmenes huérfanos de la misma tarea.
3. **Ramas locales integradas** (si el acuerdo lo autoriza). Bórralas solo si su contenido está contenido en el head del PR mergeado. Comprueba que la rama remota ya no exista o informa si sigue. No borres ramas remotas.
4. **Temporales de sesión** (si el acuerdo lo autoriza). Son la carpeta temporal del chat de la tarea (por ejemplo, `/private/tmp/claude-<uid>/<ruta del worktree codificada>`) y los archivos que el propio cierre creó. Puedes listar otros restos de `/tmp` que claramente vengan de la tarea (fixtures o builds vacíos), pero pide confirmación antes de borrarlos. Conserva siempre las cachés de herramientas, los sockets y archivos del sistema o del cliente, y los historiales de chat.
5. **Procesos y puertos**: comprueba que no queden servidores o procesos corriendo desde el worktree.

Comprueba también que los candidatos:
- No sean el checkout principal ni el ancla de las notas.
- No estén compartidos con otros chats ni los use ningún servicio activo.
- Sigan en la ruta comprobada; no sigas enlaces simbólicos para borrar destinos ajenos.

Conserva los recursos compartidos, el trabajo adicional, el material que se haya pedido conservar y los candidatos de pertenencia incierta, y explica el motivo. Los datos de prueba en entornos compartidos (stg o prod) no se borran en el cierre: se informan. Limpia los candidatos ya seguros y no fuerces la eliminación para completar el cierre.

## Elegir un mecanismo disponible

Identifica quién gestiona el worktree mediante su registro y contexto, no solo por la ruta. Consulta las instrucciones del entorno para elegir la operación apropiada.

- **Worktree gestionado por una aplicación o con hook de eliminación en el repo:** usa su operación admitida, con la identidad exacta del recurso. Lee antes el hook: si también borra contenedores o volúmenes, úsalo solo cuando el punto 2 esté autorizado; si no, usa `git worktree remove` y deja los contenedores como pendiente. Si te falta acceso al gestor o la operación se rechaza, conserva el recurso y explica el pendiente; no sustituyas el rechazo por un borrado de archivos.
- **Git ordinario no gestionado:** después de las comprobaciones, usa `git worktree remove` sin `--force` desde otro checkout estable. Si se rechaza, inspecciona y deja el pendiente.

No retires el checkout de otra sesión activa ni abras otro cliente para forzar la eliminación. Si el modo de permisos bloquea un borrado, no lo eludas: explica qué falta y pide la autorización.

## Eliminar el chat de la tarea (si el acuerdo lo autoriza)

Cuando el cierre de una tarea está completo, puedes eliminar su chat con la operación de sesiones del cliente (por ejemplo, `delete_session`), que pide la confirmación del usuario. No elimines:
- el chat actual ni el del boss;
- chats con un PR abierto, con trabajo en curso o de tareas que siguen pendientes;
- chats cuyo worktree tenga cambios sin integrar.

Si el acuerdo no autoriza eliminarlos, ofrece archivarlos o eliminarlos y no lo hagas por tu cuenta.

## Verificar y entregar

Comprueba el resultado real de cada eliminación (`git worktree list`, `git branch`, `docker compose ls`, carpetas temporales, lista de sesiones) y que las dos notas sigan accesibles. Agrega al cierre el resultado de la limpieza. Distingue entrega desplegada de limpieza completa.

Si eres el boss, actualiza su nota general con el resultado y un enlace al cierre. Si eres un chat de tarea, entrega el resumen solo al boss identificado y dentro de la autorización vigente. Si no hay herramienta o acceso, deja el mensaje listo en la respuesta; no inventes comunicación entre clientes.

Entrega:
- ubicaciones de ambas notas por tarea;
- PRs, releases o entorno verificados;
- recursos eliminados y recursos conservados, con su motivo;
- tareas que quedaron fuera del cierre, con su motivo;
- puntos «a confirmar» para el usuario y pendientes reales.

Si el cierre se interrumpe, inspecciona el estado antes de reanudar eliminaciones.
