# Actividades y procesos de arquitectura

## Introducción

En los materiales anteriores vimos qué es la arquitectura de software, por qué importa y con qué herramientas podemos representarla. Ahora nos toca la pregunta que seguramente te estás haciendo: ¿y cómo se hace? ¿De dónde sale una arquitectura? ¿Es algo que se decide de golpe, un día, con una sola persona pensando en un aula?

La respuesta corta es: no. La arquitectura de software **no aparece por arte de magia ni se decide de una sola vez**. Es el resultado de un **proceso** que tiene actividades, pasos, revisiones y decisiones que se van tomando con el tiempo. Y como todo proceso de ingeniería, se puede estudiar, planificar y mejorar.

En esta unidad vas a entender que la arquitectura:
- Se **diseña** siguiendo un proceso con pasos reconocibles.
- Tiene un **ciclo de vida**: nace, crece, se documenta, se evalúa, se implementa, se mantiene y evoluciona.
- Se construye para lograr ciertos **atributos de calidad**, que a veces chocan entre sí y hay que negociar.
- Es responsabilidad de una persona o rol específico: el **arquitecto de software**.
- Puede convivir con metodologías ágiles, aunque eso exige repensar cómo se hace.

No te asustes si al principio ves muchas palabras nuevas. Como siempre en esta materia: primero la idea, después la jerga, y por último el ejemplo. Arrancamos.

## Conceptos clave

### Proceso de diseño arquitectónico (architectural design process)

El proceso de diseño arquitectónico es el conjunto ordenado de pasos que se siguen para transformar los requisitos de un sistema en una **estructura arquitectónica** definida. Es decir, el camino que va de "qué necesitamos construir" a "cómo lo vamos a estructurar".

Según Roger Pressman, en *Ingeniería de Software: un enfoque práctico*, el diseño arquitectónico es una de las primeras actividades del diseño de software: el paso en el que se toma la decisión fundamental de **cómo se va a organizar el sistema en componentes y cómo se van a relacionar esos componentes**. Es el nivel más alto de abstracción del diseño: no estamos hablando todavía de clases, funciones o tablas, sino de grandes piezas y sus conexiones.

Pressman lo plantea como un proceso que incluye estas actividades (que detallamos abajo):
1. **Análisis de dominio.**
2. **Definición del modelo arquitectónico.**
3. **Refinamiento y especificación de la arquitectura.**
4. **Evaluación de la arquitectura.**

La idea clave es que el diseño arquitectónico es **iterativo e incremental**: se va afinando en ciclos, y en cada ciclo se entiende mejor el problema y se toman mejores decisiones.

### Análisis de dominio (domain analysis)

El análisis de dominio es la actividad de **entender el área del problema** antes de proponer soluciones. Consiste en estudiar el contexto en el que va a funcionar el sistema: qué negocio u organización lo va a usar, cuáles son las reglas de ese negocio, qué información maneja, qué sistemas similares ya existen, qué estándares o restricciones aplican.

Para Pressman, analizar el dominio permite construir o reutilizar un **modelo del dominio**: una representación de los conceptos, entidades y reglas de ese mundo. Este modelo es una base de conocimiento compartido que sirve de insumo para el diseño arquitectónico. Es como llegar a conocer el "territorio" antes de dibujar el mapa.

Por ejemplo: si vamos a construir un sistema de gestión de una biblioteca, el análisis de dominio nos obliga a entender qué es un socio, qué es un préstamo, cuáles son las multas, cómo se catalogan los libros, quiénes son los bibliotecarios y qué procesos internos existen. Sin ese conocimiento, cualquier diseño que hagamos va a estar "despegado" de la realidad.

### Definición del modelo arquitectónico (architectural model definition)

Una vez entendido el dominio, hay que **proponer la estructura**. La definición del modelo arquitectónico es la actividad en la que se decide cómo se va a organizar el sistema: qué componentes o módulos habrá, cuáles serán sus responsabilidades y cómo se van a relacionar e intercambiar información.

Es el momento creativo y técnico del proceso: acá se elige el **estilo o patrón arquitectónico** (en capas, cliente-servidor, por microservicios, hexagonal, etc.) y se define el **mapa** general del sistema. Pressman destaca que esta representación se puede analizar en tres perspectivas: la **datos** (cómo se organiza la información), la **comportamiento** (cómo responde el sistema ante eventos) y la **estructura** (cómo se organizan los componentes).

