# Simple Spec Builder
Ssb es una skill que ayuda a la explotación de las historias de usuario que se desprenden de una tarea, al mismo tiempo que permite definir las especificaciones de las historias que va a generar el agente de desarrollo.

## Flujo de trabajo recomendado

1. Crear una carpeta `.tasks` dentro del repositorio raíz.
1. Crear una subcarpeta con el ID de la tarea a realizar, por ejemplo: `.tasks/EXA-1001`.
1. Dentro de la subcarpeta creada en el punto 2, crear un archivo llamado `raw-requirement.md` donde ponemos el contenido del requerimiento que vamos a trabajar en esta tarea.
1. Correr la skill para que nos explote el requerimiento en historias de usuario y especificaciones para cada una de ellas. Generará un archivo `index-spec.md` que contiene el orden de ejecución de las specs y otro llamado `open-questions.md` para resolver inconsistencias, ambigüedades y otros problemas que hayan surgido en la explotación.
1. Resolver cada una de las preguntas en `open-questions.md` para explorar la solución. En este momento se pueden corregir las specs generadas en el paso anterior corrigiendo cada parte.
1. Correr nuevamente el agente para que nos ayude a refinar las especificaciones de las historias de usuario.
1. Una vez cerrado el loop de resolución de ambigüedades procedemos con el modo plan.
1. Con un plan cerrado corremos el agente para que construya la solución.
