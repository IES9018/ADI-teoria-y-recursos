# Diseño y desarrollo de interfaces: de la idea al código

## Introducción

Cuando usás una aplicación, lo primero que ves (y lo primero que sentís) es la interfaz. Esa pantalla donde tocás botones, escribís en formularios, ves colores y leés textos es el resultado de un trabajo que une dos mundos que muchas veces se confunden: el diseño y la programación. En esta unidad vamos a entender que una buena interfaz no aparece por casualidad, sino que es el producto de un proceso ordenado que empieza con una idea, pasa por herramientas de diseño y termina en código que corre en el navegador.

Este material te propone recorrer ese camino completo, desde el "primer boceto" hasta la implementación técnica. El objetivo no es que te conviertas en diseñador ni en experto frontend en un solo tema, sino que entiendas cómo dialogan ambas disciplinas, qué herramientas existen en cada etapa y por qué dominar este flujo te hace un mejor profesional del software. Porque, seamos honestos: una aplicación técnicamente perfecta pero con una interfaz confusa es una aplicación que nadie quiere usar.

Vamos a ir de cero a cien, sin asumir que ya sabés nada. Cada concepto se explica despacio, se compara con algo de la vida cotidiana y se acompaña con un ejemplo concreto.

## Conceptos clave

### Interfaz de usuario (User Interface, UI)

Es todo aquello con lo que la persona interactúa directamente: pantallas, botones, menús, formularios, íconos, colores y textos. Pensá en la interfaz como la "cara" del sistema: lo que el usuario ve y toca. Es la capa más externa de una aplicación, la que conecta a la persona con la lógica que está por debajo. En una materia como Modelado de Software, la interfaz sería el equivalente a lo que se ve de una clase: sus métodos públicos, digamos. El resto (la lógica de negocio) queda "detrás de la escena".

### Experiencia de usuario (User Experience, UX)

Va más allá de lo visual. UX se ocupa de cómo se siente la persona al usar el producto: si encuentra lo que busca, si las tareas le resultan fáciles o frustrantes, si el recorrido tiene sentido. Mientras la UI es "cómo se ve y se toca", la UX es "cómo se vive". Un buen UX puede existir con una UI sencilla, y una UI espectacular puede arruinarse por una UX mala. La UX incluye investigación de usuarios, organización de la información, pruebas y ajustes constantes.

### Diseño de interfaz (UI design)

Es la disciplina que decide cómo se ve la interfaz: la paleta de colores, la tipografía, el espaciado, las formas de los botones, las animaciones y la coherencia visual. Un diseñador de UI convierte los lineamientos de la experiencia (UX) en elementos visuales concretos. Es el paso donde "lo que debe funcionar" se transforma en "lo que se ve bien".

### Desarrollo de interfaces (frontend development)

Es la disciplina que convierte el diseño en código ejecutable. El desarrollador frontend toma los archivos de diseño y los implementa con tecnologías web: HTML para la estructura, CSS para el estilo y JavaScript para la interacción. Es el puente entre el diseño estático y la aplicación viva que reacciona cuando el usuario hace clic, escribe o desplaza la página.

### Herramientas de diseño de interfaz

Son los programas donde se dibuja y se prueba la interfaz antes de escribir una sola línea de código. Se usan para crear pantallas, organizar componentes, hacer prototipos interactivos y compartir el trabajo con el equipo. Las tres más conocidas son:

- **Figma**: herramienta que corre en el navegador, pensada para que varios diseñadores trabajen en el mismo archivo a la vez, en tiempo real. Permite diseño, prototipado y creación de design systems. Es la más usada en la industria hoy.
- **Adobe XD**: herramienta de Adobe, también para diseño y prototipado de interfaces. Se integra bien con el resto del ecosistema de Adobe (Photoshop, Illustrator).
- **Sketch**: herramienta de diseño para macOS, muy popular en equipos de Apple. Fue pionera en popularizar los componentes y los símbolos reutilizables.

