# Métodos de diseño de interfaces

## Introducción

Diseñar una interfaz no es "poner botones lindos". Es un proceso metódico que busca que cualquier persona pueda usar un sistema sin frustrarse. En esta unidad vas a aprender que detrás de una pantalla bien lograda hay un proceso de trabajo: se investiga al usuario, se dibujan ideas, se prueban y se vuelve a dibujar. Todo esto se conoce como **diseño centrado en el usuario** (user-centered design), y es la base de la materia.

La idea central es simple: el producto se diseña pensando en **quién lo va a usar**, no en lo que al desarrollador o al cliente le parece lindo. En este material vas a recorrer, de cero a cien, el ciclo completo: desde investigar a los usuarios, pasando por técnicas de diseño como wireframes y prototipos, hasta evaluar si la interfaz funciona de verdad con un testing de usabilidad.

## Conceptos clave

### Diseño centrado en el usuario (user-centered design)

Es un proceso de diseño que pone al usuario en el centro de todas las decisiones. No se pregunta "¿qué tecnología me gusta?", sino "¿qué necesita esta persona y cómo puedo ayudarla?". Cada decisión de diseño se valida con datos reales de usuarios, no con opiniones. El proceso se repite en ciclos: se diseña, se prueba y se ajusta.

### Guiones (scripts) y flujos de usuario (user flows)

Un **guion** describe, paso a paso y en texto, cómo un usuario realiza una tarea. Un **flujo de usuario** (user flow) es la representación visual de ese camino: una serie de pantallas y decisiones que el usuario recorre, por ejemplo, desde que entra a la aplicación hasta que completa una compra. Ayudan a detectar si hay pasos de más o de menos.

### Storyboard (guion gráfico)

Es una secuencia de viñetas, como una historieta, que muestra al usuario en su contexto usando el sistema. No se enfoca en el detalle de la pantalla, sino en el **escenario de uso**: dónde está la persona, qué siente, qué hace antes y después de usar la interfaz. Sirve para pensar el diseño en situación real.

### Wireframe (esquema de baja fidelidad)

Es el "esqueleto" de una pantalla: un dibujo simple, sin colores ni estilos, que muestra la estructura, la jerarquía y la ubicación de los elementos (dónde va el título, el menú, el botón). Se hace rápido y barato, y sirve para discutir la **estructura** antes de gastar tiempo en lo visual.

### Mockup (maqueta de media/alta fidelidad)

Es una representación estática de la pantalla con más detalle visual: colores, tipografías, imágenes y contenido real. No es interactiva: no se puede hacer clic. Se usa para validar el **aspecto visual** y para que el cliente vea cómo se va a ver el producto final.

### Prototipo interactivo (prototype)

Es una versión funcional, aunque simulada, de la interfaz. Permite hacer clic, navegar entre pantallas y "usar" el sistema aunque el backend todavía no exista. Sirve para probar la **experiencia de uso** y detectar problemas antes de programar.

### Prototipado de alta vs. baja fidelidad

La **baja fidelidad** es rápida, barata y desechable (paper prototyping, wireframes): ideal para probar ideas en etapas tempranas. La **alta fidelidad** se acerca al producto final en aspecto y comportamiento: sirve para testear decisiones finas y presentarla a stakeholders. La regla de oro es empezar por la baja y recién después subir a la alta.

### Arquitectura de la información (information architecture, IA)

Es el diseño de la **organización, etiquetado y navegación** del contenido. Responde a preguntas como: ¿cómo agrupo las secciones? ¿cómo se llama cada menú? ¿cuántos clics necesita el usuario para llegar a lo que busca? Una buena IA hace que el usuario encuentre las cosas sin pensar; una mala, lo pierde.

### Test de usabilidad (usability testing)

Consiste en observar a personas reales usando el sistema para completar tareas concretas, mientras el equipo anota dónde se traban, se confunden o abandonan. No se trata de gustos personales: se miden **hechos**. Revela los problemas reales de la interfaz.

### Inspección por heurísticas (heuristic evaluation)

Es una revisión de la interfaz hecha por **expertos**, que la evalúan contra un conjunto de reglas o "heurísticas" reconocidas (por ejemplo, las de Nielsen: visibilidad del estado del sistema, consistencia, prevención de errores, etc.). Es rápida y no requiere usuarios, pero la hacen especialistas.

### Métodos de investigación de usuarios

Son las técnicas para conocer a los usuarios antes de diseñar:

- **Entrevistas**: conversaciones uno a uno para entender necesidades y motivaciones en profundidad.
- **Cuestionarios (encuestas)**: preguntas estructuradas a muchas personas, para obtener datos cuantitativos.
- **Observación**: mirar cómo las personas hacen sus tareas en su entorno real, sin interferir, para descubrir qué hacen en lugar de qué dicen que hacen.

### Ciclo de diseño iterativo

El proceso completo: **diseñar, prototipar, evaluar y rediseñar**, repetido en vueltas. Cada vuelta mejora el diseño. Nunca se entrega "la primera idea"; se prueba, se detectan problemas y se vuelve a empezar. Es la esencia del diseño centrado en el usuario.

## Analogía

Imaginá que querés abrir un restaurante. Podrías dibujar un menú precioso con fotos, elegir los colores de las paredes y comprar mesas caras... antes de saber si a la gente le gusta la comida. Eso sería diseñar sin centrarse en el usuario.

