# INSTRUCCIONES_ORGANIZACION.md

## Reglas Obligatorias de Operatoria y Repositorios — Organización IES9018

### 1. Creación de Repositorios de Estudiantes
* **Sin Forks:** Los estudiantes **NO** deben forquear los repositorios base de la materia.
* **Creación Directa:** Cada estudiante o equipo creará su repositorio de trabajo directamente dentro de la organización `IES9018` en GitHub.
* **Nomenclatura Obligatoria:** El nombre del repositorio debe seguir estrictamente la sintaxis:
  `<nombre_estudiante>-<nombre_proyecto>` (Ejemplos: `raul-blog`, `analia-crm`).

### 2. Flujo de Trabajo y Rol Docente
* **Rol del Docente (Capataz / Arquitecto de Obra):** El profesor no escribe el código del alumno; inspecciona la arquitectura, audita el uso de especificaciones y deja revisiones mediante **Issues** y comentarios de Pull Requests.
* **Uso del Arnés (.opencoderules / INSTRUCTIONS.md):** Todo proyecto debe incluir el arnés de control en la raíz para limitar y dirigir la generación de la IA local (OpenCode).
* **Entregas:** Cada entregable o hito debe contar con su `SPEC.md` validada contra los checklists antes de la fusión: el estudiante abre rama `feature/<tema>` + Pull Request y hace el merge él mismo una vez completos los checklists (auto-aprobación documentada, trazable y reversible). El docente audita después del merge.
