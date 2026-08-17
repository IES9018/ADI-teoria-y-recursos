# Patrones de diseño mobile

## Introducción

Diseñar para dispositivos móviles no es lo mismo que diseñar para una computadora de escritorio. En un celular el espacio es limitado, se usa con una mano (o con el pulgar), y la persona interactúa tocando la pantalla en lugar de usar un mouse y un teclado. Por eso existen **patrones de diseño mobile**: soluciones ya probadas y estandarizadas para problemas comunes que aparecen al armar una interfaz móvil.

Un patrón es, básicamente, una receta que la comunidad de diseño ya validó. En lugar de inventar desde cero cómo mostrar una lista, cómo navegar entre pantallas o cómo pedirle datos al usuario, se recurre a patrones conocidos. Esto tiene varias ventajas: el desarrollo es más rápido, el resultado es predecible, y (lo más importante) el usuario ya sabe cómo usarlo porque lo vio en otras aplicaciones.

Este material cubre cuatro grandes familias de patrones móviles: **navegación**, **contenido y listas**, **entrada de datos** y **feedback** (es decir, cómo la app le comunica al usuario qué está pasando). También se explican los estados especiales (carga, error, vacío) y las buenas prácticas que aplican a todos los casos, como el tamaño de los objetivos táctiles y el área del pulgar.

## Conceptos clave

### Patrones de navegación móvil

La navegación define **cómo se mueve el usuario entre las pantallas de la aplicación**. Es la columna vertebral de la experiencia: si el usuario no encuentra cómo llegar a donde quiere, la app falla aunque el contenido sea excelente. Existen varios patrones, y cada uno sirve para una situación distinta.

#### Pestañas inferiores (bottom tab bar)

Es la barra que aparece en la parte de abajo de la pantalla con dos a cinco íconos, cada uno con su etiqueta. Es el patrón de navegación más común en apps móviles porque coincide con el área donde el pulgar trabaja con más comodidad.

Se usa cuando la app tiene **pocas secciones de nivel superior** (entre dos y cinco) que deben estar siempre accesibles. El usuario sabe en qué sección está porque el ítem correspondiente se ve "activo". Las pestañas inferiores no cambian de posición ni se ocultan: son el mapa fijo de la aplicación.

**Cuándo usarlo:** apps con tres a cinco destinos principales que el usuario visita con frecuencia y que deben estar siempre a un toque de distancia.

#### Barra de acción superior (top app bar)

Es la franja que se ubica en la parte superior de la pantalla. Contiene el título de la pantalla actual y acciones contextuales, como botones de búsqueda, compartir, menú o ajustes. En Android se llama *app bar* y forma parte de Material Design; en iOS la equivalente es la *navigation bar*.

Funciona como un encabezado que le dice al usuario dónde está. Las acciones que aparecen ahí deben ser las más importantes o las que se repiten con frecuencia dentro de esa pantalla.

**Cuándo usarlo:** siempre que la pantalla necesite un título claro y acciones rápidas relacionadas con el contenido que se está viendo. Puede combinarse con otros patrones (por ejemplo, convivir con pestañas inferiores).

#### Cajón de navegación (navigation drawer / hamburguesa)

Es un panel que se desliza desde el costado (generalmente el izquierdo) y que contiene opciones de navegación. Se abre tocando el ícono de las tres líneas horizontales, conocido como "hamburguesa".

Se usa cuando hay **muchas secciones o la navegación es jerárquica y profunda**. El cajón permite esconder un menú extenso que no entra en una barra de pestañas. La desventaja es que las opciones quedan "ocultas": el usuario tiene que saber que ese menú existe y deslizarlo.

**Cuándo usarlo:** apps con más de cinco secciones, cuentas de usuario, ajustes extensos, o cuando la navegación principal es demasiado grande para las pestañas inferiores. Conviene usarlo con cuidado porque agrega un paso extra antes de llegar al contenido.

#### Navegación basada en gestos (swipes)

Consiste en navegar deslizando el dedo sobre la pantalla. Los ejemplos más típicos son pasar a la página siguiente o anterior en una galería de imágenes, o deslizar elementos hacia un costado para revelar acciones (por ejemplo, eliminar un correo).

Los gestos son rápidos y naturales, pero tienen un problema: **no son visibles**. El usuario no puede saber que existe un gesto hasta que lo prueba o lo descubre. Por eso los gestos nunca deben ser el único camino para una acción importante.

