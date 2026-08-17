# Procesos y modelos adaptativos

## Introducción

Cuando hablamos de construir software, una de las primeras preguntas que surge es: ¿podemos saber de antemano todo lo que el cliente va a necesitar? La respuesta honesta, después de décadas de experiencia en la industria, es casi siempre NO. Los requisitos cambian, los usuarios descubren qué quieren recién cuando ven algo funcionando, y el contexto del negocio se modifica mientras desarrollamos.

Durante mucho tiempo la industria intentó resolver este problema fingiendo que los requisitos eran estables: se definía todo por adelantado, se documentaba hasta el último detalle y recién después se construía. A ese enfoque lo llamamos modelo predictivo. Pero cuando el proyecto no salía como el plano, la culpa no era del software, sino de la idea de que se podía predecir todo.

Los procesos y modelos adaptativos nacen de aceptar la incertidumbre como parte natural del desarrollo. En lugar de luchar contra el cambio, lo abrazan: se planifica en ciclos cortos, se construye un poco, se observa el resultado, se aprende y se ajusta. Es la base de lo que hoy conocemos como metodologías ágiles, y de este tema dependerá entender por qué el software profesional moderno se desarrolla así.

## Conceptos clave

### La necesidad de adaptarse a requisitos cambiantes

El software no es como construir un puente, donde el terreno y las cargas se pueden medir con precisión antes de empezar. El software es un producto que vive, que se usa, y cuyo valor depende de que siga siendo útil. Un requisito es una necesidad que el sistema debe satisfacer. Esa necesidad puede cambiar porque el negocio cambió, porque apareció una nueva ley, porque la competencia lanzó una función nueva o simplemente porque el usuario, al ver la primera versión, se dio cuenta de que lo que pidió no era lo que realmente quería. Adaptarse no es un lujo: es una condición de supervivencia del proyecto.

### Modelo predictivo

Un modelo predictivo (predictive model) supone que podemos conocer, planificar y estimar el trabajo completo de antemano. Funciona bien cuando el problema está bien entendido, los requisitos son estables y el riesgo técnico es bajo. Su gran limitación: si el contexto cambia, el plan queda desactualizado y el costo de corregirlo es alto, porque todo se renegoció sobre un esquema rígido.

### Modelo adaptativo (o empírico)

Un modelo adaptativo (adaptive model) parte de la premisa contraria: no podemos conocer todo por adelantado, así que aprendemos mientras avanzamos. Se trabaja en ciclos cortos donde se construye una porción funcional, se la entrega o prueba, se recoge información del resultado real y se ajusta el plan para el siguiente ciclo. Cada iteración es una oportunidad de corrección. A este enfoque también se lo llama modelo empírico, porque se basa en la experiencia y la observación, no en la predicción.

### Desarrollo iterativo e incremental

Es la base operativa de la adaptación. Dos ideas que van juntas:

- Iterativo (iterative): el trabajo se repite en ciclos (iteraciones). Al final de cada ciclo se revisa el resultado y se ajusta el rumbo. No se hace todo "de una sola pasada".
- Incremental (incremental): cada ciclo agrega una parte nueva y útil del producto. No se construye todo para entregarlo al final, sino que el sistema crece por porciones que ya funcionan.

La diferencia es sutil pero importante: iterativo habla de repetir y ajustar; incremental habla de ir sumando funcionalidad. Juntos, permiten que el software se adapte: si algo no funciona o no es lo que el cliente quiere, lo notamos en el próximo ciclo, no al final del proyecto.

### Manifiesto Ágil (2001)

En febrero de 2001, diecisiete referentes del desarrollo de software se reunieron y redactaron el Manifiesto Ágil, un documento breve que sintetiza una forma distinta de trabajar. Surge como reacción directa al exceso de formalismo y de documentación burocrática de los métodos tradicionales basados en la cascada, donde el proceso pesaba más que el resultado.

El Manifiesto propone cuatro valores:

1. Valoramos a los individuos y sus interacciones por sobre los procesos y las herramientas.
2. Valoramos el software funcionando por sobre la documentación exhaustiva.
3. Valoramos la colaboración con el cliente por sobre la negociación contractual.
4. Valoramos la respuesta ante el cambio por sobre seguir un plan rígido.

La clave está en leerlos bien: no se dice que las herramientas, la documentación o el plan sean inútiles. Se dice que tienen menor valor que las personas, el software funcionando, la colaboración y la capacidad de cambiar. Cuando hay conflicto, se prioriza lo primero de cada frase.

### Los 12 principios ágiles

Junto a los cuatro valores, el Manifiesto incluye doce principios que explican cómo llevar esos valores a la práctica. Explicados de forma simple:

