# Conceptos generales de arquitectura de software

## Introducción

Este material corresponde al tema 1 de la Unidad 2 ("Arquitectura de Software") de la materia Arquitectura y Diseño de Interfaces (ADI), Tecnicatura Superior en Desarrollo de Software, IES 9-018, ciclo 2026.

Si venís de materias como Programación o Modelado de Software, probablemente estés acostumbrado a pensar el código como una lista de tareas: "hago esta función, luego esta otra, y listo". La arquitectura de software te pide un paso atrás. En vez de pensar *cómo se escribe cada función*, te pregunta *cómo se organiza todo el sistema* para que no se te caiga a pedazos cuando crece.

En esta unidad vamos a entender qué es la arquitectura, por qué es tan importante, cuáles son sus piezas fundamentales (componentes, conectores, propiedades), qué es una vista arquitectónica y por qué conviene distinguirla del diseño detallado. Vamos a ir de cero a cien, con analogías, ejemplos concretos y comparaciones.

## Conceptos clave

### ¿Qué es la arquitectura de software? (software architecture)

La definición más citada es la del Software Engineering Institute (SEI) de la Universidad Carnegie Mellon, de los autores Bass, Clements y Kazman en "Software Architecture in Practice". Dice, en esencia, que la arquitectura de software es:

> La estructura o estructuras del sistema, que comprenden los elementos del software, sus propiedades visibles externamente y las relaciones entre ellos.

Vamos a desarmar esta definición palabra por palabra, porque esconde mucho:

- **"La estructura o estructuras"**: un sistema no tiene una sola forma de verse. Según qué nos interese mirar (cómo se reparte en módulos, cómo se comunican los procesos, cómo se despliega en servidores), hablamos de distintas estructuras. Todas juntas forman la arquitectura.
- **"Los elementos del software"**: son los componentes, las piezas que hacen un trabajo (por ejemplo, un módulo que valida stock, un servicio que cobra, una base de datos).
- **"Sus propiedades visibles externamente"**: son las propiedades que un componente "expone" hacia afuera, es decir, qué puede hacer y qué restricciones tiene, sin importar cómo lo implementó por dentro.
- **"Las relaciones entre ellos"**: cómo se conectan, quién depende de quién, quién llama a quién, qué protocolo o contrato usan para comunicarse.

### Por qué importa la arquitectura

La arquitectura no es un dibujo bonito para el final. Es la base de las decisiones más caras del proyecto. De ella depende, en gran medida:

- **El rendimiento** (performance): cómo y dónde se comunican los componentes define cuánto tarda una operación.
- **La seguridad**: dónde vive la validación de acceso, cómo viajan los datos entre componentes, cambia el nivel de exposición.
- **La mantenibilidad**: si los componentes están bien separados, cambiar una parte no rompe el resto.
- **La escalabilidad**: poder agregar servidores o usuarios sin reescribir todo.
- **La disponibilidad**: qué pasa si un componente se cae.

Además, la arquitectura es lo más difícil de cambiar una vez que el sistema está en producción. Corregir un error en una función es barato; cambiar la estructura completa puede costar meses y mucho dinero.

### Componentes, conectores y propiedades (components, connectors, properties)

La arquitectura se describe con tres conceptos centrales:

- **Componente (component)**: es una pieza de software con una responsabilidad clara y una interfaz. Realiza un procesamiento o guarda información. Ejemplos: un módulo de autenticación, un repositorio de clientes, un motor de reportes. Se reconoce por *qué hace* y *qué expone* hacia afuera.
- **Conector (connector)**: es el medio por el cual los componentes se relacionan. No es código de negocio; es el "canal" de comunicación. Ejemplos: una llamada a un procedimiento, un mensaje por cola, una API REST, un evento. Un conector define *cómo* se comunican las piezas.
- **Propiedades**: son características de los componentes y conectores que se pueden medir o exigir, como tiempo de respuesta, disponibilidad, seguridad o el volumen de datos que puede manejar. Estas propiedades suelen estar ligadas a los requisitos no funcionales.

### Vista arquitectónica (architectural view)

Una vista es una forma particular de "leer" la arquitectura, enfocada en un aspecto. Como la arquitectura tiene varias estructuras, se representan con distintas vistas: una vista de módulos (cómo se organiza el código), una vista de componentes y conectores (cómo se ejecutan y comunican en tiempo de ejecución), una vista de despliegue (dónde corre cada cosa: servidores, nube, dispositivos). Cada vista muestra el sistema desde un ángulo y todas juntas dan la imagen completa.

### Requisitos funcionales y no funcionales (functional requirements / non-functional requirements)

