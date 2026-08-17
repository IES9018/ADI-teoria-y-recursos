# Patrones de diseño web

## Introducción

Cuando diseñamos una interfaz web, enfrentamos siempre los mismos problemas: ¿dónde pongo el menú? ¿cómo hago que el usuario encuentre lo que busca? ¿cómo lo convenzo de que se registre? La buena noticia es que estos problemas ya tienen soluciones probadas. Esas soluciones que se repiten y funcionan se llaman **patrones de diseño web** (web design patterns).

Un patrón no es un código ni un estilo visual: es una **solución reutilizable a un problema recurrente**. Funciona como una receta probada: si la seguís, es muy probable que tu interfaz sea usable y cumpla su objetivo. Los patrones de diseño web combinan dos grandes familias: los **patrones de presentación** (cómo se organiza y muestra el contenido en pantalla) y los **patrones de arquitectura** (cómo se organiza el software que sostiene la página).

Este material te va a llevar de cero a cien: primero vas a entender qué es un patrón y por qué existen; después vas a recorrer los patrones de layout y navegación; vas a ver los patrones de página de aterrizaje y conversión; vas a conocer los patrones de interfaz específicos (búsqueda, formularios, carrito); y por último vas a entrar en el terreno de la arquitectura con MVC, la separación frontend/backend, las APIs REST y la diferencia entre una web multipágina tradicional y una aplicación web de una sola página (SPA). Para cada patrón vas a encontrar **cuándo usarlo** y **cuándo evitarlo**, porque en diseño tanto saber aplicar un patrón como saber no abusar de él es lo que marca la diferencia.

## Conceptos clave

### ¿Qué es un patrón de diseño web (web design pattern)?

Un patrón de diseño web es una **solución genérica y comprobada para un problema de diseño de interfaz que se repite una y otra vez**. Cuando miles de sitios necesitan un menú de navegación, un buscador o un formulario de contacto, con el tiempo se llega a formas de resolverlo que los usuarios ya entienden sin que nadie les explique nada.

La clave de un patrón es que **reduce la curva de aprendizaje**: si el usuario ya usó diez sitios con un carrito de compras arriba a la derecha, en el tuyo lo va a encontrar casi sin pensar. Un buen patrón combina tres cosas:

- **Usabilidad**: hace que la tarea sea fácil de completar.
- **Consistencia**: da una experiencia predecible.
- **Convención**: aprovecha lo que el usuario ya sabe de otros sitios.

Un patrón no es una ley rígida ni un molde único. Es una **guía** que se adapta al contexto. Los patrones de diseño web se diferencian de los patrones de arquitectura de software (como MVC) en un punto importante: los primeros resuelven problemas **de interfaz y experiencia de usuario**, mientras que los segundos resuelven problemas de **organización interna del código**. En este material vas a ver ambos, porque una buena aplicación web necesita de los dos.

### Patrón de estructura en forma de F (F-shaped pattern)

El patrón en forma de **F** describe cómo **los usuarios leen el contenido web**: no lo leen palabra por palabra, sino que lo **escanean**. Los estudios del grupo Nielsen Norman muestran que la mirada del usuario recorre la página siguiendo dos líneas horizontales y una vertical, formando una "F".

Concretamente, el usuario:

1. Lee las primeras líneas de forma horizontal (la barra superior de la F).
2. Baja un poco y vuelve a leer otra línea horizontal, pero más corta (la barra media de la F).
3. Finalmente recorre la parte izquierda de la pantalla en forma vertical (la pata de la F).

**Cuándo usarlo:** en páginas con mucho texto, como artículos, noticias, listados de resultados o páginas de documentación. Al conocer este comportamiento, sabés que lo más importante debe ir arriba y a la izquierda, donde la mirada pasa primero.

**Cuándo evitarlo o combinarlo:** si tu página es una aplicación con una tarea puntual (por ejemplo, llenar un formulario), el usuario no escanea tanto, sino que se concentra en la tarea. El patrón en F describe lectores "escáner", no usuarios "haciendo una tarea". Tampoco es la única forma de escanear: en pantallas modernas y con contenido menos textual aparecen otros recorridos. Sirve como **punto de partida**, no como regla absoluta.

### Patrón de navegación global (global navigation)

La **navegación global** es el patrón que garantiza que el usuario **sepa dónde está y pueda ir a cualquier sección del sitio desde cualquier página**. Típicamente aparece como una barra (menú) en la parte superior de la página, presente en todas las pantallas.

