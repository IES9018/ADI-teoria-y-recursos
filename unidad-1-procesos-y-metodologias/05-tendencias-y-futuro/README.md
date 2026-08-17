# Tendencias y futuro del desarrollo de software

## Introducción

El desarrollo de software no es un oficio estático: cambia todo el tiempo. Hace veinte años se programaba en oficinas llenas de papel, con entregas que tardaban meses o años, y nadie hablaba de "despliegue continuo" ni de "inteligencia artificial escribiendo código". Hoy el panorama es completamente distinto. En esta unidad vamos a recorrer las tendencias que están moldeando cómo se construye el software moderno: por qué aparecieron, qué problema resuelven y cómo impactan en el trabajo cotidiano de un equipo de desarrollo.

La idea no es que memorices nombres de herramientas ni comandos. La idea es que entiendas el *porqué*: qué necesidad del mundo real hizo que la industria inventara DevOps, los microservicios, los contenedores, la nube, el escalado ágil y los asistentes con inteligencia artificial. Cuando entiendes el porqué, las herramientas se vuelven casi una consecuencia lógica.

## Conceptos clave

### DevOps

**DevOps** es una cultura y un conjunto de prácticas que buscan eliminar la separación entre el equipo de *desarrollo* (dev, los que escriben el código) y el equipo de *operaciones* (ops, los que ponen el software a funcionar en producción y lo mantienen vivo). Antes, el desarrollador "tiraba el código por encima de la pared" y el equipo de operaciones tenía que hacerlo correr, muchas veces peleándose porque "en mi máquina funcionaba". DevOps propone que ambos equipos trabajen juntos, con objetivos compartidos: entregar valor rápido, pero sin romper nada.

Su impacto es enorme: reduce los tiempos de entrega, mejora la calidad porque hay retroalimentación constante, y baja el estrés de los despliegues.

### Integración y entrega continua (CI/CD)

La **integración continua (CI, continuous integration)** es la práctica de integrar el código de todos los desarrolladores en un repositorio compartido varias veces al día, y que cada integración se verifique automáticamente (se compila, se ejecutan pruebas). La **entrega continua (CD, continuous delivery)** va un paso más allá: cada cambio que pasa las verificaciones queda listo para ser desplegado en producción de forma casi automática.

CI/CD es la columna vertebral técnica de DevOps: es lo que permite que los equipos publiquen versiones nuevas varias veces al día sin que el sistema se caiga.

### Microservicios (microservices)

Un **microservicio (microservice)** es un estilo arquitectónico en el que una aplicación se divide en muchos servicios pequeños e independientes, cada uno responsable de una funcionalidad concreta y que se comunica con los demás mediante interfaces bien definidas (generalmente por red). A diferencia de la *arquitectura monolítica* (una sola aplicación gigante que lo hace todo), los microservicios se despliegan, se escalan y se actualizan de forma independiente.

El porqué: cuando un sistema monolítico crece mucho, se vuelve difícil de mantener, cualquier cambio pequeño obliga a re-desplegar todo, y un equipo se pisa con otro. Los microservicios permiten que equipos distintos trabajen y publiquen sus partes sin frenarse entre sí.

### Contenedores y orquestación (Docker, Kubernetes)

Un **contenedor (container)** es una forma de empaquetar una aplicación junto con todas sus dependencias (librerías, configuraciones, sistema operativo mínimo) para que se ejecute de la misma manera en cualquier lugar. **Docker** es la herramienta más conocida para crear y manejar contenedores. La **orquestación** es la gestión automática de muchos contenedores: levantarlos, apagarlos, escalarlos, reiniciarlos si fallan. **Kubernetes** es el orquestador más popular.

El porqué: los contenedores resuelven el clásico "en mi máquina funciona", porque el entorno queda encapsulado dentro del propio contenedor. Y cuando tienes cientos de contenedores corriendo, nadie puede gestionarlos a mano: necesitas un orquestador que lo haga por ti.

### Computación en la nube (cloud computing)

La **computación en la nube (cloud computing)** consiste en usar recursos de cómputo (servidores, almacenamiento, bases de datos, redes) que se alquilan por internet a un proveedor (como AWS, Azure o Google Cloud), pagando solo por lo que se usa, en lugar de comprar y mantener servidores físicos propios.

