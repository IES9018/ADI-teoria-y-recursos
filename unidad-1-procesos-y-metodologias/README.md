# Unidad 1: Procesos y MetodologÔö£┬ías ├ö├ç├Â Del Vibe Coding al Spec-Driven Development (SDD)

## 1. IntroducciÔö£Ôöén
En la era de la inteligencia artificial generativa, el mayor peligro en el desarrollo de software no es escribir cÔö£Ôöédigo lento, sino construir sistemas enteros sin criterio tÔö£┬«cnico. Esta unidad aborda la transiciÔö£Ôöén crÔö£┬ítica desde la generaciÔö£Ôöén impulsiva e intempestiva (Vibe Coding) hacia el Desarrollo Dirigido por Especificaciones (Spec-Driven Development), donde el desarrollador asume la soberanÔö£┬ía y la responsabilidad de la arquitectura.

---

## 2. Conceptos Clave
* **ProgramaciÔö£Ôöén por Vibras (Vibe Coding):** PrÔö£├¡ctica de redactar requerimientos vagos en lenguaje natural, aceptar el cÔö£Ôöédigo generado por la IA sin auditorÔö£┬ía y re-generar en bucle cuando ocurren errores.
* **Desarrollo Dirigido por Especificaciones (Spec-Driven Development / SDD):** Enfoque estructurado donde primero se especifican las reglas y modelos de dominio en texto plano declarativo (`SPEC.md`) y registros de decisiÔö£Ôöén (`ADR.md`), y luego se utiliza la IA para implementar bajo esas restricciones inmutables.
* **Gobernanza del Contexto y Arneses (Harnessing):** TÔö£┬«cnica de confinamiento de modelos de IA mediante archivos de reglas locales (`.opencoderules` e `INSTRUCTIONS.md`) que imponen patrones de diseÔö£ÔûÆo, tipado estricto e inmutabilidad de contexto.
* **OpenCode (agente local de IA):** agente de codigo que trabaja sobre el repositorio respetando el arnes (`.opencoderules` e `INSTRUCTIONS.md`) y bajo supervision critica del estudiante.

---

## 3. AnalogÔö£┬ía PedagÔö£Ôöégica Cotidiana
* **El Vibe Coding es pedirle a un mozo en un restaurante:** *"Traeme algo rico"*. El resultado es azaroso, probablemente costoso y no satisface las necesidades reales.
* **El Spec-Driven Development (SDD) es el Arquitecto de Obra:** El estudiante no es el obrero que coloca ladrillos a ciegas; es el **Arquitecto** que diseÔö£ÔûÆa los planos detallados, especifica los materiales inmutables, dirige la construcciÔö£Ôöén ejecutada por la constructora (la IA) y firma la responsabilidad tÔö£┬«cnica final.
* **El ArnÔö£┬«s (`.opencoderules`) son los barandales de un puente:** Imposibilitan fÔö£┬ísica y lÔö£Ôöégicamente que la IA caiga al vacÔö£┬ío o genere estructuras fuera del Ôö£├¡rea segura autorizada.

---

## 4. Ejemplo PrÔö£├¡ctico
Supongamos la creaciÔö£Ôöén de una pantalla de autenticaciÔö£Ôöén.
* **Enfoque Vibe Coding (Incorrecto):** Copiar al chat *"HacÔö£┬« un login copado con NodeJS"*. La IA decidirÔö£├¡ la base de datos, el algoritmo de hash y el manejo de sesiones de forma arbitraria, generando deuda tÔö£┬«cnica invisible.
* **Enfoque SDD (Correcto):**
  1. Redactar `SPEC.md` definiendo variables de entrada, contrato de salida JSON, cÔö£Ôöédigos HTTP y *Non-Goals* (Ej: *"No implementar OAuth2 en esta versiÔö£Ôöén"*).
  2. Documentar en `ADR-001.md` la elecciÔö£Ôöén de JWT firmado con Ed25519.
  3. Ejecutar OpenCode bajo las reglas del arnÔö£┬«s `.opencoderules`.

---

**Diagrama ilustrativo ÔÇö Ciclo de vida SDD:**

```mermaid
flowchart TD
    A[Consigna Vaga] --> B[1. Redaccion SPEC.md]
    B --> C[2. Firma ADR.md]
    C --> D[3. Arnes .opencoderules]
    D --> E[4. Generacion OpenCode]
    E --> F[5. Auditoria Capataz]
```

---

## 5. Comparativas: Vibe Coding vs. Spec-Driven Development

| Eje | ProgramaciÔö£Ôöén por Vibras (Vibe Coding) | Desarrollo Dirigido por Especificaciones (SDD) |
| :--- | :--- | :--- |
| **Flujo de Trabajo** | Impulsivo / Prueba y error a ciegas. | 4 Pasos: Especificar (`SPEC.md`), DiseÔö£ÔûÆar (`ADR.md`), Dirigir, Auditar. |
| **Uso de Tokens** | Re-generaciÔö£Ôöén masiva e ineficiente ("Factura EconÔö£Ôöémica"). | Prompts deterministas acotados y gobernados por el arnÔö£┬«s. |
| **SoberanÔö£┬ía** | DelegaciÔö£Ôöén ciega del diseÔö£ÔûÆo en la IA ("Atrofia Cognitiva"). | El estudiante es el Arquitecto que firma la responsabilidad. |
| **DocumentaciÔö£Ôöén** | Inexistente o generada a posteriori. | Parte fundamental con **arc42** (SecciÔö£Ôöén B1), **C4 Model** (B2) y **ADRs** (B3/B4). |

---

## 6. Fuentes y Marcos de Referencia (Tabla Unificada de Recursos)
El estudiante debe consultar los siguientes marcos y bibliografÔö£┬ía obligatoria para esta unidad:
* **[B1] arc42 Framework:** Template de 12 secciones para documentar arquitectura. [arc42.org](https://arc42.org/)
* **[B2] C4 Model (Simon Brown):** VisualizaciÔö£Ôöén en 4 niveles (Contexto, Contenedores, Componentes, CÔö£Ôöédigo). [c4model.com](https://c4model.com/)
* **[B3/B4] ADR / MADR Template:** Registros ligeros de decisiones de arquitectura. [adr.github.io/madr](https://adr.github.io/madr/)
* **[B5] PlantUML / Mermaid:** GeneraciÔö£Ôöén de diagramas como cÔö£Ôöédigo versionables en Git. [mermaid.js.org](https://mermaid.js.org/)
* **[C1] Beyond Vibe Coding (Addy Osmani):** Marco de trabajo *"Plan first, code second"*. [beyond.addy.ie](https://beyond.addy.ie/)
* **[Gobernanza IES 9-018]:** Marco de gobernanza de servicios digitales del instituto. [IES9018/gobernanza-servicios-digitales](https://github.com/IES9018/gobernanza-servicios-digitales)

---

## 7. Para Practicar
1. **Ejercicio 1:** Transformar una consigna vaga (*"Un sistema de turnos para el hospital"*) en una especificaciÔö£Ôöén declarativa `SPEC.md` delimitando explÔö£┬ícitamente los *Non-Goals*.
2. **Ejercicio 2:** Configurar un archivo de arnÔö£┬«s `.opencoderules` restringiendo la IA para que utilice Ôö£Ôòænicamente sintaxis ECMAScript 2024 y proscriba el tipo `any`.
3. **Ejercicio 3:** Documentar una decisiÔö£Ôöén de base de datos SQL vs NoSQL utilizando la plantilla MADR (`ADR-001.md`).
