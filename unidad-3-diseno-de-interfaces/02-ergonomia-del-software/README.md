# Ergonomía del software

## Introducción

Cuando pensamos en la palabra "ergonomía", la mayoría se imagina sillas ajustables, teclados ergonómicos o la altura correcta del monitor. Y sí, eso es parte, pero es solo una cara de la moneda. La ergonomía, en su definición más amplia, es la disciplina que estudia cómo adaptar un producto, sistema o entorno a las capacidades y limitaciones de las personas que lo usan. El objetivo es simple: que la herramienta se adapte al humano, y no al revés.

Ahora, ¿qué pasa cuando la "herramienta" es un software? El problema ya no es solo físico (que no te duela la muñeca), sino mental. Cuando interactuamos con una aplicación, nuestro cerebro tiene que procesar muchísima información: entender qué estamos viendo, recordar dónde estaba ese botón, decidir qué opción elegir, interpretar si la acción se hizo bien o mal. Todo eso es un esfuerzo mental que, si se vuelve demasiado grande, nos frustra y nos hace abandonar la aplicación.

En este material vamos a recorrer la **ergonomía del software** (también llamada ergonomía de la interfaz o ergonomía cognitiva) de cero a cien. Vamos a entender por qué una interfaz "se siente" fácil o difícil de usar, qué dice la ciencia sobre cómo procesamos la información, y qué principios concretos podemos aplicar para diseñar interfaces que respeten la mente del usuario. Además, cerraremos con la accesibilidad, que es la ergonomía llevada a su máxima expresión: que el software pueda usarlo la mayor cantidad de personas posible, incluidas aquellas con algún tipo de discapacidad.

## Conceptos clave

### ¿Qué es la ergonomía (ergonomics)?

La ergonomía es la disciplina científica que se ocupa de la interacción entre los seres humanos y los demás elementos de un sistema. Su propósito es optimizar el bienestar humano y el rendimiento general del sistema. En pocas palabras: estudia cómo el entorno y las herramientas deben diseñarse para que resulten cómodas, seguras y eficientes para quien las utiliza.

### Ergonomía física vs ergonomía cognitiva del software

Cuando hablamos de ergonomía, distinguimos dos grandes ramas:

- **Ergonomía física:** se ocupa de las características anatómicas y fisiológicas del cuerpo humano. En software, se relaciona con el hardware que rodea a la aplicación: el tamaño de los botones que hay que tocar en una pantalla táctil, el contraste que afecta a la vista, evitar movimientos innecesarios del mouse, la posición del teclado, el tamaño de la letra. Es la "silla cómoda" del mundo digital.

- **Ergonomía cognitiva:** se ocupa de los procesos mentales: percepción, memoria, razonamiento y respuesta motora. En software, es la que estudia cómo el diseño de la interfaz afecta la carga mental del usuario. Se pregunta: ¿le cuesta entender lo que ve? ¿tiene que recordar demasiadas cosas? ¿se confunde con las opciones? Esta es la rama que nos va a ocupar la mayor parte del material.

Un buen ejemplo para diferenciarlas: la ergonomía física te diría "este botón es muy chico para un dedo", mientras que la cognitiva te diría "el usuario no sabe para qué sirve este botón porque no está bien etiquetado".

### Esfuerzo mental y carga cognitiva (cognitive load)

La **carga cognitiva** es la cantidad total de esfuerzo mental que se utiliza en la memoria de trabajo para procesar una tarea. Imaginate que tu cerebro tiene un "presupuesto" limitado de atención que puede repartir por minuto. Si la interfaz obliga al usuario a usar demasiado de ese presupuesto en cosas triviales (buscar un botón, descifrar un icono raro, recordar un dato de otra pantalla), queda poco para la tarea real que quiere hacer.

La teoría de la carga cognitiva distingue tres tipos:
- **Intrínseca:** la complejidad propia de la tarea. No se puede eliminar, solo gestionar.
- **Extrínseca:** la carga impuesta por cómo está presentada la información. Esta es la que un buen diseño debe minimizar.
- **Germana:** la que se dedica a aprender y construir conocimiento nuevo. Cuando la extrínseca es alta, la germana no puede desarrollarse.

### Memoria de trabajo

La **memoria de trabajo** es el sistema cognitivo que nos permite mantener y manipular información de forma temporal mientras realizamos una tarea. Es como el "escritorio" de nuestra mente: un lugar donde apoyamos las cosas que estamos usando en este momento. El problema es que ese escritorio es muy chico. La investigación clásica indica que podemos mantener cómodamente alrededor de 4 a 7 elementos a la vez, y por muy poco tiempo.

