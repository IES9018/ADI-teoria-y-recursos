# Ciclo de vida del software

## Introducción

Cualquier producto que fabricamos —un auto, una casa, una aplicación móvil— no aparece de la nada. Pasa por una serie de etapas: primero se piensa qué se quiere lograr, después se diseña cómo hacerlo, luego se construye, se revisa, se entrega y, finalmente, se mantiene. Ese recorrido completo, desde que surge la idea hasta que el producto deja de utilizarse, es lo que llamamos **ciclo de vida del software**.

En esta materia veremos que el ciclo de vida no es una sola receta fija: existen distintos **modelos de proceso** que organizan esas etapas de maneras diferentes. Algunos modelos van paso a paso en línea recta (cascada), otros repiten ciclos cortos (iterativo e incremental), otros se enfocan en controlar el riesgo (espiral), otros separan la verificación de la validación (modelo en V) y otros ensamblan el sistema a partir de piezas ya hechas (basado en componentes). Elegir el modelo correcto es una decisión de arquitectura tan importante como elegir la tecnología.

Entender estos modelos te va a servir para algo muy concreto: cuando trabajes en un proyecto real, vas a tener que decidir cómo organizar el trabajo para entregar valor a tiempo, con calidad y sin sorpresas desagradables al final. Cada modelo tiene sus fortalezas y sus debilidades, y parte del oficio del desarrollador es saber cuándo conviene cada uno.

## Conceptos clave

### Qué es el ciclo de vida del software (software life cycle)

El ciclo de vida del software es el conjunto de **fases o etapas** por las que atraviesa un producto de software, desde que se identifica una necesidad hasta que el sistema se retira o se reemplaza. Describe el "antes, durante y después" de la vida de un programa: no termina cuando el código compila, sino que continúa mientras el sistema se usa, se corrige y se mejora.

Es importante distinguir dos ideas que a veces se confunden: el **ciclo de vida** (las fases que atraviesa el software) y el **modelo de proceso** (la manera particular en que se organizan esas fases). El ciclo de vida responde a la pregunta "¿qué etapas existen?"; el modelo de proceso responde a "¿en qué orden y con qué estrategia las recorro?".

### Las fases clásicas del desarrollo de software

Aunque cada modelo las organiza distinto, la mayoría reconoce estas etapas:

- **Análisis / Requisitos (requirements):** Se descubre y documenta qué debe hacer el sistema. Se habla con los usuarios, se relevan necesidades, se definen los requisitos funcionales (qué hace) y no funcionales (cómo lo hace: rendimiento, seguridad, usabilidad). Es la fase donde "entender bien el problema" evita pagar caro después.
- **Diseño (design):** Se define la arquitectura del sistema, la estructura de los módulos, la base de datos, las interfaces y las tecnologías. Acá se decide "cómo" se va a construir lo que se definió en el análisis.
- **Codificación (coding / implementation):** Se escribe el código fuente de los componentes, siguiendo el diseño. Es la fase que más conocemos, pero es solo una parte del todo.
- **Pruebas (testing):** Se ejecuta el sistema para verificar que cumple los requisitos y detectar errores. Incluye pruebas unitarias, de integración, de sistema y de aceptación con el usuario.
- **Despliegue (deployment):** El sistema se instala y se pone en funcionamiento en el entorno real de producción, donde los usuarios lo van a usar todos los días.
- **Mantenimiento (maintenance):** Después de la puesta en marcha, el software se corrige (errores), se adapta (cambios en el entorno) y se mejora (nuevas funcionalidades). En la práctica, es la fase que consume más tiempo y dinero en la vida de un sistema.

### Modelo en cascada (waterfall)

El modelo en cascada es el más antiguo y clásico. Propone que las fases se ejecuten **de manera secuencial y ordenada**, una detrás de otra, como el agua que cae por una escalera: recién se empieza la fase siguiente cuando termina la anterior. Se espera que cada fase entregue un producto completo y bien documentado (documento de requisitos, diseño, código, etc.) antes de pasar a la siguiente.

**¿Cuándo conviene?** Cuando los requisitos son claros, estables y poco probables de cambiar, y cuando el proyecto es de baja incertidumbre. Suele usarse en sistemas donde el costo de equivocarse en una fase temprana es muy alto y se necesita mucha documentación formal (por ejemplo, sistemas críticos con requisitos contractuales muy definidos).

**Fortalezas:** Es simple de entender y de administrar; cada fase tiene entregables claros; es fácil de planificar, presupuestar y dar seguimiento porque el avance es lineal y medible.