En este punto conviene usar representaciones como el modelo C4 o el diagrama de componentes, que ya vimos en unidades anteriores, para "dibujar" la decisión tomada.

### Refinamiento y especificación de la arquitectura (architecture refinement and specification)

La arquitectura no queda definida en bruto tras el primer diagrama. Hay que **refinarla**: ir agregando detalle a cada componente, verificando que las decisiones sean coherentes, resolviendo conflictos y documentando cada elección. El refinamiento convierte una idea general en una **especificación** clara y comunicable.

La **especificación de la arquitectura** es el documento (o conjunto de documentos) que describe formalmente la estructura del sistema, los componentes, sus interfaces, sus responsabilidades y los atributos de calidad que se comprometieron a cumplir. Es lo que permite que **todos los miembros del equipo hablen del mismo sistema**: arquitectos, desarrolladores, testers y clientes.

Esta especificación es la que después sirve de base para las actividades de evaluación, para la implementación y para el mantenimiento. Sin especificación, la arquitectura queda "en la cabeza" de unos pocos y eso es una receta para el desastre.

### Evaluación de la arquitectura (architecture evaluation)

La evaluación de la arquitectura es la actividad en la que se **comprueba** que la arquitectura propuesta realmente cumple con los requisitos y los atributos de calidad esperados, **antes** de invertir tiempo y dinero en construir el sistema entero.

Es un control de calidad temprano: mucho más barato detectar un error de estructura al principio que corregir un sistema ya implementado. La evaluación suele hacerse con técnicas de revisión (como los escenarios de calidad, que veremos más adelante) y con la participación de revisores, que pueden ser arquitectos senior o el equipo completo.

Pressman insiste en que evaluar la arquitectura es fundamental porque la arquitectura condiciona todo lo que viene después: si la estructura está mal, el resto del esfuerzo se construye sobre una base defectuosa.

### Ciclo de vida de la arquitectura (architecture lifecycle)

La arquitectura no es un artefacto congelado que se produce una vez y queda igual para siempre. Tiene su propio **ciclo de vida**. El Software Engineering Institute (SEI), de la Universidad Carnegie Mellon, describe las actividades de este ciclo:

1. **Comprender los requisitos (understanding the requirements):** antes de diseñar hay que entender qué se necesita, tanto funcional como de calidad.
2. **Crear la arquitectura (creating the architecture):** proponer una o varias soluciones y elegir la más adecuada.
3. **Documentar la arquitectura (documenting the architecture):** dejar por escrito las decisiones y la estructura, para que sea comunicable y perdurable.
4. **Evaluar la arquitectura (evaluating the architecture):** comprobar que cumple con los atributos de calidad.
5. **Implementar la arquitectura (implementing the architecture):** convertir el diseño en código y garantizar que el código respete la arquitectura.
6. **Mantener y hacer evolucionar la arquitectura (maintaining and evolving the architecture):** la arquitectura debe adaptarse a nuevos requisitos, correcciones y cambios tecnológicos a lo largo de la vida del sistema.

Este ciclo no necesariamente se recorre una sola vez en forma secuencial: en la práctica, sobre todo en entornos ágiles, se vuelve a recorrer parcialmente a medida que el sistema crece y cambia.

### Atributo de calidad (quality attribute) y trade-offs

Un **atributo de calidad** es una característica no funcional del sistema que la arquitectura debe garantizar. Son propiedades como el **rendimiento** (performance), la **seguridad** (security), la **disponibilidad** (availability), la **modificabilidad** (modifiability), la **usabilidad** (usability), la **escalabilidad** (scalability) o la **confiabilidad** (reliability).

A diferencia de los requisitos funcionales (qué hace el sistema), los atributos de calidad describen **cómo lo hace** y qué tan bien. Y aquí aparece la parte difícil: **los atributos de calidad suelen chocar entre sí**. Mejorar uno suele empeorar otro. Por ejemplo, hacer un sistema muy seguro (con muchos controles y cifrados) tiende a empeorar su rendimiento. Un sistema muy modificable (con muchos componentes desacoplados) puede volverse más lento o más complejo de desplegar.

A ese equilibrio se lo llama **trade-off**: la decisión consciente de sacrificar algo de un atributo para ganar en otro, de acuerdo con las prioridades del negocio. El arquitecto no puede quererlo todo: tiene que saber qué es lo más importante para cada proyecto y negociar en consecuencia. Pressman y también Bass, Clements y Kazman en *Software Architecture in Practice* destacan que la arquitectura es, en esencia, el resultado de una serie de trade-offs.

