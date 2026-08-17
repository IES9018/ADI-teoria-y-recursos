# Estilos arquitectónicos en el desarrollo de software

## Introducción

En el tema anterior conociste qué es la arquitectura de software: la estructura de un sistema, sus componentes y las relaciones entre ellos. Pero en la práctica, los arquitectos no diseñan cada sistema "desde cero" e inventando todo. Existen soluciones probadas, patrones de organización que se repiten en muchísimos proyectos y que ya demostraron funcionar bien. A eso lo llamamos **estilos arquitectónicos** (architectural style).

Un **estilo arquitectónico** es una *familia de arquitecturas* que comparten una misma forma de organizar sus componentes y un comportamiento común. Es como una "receta base" que nos dice: "los componentes se organizan de tal manera, se comunican de tal forma, y los datos fluyen así". Dentro de un mismo estilo, cada sistema concreto puede ser distinto, pero todos respetan el mismo esquema general.

Entender los estilos arquitectónicos es fundamental porque, al elegir uno, definimos cómo se va a organizar todo el sistema, qué tan fácil será mantenerlo, escalarlo y modificarlo. En esta unidad vas a aprender los estilos más usados en la industria y cuándo conviene aplicar cada uno.

## Conceptos clave

### ¿Qué es exactamente un estilo arquitectónico?

Un estilo arquitectónico define tres cosas básicas:
1. **Un conjunto de elementos**: qué tipos de componentes existen (por ejemplo, capas, servicios, tuberías).
2. **Un conjunto de relaciones**: cómo se conectan y comunican esos componentes.
3. **Un conjunto de restricciones**: qué se puede y qué no se puede hacer dentro de esa organización.

La diferencia entre "arquitectura" y "estilo arquitectónico" es parecida a la de una receta y el plato final: el estilo es la receta genérica (por ejemplo, "arquitectura en capas"), mientras que la arquitectura concreta es el plato terminado aplicado a tu proyecto (tu sistema con sus capas específicas y sus nombres propios).

A continuación vas a conocer los estilos principales que pide el programa.

### Arquitectura en capas (layered architecture)

Es, probablemente, el estilo más conocido y el primero que suele estudiarse. El sistema se divide en **capas** horizontales, donde cada capa tiene una responsabilidad bien definida y solo puede comunicarse con las capas contiguas (la capa de arriba usa los servicios de la de abajo).

Las tres capas clásicas son:
- **Presentación (presentation)**: lo que ve el usuario, la interfaz.
- **Lógica de negocio (business logic)**: las reglas del negocio, el "qué se debe hacer".
- **Datos (data)**: el acceso y almacenamiento de la información.

**Ventajas:** es simple de entender, fácil de desarrollar y de mantener, y favorece la separación de responsabilidades (cada capa hace una sola cosa).

**Cuándo usarla:** en aplicaciones donde el equipo necesita orden y claridad, como sistemas de gestión, CRUDs o aplicaciones corporativas de tamaño pequeño a mediano. Es una excelente puerta de entrada porque es fácil de razonar.

**Desventajas:** si el sistema crece mucho, las capas pueden "engordarse", y el flujo estrictamente de arriba hacia abajo puede volverse rígido para ciertas funcionalidades.

### Arquitectura cliente-servidor (client-server)

En este estilo hay dos roles bien diferenciados:
- **Cliente (client)**: el que solicita servicios o recursos (por ejemplo, una app en el celular o un navegador).
- **Servidor (server)**: el que brinda esos recursos y responde a las solicitudes (por ejemplo, una base de datos o un servidor web).

El cliente y el servidor se comunican a través de la red, normalmente mediante solicitudes y respuestas.

Dentro de este estilo se distinguen dos modelos por cantidad de capas:
- **Modelo de 2 capas (two-tier)**: el cliente se conecta directo al servidor de recursos (por ejemplo, una app que consulta una base de datos).
- **Modelo de 3 capas (three-tier / n-tier)**: se interpone una capa intermedia de aplicación. El cliente habla con la capa de aplicación, y esta con la base de datos. Cuando hay más capas intermedias, se habla de **n-tier**.

