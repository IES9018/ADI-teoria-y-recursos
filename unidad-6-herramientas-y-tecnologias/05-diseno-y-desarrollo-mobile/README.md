# Diseño y desarrollo mobile

## Introducción

Hoy en día casi todos llevamos un teléfono en el bolsillo, y detrás de cada aplicación que usamos hay un proceso completo que va desde una idea hasta el momento en que tocamos "Instalar" desde la Play Store o la App Store. Pero ese proceso no es mágico ni caótico: es una disciplina de ingeniería y diseño que combina decisiones técnicas, arquitectura de software y mucho trabajo de interfaz.

En este material vamos a recorrer el viaje completo de una app móvil: de dónde sale la idea, cómo se transforma en una interfaz usable, qué tecnologías existen para construirla, cómo se organiza su código internamente, cómo se prueba y, finalmente, cómo llega a las tiendas de aplicaciones. Lo importante es que entiendas el panorama completo: no hace falta que te conviertas en un experto en todas las tecnologías, pero sí que entiendas qué opciones existen, por qué se elige una u otra y qué rol cumple cada pieza del rompecabezas.

Vamos a explicarlo desde cero, con conceptos sencillos y comparaciones de la vida cotidiana, porque la idea es que al final puedas explicarle a un compañero qué significa "desarrollo mobile" sin usar palabras raras.

## Conceptos clave

### Proceso de desarrollo de una app (app development process)

Es el camino completo que recorre una aplicación desde que nace como idea hasta que está disponible para que los usuarios la descarguen. No es un camino lineal sino cíclico: primero se investiga qué necesita el usuario, luego se diseña la interfaz, después se programa, se prueba, se publica y se sigue actualizando. Cada vuelta a ese ciclo mejora la aplicación. Es parecido al ciclo de vida del software que ya viste en materias de ingeniería, pero adaptado a las particularidades del mundo móvil.

### Desarrollo nativo (native development)

Es la forma de desarrollar una app escribiendo código en el lenguaje propio de cada plataforma: Kotlin (o Java) para Android y Swift para iOS. La app se compila directamente en el lenguaje que entiende el sistema operativo, lo que le da acceso directo a todas las funciones del teléfono (cámara, GPS, notificaciones) y un rendimiento óptimo. Su gran desventaja es que necesitás dos equipos de desarrollo (o un equipo que domine dos lenguajes) para cubrir Android y iOS por separado.

### Desarrollo multiplataforma (cross-platform development)

Es una estrategia que permite escribir un solo código y que ese mismo código funcione tanto en Android como en iOS. Herramientas como Flutter o React Native se encargan de "traducir" ese código a cada plataforma. La ventaja es que se ahorra tiempo y costos porque se escribe una sola vez. La desventaja es que, en algunos casos muy específicos, el rendimiento o el acceso a funciones muy particulares del teléfono puede requerir trabajo extra.

### PWA (Progressive Web App)

Una PWA es una aplicación web que se comporta como una app nativa: se puede instalar en el teléfono desde el navegador, funciona sin conexión, puede enviar notificaciones y ocupa un ícono en la pantalla de inicio. No pasa por las tiendas de aplicaciones, se accede por una URL. Es la opción más liviana de todas, ideal para proyectos simples o con presupuesto muy bajo, pero tiene limitaciones en el acceso a funciones avanzadas del hardware y en la experiencia que ofrece a los usuarios.

### Material Design

Es el sistema de diseño oficial de Android. No es un conjunto de reglas arbitrarias sino una guía completa que define cómo deben verse y comportarse las apps de Android: colores, tipografías, tamaños, animaciones, espacios. Sigue los principios del "diseño material": superficies que se superponen, sombras, movimientos que tienen sentido físico. Su objetivo es que todas las apps de Android se vean y se sientan coherentes entre sí y con el sistema.

### Human Interface Guidelines (HIG)

Es la guía de diseño oficial de Apple para iOS. Al igual que Material Design en Android, define cómo deben verse y comportarse las apps en iPhone y iPad: la tipografía del sistema, los iconos, las barras de navegación, los gestos táctiles. Su filosofía es que la interfaz debe ser limpia, priorizar el contenido y usar elementos reconocibles para el usuario.

### Prototipo (prototype)

Es una versión preliminar e interactiva de la app que permite simular cómo funcionará la interfaz sin haber programado todavía. Sirve para probar la experiencia de usuario, validar ideas con usuarios reales y detectar problemas antes de escribir código. Es el equivalente al boceto de un edificio o a la maqueta de un producto.

### Arquitectura de una app móvil

Es la forma en que se organiza internamente el código de la aplicación. La idea central es separar las responsabilidades: por un lado la interfaz (lo que el usuario ve), por otro la lógica de negocio (las reglas y decisiones) y por otro el acceso a los datos (base de datos, servidores). Esta separación hace que el código sea más ordenado, más fácil de probar y más simple de mantener cuando la app crece.