Un buen patrón de navegación global responde tres preguntas del usuario: **¿Dónde estoy?, ¿Qué hay acá? y ¿A dónde puedo ir?**. Para eso se apoya en elementos como el logo (que suele volver a la página de inicio), las secciones principales del sitio y, en muchos casos, un indicador visual de la sección activa.

**Cuándo usarlo:** siempre que el sitio tenga más de unas pocas secciones y el usuario necesite moverse entre ellas. La navegación global es la columna vertebral de casi cualquier sitio web informativo o corporativo.

**Cuándo evitarlo:** en páginas de aterrizaje muy enfocadas o en flujos de tareas críticas (como un pago), a veces se oculta la navegación global a propósito para que el usuario no se distraiga y complete la acción. Es una decisión deliberada, no un descuido.

### Mega menús (mega menus)

Los **mega menús** son una variante del menú de navegación en la que, al pasar el cursor sobre una categoría, se despliega un **panel grande con muchas opciones organizadas en columnas**, en lugar de una simple lista vertical.

**Cuándo usarlos:** son ideales para sitios con **mucha información jerárquica**, como tiendas online, universidades, sitios gubernamentales o portales con muchas secciones. El mega menú permite que el usuario vea, de un vistazo, todas las subcategorías disponibles sin tener que navegar página por página.

**Cuándo evitarlos:** si tu sitio tiene pocas opciones, un mega menú es excesivo y agrega ruido visual. También requieren cuidado en dispositivos móviles, donde el despliegue por hover no funciona y hay que rediseñar la interacción (por ejemplo, con toques y subniveles plegables).

### Carruseles (carousels) y sus críticas

Un **carrusel** (o slider) es un componente que muestra **varias imágenes o banners que rotan**, ya sea automáticamente o mediante flechas que el usuario puede presionar.

**Las críticas son fuertes y merecen atención:** los carruseles automáticos tienen problemas serios de usabilidad. Primero, **los usuarios a menudo no los ven rotar**: la velocidad automática no coincide con el ritmo de lectura. Segundo, los banners que no son el primero **reciben muy pocas interacciones** (los usuarios rara vez hacen clic en el segundo o tercer slide). Tercero, el movimiento constante **distrae** y puede resultar molesto. Los estudios de Nielsen Norman Group recomiendan, en general, **evitar la rotación automática** y mostrar contenido estático o con control total del usuario.

**Cuándo usarlos:** si de verdad hay varios mensajes igual de importantes que no caben en pantalla y el usuario controla el avance manualmente. Mejor aún: en lugar de un carrusel, priorizá **un único mensaje destacado** bien diseñado, porque el contenido "oculto" en slides posteriores suele perderse.

**Cuándo evitarlos:** como regla general, cuando el carrusel se usa "porque queda lindo" o para acumular banners. La evidencia muestra que suelen ser menos efectivos de lo que parecen.

### Scroll infinito (infinite scroll) vs. paginación (pagination)

El **scroll infinito** carga contenido nuevo automáticamente a medida que el usuario llega al final de la página, sin interrupciones. La **paginación**, en cambio, divide el contenido en páginas numeradas con enlaces "siguiente", "anterior" y números de página.

**Scroll infinito:**
- **Cuándo usarlo:** en flujos de **exploración continua y sin objetivo específico**, como redes sociales, galerías de imágenes o feeds de noticias. El usuario "navega a la deriva" y la experiencia sin cortes es placentera.
- **Cuándo evitarlo:** cuando el usuario busca un **ítem específico** (por ejemplo, un producto puntual en un listado grande) o cuando necesita **guardar la posición** para volver más tarde. Con scroll infinito es difícil volver al punto donde estaba y no existe un marcador claro.

**Paginación:**
- **Cuándo usarla:** en **listados donde el usuario busca o compara ítems específicos** (resultados de búsqueda, catálogos de productos, listados de documentos). La paginación da sensación de control, permite numerar y estimar cuánto queda, y facilita volver a una posición conocida.
- **Cuándo evitarla:** en flujos puramente de exploración, donde los saltos de página interrumpen la inmersión.

La elección se resume en una pregunta: **¿el usuario explora o busca?** Si explora, scroll infinito; si busca, paginación. Algunos sitios combinan ambas estrategias según la sección.

### Página de aterrizaje (landing page)

Una **landing page** es una página web cuyo objetivo es **una sola acción concreta**: convencer al visitante de que haga algo específico (comprar, registrarse, descargar, suscribirse). A diferencia de una página de inicio general, la landing page está enfocada en **un único mensaje y un único llamado a la acción**.