**Debilidades:** Es muy rígido. Si se descubre un error en la fase de análisis recién en las pruebas, volver atrás es costosísimo. El cliente no ve resultados funcionales hasta el final, lo que genera un riesgo alto de "entregar algo que nadie quiere". No tolera bien los cambios de requisitos a mitad de camino.

#### Variante: cascada con retroalimentación (waterfall with feedback)

Una mejora del modelo puro permite **retroalimentación** entre fases: si en las pruebas se descubre un problema, se puede "volver" a la fase de codificación o diseño para corregirlo, en lugar de considerarlo un fracaso fatal. Sigue siendo fundamentalmente secuencial, pero admite saltos hacia atrás entre fases contiguas. Esto lo hace un poco más realista que la cascada pura, aunque sigue sin ser ágil frente a cambios grandes.

### Modelo iterativo e incremental

Este modelo construye el software **por partes y en repetidas pasadas**. Se divide el sistema en incrementos (porciones funcionales) y se trabaja en ciclos o iteraciones: en cada iteración se pasa por análisis, diseño, codificación y pruebas, pero de una porción pequeña, que se entrega funcionando. Con cada iteración, el sistema crece y se va puliendo.

La diferencia entre "iterativo" e "incremental" es sutil: **incremental** significa entregar el sistema por partes que se suman (funcionalidad creciente), mientras que **iterativo** significa repetir el ciclo completo para ir refinando y mejorando el producto. En la práctica suelen combinarse: se itera sobre lo ya construido y se incrementa con nuevas funcionalidades.

**¿Cuándo conviene?** Cuando los requisitos no están del todo claros al inicio, cuando el proyecto es grande y conviene entregar valor pronto, o cuando el cliente quiere ver resultados parciales. Es la base conceptual de muchas metodologías modernas.

**Fortalezas:** Permite entregar funcionalidad usable desde etapas tempranas; se reduce el riesgo porque los problemas se detectan en cada iteración; el usuario da retroalimentación temprana que mejora el producto final.

**Debilidades:** Requiere de una buena planificación para dividir el sistema en incrementos coherentes; el costo total puede ser mayor que en cascada si se rediseña mucho; si no se gestiona bien, la arquitectura puede "deformarse" iteración a iteración sin una visión global clara.

### Modelo en espiral (Boehm)

Propuesto por Barry Boehm, el modelo en espiral es una representación **cíclica** del proceso, que se dibuja como una espiral que crece en vueltas. Cada vuelta recorre cuatro regiones: definir objetivos y alternativas, evaluar alternativas identificando y **resolviendo riesgos**, desarrollar y verificar el producto, y planificar la siguiente iteración. En cada vuelta se trabaja con un conjunto reducido de objetivos y se profundiza cada vez más.

Su rasgo distintivo es el **manejo explícito del riesgo (risk)**: antes de avanzar, se analiza qué puede salir mal (requisitos cambiantes, tecnología inmadura, tiempos) y se diseña una estrategia para mitigarlo. Si el riesgo es muy alto, se decide no avanzar hasta resolverlo.

**¿Cuándo conviene?** En proyectos grandes, complejos, de alto riesgo y larga duración, donde el costo de fallar es elevado y conviene revisar el riesgo en cada vuelta antes de comprometer más recursos.

**Fortalezas:** El manejo del riesgo es su gran aporte; permite incorporar la retroalimentación del cliente y refinar requisitos; combina lo mejor de la construcción por prototipos y del desarrollo evolutivo.

**Debilidades:** Es complejo de administrar y explicar al cliente; requiere de experiencia en identificación y evaluación de riesgos; puede resultar difícil de presupuestar y fijar plazos porque el número de vueltas no se conoce de antemano.

### Modelo en V (verificación y validación)

El modelo en V es una evolución del cascada que **relaciona cada fase de desarrollo con su fase de prueba correspondiente**, formando una letra "V". El lado izquierdo baja por las etapas de definición (requisitos, diseño, codificación); el lado derecho sube por las etapas de prueba (pruebas de integración, de sistema, de aceptación). Cada fase de la izquierda "se verifica" contra una fase de prueba de la derecha en el mismo nivel.

**Verificación** responde a "¿estamos construyendo el producto correctamente?" (el software cumple las especificaciones). **Validación** responde a "¿estamos construyendo el producto correcto?" (el software satisface las necesidades reales del usuario). El modelo en V hace explícito que las pruebas deben planificarse desde el inicio, en paralelo con el desarrollo.