- **Requisito funcional**: define *qué* hace el sistema. "El sistema debe registrar una venta", "el sistema debe calcular el total". Se puede probar con una entrada y una salida.
- **Requisito no funcional (o atributo de calidad, quality attribute)**: define *cómo* lo hace: qué tan rápido, qué tan seguro, qué tan disponible, qué tan fácil de mantener. Ejemplos: "la consulta de stock debe responder en menos de 200 milisegundos", "el sistema debe estar disponible el 99,9 % del tiempo", "los datos de acceso deben estar encriptados".

La arquitectura está profundamente ligada a los requisitos no funcionales. Un requisito funcional se puede cumplir con muchas arquitecturas distintas; un requisito no funcional (rendimiento, seguridad) casi siempre obliga a elegir una estructura específica.

### La arquitectura como decisiones de diseño y base para la evolución

La arquitectura es, en el fondo, un **conjunto de decisiones de diseño de alto nivel**: cómo se particiona el sistema, qué tecnologías median la comunicación, qué patrones estructurales se adoptan. Cada una de estas decisiones tiene alternativas y consecuencias, por eso conviene registrarlas y justificarlas (en la práctica se documentan con ADR, "Architecture Decision Records").

Como es la estructura base, también es la **base para la evolución y el mantenimiento**. Cuando aparece un requisito nuevo o un cambio de negocio, es la arquitectura la que dice si el cambio es barato (agregar un componente nuevo) o caro (rediseñar la comunicación entre componentes). Un sistema bien arquitecturado envejece mejor.

### Arquitectura vs. diseño detallado

La arquitectura es la **estructura de alto nivel**: las piezas grandes, sus relaciones y sus propiedades. El **diseño detallado** (design) se ocupa del interior de cada pieza: qué clases hay, qué métodos, qué algoritmos. En el edificio, la arquitectura es el plano estructural general; el diseño detallado es el plano de instalación eléctrica de una habitación. La arquitectura se decide temprano y es cara de cambiar; el diseño detallado se define por pieza y es más flexible.

## Analogía

Pensemos en la **casa o el edificio**, que es la analogía clásica y muy efectiva.

Cuando se construye un edificio hay dos tipos de planos muy distintos:

- **El plano estructural (planos de arquitectura)**: muestra cómo se reparten los ambientes, dónde van los muros de carga, dónde las columnas, cómo se conectan las plantas. Es la decisión de alto nivel: cuántos pisos, cómo se sostiene, cómo circula la gente. Cambiar esto después de construir es carísimo: hay que derribar columnas. En software, este plano es la **arquitectura**.
- **El plano de detalle**: muestra, por ejemplo, cómo se instala la pileta de la cocina o cómo se cablea el tomacorriente de un dormitorio. Es una decisión de bajo nivel, dentro de una pieza concreta. Si me equivoco, muevo el tomacorriente veinte centímetros y listo, es barato. En software, este plano es el **diseño detallado**.

La arquitectura responde preguntas como "¿los muros de carga van de este lado?", es decir, "¿los módulos de negocio se separan de la base de datos?" o "¿el pago y el stock se comunican por un mensaje asíncrono?". El diseño detallado responde "¿qué tipo de caño uso para la pileta?", es decir, "¿qué método debo escribir dentro de esta clase para validar el email?".

Por eso se dice que la arquitectura es el **plano estructural** del sistema: es lo primero que se decide, lo que sostiene todo y lo más costoso de modificar.

## Ejemplo práctico

Apliquemos esto a un **sistema de gestión ganadera**, que podrías estar desarrollando en tu proyecto. Imaginemos un sistema para administrar un campo: registrar animales (con su caravana), llevar la sanidad (vacunas, tratamientos), gestionar los corrales, controlar el stock de forraje y emitir reportes de producción.

**Requisito funcional:** "El sistema debe permitir registrar un animal con su número de caravana, raza, fecha de nacimiento y corral asignado." También: "El sistema debe emitir un reporte mensual de animales vacunados."

**Requisitos no funcionales:** "La carga de un animal debe responder en menos de un segundo." "El sistema debe poder operar con internet inestable en el campo (disponibilidad y tolerancia a fallas)." "Solo el encargado y el veterinario autorizado deben acceder a los datos de sanidad (seguridad)." "El sistema debe poder crecer de un campo con 200 animales a varios establecimientos con miles, sin reescribirse (escalabilidad)."

**Componentes posibles:**
- Un componente `Gestión de animales` (alta, modificación, consulta de caravanas).
- Un componente `Sanidad` (vacunas, tratamientos, historial clínico).
- Un componente `Reportes` (producción, stock de forraje).
- Un componente `Almacenamiento` (la base de datos donde persisten los datos).

**Conectores posibles:** entre `Gestión de animales` y `Almacenamiento` puede haber una API interna o un acceso a repositorio (conector de tipo llamada). Entre `Sanidad` y `Reportes` podría haber un **evento**: cuando se aplica una vacuna, se dispara un evento "vacuna aplicada" que los reportes escuchan, sin que `Sanidad` conozca a `Reportes`. Ese evento es un conector asíncrono.

