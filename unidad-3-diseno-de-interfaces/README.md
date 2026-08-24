# Unidad 3: Dise├▒o de Interfaces ÔÇö HCI, Usabilidad y Sistemas de Dise├▒o

---

## 1. Introducci├│n
Una interfaz no se dise├▒a para quedar bonita en el portfolio: se dise├▒a para que una persona concreta logre su objetivo con la menor fricci├│n posible. La Interacci├│n Humano-Computadora (HCI) aporta d├®cadas de evidencia sobre c├│mo percibimos, decidimos y nos equivocamos frente a una pantalla. Esta unidad traduce esa evidencia en decisiones verificables: wireframes que prueban estructura, prototipos que prueban flujo, y sistemas de dise├▒o que evitan reinventar un bot├│n en cada pantalla.

---

## 2. Conceptos Clave
* **HCI (Human-Computer Interaction):** Disciplina que estudia c├│mo las personas usan sistemas computacionales y c├│mo dise├▒ar para minimizar error y esfuerzo.
* **Usabilidad:** Eficacia, eficiencia y satisfacci├│n con las que un usuario logra sus objetivos (ISO 9241). Medible, no decorativa.
* **Ergonom├¡a de Software:** Adaptar la interfaz a las capacidades humanas: memoria de trabajo limitada, objetivos de toque (44px), jerarqu├¡a visual.
* **UX vs UI:** UX es la experiencia completa del recorrido (antes, durante y despu├®s del uso); UI es la capa visible e interactiva. Una UI linda puede sostener una UX p├®sima.
* **Wireframe:** Boceto de baja fidelidad que define estructura y jerarqu├¡a sin dise├▒o visual.
* **Mockup:** Representaci├│n est├ítica de alta fidelidad: colores, tipograf├¡a, componentes finales.
* **Prototipo:** Versi├│n navegable que simula el flujo real para testear antes de programar.
* **Responsive Design:** Una misma interfaz que se adapta a viewport distintos mediante grillas flexibles, media queries e im├ígenes fluidas.
* **Sistema de Dise├▒o:** Biblioteca de tokens (colores, espaciados, tipograf├¡a) + componentes reutilizables + reglas de uso.

---

## 3. Analog├¡a Pedag├│gica Cotidiana
* **La interfaz es el tablero de mandos de un autom├│vil:** los pedales van siempre a la izquierda/derecha, el volante al centro, la bocina al alcance del pulgar. Nadie "redise├▒a" esa posici├│n en cada auto porque millones de conductores ya la aprendieron: la ergonom├¡a prevalece sobre la creatividad del dise├▒ador.
* **Un wireframe es el croquis con palitos de la distribuci├│n del muebles; el mockup, la foto renderizada del ambiente; y el prototipo, recorrer la casa modelada en 3D antes de construirla.**

---

## 4. Ejemplo Pr├íctico
**Consigna:** checkout mobile accesible para una tienda online.
1. **Wireframe:** pantalla ├║nica con resumen de carrito arriba, formulario reducido a 3 campos visibles, bot├│n fijo de confirmaci├│n abajo (thumb zone).
2. **Accesibilidad desde el dise├▒o:** contraste m├¡nimo 4.5:1 (WCAG 2.2 AA) entre texto y fondo; ├írea t├íctil ÔëÑ 44├ù44px; etiquetas siempre visibles, nunca solo placeholders.
3. **Estados obligatorios:** vac├¡o, cargando (skeleton/spinner + bot├│n deshabilitado), error de pago con mensaje accionable ("Revis├í los datos de la tarjeta"), ├®xito con confirmaci├│n clara.
4. **Prueba:** prototipo navegable testeado con 5 usuarios; si m├ís de uno duda d├│nde pagar, se redise├▒a antes de escribir c├│digo.

---

**Diagrama ilustrativo — Estados obligatorios de un componente UI:**

```mermaid
stateDiagram-v2
    [*] --> Idle
    Idle --> Loading : accion del usuario
    Loading --> Success : respuesta OK
    Loading --> Error : fallo o timeout
    Error --> Loading : reintento
    Success --> [*]
```

---

## 5. Tabla Comparativa: Wireframe vs. Mockup vs. Prototipo

| Eje | Wireframe (Baja Fidelidad) | Mockup (Media/Alta Est├ítica) | Prototipo (Alta Fidelidad Interactiva) |
| :--- | :--- | :--- | :--- |
| **Qu├® define** | Estructura y jerarqu├¡a | Aspecto visual final | Flujo y comportamiento |
| **Tiempo de producci├│n** | Minutos | Horas | HorasÔÇôd├¡as |
| **Herramientas t├¡picas** | Papel, Excalidraw, Balsamiq | Figma (dise├▒o) | Figma (prototyping), Storybook |
| **Feedback que obtiene** | "┬┐Est├í todo lo necesario?" | "┬┐Se ve y se lee bien?" | "┬┐El recorrido funciona?" |
| **Cu├índo usarlo** | Siempre, primero | Tras validar estructura | Antes de estimar/programar |

---

## 6. Fuentes y Marcos de Referencia (Tabla Unificada)
* **[Nielsen Norman Group]** Las 10 heur├¡sticas de usabilidad de Jakob Nielsen: [nngroup.com/articles/ten-usability-heuristics](https://www.nngroup.com/articles/ten-usability-heuristics/)
* **[WCAG 2.2]** Est├índar W3C de accesibilidad de contenido web: [w3.org/TR/WCAG22](https://www.w3.org/TR/WCAG22/)
* **[Refactoring UI]** Wathan & Schoger ÔÇö decisiones visuales pr├ícticas para desarrolladores: [refactoringui.com](https://www.refactoringui.com/)
* **[Material Design 3 / Apple HIG]** Sistemas de dise├▒o de referencia de las dos plataformas dominantes: [m3.material.io](https://m3.material.io/) ┬À [developer.apple.com/design](https://developer.apple.com/design/human-interface-guidelines/)

---

## 7. Para Practicar (con R├║brica de Auditor├¡a)
1. **Ejercicio 1 ÔÇö Auditor├¡a heur├¡stica:** Eleg├¡ una app real de uso masivo (banco, delivery, turnos) y evalu├í 5 pantallas contra las 10 heur├¡sticas de Nielsen. Entregable: tabla hallazgo ÔåÆ heur├¡stica violada ÔåÆ severidad ÔåÆ propuesta de correcci├│n.
2. **Ejercicio 2 ÔÇö UI Tokens en SPEC.md:** Especific├í en tu `SPEC.md` los tokens del sistema de dise├▒o de tu proyecto: paleta con contraste validado WCAG AA, escala tipogr├ífica, espaciados (m├║ltiplos de 4/8px), radios y estados de cada componente interactivo (default/hover/focus/disabled/error).