Sus partes típicas incluyen un **titular claro** que comunica la propuesta de valor, **contenido breve** que explica el beneficio, **elementos de confianza** (testimonios, estadísticas) y el **botón de acción destacado**.

**Cuándo usarla:** en campañas de marketing, lanzamientos de producto, registros a servicios o descargas. Cada campaña suele tener su propia landing page para poder medir su efectividad.

**Cuándo evitarla:** si el visitante necesita comparar muchas opciones o explorar a fondo antes de decidir, una landing page ultra-enfocada puede resultar insuficiente. En esos casos conviene una página más rica en información.

### Llamado a la acción o CTA (call to action)

El **CTA** es el elemento que **invita al usuario a realizar la acción deseada**: un botón con un texto claro como "Comprar ahora", "Registrarse", "Descargar" o "Empezar". Es el corazón de la conversión.

Las buenas prácticas del CTA incluyen:

- **Texto accionable y específico**: dice exactamente qué va a pasar ("Comenzar prueba gratis") en lugar de un vago "Enviar".
- **Destaque visual**: un color y tamaño que lo diferencien del resto.
- **Ubicación estratégica**: visible sin necesidad de desplazarse o en el lugar donde el usuario termina de leer el argumento.
- **Un único CTA principal**: cuando hay muchos botones compitiendo, ninguno convence.

**Cuándo usarlo:** en toda página cuyo objetivo sea la conversión. Sin un CTA claro, el usuario no sabe qué se espera que haga.

**Cuándo evitarlo (en exceso):** cuando hay demasiados CTAs peleando por la atención del usuario, se diluye el mensaje. La regla es **un CTA principal por página**.

### Patrones de interfaz específicos: búsqueda, filtros, carrito y check-out

Además de los patrones de estructura, existen patrones para **funciones concretas de la interfaz**.

**Búsqueda (search):** un campo de texto donde el usuario escribe lo que busca. Se usa cuando el contenido es grande y el usuario tiene un objetivo específico. Las buenas búsquedas ofrecen autocompletado, manejan errores de tipeo y muestran resultados claros. **Cuándo usarla:** en catálogos, portales, documentación y sitios grandes. **Cuándo no:** en sitios pequeños con pocas páginas, donde la navegación alcanza.

**Filtros (filters):** permiten **reducir un conjunto de resultados** según criterios (categoría, precio, color, fecha). Son imprescindibles en catálogos de productos y listados grandes. **Cuándo usarlos:** cuando hay muchos ítems con atributos diferenciadores y el usuario necesita acotar la búsqueda. **Cuándo no:** cuando el listado es pequeño, los filtros agregan complejidad innecesaria.

**Carrito de compras (shopping cart):** guarda los productos que el usuario eligió antes de pagar. Es un patrón clásico del comercio electrónico. Un buen carrito muestra el resumen, permite modificar cantidades y deja claro cómo continuar al pago. **Cuándo usarlo:** en todo e-commerce. **Cuándo no:** si vendés un único producto o un servicio sin compra acumulable, un carrito puede ser excesivo.

**Check-out de varios pasos (multi-step checkout):** divide el proceso de compra en **pasos consecutivos** (datos de envío, datos de pago, revisión, confirmación) en lugar de un solo formulario largo. **Cuándo usarlo:** cuando el proceso tiene varias etapas que exigen información distinta; mostrar una barra de progreso reduce la ansiedad. **Cuándo no:** si el proceso es muy corto (un solo paso), partirlo agrega fricción innecesaria.

**Formularios (forms):** recopilan datos del usuario. Son la base de registros, contactos y compras. Las buenas prácticas incluyen etiquetas claras, validación en tiempo real, mensajes de error comprensibles y agrupar campos relacionados. **Cuándo usarlos:** siempre que necesites capturar datos. **Cuándo optimizar:** cuanto menos campos pidas, más fácil será completarlo; cada campo extra reduce la tasa de finalización.

### MVC: Modelo-Vista-Controlador (Model-View-Controller)

El patrón **MVC** es un **patrón de arquitectura de software** que organiza una aplicación en tres componentes con responsabilidades separadas:

- **Modelo (Model):** los datos y la lógica de negocio. "Sabe" qué datos hay y cómo procesarlos.
- **Vista (View):** lo que el usuario ve. Presenta el modelo en la pantalla.
- **Controlador (Controller):** recibe las acciones del usuario, las interpreta, actualiza el modelo y refresca la vista.

