# Procesos ágiles

## Introducción

Durante décadas, la industria del software desarrolló productos con metodologías llamadas "predictivas" o "en cascada": se planificaba todo por adelantado, se escribían documentos gigantes y se recién entregaba el producto al final, muchas veces meses o años después. El problema: para cuando se entregaba, el mercado, el usuario o los requisitos ya habían cambiado.

Frente a esta rigidez, un grupo de profesionales se reunió en 2001 y firmó el Manifiesto Ágil, un documento breve que propone un cambio de mentalidad: en lugar de resistirse al cambio, se lo abraza; en lugar de entregar todo al final, se entregan pequeños resultados útiles de forma continua. Así nació el "desarrollo ágil" (agile software development).

En esta unidad vas a entender qué significa realmente "ser ágil", y vas a conocer los dos marcos de trabajo (frameworks) más usados del mundo para llevar esa filosofía a la práctica: Scrum y Kanban. También verás herramientas introductorias para estimar el trabajo y para describir lo que el usuario necesita: las historias de usuario (user stories). No hace falta que sepas nada previo; todo lo explicamos desde cero.

## Conceptos clave

### Desarrollo ágil (agile software development)

Es una filosofía de trabajo que prioriza la entrega rápida de valor, la colaboración del equipo, la respuesta al cambio y el diálogo constante con el cliente. Se apoya en cuatro valores y doce principios del Manifiesto Ágil. Algunos de los valores más importantes: se valora a las personas y su interacción por sobre los procesos y las herramientas; se valora el software funcionando por sobre la documentación extensa; se valora la colaboración con el cliente por sobre la negociación de contratos; se valora responder al cambio por sobre seguir un plan fijo.

### Sprint

Es el corazón de Scrum: una iteración (ciclo de trabajo) de duración fija, normalmente de una a cuatro semanas. Todos los Sprints duran lo mismo dentro de un mismo proyecto. Al terminar cada Sprint, el equipo debe entregar un incremento de producto funcionando. La idea es producir algo utilizable una y otra vez, en ciclos cortos.

### Product Backlog (Lista de Producto)

Es la lista priorizada de todo lo que el producto necesita. No es un documento cerrado: crece y cambia constantemente a medida que aparece nueva información. Cada elemento de la lista (que puede ser una historia de usuario, una corrección o una mejora) tiene una prioridad y, en general, una estimación de esfuerzo.

### Sprint Backlog (Lista del Sprint)

Es el subconjunto del Product Backlog que el equipo se compromete a completar en un Sprint concreto, más el plan para lograrlo. Solo el equipo puede modificarla durante el Sprint.

### Increment (Incremento)

Es el resultado sumado de todos los elementos terminados en el Sprint, sumado a los Increments anteriores. Cada Increment debe ser un producto potencialmente utilizable: puede no tener todas las funciones, pero lo que tiene debe funcionar.

### Roles en Scrum

- **Product Owner (Dueño de Producto)**: es la única persona responsable de maximizar el valor del producto. Decide qué entra al Product Backlog, su prioridad y qué es "listo" desde el punto de vista del negocio. Es el puente entre el cliente y el equipo.
- **Scrum Master**: no es un jefe ni un manager tradicional. Es quien ayuda a que el equipo entienda y aplique Scrum, elimina obstáculos (bloqueos) y facilita los eventos. Cuida el proceso.
- **Equipo de desarrollo (Development Team)**: son los que construyen el incremento. Es un equipo auto-organizado y multidisciplinario: juntos tienen todas las habilidades para convertir los requisitos en producto funcionando.

### Eventos en Scrum

- **Sprint Planning (Planificación del Sprint)**: reunión al inicio del Sprint donde el equipo elige qué elementos del Product Backlog va a trabajar y define cómo lo va a lograr.
- **Daily Scrum (Reunión diaria)**: reunión corta de no más de 15 minutos, todos los días, donde cada miembro dice qué hizo ayer, qué hará hoy y qué obstáculos tiene. No es para resolver problemas ahí mismo, sino para coordinarse.
- **Sprint Review (Revisión del Sprint)**: al final del Sprint, el equipo muestra el incremento a los interesados y recibe retroalimentación. Sirve para ajustar el Product Backlog.
- **Sprint Retrospective (Retrospectiva)**: reunión después de la Review donde el equipo reflexiona sobre cómo trabajó y decide qué mejorar en el próximo Sprint. Es la oportunidad de mejorar el proceso.

