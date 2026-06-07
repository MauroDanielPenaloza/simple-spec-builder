---
name: simple-spec-builder
description: >
  Genera, detalla, divide y mapea historias de usuario ágiles. Aplica INVEST, 5Cs, BDD/Gherkin, enfoques de "Tres Amigos", evaluación de NFRs/DoD, 10 estrategias de Story Splitting y el modelo de User Story Mapping (Backbone, Narrative Flow, Slicing) maximizando el valor (Outcome) sobre la cantidad (Output).
trigger: Cuando el usuario solicita escribir una specificacion, spec, historia de usuario, redactar criterios de aceptación, dividir una épica, gestionar deuda técnica, priorizar un backlog o mapear el flujo visual de un producto.
license: Apache-2.0
metadata:
  author: mauro.penaloza
  version: "1.1"
---

#### Cuando Usar

Usar esta skill cuando:

* El usuario describe una funcionalidad genérica y pide convertirla en una historia de usuario formal.
* Se necesita transformar una idea en requerimientos ágiles estructurados y organizados visualmente.
* Se requiere mapear visualmente la experiencia completa de un usuario (User Story Mapping).
* Se necesita dividir una historia de usuario demasiado grande (Épica) usando técnicas avanzadas de partición.
* Una historia de usuario existente carece de Criterios de Aceptación medibles o requiere estructuración en Gherkin.
* Hay incertidumbre técnica o funcional que requiere un Spike, una historia técnica independiente o un Esqueleto Funcional (Walking Skeleton).
* Existe falta de claridad sobre el valor real que aportará una funcionalidad al negocio o al cliente.

--------------------------------------------------------------------------------

#### Especificación enriquecida por ticket

Para trabajo en este repositorio con cortes verticales documentados en disco:

| Artefacto | Ubicación |
|-----------|-----------|
| Índice y orden de ejecución | `.tasks/<PBI-u-otro-id>/index-spec.md` |
| Una historia/slice por archivo | `.tasks/<id>/spec-<NN>-<nombre-kebab>.md` |
| Toma de decisiones | `.tasks/<id>/open-questions.md` |

La plantilla oficial del equipo para el formato de spec está en **[templates/enriched-template.md](./templates/enriched-template.md)**.

##### Documento `open-questions.md` — generación obligatoria

**Cuándo generarlo:** Siempre que al redactar o revisar las specs del PBI se detecten blockers,
ambigüedades o inconsistencias que requieran una decisión del tech lead o del equipo antes de implementar.
No es un artefacto opcional: si hay al menos un ítem sin resolver, el documento debe existir.

**Regla de actualización:** Cada vez que el usuario responde una decisión abierta en el documento,
reflejar el cambio en la spec correspondiente y marcar el ítem como cerrado en el resumen final.

La estructura completa del documento, las reglas de formato y un ejemplo real están en
**[templates/open-questions.md](./templates/open-questions.md)**.

--------------------------------------------------------------------------------

#### Contexto del Proyecto

| Aspecto | Detalle |
| ------ | ------ |
| Formato de Historia | `Como [rol del usuario], quiero [objetivo], para poder [beneficio]` |
| Criterios de Aceptación | Formato BDD / Lenguaje Gherkin (Dado que / Cuando / Entonces) |
| Framework de Calidad | [Modelo INVEST](./invest-guidelines.md), Criterios SMART, Jobs-to-be-Done (JTBD) |
| Enfoque de Planificación| User Story Mapping (Jeff Patton), Outcomes > Output |

Arquitectura relevante para esta skill:
Las historias deben representar cortes verticales funcionales (vertical slicing). En proyectos y épicas grandes, el primer corte debe conformar un esqueleto funcional que recorra de extremo a extremo el sistema (Functional Walking Skeleton) para validar el riesgo técnico temprano.

--------------------------------------------------------------------------------

#### Patrones Críticos

**A. Análisis y Empatía Continua**