Todas comparten una idea central: permiten diseñar sin programar y probar la idea con prototipos antes de invertir tiempo en desarrollo.

### Prototipado (prototyping)

Es la creación de una versión interactiva y preliminar de la interfaz, que simula cómo va a funcionar el producto real. Puede ser de baja fidelidad (bocetos simples, casi en papel) o de alta fidelidad (pantallas casi iguales a las finales, con clics y navegación). El prototipo sirve para validar la idea con usuarios y con el equipo antes de escribir código. Es mucho más barato cambiar un botón de lugar en un prototipo que después de haberlo programado.

### Design system (sistema de diseño)

Es el conjunto completo y documentado de componentes, reglas, colores, tipografías y patrones que dan coherencia a toda la aplicación. No es solo una colección de botones bonitos: es un estándar vivo que garantiza que todas las pantallas "se sientan del mismo producto", sin importar quién las diseñe o programe. Según Nielsen Norman Group, un design system reúne todos los recursos y reglas que se reutilizan para construir y mantener productos digitales, funcionando como un "lenguaje compartido" dentro del equipo.

### Guía de estilo (style guide)

Es la documentación visual de los elementos básicos: colores, tipografías, tamaños, íconos y su correcto uso. Es una parte del design system, pero más acotada: se enfoca en el "cómo se ve", no tanto en el "cómo se comporta". Mientras la guía de estilo dice qué colores usar, el design system además define componentes completos (un botón con sus estados: normal, hover, deshabilitado) y las reglas de uso.

### Lenguaje de marcas de hipertexto (HTML)

Es el lenguaje que define la estructura de una página web. Con HTML se indican los elementos: títulos, párrafos, imágenes, botones, formularios. Define el esqueleto semántico del contenido. No decide cómo se ven las cosas, sino qué es cada cosa.

### Hojas de estilo en cascada (CSS, Cascading Style Sheets)

Es el lenguaje que controla la presentación: colores, fuentes, tamaños, espacios, posiciones y animaciones. Con CSS se le dice al navegador "cómo se ve" cada elemento definido en HTML. La documentación oficial de MDN Web Docs explica que CSS es un lenguaje de hojas de estilos que permite aplicar estilos a los elementos seleccionados de una página. Es el responsable de que una interfaz pase de "texto plano" a "producto visual".

### JavaScript

Es el lenguaje de programación que le da comportamiento e interactividad a la página. Con JavaScript el usuario puede hacer clic en un botón y que algo cambie sin recargar la página, validar un formulario, cargar datos, animar elementos. HTML define qué hay, CSS cómo se ve y JavaScript qué pasa cuando la persona interactúa.

### Framework CSS

Es un conjunto de estilos (reglas CSS) ya hechos y reutilizables que aceleran el diseño de la interfaz. En lugar de escribir todo el CSS desde cero, el desarrollador usa clases ya definidas que le dan el estilo a los elementos. Los dos más conocidos:

- **Bootstrap**: framework CSS con componentes listos (botones, tablas, menús, tarjetas) y un sistema de grillas para organizar el contenido en columnas. Muy usado, con mucha documentación y una curva de aprendizaje amigable.
- **Tailwind CSS**: un enfoque distinto: en lugar de componentes prearmados, ofrece utilidades "atómicas". En vez de escribir una clase `.boton`, escribís varias clases pequeñas (`p-4`, `bg-blue-500`, `rounded`) que combinadas construyen el estilo. Da más control pero exige más conocimiento de CSS.

### Framework de UI / biblioteca de componentes (UI library / component library)

Es una colección de componentes de interfaz ya programados y listos para usar, que vienen con su lógica de comportamiento. El ejemplo más conocido es **Material UI**: implementa las guías de "Material Design" de Google y ofrece componentes de React (botones, diálogos, tablas, barras de navegación) con su estilo y su interacción incorporados. La ventaja: no tenés que diseñar ni programar cada componente desde cero; los adaptás a tu caso.

