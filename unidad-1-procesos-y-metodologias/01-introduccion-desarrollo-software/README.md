# Introducción al desarrollo de software

## Introducción

Si estás leyendo esto, seguramente ya escribiste algún programa en la tecnicatura: un script, una página web sencilla o un pequeño sistema de consola. En ese momento el objetivo era aprender a programar: dominar la sintaxis de un lenguaje, entender variables, funciones, estructuras de control. Pero el desarrollo de software profesional va mucho más allá de "hacer que el código funcione". Este tema te propone dar el salto desde pensar en código a pensar en producto: entender qué se va a construir, para quién, por qué y cómo se va a mantener en el tiempo.

La materia Arquitectura y Diseño de Interfaces (ADI) empieza justamente por acá porque ninguna interfaz, ninguna arquitectura, ningún patrón de diseño tiene sentido si primero no entendemos el proceso completo que convierte una idea en un sistema funcionando. Esta unidad, "Procesos y Metodologías", es la base sobre la que se apoyan todas las demás: primero entendemos cómo se concibe y organiza el desarrollo, y recién después entramos en los detalles de diseño de interfaces, arquitectura web, mobile y herramientas.

Este primer tema es introductorio pero decisivo. Acá vas a aclarar conceptos que usás todos los días sin saber su definición precisa (¿qué es exactamente el software?), vas a entender por qué el software es un producto "especial" que no se puede fabricar como se fabrica una mesa o un auto, y vas a descubrir el verdadero problema del oficio: no es escribir código, sino manejar la complejidad. Si entendés esto desde el principio, todo lo que viene después —ciclos de vida, modelos ágiles, arquitecturas— te va a caer mucho más fácil.

Además, este tema te posiciona profesionalmente. Un desarrollador no es solo alguien que "tira código": es alguien que resuelve problemas usando software de manera ordenada, medible y mantenible. Las empresas no buscan personas que programen lindo; buscan personas capaces de construir software confiable, dentro de un plazo, con un presupuesto y que se pueda seguir modificando años después. Eso es ingeniería de software.

## Conceptos clave

### ¿Qué es el software?

El software (software) es el conjunto de programas, datos, procedimientos y documentación asociada que le indican a una computadora qué hacer. En términos simples: es la parte intangible de un sistema informático, la que no se puede tocar, a diferencia del hardware (hardware), que son los componentes físicos (procesador, memoria, disco, teclado).

Una definición importante de Roger Pressman: el software es tanto un producto como un vehículo para entregar un producto. Como producto, entrega el potencial de cómputo representado por el hardware. Como vehículo, es el medio a través del cual se comunica y se almacena la información.

El software incluye más que código fuente (source code):

- Programas ejecutables que el usuario utiliza.
- Datos que esos programas procesan y generan.
- Documentación técnica (manuales, diagramas, especificaciones).
- Documentación para el usuario (guías, tutoriales).

### ¿Qué es la ingeniería de software?

La ingeniería de software (software engineering) es la aplicación de un enfoque sistemático, disciplinado y cuantificable al desarrollo, operación y mantenimiento de software. No es simplemente "programar": es programar de forma organizada, con procesos, estándares, mediciones y prácticas que permiten obtener resultados predecibles y de calidad.

Pressman define la ingeniería de software como una disciplina que abarca todo el ciclo de vida (life cycle) del software: desde que se identifica una necesidad hasta que el producto se retira. Incluye actividades como análisis de requisitos, diseño, construcción, pruebas, despliegue y mantenimiento.

Los tres principios que la sostienen son:

- Proceso (process): una secuencia de pasos definidos y repetibles.
- Métodos (methods): técnicas y notaciones para realizar cada paso (por ejemplo, cómo modelar, cómo diseñar).
- Herramientas (tools): software que automatiza y asiste los métodos (IDE, gestores de versiones, herramientas de prueba).

### Diferencia entre programa, aplicación y sistema

Son términos que a veces se usan como sinónimos, pero no significan lo mismo:

- Programa (program): un conjunto de instrucciones que la computadora ejecuta para realizar una tarea específica. Es la pieza más pequeña de software. Un programa resuelve una tarea acotada.
- Aplicación (application o app): un programa o conjunto de programas diseñados para que un usuario final realice una tarea concreta. La palabra "aplicación" pone el foco en el uso: una app de pedidos, una app de música. Toda aplicación es software, y suele estar compuesta por uno o varios programas.
- Sistema (system): el conjunto integrado que incluye software, hardware, datos, personas y procesos que trabajan juntos para lograr un objetivo. Un sistema es más amplio que una aplicación: incluye el contexto completo donde el software opera.

