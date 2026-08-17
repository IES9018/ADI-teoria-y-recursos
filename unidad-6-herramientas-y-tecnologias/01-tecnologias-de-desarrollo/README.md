# Tecnologías de desarrollo: lenguajes, frameworks, bibliotecas y herramientas

## Introducción

Si alguna vez te preguntaste "¿con qué se construye una aplicación?", este material es tu punto de partida. Cuando ves una página web, una app de pedidos de comida o un sistema de gestión de un comercio, detrás hay un conjunto de tecnologías que se combinan para que todo funcione.

Este tema te da el mapa del territorio: qué es un lenguaje de programación, qué es un framework, qué es una biblioteca, qué es un entorno de ejecución, qué tipos de bases de datos existen y cómo se guarda y comparte el código de un proyecto. No vamos a escribir código todavía: primero necesitás entender el vocabulario para poder comunicarte con otros desarrolladores y leer documentación sin frustrarte.

La idea es que al terminar puedas explicar con tus palabras qué rol cumple cada pieza de una aplicación moderna y por qué elegimos una herramienta y no otra.

## Conceptos clave

### Tecnología de desarrollo

Una tecnología de desarrollo es cualquier herramienta que usamos para crear software. Es un término "paraguas" que incluye a los lenguajes de programación, los frameworks, las bibliotecas, los entornos de ejecución, los gestores de paquetes, las bases de datos y las plataformas donde guardamos el código. Elegir bien estas tecnologías define cómo se va a construir, mantener y crecer un proyecto. En la industria se habla de "stack tecnológico" (pila tecnológica) para referirse al conjunto de tecnologías que usa un proyecto.

### Lenguaje de programación

Un lenguaje de programación es el idioma que usamos para darle instrucciones a una computadora. Así como el español o el inglés tienen reglas gramaticales, cada lenguaje tiene su sintaxis (reglas de escritura) y su semántica (significado). La computadora no entiende nuestro idioma humano; necesita que le traduzcamos nuestras intenciones a algo que pueda ejecutar.

Los lenguajes más usados para desarrollo web y de aplicaciones son:

- JavaScript (lenguaje, frente a TypeScript): es el lenguaje nativo de los navegadores. Prácticamente toda página web moderna lo usa. No hay que confundirlo con Java, que es otro lenguaje totalmente distinto. MDN lo describe como un lenguaje de programación ligero e interpretado.
- TypeScript: es una extensión de JavaScript que le agrega tipos (verifica el tipo de datos antes de ejecutar). Ayuda a evitar errores en proyectos grandes.
- Python: muy legible y fácil de aprender. Se usa muchísimo en ciencia de datos, inteligencia artificial y también en desarrollo web (con frameworks como Django).
- Java: clásico de las aplicaciones empresariales y de Android. Corre sobre una máquina virtual, lo que le permite ejecutarse en muchos sistemas.
- C# (se pronuncia "c sharp"): desarrollado por Microsoft, muy usado en aplicaciones de escritorio, web y videojuegos.
- PHP: uno de los primeros lenguajes para sitios web dinámicos. Sigue presente en una enorme cantidad de servidores del mundo.
- Kotlin: es el lenguaje oficial moderno para desarrollar aplicaciones Android.
- Swift: es el lenguaje oficial para desarrollar aplicaciones en los dispositivos de Apple (iPhone, iPad, Mac).

Cada lenguaje tiene fortalezas y debilidades. Ninguno es "el mejor": se elige según el problema, el equipo y el contexto.

### Framework

Un framework (marco de trabajo) es una estructura de software ya armada que nos da el esqueleto de una aplicación. Nos dice cómo organizar el código, nos ofrece piezas ya resueltas y establece reglas de cómo trabajar. Cuando usamos un framework, nosotros no controlamos el flujo completo de la aplicación: el framework "llama" a nuestro código cuando lo necesita.

Existen frameworks para distintas partes del sistema:

- Framework frontend (interfaz de usuario): se ocupa de la parte visual, de lo que el usuario ve y con el que interactúa en el navegador. Ejemplos: React, Angular y Vue.
- Framework backend (servidor): se ocupa de la lógica del negocio, del acceso a datos y de responder a las peticiones del frontend. Ejemplos: Express (para JavaScript/Node), Django (para Python) y Spring (para Java).

### Biblioteca o librería (library)

Una biblioteca (también llamada librería) es un conjunto de funciones ya escritas que podemos reutilizar para no reinventar la rueda. A diferencia del framework, acá somos nosotros quienes llamamos a la biblioteca cuando la necesitamos: nosotros controlamos el flujo.

