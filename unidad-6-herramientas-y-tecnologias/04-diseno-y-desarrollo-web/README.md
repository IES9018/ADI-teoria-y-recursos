# Diseño y desarrollo web

## Introducción

Cuando escribís una dirección en el navegador y aparece una página, detrás de esa pantalla hay un proceso completo que va mucho más allá de "escribir código". Construir un sitio web es, en realidad, un trabajo de diseño y de ingeniería que sigue un camino ordenado: primero se piensa qué se quiere lograr, luego se diseña la estructura visual, después se desarrolla con distintas tecnologías y, al final, se publica para que cualquiera pueda verlo.

Este material te va a llevar de cero a cien por ese recorrido. Vas a entender las piezas que componen la web (el HTML, el CSS y JavaScript), por qué existen los frameworks, cómo se comunican el frente y el fondo de una aplicación, dónde viven los datos, y qué significa "desplegar" un sitio. La idea es que al terminar tengas una visión integral del proceso: desde la estrategia inicial hasta el sitio funcionando en Internet.

## Conceptos clave

### El proceso de diseño y desarrollo web

Desarrollar un sitio no es abrir un editor y escribir código de una. Es un proceso por etapas que va de lo abstracto (ideas) a lo concreto (código desplegado). Las etapas principales son:

- **Estrategia**: se define el objetivo del sitio, el público al que va dirigido y qué acciones se espera que hagan los usuarios (comprar, informarse, registrarse).
- **Diseño de experiencia (UX) y de interfaz (UI)**: se piensa cómo va a fluir la navegación y cómo se va a ver visualmente cada pantalla. Se suelen hacer bocetos o prototipos.
- **Desarrollo frontend**: se construye la parte visible que ve el usuario en el navegador.
- **Desarrollo backend**: se construye la parte del servidor que procesa datos y reglas de negocio.
- **Pruebas y control de calidad**: se verifica que todo funcione en distintos dispositivos y navegadores.
- **Despliegue y publicación**: el sitio se sube a un servidor para que sea accesible en Internet.
- **Mantenimiento y actualización**: se corrige, se agregan funciones y se mejora en el tiempo.

### HTML (HyperText Markup Language)

Es el lenguaje de estructura de una página web. Piensen en él como el esqueleto: define qué es cada parte del contenido. Con HTML se marcan los títulos, los párrafos, las imágenes, los enlaces y los formularios mediante etiquetas.

Lo importante hoy es usar **HTML semántico**, es decir, etiquetas que describen el significado del contenido y no solo su apariencia. Por ejemplo, `<header>` para la cabecera, `<nav>` para la navegación, `<main>` para el contenido principal, `<article>` para un artículo y `<footer>` para el pie. Esto no es un capricho: facilita la lectura por buscadores, mejora la accesibilidad para personas con discapacidad y hace el código más claro.

### CSS (Cascading Style Sheets)

Es el lenguaje de estilo. Si HTML es el esqueleto, el CSS es la piel y la ropa: define los colores, las tipografías, los tamaños, los espacios y la disposición de los elementos en la pantalla (lo que se llama *layout*).

Con CSS se controla cómo se acomoda el contenido en distintos tamaños de pantalla (diseño responsive o adaptable). Existen técnicas modernas de maquetación como **Flexbox** y **Grid**, que permiten distribuir elementos en filas y columnas de forma flexible.

### JavaScript

Es el lenguaje de programación de la web que agrega **interacción**. Con JavaScript una página deja de ser estática y pasa a responder a las acciones del usuario: validar un formulario, mostrar un menú desplegable, cargar contenido nuevo sin recargar la página o animar elementos. Es el que le da "vida" al sitio.

### Frameworks de frontend (React, Angular, Vue)

A medida que un sitio crece, escribir JavaScript "a mano" se vuelve difícil de mantener. Un **framework de frontend** es una caja de herramientas que trae una estructura y reglas ya definidas para construir interfaces de usuario más complejas, organizadas y reutilizables.