### Framework de frontend (frontend framework)

Es una tecnología que organiza la construcción de la interfaz de una aplicación completa, manejando el estado, la interacción y la actualización de la pantalla. Los tres más populares:

- **React**: desarrollado por Meta. Se basa en componentes y en un "estado" que, cuando cambia, actualiza automáticamente la pantalla. Es una biblioteca (aunque suele llamársele framework).
- **Angular**: desarrollado por Google. Es un framework completo que trae herramientas de más "bajo nivel" incluidas (enrutado, formularios, manejo de dependencias).
- **Vue**: un framework progresivo, conocido por su curva de aprendizaje suave y su flexibilidad para adoptarse de a poco.

### Estado (state)

Es la información que la interfaz necesita recordar en un momento dado: si un botón está activo, qué escribió el usuario en un formulario, si un menú está abierto o cerrado, qué datos llegaron de una consulta. En aplicaciones frontend modernas, el estado es central: cuando cambia el estado, la interfaz se actualiza automáticamente. Los frameworks de frontend existen, en gran parte, para hacer manejable este problema: coordinar el estado con lo que se muestra en pantalla.

### Design-to-code y handoff

**Design-to-code** (de diseño a código) es el flujo de trabajo completo que va del diseño a la implementación. **Handoff** (entrega de diseño) es la etapa específica en la que el diseño terminado "se le pasa" al desarrollador, con toda la información necesaria: medidas, colores, estilos de texto, estados de componentes, especificaciones de espaciado. Las herramientas de handoff facilitan esta transición: en lugar de que el desarrollador "mida con la regla" sobre la imagen, la herramienta le muestra automáticamente los valores exactos, e incluso puede generar código CSS o componentes listos.

### Accesibilidad (accessibility)

Es la práctica de diseñar y desarrollar interfaces que puedan ser usadas por todas las personas, incluidas aquellas con discapacidades visuales, motoras, auditivas o cognitivas. Implica usar textos alternativos en imágenes, contraste adecuado de colores, navegación por teclado, etiquetas correctas en formularios y compatibilidad con lectores de pantalla. La accesibilidad no es un extra: es parte de la calidad del producto.

### Rendimiento (performance)

Es la velocidad y fluidez con la que la interfaz carga y responde. Un buen rendimiento implica que las imágenes estén optimizadas, que el código no sea innecesariamente pesado, que la página cargue rápido incluso en conexiones lentas y que las interacciones se sientan inmediatas. Un usuario no espera más de unos pocos segundos: una interfaz lenta se percibe como rota, sin importar lo bonita que sea.

## Analogía

Pensá que una aplicación es un restaurante, y la interfaz es todo lo que pasa del lado de los clientes (la sala), en contraposición a la cocina (la lógica de negocio).

- El **diseño de interfaz (UI)** es el trabajo del decorador y el maquetador de la sala: qué color tienen las paredes, cómo están puestas las mesas, cómo se ve la carta, qué iluminación hay. Es lo estético, lo que se percibe al entrar.
- La **experiencia de usuario (UX)** es cómo se siente el cliente al vivir la experiencia: ¿encontró el baño fácil? ¿el mozo entendió su pedido? ¿esperó demasiado la comida? No importa cuán linda esté la sala si la experiencia es frustrante.
- El **desarrollo (frontend)** es la construcción física de esa sala: los albañiles que levantan las paredes, el electricista que instala la luz, el plomero que conecta los lavabos. Es el que hace que el diseño deje de ser un plano y se convierta en una sala real donde se puede caminar.
- El **design system** es el "manual de marca" del restaurante: las reglas que garantizan que la sucursal de la esquina se vea y funcione igual que la del centro, con los mismos platos, la misma carta y los mismos estándares.
- Los **frameworks** son la caja de herramientas del constructor: no tiene que fabricar cada tornillo desde cero, sino que usa piezas estandarizadas y probadas que aceleran el trabajo y reducen errores.
- El **handoff** es el momento en que el plano del decorador se le entrega al constructor con todas las medidas exactas, para que no haya lugar a interpretaciones ni malentendidos.