La relación es de inclusión: el sistema contiene aplicaciones, y las aplicaciones contienen programas. Por ejemplo, un "sistema de gestión ganadera" puede tener dentro una "aplicación de trazabilidad" que a su vez usa varios "programas" (uno para calcular pesos, otro para emitir certificados).

### El problema de la complejidad del software

Este es el corazón de esta unidad. El software moderno es de las cosas más complejas que el ser humano construye. Pensá: un teléfono, un sistema bancario, un sistema de salud. Miles de millones de líneas de código que deben funcionar juntas sin errores.

La complejidad del software tiene varias caras:

- Complejidad de dominio (domain complexity): el problema real que el software debe resolver suele ser complejo. Entender la lógica de un negocio ganadero, de un banco o de un hospital no es trivial.
- Complejidad de construcción (construction complexity): conectar miles de componentes que interactúan entre sí, manejar estados, sincronizar datos, gestionar concurrencia.
- Complejidad de mantenimiento (maintenance complexity): el software se modifica permanentemente. El 70% o más del costo total de un sistema se gasta después de que se entrega, en corregir errores, adaptar a nuevos requisitos y mejorarlo.

El gran enemigo es la complejidad no controlada: cuando nadie planifica, el código crece desordenado, cada cambio rompe algo, nadie entiende el sistema completo y cada corrección genera más errores. Eso se llama "deuda técnica" (technical debt) y es la pesadilla de cualquier proyecto real. La ingeniería de software existe, en gran parte, para controlar esta complejidad mediante organización, abstracción y disciplina.

### Por qué el software es un producto lógico, no físico

A diferencia de casi todo lo que fabricamos, el software no tiene materia: no pesa, no se desgasta, no se oxida. Esto parece una ventaja, pero genera problemas que la física no tiene.

Pressman destaca características que hacen único al software:

- Es lógico, no físico (logical, not physical): se manifiesta a través del hardware, pero su esencia es intangible. No se puede "fabricar" en serie como bienes físicos.
- No se desgasta (does not wear out): una mesa se raya, un motor se rompe. El software no se desgasta por el uso. Sin embargo, sí se deteriora: se "deteriora" porque se lo modifica para adaptarse a cambios, y esas modificaciones mal hechas introducen errores. Es un deterioro por mantenimiento, no por uso.
- Se construye, no se manufactura (constructed, not manufactured): en una fábrica, el costo está en producir miles de unidades. En software, el costo está casi todo en el diseño y el desarrollo de la primera unidad. "Copiar" un programa es trivial (es un clic), pero "construirlo" por primera vez es lo caro.
- Evoluciona constantemente (evolves): ningún software es "terminado" para siempre. Los requisitos cambian, las tecnologías cambian, y el software debe adaptarse.

Por todas estas razones, el software obedece a la lógica de la ingeniería y no a la lógica de la artesanía. Un artesano puede hacer una pieza única sin planos, confiando en su oficio. Un ingeniero no puede construir un puente o un edificio "a ojo": necesita planos, cálculos, normas, y la obra debe ser reproducible y segura. El software, por su complejidad y por las consecuencias de un error (imaginá un error en un sistema bancario o en un controlador de vuelo), necesita el rigor de la ingeniería.

### ¿Ingeniería o artesanía? El debate

Existe un debate legítimo en la industria entre quienes creen que el software es más una artesanía (craftsmanship) —una disciplina creativa que depende del talento del programador— y quienes creen que debe tratarse como una ingeniería con procesos formales. La realidad está en el medio: el software tiene mucho de arte (diseño, creatividad, criterio), pero los proyectos que importan no pueden depender solo del talento individual. Necesitan proceso, metodología y buenas prácticas para ser confiables, predecibles y mantenibles. Ese equilibrio entre arte e ingeniería es lo que vas a recorrer a lo largo de toda esta materia.

## Analogía

Imaginemos que hay que construir una casa. Hay dos formas de hacerlo.

