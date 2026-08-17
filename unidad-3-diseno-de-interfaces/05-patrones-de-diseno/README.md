# Patrones de diseño de interfaz

## Introducción

Cuando diseñamos una pantalla, por más originales que queramos ser, casi siempre nos encontramos con los mismos problemas: ¿dónde va el menú? ¿cómo hago para que el usuario sepa en qué parte de la aplicación está? ¿cómo le aviso que guardó los cambios? ¿qué muestro cuando todavía no hay datos?

La buena noticia es que estos problemas ya fueron resueltos miles de veces por otras personas y existen soluciones probadas, documentadas y entendibles para cualquier usuario. Esas soluciones son los **patrones de diseño de interfaz** (user interface patterns). Este material te explica qué son, cuáles son los más importantes, qué problema resuelve cada uno y cuándo conviene usarlos.

No se trata de memorizar nombres: se trata de reconocer problemas de diseño y saber qué solución ya probada existe para cada uno. Es el mismo espíritu que los patrones de diseño de software (como los de la "Gang of Four"), pero aplicado a las pantallas que el usuario ve y toca.

## Conceptos clave

### ¿Qué es un patrón de interfaz de usuario?

Un **patrón de interfaz de usuario** (user interface pattern) es una solución reutilizable y probada a un problema recurrente de diseño de pantallas.

Tiene tres características esenciales:

1. **Recurrente**: el problema aparece una y otra vez en aplicaciones distintas (casi todas las apps tienen menú, formularios, listas, etc.).
2. **Reutilizable**: la solución se puede aplicar en contextos diferentes con pequeños ajustes.
3. **Convencional**: los usuarios ya lo conocen, por lo que no necesitan aprender a usarlo desde cero.

Cuando aplicás un patrón, no estás copiando el diseño de otra app: estás adoptando una **convención** que reduce el esfuerzo cognitivo del usuario. Por ejemplo, todos sabemos que la "X" arriba a la derecha de una ventana la cierra; si inventamos un diseño donde la "X" guarda los datos, confundimos a todos.

El catálogo de referencia más conocido es el de **Jennifer Tidwell** en su libro "Designing Interfaces", que organiza los patrones por el problema que resuelven: cómo organizar la página, cómo navegar, cómo ingresar datos, cómo dar feedback, entre otros.

### Patrones de navegación

Los patrones de navegación resuelven el problema de **cómo se mueve el usuario** entre las distintas pantallas y secciones de la aplicación, y **cómo sabe dónde está** en cada momento.

#### Menús (menus)

Es la forma más clásica de organizar las secciones principales. Agrupan las opciones de la aplicación en una estructura visible y estable.

- **Qué problema resuelve**: el usuario necesita llegar rápido a las secciones principales sin adivinar.
- **Cuándo usarlo**: casi siempre. Cuando la aplicación tiene más de una o dos secciones claras.
- **Variantes**: menú superior (horizontal), menú lateral (vertical, muy común en aplicaciones de escritorio y paneles de administración), menú desplegable (dropdown) para opciones secundarias, y menú de hamburguesa (☰) en móviles para ahorrar espacio.

#### Pestañas o tabs

Organizan el contenido de una misma pantalla en secciones separadas, mostrando solo una a la vez.

- **Qué problema resuelve**: hay mucho contenido que no se puede ver junto, pero querés que el usuario cambie entre secciones sin salir de la pantalla.
- **Cuándo usarlo**: cuando las secciones son **pares** (sin jerarquía entre sí) y el usuario necesita compararlas o alternar rápidamente. Por ejemplo, "General" / "Seguridad" / "Privacidad" en la configuración de una cuenta.
- **Cuándo NO**: si son más de siete u ocho pestañas, se vuelve ilegible; mejor usar menú o lista.

#### Migas de pan o breadcrumbs

Es una ruta que muestra dónde estás dentro de la jerarquía de la aplicación, generalmente en la parte superior de la página.