* **PATTERN 1: De las 3Cs a las 5Cs.** Asegúrate de no estancarte en *Card, Conversation, Confirmation*; las historias deben planificar su éxito escalando a *Construction* y *Consequences*. Agrega métricas para saber si la funcionalidad implementada realmente aportó el beneficio deseado.
* **PATTERN 2: Prevención del Antipatrón "Lanzar por el muro".** Bajo ninguna circunstancia escribas y asumas el trabajo aislado de un Product Owner; fuerza al usuario a un ciclo de preguntas. Las historias son invitaciones constantes a conversar.
* **PATTERN 3: Enfoque en User Personas y Jobs-to-be-Done (JTBD).** Abandona el uso del rol genérico "usuario". Crea y usa arquetipos ficticios detallados que empaticen con su demografía y motivaciones para el campo de Rol. Céntrate en el trabajo o problema fundamental que el cliente necesita resolver (JTBD).
* **PATTERN 4: Entendimiento Compartido sobre Documentación ("Talk and Doc").** El objetivo real de las historias no es escribir el documento perfecto, sino construir un entendimiento compartido a través de conversaciones continuas. Escribe para recordar la conversación, no para reemplazarla.

**B. Organización y Calidad de Requisitos**

* **PATTERN 5: Separación estricta de Casos de Uso.** No permitas que la historia se convierta en un caso de uso; céntrate en el "qué" necesita el usuario y deja el "cómo" y la interacción del sistema para otras documentaciones como diagramas.
* **PATTERN 6: Historias Técnicas y Spikes.** Escribe historias puramente técnicas (como infraestructura o refactorización) sin forzar el formato "Como [rol]". Si hay mucha incertidumbre, genera primero un *Spike* técnico para evaluar la viabilidad limitando el tiempo de exploración.
* **PATTERN 7: Separación de NFRs.** Nunca trates el rendimiento, escalabilidad, accesibilidad o seguridad como simples criterios de aceptación; aíslalos como Requerimientos No Funcionales (NFRs) que imponen restricciones de calidad sistémicas.
* **PATTERN 8: Respeto por la "Definition of Done" (DoD).** Los criterios de aceptación comprueban requerimientos funcionales específicos; nunca incluyas en ellos tareas de calidad genéricas (pruebas unitarias, revisiones), ya que estas pertenecen a la DoD obligatoria del proyecto.
* **PATTERN 9: Plan-Validate-Execute para IA.** En requerimientos complejos, primero genera un plan estructurado o *outline* en un archivo de validación, somételo a aprobación del usuario y luego procede a la redacción definitiva en Gherkin.

**C. Escritura de Criterios de Aceptación**

* **PATTERN 10: Calidad SMART.** Diseña cada criterio para que sea Específico, Medible, Alcanzable, Relevante y Limitado en el tiempo. Un buen criterio siempre es verificable de forma binaria.
* **PATTERN 11: Lenguaje BDD/Gherkin universal.** Aplica estrictamente los componentes base: Dado que (contexto), Cuando (evento disparador) y Entonces (resultado esperado).
* **PATTERN 12: Happy Flow primero, Unhappy Flows después.** Desarrolla el escenario principal asumiendo un entorno ideal. Posteriormente, rompe intencionalmente el escenario con errores o caminos alternativos.
* **PATTERN 13: División de Criterios Complejos.** Si el criterio encadena excesivas condiciones ("DADO a Y b CUANDO c ENTONCES d Y e"), debes fragmentarlo forzosamente en múltiples criterios individuales.
* **PATTERN 14: La Regla de los Tres Amigos.** Simula mentalmente y garantiza que los criterios cubran la alineación de tres pilares: Negocio (PO), Desarrollo (IT) y Casos borde de Diseño/QA.

**D. Story Splitting Avanzado (Estrategias de División Vertical para Épicas)**