La forma "artesanal": un albañil llega a un terreno vacío y empieza a poner ladrillos directamente, sin planos. Va decidiendo sobre la marcha dónde van las paredes, dónde las ventanas. Si es muy bueno, la casa quizá quede parada y hasta cumpla su función. Pero el resultado es impredecible: no sabés cuánto va a tardar, cuánto va a costar, si el techo va a soportar, y si querés agregarle una habitación el año que viene, seguramente haya que tirar paredes. Además, si el albañil se enferma, nadie más sabe qué hizo adentro de las paredes.

La forma "ingenieril": antes de tocar un ladrillo, un arquitecto y un ingeniero hacen los planos. Definen las medidas, calculan las cargas, determinan materiales, respetan normas y códigos de construcción. Hay un proyecto (el equivalente al diseño y la documentación), se divide el trabajo en etapas (cimientos, estructura, instalaciones, terminaciones) y cada etapa se revisa. Si el equipo cambia, los planos siguen ahí para que cualquiera continúe. El resultado es predecible, seguro y mantenible.

El desarrollo de software es exactamente igual. El "albañil que pone ladrillos" es el programador que abre el editor y escribe código sin planificar. A veces saca un programa que funciona... hasta que el proyecto crece, aparecen requisitos nuevos y todo se rompe. El "arquitecto" es el profesional de software que, antes de escribir código, planifica: analiza el problema, diseña la estructura, define cómo se van a conectar las partes, documenta las decisiones. Escribir código es solo la etapa de "poner ladrillos"; el verdadero trabajo de ingeniería está en todo lo que viene antes (y después) del código.

La analogía de la casa te va a acompañar toda la carrera: la arquitectura de software es, literalmente, hacer los planos del software antes de construirlo. Por eso esta materia se llama "Arquitectura y Diseño de Interfaces": te está enseñando a dibujar planos, no a poner ladrillos sin orden.

## Ejemplo práctico

Tomemos un proyecto muy cercano a los alumnos de esta tecnicatura: un sistema de gestión para un campo ganadero. La idea es llevar el registro de los animales (bovinos), su peso, su estado de salud, las vacunas aplicadas, los movimientos entre corrales y los certificados de trazabilidad. Un productor quiere dejar de usar planillas de papel y carpetas.

Si "empezamos a codificar" de una (como el albañil sin planos), probablemente hagamos una base de datos con una tabla "animales" y una pantalla para cargar datos. Parece simple... pero aparecen preguntas enseguida:

- ¿Un mismo animal se identifica por número de caravana? ¿Y si se cambia de caravana?
- ¿Qué pasa si un animal se vende o muere? ¿Lo borramos o lo marcamos? ¿Quién necesita ver ese historial?
- ¿Cómo calculamos el peso promedio de un lote? ¿En qué período?
- ¿Quiénes usan el sistema: solo el dueño, o también el veterinario, un administrador, un peón?
- ¿El veterinario accede desde el campo con mala señal o desde una computadora en la oficina? ¿Necesitamos una app mobile o alcanza una web?
- ¿Qué pasa si se corta la electricidad o la conexión? ¿Se pierde la carga del día?

Ninguna de estas preguntas se responde escribiendo código. Se responden con un trabajo previo de análisis y diseño. Veamos cómo lo encararía un ingeniero de software:

1. Análisis de requisitos (requirements analysis): entrevistar al productor y al veterinario para entender qué necesitan realmente. Anotar qué funciones debe cumplir el sistema y cuáles no.
2. Definición del alcance (scope): decidir qué entra en la primera versión (por ejemplo, registro de animales y vacunas) y qué se deja para después (trazabilidad completa, facturación).
3. Diseño (design): decidir cómo se estructura el software. Por ejemplo, separar la parte de datos (base de datos) de la lógica de negocio (cálculos) y de la interfaz (pantallas). Definir qué modelos de datos se necesitan.
4. Modelado (modeling): dibujar los diagramas —por ejemplo, un diagrama de clases o de entidades— para representar "Animal", "Lote", "Vacuna", "Movimiento" y cómo se relacionan. Esto es dibujar los planos antes de construir.
5. Recién después, codificación (coding): traducir ese diseño a código, yendo por partes pequeñas y verificables.
6. Pruebas (testing): confirmar que cada función hace lo que debe y que el sistema no se rompe cuando cambia algo.
7. Despliegue y mantenimiento (deployment and maintenance): poner el sistema en uso y seguir mejorándolo.