El porqué: comprar hardware, configurarlo y mantenerlo es caro y lento. La nube permite a cualquier equipo (incluso uno de dos personas) tener una infraestructura profesional, escalarla según la demanda y no preocuparse por el mantenimiento físico. Es la base que hace posibles los contenedores, los microservicios y el despliegue continuo.

### Desarrollo ágil a escala (SAFe)

El **desarrollo ágil a escala** es el intento de aplicar las prácticas ágiles (que ya vimos en temas anteriores, como Scrum) no solo a un equipo, sino a organizaciones grandes con cientos de personas trabajando en muchos equipos a la vez. **SAFe (Scaled Agile Framework)** es uno de los marcos de trabajo (frameworks) más usados para lograr esa coordinación.

El porqué: Scrum funciona muy bien con un equipo de diez personas. Pero una empresa con veinte equipos no puede simplemente hacer veinte Scrums sueltos: necesita coordinar objetivos, dependencias y ritmos. SAFe y otros marcos ofrecen una estructura para que muchos equipos ágiles colaboren hacia un objetivo común.

### Inteligencia artificial en el desarrollo (AI)

La **inteligencia artificial (IA)** está emergiendo como asistente del desarrollador. Hablamos de **asistentes de código** (que sugieren código mientras escribes, como Copilot) y de **generación de código** (que produce fragmentos o funciones completas a partir de una descripción en lenguaje natural). También se usa para revisar código, generar pruebas y documentar.

El porqué: la IA no reemplaza al desarrollador, pero le quita las tareas repetitivas y le da un "compañero que nunca se cansa de sugerir". El desarrollador pasa a enfocarse más en decidir *qué* construir y en revisar la calidad, que en escribir línea por línea desde cero.

## Analogía

Imaginemos que construir software es como preparar un gran banquete en un restaurante.

- **Antes (modelo tradicional):** la cocina (desarrollo) cocina todo el menú durante meses en secreto, y el día de la inauguración lo sirve todo de golpe. Si algo sale mal, el desastre es total y nadie sabe de quién fue la culpa.

- **DevOps y CI/CD:** es como tener una cocina y un salón que se hablan todo el tiempo. Cada plato se prueba y se aprueba al instante, y se sirve apenas está listo, en porciones pequeñas. Si un plato sale mal, se corrige rápido y solo ese plato.

- **Microservicios:** en vez de una sola cocina gigante, tienes varias estaciones pequeñas: una para la carne, otra para los postres, otra para las bebidas. Cada estación trabaja sola, pero se coordina con las demás para armar el menú completo. Si la estación de postres se quema, el resto del restaurante sigue funcionando.

- **Contenedores y Docker:** cada plato viaja en su propia caja hermética con todos sus ingredientes incluidos. Da igual si se abre en la cocina de Córdoba o en la de Buenos Aires: el plato sale igual, porque todo viene dentro de la caja.

- **Kubernetes (orquestación):** es el maître que vigila todas las cajas: si una se queda sin ingredientes, la repone; si llegan muchos clientes, agrega más estaciones; si una se rompe, manda a repararla automáticamente.

- **Nube:** es el galpón que alquilas en vez de comprar. No tenés que construir tu propio edificio con hornos y heladeras; alquilás el espacio que necesitás, lo agrandás cuando hay mucha demanda y solo pagás por lo que usás.

- **IA:** es un ayudante de cocina que te sugiere cómo cortar los ingredientes y te propone recetas completas. Vos seguís siendo el chef que decide qué plato va en el menú y revisa que la receta esté bien.

## Ejemplo práctico

Pensemos en una aplicación típica de la vida real: un sistema de reservas de turnos para consultorios médicos.

**Escenario con todas las tendencias juntas:**

1. El sistema se construye con un equipo pequeño que trabaja de forma ágil (Scrum), entregando funcionalidades en ciclos cortos de dos semanas. Cuando la organización crece a varios equipos (agenda, facturación, notificaciones, historial clínico), se coordinan con un marco como SAFe.

2. Cada parte del sistema se desarrolla como un **microservicio**: el microservicio de "turnos", el de "facturación", el de "recordatorios". Cada uno es independiente: si el de facturación tiene un problema, los pacientes siguen pudiendo sacar turnos.