La diferencia clave entre framework y biblioteca se resume en un concepto llamado inversión de control (inversion of control, IoC):

- Con una biblioteca: el código de nuestra aplicación llama a las funciones de la biblioteca.
- Con un framework: el framework controla el flujo y es él quien llama a nuestro código.

Una analogía clásica: la biblioteca es como una caja de herramientas que abrís y usás cuando querés; el framework es como contratar a una empresa que arma tu casa y solo te pregunta cómo querés cada ambiente.

### Entorno de ejecución (runtime)

Un entorno de ejecución (runtime) es el "lugar" donde un programa se ejecuta. Provee los servicios básicos que el código necesita para correr: manejo de memoria, acceso a archivos, etc. El ejemplo más famoso en desarrollo web es Node.js, que permite ejecutar JavaScript fuera del navegador, es decir, en el servidor. Gracias a Node.js, JavaScript puede usarse tanto en el frontend como en el backend, usando un solo lenguaje en todo el proyecto.

### Gestor de paquetes (package manager)

Un gestor de paquetes (package manager) es una herramienta que facilita instalar, actualizar y quitar las bibliotecas y dependencias de un proyecto. En lugar de descargar archivos a mano y copiarlos, el gestor se encarga de todo. El ejemplo clásico es npm (Node Package Manager), que viene con Node.js y es el gestor de paquetes por defecto de JavaScript.

### Bases de datos

Las aplicaciones necesitan guardar información (usuarios, pedidos, productos) y volver a recuperarla después. Ahí entran las bases de datos. Hay dos grandes familias:

- SQL (lenguaje de consulta estructurada) y bases de datos relacionales: organizan la información en tablas con filas y columnas, como una planilla, y establecen relaciones entre las tablas. Son muy ordenadas y garantizan consistencia de los datos. Ejemplos: MySQL y PostgreSQL.
- NoSQL y bases de datos documentales: no usan necesariamente tablas. Las bases documentales, como MongoDB, guardan la información en documentos flexibles (formato JSON). Son útiles cuando los datos cambian mucho de estructura o se maneja muchísimo volumen.

No se trata de que una sea mejor que la otra: se elige según cómo se relacionan los datos del problema.

### API y REST

Un API (Application Programming Interface, interfaz de programación de aplicaciones) es un conjunto de reglas que permite que dos programas se comuniquen entre sí. Define qué peticiones se pueden hacer y qué respuestas esperar. Es como el menú de un restaurante: te dice qué podés pedir y cómo lo vas a recibir.

REST (Representational State Transfer) es un estilo de diseño de APIs web que se apoya en el protocolo HTTP y en operaciones como obtener, crear, actualizar y eliminar recursos. Cuando un frontend (por ejemplo, una app React) necesita datos, se los pide al backend a través de una API REST.

### Versionado y plataformas de alojamiento de código

El versionado (control de versiones) es el registro de los cambios que sufre el código a lo largo del tiempo. Nos permite guardar historial, volver atrás si algo se rompe y trabajar en equipo sin pisarnos el trabajo.

Git es la herramienta de control de versiones más usada del mundo. La documentación oficial de Git lo describe como un sistema de control de versiones distribuido: cada desarrollador tiene una copia completa del historial en su máquina.

Las plataformas de alojamiento de código guardan esos repositorios en la nube y ofrecen herramientas para colaborar, revisar cambios y automatizar tareas. Las más conocidas son GitHub y GitLab. Ahí se centraliza el código de un proyecto y el equipo puede trabajar de forma coordinada.

## Analogía

Imaginá que querés construir un edificio de departamentos.

- Los lenguajes de programación son los materiales de construcción: hay ladrillos, hormigón y madera. Podés construir con todos, pero cada uno tiene propiedades distintas.
- Las bibliotecas son la caja de herramientas: el taladro, la cinta métrica y el nivel. Las agarrás cuando las necesitás y decidís vos cómo usarlas.
- El framework es la empresa constructora que ya tiene un método y un cronograma: te dice qué se construye en cada etapa y vos solo completás las decisiones de diseño. No controlás el proceso completo; la empresa sí.
- El entorno de ejecución es el terreno y los servicios de la obra: electricidad y agua que hacen posible que todo funcione.
- La base de datos es el depósito de planos y documentación: guarda información que después se vuelve a consultar.
- El API es la recepción del edificio: la regla por la cual los visitantes piden entrar y reciben lo que necesitan.
- Git y las plataformas de alojamiento son el archivo de obra y la mesa de reuniones: guardan cada versión del plano y permiten que todos los albañiles trabajen juntos sin pisarse.

## Ejemplo práctico

Pensemos en una aplicación de delivery de comida que funciona como sitio web.

