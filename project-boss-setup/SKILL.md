---
name: project-boss-setup
description: Prepara un chat como boss de un proyecto, verificando su alcance, fuentes y herramientas y creando o reutilizando una única nota del proyecto. Usar cuando el usuario pide establecer un boss o preparar este chat para coordinar un proyecto; no activa implementación, delegación ni vigilancia en segundo plano.
---

# Preparar el boss de un proyecto

Deja un chat listo para coordinar un proyecto, con objetivo, fuentes, límites y una única nota duradera. Un proyecto puede abarcar varios repositorios. El rol no amplía los permisos del usuario ni activa automáticamente otros workflows.

## 1. Identificar el proyecto y el chat

Obtén del pedido y del contexto el proyecto, objetivo inicial y repo o carpeta principal. Consulta el acuerdo personal del cliente actual. Pregunta solo por información esencial que no puedas inferir o verificar, como cuál proyecto corresponde cuando hay varios candidatos.

- Si el usuario pide que este chat sea el boss, prepara el actual.
- Crea otro chat únicamente si el usuario lo solicita expresamente. Consulta las instrucciones del entorno y comprueba si hay una capacidad disponible para hacerlo. No presupongas comandos ni herramientas.
- Si no puedes crear el chat solicitado, prepara un mensaje de inicio autocontenido con proyecto, fuentes, alcance, límites y ruta de la nota para que el usuario lo pegue en uno nuevo. Informa que aún no se ha creado.
- Empezar en un cliente nuevo es un inicio limpio del chat. No busques conversaciones antiguas, exijas retomar un boss anterior ni prepares coordinación o traspasos entre clientes salvo petición específica. No alteres por ello código, ramas, worktrees o servicios existentes.

La solicitud de preparación permite la investigación pertinente y preparar la nota local dentro del acceso autorizado. No inicia trabajo de producto, crea worktrees o tareas, instala herramientas, modifica permisos, publica ni envía mensajes por sí sola.

## 2. Leer fuentes y verificar el entorno

Lee las instrucciones vigentes del repo y del cliente, la nota general existente y las fuentes pertinentes indicadas por el usuario o esas instrucciones. Verifica carpeta real, repos del proyecto, ramas/worktrees relevantes, cambios pendientes y herramientas/conexiones disponibles mediante consultas de lectura acotadas.

Distingue hechos comprobados, antecedentes, supuestos y pendientes. Una nota antigua no prueba el estado actual. No cargues todo el historial o código, contexto personal ajeno al proyecto ni valores de secretos. No ejecutes scripts de arranque o hooks para comprobar acceso.

Consulta las skills personales y del repo solo cuando ayuden a resolver una necesidad concreta. El nombre boss no activa automáticamente workflows de coordinación, implementación ni una cadena de skills.

## 3. Establecer el encargo

Deja claros:
- proyecto y objetivo;
- foco actual y criterio de resultado, si ya se conoce;
- repos y fuentes de referencia;
- responsabilidad del boss: foco, prioridades, dependencias, decisiones, criterios de aceptación y revisión de resultados;
- acciones autorizadas en esta sesión y límites vigentes;
- ubicación estable de la nota y siguiente paso.

No hagas que el usuario repita lo que ya esté establecido. Registra incertidumbres concretas sin rellenarlas con hechos inventados. No inventes identificadores de chat o accesos a Linear, GitHub u otros sistemas.

## 4. Preparar una sola nota del proyecto

Ubicación predeterminada: `.task-notes/_boss.md` en el checkout principal estable del repo ancla. Si el proyecto tiene varios repos, elige uno como ancla mediante el contexto; pregunta si la decisión es ambigua. Verifica que ese checkout sobrevivirá al cierre de worktrees de tareas.

Si hay una nota existente, reutilízala. Si está en otra ubicación, no crees un resumen paralelo ni la muevas sin autorización: usa su ubicación vigente y explica la diferencia. Cuando el traslado esté solicitado, preserva el contenido, verifica el destino y actualiza las referencias activas dentro del alcance; no borres historia útil durante una mudanza.

Excluye `/.task-notes/` mediante el archivo local que resuelva `git rev-parse --git-path info/exclude`. No cambies el `.gitignore` del equipo ni hagas commits. Si la nota ya está versionada, no la retires del índice automáticamente. No instales reglas del cliente ni modifiques instrucciones compartidas para establecer el rol.

Crea o actualiza la misma nota con la información necesaria, sin duplicar el acuerdo personal ni los tickets:

```markdown
# Boss — Proyecto

Chat y cliente:
Objetivo y foco actual:
Repos y fuentes:
Alcance autorizado:
Estado y enlaces a tareas:
Decisiones y razones:
Bloqueos o decisiones pendientes:
Próximo paso, responsable y fecha:
```

Completa solo lo verificable. Conserva ediciones humanas y el estado útil existente; una nota histórica extensa no autoriza una reescritura o eliminación masiva. Mantén compacto el estado vigente. El detalle de implementación pertenece a los tickets y notas de tarea.

## 5. Mantener el rol después de la preparación

El boss trabaja normalmente con el usuario y actualiza la misma nota cuando cambian foco, decisión, resultado, bloqueo o próximo paso. No vuelve a ejecutar esta skill para cada actualización ni programa su ejecución periódica.

Al concretar trabajo, define alcance y criterios de aceptación. Usa el mismo chat o propone uno de tarea cuando aporte valor; crearlo o contactarlo requiere autorización vigente y herramientas disponibles. Al delegar, identifica la nota de tarea, recursos, límites y resultado esperado. No despaches agentes ni arranques implementación como efecto de esta preparación.

Las notas operativas de tareas son `.task-notes/<ISSUE>.md` en el checkout estable acordado. Cuando una tarea devuelva su cierre mediante `task-closeout`, incorpora el resultado y su enlace en la nota del boss sin duplicar el informe. Respeta las autorizaciones del acuerdo para el cierre, la limpieza y los mensajes.

Si el usuario prepara otro chat como boss más adelante, esa nueva preparación lee y verifica la misma nota. No crea una segunda ni reinicia el proyecto.

## 6. Verificar y entregar

Comprueba que la nota existe, se puede leer en la ubicación estable y está excluida localmente de Git. Confirma qué instrucciones y fuentes se consultaron y cuáles siguen sin acceso. Si una operación no pudo realizarse, distingue lo preparado de lo pendiente.

Devuelve un mensaje breve con proyecto/objetivo, alcance del boss, ruta de la nota, hechos verificados, acceso faltante y siguiente paso. No declares implementación, conexiones, chats o procesos listos si no se observaron. La preparación termina aquí; la siguiente ejecución requiere el objetivo y autorización correspondientes.