### Estado (state)

Es la información que la aplicación necesita recordar mientras está en uso. Por ejemplo, si el usuario está logueado, qué pantalla está mirando o qué elementos hay en un carrito de compras. La gestión del estado (state management) es la disciplina de decidir dónde vive esa información y cómo se actualiza cuando el usuario interactúa. Un mal manejo del estado es una de las causas más comunes de bugs en las apps.

### Persistencia de datos (data persistence)

Es la capacidad de la app de guardar información de forma permanente, de modo que sobreviva al cierre de la aplicación o al reinicio del teléfono. Puede ser local (guardada en el mismo dispositivo, por ejemplo en una base de datos SQLite) o remota (en un servidor en la nube). Es la diferencia entre que el usuario cierre la app y, al volver, todo siga como estaba o que todo se haya borrado.

### Emulador (emulator)

Es un programa que simula un teléfono dentro de la computadora. Permite ejecutar y probar la app sin necesidad de tener un dispositivo físico. Es muy útil para desarrollo rápido, pero no reproduce exactamente el comportamiento del hardware real. El emulador de Android se llama Android Emulator y el de iOS, Simulator.

### Despliegue (deployment)

Es el proceso final de publicar la aplicación para que los usuarios puedan descargarla. En el mundo móvil esto significa subir la app a las tiendas oficiales: Google Play Store para Android y App Store para iOS. Este proceso implica preparar la app, pasar una revisión de calidad y luego mantenerla con actualizaciones.

## Analogía

Pensemos en el desarrollo de una app móvil como si fuera la construcción de un restaurante.

La idea original es "quiero un restaurante". El proceso de descubrimiento es investigar qué tipo de comida quiere la gente del barrio y qué hace falta. El diseño de la interfaz es el plano del local: dónde van las mesas, dónde la barra, cómo se camina entre las mesas. Ese plano es el prototipo: lo mostrás a clientes potenciales para que te digan si está cómodo antes de gastar plata en construir.

Ahora, la diferencia entre nativo y multiplataforma: es como decidir si vas a construir un restaurante con dos cocinas distintas (una para cada grupo de clientes) o una sola cocina que sirva a todos. La cocina única (multiplataforma) es más barata, pero si un cliente pide algo muy especializado de su región, puede que necesites adaptar recetas.

La arquitectura de la app es la separación del restaurante en zonas: la cocina (lógica y datos), el salón (interfaz) y el mozo que las conecta. Si todo estuviera mezclado en un mismo lugar, cualquier cambio en el menú rompería la atención al cliente.

La gestión del estado es el cuaderno de pedidos del mozo: recordar qué pidió cada mesa, en qué punto está cada plato. La persistencia es la caja registradora que guarda las ventas del día aunque cierres el restaurante.

El emulador es probar el restaurante en una maqueta en miniatura antes de abrir: ves el flujo, pero no sentís el ruido real del local ni el sabor de la comida. El dispositivo real es abrir al público.

Finalmente, el despliegue es inaugurar el local: pasás la inspección de sanidad y de seguridad (la revisión de la tienda), abrís las puertas y, después, seguís ajustando el menú con las actualizaciones.

## Ejemplo práctico

Imaginemos que queremos crear una app de recetas de cocina. Vamos a recorrer el proceso completo, paso a paso, para ver todos los conceptos en acción.

Primero, la investigación: definimos que el usuario quiere buscar recetas por ingrediente y guardar sus favoritas. Con esto claro, diseñamos la interfaz siguiendo la guía de la plataforma elegida. Si apuntamos a Android, usamos Material Design: definimos la paleta de colores, la tipografía y cómo se ven las tarjetas de recetas. Si apuntamos a iOS, seguimos las Human Interface Guidelines de Apple.

Luego creamos un prototipo interactivo: una pantalla con el buscador, una lista de recetas, y el detalle de cada receta con la posibilidad de marcarla como favorita. Lo probamos con un par de personas para ver si encuentran rápido lo que buscan.

Después decidimos la tecnología. Supongamos que tenemos un equipo pequeño y poco presupuesto: elegimos Flutter para escribir una vez y publicar en Android e iOS. Ahora organizamos el código con una arquitectura clara: las pantallas (vistas) por un lado, la lógica que filtra las recetas por otro, y la capa de datos que consulta una base de datos local y un servidor de recetas por otro.

Manejamos el estado de la app: si el usuario toca el corazón de favorito, esa información debe actualizar la pantalla y guardarse. La persistencia local permite que sus favoritos sigan ahí aunque cierre la app.