Por eso el diseño debe respetar la memoria de trabajo: no obligar al usuario a recordar información de una pantalla para usarla en otra, mostrar opciones visibles en lugar de pedir que las recuerde, y descomponer tareas complejas en pasos más simples.

### Ley de Fitts

La **ley de Fitts** establece una relación matemática entre el tiempo que tarda una persona en moverse hacia un objetivo y dos variables: el **tamaño** del objetivo y la **distancia** hasta él. La fórmula dice, en esencia: a mayor tamaño del objetivo y menor distancia hasta él, más rápido y más fácil es hacer clic o tocar. Es una ley de la ergonomía física con consecuencias cognitivas claras.

Sus implicancias prácticas son muy conocidas: los botones de acción principal deben ser grandes, los elementos que se usan juntos deben estar cerca, y los elementos pequeños (como botones de cierre o enlaces) deben tener suficiente área para no frustrar al usuario.

### Ley de Hick

La **ley de Hick** establece que el tiempo que tarda una persona en tomar una decisión aumenta a medida que crece el número y la complejidad de las opciones disponibles. Es decir: cuantas más opciones le mostramos al usuario, más lento se vuelve para elegir.

La aplicación práctica es clara: no saturar la interfaz con demasiadas opciones a la vez. Si son necesarias muchas, conviene agruparlas, jerarquizarlas o esconder las menos usadas. La ley explica por qué "menos es más" cuando de menús y botoneras se trata.

### Principio de proximidad

El **principio de proximidad** (parte de la Ley de la Proximidad de la Gestalt) establece que los elementos que están cerca unos de otros tendemos a percibirlos como parte del mismo grupo. Es una de las leyes de la percepción visual: nuestro cerebro agrupa automáticamente lo que está juntico. Por eso, en una interfaz, los controles relacionados deben estar visualmente cerca, y separados con espacio de los que no tienen relación.

### Contraste y agrupamiento visual

El **contraste** es la diferencia perceptible entre un elemento y su entorno. Un buen contraste (por ejemplo, entre texto y fondo) hace que la información sea legible y que los elementos importantes "salten a la vista". Sin contraste, todo se funde en una mancha gris y el usuario no sabe qué mirar.

El **agrupamiento visual** se apoya en la proximidad, el contraste y otros principios para crear bloques visuales con significado. Agrupar visualmente los campos de un formulario según su función (datos personales, datos de pago, etc.) reduce el esfuerzo de comprensión.

### Consistencia

La **consistencia** es el principio que dice que elementos similares deben comportarse de manera similar, y que la interfaz debe mantener patrones uniformes en toda la aplicación. Si un botón verde en una pantalla significa "confirmar", en todas las demás pantallas debe significar lo mismo. Si los botones de acción están siempre en el mismo lugar, el usuario aprende el patrón y ya no tiene que pensar. La consistencia reduce la carga cognitiva porque el usuario "recicla" lo que ya aprendió.

### Retroalimentación (feedback)

La **retroalimentación** es la respuesta que la interfaz le da al usuario después de una acción. Cada acción debe tener una respuesta visible: un botón que se presiona, un mensaje de "guardado", un cambio de color, una animación. Sin feedback, el usuario no sabe si su acción funcionó y queda en la incertidumbre, lo que genera ansiedad y errores. La regla de oro: a cada acción del usuario, corresponde una reacción del sistema.

### Prevención de errores

La **prevención de errores** es mejor que el mensaje de error. Un buen diseño anticipa dónde el usuario podría equivocarse y lo evita antes de que ocurra: por ejemplo, usando listas desplegables en lugar de campos de texto libres, confirmando acciones destructivas, o bloqueando botones "enviar" hasta que el formulario esté completo. Cuando el error no se puede evitar, el sistema debe ofrecer un mensaje claro que explique qué pasó y cómo corregirlo.

### Accesibilidad (accessibility)

La **accesibilidad** es la práctica de hacer que los productos y servicios digitales puedan ser utilizados por la mayor cantidad de personas posible, incluidas las personas con discapacidades (visuales, auditivas, motoras, cognitivas). No es un extra opcional: es parte esencial de la ergonomía, porque se trata de adaptar el software a las capacidades humanas en toda su diversidad.