**Cuándo usarla:** es la base de casi toda la web moderna. El modelo de 3 capas es muy usado porque separa la interfaz de la lógica y de los datos, permitiendo escalar y mantener cada parte por separado.

### Arquitectura orientada a servicios (SOA) y microservicios (microservices)

En este grupo, el sistema se compone de **servicios**: unidades de software independientes que se comunican entre sí a través de la red (normalmente mediante APIs y protocolos como HTTP).

- **Arquitectura orientada a servicios (Service-Oriented Architecture, SOA)**: organiza el sistema como un conjunto de servicios que colaboran. Suele usar un intermediario central (un bus de servicios) para orquestar la comunicación entre servicios de distintos sistemas. Es una visión más "de empresa", que integra múltiples aplicaciones.

- **Microservicios (microservices)**: es una evolución más fina. Cada microservicio es una pieza pequeña, autónoma y especializada en una sola funcionalidad de negocio, con su propia base de datos y su propio ciclo de vida. Se desarrollan, despliegan y escalan de forma independiente.

**Ventajas:** cada servicio se puede desarrollar, probar, desplegar y escalar por separado, lo que favorece equipos autónomos y despliegues continuos. **Desventajas:** la comunicación por red agrega complejidad (latencias, manejo de fallos) y la gestión de muchos servicios es difícil.

**Cuándo usarla:** microservicios para sistemas grandes, complejos y con equipos que crecen, donde el escalado independiente es clave. SOA para integrar sistemas empresariales existentes.

### Estilo pipes-and-filters (tuberías y filtros)

En este estilo, los **datos fluyen** a través de una cadena de etapas. Cada etapa se llama **filtro (filter)**, que procesa los datos que recibe y los pasa al siguiente; las **tuberías (pipes)** son los canales que conectan un filtro con el siguiente.

Imaginate una línea de producción donde el material pasa de máquina en máquina y cada máquina le aplica una transformación.

**Cuándo usarla:** para procesamiento de datos, transformación de información, análisis de texto o audio, y pipelines en general. Ejemplos clásicos son los filtros de Unix (como concatenar `grep`, `sort`, `head`) y los procesadores de imágenes o flujos de datos.

**Ventajas:** cada filtro es reutilizable y se puede reordenar o agregar sin tocar el resto. **Desventaja:** no es ideal para aplicaciones interactivas con mucha interacción del usuario.

### Estilo basado en eventos (event-driven)

Aquí los componentes **reaccionan a eventos**: cambios o sucesos que ocurren en el sistema (un usuario hizo clic, se cargó un archivo, se modificó un dato). Cuando ocurre un evento, se dispara una acción, sin que el productor del evento tenga que saber quién lo va a consumir.

Un mecanismo muy usado es la **publicación-suscripción (publish-subscribe)**: un componente **publica (publish)** un evento en un canal, y otros componentes que están **suscritos (subscribe)** a ese canal lo reciben y reaccionan. El publicador y el suscriptor no se conocen entre sí.

**Cuándo usarla:** para sistemas con mucha interacción y cambios en tiempo real, como notificaciones, aplicaciones de mensajería, dashboards en vivo, juegos o sistemas donde los eventos surgen de forma impredecible.

**Ventajas:** alta flexibilidad y desacoplamiento (los componentes no se conocen). **Desventaja:** es más difícil de razonar y de depurar, porque el flujo del sistema no es lineal.

### Arquitectura de pizarra (blackboard) y repositorio (repository)

Estos dos estilos comparten la idea de que existe un **dato central compartido** al que acceden varios componentes.

- **Repositorio (repository)**: un almacén de datos central (como una base de datos) que es consultado y actualizado por varios componentes. El flujo de control lo tiene quien accede al repositorio.

