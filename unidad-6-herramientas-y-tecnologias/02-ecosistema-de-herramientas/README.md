# Ecosistema de herramientas para el desarrollo

## Introducción

Cuando hablamos de "desarrollo de software" muchas veces imaginamos a una persona escribiendo código frente a una pantalla. Pero la realidad es que el desarrollo profesional moderno es un **trabajo en equipo** que involucra muchísimas herramientas que trabajan juntas, igual que los instrumentos de una orquesta. Cada herramienta cumple una función específica: unas sirven para escribir el código, otras para guardar su historial, otras para probarlo, otras para automatizar su publicación y otras para coordinar el trabajo del equipo.

A ese conjunto de herramientas interconectadas y a las prácticas que las rodean lo llamamos **ecosistema de herramientas para el desarrollo**. Entender este ecosistema es tan importante como saber programar: un desarrollador profesional no solo escribe código, sino que además sabe usar las herramientas que permiten que ese código llegue de forma segura, ordenada y automática hasta los usuarios finales.

En este material vamos a recorrer el **flujo de trabajo (workflow)** de un desarrollador moderno de principio a fin: desde el editor donde escribe el código, pasando por el control de versiones, la gestión de dependencias, la automatización de pruebas y la publicación de la aplicación, hasta las herramientas de colaboración del equipo.

## Conceptos clave

### El flujo de trabajo del desarrollador moderno (workflow)

El workflow es la secuencia de pasos que sigue un desarrollador desde que recibe una tarea hasta que su código llega a producción. Un flujo típico es:

1. El equipo recibe una tarea (por ejemplo, "agregar una pantalla de login").
2. El desarrollador escribe el código en su editor.
3. Guarda los cambios en el control de versiones (Git).
4. Las herramientas de integración continua ejecutan pruebas automáticas.
5. Si todo está bien, el código se publica (entrega continua) en el entorno de producción.

Este flujo parece simple, pero cada paso involucra herramientas específicas que veremos a continuación.

### Editores de código e IDEs

Un **editor de código** es el programa donde se escribe el código fuente. Los editores modernos incluyen resaltado de sintaxis (colores que diferencian palabras clave, variables, textos), autocompletado y herramientas para depurar errores.

Un **IDE** (Entorno de Desarrollo Integrado, del inglés *Integrated Development Environment*) es un editor "potenciado" que además integra otras herramientas del desarrollo en una sola ventana: compilación, depuración, gestión de bases de datos, perfiles de ejecución, etc.

**Visual Studio Code** es el editor más popular de la actualidad. Es liviano, multiplataforma y se puede ampliar con extensiones para prácticamente cualquier lenguaje. Algunos de sus puntos fuertes:

- Terminal integrada.
- Control de versiones Git integrado.
- Extensiones para lenguajes (Python, JavaScript, Java, etc.).
- Depuración (debugging) con puntos de interrupción.

### Control de versiones con Git

El control de versiones es un sistema que registra **todos los cambios** que se hacen a los archivos de un proyecto a lo largo del tiempo, como si fuera una máquina del tiempo. Permite volver atrás, ver quién cambió qué y cuándo, y coordinar el trabajo de varias personas sobre los mismos archivos.

**Git** es el sistema de control de versiones más usado del mundo. Sus conceptos fundamentales son:

- **Repositorio (repository)**: es la "carpeta especial" donde Git guarda todo el historial del proyecto. Puede ser local (en la máquina del desarrollador) o remoto (en un servidor como GitHub o GitLab).
- **Commit**: es una "foto" del estado del proyecto en un momento dado. Cada commit guarda qué cambió, quién lo hizo y un mensaje explicando el cambio. Es como una casilla de guardado en un videojuego.
- **Rama (branch)**: es una línea de trabajo paralela. Permite desarrollar una funcionalidad nueva sin tocar el código principal. La rama principal suele llamarse `main` o `master`.
- **Merge**: es la operación de unir los cambios de una rama con otra. Cuando la funcionalidad de una rama está terminada y probada, se "fusiona" con la principal.
- **Push y Pull**: `push` envía los commits locales al repositorio remoto (sube los cambios). `pull` trae los commits remotos al equipo local (baja los cambios de los compañeros).

### Plataformas GitHub y GitLab