### Kanban

Kanban significa "tablero" o "señal" en japonés. Es un marco de trabajo (framework) que gestiona el trabajo de forma continua, sin iteraciones fijas. Se basa en visualizar el flujo de trabajo en un tablero (kanban board), limitar la cantidad de trabajo en progreso (WIP) y optimizar el flujo para entregar de forma constante.

### Tablero Kanban (Kanban board)

Es un tablero con columnas que representan etapas del proceso, por ejemplo: "Por hacer", "En curso", "En revisión", "Terminado". Cada tarjeta representa un ítem de trabajo. Al mover las tarjetas entre columnas, todo el equipo ve el estado real del trabajo de un vistazo.

### Límites de trabajo en progreso (WIP limits)

Es una regla que limita cuántos ítems pueden estar simultáneamente en una columna. Si una columna llega a su límite, no se pueden agregar más tarjetas hasta que avancen. Esto evita la sobrecarga del equipo y obliga a terminar antes de empezar cosas nuevas.

### "Deja de empezar, empieza a terminar"

Es el lema de Kanban. En vez de abrir muchas tareas en paralelo y terminar pocas, Kanban promueve concentrarse en pocas tareas y llevarlas hasta el final. Terminar más tareas completas aporta más valor que tener muchas a medio hacer.

### Historia de usuario (user story)

Es una descripción corta y sencilla de una necesidad desde el punto de vista del usuario, escrita en lenguaje cotidiano. Su formato típico es: "Como [rol], quiero [acción], para [beneficio]". Ejemplo: "Como productor, quiero registrar el peso de un animal, para llevar un control de su evolución".

### Estimación en puntos de historia (story points)

Es una forma relativa de medir el esfuerzo de una historia de usuario. En lugar de decir "me llevará 3 días", el equipo compara historias entre sí y les asigna un número (por ejemplo, 1, 2, 3, 5, 8), usando una escala conocida como Fibonacci. No mide horas, mide tamaño relativo del trabajo y su complejidad.

## Analogía

Imaginá que querés construir una casa, pero en vez de seguir el plan tradicional (dibujar los planos completos durante dos años y después construir), decidís trabajar ágil. El propietario (el cliente) quiere una casa, pero no sabe exactamente cómo será.

Con Scrum: dividís el proyecto en Sprints. En el primer Sprint (una semana) construís los cimientos. En el segundo, las paredes de una habitación. Al final de cada Sprint le mostrás al propietario lo que hay: "Mirá, ya tenés los cimientos y una habitación usable". Él te dice "me gustaría la cocina más grande" y vos lo anotás en el Product Backlog. Cada semana entregás algo que se puede usar y aprendés del dueño.

El Product Owner es como el representante del dueño de la casa: decide qué es lo más importante para construir a continuación. El Scrum Master es el capataz que se asegura de que no haya demoras por falta de materiales (obstáculos) y de que todos entiendan el método. El equipo de desarrollo son los albañiles, plomeros y electricistas, que juntos tienen todas las habilidades.

Con Kanban, en cambio, no hay Sprints. La casa se va construyendo como un flujo continuo: el tablero muestra columnas "A planificar", "En obra", "En terminaciones", "Listo". Ponés un límite de WIP: no más de dos habitaciones "en obra" a la vez. Si la columna "En obra" está llena, no empezás otra habitación: primero terminás las que están a medio hacer. Así el flujo es constante, como una línea de agua que nunca se corta.

## Ejemplo práctico

Un equipo está desarrollando un sistema ganadero para que un productor registre y gestione su ganado (animales, peso, vacunas, ventas). Veamos cómo aplicaría Scrum y Kanban.

### Con Scrum

El Product Owner arma el Product Backlog con historias de usuario. Por ejemplo:

- "Como productor, quiero registrar un animal con su caravana, para identificarlo de forma única."
- "Como veterinario, quiero cargar la vacunación de un lote, para llevar el historial sanitario."
- "Como productor, quiero consultar el peso histórico de un animal, para decidir el momento de venta."

