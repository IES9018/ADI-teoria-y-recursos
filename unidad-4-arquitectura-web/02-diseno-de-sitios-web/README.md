# Diseño de sitios web: una introducción desde cero

## Introducción

Cuando hablamos de "diseñar un sitio web", la mayoría de las personas piensa solo en colores, tipografías e imágenes bonitas. Pero el diseño de un sitio web es mucho más que la estética: es la disciplina que organiza *qué* va a contener el sitio, *cómo* se estructura la información, *cómo* navega el usuario y *cómo* se ve y se comporta en distintos dispositivos. En esta unidad vamos a recorrer el tema desde la raíz: primero qué significa diseñar centrado en el usuario, luego las partes de una página, después cómo hacemos que un sitio se vea bien en cualquier pantalla, y finalmente conceptos fundamentales como la arquitectura de la información, la accesibilidad y el rendimiento.

Este material está pensado para estudiantes que recién empiezan. No hace falta saber programar para entender los conceptos; los ejemplos de código que aparecen son solo ilustrativos y no son el foco. El objetivo es que al terminar puedas explicar con palabras simples qué es el diseño web centrado en el usuario, qué son las capas de la experiencia según Jesse James Garrett y por qué la accesibilidad y el rendimiento importan tanto como el diseño visual.

## Conceptos clave

### Diseño web centrado en el usuario (User-Centered Design, UCD)

Es un enfoque que pone a las personas reales en el centro de todo el proceso de diseño. En lugar de preguntarnos "¿qué quiero mostrar?", nos preguntamos "¿qué necesita hacer el usuario y cómo lo hago más fácil?". Implica conocer a la audiencia, observar cómo usa el sitio, probar con usuarios reales y ajustar el diseño según lo que se aprende. No es un paso puntual: es una filosofía que acompaña todo el ciclo de vida del proyecto.

### Estructura de una página web

Una página web típica se compone de partes identificables que ayudan al usuario a orientarse:

- **Encabezado (header):** la zona superior de la página. Suele contener el logo, el nombre del sitio y, muchas veces, información de contacto o botones de acción rápida.
- **Navegación (navigation):** el conjunto de enlaces que permiten moverse por el sitio. Puede ser un menú horizontal en el encabezado, una barra lateral, un menú desplegable o una combinación de estos.
- **Contenido principal (main):** el corazón de la página. Es donde está la información que el usuario vino a buscar: texto, imágenes, formularios, videos, etc.
- **Pie (footer):** la zona inferior. Suele incluir información legal, enlaces secundarios, contacto, redes sociales y mapa del sitio.

### Diseño responsivo (Responsive Web Design, RWD)

Es la capacidad de un sitio web de adaptar su diseño al tamaño de la pantalla en la que se visualiza. Un mismo sitio debe verse y funcionar bien en un teléfono, una tablet, una notebook o un monitor de escritorio, sin necesidad de crear versiones separadas. Se logra con técnicas como grillas flexibles, imágenes flexibles y las *media queries*, que permiten aplicar estilos distintos según el ancho de la pantalla.

### Diseño mobile-first (móvil primero)

Es una estrategia de diseño responsivo que propone diseñar primero para la pantalla más pequeña (el teléfono) y luego ir "subiendo" hacia pantallas más grandes. La idea es obligarse a priorizar lo esencial: si algo no entra en una pantalla de teléfono, seguramente no era lo más importante. Es el enfoque más común hoy porque la mayoría del tráfico web mundial proviene de dispositivos móviles.

### Los cinco planos de la experiencia (The Elements of User Experience)

Jesse James Garrett, en su libro *The Elements of User Experience*, propone pensar el diseño de un sitio como una estructura de cinco capas o planos, de lo más abstracto a lo más concreto:

- **Estrategia (Strategy):** define qué queremos lograr (objetivos del negocio o del sitio) y qué necesitan los usuarios. Es la base de todo.
- **Alcance (Scope):** a partir de la estrategia, se define qué contenidos y funcionalidades va a incluir el sitio. Es la "lista de lo que hay".
- **Estructura (Structure):** organiza cómo se agrupa y relaciona la información (arquitectura de la información) y cómo se diseñan las interacciones.
- **Esqueleto (Skeleton):** define la disposición de los elementos en la pantalla: dónde va el menú, dónde el contenido, dónde los botones. Es el "wireframe".
- **Superficie (Surface):** la capa visible final: colores, tipografías, imágenes, espaciados. Es lo que el ojo ve y lo que la mayoría cree que es "todo el diseño".

Estos planos funcionan de abajo hacia arriba: primero se define la estrategia y solo al final se pinta la superficie. Saltarse pasos produce sitios bonitos pero que no cumplen su objetivo.

### Arquitectura de la información (Information Architecture, IA)

Es la disciplina de organizar, estructurar y etiquetar el contenido de un sitio para que los usuarios encuentren la información fácilmente. Responde a preguntas como: ¿qué secciones tiene el sitio? ¿cómo se llaman? ¿cómo se jerarquiza el contenido? ¿qué es más importante y qué va más profundo? Una buena arquitectura de la información es como un buen sistema de señalización en un edificio: el usuario nunca debería perderse.

### Navegación web

Es el conjunto de elementos y mecanismos que permiten al usuario moverse por el sitio: menús, enlaces, migas de pan, buscadores internos, botones de "anterior/siguiente". Una navegación clara y predecible es esencial para la usabilidad. Si el usuario no encuentra cómo ir a donde quiere, abandona el sitio.

### Accesibilidad web y diseño inclusivo

La accesibilidad web (WAI/WCAG) es la práctica de hacer que los sitios puedan ser usados por la mayor cantidad de personas posible, incluidas aquellas con discapacidades visuales, auditivas, motoras o cognitivas. Esto incluye, por ejemplo, texto alternativo en imágenes, suficiente contraste de colores, navegación completa con teclado y textos legibles. El diseño inclusivo va un paso más allá: no se trata de adaptar "para algunos", sino de diseñar productos que funcionen bien para todos desde el inicio. Además de ser éticamente correcto, en muchos lugares la accesibilidad es un requisito legal.

### Rendimiento de carga y optimización

El rendimiento se refiere a la velocidad con la que un sitio carga y responde. Un sitio lento frustra a los usuarios y, además, los buscadores lo penalizan en los resultados. Optimizar implica reducir el peso de las imágenes, minimizar archivos de código, aprovechar el almacenamiento en caché y evitar pedidos innecesarios al servidor. El rendimiento es parte del diseño porque un sitio "bien diseñado" que tarda demasiado en cargar, en la práctica, no está bien diseñado.

### Fundamentos de HTML, CSS y JavaScript para el layout

Para implementar todo lo anterior se usan tres tecnologías básicas del desarrollo web:

- **HTML** define la *estructura* semántica: qué es un encabezado, qué es un párrafo, qué es una lista, qué es el contenido principal.
- **CSS** define el *estilo* y la *disposición* visual: colores, tipografías, y cómo se distribuyen los elementos en la pantalla.
- **JavaScript** agrega *comportamiento*: interacciones, validación de formularios, actualización de contenido sin recargar la página.

Para organizar el layout, el modelo más básico es la **caja de elementos (box model)**: cada elemento se trata como una caja con contenido, relleno interno (padding), borde y margen externo. Sobre ese modelo se construyen técnicas de distribución como:

- **Grillas (grids):** dividir la página en columnas y filas para alinear los contenidos de forma ordenada.
- **Flexbox:** un sistema para distribuir elementos en una sola dirección (fila o columna), ideal para alinear menús, tarjetas o barras.
- **CSS Grid:** un sistema bidimensional más potente que permite definir filas y columnas complejas a la vez. Es una de las herramientas clave del diseño responsivo.

## Analogía

Imaginá que diseñar un sitio web es como **diseñar y construir un edificio público**, por ejemplo un centro cultural.