### Rol del arquitecto de software (software architect)

El **arquitecto de software** es la persona responsable de las decisiones arquitectónicas del sistema. Es quien define la estructura, elige los estilos y patrones, decide cómo se logran los atributos de calidad y, sobre todo, quien **comunica y justifica** esas decisiones al resto del equipo.

Las responsabilidades del arquitecto incluyen:
- Analizar los requisitos y traducirlos en decisiones estructurales.
- Definir y mantener el modelo arquitectónico.
- Documentar la arquitectura y las decisiones (a menudo con ADR, *Architecture Decision Records*).
- Evaluar la arquitectura y revisar que la implementación la respete.
- Liderar el análisis de trade-offs entre atributos de calidad.
- Actuar como puente entre los intereses técnicos y los del negocio.

Las **habilidades** que necesita no son solo técnicas. Un buen arquitecto combina:
- **Conocimiento técnico:** patrones, estilos, tecnologías, lenguajes.
- **Conocimiento del dominio:** entender el negocio para el que se diseña.
- **Habilidades de comunicación:** explicar decisiones a desarrolladores, clientes y directivos.
- **Pensamiento sistémico:** ver el problema en su totalidad y anticipar consecuencias.
- **Capacidad de negociación:** resolver trade-offs y acordar prioridades.
- **Liderazgo y mentoring:** guiar al equipo sin imponer decisiones a ciegas.

En equipos pequeños el rol puede recaer en una persona que también programa; en equipos grandes puede haber un grupo de arquitectos. Pero el rol existe siempre: alguien tiene que tomar y defender las decisiones de estructura.

### Arquitectura ágil (agile architecture)

La arquitectura ágil es la forma de hacer arquitectura dentro de metodologías ágiles como Scrum o Kanban. El desafío es que el enfoque ágil valora responder al cambio por sobre seguir un plan rígido, y la arquitectura tradicional a veces se asociaba a un diseño masivo previo. La arquitectura ágil busca reconciliar ambas cosas.

Los principios de la arquitectura ágil son:
- **No "big design up front" (BDUF):** no se hace un diseño gigantesco y completo antes de empezar a codificar, porque el riesgo de equivocarse es enorme y el cambio es inevitable.
- **Una base inicial mínima:** sí se define una arquitectura inicial suficiente para arrancar (estructura básica, tecnologías, decisiones clave), pero no todo el detalle.
- **La arquitectura surge y evoluciona:** la arquitectura se va descubriendo y refinando a medida que se desarrolla, en iteraciones cortas y con retroalimentación constante del usuario.
- **El código refleja la arquitectura:** la arquitectura no es solo un documento; está viva en el código y debe mantenerlo limpio y alineado.
- **Refactorización continua:** a medida que se aprende, se reestructura el código para mantener la arquitectura adecuada.

La diferencia clave con el enfoque tradicional es el **momento y la cantidad** de diseño: en el enfoque tradicional se diseña mucho al principio; en el ágil se diseña lo justo para empezar y se sigue diseñando durante todo el proyecto.

### Revisión de la arquitectura (architecture review)

La **revisión de la arquitectura** es un proceso sistemático para evaluar la arquitectura de un sistema, con el objetivo de detectar riesgos, defectos y decisiones cuestionables **antes** de que sea demasiado tarde para corregirlos.

Puede hacerse de varias formas:
- **Interna:** el mismo equipo revisa su propia arquitectura.
- **Externa:** un equipo de revisores independientes (que no participaron del diseño) analiza la arquitectura, aportando una mirada fresca y menos sesgada.
- **Formal:** técnicas estructuradas como los **escenarios de calidad** (quality attribute scenarios), en los que se definen situaciones concretas y se verifica si la arquitectura las soporta.

El SEI es un referente mundial en este tema y promueve métodos formales de evaluación como ATAM (*Architecture Tradeoff Analysis Method*) y CBAM, que se basan en analizar cómo la arquitectura responde a escenarios de atributos de calidad y qué trade-offs implica. La revisión no es un juicio de valor sobre el trabajo, sino un control de calidad que ahorra costos enormes.

## Analogía

Imaginemos que vamos a **construir un edificio de departamentos**.

