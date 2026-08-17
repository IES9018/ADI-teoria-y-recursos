# Vistas arquitectónicas y escenarios

## Introducción

Cuando hablamos de arquitectura de software, lo primero que tenemos que entender es que **un edificio real no se puede describir con un solo plano**. Necesitamos el plano de la estructura, el plano eléctrico, el plano de plomería, el de ventilación, el de instalación de gas... cada uno muestra el mismo edificio pero desde una perspectiva distinta. Con el software pasa exactamente lo mismo.

Una arquitectura de software es un sistema complejo con muchos interesados (personas que tienen intereses en el sistema): el cliente, el usuario final, el desarrollador, el administrador de sistemas, el responsable de seguridad, el jefe de proyecto. Cada uno de ellos necesita ver la arquitectura "de una manera" que le sirva para su trabajo. Si le mostramos a todos el mismo diagrama, alguno se va a quedar afuera: al desarrollador no le sirve un diagrama de despliegue físico, y al administrador de servidores no le sirve un diagrama de clases.

Por eso nace la idea de **vistas arquitectónicas**: distintas representaciones de la misma arquitectura, cada una pensada para responder las preocupaciones de un grupo de interesados. Y sobre eso hay dos modelos de referencia que vamos a estudiar en este material: el **modelo 4+1** de Philippe Kruchten y el modelo **Views and Beyond** del SEI (Software Engineering Institute).

## Conceptos clave

### El problema de una sola representación

Un sistema de software tiene varios aspectos al mismo tiempo: cómo se organiza en módulos lógicos, cómo esos módulos se reparten entre equipos de desarrollo, cómo se comportan los componentes en tiempo de ejecución, y sobre qué hardware se despliega. Ningún diagrama único puede mostrar todo eso a la vez. Si intentáramos hacerlo, tendríamos un diagrama ilegible y que no le sirve a nadie. Por eso separamos el problema en **vistas**.

### Vista arquitectónica (architectural view)

Es una forma de representar la arquitectura desde una **perspectiva particular**, guiada por las **preocupaciones de un grupo de interesados**. Cada vista es una "foto" del sistema que destaca ciertos aspectos y oculta otros. La vista no es la arquitectura en sí: es una *manera de verla*. Una misma arquitectura puede describirse con muchas vistas distintas, y cada una es correcta dentro de su propósito.

### Modelo 4+1 (4+1 views) de Philippe Kruchten

Propuesto en 1995 en el artículo "Architectural Blueprints – The 4+1 View Model", este modelo describe la arquitectura con **cinco vistas** (cuatro más una). Las cuatro vistas cubren los aspectos lógico, de desarrollo, de proceso y físico. La vista "+1" son los **escenarios**, que sirven para unir y validar a las otras cuatro. Veamos cada una.

#### Vista lógica (logical view)

Describe cómo está estructurado el sistema en términos de **objetos, clases y sus relaciones**, es decir, la funcionalidad que ofrece el sistema a los usuarios. Se enfoca en el "qué hace" el sistema desde el punto de vista de su diseño interno.

- **Diagrama que le corresponde**: diagrama de clases, diagrama de objetos, diagrama de componentes lógicos.

#### Vista de desarrollo (development view)

Describe la organización del software en **módulos, paquetes y subsistemas** desde la perspectiva del programador. Muestra cómo se organiza el código en unidades que pueden desarrollarse por separado, y cómo esas unidades se relacionan (por ejemplo, qué módulo depende de qué otro).

- **Diagrama que le corresponde**: diagrama de paquetes, diagrama de componentes de código, estructura de módulos.

#### Vista de proceso (process view)

Describe el comportamiento del sistema **en tiempo de ejecución**: los procesos, hilos y tareas, cómo se comunican y cómo se sincronizan. Se enfoca en el "cómo se comporta" el sistema cuando está corriendo: concurrencia, rendimiento, distribución de procesos.

- **Diagrama que le corresponde**: diagrama de secuencia, diagrama de actividades, diagrama de comunicación.

#### Vista física (physical view)

Describe **sobre qué hardware** se despliega el software: servidores, computadoras, dispositivos, y cómo se conectan entre sí por la red. Se enfoca en la infraestructura y el despliegue físico del sistema.

