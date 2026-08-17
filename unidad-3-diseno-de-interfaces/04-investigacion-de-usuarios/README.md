# Investigación de usuarios (User Research)

## Introducción

Imaginá que tenés que diseñar una cocina para un restaurante. Si nunca hablás con los cocineros, si no sabés cómo trabajan, qué utensilios usan, en qué orden hacen las cosas, qué les molesta del espacio actual... cualquier diseño que hagas va a ser una apuesta a ciegas. Podés hacerla muy linda, muy moderna, con los mejores materiales, pero si no se adapta a la forma real de trabajar de la gente, va a ser un fracaso.

Con el software pasa exactamente lo mismo. **La investigación de usuarios (user research)** es el proceso de entender quiénes son las personas que van a usar nuestro sistema, qué necesitan, qué problemas tienen y cómo se comportan. Es el primer paso, y quizá el más importante, del diseño centrado en el usuario: una filosofía que pone a las personas en el centro de todo el proceso de diseño, en lugar de diseñar "por intuición" o "porque el cliente lo pidió".

En esta unidad vamos a recorrer los métodos que existen para investigar, cuándo usar cada uno, cómo hacer una buena entrevista sin meter la pata, y cómo transformar todo lo que aprendemos en herramientas concretas: personas, escenarios y mapas de viaje.

## Conceptos clave

### Diseño centrado en el usuario (User Centered Design, UCD)

Es la idea madre de todo este tema. Consiste en que cada decisión de diseño se toma pensando en los usuarios finales: sus objetivos, sus limitaciones, sus contextos. La investigación de usuarios es el motor que alimenta este enfoque: sin datos reales de usuarios, no hay diseño centrado en el usuario, hay diseño centrado en la suposición.

### Investigación de usuarios (User Research)

Es el proceso sistemático de recolectar información sobre los usuarios y sus necesidades para guiar las decisiones de diseño. Puede hacerse al inicio de un proyecto (para entender el problema), durante el desarrollo (para validar ideas) o al final (para evaluar si se logró el objetivo). La investigación no es opcional: es la base sobre la que se construye todo lo demás.

### Métodos cualitativos (Qualitative methods)

Buscan el "porqué" y el "cómo": entender las motivaciones, emociones y razones detrás de los comportamientos. Trabajan con pocos participantes pero en profundidad. Los datos no se miden numéricamente, se interpretan.

- **Entrevistas en profundidad**: conversaciones uno a uno, guiadas por preguntas abiertas, para entender la experiencia, motivaciones y frustraciones de una persona. Es el método más usado para arrancar una investigación.
- **Grupos focales (focus groups)**: una sesión moderada con un grupo pequeño de personas (entre 6 y 10) que discuten un tema. Útil para explorar percepciones y generar ideas, aunque tiene limitaciones: la opinión de uno puede influenciar a los demás.
- **Observación etnográfica (ethnographic observation)**: el investigador observa a los usuarios en su entorno real de trabajo, sin intervenir. Sirve para ver lo que la gente realmente hace, que muchas veces no coincide con lo que dice que hace.
- **Estudio de casos (case studies)**: análisis profundo de un caso particular (una persona, una organización, un proceso) para extraer aprendizajes que se puedan generalizar. Muy útil en contextos específicos o industrias concretas.

### Métodos cuantitativos (Quantitative methods)

Buscan el "cuánto" y el "cuántos": medir magnitudes, frecuencias y porcentajes. Trabajan con muchas muestras y producen datos numéricos que se pueden analizar estadísticamente.

- **Encuestas y cuestionarios (surveys)**: preguntas estandarizadas aplicadas a muchas personas. Sirven para validar, a gran escala, lo que ya se descubrió de forma cualitativa, o para medir satisfacción.
- **Análisis de datos de uso (analytics)**: estudiar los datos que deja el sistema: qué botones se tocan, dónde se quedan los usuarios, dónde abandonan. Es investigación a partir de la evidencia real de uso.
- **Pruebas A/B (A/B testing)**: se muestran dos versiones de un diseño a dos grupos y se mide cuál funciona mejor según una métrica definida (por ejemplo, más clics o más ventas). Excelente para optimizar decisiones concretas.

### Personas (User personas)