1. Nuestra mayor prioridad es satisfacer al cliente mediante entregas tempranas y continuas de software con valor. Se entrega pronto y seguido, no esperando al final.
2. Aceptamos los cambios en los requisitos, incluso en etapas tardías. Los procesos ágiles aprovechan el cambio para dar ventaja competitiva al cliente.
3. Entregamos software funcionando con frecuencia, en períodos cortos. Preferimos varias entregas chicas a una sola enorme.
4. Personas de negocio y desarrolladores trabajan juntos a diario durante todo el proyecto. No cada tres meses en una reunión formal.
5. Construimos proyectos alrededor de personas motivadas, confiando en que hagan bien su trabajo. Menos control burocrático y más confianza.
6. La conversación cara a cara es el método más eficiente y efectivo de transmitir información. Documentar es útil, pero hablar es mejor.
7. El software funcionando es la principal medida de progreso. Avanzamos cuando hay software que funciona, no cuando hay papeles firmados.
8. Los procesos ágiles promueven el desarrollo sostenible: se debe poder mantener un ritmo constante de forma indefinida. Nada de "maratones" insostenibles.
9. La atención continua a la excelencia técnica y al buen diseño mejora la agilidad. Lo que se hace rápido y mal, después sale caro.
10. La simplicidad es esencial: hacer la máxima cantidad de trabajo sin hacerlo innecesario. Solo lo que aporta valor.
11. Las mejores arquitecturas, requisitos y diseños surgen de equipos que se autoorganizan. Las decisiones las toma el equipo, no un jefe lejano.
12. El equipo reflexiona sobre cómo ser más efectivo y ajusta su comportamiento. Al final de cada ciclo se mira atrás y se mejora.

### Empirismo e inspección y adaptación

El empirismo (empiricism) sostiene que el conocimiento proviene de la experiencia y de tomar decisiones en base a lo observado, no en base a teorías o predicciones. En el desarrollo de software se traduce en tres pilares que se aplican en cada ciclo:

- Transparencia: todos los involucrados deben poder ver el estado real del trabajo. No se esconden problemas.
- Inspección (inspect): se revisa con frecuencia el producto y el proceso para detectar desviaciones. "Inspeccionar" es observar el resultado real.
- Adaptación (adapt): si la inspección revela un problema, se ajusta el proceso o el producto de inmediato. Inspeccionar sin adaptar no sirve de nada.

La idea "inspeccionar y adaptar" (inspect and adapt) es el motor de los métodos ágiles: cada ciclo corto es una oportunidad de mirar qué salió bien, qué salió mal y corregir el rumbo antes de que sea tarde. Esto solo funciona si los ciclos son cortos; si el proyecto entero es un solo ciclo, nunca hay oportunidad de adaptarse a tiempo.

### Contexto: la reacción a la cascada

Los modelos ágiles no nacieron en el vacío. Surgieron como reacción al modelo en cascada (waterfall), donde el proyecto avanzaba en fases lineales (requisitos, diseño, desarrollo, pruebas, despliegue) y no se podía volver atrás sin grandes costos. La cascada producía proyectos que se entregaban tarde, con funciones que ya no servían y con mucha documentación pero poco software funcionando. Los métodos ágiles, inspirados por las prácticas de desarrollo iterativo de décadas anteriores, propusieron lo opuesto: ciclos cortos, colaboración cercana con el cliente y aceptación del cambio como norma.

## Analogía

Pensá en cocinar para una cena, pero con invitados que todavía no saben exactamente qué quieren comer.

El enfoque predictivo sería escribir el menú completo con cinco días de anticipación, comprar todos los ingredientes según ese menú, y negarte a cambiar nada porque "ya está todo planificado". Si un invitado llega y dice "en realidad prefiero algo más liviano", te quedaste con ingredientes que ya compraste y un plan que no se puede tocar. Seguís adelante con el menú original aunque nadie lo quiera, porque cambiarlo es demasiado caro.

El enfoque adaptativo sería hacer una primera tanda simple de platos, probarla con los invitados, preguntar qué les pareció, y recién entonces decidir la siguiente tanda teniendo en cuenta lo que te dijeron. Cocina un poco, sirve un poco, observa qué se comió y qué no, y ajusta. No sabés el menú final desde el día uno, pero sabés que siempre vas a estar cocinando algo que los invitados sí quieren comer.

El software adaptativo funciona igual: construís un poco, lo mostrás, aprendés de la reacción real y ajustás. Cada ciclo corto es como esa pregunta "¿te gustó? ¿qué cambio harías?" que te permite cocinar mejor la próxima ronda.

## Ejemplo práctico

