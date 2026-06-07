# User Story – plantilla enriquecida

Use esta plantilla cuando documentes historias bajo **`.tasks/<ticket>/`** (ej. `PBI-24287`; el identificador es variable).  
**Convenciones de archivos (misma carpeta del ticket):**

| Archivo | Propósito |
|---------|-----------|
| `index-spec.md` | Índice: fuentes, orden de ejecución, dependencias entre specs, mapeo global campo-a-campo si aplica. |
| `spec-<NN>-<nombre-kebab>.md` | Una historia/slice vertical por archivo; `<NN>` = `01`, `02`, … |

**Idioma:** historias y Gherkin **en inglés** por defecto (equipo); encabezados pueden seguir el template funcional en español como en esta plantilla.

---

## Plantilla por archivo — `spec-<NN>-*.md`

Copiar secciones que apliquen; omitir las vacías.

---

### `# Descripcion de User Story`

Un párrafo corto (qué problema resuelve este slice y cómo encaja en la épica).

---

### `# Story (INVEST)`

```
**As** …  
**I want** …  
**So that** …
```

---

### `# Análisis`

#### Approach

Breve texto: estrategia de solución (vertical slice), supuestos, alcance explícito / fuera de alcance.

#### API Controller (este spec)

Tabla `Method | Route | Purpose`, luego fragmentos JSON:

- Request (cuando aplique): `Content-Type`, ejemplo `application/json`.
- Response (códigos esperados según controller actual).
- **Validaciones de entrada** (FluentValidation / DataAnnotations): opcionalidad, longitudes, tipos — sin duplicar DoD genérica.

---

### `# Punto de Arranque`

Tabla de ejemplo:

| | |
| -- | -- |
| **Proyecto** | `current-project`, `Core`, etc. |
| **Clases** | Rutas de archivo desde raíz repo (`src/…`). |
| **Método / mapping** | Qué método o perfil AutoMapper tocar. |

---

### `# Context` (opcional)

Enlaces relativos a `raw-definition.md`, `frontend-change-definition.md`, otros specs (`spec-02-…`).

---

### `# Criterio de Aceptación`

Escenarios **Given / When / Then** (inglés recomendado). Primero **happy path**, luego **unhappy** / autorización / validación.

---

### `# Test Plan`

#### Contexto

Qué datos, ambiente o policies hacen falta.

#### Escenarios

Tabla numerada: Éxito / Éxito alternativo / Error / Regresión.

---

### `# Validacion post implementacion`

Lista corta alineada con el repo, por ejemplo:

1. `mvn clean install`
2. `mvn test` en proyectos de test relevantes
3. Arranque local y prueba manual o funcional si aplica

---

### `# Non-functional notes`

NFRs globales (performance, seguridad por políticas); **no** meter DoD (tests unitarios genéricos, code review) dentro de los AC.

---

### `# Open questions` (opcional)

Bullets si hay ambigüedad de negocio pendiente de PO.

---

## Plantilla — `index-spec.md`

```markdown
# <TICKET> — specification index

## Source artifacts

Tabla: archivo | propósito.

## Field mapping (contract ↔ Core) — cuando aplique

Tabla resumen JSON ↔ DTO ↔ dominio; enlaces a cada spec.

## Execution order

Tabla: Order | spec file | Summary | Depends on

## Suggested increments / Backbone

Narrativa MVP → mejoras (Story Mapping / Walking Skeleton).
```

Referencia cruzada a esta plantilla desde la skill [simple-spec-builder](../SKILL.md).