Son personajes ficticios pero basados en datos reales de la investigación, que representan a los distintos tipos de usuarios de un producto. Cada persona tiene nombre, edad, perfil, objetivos, frustraciones y contexto. Sirven para que todo el equipo diseñe pensando en personas concretas y no en un vago "usuario promedio". Nielsen Norman Group las define como una herramienta central del diseño centrado en el usuario.

### Escenarios de uso (Use scenarios)

Son descripciones narrativas de cómo una persona determinada usaría el sistema para lograr un objetivo concreto. Combinan una persona con un contexto y una tarea: "María, que maneja un comercio, quiere generar la factura de un cliente desde su teléfono". Ayudan a evaluar si el diseño funciona en situaciones reales.

### Mapa de viaje del usuario (User journey map)

Es una representación visual de los pasos que atraviesa un usuario para lograr un objetivo con un producto o servicio, incluyendo sus emociones en cada etapa: qué piensa, qué siente, qué hace, qué toca y qué puntos de dolor (frustraciones) encuentra. Su utilidad es enorme: permite ver el proceso completo y detectar dónde se pierde gente o dónde la experiencia se rompe.

### Toma de requisitos (Requirements gathering)

Es el proceso de convertir lo aprendido en la investigación en requerimientos concretos del sistema: qué funcionalidades necesita, bajo qué condiciones, para qué tipo de usuario. La investigación de usuarios alimenta directamente este proceso: primero entendemos al usuario, después escribimos los requisitos.

## Analogía

Pensá en un médico. Cuando llega un paciente, el médico no receta un remedio sin antes preguntar, escuchar y hacer estudios. Si recetara a ciegas, "porque casi siempre funciona", sería un desastre. La investigación de usuarios es la consulta médica del diseño: es el momento de escuchar al paciente (el usuario), entender sus síntomas (sus necesidades y frustraciones) y recién después recetar el tratamiento (el diseño del sistema).

Y los métodos son las distintas herramientas del médico: la entrevista en profundidad es el interrogatorio clínico, cara a cara; la encuesta es la estadística de salud pública, que dice cuántas personas en general padecen tal cosa; el análisis de datos de uso es el electrocardiograma, que muestra qué está pasando en tiempo real con el corazón del sistema. Ninguna herramienta reemplaza a las demás: cada una responde una pregunta distinta.

## Ejemplo práctico

Imaginemos que la Tecnicatura quiere rediseñar la plataforma que los estudiantes usan para anotarse a los exámenes finales.

**Paso 1 - Investigación cualitativa.** Entrevistamos en profundidad a cinco estudiantes de distintos años. Descubrimos que muchos se anotan de noche desde el celular, que se frustran cuando el sistema no les muestra si ya rindieron esa materia, y que algunos abandonan el proceso porque no encuentran la pestaña correcta. También hacemos observación etnográfica: miramos cómo un estudiante se anota en su casa, y confirmamos que usa el celular y que se confunde con el menú.

**Paso 2 - Validación cuantitativa.** Con esos hallazgos, lanzamos una encuesta a todos los estudiantes del instituto. Confirmamos que el 70% usa el celular para anotarse y que el 55% "no encuentra fácil la opción". Los datos cualitativos y cuantitativos se refuerzan mutuamente.

**Paso 3 - Personas.** Creamos la persona "Ezequiel, estudiante de 2do año, 22 años, trabaja de día, se anota de noche desde el celular, se frustra cuando no ve su historial de materias". Todo el equipo diseña pensando en Ezequiel.

**Paso 4 - Escenarios y journey map.** Dibujamos el recorrido de Ezequiel: "abre la app, busca la materia, se anota, recibe confirmación". En el mapa de viaje marcamos sus emociones y detectamos el punto de dolor en el menú, justo donde confirmó la observación etnográfica.

**Paso 5 - Toma de requisitos.** De todo esto salen requisitos concretos: "el sistema debe mostrar el historial de materias rendidas" y "el proceso de anotación debe completarse desde un dispositivo móvil". Sin la investigación, esos requisitos jamás habrían aparecido: son el fruto directo de escuchar al usuario.

## Comparativas

### Cualitativo vs cuantitativo