* **PATTERN 15: División por Pasos del Flujo de Trabajo (Estrategia 1).** Divide flujos aislando las partes iniciales y finales para crear el MVP, difiriendo los pasos intermedios.
* **PATTERN 16: División por Reglas de Negocio (Estrategia 2).** Empieza relajando las restricciones operativas e incorpora posteriormente el endurecimiento (normas legales, rechazos) mediante historias subsecuentes.
* **PATTERN 17: División por Opciones de Entrada/Plataformas (Estrategia 4).** Genera historias separadas basándote en la interfaz (App vs Web) o en cómo entran los datos.
* **PATTERN 18: División por Tipos de Datos (Estrategia 5).** Aísla requerimientos extrayendo la complejidad de parámetros (ej. buscador simple vs filtros avanzados).
* **PATTERN 19: División por Operaciones CRUD (Estrategia 6).** Penaliza el uso del verbo "Gestionar"; desglósalo forzosamente en creación, lectura, actualización y eliminación.
* **PATTERN 20: División por Escenarios de Prueba (Estrategia 7).** Usa flujos *unhappy* y casos borde complejos para independizarlos del requerimiento padre y crear historias propias.
* **PATTERN 21: División por Roles (Estrategia 8).** Extrae el objetivo a varias historias si el resultado impacta directamente pero de formas diversas a clientes ordinarios, VIPs o administradores.
* **PATTERN 22: Optimizar Más Tarde (Estrategia 9).** Aplica "hazlo funcionar primero" dejando la funcionalidad base y aplaza a futuras historias los refinamientos severos en velocidad.
* **PATTERN 23: Compatibilidad de Tecnologías (Estrategia 10).** Asegura entregar valor concentrando el desarrollo inicial en los navegadores o tecnologías primarias.
* **PATTERN 24: División "Good-Better-Best".** Para evitar parálisis, define primero las historias "suficientemente buenas por ahora" (Good), luego extrae las que harían la experiencia "Mejor" (Better) y deja para el final las "Óptimas" (Best).

**E. User Story Mapping (Planificación Visual de Producto)**

* **PATTERN 25: Resultados (Outcomes) sobre Producción (Output).** Tu trabajo no es construir más software, sino maximizar el impacto de la solución. Prioriza los resultados del negocio antes que las características.
* **PATTERN 26: Amplitud antes que Profundidad (Mile Wide, Inch Deep).** Al mapear, no te pierdas en detalles. Construye primero la "columna vertebral" (Backbone) agrupando actividades de alto nivel en un flujo narrativo de izquierda a derecha antes de profundizar de arriba a abajo.
* **PATTERN 27: Slicing Estratégico (MVP).** Traza líneas horizontales en el Story Map para recortar todo lo que no sea necesario y agrupa las historias de la primera franja para formar el MVP funcional.
* **PATTERN 28: Esqueleto Funcional Andante (Functional Walking Skeleton).** En el Slicing, no dividas por capas técnicas. Crea un primer corte que sea un esqueleto funcional de extremo a extremo para descubrir riesgos técnicos de inmediato.

**F. Herramientas de Estimación y Valoración Económica**

* **PATTERN 29: Matriz MoSCoW.** Proporciona contextos ayudando al usuario a etiquetar los requisitos entre Must have, Should have, Could have y Won't have.
* **PATTERN 30: Cálculo del Valor Real (ROI / WSJF).** Aplica priorización WSJF (Coste de demora / Tamaño) motivando a medir en base al beneficio empírico económico.

--------------------------------------------------------------------------------

#### Árbol de Decisión Avanzado

El agente debe determinar si la solicitud es una redacción/refinamiento específico o un mapeo de producto completo.

**FLUJO 1: Análisis, Redacción y División (Historias / Épicas)**

1. **¿El usuario proporciona un requerimiento carente de Rol explícito, Valor empírico o contexto "Por qué"?**
   * SÍ: **Detente**. Haz preguntas para construir un "User Persona" y usa *Jobs-to-be-Done* para entender la necesidad. Aplica **Pattern 9**.
   * NO: Continúa al paso 2.
2. **¿Es un requerimiento de cara al cliente (funcional) o técnico de sistema?**
   * TÉCNICO: Aplica **Pattern 6** (Historia Técnica/Spike sin formato "Como usuario").
   * FUNCIONAL: Continúa al paso 3.
3. **¿La solicitud implica el término ambiguo "gestionar", o abarca un flujo gigantesco (Épica)?**
   * SÍ: Evalúa aplicar división por **CRUD (Pattern 19)**, **Opciones de Entrada (Pattern 17)**, o **Good-Better-Best (Pattern 24)**. Propón 2 o 3 estrategias de división.
   * NO: Continúa al paso 4.
4. **¿Los Criterios de Aceptación (AC) cubren únicamente escenarios felices?**
   * SÍ: Interrumpe. Aplica **Pattern 12** exigiendo definir *unhappy flows*. Si son muy arriesgados, divídelos usando **Pattern 20**.
   * NO: Continúa al paso 5.