- El **análisis de dominio** sería estudiar el terreno, el barrio, las ordenanzas municipales, cuánta gente lo va a habitar y qué necesidades tiene. No podemos diseñar sin conocer el lugar.
- La **definición del modelo arquitectónico** es cuando el arquitecto dibuja el plano maestro: cuántos pisos, cómo se distribuyen los departamentos, dónde van las escaleras y los ascensores.
- El **refinamiento y la especificación** es pasar de ese boceto a los planos técnicos detallados, con medidas exactas, materiales y especificaciones para cada especialidad (estructura, electricidad, plomería).
- La **evaluación** es que un ingeniero revise los planos para comprobar que el edificio no se va a caer, que las cargas están bien distribuidas y que cumple las normas. Mucho mejor descubrirlo en el papel que cuando ya está construido.
- Los **atributos de calidad** son cosas como la resistencia sísmica, el aislamiento térmico, la seguridad contra incendios o la accesibilidad. Y acá aparece el trade-off: un edificio muy aislado térmicamente puede costar más y reducir espacio útil. El arquitecto tiene que decidir qué prioriza según el presupuesto y el destino del edificio.
- El **arquitecto de software** es ese arquitecto del edificio: el que decide la estructura, el que negocia con el dueño (el cliente) y el que coordina con los maestros mayores (los desarrolladores).
- La **arquitectura ágil** es como construir el edificio por módulos: en lugar de diseñar todo antes, se construye y se valida un primer sector, se aprende, y se sigue. No es improvisar: es tener un plano inicial claro, pero permitir ajustes mientras se avanza.
- La **revisión de la arquitectura** es el control de obra: un experto que pasa periódicamente a verificar que lo que se está haciendo coincide con el plano y que no haya errores estructurales que después sean carísimos de corregir.

La clave: **el plano no es el edificio, pero sin buen plano el edificio se cae.** La arquitectura es el plano, y el proceso es todo el trabajo que se hace para que ese plano sea bueno.

## Ejemplo práctico

Pongamos en juego el proceso con un caso concreto: el equipo de una tecnicatura decide construir **"SGBiblio"**, un sistema web para gestionar los préstamos de la biblioteca del instituto.

**Paso 1: Análisis de dominio.** El equipo conversa con los bibliotecarios y el personal. Aprende que hay socios (estudiantes y docentes), libros con varios ejemplares, préstamos con fecha de devolución, multas por demora y reservas. Descubre que el sistema más importante es poder saber, en cualquier momento, qué ejemplares hay disponibles. Registra todas estas reglas en un modelo del dominio.

**Paso 2: Definición del modelo arquitectónico.** Con el dominio claro, el arquitecto propone una arquitectura **en capas** (presentación, lógica de negocio, acceso a datos), porque es simple y comprensible para un equipo chico. Define los componentes principales y cómo se comunican. Dibuja el modelo C4 de nivel 1 y 2.

**Paso 3: Refinamiento y especificación.** Se afinan los componentes: se define que la capa de acceso a datos va a usar un repositorio, se elige el motor de base de datos, se especifican las interfaces entre capas y se documenta todo. Se registra cada decisión importante en un ADR (por ejemplo: "decidimos separar la lógica de multas en un módulo propio").

**Paso 4: Evaluación.** Se revisa la arquitectura. Se plantea un escenario de calidad: "¿qué pasa si hay 500 personas consultando el catálogo a la vez en época de inscripción?" Se comprueba que la capa de presentación y la base de datos soportan esa carga o, si no, se ajusta el diseño. Se detecta un riesgo: la capa de multas depende demasiado de la capa de préstamos, y se decide desacoplarla.

Después viene el **ciclo de vida del SEI**: se implementa la arquitectura (el equipo codifica respetando las capas), se mantiene y, cuando el instituto pide una nueva función (por ejemplo, notificaciones por correo a los socios con deudas), la arquitectura **evoluciona**: se agrega un módulo de notificaciones sin romper lo existente.

A lo largo de todo esto, el **arquitecto** lleva adelante las decisiones, negocia con el cliente (el director de la biblioteca) cuáles son los atributos de calidad más importantes (¿es más crítico el rendimiento o la facilidad de cambio?) y coordina al equipo. Y si el proyecto se maneja de forma **ágil**, no se diseña todo SGBiblio de una vez: se define una base inicial (las capas y la tecnología), se entrega primero la función más básica (consultar el catálogo), se valida con el bibliotecario y se va evolucionando la arquitectura en cada sprint.

## Comparativas

### Diseño arquitectónico tradicional vs. Arquitectura ágil