**GitHub** y **GitLab** son plataformas que alojan repositorios Git en la nube. Son el "servidor central" donde el equipo guarda y comparte el código. Además de alojar repositorios, ofrecen herramientas extra muy valiosas: revisión de código (pull requests), gestión de issues, tableros de proyectos e integración continua integrada.

### Gestión de dependencias y gestores de paquetes

Casi ningún proyecto se escribe "desde cero": el desarrollador reutiliza librerías y paquetes creados por otras personas. Una **dependencia** es ese código externo del que nuestro proyecto depende para funcionar.

El **gestor de paquetes** es la herramienta que descarga, actualiza y administra esas dependencias de forma automática. Cada ecosistema de lenguaje tiene el suyo:

- **npm** (Node Package Manager): para JavaScript y Node.js.
- **pip**: para Python.
- **Maven**: para Java.
- **Composer**: para PHP.

El gestor de paquetes también registra qué versiones exactas de cada dependencia se usan, lo que garantiza que todos los desarrolladores del equipo (y los servidores de producción) tengan el mismo entorno.

### Integración continua y entrega continua (CI/CD)

La **integración continua** (*Continuous Integration*, CI) es una práctica que consiste en integrar los cambios de código de todos los desarrolladores de forma frecuente y automática. Cada vez que alguien sube código, se ejecutan automáticamente una serie de tareas (generalmente compilación y pruebas) para detectar errores temprano.

La **entrega continua** (*Continuous Delivery*, CD) extiende esta idea: si las pruebas pasan, el código queda listo para publicarse automáticamente en producción, o se publica directamente.

Esta automatización se define en "pipelines" (tuberías de tareas en serie). Herramientas populares:

- **GitHub Actions**: la solución de CI/CD integrada en GitHub.
- **GitLab CI**: la solución de CI/CD integrada en GitLab.

El beneficio principal es la **velocidad y la confianza**: detectar un error cinco minutos después de escribirlo es mucho más barato que detectarlo un mes después en producción.

### Contenedores (Docker) y orquestación (Kubernetes)

Un **contenedor** es un paquete que incluye la aplicación junto con todo lo que necesita para ejecutarse (librerías, configuraciones, dependencias del sistema). **Docker** es la herramienta más popular para crear y administrar contenedores.

La gran ventaja es la **portabilidad**: si una aplicación funciona en un contenedor en la máquina de un desarrollador, funcionará igual en el servidor de producción, porque el contenedor "lleva su propio mundo" consigo. Elimina el famoso problema del "en mi máquina funciona".

La **orquestación** (con **Kubernetes**) es la administración de muchos contenedores a la vez: decide dónde se ejecuta cada uno, escala la aplicación según la demanda (más copias cuando hay más usuarios), reinicia los que fallan y equilibra la carga. Es una herramienta de nivel más avanzado, pero conviene conocer su existencia y su propósito.

### Testing: pruebas unitarias, de integración y end-to-end

El **testing** (pruebas) es el proceso de verificar que el software se comporta como se espera. Se organiza en niveles según qué tan "grande" es la porción que se prueba:

- **Pruebas unitarias (unit tests)**: prueban la unidad más pequeña de código (una función, un método) de forma aislada. Son rápidas y numerosas.
- **Pruebas de integración (integration tests)**: prueban que varios módulos o componentes funcionen bien cuando se conectan entre sí (por ejemplo, que el módulo de pagos interactúe correctamente con la base de datos).
- **Pruebas end-to-end (e2e)**: prueban el flujo completo del sistema tal como lo usaría un usuario real, de principio a fin (por ejemplo, registrarse, iniciar sesión y hacer una compra).

Cada lenguaje tiene sus herramientas de testing (por ejemplo, Jest para JavaScript, Pytest para Python, JUnit para Java). Las pruebas son la base que le da sentido a la integración continua: sin pruebas automáticas, la CI/CD no tendría nada que verificar.

### Entornos de desarrollo (dev, staging, producción)

Una aplicación suele tener varias **copias** que se usan con distintos fines:

- **Desarrollo (dev)**: el entorno local donde el desarrollador escribe y prueba su código mientras trabaja. Es donde está permitido equivocarse.
- **Staging**: un entorno de prueba que replica lo más fielmente posible al de producción. Allí el equipo prueba la aplicación "como si fuera de verdad" antes de publicarla, con datos y configuraciones cercanas a las reales.
- **Producción (prod)**: el entorno real al que acceden los usuarios finales. Es el entorno crítico: un error aquí afecta a los clientes reales.