La gran ventaja de MVC es la **separación de responsabilidades**: si cambio la lógica de negocio, no rompo la interfaz; si rediseño la interfaz, no toco los datos. Esto hace el código más ordenado, testeable y mantenible.

Según MDN, aunque MVC se definió originalmente para interfaces de escritorio, se adaptó muy bien al desarrollo web. En las aplicaciones web modernas existen muchas variantes (como la arquitectura basada en componentes de frameworks modernos), pero la idea central de **separar datos, presentación y control** sigue siendo la base de casi todo.

**Cuándo usarlo:** cuando la aplicación tiene lógica de negocio, interfaz y acciones del usuario que conviene mantener separadas y probar por partes. Es el punto de partida de casi cualquier aplicación web estructurada.

**Cuándo reconsiderarlo:** en proyectos muy simples, aplicar MVC de forma estricta puede sentirse pesado. Y en aplicaciones muy complejas, MVC básico puede quedar corto frente a arquitecturas más sofisticadas. Pero como **concepto fundacional**, entenderlo es obligatorio.

### Separación frontend/backend y APIs REST

Un paso natural después de MVC es separar la aplicación en dos grandes bloques:

- **Frontend:** la parte que el usuario ve e interactúa (la interfaz). Corre en el navegador.
- **Backend:** la parte que procesa datos, reglas de negocio y seguridad. Corre en el servidor.

La **API** (Interfaz de Programación de Aplicaciones) es el **puente** entre ambos: el frontend le pide datos al backend mediante peticiones, y el backend responde. **REST** es un estilo de diseño de APIs que organiza los recursos como "cosas" identificadas por URLs y las manipula con verbos HTTP (GET para leer, POST para crear, PUT/PATCH para actualizar, DELETE para eliminar). Una API REST devuelve normalmente los datos en formato JSON.

**Cuándo usarla:** siempre que tengas una aplicación web donde la interfaz y la lógica sean lo bastante complejas como para justificar separarlas, o cuando quieras que la misma lógica sirva a varios clientes (una web, una app móvil, etc.).

**Cuándo evitarla (simplificar):** en prototipos o sitios muy pequeños, la separación completa agrega estructura que tal vez no se necesita aún. Pero para aplicaciones reales que van a crecer, frontend/backend + API es el estándar.

### Web multipágina tradicional vs. SPA (Single Page Application)

Este punto compara dos formas de construir una experiencia web:

**Web tradicional multipágina (MPA):** cada vez que el usuario navega a otra sección, el navegador **carga una página completa nueva** desde el servidor. La URL cambia y la página "recarga".

- **Ventajas:** mejor para SEO (cada página es indexable de forma independiente), carga inicial simple, comportamiento predecible.
- **Desventajas:** cada navegación recarga todo, lo que puede sentirse más lento y menos fluido.

**Aplicación web de una sola página (SPA):** se carga **una única página HTML** y luego el contenido se actualiza dinámicamente **sin recargar la página**, intercambiando datos con el servidor mediante peticiones a la API (típicamente REST). Es la base de muchas aplicaciones modernas (redes sociales, paneles de control, herramientas online).

- **Ventajas:** experiencia fluida y "de aplicación", sin recargas constantes, muy interactiva.
- **Desventajas:** requiere más trabajo inicial, y el SEO y la carga inicial pueden ser más complejos de manejar.

**Cuándo usar cada una:** una MPA tradicional es ideal para **sitios informativos** (blogs, sitios corporativos, catálogos) donde el contenido es lo central. Una SPA es ideal para **aplicaciones con mucha interacción** (dashboards, herramientas, redes) donde la fluidez de la interfaz es crítica. Muchos proyectos modernos mezclan ambas estrategias según la sección.

## Analogía

Imaginemos que los patrones de diseño web son los **planos de una casa que la gente ya conoce**. Cuando entrás a una casa típica, no te dicen dónde está la cocina: sabés que las puertas abren hacia adentro, que la mesa está en el comedor y que la heladera no está en el baño. Si alguien te muestra una casa donde la puerta abre hacia afuera o el baño no tiene puerta, te descoloca: tenés que pensar para usarla.

Los patrones funcionan igual. Cuando entrás a un sitio y el menú está arriba, el buscador arriba a la derecha y el carrito en la esquina, no tenés que pensar nada: ya lo usaste mil veces. Si un sitio pone el menú abajo y el carrito donde menos esperás, el usuario se siente como en esa casa rara: tiene que "pensar" para navegar, y eso es lo que un buen diseño quiere evitar.