| Aspecto | Diseño tradicional | Arquitectura ágil |
|:--------|:-------------------|:------------------|
| Momento del diseño | Mucho diseño al principio, antes de codificar | Diseño inicial mínimo y diseño continuo |
| "Big design up front" | Sí, se busca definir todo por adelantado | No, se evita explícitamente |
| Cambio de requisitos | Se ve como un riesgo que se intenta evitar | Se espera y se aprovecha como aprendizaje |
| Documentación | Extensa y detallada desde el inicio | Esencial y suficiente, se ajusta con el tiempo |
| Relación con el código | El diseño guía al código desde el comienzo | El código refleja y retroalimenta la arquitectura |
| Refactorización | Se evita, porque el diseño es estable | Es una práctica normal y continua |
| Evaluación | Generalmente al inicio o en hitos grandes | Revisión constante en cada iteración |
| Enfoque | Planificación y control | Adaptación y retroalimentación |

### Proceso de diseño (Pressman) vs. Ciclo de vida (SEI)

| Actividad | Proceso de diseño (Pressman) | Ciclo de vida (SEI) |
|:----------|:------------------------------|:---------------------|
| Comprensión del problema | Análisis de dominio | Comprender los requisitos |
| Propuesta de estructura | Definición del modelo arquitectónico | Crear la arquitectura |
| Registro y detalle | Refinamiento y especificación | Documentar la arquitectura |
| Control de calidad | Evaluación de la arquitectura | Evaluar la arquitectura |
| Puesta en marcha | (se da por supuesta en el diseño) | Implementar la arquitectura |
| Vida del sistema | (fuera del alcance del diseño) | Mantener y evolucionar la arquitectura |

## Fuentes

### Pressman - "Ingeniería de Software, un enfoque práctico"

Pressman, R. S. *Ingeniería de Software, un enfoque práctico* (5ta edición).

https://archive.org/details/ingenieria-del-software-5ta-edicion-roger-s.-pressman

Usado para: el proceso de diseño arquitectónico y sus actividades (análisis de dominio, definición del modelo arquitectónico, refinamiento, especificación y evaluación).

### SEI - Software Engineering Institute (arquitectura de software)

Sitio oficial del SEI sobre arquitectura de software.

https://www.sei.cmu.edu/architecture/

Usado para: el ciclo de vida de la arquitectura (comprender requisitos, crear, documentar, evaluar, implementar, mantener y evolucionar), el rol del arquitecto y la revisión de la arquitectura.

### Bass, L.; Clements, P.; Kazman, R. - "Software Architecture in Practice"

Bass, L.; Clements, P.; Kazman, R. *Software Architecture in Practice*. Referenciado desde el SEI.

https://www.sei.cmu.edu/architecture/

Usado para: los atributos de calidad, los trade-offs y el rol del arquitecto de software.

## Para practicar

1. **Identificá las actividades:** tomá un sistema que conozcas (una app de delivery, la plataforma del instituto, un juego) y describí cómo se aplicarían las cuatro actividades del proceso de Pressman: análisis de dominio, definición del modelo, refinamiento y especificación, y evaluación.

2. **Analizá un trade-off:** elegí dos atributos de calidad que suelen chocar (por ejemplo, seguridad y rendimiento). Escribí un breve párrafo explicando en qué caso priorizarías cada uno y por qué.

3. **Rol del arquitecto:** pensá en un proyecto de tu tecnicatura. ¿Qué habilidades técnicas y no técnicas necesitaría el arquitecto de ese proyecto? Hacé una lista y justificá cada una.

4. **Ciclo de vida del SEI:** describí cómo se recorren las seis actividades del ciclo de vida del SEI en el desarrollo de una aplicación simple de lista de tareas. ¿En qué momento entra cada actividad?

5. **Ágil vs. tradicional:** para un proyecto de tu elección, compará qué harías distinto si lo encarás con enfoque tradicional en vez de ágil. Usá la tabla de la sección de comparativas como guía.

6. **Revisión con escenarios:** inventá un escenario de calidad para un sistema de comercio electrónico (por ejemplo, "durante una promo, entran 10.000 usuarios en 5 minutos") y proponé qué debería verificar la revisión de la arquitectura frente a ese escenario.

7. **Debate:** discutí en grupo: ¿el arquitecto de software debería seguir programando o dedicarse solo a diseñar y coordinar? Fundamentá con ventajas y desventajas.
