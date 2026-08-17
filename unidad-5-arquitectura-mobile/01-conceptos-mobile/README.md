# Conceptos de la arquitectura mobile

## Introducción

Cuando hablamos de "desarrollo de software", la mayoría de las personas piensa en programas que se ejecutan en una computadora de escritorio o en páginas que se abren en un navegador. Sin embargo, hoy la mayor parte del tiempo que pasamos frente a una pantalla ocurre con un teléfono celular en la mano. El desarrollo de aplicaciones móviles (o "apps") es una disciplina que, aunque comparte principios con el desarrollo web y de escritorio, tiene particularidades propias que cambian la forma de diseñar, construir y desplegar software.

Esta unidad te introduce al mundo de la arquitectura mobile: qué es, cuáles son sus desafíos, qué tipos de aplicaciones existen, qué herramientas se usan para construirlas y en qué ecosistema viven. No es un tutorial de código, sino un mapa conceptual para que entiendas las decisiones que se toman detrás de cada aplicación que usás a diario.

Al finalizar esta lectura vas a poder diferenciar una aplicación nativa de una híbrida, explicar qué es una PWA, entender para qué sirve un SDK y reconocer el rol de las tiendas de aplicaciones en el ciclo de vida del software móvil.

## Conceptos clave

### Desarrollo de aplicaciones móviles (mobile development)

Es el proceso de crear software diseñado para ejecutarse en dispositivos móviles: teléfonos, tablets y otros equipos portátiles. A diferencia de un programa de escritorio, la app móvil convive con un conjunto de restricciones de hardware y de uso que condicionan toda la arquitectura. No es "una web más chica", sino un entorno de ejecución con reglas propias.

### Particularidades frente al desarrollo de escritorio o web

El dispositivo móvil impone condiciones que el desarrollador debe considerar desde el primer día:

- **Pantalla pequeña (small screen):** el espacio visual es limitado. Hay que priorizar contenido, diseñar jerarquías de información y adaptar la interfaz a distintos tamaños de pantalla.
- **Interfaz táctil (touch interface):** el usuario interactúa con los dedos, no con un mouse y teclado. Los elementos de interacción deben ser lo suficientemente grandes, los gestos (toque, deslizamiento, pellizco) pasan a ser el lenguaje de la interfaz y no existe el "hover" como en una computadora.
- **Batería (battery):** la energía es un recurso finito y valioso. El código ineficiente, las animaciones innecesarias o las tareas en segundo plano mal gestionadas agotan la batería rápidamente. La arquitectura debe ser consciente del consumo energético.
- **Conectividad intermitente (intermittent connectivity):** a diferencia de una PC con cable o WiFi estable, el móvil alterna entre WiFi, datos móviles, y momentos sin conexión (subte, rutas, zonas rurales). El software debe tolerar la pérdida de red y, en muchos casos, permitir trabajar sin conexión y sincronizar después.
- **Sensores (sensors):** el dispositivo incorpora hardware que las aplicaciones pueden leer: GPS, acelerómetro, giroscopio, cámara, micrófono, brújula, sensor de luz. Esto abre posibilidades (geolocalización, realidad aumentada, detección de movimiento) pero también obliga a gestionar permisos y privacidad.
- **Notificaciones push (push notifications):** la app puede enviar alertas al usuario incluso cuando no está abierta. Esto permite comunicación directa, pero debe usarse con cuidado para no resultar invasiva.

### Tipos de aplicaciones móviles

Existen distintas estrategias para construir una app móvil. La elección depende del presupuesto, del tiempo, del equipo y de las necesidades del producto.

#### Aplicaciones nativas (native apps)

Se desarrollan específicamente para un sistema operativo, usando su lenguaje y sus herramientas oficiales. Una app nativa para Android se escribe con Kotlin o Java; una para iOS, con Swift o Objective-C. Cada versión se instala desde la tienda correspondiente.

**Ventajas:** máximo rendimiento, acceso total a las funciones del dispositivo (cámara, GPS, sensores, notificaciones), mejor experiencia de usuario, y soporte directo de las actualizaciones del sistema operativo.

**Desventajas:** hay que desarrollar, mantener y publicar una versión por cada plataforma. Es decir, duplicar trabajo si querés llegar a Android e iOS.

#### Aplicaciones web (web apps / responsive)

Son sitios web optimizados para verse y funcionar bien en pantallas táctiles pequeñas. Se acceden desde el navegador del dispositivo, sin necesidad de instalarlas. El diseño "responsive" (adaptable) ajusta el contenido según el tamaño de la pantalla.

