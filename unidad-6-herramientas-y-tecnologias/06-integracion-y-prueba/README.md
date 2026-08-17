# Integración y prueba

## Introducción

Imaginate que estás armando una aplicación de principio a fin: por un lado tenés el frontend (lo que ve el usuario), por otro el backend (la lógica de negocio) y por otro la base de datos (donde se guarda la información). Cada una de esas partes se puede desarrollar por separado, pero la aplicación en serio funciona recién cuando las tres trabajan juntas, como un solo equipo. Y ahí está el problema: muchas veces cada pieza funciona bien por su cuenta, pero cuando se conectan, aparece el desastre.

"Integración y prueba" es justamente el tema que se encarga de eso: de unir las capas y de verificar que el conjunto completo haga lo que tiene que hacer. En esta unidad vas a entender por qué testear no es un trámite molesto que se hace al final del proyecto, sino una parte fundamental del ciclo de desarrollo. Vas a conocer la pirámide de testing, los distintos tipos de pruebas, el desarrollo guiado por pruebas (TDD), y cómo la integración continua (CI) y la entrega continua (CD) permiten integrar y publicar el software de forma automática.

Este material es de enfoque conceptual: no vamos a escribir código, sino a entender las ideas, los porqués y el vocabulario que vas a usar como desarrolladora o desarrollador profesional.

## Conceptos clave

### ¿Por qué es importante integrar y probar el conjunto?

Desarrollar una aplicación en capas (frontend, backend, base de datos) es ordenado, pero cada capa por separado no te sirve de nada si no se comunican bien. El frontend puede mandar un formulario, el backend puede validar datos y la base de datos puede guardar registros, pero si el formato de la fecha que manda el frontend no lo entiende el backend, todo se rompe.

Probar el conjunto permite detectar problemas de conexión entre las capas: contratos de API que no coinciden, datos que se pierden en el camino, campos que llegan vacíos, permisos mal configurados. Cuanto antes se detecten estos problemas, más barato (en tiempo y dinero) es corregirlos. Encontrar un bug después de que el software está en producción cuesta muchísimo más que encontrarlo durante el desarrollo.

### El testing como parte del ciclo de desarrollo

Durante mucho tiempo se pensó que las pruebas eran una etapa final: primero se desarrollaba todo y después se probaba. Ese enfoque (a veces llamado "waterfall" o cascada) es riesgoso, porque los errores se acumulan y aparecen todos juntos al final.

Hoy el testing se integra a lo largo de todo el ciclo de desarrollo. Se escribe y se ejecutan pruebas constantemente, en paralelo con la escritura del código. Esto tiene varias ventajas: el código queda más estable, los errores se detectan apenas se introducen y el equipo gana confianza para hacer cambios sin miedo a romper algo que ya funcionaba.

### La pirámide de testing

La pirámide de testing es una guía visual para pensar cuántas pruebas de cada tipo conviene tener. Se llama pirámide porque tiene forma de triángulo:

- En la **base, ancha**, están las **pruebas unitarias**: son muchas, se ejecutan rápido y son baratas.
- En el **medio** están las **pruebas de integración**: menos que las unitarias, más lentas, pero verifican que las piezas se conecten bien.
- En la **punta, angosta**, están las **pruebas end-to-end** (de extremo a extremo): son pocas, lentas y más difíciles de mantener, pero prueban el sistema completo.

La idea es tener una base sólida de pruebas unitarias y usar las de integración y las end-to-end con moderación, solo donde aportan más valor. No conviene construir la pirámide al revés (muchas pruebas end-to-end y pocas unitarias), porque se vuelve lenta y frágil.

### Pruebas unitarias (unit tests)

Las pruebas unitarias verifican la unidad más pequeña de código, normalmente una función o un método, de forma aislada. El objetivo es comprobar que una pieza lógica hace exactamente lo que debería: si le doy tal entrada, me devuelve tal salida. Son rápidas, se ejecutan en milisegundos y corren constantemente.

Su gran ventaja es que aíslan el problema: si una prueba unitaria falla, sabés exactamente qué función está fallando y por qué. También funcionan como documentación viva del comportamiento esperado de tu código.

### Pruebas de integración (integration tests)

Las pruebas de integración verifican que dos o más componentes funcionen bien juntos. Por ejemplo, que el backend se comunique correctamente con la base de datos, o que el frontend llame bien a un endpoint de la API. Aquí ya no trabajamos con una función aislada, sino con la conexión entre piezas.

Son un poco más lentas que las unitarias porque implican más infraestructura (bases de datos de prueba, servidores, etc.), pero detectan el tipo de problemas que las unitarias no pueden ver: contratos rotos entre componentes.