Fijate que el código es apenas uno de los pasos, y no el primero. La mayor parte del trabajo del ingeniero está en entender el problema, diseñar la solución y verificar que cumpla lo prometido. Si saltás directo a codificar sin pensar, vas a terminar con un sistema que "anda", pero que no cubre lo que el productor necesita y que es imposible de mantener cuando cambie el negocio. La ingeniería de software es exactamente esto: pensar antes de construir.

## Comparativas

### Programa vs. aplicación vs. sistema

| Criterio | Programa | Aplicación | Sistema |
|----------|----------|------------|---------|
| Qué es | Conjunto de instrucciones | Programa(s) orientados a un usuario | Conjunto integrado de software + hardware + datos + personas |
| Tamaño | Pequeño, una tarea | Mediano, una función | Amplio, un objetivo global |
| Ejemplo | Cálculo del peso de un animal | App de registro de vacunas | Sistema de gestión ganadera completo |
| Enfoque | Ejecutar una tarea | Facilitar una tarea al usuario | Resolver un problema organizacional |
| Se puede tocar | No (lógico) | No (lógico) | No (lógico), pero incluye hardware y procesos |

### Software artesanal vs. software con ingeniería

| Criterio | Software "artesanal" | Software con ingeniería |
|----------|----------------------|-------------------------|
| Planificación | Escasa o nula | Existe un proceso y planos |
| Previsibilidad | Impredecible en costo y tiempo | Procesos y medición lo hacen más predecible |
| Calidad | Depende del talento individual | Asegurada por métodos y pruebas |
| Mantenimiento | Difícil, nadie documentó | Documentado y fácil de modificar |
| Riesgo de fracaso | Alto cuando el proyecto crece | Controlado mediante buenas prácticas |
| Actitud | "Empezar a codificar ya" | "Pensar antes de construir" |

## Fuentes

Todas las fuentes listadas son reales, gratuitas y verificables. Podés consultarlas para profundizar.

### Pressman — Ingeniería de Software, un enfoque práctico (5ta ed.)

Libro clásico y de referencia de la materia. Explica en profundidad los conceptos de esta unidad: qué es el software, sus características (lógico, no se desgasta, se construye y no se manufactura), la ingeniería de software como disciplina, el proceso, los métodos y las herramientas. Ideal para los capítulos 1 y 2.

PDF gratuito (licencia CC0) en Archive.org:
https://archive.org/details/ingenieria-del-software-5ta-edicion-roger-s.-pressman

### Pressman — Ingeniería del Software

Otra edición/copia del mismo autor en formato PDF, alojada en un repositorio académico. Útil como copia alternativa si la anterior no está disponible.

https://escuelaesam.pe/biblioteca/assets/uploads/libro_689d13f16f1dc.pdf

### Manifiesto Ágil (en español)

Documento oficial que define los valores y principios del desarrollo ágil (agile), que verás en temas posteriores de esta unidad. Fue el puntapié para cambiar la manera de pensar el desarrollo de software, alejándolo del exceso de burocracia y acercándolo a la colaboración y a la entrega de valor. Es corto y muy legible.

https://agilemanifesto.org/iso/es/manifesto.html

## Para practicar

1. Tomá un proyecto que hayas hecho en una materia anterior (un programa, una web o un sistema pequeño). Identificá, con tus palabras, cuál fue el "problema" que resolvió y qué información te faltó definir antes de empezar a codificar. ¿Qué hubieras preguntado al usuario primero?

2. Explicá con tus palabras, sin usar términos técnicos, la diferencia entre un programa, una aplicación y un sistema. Usá un ejemplo de tu vida cotidiana (por ejemplo, una app de mensajería y el "sistema" que hay detrás). Si podés explicárselo a un compañero que no sabe nada, lo entendiste.

3. Analizá el ejemplo del sistema ganadero de este material. Proponé tres preguntas más que deberías hacerle al productor antes de diseñar el sistema. ¿Por qué creés que esas preguntas son importantes?

4. La analogía de la casa: llevála a otro rubro. Elegí otro producto construido por humanos (un puente, un edificio, un auto) y explicá qué "planos" necesita que el software también necesita. ¿Qué podría salir mal si se construye sin planos?

5. Reflexioná sobre la frase: "El software no se desgasta por el uso, pero se deteriora con el mantenimiento". ¿Qué creés que significa en la práctica? ¿Qué cuidados debería tener un equipo para que el software no se "deteriore" mientras lo modifica?