- **React**: creado por Meta. Se basa en componentes (piezas de interfaz reutilizables) y es muy popular por su flexibilidad.
- **Angular**: creado por Google. Es un framework más completo y estructurado, que trae muchas herramientas integradas.
- **Vue**: es más liviano y con una curva de aprendizaje amigable, ideal para proyectos medianos.

El rol de estos frameworks es resolver el problema de las **aplicaciones de una sola página** (SPA, *Single Page Application*), donde la interfaz se actualiza de forma dinámica sin recargar todo el sitio.

### Frameworks CSS (Bootstrap, Tailwind)

Así como los frameworks de JavaScript ayudan con la lógica, los **frameworks CSS** ayudan con el estilo y el layout. Traen clases y estilos ya preparados para no escribir cada propiedad desde cero.

- **Bootstrap**: ofrece componentes ya diseñados (botones, tablas, menús) con un sistema de grilla listo para usar. Muy rápido para prototipar.
- **Tailwind CSS**: no trae componentes terminados, sino clases utilitarias de bajo nivel que se combinan para construir el diseño. Da más control y es preferido por quienes quieren un resultado más a medida.

### Backend y frameworks backend (Node/Express, Django, Spring)

El **backend** es la parte que no se ve y que corre en el servidor. Se encarga de la lógica de negocio, la validación de datos, la autenticación de usuarios y el acceso a la base de datos. Cuando el navegador necesita datos, se los pide al backend.

Los **frameworks backend** facilitan la construcción de esa lógica:

- **Node.js con Express**: JavaScript del lado del servidor. Usa el mismo lenguaje que el frontend, lo que facilita equipos que solo dominan JavaScript.
- **Django**: framework de Python. Trae mucho ya resuelto (administración, autenticación) y privilegia la rapidez de desarrollo.
- **Spring**: framework de Java, muy usado en empresas grandes por su robustez y escalabilidad.

### APIs REST y comunicación frontend-backend

El frontend y el backend necesitan hablarse. Lo hacen a través de **APIs** (Application Programming Interface), que son contratos que definen cómo pedir y entregar información.

Una **API REST** es un estilo de API basado en el protocolo HTTP. Usa verbos como GET (obtener), POST (crear), PUT (actualizar) y DELETE (eliminar) sobre recursos identificados por URLs. Por ejemplo, `GET /usuarios` devuelve la lista de usuarios y `POST /usuarios` crea uno nuevo. La información suele viajar en formato **JSON**, que es un texto estructurado fácil de leer tanto por humanos como por programas. Así, el frontend hace peticiones al backend y este responde con los datos que la interfaz necesita.

### Bases de datos y acceso a datos

Los datos de un sitio (usuarios, productos, pedidos) no viven dentro del código: viven en una **base de datos**. El backend es el intermediario que conecta la aplicación con la base de datos, guardando, consultando y actualizando la información.

Existen dos grandes familias: las **bases relacionales** (como PostgreSQL o MySQL), que organizan los datos en tablas relacionadas entre sí y se consultan con SQL, y las **no relacionales** (como MongoDB), que guardan documentos más flexibles. La elección depende del tipo de datos y de las necesidades del proyecto.

### Despliegue y hosting

**Desplegar** significa publicar el sitio para que sea accesible desde Internet. Para eso hace falta un **hosting**: un servidor donde viven los archivos. Ese servidor siempre está encendido y conectado a Internet para responder cuando alguien pide la página.

Existen varias opciones:

- **Servidores propios o virtuales**: máximo control, pero requieren configuración y mantenimiento (por ejemplo, configurar un servidor web como Nginx o Apache).
- **Plataformas de despliegue simples**: como Vercel o Netlify, muy usadas para frontends y sitios estáticos. Conectar el repositorio de código alcanza para que el sitio se publique automáticamente.
- **Servicios cloud**: como AWS, Azure o Google Cloud, que ofrecen infraestructura escalable para aplicaciones más grandes.

### SEO básico