La **estrategia** sería la decisión de "vamos a construir un lugar donde la comunidad pueda ir a leer, ver obras y hacer talleres": quién lo va a usar y para qué. El **alcance** es la lista de ambientes que habrá: biblioteca, sala de exposiciones, dos aulas para talleres. La **estructura** es cómo se conectan esos ambientes entre sí y en qué orden se visitan: ¿la biblioteca queda al lado de las aulas? ¿por dónde se entra? El **esqueleto** es el plano técnico: las dimensiones de cada sala, dónde van las puertas y los pasillos, dónde se ubican los carteles de señalización. Y la **superficie** es la decoración final: qué color de pintura, qué tipo de iluminación, cómo quedan los carteles una vez pintados.

Fijate el orden: nadie razonable elegiría el color de la pintura antes de decidir qué ambientes va a tener el edificio. Sin embargo, eso es exactamente lo que hace mucha gente cuando diseña una web: empieza por los colores sin haber pensado la estrategia ni el contenido. Y después el "edificio" no sirve para nada.

## Ejemplo práctico

Supongamos que una escuela quiere un sitio web para comunicar noticias y novedades a las familias. Veamos cómo aplicarían los conceptos.

**Estrategia:** el objetivo es informar (publicar novedades) y que las familias encuentren información institucional (inscripciones, calendario, contacto). El usuario principal es una familia ocupada que entra desde el celular.

**Alcance:** se decide que el sitio tendrá: sección de noticias, página institucional, calendario escolar, sección de inscripciones y datos de contacto. Eso es lo que "entra" en el sitio; todo lo demás queda fuera por ahora.

**Estructura:** se define que la noticia destacada aparece en la portada, y que las demás se agrupan por fecha. Se decide el nombre de las secciones del menú: "Inicio", "Institucional", "Calendario", "Inscripciones", "Contacto".

**Esqueleto:** se diseña el wireframe de la portada: arriba el logo y el menú horizontal, en el centro la noticia destacada con una lista de las recientes al costado, y abajo el pie con contacto y datos legales.

**Superficie:** se eligen los colores de la escuela, la tipografía legible y las imágenes de las actividades.

Como la mayoría de las familias entra desde el celular, se aplica **mobile-first**: primero se diseña la versión móvil con el contenido esencial bien visible, y luego se amplía el diseño para pantallas de escritorio usando **diseño responsivo** (grillas y media queries). La **navegación** en el celular se convierte en un menú desplegable para no ocupar espacio. La **arquitectura de la información** garantiza que una familia encuentre "Inscripciones" en dos toques como máximo. La **accesibilidad** se cuida con buen contraste y textos alternativos en las fotos, y el **rendimiento** se optimiza comprimiendo las imágenes de las noticias para que la portada cargue rápido incluso con datos móviles.

## Comparativas

### Los cinco planos de Garrett: de lo abstracto a lo concreto

| Plano (capa) | Pregunta clave | Qué define | Ejemplo en un sitio web | Analogía del edificio |
|:--|:--|:--|:--|:--|
| Estrategia (Strategy) | ¿Qué queremos lograr y qué necesita el usuario? | Objetivos del sitio y del negocio | El sitio busca informar a las familias | Decidir qué edificio construir y para quién |
| Alcance (Scope) | ¿Qué contiene el sitio? | Contenidos y funcionalidades | Noticias, calendario, inscripciones | Lista de ambientes del edificio |
| Estructura (Structure) | ¿Cómo se organiza y conecta la información? | Arquitectura de la información e interacciones | Cómo se agrupan y relacionan las secciones | Cómo se conectan y se visitan los ambientes |
| Esqueleto (Skeleton) | ¿Dónde van los elementos en la pantalla? | Wireframes, disposición y navegación | Dónde va el menú y dónde la noticia | Plano técnico con puertas y pasillos |
| Superficie (Surface) | ¿Cómo se ve y se percibe? | Colores, tipografías, imágenes | Paleta de colores de la escuela | Pintura, iluminación y carteles finales |