5. **¿Los Criterios de Aceptación arrastran validaciones excesivas o incluyen requisitos como "Cargar rápido"?**
   * SÍ: Refina y aplica **Pattern 13** fragmentando criterios largos. Aplica **Pattern 7 y 8** para separar Restricciones Globales (NFRs) y DoD.
   * NO: Procede a estructurar en sintaxis BDD/Gherkin.
6. **¿El usuario tiene claro cómo medir el impacto tras su despliegue?**
   * NO: Incorpora a la discusión métricas de seguimiento (*Consequences* / Pattern 1).
   * SÍ: Genera la historia ágil final.

**FLUJO 2: User Story Mapping (Mapeo de Producto / Trazado Visual)**
Si el usuario solicita "mapear", "crear un flujo", o "definir un MVP":

1. **Frame the problem:** ¿Se ha definido el arquetipo de usuario y el resultado esperado (Outcome / Pattern 25)?
2. **Map the big picture (Backbone):** Define la columna vertebral ordenando cronológicamente (izquierda a derecha) las actividades principales (Pattern 26).
3. **Explore (Detalles):** Profundiza de arriba a abajo. Pregunta por alternativas, reglas de negocio o variaciones de datos.
4. **Slice out a release strategy (MVP):** Traza líneas de "Slicing" enfocándote solo en el mínimo necesario para lograr el resultado principal (Pattern 27).
5. **Slice out a learning strategy (Walking Skeleton):** Si hay alto riesgo técnico, propón un "Functional Walking Skeleton" (Pattern 28) como el primer slice (Corte 1).

--------------------------------------------------------------------------------

#### Ejemplos

##### Ejemplo 1: Historia estándar Gherkin (Happy/Unhappy Flow)

**Historia:** Como cliente, quiero retirar dinero del cajero para poder evitar hacer cola en el banco.
**Criterio de Aceptación (Escenario 1: Happy flow)**:

* **Dado que** la cuenta tiene crédito y la tarjeta es válida
* **Cuando** el cliente pide dinero
* **Entonces** la cuenta es debitada y el dinero entregado.
**Criterio de Aceptación (Escenario 2: Unhappy flow)**:
* **Dado que** la cuenta excede el límite negativo acordado
* **Cuando** el cliente pide dinero
* **Entonces** el cajero muestra un mensaje negando el pedido.

##### Ejemplo 2: División de historias por operaciones CRUD

*Solicitud: "Como usuario quiero gestionar mi carrito"*

* *Alta:* Como comprador quiero añadir libros nuevos a mi carrito para realizar el pedido.
* *Lectura:* Como comprador quiero consultar los items en mi carrito para saber el total.
* *Modificación:* Como comprador quiero actualizar las unidades de un libro en mi carrito.

##### Ejemplo 3: User Story Mapping - Amplitud (Backbone) vs Profundidad (Detalles)

**Backbone (Izquierda a Derecha):** Buscar producto -> Añadir a carrito -> Pagar -> Confirmar envío.
**Detalles bajo "Pagar" (Arriba a Abajo):**

* *Good enough:* Pagar con tarjeta de crédito (MVP).
* *Better:* Pagar con PayPal.
* *Unhappy flow:* Mostrar error si la tarjeta es rechazada.

##### Ejemplo 4: Slicing y Functional Walking Skeleton

**Épica:** Como organizador quiero gestionar los asistentes al evento.

* **Slice 1 (Walking Skeleton):** Registrar un asistente manualmente con nombre y email para ver que el flujo integral de base de datos funciona.
* **Slice 2 (Make it better):** Importar lista de asistentes vía CSV.
* **Slice 3 (Make it releasable):** Enviar email automático de bienvenida.

--------------------------------------------------------------------------------

#### Recursos

* **Guía de Calidad**: [Guías INVEST y Calidad de Historias de Usuario](./invest-guidelines.md)
* **Template HTML de referencia**: [templates/user_story_template.md](./templates/user_story_template.md)
* **Metodología Mapeo**: [*User Story Mapping* por Jeff Patton (Conceptos: Backbone, Narrative Flow, Outcomes > Output, Slicing)](./templates/key_concept_jeff_patton.md)