### Pruebas de sistema (system tests) y de aceptación / end-to-end

Las **pruebas de sistema** verifican el sistema completo como una unidad, simulando un uso real pero aún en un ambiente controlado. Buscan confirmar que todo el software, con todas sus capas integradas, cumple los requisitos funcionales.

Las **pruebas de aceptación / end-to-end** (de extremo a extremo) simulan el recorrido completo de un usuario real: desde abrir el frontend, hacer clic, completar un formulario, hasta que la información se guarda y vuelve a mostrarse. Son las que más se parecen a la experiencia real del usuario, pero también las más lentas y las que más mantenimiento requieren. Por eso, según la pirámide, se usan en poca cantidad.

### Desarrollo guiado por pruebas (TDD, Test-Driven Development)

El TDD (por sus siglas en inglés, Test-Driven Development) invierte el orden tradicional: en lugar de escribir el código y después las pruebas, primero se escribe la prueba y después el código que la hace pasar.

El ciclo es simple y se repite en tres pasos (rojo, verde, refactor):

1. **Escribís una prueba que falla** (porque todavía no existe el código): es el estado "rojo".
2. **Escribís el código mínimo necesario para que la prueba pase**: es el estado "verde".
3. **Refactorizás** el código para mejorarlo, siempre con la prueba pasando para asegurarte de que no rompiste nada.

El TDD obliga a pensar primero en el comportamiento esperado y da mucha confianza, porque cada pedacito de código nace acompañado de su prueba.

### Integración continua (CI) y entrega continua (CD)

La **integración continua** (CI, Continuous Integration) es una práctica por la cual todo el equipo integra su código en un repositorio compartido de forma frecuente (varias veces al día), y cada integración se verifica automáticamente con compilación y pruebas. Si algo rompe, el equipo lo sabe al instante y lo arregla rápido, en lugar de descubrirlo semanas después.

La **entrega continua** (CD, Continuous Delivery) va un paso más allá: además de integrar y probar de forma automática, el software queda listo para publicarse en cualquier momento con un solo comando. Incluso puede llegar a la **implementación continua** (Continuous Deployment), donde cada cambio aprobado se publica en producción automáticamente, sin intervención manual.

CI y CD se apoyan en las pruebas: si no tenés una buena base de tests, no podés confiar en la automatización.

### Ambientes de pruebas y producción

En un desarrollo serio no existe un solo "lugar" donde corre el software. Se separan ambientes para proteger la información real y poder probar con tranquilidad:

- **Ambiente de desarrollo**: donde los desarrolladores trabajan a diario.
- **Ambiente de pruebas / integración**: donde se integran y prueban las piezas antes de liberar, con datos de prueba.
- **Ambiente de producción**: donde corre el software real, con datos reales, usado por los usuarios finales.

Separar estos ambientes evita que una prueba rompa datos reales y permite validar los cambios en condiciones seguras antes de exponerlos al público.

### Control de calidad (QA) y buenas prácticas de testing

El control de calidad (QA, Quality Assurance) es el proceso y el rol dedicado a asegurar que el software cumpla con los estándares de calidad antes de salir. Va más allá de "encontrar bugs": se trata de prevenirlos, definiendo procesos, estándares y estrategias de prueba.

Entre las buenas prácticas de testing se destacan: escribir pruebas claras y con nombres descriptivos, mantenerlas independientes (que no dependan del orden de ejecución), que sean deterministas (mismo resultado siempre), ejecutarlas con frecuencia y de forma automatizada, y mantener un equilibrio según la pirámide (muchas unitarias, menos integración, pocas end-to-end).

## Analogía

Pensá en el equipo de una cocina de restaurante que prepara un plato de tres pasos: la entrada, el plato principal y el postre.

Cada cocinero prepara su parte por separado y la prueba individualmente. El cocinero de la entrada prueba su plato y le sale perfecto. El del principal, también. El del postre, también. Cada uno por su cuenta es un genio.

Pero cuando llega la hora del servicio, se dan cuenta de que el plato principal se hace en 40 minutos, la entrada en 2, y el postre necesita 30 minutos de frío. Los tiempos no calzan, los platos no se coordinan y el comensal se queda esperando una hora. Ninguna de las partes estaba mal: el problema era la integración.

Las **pruebas unitarias** son cada cocinero probando su plato aislado. Las **pruebas de integración** son verificar que la entrada y el principal se puedan servir en el mismo tiempo de mesa. Las **pruebas end-to-end** son simular un cliente real que come la entrada, espera, recibe el principal y termina con el postre, todo en orden.

Y la **integración continua** sería tener un sistema que, cada vez que un cocinero cambia su receta, le avisa a los demás si eso desacomoda el servicio, antes de que abra el restaurante. Así evitás el desastre de la hora pico.

