# Herramientas de Desarrollo Mobile

## Introducción

Desarrollar una aplicación móvil no es simplemente "escribir código y listo". Detrás de cada app que usás a diario —desde una red social hasta una app de pedidos de comida— hay un conjunto de herramientas que permiten escribir el código, probarlo, diseñar su interfaz, controlar sus versiones y, finalmente, publicarla en las tiendas. En esta unidad vamos a recorrer ese ecosistema de herramientas de principio a fin, entendiendo para qué sirve cada una y por qué es necesaria, sin entrar en detalles de tutorial. Al terminar, vas a poder mirar cualquier aplicación móvil y tener una idea clara de qué herramientas y decisiones estuvieron detrás de su desarrollo.

## Conceptos clave

### Entornos de Desarrollo Integrado (IDE)

Un IDE (Integrated Development Environment, "Entorno de Desarrollo Integrado") es un programa que reúne en un solo lugar todas las herramientas que un desarrollador necesita para programar: un editor de texto, un compilador, un depurador y un gestor de archivos. La idea es que no tengas que saltar entre cinco programas distintos para hacer tu trabajo. En el mundo mobile, los dos grandes IDEs son:

- **Android Studio**: es el IDE oficial para desarrollar aplicaciones Android. Lo provee Google y está pensado específicamente para el ecosistema Android.
- **Xcode**: es el IDE oficial de Apple, exclusivo para desarrollar aplicaciones para iPhone, iPad, Mac y Apple Watch. Solo funciona en computadoras Mac.

Cada uno está atado a su ecosistema: si querés hacer una app para Android, usás Android Studio; si querés una para iPhone, usás Xcode en una Mac.

### SDK (Software Development Kit)

Un SDK, o "Kit de Desarrollo de Software", es un conjunto de herramientas, bibliotecas y documentación que te permiten crear aplicaciones para una plataforma específica. Si el IDE es "la mesa de trabajo", el SDK es "la caja de herramientas" que te deja usar las funciones del dispositivo: la cámara, el GPS, las notificaciones, el almacenamiento, etc. Android Studio incluye el Android SDK, y Xcode incluye el iOS SDK. Sin el SDK correspondiente, el IDE no tendría con qué "hablar" con el sistema operativo del teléfono.

### Emuladores y simuladores

Para probar una app durante el desarrollo no siempre tenés un teléfono a mano. Por eso existen dos herramientas que imitan un dispositivo real:

- **Emulador**: reproduce el comportamiento de un dispositivo, incluida su lógica interna (procesador, memoria, sistema operativo). Android Studio trae el Emulador de Android, que es un emulador.
- **Simulador**: imita la apariencia y el comportamiento de la interfaz, pero no reproduce la lógica interna real del dispositivo. El Simulador de iOS que trae Xcode es un simulador.

La diferencia es técnica y sutil: el emulador "se hace pasar" por el hardware real, mientras que el simulador solo "se parece" en pantalla. En la práctica, ambos sirven para probar sin necesidad de un dispositivo físico.

### Lenguajes de programación móviles

Cada plataforma tiene sus lenguajes de programación oficiales:

- **Android**: históricamente se programó en Java, un lenguaje clásico y muy extendido. Hoy, el lenguaje recomendado por Google es **Kotlin**, más moderno, conciso y con menos errores típicos de Java.
- **iOS**: el lenguaje tradicional es **Objective-C**, que existe desde los años 80 y es la base histórica de las apps de Apple. Actualmente, el lenguaje recomendado es **Swift**, creado por Apple para ser más seguro, legible y fácil de aprender.

En resumen: para Android aprendés Java y/o Kotlin; para iOS aprendés Objective-C y/o Swift. En ambos casos, lo "nuevo" y recomendado es el segundo.

### Frameworks multiplataforma

Desarrollar en nativo significa hacer una app para Android en Kotlin y otra separada para iOS en Swift, dos proyectos distintos. Para no duplicar trabajo, existen los **frameworks multiplataforma**, que permiten escribir un solo código que funciona en ambas plataformas:

- **Flutter**: desarrollado por Google, usa el lenguaje **Dart**. Compila el código directamente al lenguaje de la máquina, lo que da un rendimiento muy parecido al nativo. Sitio oficial: https://flutter.dev/
- **React Native**: desarrollado por Meta (Facebook), usa **JavaScript** (el mismo lenguaje de la web). Permite que desarrolladores web pasen al mundo mobile reutilizando conocimientos.

La gran ventaja de ambos es la **reutilización de código**: un solo equipo escribe una vez y publica en Android e iOS, ahorrando tiempo y dinero.

### Control de versiones