La clave: el decorador que dibuja un plano hermoso pero imposible de construir es tan inútil como el constructor que levanta una sala sin consultar el plano. Diseño y desarrollo son dos momentos del mismo proceso, y la calidad final depende de que se entiendan.

## Ejemplo práctico

Imaginemos que un equipo quiere construir la interfaz de una aplicación de pedidos de comida llamada "La Tiendita". Veamos el recorrido completo con un caso concreto: la pantalla de "confirmar pedido".

**1. El equipo define la experiencia (UX).** Investigan que los usuarios quieren confirmar su pedido en pocos pasos, sin sorpresas. Se define que la pantalla debe mostrar el total, el tiempo estimado y un botón grande de confirmar.

**2. El diseñador crea la interfaz (UI) en Figma.** Dibuja la pantalla: una tarjeta con el detalle del pedido, el botón verde "Confirmar pedido", la tipografía y los colores de la marca. Hace un prototipo haciendo clic en el botón y probando cómo se ve la confirmación. Guarda todos estos elementos dentro de un **design system**: define el componente "botón primario" con sus estados (normal, al pasar el mouse, deshabilitado).

**3. El desarrollador recibe el diseño (handoff).** En Figma, el desarrollador selecciona el botón y la herramienta le muestra los valores exactos: color de fondo, radio de las esquinas, tipografía, padding. No tiene que adivinar nada.

**4. El desarrollador implementa con HTML, CSS y JavaScript.** Escribe el HTML con la estructura (la tarjeta, el título, el botón), el CSS con los estilos del design system y el JavaScript para que al hacer clic en el botón se valide el pedido y se muestre la confirmación.

**5. El desarrollador acelera el trabajo con herramientas.** Usa un framework CSS (por ejemplo, Tailwind) para dar los estilos con utilidades rápidas. Luego, para que la interfaz reaccione de forma organizada a los cambios (por ejemplo, que el total se actualice si el usuario cambia la cantidad), usa un framework de frontend como React. Con React, el "estado" del pedido (cantidad, total, estado de confirmación) vive en un lugar controlado, y cuando cambia, la pantalla se actualiza sola.

**6. El equipo revisa accesibilidad y rendimiento.** Verifican que el botón se pueda activar con el teclado, que el contraste del texto sea suficiente, que las imágenes del menú estén comprimidas y que la página cargue rápido.

Así, la misma pantalla recorrió todo el flujo: investigación, diseño, prototipo, handoff, implementación, frameworks y controles de calidad. Ese es el design-to-code en acción.

## Comparativas

### Sistemas de diseño vs. guías de estilo

| Aspecto | Guía de estilo | Design system |
|:--------|:---------------|:--------------|
| Alcance | Visual: colores, tipografías, íconos | Completo: componentes, comportamiento, reglas de uso |
| Incluye | Paleta, tipografías, tamaños | Todo lo de la guía más componentes, estados y patrones |
| Enfoque | "Cómo se ve" | "Cómo se ve" y "cómo se comporta" |
| Actualización | Estática, documenta decisiones | Vivo, evoluciona con el producto |
| Ejemplo | "El azul de marca es este" | "El botón primario, con su estado normal, hover y deshabilitado, y cuándo usarlo" |

### Bootstrap vs. Tailwind CSS

| Aspecto | Bootstrap | Tailwind CSS |
|:--------|:----------|:-------------|
| Enfoque | Componentes prearmados | Utilidades atómicas |
| Uso típico | `.btn`, `.card`, `.navbar` | `p-4`, `bg-blue-500`, `rounded` |
| Velocidad inicial | Alta (solo agregás clases) | Media (hay que combinar utilidades) |
| Control del diseño | Menor (estilos definidos) | Mayor (armás tu propio estilo) |
| Curva de aprendizaje | Baja | Media (requiere conocer CSS) |