El estándar de referencia internacional es el **WCAG** (Web Content Accessibility Guidelines, Pautas de Accesibilidad para el Contenido Web), publicado por el W3C. Se organiza en cuatro principios fundamentales: **Perceptible** (la información debe poder percibirse), **Operable** (la interfaz debe poder usarse), **Comprensible** (la información y el funcionamiento deben ser comprensibles) y **Robusto** (el contenido debe funcionar con distintas tecnologías y agentes de usuario). Dentro de cada principio hay pautas y criterios de conformidad con niveles A, AA y AAA.

## Analogía

Pensemos en la ergonomía del software como el diseño de una cocina profesional.

La **ergonomía física** sería que la mesada esté a la altura justa, que la heladera no esté a diez metros de la zona de preparación y que los utensilios tengan mangos cómodos. Si la cocina está mal diseñada físicamente, el cocinero se cansa, pierde tiempo y hasta se lastima.

La **ergonomía cognitiva** sería el orden mental de la cocina. Si cada cuchillo está en un lugar distinto según el día, si las especias no tienen etiqueta y si hay cincuenta sartenes iguales apilados sin orden, el cocinero pierde tiempo buscando, se distrae y arruina la receta. Eso es exactamente la **carga cognitiva**: el esfuerzo mental extra que se gasta en buscar y decidir en lugar de cocinar.

La **memoria de trabajo** es como ese mesón de trabajo reducido: el cocinero solo puede tener "en la cabeza y a mano" unas pocas cosas a la vez. Si le pedís que recuerde la receta completa de memoria mientras busca ingredientes, se le va a caer todo.

La **Ley de Fitts** es como tener los utensilios que más usa el cocinero grandes, a la vista y cerca de la mano. La **Ley de Hick** es como el menú de la carta: si tiene quinientos platos, el cliente tarda una eternidad en elegir; si tiene ocho bien explicados, elige rápido. La **consistencia** es que el fuego siempre se prenda girando la perilla igual, y el **feedback** es que el horno te avise con un sonido cuando llegó a temperatura. Y la **accesibilidad** es diseñar esa cocina para que también pueda usarla una persona con movilidad reducida o con baja visión.

## Ejemplo práctico

Vamos a aplicar todo esto a un caso concreto: el diseño de un formulario de compra en una tienda online.

**Ergonomía física y ley de Fitts:** el botón "Completar compra" debe ser grande, de alto contraste y ubicado cerca de los campos que el usuario acaba de llenar. Un botón chiquito, gris y escondido al final de la página viola la ley de Fitts: es un objetivo pequeño y lejano, difícil de alcanzar.

**Carga cognitiva y memoria de trabajo:** no obliguemos al usuario a recordar el código de descuento de un correo mientras completa los datos de envío. Mejor, ofrezcamos un campo con ayuda o pre-validemos que el código esté bien. Si la compra tiene varios pasos, mostremos una barra de progreso: esto da una "hoja de ruta" y reduce la incertidumbre, evitando que el usuario deba mantener en la memoria dónde está parado.

**Ley de Hick:** en vez de un menú desplegable con cuarenta países, agrupemos por región o usemos un buscador. Cuantas menos opciones visibles, más rápida la decisión.

**Proximidad, contraste y agrupamiento visual:** agrupemos visualmente los campos en bloques ("Datos personales", "Datos de envío", "Datos de pago") separados con espacio. Resaltemos con contraste el botón principal de acción para que sea lo primero que la vista encuentre.

**Consistencia:** que el botón "Siguiente" esté siempre en la misma posición en todos los pasos del proceso. Si en un paso está a la derecha y en el otro a la izquierda, el usuario se desconcierta.

**Feedback:** al tocar "Completar compra", el sistema debe responder inmediatamente con un indicador de carga o un mensaje de confirmación. Sin esa respuesta, el usuario podría hacer clic varias veces y duplicar la compra.

**Prevención de errores:** validar en tiempo real el formato del email o del número de tarjeta, y si algo falla, mostrar un mensaje claro que indique exactamente qué campo está mal y por qué. Confirmar la compra con un diálogo de "¿estás seguro?" evita el arrepentimiento.

**Accesibilidad (WCAG):** asegurar contraste suficiente entre texto y fondo (criterio de conformidad), que todo el formulario se pueda completar usando solo el teclado (principio Operable), y que cada campo tenga una etiqueta de texto asociada que pueda leer un lector de pantalla (principio Perceptible).

## Comparativas