- **Pizarra (blackboard)**: es una variante donde un "tablero" central (la pizarra) contiene el estado del problema y varios especialistas lo van actualizando de forma colaborativa para resolverlo de manera incremental. El flujo de control lo disparan los datos de la pizarra.

**Cuándo usarlas:** el repositorio para sistemas donde muchos módulos comparten información (muy común en casi cualquier sistema con base de datos). La pizarra para problemas complejos de razonamiento, como reconocimiento de voz, inteligencia artificial o sistemas expertos.

## Analogía

Pensemos cada estilo como una manera distinta de organizar una oficina o un taller.

- **En capas** es como un restaurante donde el mozo (presentación) solo le habla a la cocina (lógica de negocio), y la cocina le pide los ingredientes al depósito (datos). Cada uno tiene su lugar y su rol.

- **Cliente-servidor** es como pedir una pizza por teléfono: vos sos el cliente, la pizzería es el servidor. En el modelo de 3 capas, el que te atiende el teléfono (capa de aplicación) transmite tu pedido a la cocina (datos).

- **Microservicios** son como un grupo de freelancers especializados: uno solo hace diseño, otro solo hace redacción, otro solo hace programación. Cada uno trabaja por su cuenta, tiene su propia mesa y entregas su parte por internet.

- **Pipes-and-filters** es una línea de producción de una fábrica: el producto crudo entra por un extremo y cada máquina le agrega una transformación hasta llegar al producto final.

- **Basado en eventos** es como un grupo de WhatsApp: cuando alguien manda un mensaje (evento), todos los que están en el grupo (suscritos) lo reciben y reaccionan, sin necesidad de que el que escribió le avise a cada uno personalmente.

- **Pizarra** es una pizarra compartida en una sala de crisis: varios especialistas van escribiendo lo que saben y el problema se va resolviendo entre todos, sumando aportes en la misma pizarra.

## Ejemplo práctico

Imaginemos que queremos desarrollar una **plataforma de streaming de video** como proyecto integrador. Veamos cómo se aplicaría cada estilo.

- **En capas**: la parte de gestión de usuarios se organiza con una capa de presentación (el formulario web), una capa de lógica de negocio (las reglas de registro, contraseñas, planes) y una capa de datos (la tabla de usuarios en la base de datos).

- **Cliente-servidor**: el navegador del usuario (cliente) solicita las películas al servidor web, y este las pide a su vez al servidor de base de datos. Es un modelo de 3 capas.

- **Microservicios**: en lugar de una sola aplicación enorme, tenemos microservicios independientes: uno de catálogo, otro de facturación, otro de recomendaciones. Cada uno se despliega y escala por separado.

- **Pipes-and-filters**: cuando se sube un video, el archivo pasa por etapas: se recibe, se convierte de formato, se comprime y se genera la miniatura. Cada etapa es un filtro que transforma los datos y los pasa a la siguiente.

- **Basado en eventos**: cuando un usuario termina de ver una película, se publica el evento "película vista". Otros componentes suscritos reaccionan: uno actualiza el historial, otro dispara una recomendación, otro envía una notificación.

- **Repositorio**: todos los microservicios comparten datos a través de un catálogo central de películas (el repositorio común), aunque cada uno tenga su base propia para sus datos específicos.

Ningún proyecto real usa un solo estilo puro: casi siempre se **combinan**. Este ejemplo te muestra cómo distintos estilos resuelven distintos problemas dentro de un mismo sistema.

## Comparativas