- **Diagrama que le corresponde**: diagrama de despliegue.

#### Vista de escenarios (+1) (scenarios / use cases)

Es la vista que **une a las otras cuatro**. Consiste en un conjunto de escenarios o casos de uso que recorren las demás vistas para comprobarlas y validarlas. Un escenario describe una secuencia de interacciones entre los objetos y procesos de las otras vistas. Si un escenario no se puede "contar" con las otras vistas, significa que la arquitectura tiene un problema.

- **Diagrama que le corresponde**: diagrama de casos de uso, diagramas de secuencia para cada escenario.

### Modelo Views and Beyond del SEI

Los autores Clements, Bachmann, Bass, Garlan, Ivers, Little, Nord y Stafford, del SEI (Software Engineering Institute), propusieron en el libro "Documenting Software Architectures" una idea complementaria a la de Kruchten: las vistas **no se describen por sí solas**, sino mediante **documentos de vista** (view documents). Es decir, una vista no es solo un dibujo: es un documento completo con una plantilla que incluye la descripción de los elementos, sus responsabilidades, sus relaciones, la justificación de las decisiones y los atributos de calidad que esa vista ayuda a lograr. A esto se lo llama "Views and Beyond": las vistas, y lo que va más allá de la vista misma.

### Escenarios de atributos de calidad (quality attribute scenarios)

Una vista nos dice cómo está estructurado el sistema, pero ¿cómo sabemos si cumple con los **atributos de calidad** (rendimiento, disponibilidad, seguridad, mantenibilidad)? Para eso existen los **escenarios de atributos de calidad**: descripciones estructuradas de una situación concreta que queremos que el sistema soporte. Un escenario de atributo de calidad tiene partes bien definidas: la **fuente** de estímulo, el **estímulo** (qué llega al sistema), el **artefacto** (qué parte del sistema recibe el estímulo), el **entorno** (en qué condiciones ocurre), la **respuesta** (qué debe hacer el sistema) y la **medida** de la respuesta. Por ejemplo: "Cuando el sistema recibe 100 consultas por segundo (estímulo) en un horario pico (entorno), debe responder en menos de 200 milisegundos (respuesta y medida)". Los escenarios se convierten en los requisitos concretos que validan a las vistas.

### Cómo elegir las vistas según los stakeholders

No hay una cantidad fija de vistas que siempre haya que usar. La regla es: **las vistas se eligen según las preocupaciones de los interesados**. Primero identificamos quiénes son los stakeholders del sistema y qué necesitan saber. Luego elegimos las vistas que respondan a esas preocupaciones. Si un interesado no tiene ninguna vista que le hable, tenemos un problema. La selección de vistas es un acto de diseño: documentamos lo que importa para tomar decisiones y omitimos lo que no aporta valor.

## Analogía

Imaginemos que vamos a construir un **edificio de departamentos**. Hay varios oficios trabajando: el arquitecto, el ingeniero estructural, el electricista, el plomero y el que hace la instalación de gas. Todos trabajan sobre el MISMO edificio, pero cada uno necesita su propio plano:

- El arquitecto necesita el plano de distribución de ambientes (para que la gente viva bien).
- El ingeniero estructural necesita el plano de columnas y vigas (para que no se caiga).
- El electricista necesita el plano de circuitos eléctricos.
- El plomero necesita el plano de cañerías.
- El que instala gas necesita el plano de la red de gas.

Si le damos al plomero el plano de circuitos eléctricos, no puede trabajar. Y si le damos a todos un "plano único", es un caos de líneas que nadie entiende. El software es exactamente igual: cada interesado ve la arquitectura con su propio "plano", es decir, con su vista. Y los escenarios del 4+1 serían, en esta analogía, el "recorrido por el edificio": caminar por cada ambiente para verificar que todo se conecta bien entre sí.

## Ejemplo práctico

Apliquemos el modelo 4+1 a un **sistema de gestión ganadera** que permite a un establecimiento registrar animales, llevar el control sanitario, registrar el peso y administrar los lotes de animales.

