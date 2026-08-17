# Evolución de la Web: De las páginas estáticas a las aplicaciones modernas

## Introducción

Cuando hoy abrimos una página web, damos por sentado que podemos iniciar sesión, escribir un comentario, ver contenido que se actualiza solo y hasta hacer compras en línea. Pero la web no siempre fue así. Entender cómo evolucionó desde sus orígenes hasta las aplicaciones modernas es la base para comprender la arquitectura web actual, y por qué existen conceptos como frontend, backend, aplicaciones de una sola página (SPA) o renderizado del lado del servidor (SSR).

Esta unidad te va a llevar de 0 a 100: empezamos desde el principio histórico, pasamos por el gran salto de la Web 2.0, y terminamos en el presente, donde las webs dejaron de ser "documentos" para convertirse en verdaderas aplicaciones. Es un recorrido conceptual, no técnico: no vamos a escribir código todavía, sino a entender las ideas que explican por qué la arquitectura de software web se ve como se ve hoy.

## Conceptos clave

### Orígenes de la web: la web estática de solo lectura

La web nació a comienzos de los años 90 de la mano de Tim Berners-Lee, que trabajaba en el CERN (el laboratorio europeo de física de partículas). Su objetivo era simple pero poderoso: permitir que científicos de distintas partes del mundo compartieran documentos de manera interconectada. Para eso creó el protocolo HTTP (HyperText Transfer Protocol), la URL (Uniform Resource Locator, la dirección de un recurso) y el lenguaje HTML (HyperText Markup Language, el idioma en el que se escriben las páginas).

En esta primera etapa, la web era **de solo lectura**. Cada página era un archivo fijo, guardado en un servidor, que se mostraba exactamente igual a todos los visitantes. Si querías cambiar algo, había que modificar el archivo HTML manualmente y volver a subirlo. El usuario era un mero espectador: podía leer, hacer clic en enlaces y pasar de página, pero no interactuar de verdad con el contenido. Se la llama "web de lectura" porque el flujo era unidireccional: el servidor entrega, el navegador muestra.

### La Web 2.0: contenido generado por el usuario

A partir de los años 2000, la web dio un salto conceptual enorme. Ya no se trataba solo de leer documentos: ahora el usuario podía **crear, publicar y compartir contenido**. Este cambio se conoce como Web 2.0, y es la web que todos conocemos y usamos: blogs donde cualquiera escribe, redes sociales donde cada persona publica fotos y estados, foros, wikis, plataformas de video.

Las características centrales de la Web 2.0 son:

- **Contenido generado por el usuario (User-Generated Content):** el contenido deja de ser producido por unos pocos expertos y pasa a ser creado por millones de personas.
- **La web como plataforma:** los programas ya no se instalan en la computadora, sino que se usan directamente desde el navegador (correo web, editores de documentos en línea).
- **Aplicaciones dinámicas:** las páginas ya no son archivos fijos; el contenido se genera según quien las visita, en el momento.

El motor técnico de este cambio fue la llegada de AJAX (Asynchronous JavaScript And XML), una técnica que permite que el navegador intercambie datos con el servidor **sin recargar toda la página**. Gracias a AJAX, podías escribir un comentario, subir un estado o chatear sin que la pantalla "parpadeara" y se recargara por completo. Fue lo que hizo posibles las interfaces fluidas y dinámicas de las redes sociales y del correo web.

### La web semántica y la Web 3.0: datos y descentralización

En paralelo, Tim Berners-Lee propuso la **web semántica**: la idea de que los datos de la web no solo deberían ser legibles por las personas, sino también comprensibles por las máquinas. Si una página tiene datos **estructurados** (por ejemplo, etiquetas que dicen "esto es un evento", "esto es un precio", "esta es una reseña"), los programas pueden procesarlos, combinarlos y reutilizarlos de forma automática, sin intervención humana. Eso permite la **interconexión de datos**: información que vive en distintos sitios pero que las máquinas pueden vincular y razonar.