| Aspecto | Ergonomía física | Ergonomía cognitiva |
|:--------|:-----------------|:--------------------|
| Objeto de estudio | El cuerpo (postura, movimiento, percepción) | La mente (percepción, memoria, decisión) |
| En software se enfoca en | Tamaño de botones, contraste, legibilidad, hardware | Carga cognitiva, memoria de trabajo, consistencia, feedback |
| Pregunta típica | "¿Le resulta cómodo tocar este botón?" | "¿Le resulta fácil entender qué hacer?" |
| Leyes representativas | Ley de Fitts | Ley de Hick, principio de proximidad |
| Consecuencia si se ignora | Fatiga, frustración, errores de clic | Confusión, abandono, errores de comprensión |

| Principio | ¿Qué dice? | Aplicación práctica |
|:----------|:-----------|:--------------------|
| Ley de Fitts | Menos distancia y más tamaño = más rápido | Botones principales grandes y cerca |
| Ley de Hick | Más opciones = más tiempo de decisión | Reducir y agrupar opciones |
| Proximidad | Lo cercano se percibe como un grupo | Agrupar controles relacionados |
| Contraste | Lo diferente resalta | Destacar la acción principal |
| Consistencia | Lo similar se comporta igual | Repetir patrones en toda la app |
| Feedback | Toda acción requiere respuesta | Mostrar confirmaciones y estados |

| Nivel de conformidad WCAG | Significado aproximado |
|:--------------------------|:-----------------------|
| A | Nivel mínimo indispensable de accesibilidad |
| AA | Nivel recomendado para la mayoría de los sitios |
| AAA | Nivel máximo, de acceso ampliado |

## Fuentes

### Nielsen Norman Group - "10 Usability Heuristics" (inglés)

https://www.nngroup.com/articles/ten-usability-heuristics/

Esta fuente reúne los diez heurísticos de usabilidad de Jakob Nielsen, que son la base práctica para evaluar interfaces. De ahí se desprenden, directamente, los principios de retroalimentación (feedback), consistencia y prevención de errores que tratamos en este material.

### Nielsen Norman Group - página sobre Fitts's law (inglés)

https://www.nngroup.com/articles/fitts-law/

Página que explica la ley de Fitts en detalle, con su formulación y sus implicancias concretas para el tamaño y la distancia de los objetivos interactivos en las interfaces.

### W3C / Web Accessibility Initiative - "Introducción a la accesibilidad web" (español)

https://www.w3.org/WAI/fundamentals/accessibility-intro/es

Documento oficial del W3C que introduce qué es la accesibilidad web, por qué importa y cómo se relaciona con las pautas WCAG. Es la referencia autoritativa para el apartado de accesibilidad.

## Para practicar

1. Elegí una aplicación que uses a diario y aplicá la ley de Fitts: identifcá dos botones de acción y analizá si su tamaño y su distancia respecto a donde está el cursor facilitan o dificultan el clic. ¿Cómo los mejorarías?

2. Tomá un menú de una aplicación (por ejemplo, el menú principal de un sitio de compras) y aplicale la ley de Hick. ¿Hay demasiadas opciones? ¿Cómo las agruparías para reducir el tiempo de decisión?

3. Abrí un formulario de registro de cualquier sitio y buscá un ejemplo de buena retroalimentación (feedback) y un ejemplo de falta de ella. ¿Qué pasa si el usuario no recibe respuesta al enviar el formulario?

4. Repasá los diez heurísticos de usabilidad de Nielsen (fuente 1) y encontrá en una app de tu celular un caso de violación de al menos tres de ellos. Describí el problema y proponé una solución.

5. Investigá el contraste de un texto sobre su fondo en un sitio que uses con frecuencia. Según el principio de contraste y los criterios de WCAG, ¿la legibilidad es suficiente? ¿Cómo lo corregirías?

6. Pensá en un usuario con baja visión usando la misma aplicación del punto 5. Aplicando los principios de accesibilidad (WCAG), ¿qué ajustes harías para que pueda operarla con un lector de pantalla o con texto ampliado?

7. Redactá en tres líneas qué diferencia hay entre ergonomía física y ergonomía cognitiva, usando tus propias palabras y un ejemplo de cada una. No vale copiar el texto del material.

8. Debatí con un compañero: ¿es más importante la prevención de errores o la retroalimentación en una interfaz? Fundamenten la respuesta con ejemplos concretos de una app de compras o de transferencias bancarias.