Probamos en el emulador mientras desarrollamos y, antes de publicar, probamos en un teléfono físico real para verificar el rendimiento, la velocidad y cómo se siente la app en la mano. También hacemos un testeo de usabilidad con usuarios que prueban la app y nos dicen si la experiencia es cómoda.

Finalmente, preparamos el despliegue: generamos la versión de lanzamiento, creamos los íconos y las capturas de pantalla, escribimos la descripción y la subimos a Google Play y a la App Store. Cada tienda revisa la app, la aprueba y la publica. Después, cada vez que mejoramos algo, publicamos una actualización con las notas de qué cambió.

## Comparativas

### Desarrollo nativo vs. multiplataforma vs. PWA

| Criterio | Nativo (Kotlin/Swift) | Multiplataforma (Flutter/React Native) | PWA |
| --- | --- | --- | --- |
| Código para Android e iOS | Dos códigos separados | Un solo código | Un solo código web |
| Rendimiento | Máximo, acceso directo al hardware | Muy bueno en la mayoría de casos | Limitado, depende del navegador |
| Acceso a funciones del teléfono | Completo | Completo (con adaptaciones) | Limitado |
| Distribución | Play Store y App Store | Play Store y App Store | Por URL (navegador) |
| Costo de desarrollo | Más alto (dos equipos) | Medio (un equipo) | Bajo |
| Instalación | Requiere pasar por la tienda | Requiere pasar por la tienda | Se instala desde el navegador |

### Etapas del desarrollo de una app de principio a fin

| Etapa | ¿Qué se hace? | Herramienta / rol | Resultado |
| --- | --- | --- | --- |
| Investigación | Entender al usuario y sus necesidades | Equipo de producto / UX | Requisitos definidos |
| Diseño de interfaz | Definir pantallas según la guía de la plataforma | Diseñador UI | Wireframes y guía visual |
| Prototipado | Simular la interfaz para probar | Herramienta de prototipado | Prototipo interactivo |
| Desarrollo | Escribir el código organizado | Desarrollador / Arquitecto | App funcional |
| Gestión de estado y datos | Manejar información y persistencia | Desarrollador | App que recuerda datos |
| Testeo | Probar en emulador y dispositivo real | Tester / QA | App verificada |
| Despliegue | Publicar en las tiendas | DevOps / Publicador | App disponible para descargar |
| Mantenimiento | Actualizar y corregir | Equipo completo | Mejoras continuas |

## Fuentes

Para este material se usaron las siguientes fuentes oficiales, que son seguras y de documentación verificada:

### Android Developers

Documentación oficial de desarrollo de Android, donde se explica el lenguaje Kotlin, las guías de Material Design y el proceso de publicación en Google Play.

https://developer.android.com/

### Apple Developer

Documentación oficial de desarrollo para Apple, donde se explican Swift, las Human Interface Guidelines y el proceso de publicación en la App Store.

https://developer.apple.com/

### Flutter

Página oficial de Flutter, el framework multiplataforma de Google, con documentación sobre cómo escribir una app que funciona en Android e iOS.

https://flutter.dev/

## Para practicar

Para afianzar lo que aprendiste, te proponemos estos ejercicios:

1. Elegí una app que uses a diario en tu teléfono y describí qué partes creés que son la vista (interfaz), la lógica y los datos. ¿Podés identificar dónde se guarda la información que ves?

2. Compará dos apps del mismo tipo (por ejemplo, dos apps de mensajería) y analizá si creés que una es nativa o multiplataforma según cómo se siente y responde al tocarla. Justificá tu respuesta.

3. Imaginá que te encargan una app para un pequeño negocio local. Explicá en un párrafo qué tecnología elegirías (nativa, multiplataforma o PWA) y por qué, teniendo en cuenta el presupuesto y la cantidad de usuarios.

4. Tomá una app conocida y pensá qué pasaría si no se gestionara bien el estado ni la persistencia. Describí al menos dos fallas concretas que ocurrirían en la experiencia del usuario.

5. Diseñá en papel el prototipo de una app simple (por ejemplo, una lista de tareas). Marcá en tu boceto qué decisiones de interfaz tomaste siguiendo las guías de la plataforma (colores, botones, navegación).

6. Explicá con tus palabras, sin usar términos técnicos, la diferencia entre un emulador y un teléfono real para probar una app, y cuándo usarías cada uno.

7. Investigá en la documentación oficial de Android o de Apple cuáles son los requisitos principales para publicar una app en sus tiendas y resumí los tres pasos más importantes que encontraste.

Recordá que la clave no es memorizar definiciones sino entender el proceso completo: una app no es solo código, es una idea que se diseña, se construye de forma ordenada, se prueba con cuidado y se entrega a los usuarios para seguir mejorándola. Si podés explicarle ese viaje completo a un compañero con tus propias palabras, ya entendiste el tema.