El control de versiones es un sistema que registra cada cambio que se hace en el código, como si fuera un historial con "fotos" de cada momento del proyecto. El más usado es **Git**. Te permite volver atrás si algo se rompe, trabajar en equipo sin pisarse los archivos y mantener un registro de quién hizo qué y cuándo. En el desarrollo mobile es indispensable: los proyectos son grandes, los equipos trabajan en paralelo y los errores deben poder deshacerse.

### Integración continua (CI)

La **integración continua** (Continuous Integration, CI) es una práctica que automatiza la verificación del código cada vez que se hace un cambio. Un servidor revisa automáticamente que el código compile, que los tests pasen y que no haya errores básicos, sin que nadie tenga que hacerlo a mano. En mobile, esto garantiza que cada nuevo cambio no rompa la aplicación y acelera la detección de problemas.

### Herramientas de diseño de interfaz

Antes de programar la interfaz, los equipos la **diseñan**. Para eso se usan herramientas de diseño y prototipado:

- **Figma**: herramienta de diseño de interfaces basada en la web, muy popular porque permite que varios diseñadores trabajen en el mismo archivo en tiempo real y porque sirve tanto para el diseño como para crear prototipos interactivos. Sitio oficial: https://www.figma.com/
- **Adobe XD**: herramienta de Adobe para diseñar interfaces y crear prototipos. También permite diseño, wireframes y animaciones de la interacción.

Estas herramientas no generan el código final, pero definen exactamente cómo debe verse y comportarse la app, y sirven de guía para los programadores.

### Testeo de aplicaciones móviles

Probar una app es verificar que funcione bien antes de lanzarla. Existen dos grandes maneras:

- **Pruebas en emulador/simulador**: rápidas y sin costo de hardware, ideales para las primeras etapas.
- **Pruebas en dispositivos reales**: imprescindibles al final, porque solo un teléfono real muestra cómo se comporta la app con batería, red, pantallas reales y sensores de verdad.

Además del testeo técnico existe el **testing de usabilidad**, que evalúa qué tan fácil y cómoda es la app para las personas que la usan. Una app puede funcionar perfecto en lo técnico y aun así ser difícil de usar; la usabilidad se encarga de ese aspecto humano.

### Despliegue en las tiendas

Una vez terminada y probada, la app se publica:

- **Play Store**: la tienda oficial de Android, donde se publican las apps para Android. El proceso lo administra Google.
- **App Store**: la tienda oficial de Apple, para publicar apps de iOS. El proceso es más estricto y controlado.

Publicar en una tienda no es solo "subir el archivo": hay que preparar los íconos, las capturas de pantalla, las descripciones y, en algunos casos, pasar por una revisión del equipo de la tienda. Es la puerta de entrada final hacia los usuarios.

## Analogía

Imaginá que querés construir y vender una casa.

- El **IDE (Android Studio o Xcode)** es tu mesa de trabajo con todas tus herramientas ordenadas en un solo lugar: el martillo, la sierra y el nivel están a mano.
- El **SDK** es la "caja de herramientas del oficio": no cualquier martillo sirve, necesitás las herramientas específicas de esa plataforma para trabajar su material.
- El **emulador/simulador** es una maqueta de la casa. Podés ver cómo va quedando y moverte por las habitaciones, pero no es la casa real.
- Los **lenguajes de programación (Kotlin, Swift)** son los materiales de construcción: el ladrillo y el cemento con los que se levanta la estructura.
- Los **frameworks multiplataforma (Flutter, React Native)** son una fábrica que produce dos casas idénticas con la misma maquinaria: un solo proceso, dos casas listas.
- El **control de versiones (Git)** es el plano con historial: cada vez que alguien cambia una pared, queda registrado, y podés volver a un plano anterior si algo salió mal.
- La **integración continua** es el control de calidad automático: cada vez que se agrega una pared, un inspector la revisa en el momento, sin esperar al final de la obra.
- **Figma y Adobe XD** son el arquitecto que dibuja la casa en papel antes de construirla, para que todos sepan exactamente cómo tiene que quedar.
- El **testeo** es recorrer la casa terminada: primero la maqueta (emulador) y después la casa real (dispositivo), y también invitar a gente a usarla para ver si les resulta cómoda (usabilidad).
- Finalmente, el **despliegue en las tiendas** es poner la casa en venta en el mercado inmobiliario: preparás la publicidad y la exhibís para que el público la encuentre y la compre.

## Ejemplo práctico

Imaginemos un equipo pequeño que quiere lanzar una app de listas de compras que funcione en Android y en iPhone. El flujo completo sería así:

1. El equipo empieza en **Figma**, diseñando cómo se verá la pantalla principal (la lista) y creando un prototipo interactivo para que los interesados lo prueben y aprueben antes de programar.
2. Deciden usar **Flutter** (con lenguaje Dart) para escribir una sola vez y publicar en ambas plataformas. Si hubieran elegido desarrollo nativo, habrían tenido que armar dos proyectos: uno en Kotlin con Android Studio y otro en Swift con Xcode.
3. Durante el desarrollo, usan **Git** para guardar cada cambio: cada integrante trabaja en su rama y luego se unifica. Configuran **integración continua** para que, cada vez que alguien hace un cambio, el servidor compile y corra los tests automáticamente.
4. Prueban la app en el **emulador** (para verificar la lógica) y luego en un par de **teléfonos reales**, uno barato y uno moderno, para comprobar que se vea y funcione bien en distintos tamaños de pantalla. Hacen además un **test de usabilidad**: le piden a dos personas que intenten crear una lista sin ayuda y observan dónde se traban.
5. Finalmente, preparan los íconos, las capturas y las descripciones, y publican: en la **Play Store** para Android y en la **App Store** para iPhone.

Cada herramienta tuvo un rol concreto y en conjunto permitieron que la app llegara de la idea a la tienda.

## Comparativas

### Desarrollo nativo vs. multiplataforma

| Aspecto | Desarrollo nativo | Desarrollo multiplataforma (Flutter, React Native) |
|:--------|:------------------|:---------------------------------------------------|
| Código | Uno por plataforma (Kotlin y Swift por separado) | Un solo código para Android e iOS |
| Lenguaje | Java/Kotlin (Android), Swift/Objective-C (iOS) | Dart (Flutter), JavaScript (React Native) |
| IDE | Android Studio y Xcode | Se puede trabajar con varios editores |
| Rendimiento | Óptimo, acceso directo al hardware | Muy bueno; Flutter se acerca al nativo |
| Esfuerzo de mantenimiento | Alto (dos proyectos) | Bajo (un proyecto) |
| Acceso a funciones del dispositivo | Completo e inmediato | Muy amplio, con bibliotecas adicionales |
| Curva de aprendizaje | Requiere dominar dos lenguajes | Más simple, un solo lenguaje |
| Costo y tiempo | Mayor | Menor |

### Emulador vs. dispositivo real

| Aspecto | Emulador/Simulador | Dispositivo real |
|:--------|:-------------------|:-----------------|
| Velocidad de prueba | Rápida, sin necesidad de hardware | Más lenta de preparar |
| Fidelidad | Parcial (el simulador no reproduce el hardware) | Total, es el hardware real |
| Costo | Gratuito | Requiere comprar dispositivos |
| Sensores y red reales | No siempre representativos | Exactos (batería, GPS, cámara) |
| Momento de uso | Etapas tempranas del desarrollo | Pruebas finales antes de publicar |

### IDE para Android vs. IDE para iOS

| Aspecto | Android Studio | Xcode |
|:--------|:---------------|:------|
| Sistema operativo | Windows, macOS, Linux | Solo macOS |
| Plataforma destino | Android | iOS y otros sistemas de Apple |
| Lenguajes | Java, Kotlin | Objective-C, Swift |
| Emulador/simulador | Emulador de Android | Simulador de iOS |

## Fuentes

### Android Studio (página oficial)

Página oficial de Android Studio, el IDE para desarrollo Android, donde se explica su función, el SDK y el emulador integrado.

https://developer.android.com/studio

### Flutter (página oficial)

Sitio oficial de Flutter, el framework multiplataforma de Google basado en el lenguaje Dart.

https://flutter.dev/

### Figma (página oficial)

Sitio oficial de Figma, herramienta de diseño de interfaces y prototipado colaborativo.

https://www.figma.com/

## Para practicar

1. **Clasificá las herramientas**: Hacé una lista con los siguientes elementos y clasificá cada uno en su categoría: Android Studio, Xcode, Flutter, React Native, Git, Figma, Adobe XD, Play Store, App Store. Fundamentá por qué cada uno entra en su categoría.

2. **Decisión de arquitectura**: Un cliente quiere una app para Android e iOS con el menor costo posible. ¿Qué opción le recomendarías: nativo o multiplataforma? Justificá tu respuesta usando los conceptos de la unidad y la tabla comparativa.

3. **Emulador o real**: Explicá en qué situación conviene probar en emulador/simulador y en cuál conviene usar un dispositivo real. Dale un ejemplo concreto de cada caso.

4. **Secuencia de trabajo**: Ordená de forma lógica los siguientes pasos del desarrollo de una app y explicá por qué ese orden: publicar en la tienda, diseñar en Figma, probar en un teléfono real, escribir el código, probar en el emulador, configurar control de versiones.

5. **Mapa de conceptos**: Elegí tres conceptos de la unidad (por ejemplo, SDK, framework multiplataforma e integración continua) y explicá cada uno con una analogía propia, distinta de las del material, que demuestre que realmente los entendiste.

6. **Investigación guiada**: Visitá las páginas oficiales de Android Studio y Flutter (enlazadas en las fuentes) y anotá tres datos de cada una que no estén en este material. Este ejercicio te prepara para evaluar información oficial por vos mismo.