### UI framework vs. CSS framework

| Aspecto | Framework CSS | Framework de UI (component library) |
|:--------|:--------------|:-------------------------------------|
| Qué entrega | Estilos (visual) | Componentes con estilos y comportamiento |
| Ejemplo | Bootstrap, Tailwind | Material UI |
| Incluye lógica | No | Sí (estados, eventos, accesibilidad básica) |
| Depende de un framework JS | No necesariamente | Sí (por ejemplo, Material UI es para React) |
| Nivel de abstracción | Bajo-medio | Alto |

## Fuentes

Las siguientes fuentes fueron consultadas y verificadas para este material. Son las que realmente aportaron a los conceptos de design system, herramientas de diseño y CSS.

### Figma (página oficial)

https://www.figma.com/

Figma es la herramienta de diseño y prototipado colaborativo de referencia. Su sitio oficial documenta el diseño de interfaces, la creación de prototipos interactivos, el trabajo en equipo en tiempo real y la construcción de design systems, así como las funciones de handoff que facilitan el pasaje del diseño al desarrollador.

### MDN Web Docs - "CSS"

https://developer.mozilla.org/es/docs/Web/CSS

La documentación de referencia de la web (mantenida por Mozilla) explica CSS de forma completa y en español. Define qué son las hojas de estilo en cascada, cómo se aplican a los elementos de una página y por qué son fundamentales para el desarrollo de interfaces web. Es la fuente autorizada para entender CSS más allá de cualquier framework.

### Nielsen Norman Group - "Design Systems 101"

https://www.nngroup.com/articles/design-systems-101/

El grupo Nielsen Norman, referente mundial en experiencia de usuario, publica una guía introductoria a los sistemas de diseño: qué son, para qué sirven, qué problemas resuelven y cómo se relacionan con las guías de estilo. Fue la base conceptual para la sección de design systems de este material.

## Para practicar

**1. Identificar el flujo.** Describí con tus palabras el recorrido que hace una pantalla desde que se piensa hasta que se programa. Nombrá las etapas y las herramientas típicas de cada una. Comparalo con el ejemplo del restaurante.

**2. Diferenciar conceptos.** Explicá, con un ejemplo propio, la diferencia entre UI y UX. ¿Por qué una interfaz linda puede ser una mala experiencia? ¿Y por qué una interfaz fea puede ser una buena experiencia?

**3. Guía de estilo vs. design system.** Usá una tabla para comparar una guía de estilos y un design system. Luego decí: ¿qué incluiría un design system de una aplicación de biblioteca (listado de libros, ficha de libro, préstamo)? Listá al menos cinco componentes y sus estados.

**4. Elegir herramientas.** Investigá el sitio oficial de Figma y anotá tres funciones relacionadas con el diseño, tres con el prototipado y dos con el handoff. ¿En qué etapa del flujo usarías cada una?

**5. Comparar CSS frameworks.** Entrá a la documentación de MDN sobre CSS y definí qué es una clase CSS. Luego, con base en la tabla de Bootstrap vs. Tailwind, elegí cuál usarías para un proyecto simple y justificá por qué. ¿Cuándo elegirías el otro?

**6. Estado en frontend.** Imaginá un formulario de registro. Listá tres datos de "estado" que la interfaz debe recordar (por ejemplo, si el campo tiene un error). Explicá, sin escribir código, por qué sería un problema si la pantalla no supiera cuál es ese estado en cada momento.

**7. Accesibilidad y rendimiento.** Proponé tres mejoras de accesibilidad y tres de rendimiento para una pantalla de listado de productos con imágenes. Para cada una, explicá qué problema concreto resuelve.