El diseño centrado en el usuario es lo contrario: primero **investigás** a tus comensales (¿qué les gusta comer? ¿cuánto pagan?), después hacés un **menú de prueba** en papel (el wireframe), lo mostrás y probás platos sueltos (el prototipo), y cuando alguien come y te dice "esto no tiene sal" o "me perdí buscando el baño", **volvés a cocinar**. Así, varias vueltas, hasta que la experiencia sea placentera.

El testing de usabilidad es como invitar a desconocidos a comer y **observar en silencio** qué les cuesta, en vez de preguntarle a tu socio si le gustó (que siempre te va a decir que sí).

## Ejemplo práctico

Vamos a diseñar una aplicación para reservar turnos en una peluquería. El proceso completo, de cero:

1. **Investigar**: entrevistamos a 5 clientes y observamos cómo hoy reservan por WhatsApp. Descubrimos que lo que más les molesta es no saber si hay lugar y perder el turno esperando respuesta.

2. **Flujo de usuario**: dibujamos el recorrido "entrar → elegir servicio → elegir día y hora → confirmar". Detectamos que "elegir peluquero" es un paso extra que confunde, y lo quitamos.

3. **Storyboard**: dibujamos viñetas de una clienta en el trabajo, con el celular, reservando en 2 minutos mientras espera el colectivo.

4. **Wireframe**: dibujamos en papel la pantalla principal: arriba el nombre, un calendario, la lista de horarios y el botón "Confirmar". Sin colores.

5. **Mockup**: le ponemos colores de la marca, fotos de peinados y tipografías. Se lo mostramos a la dueña de la peluquería para validar el look.

6. **Prototipo interactivo**: hacemos clic entre pantallas para simular una reserva completa. Lo prueban 3 personas.

7. **Test de usabilidad**: observamos que dos personas intentaron tocar el nombre del servicio (que no era clicable) y una se confundió entre "horario" y "turno". Anotamos todo.

8. **Rediseñar**: agrandamos las zonas clicables y cambiamos la etiqueta "horario" por "elegí tu turno". Probamos de nuevo.

Cada vuelta del ciclo mejoró la aplicación, y recién cuando las personas completaban la tarea sin ayuda, se consideró lista para programar.

## Comparativas

### Wireframe vs. Mockup vs. Prototipo

| Criterio | Wireframe | Mockup | Prototipo interactivo |
|:---------|:----------|:-------|:----------------------|
| Fidelidad | Baja | Media / alta | Baja a alta (según etapa) |
| Contenido | Estructura y jerarquía | Visual: colores, tipografía | Comportamiento y navegación |
| Interactivo | No | No | Sí |
| Costo / tiempo | Muy bajo | Medio | Alto |
| Para qué sirve | Definir estructura y ubicación | Validar el aspecto visual | Probar la experiencia de uso |

### Baja fidelidad vs. Alta fidelidad

| Criterio | Baja fidelidad | Alta fidelidad |
|:---------|:---------------|:---------------|
| Ejemplos | Paper prototyping, wireframes | Mockups, prototipos funcionales |
| Rapidez | Muy rápida | Lenta |
| Costo | Barata | Cara |
| Detalle | Esquemático | Cercano al producto final |
| Momento del proceso | Etapas tempranas | Etapas avanzadas |
| Riesgo de feedback | La gente critica la idea | La gente critica detalles visuales |

## Fuentes

### Nielsen Norman Group — "Usability 101" (inglés)

https://www.nngroup.com/articles/usability-101-introduction-to-usability/

Texto de referencia para entender el concepto de usabilidad, sus cinco componentes (learnability, efficiency, memorability, errors, satisfaction) y por qué el diseño centrado en el usuario mejora la experiencia.

### Nielsen Norman Group — "Wireframes" / prototipado (inglés)

https://www.nngroup.com/articles/wireframes/

Explica qué son los wireframes, en qué etapa del proceso se usan, su rol en la estructura de la información y su relación con el prototipado de baja fidelidad.

### Usability.gov — "User Experience (UX) Basics" (inglés, gobierno de EE.UU.)

https://www.usability.gov/what-and-why/user-experience.html

Presenta los fundamentos de la experiencia de usuario y el proceso de diseño centrado en el usuario, incluyendo la investigación y la evaluación.

## Para practicar

1. Elegí una app que uses a diario (una de compras, de mensajería o de transporte) y dibujá a mano alzada, en papel, un **wireframe** de su pantalla principal. No copies los colores: solo la estructura.

2. Tomá ese mismo wireframe y dibujá el **flujo de usuario** para completar una tarea simple, por ejemplo "hacer una reserva" o "enviar un mensaje". Contá los pasos: ¿te parece que hay pasos de más?

3. Inventá un **cuestionario** de 5 preguntas para conocer a los posibles usuarios de una app de tu barrio. ¿Qué le preguntarías para saber si la usarían?

4. Hacé un **test de usabilidad casero**: pedile a un compañero o familiar que use una app que vos no conocés para completar una tarea. Observá en silencio, no lo ayudes, y anotá dónde se detuvo o se confundió. Eso son tus datos de evaluación.

5. Usá las tres heurísticas de Nielsen que te resulten más claras (por ejemplo, visibilidad del estado del sistema, consistencia y prevención de errores) y evaluá la pantalla que dibujaste en el punto 1: ¿cumple o viola cada una? Fundamentá.

6. Reflexioná: ¿en qué parte del **ciclo de diseño iterativo** (diseñar, prototipar, evaluar, rediseñar) te resultaría más tentador saltarte pasos? ¿Qué riesgos tiene saltarse la evaluación antes de programar?