- **Qué problema resuelve**: el usuario se pierde en una estructura jerárquica profunda y no sabe cómo volver atrás ni qué relación tiene la pantalla actual con las anteriores.
- **Cuándo usarlo**: en sitios o aplicaciones con jerarquía de **3 niveles o más** (por ejemplo: Categoría > Subcategoría > Producto).
- **Cuándo NO**: en interfaces planas de una o dos capas, las migas son ruido innecesario.

#### Navegación por pasos o wizard

Divide una tarea larga en una secuencia de pasos numerados, mostrando al usuario dónde está y cuánto le falta.

- **Qué problema resuelve**: una tarea larga o compleja (como registrarse, configurar algo, o comprar en varios pasos) abruma si se muestra toda junta.
- **Cuándo usarlo**: cuando la tarea exige datos en un orden específico, o cuando dividirla reduce el error y el abandono. Ejemplos típicos: procesos de registro paso a paso, carritos de compra, configuraciones iniciales.
- **Beneficio extra**: le da al usuario una sensación de progreso ("voy en el paso 2 de 4"), lo que reduce el abandono.

### Patrones de entrada de datos

Estos patrones resuelven el problema de **cómo el usuario ingresa información** a la aplicación de forma clara, rápida y sin errores.

#### Formularios (forms)

Es el patrón más básico de entrada de datos: un conjunto de campos que el usuario completa y envía.

- **Qué problema resuelve**: recolectar datos del usuario de manera estructurada.
- **Cuándo usarlo**: siempre que necesites datos del usuario (registro, login, contacto, búsqueda avanzada, etc.).
- **Buenas prácticas**: cada campo debe tener una etiqueta clara, el formulario no debe pedir datos innecesarios, y el botón de envío debe ser evidente.

#### Validación

Es el mecanismo que comprueba que los datos ingresados son correctos antes de aceptarlos.

- **Qué problema resuelve**: recibir datos inválidos, incompletos o en un formato incorrecto, que luego generan errores en el sistema.
- **Cuándo usarla**: en todo formulario. La validación **en el momento** (mientras el usuario escribe) evita la frustración de enterarse al final de que todo estaba mal.
- **Tipos**: validación de formato (email válido, números), de requerido (campo obligatorio) y de consistencia (que las contraseñas coincidan).
- **Importante**: los mensajes de error deben decir **qué pasó y cómo corregirlo**, nunca solo "Error".

#### Autocompletado (autocomplete)

Mientras el usuario escribe, la aplicación sugiere opciones posibles basadas en lo que ya escribió.

- **Qué problema resuelve**: tipear datos largos, conocidos o propensos a error (ciudades, marcas, términos de búsqueda) es lento y propenso a equivocaciones.
- **Cuándo usarlo**: cuando el dato proviene de una lista finita de opciones (por ejemplo, elegir un país), o cuando el usuario escribe algo que la aplicación ya conoce (historial de búsqueda).
- **Beneficio**: acelera la entrada y reduce errores de tipeo.

#### Entrada de fecha (date picker)

Es un control específico para que el usuario elija una fecha sin escribirla a mano.

- **Qué problema resuelve**: escribir fechas a mano es propenso a errores de formato (¿dd/mm/aaaa o mm/dd/aaaa?) y a fechas inválidas (30 de febrero).
- **Cuándo usarlo**: siempre que la aplicación necesite una fecha. Un calendario desplegable o un selector de día/mes/año evita ambigüedades.
- **Beneficio**: garantiza un formato consistente y elimina errores de interpretación.

### Patrones de contenido y listas

Resuelven el problema de **cómo presentar y organizar información** para que sea fácil de recorrer, comparar y entender.

#### Lista (list)

Presenta los elementos uno debajo del otro, típicamente uno por fila.

- **Qué problema resuelve**: mostrar muchos elementos de manera ordenada y escaneable.
- **Cuándo usarla**: cuando cada elemento tiene un peso similar y se necesita recorrerlos verticalmente. Es la base de las "noticias", "mensajes", "contactos", etc.
- **Variantes**: lista con imágenes, lista agrupada por categorías.

#### Tarjeta o card

Presenta cada elemento como un bloque visual separado y autocontenido.