El usuario abre la página en el navegador. La interfaz que ve (el frontend) está construida con un framework de JavaScript como React. Mientras usa la app, el navegador también ejecuta JavaScript puro y quizás usa bibliotecas para tareas puntuales como dar formato a fechas.

Cuando el usuario hace un pedido, el frontend se comunica con el backend a través de una API REST: envía una petición HTTP pidiendo crear un nuevo pedido. El backend, que corre en un servidor usando Node.js (entorno de ejecución de JavaScript) con el framework Express, recibe la petición, valida los datos y decide qué hacer.

El backend guarda el pedido en una base de datos. Si los datos de un pedido son muy estructurados y se relacionan entre sí, probablemente use una base SQL como PostgreSQL. Si, en cambio, cada pedido tiene estructura muy variable, podría usar una documental como MongoDB. Las bibliotecas que el proyecto necesita (para seguridad, por ejemplo) se instalaron con el gestor de paquetes npm.

Todo ese código vive en un repositorio de Git, alojado en GitHub. El equipo desarrolla en paralelo: cada uno trabaja en su rama (copia del proyecto), y los cambios se integran revisando que no haya conflictos. Si algo sale mal, pueden volver a una versión anterior del código.

## Comparativas

### Framework vs biblioteca

| Característica | Biblioteca (library) | Framework |
|:---------------|:---------------------|:----------|
| Quién controla el flujo | Tu código llama a la biblioteca | El framework llama a tu código |
| Principio | Reutilizás funciones cuando las necesitás | Adoptás una estructura y reglas predefinidas |
| Flexibilidad | Alta: usás solo lo que querés | Baja: seguís la convención del framework |
| Curva de aprendizaje | Menor | Mayor |
| Ejemplos | Bibliotecas de utilidades para fechas, formato, peticiones | React, Angular, Vue (frontend); Express, Django, Spring (backend) |
| Analogía | Caja de herramientas que abrís cuando querés | Empresa constructora que dirige el proceso |

La diferencia central se resume en la inversión de control: con la biblioteca, vos llamás; con el framework, te llaman a vos.

### SQL vs NoSQL

| Característica | SQL (relacional) | NoSQL (documental) |
|:---------------|:-----------------|:-------------------|
| Organización | Tablas con filas y columnas | Documentos flexibles (formato JSON) |
| Esquema | Fijo y definido de antemano | Flexible, puede variar |
| Relaciones | Muy buenas entre tablas | Menos énfasis en relaciones |
| Consistencia | Alta, garantizada | Puede relajarse en favor de la velocidad |
| Ejemplos | MySQL, PostgreSQL | MongoDB |
| Momento de uso | Datos estructurados y relacionados | Datos variables y de gran volumen |

## Fuentes

### MDN Web Docs - JavaScript (español)

Documentación oficial de Mozilla sobre el lenguaje JavaScript, la base de todo desarrollo web moderno.

https://developer.mozilla.org/es/docs/Web/JavaScript

### FreeCodeCamp en español - Diferencia entre framework y librería

Explicación clara en español de la diferencia entre framework y biblioteca, centrada en el concepto de inversión de control.

https://www.freecodecamp.org/espanol/news/diferencia-entre-framework-y-libreria/

### Git - Documentación oficial

Página oficial de documentación de Git, donde se explica el sistema de control de versiones más usado del mundo.

https://git-scm.com/doc

## Para practicar

1. Elegí una aplicación que uses todos los días (por ejemplo, una red social o una app de mensajería). Identificá qué parte creés que sería el frontend y cuál el backend. No necesitás saber las tecnologías exactas: solo pensá qué capa ve el usuario y cuál procesa los datos.

2. Explicá con tus palabras, sin usar términos técnicos, la diferencia entre una biblioteca y un framework. Si podés contársela a un compañero que no estudió el tema, la entendiste.

3. Investigá en la web qué significa que Node.js "permite ejecutar JavaScript fuera del navegador" y anotá por qué eso habilita usar JavaScript tanto en el frontend como en el backend.

4. Elegí dos lenguajes de esta lista (JavaScript, Python, Java) y buscá en qué tipo de aplicaciones se usan con más frecuencia. Compará tus hallazgos con lo que vimos en este material.

5. Reflexioná: ¿en qué situación elegirías una base de datos SQL y en cuál una NoSQL? Pensá en dos ejemplos de la vida real de cada una y justificá tu decisión.

6. Simulá mentalmente el recorrido de una petición en un sistema web: el usuario toca un botón, el frontend pide datos al backend por una API, el backend consulta la base de datos y devuelve la respuesta. Escribí el recorrido en cinco pasos con tus palabras.
