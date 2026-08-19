# ADI - Teoría y Recursos

Material de estudio teórico de la materia **Arquitectura y Diseño de Interfaces (ADI)**
del IES 9-018 — Tecnicatura Superior en Desarrollo de Software — ciclo 2026.

## Estructura

El material está organizado por las **6 unidades** del programa oficial de la materia:

| Unidad | Carpeta | Temas |
|--------|---------|-------|
| 1. Procesos y Metodologías | [`unidad-1-procesos-y-metodologias/`](./unidad-1-procesos-y-metodologias/) | Introducción al desarrollo de software, ciclo de vida, modelos adaptativos, procesos ágiles, tendencias |
| 2. Arquitectura de Software | [`unidad-2-arquitectura-de-software/`](./unidad-2-arquitectura-de-software/) | Conceptos generales, estilos arquitectónicos, patrones de diseño, vistas y escenarios, actividades |
| 3. Diseño de Interfaces | [`unidad-3-diseno-de-interfaces/`](./unidad-3-diseno-de-interfaces/) | HCI y usabilidad, ergonomía del software, métodos de diseño, investigación de usuarios, patrones |
| 4. Arquitectura Web | [`unidad-4-arquitectura-web/`](./unidad-4-arquitectura-web/) | Evolución de la web, diseño de sitios, patrones de diseño web |
| 5. Arquitectura Mobile | [`unidad-5-arquitectura-mobile/`](./unidad-5-arquitectura-mobile/) | Conceptos mobile, patrones, herramientas de desarrollo |
| 6. Herramientas y Tecnologías | [`unidad-6-herramientas-y-tecnologias/`](./unidad-6-herramientas-y-tecnologias/) | Tecnologías, ecosistema de herramientas, diseño y desarrollo de interfaces/web/mobile, integración |

## Cómo leer cada archivo

Cada tema sigue un **formato estándar**:

1. **Introducción** — contexto de por qué es importante.
2. **Conceptos clave** — explicación de 0 a 100, para quien no sabe nada de la materia.
3. **Analogía** — comparación con algo cotidiano para conceptos abstractos.
4. **Ejemplo práctico** — aplicación concreta.
5. **Comparativas** — tablas que enfrentan opciones.
6. **Fuentes** — links reales verificables (PDFs gratuitos, docs oficiales, recursos académicos).
7. **Para practicar** — ejercicios para afianzar.

El material está redactado en **español**, con el término técnico en inglés entre paréntesis
donde corresponde.

## Recursos generales

En [`recursos-generales/`](./recursos-generales/) se recopilan los vínculos a las fuentes
verificables usadas en todo el material (libros, guías oficiales, documentación técnica).

## 🛠️ Método de trabajo colaborativo

Este repositorio (`ADI-teoria-y-recursos`) y el repo de consignas (`proyecto-adi-2026`)
trabajan en conjunto. El flujo de trabajo para los estudiantes es:

### 1. Fork y clonar
- Hacé fork de **ambos repos** desde tu cuenta de GitHub.
- Cloná ambos repos a tu máquina local.
- Agregá el repo base como upstream en cada uno.

### 2. Avanzar en una tarea
- Trabajá en un tema, ejercicio o mejora en cualquiera de los dos repos.
- Cuando tengas avances relevantes, **hacé un commit** con mensaje Conventional Commit (ej: `feat:`, `docs:`, `fix:`).

### 3. Abrir un Pull Request
- Subí tu rama a tu fork y abrí un PR contra `main` del repo correspondiente.
- En el cuerpo del PR, **describí qué hiciste y por qué es relevante** para la materia.
- Si la mejora es de contenido teórico, abrí el PR en `ADI-teoria-y-recursos`.
- Si la mejora es de proyecto/andamiaje, abrí el PR en `proyecto-adi-2026`.

### 4. Iteración con el docente
- Como docente, revisaré los PRs y dejaré comentarios o aprobaciones.
- Si hay cambios solicitados, hacé los ajustamientos y pushá de nuevo a la misma rama del PR (se actualiza automáticamente).
- Una vez aprobado, el PR se mergea a `main`.

### 5. Usar Issues para sugerencias
- Si tenés una idea pero aún no está lista para un PR, **abrí un Issue** en el repo correspondiente.
- Etiquetá el Issue con `mejora`, `analogía`, `duda` o `sugerencia` según corresponda.
- El docente y los compañeros pueden comentar y ayudarte a definirlo mejor.

### 6. Flujo recomendado (resumen)
```
# Fork ambos repos
gh repo fork IES9018/ADI-teoria-y-recursos --clone=true
gh repo fork IES9018/proyecto-adi-2026 --clone=true

# En cada repo, después del fork:
git remote add upstream https://github.com/IES9018/<repo>.git
git checkout -b feat/mejora-analogia-x

# Trabajar, commitear y push
git add .
git commit -m "feat: nueva analogía para concepto Y"
git push -u origin feat/mejora-analogia-x

# Abrir PR contra main del repo correspondiente
gh pr create --base main --head origin/feat/mejora-analogia-x \
  --title "feat: nueva analogía para concepto Y" --body "Descripción del aporte..."
```