**¿Cuándo conviene?** En sistemas donde la calidad y la trazabilidad entre requisitos y pruebas son críticas, como software de misión crítica, sistemas embebidos, aeroespaciales o médicos, donde cada requisito debe demostrar que se cumplió.

**Fortalezas:** Promueve la calidad desde el inicio, con pruebas diseñadas temprano; mejora la trazabilidad requisito-prueba; reduce defectos que llegarían tarde si las pruebas fueran solo al final.

**Debilidades:** Comparte la rigidez del cascada en cuanto a la secuencia; sigue siendo débil frente a cambios de requisitos; puede generar mucho papeleo y formalismo que no siempre es necesario.

### Modelo basado en componentes (component-based)

Este modelo se centra en **reutilizar piezas de software ya existentes** —los componentes— en lugar de construir todo desde cero. El proceso consiste en: identificar candidatos a componentes reutilizables, evaluar y seleccionarlos, adaptarlos si es necesario, ensamblarlos para formar el sistema y probar el ensamblaje completo. El trabajo se orienta más a "componer" que a "escribir".

**¿Cuándo conviene?** Cuando en la organización o en el mercado existen componentes probados que cubren gran parte de la funcionalidad, y cuando el tiempo de entrega es prioritario. Es común en desarrollos que integran librerías, frameworks y servicios ya existentes.

**Fortalezas:** Reduce tiempo y costo de desarrollo al reutilizar código probado; mejora la calidad porque se usan componentes maduros; facilita el mantenimiento y la actualización de piezas individuales.

**Debilidades:** Depende de la calidad y disponibilidad de los componentes externos; puede haber conflictos de licencias o incompatibilidades entre componentes; a veces hay que "adaptarse" a lo que ofrece el componente, sacrificando un diseño ideal.

## Analogía

Imaginemos que queremos construir una casa, y que cada modelo de proceso es una manera distinta de encarar la obra.

**Cascada:** Contratamos un plano cerrado y una secuencia estricta: primero se cava el pozo, después se hacen los cimientos, después las paredes, después el techo, y recién al final se entrega la llave. Si el dueño descubre a mitad de obra que quiere la cocina en otro lado, es un problema enorme porque ya todo está hecho sobre el plano original. Funciona bien si el plano es perfecto y nada cambia.

**Iterativo e incremental:** Empezamos a construir una habitación completa y usable, la entregamos y vivimos en ella; después agregamos otra habitación, después otra. Cada entrega se puede usar de verdad, y si el dueño no le gusta cómo quedó la primera, lo corregimos antes de construir el resto.

**Espiral:** Antes de cada ampliación, nos sentamos y preguntamos "¿qué puede salir mal si construimos este piso?" (que el terreno no aguante, que no alcance el presupuesto). Si el riesgo es alto, diseñamos un plan para resolverlo antes de gastar más. Avanzamos de a vueltas, controlando el peligro en cada una.

**Modelo en V:** Para cada piso que dibujamos en el plano, ya dejamos escrito cómo vamos a comprobar que quedó bien: si el plano dice "este muro soporta X", dejamos anotado el ensayo que lo va a verificar. La verificación acompaña a la construcción desde el inicio.

**Basado en componentes:** En lugar de fabricar cada ladrillo, usamos paredes y ventanas prefabricadas ya probadas, y las ensamblamos. Ahorramos tiempo y confiamos en piezas que ya funcionan en otras obras, aunque tengamos que ajustar el diseño a las medidas que vienen de fábrica.

## Ejemplo práctico

Tomemos como caso un **sistema de gestión ganadera** que debe registrar animales, seguimiento de sanidad, control de peso, trazabilidad y reportes para el dueño del campo.

**Con cascada:** El productor entrega un pedido muy detallado ("necesito el sistema completo con todos los módulos, para una fecha fija, porque hay una inspección sanitaria"). El equipo releva todo, diseña la base de datos completa, programa todos los módulos, prueba y entrega. Funciona si el productor sabe exactamente lo que quiere y no va a cambiar nada. Pero si a mitad de obra pide agregar un módulo de vacunas, el plan se desarma.

**Con iterativo e incremental:** En la primera iteración se entrega solo el registro de animales funcionando (cargar, listar, editar). El productor lo usa y pide ajustes. En la segunda iteración se agrega el módulo de pesaje; en la tercera, sanidad; y así. El productor ve valor desde el primer mes y va corrigiendo sobre lo real, no sobre supuestos.