### Diseño responsivo vs. diseño mobile-first

| Criterio | Diseño responsivo (RWD) | Diseño mobile-first |
|:--|:--|:--|
| Punto de partida | Se diseña para escritorio y se adapta hacia abajo | Se diseña para móvil y se amplía hacia arriba |
| Enfoque mental | "¿Cómo reduzco este diseño para el celular?" | "¿Qué es lo esencial que cabe en una pantalla chica?" |
| Prioridad de contenido | Puede heredar mucho contenido de la versión grande | Fuerza a priorizar lo esencial |
| Uso típico | Técnica para que el layout se adapte | Estrategia y técnica a la vez (muy común hoy) |
| Resultado esperado | Sitio que se ve bien en varias pantallas | Sitio optimizado desde el principio para móviles |

## Fuentes

Las fuentes utilizadas para este material son las siguientes. Se recomienda leerlas para profundizar cada tema.

### Garrett, J. J. — "The Elements of User Experience"

Sitio oficial del libro con el modelo de los cinco planos que estructura la experiencia de usuario. Es la base conceptual de la sección de capas de la experiencia.

https://www.jjg.net/elements/

### MDN Web Docs — "Diseño web responsivo"

Documentación en español que explica los fundamentos del diseño responsivo: grillas flexibles, imágenes flexibles, media queries y la relación con CSS Grid y Flexbox. Sustenta las secciones de diseño responsivo, mobile-first y layout.

https://developer.mozilla.org/es/docs/Learn/CSS/CSS_layout/Responsive_Design

### W3C / Web Accessibility Initiative — "Introducción a la accesibilidad web"

Guía en español de la Iniciativa de Accesibilidad Web (WAI) que explica qué es la accesibilidad, por qué es importante y cómo se relaciona con las pautas WCAG. Sustenta la sección de accesibilidad y diseño inclusivo.

https://www.w3.org/WAI/fundamentals/accessibility-intro/es

## Para practicar

1. **Identificar las partes de una página.** Abrí tres sitios web que uses a diario (por ejemplo, un diario, una tienda online y una red social). Identificá en cada uno el encabezado, la navegación, el contenido principal y el pie. ¿Tienen la misma estructura? ¿Qué diferencias encontrás?

2. **Mapear los cinco planos.** Elegí un sitio real (puede ser el de tu institución o de un comercio local) y tratá de inferir, solo mirándolo, cuál podría ser su estrategia, su alcance, su estructura, su esqueleto y su superficie. Anotá tus respuestas y justificalas.

3. **Probar el mobile-first.** Abrí un sitio en el celular y luego en la computadora. ¿Cómo cambia la navegación? ¿Qué contenido desaparece, se oculta o cambia de lugar? ¿Notás si el sitio fue pensado "móvil primero" o "escritorio primero"? Explicá cómo lo deducís.

4. **Evaluar la arquitectura de la información.** Elegí un sitio con mucha información (un ministerio, una universidad, un banco). ¿Cuántos toques te toma encontrar un dato puntual (por ejemplo, un trámite o el contacto)? ¿Es fácil o te perdés? ¿Cómo lo mejorarías?

5. **Revisar accesibilidad.** En un sitio, probá navegar solo con el teclado (usando Tab, Enter y las flechas). ¿Podés llegar a todas las secciones? Fijate si las imágenes tienen texto alternativo y si el contraste de color deja leer bien el texto.

6. **Medir rendimiento.** Usá el modo incógnito de tu navegador y fijate cuánto tarda en cargar un sitio que uses seguido. Probá el mismo sitio en la computadora y en el celular. ¿Qué sitio te pareció más lento y por qué podría ser?

7. **Diseñar un wireframe en papel.** Dibujá en una hoja (sin código) el esqueleto de la portada de un sitio para una pequeña biblioteca: encabezado, menú, contenido principal con novedades y pie. Dibujá primero la versión móvil y después la de escritorio. ¿Qué cambia entre una y otra?