**Cuándo usarlo:** para acciones que se repiten mucho (pasar de foto en foto), para organizar listas, y como complemento de otras navegaciones. Nunca como reemplazo total de un camino visible.

#### Navegación en pilas de pantallas (navigation stack)

Es la forma de navegar en profundidad: el usuario avanza de una pantalla a otra (por ejemplo, de la lista de productos al detalle de un producto) y luego retrocede. Las pantallas se apilan una sobre otra, como platos en una pila: la pantalla actual está arriba, y al volver atrás se "desapila".

Se implementa con un botón de retroceso. En Android existe un botón físico o gestual de "atrás"; en iOS el retroceso es una flecha en la barra superior izquierda. Esta navegación es la que da estructura a las apps con flujos de varios pasos, como un formulario de compra o una lista con detalle.

**Cuándo usarlo:** para profundizar en el contenido (lista → detalle → más detalle), para flujos lineales (paso 1 → paso 2 → paso 3) y para cualquier pantalla que tenga una pantalla "padre" a la que volver.

### Patrones de contenido y listas móviles

Estos patrones definen **cómo se organiza y se presenta el contenido** en pantalla. La pantalla del celular es chica, así que hay que elegir bien cómo mostrar mucha información sin abrumar.

#### Listas (lists)

Una lista es un conjunto de ítems dispuestos uno debajo del otro. Cada ítem tiene contenido textual (título, descripción) y opcionalmente una imagen o un ícono. Es el patrón más básico y universal para presentar conjuntos de datos: contactos, mensajes, resultados de búsqueda, ajustes.

**Cuándo usarla:** cuando hay muchos elementos del mismo tipo que se leen de arriba hacia abajo y el usuario necesita escanearlos rápido para encontrar uno en particular.

#### Tarjetas (cards)

Una tarjeta es un contenedor con bordes o sombra que agrupa información relacionada de un mismo tema. A diferencia de una lista plana, la tarjeta puede combinar imagen, texto y acciones en un solo bloque, como una ficha de producto, una publicación o un evento.

**Cuándo usarlas:** cuando cada ítem tiene contenido heterogéneo (varias piezas de información y acciones) o cuando los elementos deben distinguirse claramente entre sí. Las tarjetas permiten tocarlas para abrir el detalle.

#### Carruseles (carousels)

Un carrusel es una fila horizontal de ítems que se puede deslizar hacia los costados. Solo se ve una porción de los elementos y el resto aparece al deslizar. Es típico de banners de ofertas, historias o recomendaciones.

**Cuándo usarlo:** para contenido destacado que ocupa poco espacio y que se explora de forma horizontal, como promociones, categorías o contenido reciente. Conviene usarlo con moderación, porque al ocultar los ítems fuera de pantalla puede que el usuario no sepa que hay más.

#### Grid (grid)

Un grid es una cuadrícula de elementos dispuestos en filas y columnas. A diferencia de la lista (una sola columna), el grid muestra varios ítems por fila. Es ideal para contenido visual donde la imagen manda y el texto es secundario, como galerías de fotos, productos o videos.

**Cuándo usarlo:** cuando el contenido es principalmente visual y el usuario prefiere ver muchos ítems a la vez en lugar de leer descripciones largas.

### Patrones de entrada de datos móviles

Estos patrones definen **cómo la persona ingresa información** en el dispositivo. Es un área crítica, porque escribir en un teclado virtual es lento y propenso a errores; cada dato pedido tiene un costo para el usuario.

#### Formularios en móvil (mobile forms)

Un formulario móvil es un conjunto de campos que el usuario completa, pero pensado para las limitaciones del celular. Los campos se apilan verticalmente (uno por línea), cada uno con su etiqueta visible, y se usa el tipo de teclado adecuado para cada dato (numérico para teléfonos, con @ para emails).

**Cuándo usarlo:** siempre que haya que capturar datos. La regla de oro es **pedir la menor cantidad de campos posible** y dividir formularios largos en pasos para no abrumar.

#### Selectores (selectors / pickers)

Los selectores evitan que el usuario escriba: en su lugar, elige entre opciones predefinidas. En móvil se presentan como listas desplegables, ruedas de selección (para fechas y horas), botones de opción o chips.

**Cuándo usarlos:** cuando las opciones son conocidas y limitadas (día de nacimiento, país, talla). Elegir es mucho más rápido y menos propenso a errores que tipear, así que conviene reemplazar la escritura por selección siempre que sea posible.

#### Entrada por gestos (gesture-based input)