- **Qué problema resuelve**: mostrar información heterogénea o "rica" (imagen + texto + botón) de cada elemento de forma atractiva.
- **Cuándo usarla**: cuando cada elemento tiene contenido variado que se muestra mejor en un bloque (productos, artículos, resultados de búsqueda). Muy común en interfaces modernas y móviles.

#### Cuadrícula o grid

Organiza los elementos en filas y columnas formando una grilla regular.

- **Qué problema resuelve**: mostrar muchos elementos visuales del mismo tipo (imágenes, productos, fotos) aprovechando el espacio horizontal.
- **Cuándo usarla**: cuando los elementos son predominantemente visuales y de tamaño similar (galerías de fotos, catálogos de productos).
- **Relación con cards**: una cuadrícula suele estar compuesta de tarjetas.

#### Tabla (table)

Organiza la información en filas y columnas, con encabezados que identifican cada columna.

- **Qué problema resuelve**: comparar datos estructurados y con varios atributos (por ejemplo, una lista de alumnos con su legajo, nota y condición).
- **Cuándo usarla**: cuando cada elemento tiene **múltiples campos** y el usuario necesita compararlos, ordenarlos o filtrarlos por columna (típico en paneles de administración y reportes).
- **Cuándo NO**: cuando hay mucha información visual por elemento o cuando la tabla se vuelve tan ancha que no entra en la pantalla; ahí conviene una tarjeta.

### Patrones de feedback y estado

Resuelven el problema de **cómo comunicarle al usuario** qué está pasando, si algo salió bien, mal, o si no hay nada que mostrar.

#### Modales o diálogos (modals)

Son ventanas que se superponen al contenido y bloquean la interacción con la pantalla de atrás hasta que el usuario las cierra o responde.

- **Qué problema resuelve**: conseguir una respuesta o decisión del usuario sin que se distraiga (por ejemplo: "¿Seguro que querés eliminar este archivo?").
- **Cuándo usarlos**: para tareas que requieren foco total y una respuesta rápida. **Con moderación**: abusar de los modales interrumpe el flujo y molesta.
- **Contraste con toasts**: a diferencia de las notificaciones, el modal **exige** una acción del usuario.

#### Notificaciones o toasts

Son mensajes breves que aparecen de forma temporal (generalmente en un costado o abajo) y desaparecen solos.

- **Qué problema resuelve**: informar al usuario de un evento sin interrumpir lo que está haciendo (por ejemplo: "Cambios guardados" o "Mensaje enviado").
- **Cuándo usarlos**: para confirmaciones de acciones y avisos que no requieren respuesta inmediata.
- **Contraste con modales**: el toast **no bloquea** ni exige acción; es informativo y efímero.

#### Estados vacíos (empty states)

Es lo que se muestra cuando todavía no hay datos que presentar en una sección.

- **Qué problema resuelve**: una pantalla en blanco confunde y hace pensar que hay un error; el usuario no sabe qué hacer.
- **Cuándo usarlos**: siempre que una sección puede estar sin contenido (bandeja vacía, lista de favoritos vacía, sin resultados de búsqueda).
- **Cómo hacerlo bien**: en vez de un espacio en blanco, mostrar un mensaje amigable, una imagen y una **acción sugerida** ("Aún no tenés favoritos. Tocá la estrella para agregar uno.").

#### Mensajes de error y confirmación

Son mensajes específicos que informan que algo falló, o que piden confirmación antes de una acción riesgosa.

- **Qué problema resuelven**: evitar acciones irreversibles por accidente (confirmación) y ayudar al usuario a corregir un error (mensajes de error).
- **Cuándo usarlos**: confirmación antes de eliminar o sobrescribir datos; mensajes de error en formularios y operaciones fallidas.
- **Cómo hacerlo bien**: un buen mensaje de error indica el problema, la causa y cómo solucionarlo, en un lenguaje claro, no técnico.

## Analogía

Imaginá que sos un maestro constructor y te encargan hacer una casa, pero **no partís de cero**: hay un manual de soluciones probadas para los problemas típicos.