Cuando hablamos de **Web 3.0**, el término es más ambiguo y está en debate. Para algunos, es la continuación de la web semántica (datos interconectados y legibles por máquinas). Para otros, está asociado a la **descentralización** mediante tecnologías como **blockchain** (cadena de bloques), donde los datos y las aplicaciones no dependen de un servidor central controlado por una empresa, sino de redes distribuidas gestionadas por muchos participantes. Es importante entender que la Web 3.0 es un tema de debate y no un estándar fijo: mientras la web semántica es una idea consolidada del W3C, la parte de descentralización y blockchain sigue siendo campo de discusión y experimentación.

### Aplicaciones web frente a sitios web estáticos

Una distinción clave para la arquitectura es la diferencia entre un **sitio web** y una **aplicación web (web application)**.

- Un **sitio web estático** es informativo: muestra contenido fijo, como una página institucional, un portafolio o un artículo. Su objetivo es presentar información que cambia poco.
- Una **aplicación web** es un programa completo que corre en el navegador y que permite **realizar acciones**: guardar datos, procesar información, gestionar cuentas, vender productos. Piensa en un sistema de gestión, una plataforma bancaria, un carrito de compras o un panel de administración. La aplicación web tiene lógica de negocio, estado y una base de datos detrás.

La frontera no siempre es nítida (un sitio puede tener partes interactivas), pero en términos de arquitectura es esencial: una aplicación web necesita un **backend** (la lógica y los datos del lado del servidor) mientras que un sitio estático solo necesita servir archivos.

### La evolución hacia frontend y backend modernos

Al hacerse las webs más dinámicas e interactivas, se consolidó una división de responsabilidades que hoy es la base de toda la arquitectura web:

- **Frontend:** todo lo que se ejecuta en el navegador del usuario y que define lo que se ve y cómo se interactúa. Generalmente se construye con HTML, CSS y JavaScript. Es "la vitrina".
- **Backend:** la lógica que se ejecuta en el servidor: procesamiento de datos, autenticación, conexión a bases de datos, reglas de negocio. Es "la trastienda" que el usuario no ve pero que hace funcionar todo.

Ambos se comunican a través de HTTP, enviándose datos (muchas veces en formatos como JSON) a través de una API (interfaz de programación de aplicaciones).

### Aplicaciones de una sola página (SPA) y renderizado del lado del servidor (SSR)

Con el tiempo surgieron dos grandes estrategias de renderizado, es decir, de cómo se construye y se muestra la interfaz:

- **Aplicaciones de una sola página (Single Page Application, SPA):** la aplicación carga una única página HTML y, a partir de ahí, JavaScript se encarga de actualizar el contenido en el navegador, pidiendo datos al servidor sin recargar la página. Es el modelo que usan muchas plataformas modernas: la sensación es la de una aplicación de escritorio, fluida y sin "saltos" entre páginas. El renderizado ocurre en el **lado del cliente** (client-side rendering).

- **Renderizado del lado del servidor (Server-Side Rendering, SSR):** el servidor arma el HTML completo de cada página (con su contenido) y lo envía listo al navegador. Es el modelo clásico, pero sigue muy vigente: es excelente para el posicionamiento en buscadores (SEO) y para la primera carga, porque el contenido llega listo.

Cada enfoque tiene ventajas y desventajas, y muchas aplicaciones modernas combinan ambos. La elección entre SPA y SSR es una decisión de arquitectura, no de gusto.

### Las tecnologías base: HTML, CSS, JavaScript y HTTP

Todo lo anterior descansa sobre cuatro tecnologías fundamentales:

- **HTML (HyperText Markup Language):** define la **estructura** y el contenido de la página. Es el esqueleto: qué hay, títulos, párrafos, imágenes, enlaces.
- **CSS (Cascading Style Sheets):** define la **presentación** y el estilo: colores, tamaños, distribución, diseño visual. Es la "ropa" y el aspecto de la página.
- **JavaScript:** define el **comportamiento** y la interactividad: qué pasa cuando el usuario hace clic, envía un formulario, o cuando la página reacciona a eventos. Es el "músculo" que hace que la página haga cosas.
- **HTTP (HyperText Transfer Protocol):** es el **protocolo** de comunicación que permite que el navegador (cliente) y el servidor intercambien información. Define cómo se hacen las peticiones y cómo se responden.

Estas cuatro piezas son la base de toda la web, tanto la estática de los orígenes como la aplicación moderna más compleja.

## Analogía

Imaginá que la web es como una biblioteca que fue evolucionando.

Al principio, era una biblioteca de **solo lectura**: había miles de libros (las páginas estáticas) escritos por pocos autores. Vos podías entrar, leer, pasar de una sala a otra con los pasillos (los enlaces), pero no podías escribir nada en los libros. Si el bibliotecario (el desarrollador) quería cambiar una palabra, tenía que reescribir el libro entero y volver a colocarlo en el estante.

Después, la biblioteca se volvió una **plaza pública**: la Web 2.0. Ahora cualquiera podía entrar, pegar un cartel, escribir en un pizarrón, conversar con otros y compartir su propio material. Y aparecieron "bibliotecarios digitales" que te traían el contenido justo que querías sin que tengas que caminar por todo el edificio (eso es AJAX, que te trae datos sin recargar toda la biblioteca).

Hoy, la biblioteca se convirtió en una **sede de oficinas**: una aplicación web. Ya no vas a leer un libro fijo; vas a *trabajar*. Entrás a tu cuenta, el sistema sabe quién sos (backend), te muestra un panel que se actualiza solo (frontend con SPA), y todo se mueve a través de un mensajero que corre por los pasillos llevando y trayendo papeles entre vos y las oficinas del fondo: ese mensajero es HTTP.

## Ejemplo práctico

Imaginemos un ejemplo muy cotidiano: una **red social de fotos** (como un Instagram conceptual).

- **Web 1.0 (estática):** el sitio sería una galería de fotos fija que el administrador subía a mano. Todos veían lo mismo, en el mismo orden, y no había forma de comentar, seguir a alguien ni que el contenido fuera "tuyo". Para agregar una foto, había que editar un archivo HTML y subirlo de nuevo al servidor.

- **Web 2.0 (dinámica):** ahora vos podés crearte una cuenta, subir tus fotos, darle "me gusta" a las de otros y escribir comentarios. Cuando hacés clic en "me gusta", AJAX envía la acción al servidor y la interfaz se actualiza al instante, sin recargar la página. El contenido ya no es fijo: es diferente para cada usuario y se genera en el momento. Este modelo descansa sobre una división clara: el frontend muestra tu perfil y tus fotos, el backend guarda los datos en una base de datos y responde a través de una API, y HTTP transporta cada petición y cada respuesta.

- **SPA moderna:** la aplicación carga una sola página. Cuando entrás a tu perfil, luego a la página de un amigo y después al buscador, en realidad seguís en la misma página: JavaScript pide los datos al backend y reconstruye la interfaz al vuelo. Todo se siente fluido, como una app instalada. Si, en cambio, la red social usara SSR, cada vez que navegás a un nuevo perfil, el servidor armaría el HTML de esa vista con su contenido y te lo enviaría completo.

## Comparativas

### Sitio web estático frente a aplicación web

| Aspecto | Sitio web estático | Aplicación web |
|:--------|:-------------------|:---------------|
| Objetivo | Presentar información | Realizar acciones / procesos |
| Interacción | Limitada (leer, navegar) | Alta (cuentas, datos, lógica) |
| Contenido | Fijo, igual para todos | Dinámico, según el usuario |
| Backend | No necesario (o mínimo) | Esencial |
| Ejemplo | Página institucional, portafolio | Panel de gestión, e-commerce |

### Web 1.0 frente a Web 2.0