## Ejemplo práctico

Pensemos en una aplicación típica de una tecnicatura: un sistema de gestión de biblioteca. La arquitectura tiene tres capas:

- **Frontend**: la página web donde el bibliotecario carga un libro nuevo.
- **Backend**: la lógica que valida que el código ISBN tenga el formato correcto.
- **Base de datos**: donde se guardan los libros.

**Pruebas unitarias**: se testea la función del backend que valida el ISBN. Si le paso un ISBN válido, devuelve "ok"; si le paso uno inválido, devuelve un error. Cada caso es una prueba rápida y aislada.

**Pruebas de integración**: se verifica que el backend realmente guarde el libro en la base de datos de prueba, y que cuando el frontend llame al endpoint "crear libro", el backend le responda correctamente con los datos esperados.

**Prueba end-to-end**: se simula al bibliotecario real: abre la web, hace clic en "Nuevo libro", completa el formulario, lo envía, y verifica que el libro aparezca en el listado. Es el recorrido completo de punta a punta.

Si el frontend manda el ISBN como un texto "978-3-16-148410-0" y el backend esperaba un número sin guiones, la prueba unitaria de cada parte no va a detectar nada (cada una pasa). Solo la prueba de integración va a revelar el conflicto de formato entre las capas. Ese es justamente el valor de probar el conjunto.

## Comparativas

### La pirámide de testing

| Nivel | Cantidad | Velocidad | Costo | Qué verifica |
|-------|----------|-----------|-------|--------------|
| Pruebas unitarias | Muchas (base ancha) | Muy rápidas | Bajo | Cada función o método por separado |
| Pruebas de integración | Medianas | Medias | Medio | La conexión entre dos o más componentes |
| Pruebas end-to-end | Pocas (punta angosta) | Lentas | Alto | El sistema completo como lo usa el usuario |

### Tipos de pruebas

| Tipo | Alcance | Objetivo principal |
|------|---------|-------------------|
| Unitaria | Función o método aislado | Verificar comportamiento de una pieza lógica |
| Integración | Conexión entre componentes | Verificar que las piezas se comunican bien |
| Sistema | Sistema completo en ambiente controlado | Confirmar que el todo cumple requisitos funcionales |
| Aceptación / end-to-end | Recorrido real del usuario | Validar la experiencia de punta a punta |

## Fuentes

### Martin Fowler - "Test Driven Development" (inglés)

https://martinfowler.com/bliki/TestDrivenDevelopment.html

Esta fuente explica en detalle el ciclo del desarrollo guiado por pruebas (TDD): escribir la prueba, verla fallar, escribir el código mínimo y refactorizar. Se usó para la sección de TDD.

### Martin Fowler - "Continuous Integration" (inglés)

https://martinfowler.com/articles/continuousIntegration.html

Fuente de referencia clásica sobre integración continua: integrar el código con frecuencia en un repositorio compartido y verificar cada integración de forma automática. Se usó para las secciones de CI y CD.

### Atlassian - "Pruebas automatizadas" / pirámide de testing (español)

https://www.atlassian.com/es/continuous-delivery/software-testing/types-of-software-testing

Guía en español que explica los tipos de pruebas de software y el concepto de pirámide de testing, con el equilibrio entre pruebas unitarias, de integración y end-to-end. Se usó para las secciones de tipos de pruebas y pirámide de testing.

## Para practicar

1. **Dibujá la pirámide de testing** y explicá, con tus palabras, por qué la base debe ser ancha (muchas unitarias) y la punta angosta (pocas end-to-end).

2. **Pensá en un proyecto que ya hayas hecho** (por ejemplo, un sistema de ventas o una biblioteca). Identificá un caso concreto para cada tipo de prueba: una prueba unitaria, una de integración y una end-to-end.

3. **Explicá el ciclo del TDD** a un compañero sin usar tecnicismos. Si podés explicar "rojo, verde, refactor" con un ejemplo de la vida cotidiana, es que lo entendiste.

4. **Debatí**: ¿por qué separar los ambientes de pruebas y de producción? ¿Qué podría pasar si se prueban cambios directamente sobre los datos reales de los usuarios?

5. **Reflexioná sobre CI/CD**: ¿qué ventaja le da a un equipo poder integrar su código varias veces al día y detectar errores al instante, en lugar de juntar todo al final? ¿Qué rol juegan las pruebas en ese proceso automatizado?

6. **Analizá las buenas prácticas**: de la lista de buenas prácticas de testing, elegí dos y explicá con un ejemplo propio por qué son importantes para mantener una suite de pruebas útil y confiable.