El **SEO** (Search Engine Optimization, optimización para motores de búsqueda) es el conjunto de prácticas para que un sitio aparezca bien posicionado en los resultados de Google y otros buscadores. Algunas prácticas básicas son: usar HTML semántico, títulos y descripciones claros, URLs legibles, y contenido bien estructurado. Los buscadores "leen" el código, así que un código limpio y semántico ayuda a que entiendan de qué trata cada página.

### Accesibilidad web

La **accesibilidad web** busca que los sitios puedan ser utilizados por todas las personas, incluidas aquellas con discapacidades (visuales, auditivas, motoras o cognitivas). Incluye prácticas como: dar texto alternativo a las imágenes, garantizar suficiente contraste de colores, permitir la navegación con teclado y usar etiquetas HTML correctas para que los lectores de pantalla funcionen. Es un aspecto ético y también legal en muchos países, y está regulado por pautas internacionales como las WCAG.

## Analogía

Imaginen que el sitio web es un **restaurante**.

- El **HTML** es la **estructura del local**: dónde está la cocina, el salón, la barra y la entrada. Define qué espacio es cada cosa.
- El **CSS** es la **decoración**: los colores de las paredes, la iluminación, la disposición de las mesas y el uniforme de los mozos. Es lo que hace que el lugar se vea bien.
- **JavaScript** es el **comportamiento en vivo**: el mozo que responde cuando pedís, que levanta la mano si el plato tiene algo raro. Es la interacción con el cliente.
- El **backend** es la **cocina y el almacén**: ahí se preparan los platos (se procesa la lógica) y se guardan los ingredientes (los datos). El cliente no ve la cocina, pero nada funcionaría sin ella.
- La **API REST** es el **pedido entre el mozo y la cocina**: el mozo le pide al cocinero "una milanesa con puré" (una petición) y la cocina le devuelve el plato (la respuesta). Hay un contrato claro de qué se puede pedir y qué se recibe.
- La **base de datos** es la **despensa**: el lugar donde se guardan todos los ingredientes para preparar cualquier plato cuando se lo piden.
- El **despliegue** es **abrir el restaurante al público**: todo lo que estaba en preparación finalmente queda disponible para que cualquiera entre.
- El **SEO** y la **accesibilidad** son el **cartel del local y la entrada con rampa**: que los clientes te encuentren (SEO) y que todos puedan entrar, incluso quienes tienen movilidad reducida (accesibilidad).

## Ejemplo práctico

Vamos a recorrer el proceso pensando en un proyecto concreto: **una tienda de libros online** que vende alquiler de eBooks.

**Estrategia**: el objetivo es que los usuarios puedan registrarse, navegar el catálogo y alquilar un libro digital. El público son estudiantes y lectores habituales.

**Diseño**: se dibuja un prototipo donde la página principal muestra el catálogo, cada libro tiene una ficha con su portada y descripción, y hay una pantalla para iniciar sesión.

**Frontend**: el HTML semántico estructura la página (un `<header>` con el logo y la navegación, un `<main>` con la grilla de libros, un `<footer>`). El CSS define el estilo y el layout para que la grilla se adapte a pantallas chicas. JavaScript (ayudado por un framework como React) permite filtrar libros por género sin recargar la página.

**Backend**: con un framework como Express (Node.js), se definen los "endpoints" de la API REST: `GET /libros` devuelve el catálogo, `GET /libros/:id` devuelve un libro particular y `POST /alquileres` registra un alquiler. El frontend llama a estos endpoints y muestra los datos recibidos en formato JSON.

**Base de datos**: los usuarios y los libros se guardan en una base relacional. El backend consulta esa base para responder las peticiones del frontend.

**Despliegue**: el frontend se publica en Vercel y el backend en un servicio cloud. Ahora cualquier persona con Internet puede entrar a la tienda.

**SEO y accesibilidad**: se usa HTML semántico y títulos descriptivos para que Google muestre bien la tienda, y se agrega texto alternativo a las portadas y navegación por teclado para que personas con discapacidad puedan usarla.