La separación de entornos es clave: no se desarrolla ni se prueba en producción, porque los errores de pruebas afectarían a los usuarios reales.

### Herramientas de colaboración

El desarrollo es un trabajo en equipo, y por eso existen herramientas para coordinar el trabajo:

- **Gestión de proyectos**: plataformas como **Jira** o **Trello** permiten organizar el trabajo en tareas (issues) y tableros, asignar responsables, estimar plazos y hacer seguimiento del avance. Es el "pizarrón de tareas" del equipo.
- **Documentación**: plataformas y herramientas (como wikis, Confluence, o simplemente Markdown en el propio repositorio) para documentar el proyecto: cómo instalarlo, cómo está estructurado, decisiones de diseño, etc.

La colaboración no es un "extra": es lo que permite que decenas de personas trabajen sobre el mismo código sin pisarse y manteniendo el proyecto ordenado.

## Analogía

Imaginemos que construir software es como construir un **edificio**:

- El **editor de código / IDE** es la oficina del arquitecto y la mesa de dibujo: el lugar donde se diseña y se plasma el trabajo.
- **Git** es el **plano maestro con su historial**: guarda cada versión de los planos, quién los modificó y cuándo. Las **ramas** son como tener "copias del plano" en distintos escritorios para trabajar en paralelo sin romper el original; el **merge** es cuando se unifican esas versiones en el plano definitivo. El **push/pull** es llevar copias a la oficina central (GitHub/GitLab) y traer las versiones de los colegas.
- Los **gestores de paquetes** (npm, pip) son el **depósito de materiales**: en vez de fabricar cada tornillo o cada viga, los pedimos a proveedores confiables y los incorporamos automáticamente.
- La **CI/CD** es el **control de calidad automático**: cada plano que se entrega pasa por una serie de inspecciones automáticas antes de aprobarse.
- **Docker** es el **contenedor de obra**: cada departamento llega con todos sus muebles y artefactos adentro, listo para funcionar en cualquier edificio sin importar cómo sea el edificio.
- **Kubernetes** es el **administrador del edificio**: decide en qué piso vive cada departamento, cuántos duplicados hacer si hay demanda, y qué hacer si uno falla.
- Los **entornos** son los **distintos edificios**: uno de pruebas (dev), uno de ensayo general (staging) y el edificio final donde viven los inquilinos (producción).
- Las **herramientas de colaboración** (Jira, Trello) son el **cronograma de obra y el pizarrón de tareas**: quién hace qué y en qué plazo.

Todo el ecosistema trabaja junto para que el edificio se construya en orden, sin errores, y se entregue a tiempo.

## Ejemplo práctico

Sigamos el flujo completo de una tarea sencilla: "agregar un botón de 'Guardar' en el formulario de registro".

1. **Planificación**: el equipo registra la tarea en Jira o Trello, la asigna a una desarrolladora y la mueve a la columna "En progreso".
2. **Código**: la desarrolladora abre Visual Studio Code, crea una rama nueva en Git (por ejemplo, `agregar-boton-guardar`) para no tocar la rama principal.
3. **Dependencias**: si necesita una librería nueva (por ejemplo, un ícono), la instala con npm (o pip, Maven, etc.), y el gestor de paquetes la registra automáticamente.
4. **Pruebas locales**: ejecuta las pruebas unitarias en su entorno de desarrollo (dev) para verificar que el botón funciona y que no rompió nada.
5. **Commit y push**: guarda sus cambios con un commit (con un mensaje claro, por ejemplo "Agregar botón de guardar al formulario") y lo envía con push al repositorio remoto en GitHub.
6. **Revisión**: crea una solicitud de revisión (pull request). Un compañero revisa el código y sugiere cambios.
7. **Integración continua**: al subir el código, GitHub Actions ejecuta automáticamente las pruebas del pipeline. Si alguna falla, el equipo se entera al instante.
8. **Deploy en staging**: al aprobarse la revisión, se hace merge de la rama con la principal y la aplicación se publica en el entorno staging para una prueba más realista.
9. **Entrega**: cuando todo se valida, el pipeline de entrega continua publica la versión en producción. El botón llega a los usuarios.
10. **Documentación**: si el cambio es relevante, se actualiza la documentación del proyecto.

Este recorrido muestra cómo las herramientas del ecosistema se encadenan: una sola tarea atraviesa el editor, Git, el gestor de paquetes, las pruebas, la CI/CD, los entornos y las herramientas de colaboración.