Supongamos que un cliente pide un sistema para gestionar turnos en una peluquería. Con un enfoque predictivo, el equipo pediría una lista exhaustiva de todos los requisitos (clientes, turnos, pagos, recordatorios, reportes, etc.), documentaría todo, y se pondría a construir durante seis meses. Recién al final le mostraría al cliente el sistema terminado. Si el cliente en el camino descubre que lo que realmente necesita es poder vender productos además de reservar turnos, el equipo tendría que volver a negociar todo desde cero: demasiado tarde, demasiado caro.

Con un enfoque adaptativo (por ejemplo, con ciclos de dos semanas), el equipo comienza por lo más esencial: el calendario para reservar turnos. A las dos semanas, el cliente ya tiene algo funcionando y lo prueba con sus empleados. Surgen problemas reales que el cliente no había anticipado (por ejemplo, la necesidad de bloquear horarios de almuerzo), y el equipo los incorpora en el siguiente ciclo. En cada iteración se agrega una porción nueva: la agenda de clientes, luego el recordatorio por mensaje, luego el cobro. Al final del proyecto, el software no es exactamente lo que se pidió al principio, pero es exactamente lo que el cliente necesita, porque se fue construyendo y ajustando en base a lo que realmente se observaba.

## Comparativas

| Aspecto | Modelo predictivo | Modelo adaptativo (empírico) |
|:--------|:------------------|:-----------------------------|
| Supuesto base | Los requisitos se pueden conocer y definir por adelantado | Los requisitos se descubren y cambian mientras se desarrolla |
| Planificación | Se planifica todo al inicio, en detalle | Se planifica por ciclos cortos, con plan flexible |
| Ciclo de trabajo | Una sola pasada en fases lineales | Iterativo e incremental: ciclos cortos que se repiten |
| Toma de decisiones | Basada en el plan y la predicción | Basada en la observación del resultado real (empirismo) |
| Manejo del cambio | Difícil y costoso; se resiste | Esperado y bienvenido; se integra en cada ciclo |
| Retroalimentación | Escasa; se revisa al final del proyecto | Constante; al final de cada iteración |
| Documentación | Extensa y formal, se produce antes de construir | Justa y necesaria, prioriza software funcionando |
| Relación con el cliente | Se negocia por contrato, contacto puntual | Colaboración continua y cercana |
| Momento de ver valor | Al final, cuando se entrega todo | Temprano, desde las primeras iteraciones |
| Riesgo | Alto: un error se descubre tarde y es caro | Bajo: los errores se corrigen en cada ciclo |
| Ideal para | Problemas bien entendidos y estables | Problemas con incertidumbre y requisitos cambiantes |

## Fuentes

### Manifiesto Ágil (español)

URL oficial del Manifiesto Ágil en español, donde se encuentran los cuatro valores y los doce principios. Es la fuente primaria de este tema y conviene leerla directamente en su versión original.

https://agilemanifesto.org/iso/es/manifesto.html

### Scrum Guide (inglés oficial)

La guía oficial de Scrum, el marco de trabajo ágil más usado, publicada por Ken Schwaber y Jeff Sutherland. Profundiza en los conceptos de empirismo, inspección y adaptación, y en los pilares de transparencia, inspección y adaptación que se mencionaron en este material.

https://scrumguides.org

## Para practicar

1. Explicá con tus palabras la diferencia entre un modelo predictivo y un modelo adaptativo. Usá un ejemplo que no sea de software (por ejemplo, organizar un viaje o armar una dieta).
2. ¿Por qué el desarrollo iterativo e incremental es el "motor" que permite la adaptación? ¿Qué pasaría si fuera iterativo pero no incremental, o al revés?
3. Redactá los cuatro valores del Manifiesto Ágil y explicá en una línea, para cada uno, qué es lo que NO se está negando (qué cosa de la segunda parte sigue siendo válida, aunque con menor prioridad).
4. Elegí tres de los doce principios del Manifiesto y explicá con un ejemplo concreto cómo se aplicarían en un proyecto de desarrollo de software real.
5. Definí los tres pilares del empirismo (transparencia, inspección, adaptación) y contá una situación en la que "inspeccionar sin adaptar" sería un error.
6. Investigá en el Scrum Guide (https://scrumguides.org) qué relación tienen los tres pilares del empirismo con los eventos de Scrum (como el Sprint Review o la Retrospectiva). Resumí lo que encontraste.
7. Debate argumentado: ¿existe algún tipo de proyecto donde un modelo predictivo siga siendo más adecuado que uno adaptativo? Justificá tu respuesta con las características del problema.

Para ampliar: leé el Manifiesto Ágil en su versión original en español (https://agilemanifesto.org/iso/es/manifesto.html) y prestá atención a cómo la frase de cada valor deja lugar a la parte que se desprioriza.