Es la entrada de datos mediante gestos en lugar de teclado: deslizar un interruptor, dibujar una firma, arrastrar un control deslizante (slider), hacer zoom con pellizco o girar la pantalla. Son interacciones rápidas y táctiles que no requieren escribir.

**Cuándo usarla:** para datos que se expresan mejor con movimiento que con texto, como un control de volumen, una valoración con estrellas o una firma digital. Como con toda navegación por gestos, hay que garantizar que la acción sea descubrible y accesible.

### Manejo del estado vacío y de los estados de carga y error

Una app móvil no siempre tiene contenido disponible. Toda pantalla puede encontrarse en uno de tres estados especiales, y el diseño debe contemplarlos para que el usuario nunca se sienta perdido.

#### Estado vacío (empty state)

Aparece cuando no hay contenido que mostrar: el usuario no tiene mensajes, no ha hecho pedidos o no hay resultados para una búsqueda. El patrón correcto es mostrar un mensaje claro que explique **por qué** no hay contenido y **qué puede hacer** el usuario a continuación (por ejemplo, un botón para empezar). Un estado vacío bien diseñado convierte una frustración en una oportunidad de acción.

**Cuándo usarlo:** en listas, búsquedas, bandejas de entrada y secciones que dependen de acciones del usuario.

#### Estados de carga (loading states)

Cuando la app está trayendo datos (por red o de la base de datos) hay que avisarle al usuario. Se usan indicadores de progreso: ruedas giratorias (spinners) para cargas cortas e indeterminadas, y barras de progreso o esqueletos (skeletons) para cargas más largas o con estructura conocida. Los esqueletos son especialmente útiles porque muestran la forma del contenido que viene.

**Cuándo usarlo:** en toda operación que tarde más de unos cientos de milisegundos, para que el usuario no piense que la app se congeló.

#### Estados de error (error states)

Cuando una operación falla (se cortó la red, el servidor no respondió, los datos son inválidos), la app debe comunicarlo de forma clara y ofrecer una salida: un botón para reintentar, o la opción de volver. Un buen estado de error explica qué pasó en lenguaje simple y propone el siguiente paso, en lugar de mostrar un mensaje técnico críptico.

**Cuándo usarlo:** ante fallas de conexión, tiempos de espera agotados o errores de validación. Es la otra cara de la moneda del estado de carga.

### Patrones de feedback

El feedback es la forma en que la aplicación **comunica al usuario el resultado de sus acciones**: "guardaste el cambio", "no se pudo enviar", "te quedan tres intentos". Hay tres patrones principales, que se diferencian por su urgencia y permanencia.

#### Toasts

El toast es un mensaje breve que aparece y desaparece solo, sin que el usuario tenga que hacer nada. Se usa para confirmaciones rápidas y no críticas ("Mensaje enviado", "Cambios guardados"). Por su naturaleza efímera, no sirve para información que el usuario deba leer con calma o para errores que requieran una acción.

**Cuándo usarlos:** para confirmaciones de acciones de baja importancia que no necesitan respuesta del usuario.

#### Diálogos (dialogs)

El diálogo es una ventana que se superpone al contenido y exige una decisión antes de continuar. Puede pedir confirmación ("¿Eliminar este archivo?"), presentar una alerta importante o solicitar un ingreso de datos. A diferencia del toast, el diálogo **interrumpe** y captura la atención, por eso se reserva para situaciones importantes.

**Cuándo usarlos:** para confirmaciones destructivas (borrar, salir sin guardar), para decisiones que detienen el flujo y para errores críticos. No deben usarse en exceso, porque interrumpen.

#### Banners (banners)

El banner es una franja que aparece generalmente en la parte superior de la pantalla y permanece visible hasta que el usuario la descarta o hasta que se resuelve la condición. Es menos intrusivo que el diálogo pero más notorio que el toast. Se usa para avisos persistentes: "sin conexión a internet", "se detectó una actualización", "el formulario tiene errores".

**Cuándo usarlos:** para avisos que deben permanecer visibles mientras exista la condición que los causa, sin bloquear por completo la interacción.

### Buenas prácticas de diseño móvil

Estas pautas no son un patrón puntual sino reglas que atraviesan a todos los patrones. Son la base de una buena experiencia móvil.

#### Objetivos táctiles de tamaño adecuado