## Comparativas

### Comparación de frameworks de frontend

| Criterio | React | Angular | Vue |
|:---------|:------|:--------|:----|
| Creador | Meta | Google | Comunidad / Evan You |
| Complejidad de aprendizaje | Media | Alta | Baja a media |
| Enfoque | Librería flexible, basada en componentes | Framework completo y estructurado | Framework progresivo, liviano |
| Curva de adopción | Muy popular en la industria | Usado en proyectos empresariales grandes | Buen equilibrio para proyectos medianos |
| Herramientas | Requiere integrar librerías externas | Trae todo integrado | Modelo intermedio |

### Comparación de frameworks CSS

| Criterio | Bootstrap | Tailwind CSS |
|:---------|:----------|:-------------|
| Enfoque | Componentes listos (botones, menús) | Clases utilitarias de bajo nivel |
| Velocidad para prototipar | Alta | Media |
| Control del diseño | Menor (estilos predefinidos) | Mayor (diseño a medida) |
| Resultado visual | Se reconoce fácilmente su "estilo" | Se personaliza sin tanta marca propia |

### Comparación de frameworks backend

| Criterio | Express (Node.js) | Django (Python) | Spring (Java) |
|:---------|:------------------|:----------------|:--------------|
| Lenguaje | JavaScript | Python | Java |
| Estilo | Mínimo y flexible | Completo y "baterías incluidas" | Robusto y empresarial |
| Curva de aprendizaje | Baja a media | Media | Alta |
| Uso típico | Aplicaciones web y APIs ágiles | Prototipos rápidos y apps completas | Sistemas grandes de empresas |

## Fuentes

### MDN Web Docs - "Aprender desarrollo web"

https://developer.mozilla.org/es/docs/Learn

Esta es la guía oficial de Mozilla para aprender desarrollo web desde cero. Es la referencia principal de este material: cubre el proceso completo, el HTML semántico, el CSS, JavaScript y los conceptos de funcionamiento de la web, siempre con explicaciones claras y en español.

### MDN Web Docs - "Como funciona la web"

https://developer.mozilla.org/es/docs/Learn/Getting_started_with_the_web/How_the_Web_works

Este artículo explica el funcionamiento básico de la web: qué son el cliente y el servidor, cómo viajan los datos, y qué pasa exactamente cuando escribís una dirección en el navegador. Es ideal para entender el papel del hosting y del despliegue en el panorama general.

### W3C / Web Accessibility Initiative - "Introducción a la accesibilidad web"

https://www.w3.org/WAI/fundamentals/accessibility-intro/es

La guía oficial de la Iniciativa de Accesibilidad Web del W3C. Explica qué es la accesibilidad web, por qué importa y qué principios se deben seguir, y es la base de las pautas WCAG mencionadas en este material.

## Para practicar

1. Tomá cualquier sitio web que uses a diario e identificá en qué etapa del proceso de diseño y desarrollo creés que se encuentra bien resuelto y en cuál podría mejorar. Justificá cada respuesta.

2. Elegí una página y describí qué partes corresponderían al HTML (estructura), al CSS (estilo) y a JavaScript (interacción). Nombren al menos dos ejemplos de cada uno.

3. En el ejemplo de la tienda de libros, inventá dos peticiones de API REST adicionales a las ya vistas (por ejemplo, una para buscar por autor o una para cancelar un alquiler). Indicá qué verbo HTTP usarías y qué URL propondrías.

4. Completá la siguiente frase y explicála con tus palabras: "El frontend y el backend se comunican a través de una API porque...".

5. Compará Vercel/Netlify con un servidor propio o virtual. ¿En qué caso elegirías cada uno? Argumentá.

6. Revisá un sitio y proponé tres mejoras concretas de accesibilidad que le harías. Fundamentá cada una con lo visto en el material.

7. Investigué con tus propias palabras la diferencia entre una base de datos relacional y una no relacional, y elegí cuál usarías para la tienda de libros justificando por qué.