El equipo planifica el Sprint 1 (de dos semanas) y elige las dos primeras historias para el Sprint Backlog. Cada día hacen el Daily Scrum de 15 minutos: "Ayer terminé el registro de animales, hoy arranco el listado, y me bloquea que no tengo acceso a la base de datos de pruebas".

Al final del Sprint, en la Sprint Review, muestran al productor el registro de animales funcionando. Él sugiere agregar el campo "sexo del animal", que el Product Owner prioriza para el próximo Sprint. Luego, en la Sprint Retrospective, el equipo detecta que las reuniones de estimación eran muy largas y decide probar la técnica de planificación de póker (planning poker) para agilizarlas.

### Con Kanban

Si el mismo equipo prefiere Kanban, arma un tablero con columnas: "Por hacer", "En curso", "En revisión", "Hecho". Cada tarjeta es una historia. Ponen un límite de WIP de 2 en la columna "En curso". Si ya hay dos tarjetas en esa columna y llega una nueva, nadie la arranca hasta terminar una de las dos.

El equipo trabaja de forma continua: cuando una tarjeta llega a "Hecho", automáticamente "tira" de la siguiente historia del Product Backlog a "En curso". No hay planificación de Sprint porque el flujo es permanente, y las historias se priorizan sobre la marcha.

## Comparativas

| Aspecto | Scrum | Kanban |
|:--------|:------|:-------|
| Filosofía | Basado en iteraciones (Sprints) de duración fija | Flujo continuo, sin iteraciones fijas |
| Duración | Sprints de 1 a 4 semanas | Sin ciclos; entrega continua |
| Roles | Roles definidos: Product Owner, Scrum Master, equipo | Sin roles obligatorios; el equipo se organiza como quiera |
| Planificación | Sprint Planning al inicio de cada Sprint | Planificación continua, priorizando sobre la marcha |
| Cambios | El Sprint Backlog es fijo durante el Sprint | Los cambios pueden ingresar en cualquier momento |
| Medición | Velocidad por Sprint | Tiempo de ciclo y tiempo de entrega (lead time) |
| Cuándo usarlo | Proyectos con requisitos que pueden definirse en entregas | Equipos con flujo de trabajo variable y prioridades cambiantes |

Ambos comparten la base del Manifiesto Ágil: entregar valor rápido, colaborar con el cliente y adaptarse al cambio. La diferencia central es que Scrum organiza el trabajo en "cajas de tiempo" (Sprints), mientras que Kanban deja que el trabajo fluya de forma continua.

## Fuentes

### Manifiesto Ágil (español)

https://agilemanifesto.org/iso/es/manifesto.html

### Scrum Guide (inglés oficial)

https://scrumguides.org

### Atlassian - ¿Qué es Scrum? (español)

https://www.atlassian.com/es/agile/scrum

## Para practicar

1. Leé el Manifiesto Ágil (fuente 1) y elegí los dos valores que te parezcan más importantes. Explicá con tus palabras por qué creés que marcan una diferencia frente a las metodologías tradicionales.
2. Con un compañero, armá un mini Product Backlog de 5 historias de usuario para el sistema ganadero. Escribí cada historia con el formato "Como [rol], quiero [acción], para [beneficio]".
3. En una hoja, dibujá un tablero Kanban de 4 columnas y colocá las 5 historias del punto 2. Definí un límite de WIP de 2 en la columna "En curso" y explicá qué pasa si llega una historia nueva y esa columna ya está llena.
4. Investigá en la Scrum Guide (fuente 2) qué diferencia existe entre un Product Owner y un Scrum Master, y anotá tres responsabilidades de cada uno.
5. Elegí dos historias del punto 2 y estimarlas en puntos de historia (por ejemplo, 3 y 8). Justificá por qué una tiene más tamaño relativo que la otra.
6. Completá la tabla de comparación Scrum vs Kanban agregando una fila propia con un criterio que vos consideres útil, por ejemplo "riesgo" o "tamaño de equipo".
7. Pensá en un proyecto de la vida cotidiana (organizar una fiesta, armar un viaje). ¿Aplicarías Scrum o Kanban? Justificá tu respuesta usando al menos dos conceptos vistos.