Un objetivo táctil es cualquier zona de la pantalla que el usuario debe tocar para activar algo: un botón, un ícono, un enlace. **La recomendación de Material Design es un tamaño mínimo de 48 por 48 dp** (unidad de densidad de píxeles independiente del dispositivo). Si los objetivos son demasiado chicos, el usuario los toca mal, se frustra y comete errores. Regla práctica: el área que se toca debe ser generosa, aunque el elemento visual (el ícono) sea más pequeño.

#### Área del pulgar (thumb zone)

Las personas sostienen el celular con una mano y tocan con el pulgar. El pulgar se mueve con comodidad en una zona en forma de arco en la parte **inferior y central** de la pantalla; llegar a la esquina superior requiere estirarse y a veces cambiar de mano. Por eso los elementos de uso frecuente (como las pestañas inferiores y los botones principales) se ubican en la zona del pulgar, y las acciones de uso ocasional se dejan arriba.

#### Consistencia con Material Design (Android) y Human Interface Guidelines (iOS)

Cada plataforma tiene su propia guía de diseño oficial. **Material Design** es la guía de Google para Android y se basa en superficies, elevación y movimiento. **Las Human Interface Guidelines (HIG)** son la guía de Apple para iOS y priorizan la claridad, la deferencia hacia el contenido y la profundidad. Usar cada guía en su plataforma garantiza que la app se sienta "nativa": que respete las convenciones que el usuario ya conoce en su sistema operativo.

## Analogía

Imaginá que diseñás la planta de un edificio de departamentos.

La **pestaña inferior** es como el hall central del edificio: tiene pocas puertas bien visibles y siempre sabés cuál elegir para llegar a las zonas principales. La **barra de acción superior** es el cartel en cada piso que te dice "estás en el piso 3" y las salidas de emergencia (las acciones rápidas). El **cajón de navegación** es el tablero con el directorio completo en la entrada: no está a la vista todo el tiempo, pero si lo abrís encontrás todos los locales, hasta los que están en el subsuelo.

La **pila de pantallas** es el recorrido por una escalera: subís de la planta baja (lista) al primer piso (detalle) y al segundo (subdetalle), y para volver bajás por donde viniste. Los **gestos** son los atajos que solo los que conocen el edificio usan, como la puerta de servicio que no tiene cartel. Las **tarjetas** son los departamentos: cada uno agrupa todo lo suyo (habitaciones, baño, cocina) en un bloque. El **carrusel** es la vidriera de la planta baja que va rotando los productos en oferta.

Y el **toast, el diálogo y el banner** son las formas de avisar. El toast es el encargado que te dice "puerta cerrada" al pasar sin que te detengas. El diálogo es el guardia que te corta el paso y te pregunta "¿realmente querés tirar este mueble? Sí / No". El banner es el cartel permanente de "ascensor en mantenimiento" que queda visible hasta que lo arreglan.

## Ejemplo práctico

Pensemos en una app de **compra de productos** y cómo se aplican estos patrones.

La pantalla principal usa **pestañas inferiores** con cuatro secciones: "Inicio", "Buscar", "Carrito" y "Perfil". Arriba, la **barra de acción superior** muestra el título "Inicio" y un ícono de notificaciones.

En "Inicio" el contenido se organiza con una mezcla de patrones: un **carrusel** horizontal arriba con los productos en oferta, y debajo un **grid** de dos columnas con los productos destacados. Cada producto es una **tarjeta** con imagen, precio y un botón de agregar. Al tocar una tarjeta, la **pila de pantallas** nos lleva del grid al detalle del producto, y con la flecha de atrás volvemos.

Al agregar un producto, aparece un **toast** breve: "Agregado al carrito". Si intentamos agregar el mismo producto dos veces, un **diálogo** pregunta: "Ya tenés este artículo. ¿Querés agregar otro?" con opciones "Sí" y "No". Si la red está caída, un **banner** fijo avisa "Sin conexión a internet" en la parte superior.

Cuando entramos al carrito vacío por primera vez, vemos un **estado vacío** con un mensaje ("Tu carrito está vacío") y un botón "Ver productos" que nos devuelve al grid. Mientras la app carga los productos desde el servidor, vemos **esqueletos** con la forma de las tarjetas. Si la carga falla, aparece un **estado de error** con el mensaje "No pudimos cargar los productos" y un botón "Reintentar".

Todos los botones de la app respetan el **objetivo táctil mínimo de 48 por 48 dp**, los **íconos de navegación y los botones principales** están en la **zona del pulgar** (abajo y en el centro), y la app usa las convenciones de **Material Design** en Android y de las **HIG** de Apple en iOS (por ejemplo, en Android el retroceso se resuelve con el botón "atrás" del sistema, mientras que en iOS se usa la flecha superior izquierda).