**Vista arquitectónica:** la vista de componentes y conectores muestra estas piezas comunicándose en tiempo de ejecución. La vista de despliegue muestra dónde corre cada una: el módulo de carga corriendo en una tablet en el campo y la base de datos centralizada en un servidor en la ciudad.

**Decisiones de arquitectura:** separar `Sanidad` del resto (así, cambiar las reglas de vacunación no rompe los reportes), usar eventos para los reportes (así, si el sistema de reportes se cae, el registro de vacunas sigue funcionando), y garantizar que la carga funcione sin conexión (decisión ligada a la disponibilidad).

La arquitectura de este sistema responde a los **requisitos no funcionales**: la separación en componentes ataca la mantenibilidad, el uso de eventos ataca la disponibilidad y la independencia de módulos ataca la escalabilidad.

## Comparativas

### Requisitos funcionales vs. no funcionales

| Aspecto | Requisito funcional | Requisito no funcional (atributo de calidad) |
|:--------|:--------------------|:---------------------------------------------|
| Responde a | Qué hace el sistema | Cómo lo hace |
| Ejemplo | "Registrar un animal con su caravana" | "La carga debe responder en menos de 1 segundo" |
| Prueba | Se verifica con entrada y salida | Se verifica con mediciones de rendimiento, seguridad, etc. |
| Impacto en la arquitectura | Se cumple con casi cualquier estructura | Suele condicionar la estructura elegida |
| Vinculación | Describe funcionalidad | Describe propiedades de los componentes y conectores |

### Arquitectura vs. diseño detallado

| Aspecto | Arquitectura | Diseño detallado |
|:--------|:-------------|:-----------------|
| Alcance | Todo el sistema, piezas grandes | El interior de cada pieza |
| Nivel | Alto nivel (componentes, conectores, propiedades) | Bajo nivel (clases, métodos, algoritmos) |
| Decisiones | Particionado, comunicación, tecnologías | Estructura interna de una clase, detalles de implementación |
| Costo de cambio | Muy alto, tarde y caro | Bajo, localizado y barato |
| Analogía | Plano estructural del edificio | Plano de detalle de una habitación |
| Momento | Se decide al inicio | Se define pieza por pieza |

## Fuentes

### Bass, L.; Clements, P.; Kazman, R. — Software Engineering Institute

Definición oficial de arquitectura de software y conceptos de componentes, conectores, propiedades y vistas arquitectónicas.

- Sitio oficial de la SEI: https://www.sei.cmu.edu/architecture/
- Edición en línea gratuita (Bass, Clements, Kazman, "Software Architecture in Practice"): https://www.dim.uchile.cl/~rgutierrez/Architecture/Book-3.pdf

### Pressman, R. S. — Ingeniería de Software, un enfoque práctico (5.ª ed.)

Para el enfoque de requisitos funcionales y no funcionales, el ciclo de vida del software y el rol de la arquitectura en el proceso de ingeniería.

- PDF gratuito (Internet Archive): https://archive.org/details/ingenieria-del-software-5ta-edicion-roger-s.-pressman

### Fowler, M. — Patterns of Enterprise Application Architecture

Para complementar el concepto de vista arquitectónica y la separación entre componentes y conectores en sistemas empresariales.

- Capítulo introductorio en el sitio de Martin Fowler: https://martinfowler.com/books/eaa.html

## Para practicar

1. Con la definición de la SEI, tomá tu propio proyecto (por ejemplo, el sistema de gestión ganadera) y enumerá al menos **tres componentes**, sus **propiedades visibles externamente** y los **conectores** que los unen.
2. Tomá un sistema que conozcas (una red social, un banco, una app de delivery) y escribí **tres requisitos funcionales** y **tres requisitos no funcionales**. Explicá por qué uno de los no funcionales obliga a una arquitectura particular.
3. Elegí un módulo de tu proyecto y explicá la diferencia entre la **decisión arquitectónica** que lo separa del resto y las **decisiones de diseño detallado** que tocarías dentro de ese módulo (clases, métodos). Justificá cuál es más cara de cambiar y por qué.
4. Dibujá (puede ser a mano o con un diagrama) la **vista de componentes y conectores** de tu sistema y la **vista de despliegue** (dónde corre cada componente). Marca qué conector es síncrono y cuál asíncrono.
5. Pensá una decisión de arquitectura de tu proyecto (por ejemplo, separar sanidad del resto, o usar mensajes asíncronos para reportes). Escribí, como si fuera un ADR, qué alternativa descartaste y qué consecuencias tiene la decisión elegida para el rendimiento, la seguridad y la mantenibilidad.