**Ventajas:** un solo código que funciona en cualquier dispositivo con navegador, sin instalación, actualizaciones inmediatas, sin pasar por la tienda de aplicaciones.

**Desventajas:** acceso limitado a las funciones del hardware, dependen de la conexión a internet, y por lo general ofrecen una experiencia de uso inferior a la nativa.

#### Aplicaciones híbridas (hybrid apps)

Combinan tecnología web (HTML, CSS, JavaScript) dentro de un contenedor nativo. El código se escribe una sola vez y se empaqueta para que se ejecute como si fuera una app nativa, con acceso a algunas funciones del dispositivo a través de puentes de comunicación.

**Ventajas:** se desarrolla un solo código para múltiples plataformas, se instalan desde las tiendas, y tienen acceso a más funciones del dispositivo que una simple web.

**Desventajas:** rendimiento en general inferior al nativo, dependencia de los "puentes" hacia el hardware, y posibles diferencias de comportamiento entre plataformas.

#### Aplicaciones web progresivas (Progressive Web Apps, PWA)

Son aplicaciones web que incorporan capacidades de las nativas: se pueden "instalar" en la pantalla de inicio, funcionan sin conexión (gracias a los *service workers*), pueden recibir notificaciones push y se actualizan solas. La documentación de MDN Web Docs ofrece una guía completa en español sobre este tema.

**Ventajas:** un solo código, instalables sin pasar por la tienda, funcionan offline, actualizaciones automáticas y costos de desarrollo reducidos.

**Desventajas:** menor acceso al hardware que una nativa, y en algunos casos comportamiento de notificaciones o de instalación limitado según el navegador o el sistema operativo.

#### Aplicaciones multiplataforma con frameworks (React Native, Flutter)

Son un caso particular de desarrollo híbrido que usa frameworks modernos para escribir un solo código (JavaScript/TypeScript en React Native; Dart en Flutter) que luego se compila o traduce a componentes nativos reales. A diferencia de un contenedor web, estos frameworks generan interfaces que se dibujan de forma nativa.

**Ventajas:** un solo código para Android e iOS, buen rendimiento (más cercano al nativo que las híbridas tradicionales), comunidades grandes y ecosistemas de librerías maduros.

**Desventajas:** más curva de aprendizaje que una web simple, algunas funciones muy específicas del dispositivo pueden requerir escribir código nativo adicional, y dependencia del framework y de su mantenimiento.

### SDK (Software Development Kit)

Un SDK (kit de desarrollo de software) es un conjunto de herramientas, librerías, documentación y ejemplos que un fabricante entrega para que los desarrolladores construyan aplicaciones para su plataforma. Cuando desarrollás para Android, usás el Android SDK; cuando desarrollás para iOS, usás el iOS SDK. El SDK es, en definitiva, la caja de herramientas oficial que te da acceso a las capacidades del sistema operativo y del dispositivo.

### Sistemas operativos móviles dominantes

Dos sistemas operativos concentran la enorme mayoría del mercado de teléfonos inteligentes:

- **Android (de Google):** de código abierto, presente en una enorme cantidad de fabricantes (Samsung, Xiaomi, Motorola, entre otros). Su documentación oficial se encuentra en Android Developers.
- **iOS (de Apple):** propietario y cerrado, exclusivo de los dispositivos de Apple (iPhone, iPad). Su documentación oficial está en Apple Developer.

La elección de uno u otro afecta directamente las decisiones de arquitectura: lenguajes, herramientas, tiendas y estrategias de distribución.

### Ecosistema de tiendas de aplicaciones (app stores)

Las apps se distribuyen a través de tiendas oficiales: Google Play para Android y App Store para iOS. Estas tiendas no solo son un canal de descarga, sino también un punto de control: definen políticas, realizan revisiones de seguridad y calidad, gestionan actualizaciones y permiten monetización. Publicar una app implica cumplir requisitos, en algunos casos pagar una cuenta de desarrollador, y someterse a un proceso de revisión.

## Analogía

Imaginá que querés abrir un restaurante. Podés hacerlo de varias formas:

- **Abrir un local propio y exclusivo** (app nativa): instalás cocina, salón y carta a tu medida. Es caro y requiere mantenimiento, pero el control total y la calidad son máximos.
- **Montar un puesto en una feria** (app web): es rápido y barato, cualquiera te encuentra, pero dependés del lugar y del clima (la conexión), y no controlás bien la experiencia.
- **Usar un local de franquicia** (app híbrida): usás una estructura prearmada para montar tu restaurante en varios puntos. Es más barato que el local propio, pero el modelo tiene limitaciones.
- **Un food truck que recorre la ciudad** (PWA): podés aparecer donde haya gente, instalarte rápido y moverte sin necesidad de un local fijo, aunque con ciertas limitaciones respecto a un restaurante completo.

En todos los casos el objetivo es alimentar a la gente, pero la estrategia cambia según el presupuesto, el tiempo y el nivel de control que necesites.

## Ejemplo práctico

Supongamos que una empresa quiere lanzar una app para pedir turnos en su peluquería. Analicemos las opciones:

- Si eligen una **app nativa para Android e iOS**, necesitarán dos equipos o dos desarrollos (Kotlin y Swift), doble mantenimiento y dos publicaciones. A cambio, tendrán acceso total al calendario del teléfono, notificaciones push confiables y la mejor experiencia posible.
- Si eligen una **app híbrida o multiplataforma (React Native o Flutter)**, escribirán un solo código para ambas plataformas, lo que reduce costos. Podrán enviar notificaciones y acceder a muchas funciones del dispositivo.
- Si eligen una **PWA**, podrán ofrecer una experiencia instalable desde el navegador, que funciona sin conexión para consultar los turnos ya reservados y que no requiere pasar por la tienda. Es la opción más rápida y económica de lanzar.
- Si eligen una **web responsive**, tendrán lo más simple: una página adaptada al celular, sin instalación, aunque sin notificaciones push ni acceso al hardware.

La decisión de arquitectura no es técnica en abstracto: depende del negocio, del presupuesto y de qué tan críticas sean las funciones del dispositivo para el producto.

## Comparativas

| Característica | Nativa | Híbrida | Web responsive | PWA |
|----------------|--------|---------|----------------|-----|
| Código por plataforma | Uno por sistema operativo | Uno para todas | Uno para todas | Uno para todas |
| Instalación | Desde la tienda | Desde la tienda | Ninguna (se navega) | Desde la pantalla de inicio |
| Acceso a hardware del dispositivo | Total | Parcial (vía puentes) | Muy limitado | Parcial |
| Funcionamiento sin conexión | Sí | Depende | No | Sí |
| Notificaciones push | Sí | Sí | No | Sí |
| Rendimiento | Máximo | Medio | Bajo | Medio |
| Costo de desarrollo | Alto | Medio | Bajo | Bajo/Medio |
| Publicación en tienda | Requerida | Requerida | No | No |

## Fuentes

### Android Developers (documentación oficial)

Guía de desarrollo para la plataforma Android, que cubre el SDK, las herramientas y las buenas prácticas de arquitectura móvil.

https://developer.android.com/guide

### Apple Developer (documentación oficial)

Portal oficial de desarrollo para el ecosistema iOS, con las herramientas, lenguajes y guías para construir aplicaciones nativas de Apple.

https://developer.apple.com/

### MDN Web Docs - "Progressive web apps"

Guía en español sobre aplicaciones web progresivas (PWA), sus capacidades, instalación, funcionamiento sin conexión y notificaciones.

https://developer.mozilla.org/es/docs/Web/Progressive_web_apps

## Para practicar

1. Explicá con tus palabras la diferencia entre una aplicación nativa y una aplicación web responsive. ¿En qué caso elegirías cada una?
2. ¿Qué particularidades del entorno móvil (pantalla, batería, conectividad) tendrías que considerar al diseñar una app de mensajería que debe funcionar en zonas sin señal?
3. Compará una aplicación híbrida tradicional con una multiplataforma con framework (React Native o Flutter). ¿En qué se diferencia técnicamente la forma de "dibujar" la interfaz?
4. Investigá y enumerá tres funciones de tu celular que solo se pueden usar si la app tiene permisos sobre sensores o hardware. ¿Qué implicancias de privacidad genera eso?
5. Buscá un ejemplo real de una PWA que uses o conozcas. ¿Qué ventajas le ves frente a su versión nativa, si es que existe?
6. ¿Qué es un SDK y por qué el fabricante del sistema operativo entrega uno? ¿Qué pasaría si no existiera?
7. Analizá una app que uses a diario e intentá clasificarla (nativa, híbrida, PWA o web). Justificá tu respuesta según las características que aprendiste en esta lectura.