## Comparativas

La siguiente tabla resume los patrones de navegación y cuándo conviene usar cada uno.

| Patrón de navegación | Cuántas secciones principales | Visibilidad de las opciones | Cuándo usarlo |
|:---------------------|:-----------------------------|:----------------------------|:--------------|
| Pestañas inferiores | 2 a 5 | Siempre visibles | Destinos principales que el usuario visita seguido y deben estar a un toque |
| Barra de acción superior | Acompaña cualquier cantidad | Título y acciones contextuales | Toda pantalla con título y acciones rápidas; no es un menú en sí |
| Cajón de navegación (hamburguesa) | Más de 5, o jerárquicas | Ocultas hasta deslizar el panel | Menús extensos, ajustes, cuentas; cuando no entran en pestañas |
| Gestos (swipes) | Complemento | No visibles | Acciones repetidas (galerías) o acciones sobre ítems; nunca como única vía |
| Pila de pantallas (stack) | Flujos de profundidad | Muestra la pantalla actual | Lista → detalle, flujos de varios pasos, retroceso hacia la pantalla padre |

Otra comparación útil entre los patrones de feedback:

| Patrón | Nivel de interrupción | Cuánto dura | Cuándo usarlo |
|:-------|:----------------------|:------------|:--------------|
| Toast | Muy bajo | Desaparece solo | Confirmaciones breves y no críticas |
| Banner | Medio | Permanece hasta que se resuelve | Avisos persistentes (sin conexión, actualización) |
| Diálogo | Alto | Interrumpe hasta que el usuario decide | Confirmaciones destructivas y errores críticos |

## Fuentes

Estas son las guías oficiales de diseño usadas para este material. Ambas son seguras y de referencia obligatoria para el diseño mobile.

### Material Design

https://m3.material.io/

Guía oficial de diseño de Google para Android y para la web. Define componentes, patrones de navegación, sistemas de elevación y color, y las pautas de objetivos táctiles y consistencia. Es la referencia de base para los patrones de navegación, contenido, entrada de datos y feedback en la plataforma Android.

### Apple Human Interface Guidelines

https://developer.apple.com/design/human-interface-guidelines/

Guía oficial de diseño de Apple para iOS y macOS. Explica las convenciones de la plataforma (navigation bar, gestos, retroceso con flecha) y los principios de claridad y deferencia al contenido. Es la referencia para adaptar los mismos patrones a la experiencia nativa de iOS.

### Nielsen Norman Group - artículos de diseño mobile

https://www.nngroup.com/articles/

Portal de artículos de investigación en experiencia de usuario (UX) sobre diseño mobile. Su contenido profundiza en temas como el área del pulgar, los objetivos táctiles, la usabilidad de los menús hamburguesa y los patrones de navegación, complementando las guías oficiales con evidencia de estudios de usuarios.

## Para practicar

1. **Identificar patrones:** abrí tres aplicaciones conocidas de tu celular y anotá qué patrones de navegación usan (pestañas, cajón, gestos, pila). ¿Cuántas secciones tienen en las pestañas inferiores? ¿Usan carruseles o grids para el contenido? ¿Cómo manejan los estados de carga y error?

2. **Decidir el patrón adecuado:** para cada caso, elegí el patrón de navegación correcto y justificá: (a) una app de banco con cuatro secciones principales; (b) una app de ajustes de un sistema con más de diez secciones; (c) una galería de fotos donde el usuario pasa de una imagen a otra; (d) una app de recetas que va de la lista de recetas al detalle de una receta.

3. **Detectar malas prácticas:** buscá en una app que uses seguido un botón demasiado chico para tocar, un elemento fuera de la zona del pulgar que se usa mucho, o un diálogo que interrumpe por una acción trivial. ¿Cómo lo rediseñarías?

4. **Diseñar estados vacíos:** para una app de lista de tareas sin tareas pendientes, un carrito de compras vacío y una búsqueda sin resultados, redactá el mensaje y la acción sugerida que mostrarías en cada caso.

5. **Revisar el objetivo táctil:** en una pantalla simple que diseñes, verificá que todos los botones cumplan el mínimo de 48 por 48 dp. Si un botón es más chico, aumentá su área táctil aunque el ícono visual siga siendo pequeño.