| Aspecto | Cualitativo | Cuantitativo |
|---------|-------------|--------------|
| Pregunta que responde | ¿Por qué? ¿Cómo? | ¿Cuánto? ¿Cuántos? |
| Tipo de datos | Palabras, observaciones, historias | Números, porcentajes, estadísticas |
| Cantidad de participantes | Pocos (5 a 15) | Muchos (decenas a miles) |
| Profundidad | Alta, en cada persona | Baja, en cada persona |
| Métodos típicos | Entrevista, focus group, observación, caso | Encuesta, analytics, prueba A/B |
| Momento ideal | Descubrir problemas e hipótesis | Validar y medir |
| Interpretación | Subjetiva, requiere análisis del investigador | Objetiva, se procesa estadísticamente |

La regla práctica: primero cualitativo para entender el problema, después cuantitativo para validar su magnitud.

### Entrevista vs encuesta

| Aspecto | Entrevista | Encuesta |
|---------|------------|----------|
| Formato | Conversación uno a uno | Cuestionario estandarizado |
| Profundidad | Alta, se puede indagar | Baja, respuestas fijas |
| Preguntas | Abiertas | Cerradas o de opción múltiple |
| Cantidad de personas | Pocas | Muchas |
| Costo y tiempo | Alto | Bajo |
| Mejor para | Descubrir motivaciones | Medir frecuencia o satisfacción |

## Fuentes

Estas son las fuentes autoritativas que usamos para este material. Te recomiendo leerlas porque profundizan cada concepto con ejemplos reales.

### Nielsen Norman Group - "Personas"

https://www.nngroup.com/articles/persona/

Artículo de referencia mundial sobre la creación y el uso de personas (user personas) en diseño centrado en el usuario. Explica qué son, para qué sirven, cómo construirlas a partir de investigación real y los errores más comunes (como crear personas inventadas, sin base en datos).

### Usability.gov - "User Research"

https://www.usability.gov/how-to-and-tools/methods/user-research.html

Guía del gobierno de los Estados Unidos sobre investigación de usuarios. Describe los métodos cualitativos y cuantitativos, cuándo aplicarlos y cómo encajan en el proceso de diseño. Excelente para repasar la clasificación que vimos acá.

### Nielsen Norman Group - "How to Conduct User Interviews"

https://www.nngroup.com/articles/user-interviews/

Guía práctica para conducir entrevistas con usuarios: cómo prepararlas, cómo formular buenas preguntas y cómo evitar los errores clásicos, incluidas las preguntas sesgadas o inductivas que llevan al usuario a responder lo que "se espera" en lugar de lo que realmente piensa.

## Para practicar

1. **Clasificá los métodos.** Para cada situación, indicá si usarías un método cualitativo o cuantitativo y justificá: (a) querés saber si el 60% de los usuarios abandona el carrito de compras; (b) querés entender por qué lo abandonan; (c) querés verificar si un botón rojo genera más clics que uno azul; (d) querés explorar cómo los contadores de una empresa llevan su registro de gastos.

2. **Detectá la pregunta sesgada.** De esta lista, marcá cuáles son preguntas sesgadas o inductivas y reescribilas para que sean neutras: (a) "¿Te resulta difícil usar nuestra app?"; (b) "¿Qué tan complicado te resultó encontrar el botón de pagar?"; (c) "¿Usás nuestra app todos los días?"; (d) "Contame cómo fue tu última experiencia comprando online". Acordate de lo que vimos: las preguntas no deben sugerir la respuesta.

3. **Armá una persona.** Elegí un producto que uses seguido (una app de delivery, una red social, una plataforma de video). Definí dos personas distintas que lo usen, con nombre, edad, perfil, objetivos y frustraciones. Justificá cada dato con una observación o experiencia real (aunque sea propia).

4. **Dibujá un journey map.** Para una de las personas del punto anterior, trazó los pasos que atraviesa para lograr un objetivo con ese producto. En cada etapa anotá qué hace, qué piensa y qué siente, y marcá los puntos de dolor. Después señalá en qué etapa se podría mejorar la experiencia.

5. **Entrevista real.** Prepará una entrevista de 10 preguntas abiertas sobre un tema cotidiano (por ejemplo, cómo la gente organiza su agenda). Entrevistá a un compañero, grabá las respuestas y luego escribí 3 conclusiones que saques de esa conversación. Practicá hacer preguntas de seguimiento ("¿por qué?", "¿me das un ejemplo?") para profundizar.