**Vista lógica (logical view):** el sistema se organiza en clases que representan el dominio ganadero: `Animal`, `Lote`, `Vacunacion`, `Pesaje`, `Establecimiento`. Estas clases se agrupan en módulos de negocio (gestión de animales, gestión sanitaria, gestión de peso). Esta vista le responde al analista funcional y al diseñador: "así está modelado el problema del campo".

**Vista de desarrollo (development view):** el código se organiza en paquetes por capas: `presentacion` (interfaces), `dominio` (reglas de negocio), `datos` (acceso a la base de datos) y `infraestructura` (conexiones). Cada equipo de desarrollo puede trabajar en un paquete sin pisarse. Esta vista le responde al programador y al líder técnico.

**Vista de proceso (process view):** en tiempo de ejecución, cuando el veterinario registra una vacunación de un lote entero, se lanza un proceso que recorre los animales del lote y actualiza sus registros de forma concurrente. Otro proceso consulta el historial de peso para armar reportes. Esta vista le responde al responsable de rendimiento y al administrador del sistema.

**Vista física (physical view):** el sistema corre en un servidor en el establecimiento (o en la nube), los usuarios lo usan desde una computadora de escritorio en la oficina y desde una tablet en el corral, todos conectados por red. Esta vista le responde al administrador de infraestructura.

**Vista de escenarios (+1):** el escenario "Registrar vacunación de un lote" recorre todas las vistas: la clase `Vacunacion` (lógica), el módulo sanitario (desarrollo), el proceso de actualización masiva (proceso) y el acceso desde la tablet en el corral (física). Si el escenario no se puede contar con las cuatro vistas, la arquitectura tiene un problema.

## Comparativas

| Vista | Preocupación principal | Stakeholder principal |
|:------|:-----------------------|:----------------------|
| Lógica (logical view) | Qué hace el sistema, estructura funcional interna | Analista funcional, diseñador |
| Desarrollo (development view) | Cómo se organiza el código en módulos | Programador, líder técnico |
| Proceso (process view) | Comportamiento en tiempo de ejecución, concurrencia | Arquitecto, responsable de rendimiento |
| Física (physical view) | Sobre qué hardware se despliega | Administrador de infraestructura |
| Escenarios (+1) | Validar y unir las otras vistas | Todos los interesados |

## Fuentes

### Kruchten, P. "Architectural Blueprints – The 4+1 View Model"

Artículo original de Philippe Kruchten donde se presenta el modelo 4+1, fuente primaria clave de este tema.

https://www.cs.ubc.ca/~gregor/teaching/papers/4+1view-architecture.pdf

### SEI (Software Engineering Institute) – Página de arquitectura de software

Página oficial del SEI con recursos sobre arquitectura de software, documentación de arquitecturas y el modelo Views and Beyond.

https://www.sei.cmu.edu/architecture/

### Bass, L.; Clements, P.; Kazman, R. "Software Architecture in Practice"

Obra de referencia del SEI (libro en línea gratuito) donde se profundiza en atributos de calidad, escenarios y vistas arquitectónicas.

https://www.sei.cmu.edu/architecture/

## Para practicar

1. Para el sistema de gestión ganadera del ejemplo, identifique a los stakeholders de un establecimiento real y qué vista le resultaría más útil a cada uno. Justifique.

2. Escriba un **escenario de atributo de calidad** completo (fuente, estímulo, artefacto, entorno, respuesta y medida) para el atributo "disponibilidad" del sistema ganadero: qué pasa si el veterinario se queda sin conexión en el corral.

3. Explique con sus palabras la diferencia entre la vista lógica y la vista de desarrollo del modelo 4+1. Use el sistema ganadero como ejemplo.

4. Según el modelo Views and Beyond del SEI, ¿por qué una vista no se describe por sí sola? ¿Qué debería contener un documento de vista?

5. Dado el siguiente escenario, determine a qué vista del 4+1 pertenece: "El módulo de datos depende del paquete de infraestructura para obtener la conexión a la base de datos".

6. Investigue: ¿en qué se diferencia el modelo 4+1 de Kruchten del enfoque Views and Beyond del SEI? ¿Son excluyentes o complementarios?