## Comparativas

### Los entornos dev / staging / producción

| Aspecto | Desarrollo (dev) | Staging | Producción (prod) |
|---------|------------------|---------|-------------------|
| Objetivo | Escribir y probar código en desarrollo | Probar la app "casi como en producción" | Atender a los usuarios finales |
| Quién accede | Desarrolladores del equipo | Equipo de pruebas y QA | Usuarios reales / clientes |
| Datos usados | Datos de prueba o sintéticos | Datos simulados o copia de producción | Datos reales de los clientes |
| Tolerancia a errores | Alta (es lugar de experimentación) | Media (se usa para validar) | Muy baja (los errores afectan a clientes) |
| Frecuencia de cambios | Continua (a cada momento) | Antes de cada publicación | Baja y controlada |
| Riesgo de fallar | Bajo | Bajo (no hay usuarios reales) | Alto (impacto real) |

### Herramientas por categoría

| Categoría | Ejemplos de herramientas | Función principal |
|-----------|-------------------------|-------------------|
| Editor / IDE | Visual Studio Code, otros IDEs | Escribir y depurar código |
| Control de versiones | Git | Registrar el historial de cambios |
| Plataformas de repositorio | GitHub, GitLab | Alojar y compartir el código |
| Gestores de paquetes | npm, pip, Maven, Composer | Administrar dependencias |
| Integración continua | GitHub Actions, GitLab CI | Automatizar pruebas y publicación |
| Contenedores | Docker | Empaquetar la app con su entorno |
| Orquestación | Kubernetes | Administrar muchos contenedores |
| Gestión de proyectos | Jira, Trello | Organizar tareas del equipo |

### Tipos de pruebas

| Tipo | Qué se prueba | Alcance | Velocidad | Ejemplo |
|------|---------------|---------|-----------|---------|
| Unitarias | Una función o método aislado | Muy pequeño | Muy rápida | El botón llama a la función correcta |
| Integración | Varios módulos conectados | Mediano | Media | El formulario guarda el dato en la BD |
| End-to-end | Flujo completo de usuario | Grande | Lenta | El usuario se registra y compra |

## Fuentes

### Git (documentación oficial)

https://git-scm.com/doc

Documentación oficial del sistema de control de versiones Git. Consultada para los conceptos de repositorio, commit, rama, merge y las operaciones push y pull.

### Docker (documentación oficial)

https://docs.docker.com/

Documentación oficial de Docker. Consultada para explicar el concepto de contenedores y su rol en la portabilidad de las aplicaciones.

### GitHub Docs - "About CI/CD"

https://docs.github.com/es/actions

Documentación oficial de GitHub sobre integración y entrega continua. Consultada para explicar el concepto de CI/CD y su aplicación en GitHub Actions.

## Para practicar

1. **Repositorio inicial**: creá un proyecto simple (aunque sea con un archivo de texto) e inicializá un repositorio de Git. Hacé tu primer commit, creá una rama, hacé un cambio y volvé a la rama principal. Luego uní los cambios con un merge.

2. **Encontrá el gestor de paquetes**: elegí un lenguaje que conozcas (Python, JavaScript, Java o PHP) e investigá cuál es su gestor de paquetes. Averiguá cómo se instala una librería y cómo se registran las dependencias en el proyecto.

3. **Mapeá tu entorno**: para cada entorno (dev, staging, producción) escribí una breve descripción de qué datos usarías, quién accedería y qué tan controlada estaría la publicación.

4. **Simulá un pipeline**: escribí en papel (o en un documento) los pasos que ejecutaría un pipeline de CI/CD para una tarea tuya: qué pruebas correría, en qué orden, y qué debería pasar para que se publique en staging y luego en producción.

5. **Compará las pruebas**: para una funcionalidad que ya hayas programado, identificá qué se probaría con una prueba unitaria, qué con una de integración y qué con una end-to-end.

6. **Explorá GitHub Actions**: con la documentación oficial de GitHub, buscá un ejemplo simple de un workflow de CI/CD y describí en tus palabras qué hace cada sección.

7. **Conectá el ecosistema**: tomá un proyecto tuyo anterior y describí cómo lo "modernizarías" incorporando cada herramienta del ecosistema (control de versiones, gestor de paquetes, CI/CD, entornos y colaboración).
