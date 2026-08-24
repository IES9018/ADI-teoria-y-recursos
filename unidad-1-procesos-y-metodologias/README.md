# Unidad 1: Procesos y Metodologías — Del Vibe Coding al Spec-Driven Development (SDD)

## 1. Metadata y Contexto Cátedra
- **Materia:** Arquitectura y Diseño de Interfaces (ADI) - Ciclo Lectivo 2026
- **Unidad Didáctica:** Unidad 1 - Procesos y Metodologías
- **Ruta Destino Repo:** `ADI-teoria-y-recursos/unidad-1-procesos-y-metodologias/README.md`
- **Enfoque Pedagógico:** Sustitución de la generación impulsiva ("Vibe Coding") por el Desarrollo Dirigido por Especificaciones (Spec-Driven Development) y uso de Arneses de Control (Harnessing).
- **Prerrequisito Conceptual:** Modelado de Software (2025).

---

## 2. Objetivos de Aprendizaje
* **Diferenciar** operativamente el *Vibe Coding* del *Spec-Driven Development* (SDD) evaluando costos computacionales, deuda técnica y soberanía del desarrollador.
* **Diseñar** documentos de especificación declarativa (`SPEC.md`) y registros de decisiones arquitectónicas (`ADR.md`) previos a la fase de codificación.
* **Configurar** arneses de contexto y restricciones para LLMs (`.opencoderules`, `INSTRUCTIONS.md`) que restrinjan la generación de código al ámbito del diseño definido.
* **Asumir** la Metáfora del Arquitecto: el estudiante actúa como supervisor crítico y firmante de la responsabilidad técnica, no como un mero ejecutor pasivo.

---

## 3. Matriz de Contenidos Teóricos

| Eje Temático | Vibe Coding (Patrón Antagónico) | Spec-Driven Development (Patrón Objetivo) |
| :--- | :--- | :--- |
| **Flujo de Trabajo** | Generación por impulsos en lenguaje natural; aceptación ciega del output sin auditoría técnica. | Proceso en 4 pasos: Especificar (`SPEC.md`), Diseñar (`ADR.md`), Dirigir (Prompting acotado), Revisar (Code Review). |
| **Gestión de Errores** | Regeneración en bucle estilo "Tragaperras" (copiar/pegar la traza de error en la IA). | Depuración estructurada con hipótesis explicativas, aislamiento de variables y lecturas de logs. |
| **Control de Contexto** | Prompts masivos sin estructura; consumo ineficiente e ilimitado de tokens por falta de límites. | Gobernanza del contexto mediante archivos de arnés (`.opencoderules` / `INSTRUCTIONS.md`) con reglas inmutables. |
| **Evaluación del Código** | Aceptación si el sistema "parece funcionar" visualmente. | Defensa técnica del *porqué* de la arquitectura elegida y cumplimiento estricto de la especificación. |

---

## 4. Las 3 Facturas del Vibe Coding
1. **Factura Económica (Degradación de Tokens):** La regeneración impulsiva consume la ventana de contexto de los modelos, diluyendo la precisión y generando costos innecesarios en cómputo.
2. **Deuda Técnica Invisible:** El código aceptado sin revisión profunda introduce vulnerabilidades de seguridad, acoplamiento alto y problemas de escalabilidad que fallan en producción.
3. **Atrofia Cognitiva y Estancamiento:** Delegar el diseño lógico a la IA impide la consolidación del criterio técnico indispensable para ejercer la profesión.

---

## 5. Protocolo de Trabajo en Aula: Flujo SDD
- Creación directa del repositorio del alumno en la Org `IES9018` bajo el formato `<nombre_alumno>-<nombre_proyecto>`.
- Configuración inicial de arneses locales (`.opencoderules` / `INSTRUCTIONS.md`).
- Redacción de especificaciones de diseño (`SPEC.md`) antes de invocar herramientas de generación como OpenCode.
- Revisión del docente bajo la figura de Capataz/Arquitecto mediante apertura de Issues y Code Reviews sobre la organización.