| Aspecto | Web 1.0 (solo lectura) | Web 2.0 |
|:--------|:-----------------------|:--------|
| Rol del usuario | Espectador | Creador de contenido |
| Dirección del contenido | Unidireccional (servidor → usuario) | Bidireccional (usuario → servidor y vuelta) |
| Interactividad | Mínima | Alta (AJAX, sin recargar) |
| Modelo | Páginas fijas | Aplicaciones dinámicas / plataformas |
| Ejemplo | Galería fija, enciclopedia | Redes sociales, blogs, correo web |

### SPA frente a SSR

| Aspecto | SPA (una sola página) | SSR (servidor) |
|:--------|:----------------------|:---------------|
| Dónde se renderiza | Navegador (lado del cliente) | Servidor |
| Carga inicial | Más lenta, luego muy fluida | Rápida, contenido listo |
| Recarga de página | No recarga al navegar | Recarga o navegación servidor-cliente |
| SEO | Más complejo de optimizar | Mejor para buscadores |
| Sensación de uso | Como app de escritorio | Página tradicional |

## Fuentes

Las fuentes de este material fueron verificadas y son sitios oficiales y confiables. A continuación se citan únicamente las que se usaron.

### MDN Web Docs (Mozilla)

**MDN Web Docs - "HTML: Lenguaje de marcas de hipertexto" / guía web (inglés):**
https://developer.mozilla.org/es/docs/Web/HTML
Se utilizó como referencia para definir las tecnologías base, en particular HTML, y el funcionamiento de los componentes que componen la web.

**MDN Web Docs - "Como funciona la web" (español):**
https://developer.mozilla.org/es/docs/Learn/Getting_started_with_the_web/How_the_Web_works
Se utilizó para explicar la comunicación entre el cliente (navegador) y el servidor a través de HTTP, base del modelo de arquitectura web.

### W3C (World Wide Web Consortium)

**W3C - "Historia de la Web" (Tim Berners-Lee):**
https://www.w3.org/History.html
Se utilizó para describir los orígenes de la web, la creación del HTTP, la URL y el HTML por parte de Tim Berners-Lee, y el concepto de web semántica.

## Para practicar

Para afianzar los conceptos de este material, te proponemos los siguientes ejercicios:

1. **Clasificar servicios:** Tomá tres sitios o aplicaciones que uses a diario (por ejemplo, un buscador, una red social y el sitio de tu facultad). Clasificalos como "sitio estático" o "aplicación web" y justificá por qué. ¿En cuáles te registrás o generás contenido?

2. **Detectar SPA y SSR:** Cuando navegás por un sitio moderno, prestá atención a si la página se "recarga" al cambiar de sección. Si no se recarga y todo es fluido, probablemente es una SPA. Si cada vista llega completa desde el servidor, es SSR. Anotá tus observaciones en una lista.

3. **Pensar en roles:** Para una red social de fotos, explicá con tus palabras qué haría el frontend y qué haría el backend. ¿Qué información creés que viajaría a través de HTTP?

4. **Explicar a un compañero:** Tratá de explicarle a un compañero, sin usar palabras técnicas, la diferencia entre la web de solo lectura y la Web 2.0 usando la analogía de la biblioteca y la plaza pública. Si lo lográs, entendiste el concepto.

5. **Debatir la Web 3.0:** Investigá y anotá tus propias conclusiones sobre el debate entre la web semántica (datos interconectados) y la descentralización con blockchain. ¿Por qué pensás que todavía es un tema en discusión y no una realidad consolidada?

Este material corresponde al tema 1 de la Unidad 4 "Arquitectura Web" de la materia Arquitectura y Diseño de Interfaces (ADI). La clave es recordar que la web pasó de ser un conjunto de documentos fijos a un ecosistema de aplicaciones, y que todas las arquitecturas modernas (frontend/backend, SPA, SSR) son respuestas evolutivas a ese proceso histórico.