| Estilo | ¿Cuándo usarlo? | Ventaja principal | Desventaja principal |
|:-------|:----------------|:------------------|:---------------------|
| En capas | Sistemas simples y medianos, CRUDs, aplicaciones de gestión | Orden, claridad, fácil de mantener | Rígido si el sistema crece mucho |
| Cliente-servidor (2 y 3 capas) | Aplicaciones web y de red en general | Separación clara cliente / datos, escalable | Comunicación por red (latencias) |
| SOA | Integración de sistemas empresariales existentes | Reutilización de servicios, integración | Complejo por el intermediario central |
| Microservicios | Sistemas grandes y complejos con equipos que escalan | Independencia total, escalado por servicio | Complejidad de gestión y comunicación |
| Pipes-and-filters | Procesamiento y transformación de datos | Etapas reutilizables y reordenables | No apto para interfaces muy interactivas |
| Basado en eventos | Sistemas en tiempo real, notificaciones, interacción | Alto desacoplamiento, reactivo | Difícil de depurar y razonar |
| Repositorio / Pizarra | Datos compartidos, problemas de razonamiento complejo | Dato central consistente | Puede convertirse en cuello de botella |

**Resumen práctico para elegir:** si el sistema es chico y querés orden, empezá con **capas**. Si es una app web clásica, pensá en **cliente-servidor de 3 capas**. Si es grande y con equipos que crecen, considerá **microservicios**. Si procesás datos en cadena, usá **pipes-and-filters**. Si tenés mucha interacción en tiempo real, usá **eventos**. Y si necesitás un dato compartido entre muchos módulos, tenés **repositorio**.

## Fuentes

Para este material se usaron principalmente las siguientes fuentes (las que resultaron más útiles y verificadas):

### Microsoft Learn (principal, en español)

Guía oficial de Microsoft que presenta los estilos de arquitectura de aplicación: en capas, cliente-servidor, microservicios, basado en eventos y más. Es la referencia principal de este tema por estar en español y estar verificada.

https://learn.microsoft.com/es-es/azure/architecture/guide/architecture-styles/

### Software Architecture in Practice (SEI)

Libro clásico de Bass, Clements y Kazman, referente académico mundial en arquitectura de software, publicado por el Software Engineering Institute (SEI) de la Universidad Carnegie Mellon.

https://www.dim.uchile.cl/~rgutierrez/Architecture/Book-3.pdf
Página oficial del SEI: https://www.sei.cmu.edu/architecture/

### Patterns of Enterprise Application Architecture (Fowler)

Libro de Martin Fowler que aborda patrones de arquitectura de aplicaciones empresariales, útil para profundizar en capas, repositorios y organización de la lógica de negocio.

https://martinfowler.com/books/eaa.html

## Para practicar

1. **Identificar estilos en la vida real.** Elegí tres aplicaciones que uses todos los días (por ejemplo, una red social, un banco online y un juego). Para cada una, intentá identificar qué estilo o estilos arquitectónicos creés que usan y justificá tu respuesta.

2. **Elegir el estilo adecuado.** Tenés que desarrollar un sistema para administrar los turnos de un consultorio médico. ¿Qué estilo elegirías y por qué? Pensalo primero con capas y luego considerá si convendría sumar eventos o microservicios.

3. **Dibujar un diagrama.** Para el sistema de turnos del punto 2, dibujá un diagrama sencillo de la arquitectura en capas: marcá la capa de presentación, la de lógica de negocio y la de datos, y dibujá las flechas de comunicación entre ellas.

4. **Comparar por escrito.** Escribí un párrafo comparando la arquitectura en capas con los microservicios: ¿en qué casos elijo una y en cuáles la otra? ¿Cuál es más fácil de mantener en un proyecto chico?

5. **Pensar en eventos.** ¿Cómo cambiaría el sistema de turnos del consultorio si usaras un estilo basado en eventos? Describí tres eventos posibles (por ejemplo, "se reservó un turno") y qué componentes reaccionarían a cada uno.

6. **Analizar un caso real.** Buscá la sección de estilos de arquitectura en la guía de Microsoft Learn (fuente principal de este material) y leé el detalle de al menos un estilo que te haya quedado dudoso. Tomá apuntes con tus palabras y comentá en el foro de la materia qué aprendiste.

7. **Pregunta de reflexión para el debate en clase:** ¿Por qué casi ningún sistema real usa un único estilo puro? ¿Qué ventajas y riesgos tiene combinar varios estilos en un mismo proyecto?