3. Cada microservicio se empaqueta en un **contenedor (Docker)**, que incluye todo lo que necesita para funcionar. Los contenedores se gestionan con **Kubernetes**, que los levanta, los escala cuando hay mucha demanda de turnos a la mañana temprano, y reinicia automáticamente el que se cae.

4. Todo corre en la **nube**: la organización no compra servidores, alquila capacidad en un proveedor y solo paga por lo que usa.

5. El equipo publica cambios varias veces por semana gracias a **CI/CD**: cada vez que un desarrollador hace un cambio, se ejecutan pruebas automáticas (integración continua) y, si pasan, el cambio queda listo para publicarse (entrega continua). Así, las mejoras llegan a los usuarios rápido y sin romper nada.

6. Por último, el equipo usa un **asistente con IA** para escribir las pruebas automáticas y para sugerir código de las funciones nuevas, lo que les ahorra horas de tarea repetitiva.

## Comparativas

### Desarrollo tradicional vs. DevOps

| Aspecto | Desarrollo tradicional | DevOps |
|:--------|:-----------------------|:-------|
| Relación dev/ops | Equipos separados, con conflicto | Colaboración y objetivos compartidos |
| Frecuencia de publicación | Pocas veces al año | Varias veces al día o por semana |
| Integración del código | Al final del proyecto | Continua, varias veces al día (CI) |
| Pruebas | Al final | Automáticas, en cada cambio |
| Manejo de errores | Se descubren tarde, son costosos | Se detectan temprano, se corrigen rápido |
| Cultura | "Tirar el código por encima de la pared" | Responsabilidad compartida del ciclo completo |

### Arquitectura monolítica vs. microservicios

| Aspecto | Monolito | Microservicios |
|:--------|:---------|:---------------|
| Estructura | Una sola aplicación grande | Muchos servicios pequeños e independientes |
| Despliegue | Se re-despliega todo junto | Cada servicio se despliega por separado |
| Escalado | Se escala la aplicación completa | Solo se escala el servicio que lo necesita |
| Mantenimiento | Difícil cuando crece mucho | Más módulos que gestionar, requiere coordinación |
| Fallo | Un problema puede tumbar todo | Un fallo queda aislado en su servicio |

## Fuentes

### Manifiesto Ágil (español)

Documento fundacional de la cultura ágil, base sobre la que se apoya DevOps, el escalado ágil y gran parte de las tendencias actuales.

https://agilemanifesto.org/iso/es/manifesto.html

### Atlassian - ¿Qué es Scrum? (español)

Explicación clara y didáctica de Scrum, el marco de trabajo ágil que luego se escala con frameworks como SAFe.

https://www.atlassian.com/es/agile/scrum

### Scrum Guide (inglés)

Guía oficial de Scrum, la referencia autorizada del marco sobre el que se construye el desarrollo ágil a escala.

https://scrumguides.org

## Para practicar

1. **Ponete a prueba con tus palabras:** explicá a un compañero, sin usar términos técnicos, por qué DevOps evita el "en mi máquina funciona". Usá la analogía del restaurante.

2. **Caso cotidiano:** identificá un servicio de tu vida diaria (una app de delivery, un banco digital, una red social) y pensá: ¿por qué creés que es más útil para esa empresa usar microservicios en vez de un monolito? ¿Y por qué la nube le conviene?

3. **Comparación:** armá una tabla propia donde compares cómo sería desarrollar un sistema de "gestión de biblioteca" con el modelo tradicional y con el modelo con CI/CD. ¿En qué se nota la diferencia de velocidad y de riesgo?

4. **Reflexión:** si una empresa muy grande (con cientos de desarrolladores) quisiera usar Scrum, ¿qué problemas se le presentarían? ¿Cómo ayuda un framework como SAFe a resolverlos?

5. **Mirada crítica sobre la IA:** buscá un ejemplo de asistente de código y probá usarlo para una función simple. ¿Qué hace bien y qué le costaría? ¿En qué tareas te parece que la IA ayuda más y en cuáles el criterio humano sigue siendo indispensable?

6. **Integración de conceptos:** explicá en un párrafo cómo se relacionan entre sí la nube, los contenedores, la orquestación y los microservicios. ¿Podrían existir los microservicios sin la nube? ¿Y sin contenedores? Justificá tu respuesta.