La **separación frontend/backend** se puede entender con el restaurante. El **frontend** es el salón y el mozo: es lo que el cliente ve y con lo que interactúa. El **backend** es la cocina: ahí se prepara la comida con reglas (recetas), se controla la higiene (seguridad) y se guardan los insumos (datos). La **API REST** es la ventanilla donde el mozo le pasa el pedido a la cocina y la cocina le entrega el plato. Si mañana cambias la carta (back-end), el salón no tiene que rediseñarse; si cambiás la decoración del salón (front-end), la cocina no se entera. Ambos están conectados por la ventanilla, pero funcionan de forma independiente. Y el **MVC** es, dentro de cada área, una forma ordenada de que cada empleado tenga una sola responsabilidad clara.

## Ejemplo práctico

Armemos un ejemplo concreto que recorra los patrones: un **sitio de comercio electrónico de indumentaria**.

1. **Estructura en forma de F:** en la página de inicio, colocamos las promociones principales arriba a la izquierda, donde la mirada escanea primero, y los accesos secundarios más a la derecha y abajo, sabiendo que el usuario leerá en F.
2. **Navegación global:** un menú superior persistente con las secciones "Hombre", "Mujer", "Accesorios" y "Ofertas", con la sección activa resaltada.
3. **Mega menú:** al pasar por "Mujer", se despliega un panel con columnas: "Remeras", "Pantalones", "Zapatos", "Novedades". El usuario ve todo el catálogo de un vistazo.
4. **Carrusel (crítico):** en lugar de un carrusel automático con cinco banners, mostramos **un único banner estático** con la campaña principal. Evitamos el desgaste de la rotación automática.
5. **Paginación en catálogo:** en el listado de remeras, usamos **paginación** porque el usuario está **buscando** un ítem puntual y necesita saber cuánto queda y volver a posiciones conocidas. (El scroll infinito lo dejamos para la sección de "inspiración" en redes, donde el usuario explora sin objetivo.)
6. **CTA:** en cada producto, un botón destacado "Agregar al carrito" con color llamativo y texto accionable.
7. **Carrito:** un ícono de carrito arriba a la derecha que guarda los productos elegidos y muestra un resumen antes del pago.
8. **Check-out de varios pasos:** al pagar, dividimos en pasos con barra de progreso: "Datos de envío" → "Pago" → "Revisión" → "Confirmación".
9. **Búsqueda y filtros:** un buscador con autocompletado arriba y, en el catálogo, filtros por talle, color y precio para acotar los resultados.
10. **Arquitectura (MVC + frontend/backend + API REST):** el frontend (la tienda que ves en el navegador) le pide los productos al backend mediante una API REST (`GET /productos`, `POST /pedidos`). Internamente, el backend organiza su código con el espíritu de MVC: el modelo guarda los datos de productos y pedidos, la vista genera las respuestas, y el controlador maneja las peticiones. Al separar frontend y backend, la misma API podría servir más adelante para una **app móvil** sin tocar nada del backend.
11. **SPA vs MPA:** la **zona de administración** (panel del vendedor para cargar productos y ver pedidos) la construimos como una **SPA** porque necesita mucha interacción fluida sin recargas. El **blog o catálogo público** puede ser una web tradicional multipágina, que facilita el SEO de cada producto.

Este ejemplo muestra que un proyecto real no elige un solo patrón: **combina varios según la necesidad de cada zona**, y saber cuál usar en cada lugar es el oficio del diseñador de interfaces y del arquitecto web.

## Comparativas

### Carouseles vs. contenido estático

| Criterio | Carrusel con rotación automática | Contenido estático destacado |
|:---------|:--------------------------------|:----------------------------|
| Atención del usuario | Baja: muchos slides pasan sin ser vistos | Alta: un único mensaje concentra la atención |
| Control del usuario | Bajo: el avance es automático | Total: el usuario decide qué ver |
| Riesgo de distracción | Alto: movimiento constante | Bajo |
| Efectividad de los mensajes posteriores | Muy baja | No aplica (un solo mensaje) |
| Cuándo conviene | Solo con control manual y pocos slides | Como regla general |

### Scroll infinito vs. paginación

| Criterio | Scroll infinito | Paginación |
|:---------|:----------------|:-----------|
| Comportamiento del usuario | Exploración continua | Búsqueda de ítems específicos |
| Sensación de control | Baja: difícil volver a un punto | Alta: numeración y posición clara |
| Marcador de posición | Difícil de retomar | Fácil de retomar |
| Carga de contenido | Progresiva, sin interrupciones | Por lotes, con saltos de página |
| Cuándo conviene | Redes, feeds, galerías | Catálogos, resultados de búsqueda, listados |