- El **menú** es como el mapa de la casa: te dice qué hay y cómo llegar.
- Las **migas de pan** son como las señales de "estás en la cocina, para volver al living girá a la izquierda".
- El **formulario** es como la planilla que llenás para pedir un trámite: tiene espacios claros y te dice qué escribir en cada uno.
- La **validación** es como el encargado que te devuelve la planilla diciendo "te faltó el DNI" **antes** de darla por terminada, no tres días después.
- Las **tarjetas** y **cuadrículas** son como el catálogo de productos de un supermercado online: cada producto con su foto y precio en un bloque.
- La **tabla** es como el cuadro de horarios de trenes: filas y columnas para comparar a qué hora pasa cada tren.
- El **modal** es como cuando el cajero te pregunta "¿Seguro que querés pagar en efectivo?" antes de cerrar la venta.
- El **toast** es como el aviso breve de "transacción aprobada" en el cajero automático: aparece, lo leés y desaparece.
- El **estado vacío** es como cuando abrís la heladera y está vacía: mejor que te digan "no hay nada, acá podés agregar" a que te quedés mirando una heladera abierta sin saber qué hacer.

La clave de los patrones es que **todos ya conocemos estas convenciones**, así que no hace falta que cada usuario aprenda una casa nueva desde cero.

## Ejemplo práctico

Tomemos una aplicación de **gestión de tareas (to-do)** y apliquemos los patrones a cada pantalla.

**1. Pantalla de login (entrada de datos)**
- **Formulario** con campos "Usuario" y "Contraseña".
- **Validación** en vivo: si el email no tiene @, avisa apenas el usuario termina de escribir.
- **Mensaje de error** si las credenciales son incorrectas: "Usuario o contraseña inválidos. Revisá e intentá de nuevo."

**2. Pantalla principal con proyectos y tareas**
- **Menú lateral** para ir a "Mis proyectos", "Calendario" y "Configuración".
- **Migas de pan** si navegás en jerarquía: "Inicio > Proyecto Marketing > Tareas".
- **Lista** para las tareas del día, una debajo de otra.
- **Cuadrícula de tarjetas** para mostrar los proyectos, cada uno con su nombre, avance y fecha límite.

**3. Crear una tarea (wizard)**
- **Navegación por pasos**: "1. Datos básicos, 2. Recordatorio, 3. Revisión".
- **Autocompletado** en el campo "Asignar a", que sugiere contactos mientras escribís.
- **Date picker** para elegir la fecha de vencimiento sin escribirla a mano.

**4. Feedback durante el uso**
- **Toast** ("Tarea guardada correctamente") cuando guardás, sin interrumpirte.
- **Modal de confirmación** antes de eliminar: "¿Seguro que querés eliminar la tarea 'Informe'? Esta acción no se puede deshacer."
- **Estado vacío** en la sección "Finalizadas" la primera vez: "Aún no tenés tareas finalizadas. Cuando completes una, aparece acá."

Así, con un solo ejemplo, vemos cómo los patrones se combinan para resolver cada problema puntual de una pantalla.

## Comparativas

### Patrón según cuándo usarlo