**Con espiral:** Como es un sistema donde los datos de sanidad son críticos (un error en un registro puede costar una multa o un problema de trazabilidad), el equipo identifica el riesgo principal: "¿y si los datos de vacunas no son exactos?". En cada vuelta se diseña una estrategia para ese riesgo (doble verificación, permisos de usuario) antes de avanzar al siguiente módulo.

**Con modelo en V:** Se exige trazabilidad total: cada requisito (por ejemplo, "todo animal debe tener un número de caravana único") tiene su prueba de aceptación definida desde el inicio. Al final, se demuestra requisito por requisito que el sistema cumple, lo cual es valioso si hay auditorías.

**Con basado en componentes:** En lugar de programar desde cero el envío de correos, la generación de reportes en PDF o la autenticación de usuarios, se reutilizan librerías y servicios ya probados, y el equipo se enfoca en la lógica propia del negocio ganadero. El sistema sale más rápido y con menos errores en las partes "comunes".

## Comparativas

| Modelo | Enfoque | Orden | Cuándo conviene | Fortaleza principal | Debilidad principal |
|:-------|:-------|:------|:----------------|:--------------------|:--------------------|
| Cascada | Secuencial | Fases en línea recta | Requisitos claros y estables | Simple, planificable, entregables claros | Rígido, cambios caros, se ve el resultado al final |
| Cascada con retroalimentación | Secuencial con saltos atrás | Fases contiguas con corrección | Como cascada pero admitiendo revisiones | Más realista que cascada pura | Sigue sin tolerar cambios grandes |
| Iterativo e incremental | Por partes en ciclos | Repetición de ciclos crecientes | Requisitos inciertos, proyectos grandes | Entrega valor temprano, retroalimentación del cliente | Requiere planificar bien los incrementos |
| Espiral (Boehm) | Cíclico con análisis de riesgo | Vueltas que evalúan riesgo | Proyectos grandes y de alto riesgo | Manejo explícito del riesgo | Complejo, difícil de presupuestar |
| Modelo en V | Cascada + verificación/validación | Desarrollo y pruebas espejadas | Sistemas críticos con trazabilidad | Calidad y trazabilidad requisito-prueba | Rígido frente a cambios, mucho formalismo |
| Basado en componentes | Reutilización y ensamblaje | Componer piezas probadas | Reutilizar existentes, entrega rápida | Menos costo y tiempo, componentes probados | Depende de componentes externos |

Otra forma de comparar: la **cascada** optimiza la previsibilidad pero arriesga la utilidad del resultado; el **iterativo e incremental** mejora la adaptación pero exige más gestión; la **espiral** maximiza el control del riesgo pero es compleja; el **modelo en V** privilegia la calidad y verificación; el **basado en componentes** prioriza la velocidad y la reutilización. No hay un "mejor modelo" en abstracto: hay un modelo más adecuado para cada contexto.

## Fuentes

### Pressman, "Ingeniería de Software, un enfoque práctico" (5ta edición)

PDF gratuito (licencia CC0) en Archive.org, ideal para los capítulos de modelos de proceso.

https://archive.org/details/ingenieria-del-software-5ta-edicion-roger-s.-pressman

### Manifiesto Ágil (versión en español)

Documento oficial donde se definen los valores y principios del desarrollo ágil.

https://agilemanifesto.org/iso/es/manifesto.html

## Para practicar

1. Tomá un proyecto que conozcas (una aplicación de tu teléfono o un sistema de tu facultad). Identificá en qué fase del ciclo de vida creés que está ahora mismo y justificá tu respuesta.

2. Compará la cascada con el modelo iterativo e incremental para un sistema de gestión ganadera. ¿En qué circunstancias elegirías cada uno? ¿Qué le dirías a un productor que quiere "todo listo en una fecha fija"?

3. Explicá con tus palabras la diferencia entre verificación y validación, usando el modelo en V y un ejemplo de trazabilidad en un sistema de sanidad animal.

4. Pensá en los riesgos de un sistema de gestión ganadera y aplicá el modelo en espiral: identificá un riesgo concreto y proponé una estrategia para mitigarlo antes de avanzar al siguiente módulo.

5. Investigá en el Manifiesto Ágil (fuente del material) y respondé: ¿qué principios del manifiesto se relacionan con el modelo iterativo e incremental? ¿Y cuáles chocarían con el modelo en cascada?