### Web tradicional (MPA) vs. aplicación de una sola página (SPA)

| Criterio | Web multipágina (MPA) | SPA (Single Page Application) |
|:---------|:----------------------|:------------------------------|
| Navegación | Carga una página completa por sección | Actualiza contenido sin recargar |
| Fluidez | Menor: recargas constantes | Mayor: experiencia de aplicación |
| SEO | Mejor: cada página indexable | Más complejo de optimizar |
| Carga inicial | Rápida y simple | Puede ser más pesada |
| Interactividad | Limitada | Muy alta |
| Cuándo conviene | Sitios informativos, blogs, catálogos | Dashboards, herramientas, redes, apps |

### MVC: responsabilidades de cada componente

| Componente | Responsabilidad | Ejemplo en un e-commerce |
|:-----------|:----------------|:-------------------------|
| Modelo | Datos y lógica de negocio | Guardar productos, calcular precios, validar stock |
| Vista | Presentación al usuario | La página que muestra el catálogo |
| Controlador | Recibir acciones, coordinar modelo y vista | Manejar "agregar al carrito" y actualizar la vista |

## Fuentes

### Nielsen Norman Group - "F-Shaped Pattern for Reading Web Content"

https://www.nngroup.com/articles/f-shaped-pattern-reading-web-content-discovered/

Fuente principal para el patrón de estructura en forma de F: describe cómo los usuarios escanean el contenido web siguiendo ese recorrido y qué implicancias tiene para la ubicación de la información importante.

### MDN Web Docs - "Modelo de objetos / MVC"

https://developer.mozilla.org/es/docs/Glossary/MVC

Fuente principal para explicar el patrón MVC: define de forma clara y en español los componentes Modelo, Vista y Controlador, y explica su adaptación al desarrollo web moderno.

### Nielsen Norman Group - página general de artículos de diseño web

https://www.nngroup.com/articles/

Fuente de referencia general: respalda las recomendaciones sobre carruseles, scroll infinito, paginación, landing pages y demás patrones de experiencia de usuario citados en este material.

## Para practicar

1. **Identificar patrones:** elegí tres sitios web que uses seguido. Identificá en cada uno: el tipo de navegación (global, mega menú, etc.), si usa carrusel o contenido estático, y si el listado principal usa scroll infinito o paginación. Justificá por qué creés que eligieron cada patrón.

2. **Diseñar una landing page:** redactá el esquema de una landing page para un servicio de suscripción a una app. Definí el titular, el contenido de apoyo, los elementos de confianza y **un único CTA**, explicando por qué es el principal.

3. **Decidir entre carrusel y estático:** para la página de inicio de una tienda de zapatillas, fundamentá por escrito si usarías un carrusel automático o un único banner estático, apoyándote en las críticas de los carruseles.

4. **Scroll infinito o paginación:** un sitio tiene dos listados: el feed de "inspiración" y el catálogo de productos con búsqueda. Explicá cuál conviene usar en cada uno y por qué, usando el criterio "explorar vs. buscar".

5. **Modelar un proceso de compra:** diseñá el flujo de un check-out de varios pasos para un e-commerce de libros. Listá los pasos, la información de cada uno y en qué momento se usa una barra de progreso.

6. **Distinguir MVC:** en una aplicación de notas (crear, editar, borrar notas), identificá qué haría el Modelo, qué la Vista y qué el Controlador, y explicá por qué conviene separarlos.

7. **Diseñar una API REST simple:** para esa misma app de notas, proponé las URLs de una API REST con sus verbos HTTP: cómo se listarían las notas, cómo se crearía una, cómo se editaría y cómo se borraría.

8. **Comparar MPA vs. SPA:** tomá dos aplicaciones reales que conozcas (una que parezca MPA y otra SPA). Compará la experiencia de navegación y razoná por qué cada una eligió su arquitectura según su objetivo.

9. **Análisis de formularios:** revisá un formulario de registro de un sitio real y listá qué buenas prácticas cumple (etiquetas, validación, mensajes de error, campos mínimos) y qué podría mejorar.

10. **Reflexión integradora:** pensá en una idea propia de aplicación. Escribí una breve memoria donde decidas: qué patrones de layout y navegación usarías, qué patrón de conversión aplicás, y si construirías una web multipágina o una SPA con frontend/backend separados. Justificá cada decisión.