| Patrón | Problema que resuelve | Cuándo usarlo | Cuándo NO |
|--------|----------------------|---------------|-----------|
| Menú | Acceso a secciones principales | Aplicación con varias secciones | Una sola pantalla simple |
| Pestañas (tabs) | Alternar entre secciones pares | Pocas secciones sin jerarquía, comparar rápido | Más de 7 u 8 secciones |
| Migas de pan | Ubicar al usuario en jerarquía | Estructura de 3 niveles o más | Interfaces planas |
| Wizard (pasos) | Tareas largas y ordenadas | Registro, compra, configuración | Tareas cortas de un paso |
| Formulario | Recolectar datos | Cualquier entrada de datos | Cuando no hacés falta pedir datos |
| Validación | Evitar datos inválidos | Todo formulario | Nunca está de más (usar siempre) |
| Autocompletado | Acelerar tipeo y evitar errores | Datos de una lista conocida | Datos libres que nadie puede predecir |
| Date picker | Elegir fechas sin error | Cualquier fecha | — |
| Lista | Mostrar elementos ordenados | Recorrido vertical de elementos | Elementos con mucha información visual |
| Tarjeta (card) | Mostrar bloques ricos | Elementos con imagen + texto + acción | Elementos solo textuales y densos |
| Cuadrícula (grid) | Aprovechar espacio visual | Catálogos, galerías | Elementos con mucho texto |
| Tabla | Comparar datos estructurados | Múltiples campos, ordenar/filtrar | Mucho contenido visual por elemento |
| Modal | Exigir una decisión | Acciones críticas, confirmaciones | Avisos que no requieren respuesta |
| Toast | Informar sin interrumpir | Confirmaciones breves, avisos | Decisiones críticas que exigen respuesta |
| Estado vacío | Evitar pantallas en blanco | Secciones sin contenido | Siempre que aplique (es buena práctica) |
| Error / confirmación | Comunicar fallos / evitar accidentes | Fallos y acciones irreversibles | Siempre con mensajes claros |

### Tabla vs. Tarjeta

| Criterio | Tabla | Tarjeta |
|----------|-------|---------|
| Contenido | Texto estructurado, múltiples campos | Contenido variado (imagen + texto + acción) |
| Comparación | Excelente (columnas alineadas) | Regular (bloques separados) |
| Pantallas | Ideal en escritorio/paneles | Ideal en móviles |
| Ancho | Puede desbordarse si hay muchas columnas | Se adapta mejor |

## Fuentes

### Designing Interfaces (Jennifer Tidwell, O'Reilly)

Referencia clásica de patrones de diseño de interfaz. Organiza los patrones según el problema que resuelven (organización de la página, navegación, entrada de datos, feedback) y es la base de gran parte de este material.

https://www.oreilly.com/library/view/designing-interfaces-3rd/9781492051961/

### UI Patterns

Catálogo web de patrones de interfaz de usuario. Permite ver cada patrón con ejemplos reales de aplicaciones y explicación de cuándo usarlo. Es útil como consulta rápida para reconocer patrones en interfaces de la vida real.

https://ui-patterns.com/patterns

### Nielsen Norman Group (artículos de patrones de UI)

Grupo de investigación de usabilidad con artículos profundos sobre patrones de interfaz y mejores prácticas de UX. Es una fuente autorizada para profundizar en por qué funcionan los patrones y cómo aplicarlos bien.

https://www.nngroup.com/articles/

## Para practicar

1. **Cazadores de patrones**: abrí tres aplicaciones que uses a diario (un banco, un delivery, una red social). Identificá al menos cinco patrones de este material en cada una y anotá qué problema resuelven en ese contexto.

2. **Antes y después**: tomá una pantalla mal diseñada (o inventala) donde todo esté desordenado. Rediseñala aplicando los patrones correctos y justificá en una línea qué problema resuelve cada decisión.

3. **Decidí el patrón**: para cada caso, indicá qué patrón usarías y por qué:
   - Mostrar los productos de un catálogo de ropa con fotos.
   - Comparar las ventas de cinco sucursales por mes.
   - Un proceso de compra en cuatro pasos.
   - Una sección de "favoritos" que todavía no tiene nada.
   - Confirmar antes de eliminar una cuenta.
   - Informar que un archivo se subió correctamente.

4. **Test de pares**: en la tabla "Tabla vs. Tarjeta", tomá un mismo conjunto de datos (por ejemplo, alumnos con legajo, nota y estado) y mostralo de las dos formas. ¿Cuál conviene para un panel de administración y cuál para una app móvil? ¿Por qué?

5. **Reflexión sobre el modal**: ¿cuándo usás un modal y cuándo un toast? Buscá en una aplicación real un ejemplo de cada uno y explicá por qué esa elección es acertada (o no) según lo visto en este material.

*Material elaborado para la materia Arquitectura y Diseño de Interfaces (ADI), Tecnicatura Superior en Desarrollo de Software, IES 9-018. Ciclo 2026.*
