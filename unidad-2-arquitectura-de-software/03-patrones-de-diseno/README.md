# Patrones de diseño

## Introducción

Imaginá que estás aprendiendo a cocinar. No necesitás inventar cada plato desde cero: existen recetas que ya probaron miles de personas, que sabés que funcionan y que podés adaptar a tu cocina. Los patrones de diseño en software funcionan igual: son recetas probadas para resolver problemas que aparecen una y otra vez en el desarrollo de aplicaciones.

Cuando empecés a trabajar en sistemas reales —como un sistema de gestión ganadera— vas a notar que muchos problemas ya tienen solución conocida. Los patrones de diseño son exactamente eso: soluciones reutilizables y probadas a problemas recurrentes en un contexto dado. No son código copiado y pegado, sino una plantilla conceptual que vos adaptás a tu situación particular.

Este material te va a servir para entender qué son los patrones, cuáles son los más usados según el famoso libro "Design Patterns" (conocido como el libro GoF, por las iniciales de sus autores: Gamma, Helm, Johnson y Vlissides), y cómo distinguir las tres grandes familias que existen: creacionales, estructurales y de comportamiento.

## Conceptos clave

### Qué es un patrón de diseño (design pattern)

Un patrón de diseño es una **solución general, reutilizable y probada a un problema recurrente** que aparece dentro de un contexto específico. Cuatro características lo definen:

- **Nombre**: un identificador que permite comunicarse (por ejemplo, "Singleton").
- **Problema**: cuándo aplicarlo, qué condiciones lo disparan.
- **Solución**: la estructura de clases y objetos que lo resuelven (no código exacto, sino un esquema).
- **Consecuencias**: qué ganás y qué perdés al aplicarlo (trade-offs).

Un patrón **no es** una librería ni un fragmento de código listo para copiar. Es un esquema mental que vos implementás según tu lenguaje y tu necesidad.

El libro GoF ("Design Patterns: Elements of Reusable Object-Oriented Software", 1994) clasificó los patrones en tres familias según su propósito:

- **Creacionales (creational)**: se ocupan de **cómo se crean los objetos**.
- **Estructurales (structural)**: se ocupan de **cómo se componen las clases y los objetos**.
- **De comportamiento (behavioral)**: se ocupan de **cómo se comunican y reparten responsabilidades** los objetos.

### Principio: separar "qué varía" y "programar a interfaz, no a implementación"

Antes de ver los patrones, hay que entender dos principios que los atraviesan a todos.

**Separar lo que varía (encapsular la variación)**: en cualquier sistema hay partes que cambian y partes que se mantienen estables. El arte está en aislar lo que cambia para que, cuando haya que modificarlo, no tengamos que tocar todo el programa. Por ejemplo, si hoy el sistema ganadero calcula el peso de un animal con una fórmula y mañana con otra, esa fórmula tiene que vivir en un lugar aparte, no pegada en cada pantalla.

**Programar a interfaz, no a implementación**: en lugar de depender de una clase concreta (por ejemplo, `ToroConcreto`), dependemos de una abstracción (una interfaz `Animal`). Así, si mañana cambia la implementación, el resto del código no se entera. Es como enchufar un cargador USB-C: el teléfono no sabe si está conectado a la pared, a la compu o a una batería; solo sabe que hay una "interfaz" que le da energía.

### Patrones creacionales (creational)

Se centran en la creación de objetos. Su objetivo es que el código no dependa de cómo y cuándo se crean las instancias.

#### Singleton

**Propósito**: garantizar que una clase tenga **una única instancia** en todo el programa y ofrecer un punto de acceso global a ella.

**Cuándo usarlo**: cuando necesitás exactamente un objeto compartido, como una conexión a base de datos, un registro de logs o una configuración global del sistema ganadero.

**Código conceptual** (pseudocódigo):

```
clase ConexionBaseDatos
    instancia_unica = null

    metodo privado constructor()
        # configuro la conexión
    fin

    metodo estatico obtenerInstancia()
        si instancia_unica es null:
            instancia_unica = nueva ConexionBaseDatos()
        fin
        retornar instancia_unica
    fin
fin

conexion1 = ConexionBaseDatos.obtenerInstancia()
conexion2 = ConexionBaseDatos.obtenerInstancia()
# conexion1 y conexion2 son el MISMO objeto
```

**Ojo**: su uso excesivo se considera un anti-patrón, porque introduce estado global. Hay que usarlo con moderación.

#### Factory Method (Método de Fábrica)

**Propósito**: definir una interfaz para crear un objeto, pero **dejar que las subclases decidan qué clase concreta instanciar**.

**Cuándo usarlo**: cuando no sabés de antemano qué tipo de objeto vas a necesitar, o cuando querés que el código que crea quede separado del que usa.

**Código conceptual**:

```
interfaz Animal
    metodo obtenerPeso() -> numero
fin

clase Vaca implementa Animal
    metodo obtenerPeso() -> 450
fin

clase Toro implementa Animal
    metodo obtenerPeso() -> 850
fin

clase FabricaAnimales
    metodo crearAnimal(tipo)
        si tipo == "vaca": retornar nueva Vaca()
        si tipo == "toro": retornar nueva Toro()
    fin
fin
```

Acá la fábrica decide qué animal crear según el tipo, y el resto del sistema solo conoce la interfaz `Animal`.

#### Abstract Factory (Fábrica Abstracta)

**Propósito**: crear **familias de objetos relacionados** sin especificar sus clases concretas. Es un paso más allá del Factory Method: en vez de crear un objeto, crea un conjunto de objetos que funcionan juntos.

**Cuándo usarlo**: cuando tu sistema tiene varias familias de productos que deben usarse en conjunto. Por ejemplo, distintas razas bovinas, donde cada raza trae su propia forma de calcular alimentación, sanidad y reproducción.

**Código conceptual**:

```
interfaz FabricaGanado
    metodo crearAnimal() -> Animal
    metodo crearAlimento() -> Alimento
fin

clase FabricaBovinos implementa FabricaGanado
    metodo crearAnimal() -> nueva Vaca()
    metodo crearAlimento() -> nueva RacionBovino()
fin

clase FabricaOvinos implementa FabricaGanado
    metodo crearAnimal() -> nueva Oveja()
    metodo crearAlimento() -> nueva PasturaOvino()
fin
```

El código que usa la fábrica nunca sabe si está trabajando con bovinos u ovinos; simplemente pide "dame un animal y su alimento" y recibe una familia coherente.

### Patrones estructurales (structural)

Se ocupan de **cómo se combinan clases y objetos** para formar estructuras más grandes, sin romper su independencia.

#### Adapter (Adaptador)

**Propósito**: permitir que dos clases con interfaces incompatibles trabajen juntas, actuando como un traductor.

**Cuándo usarlo**: cuando tenés un componente viejo o de terceros que no encaja con el sistema nuevo y no podés (o no querés) modificarlo.

**Código conceptual**:

```
interfaz LecturaPeso
    metodo leerPeso() -> numero
fin

# Componente viejo que habla "kilos"
clase BalanzaVieja
    metodo obtenerKilos() -> 500
fin

clase AdaptadorBalanza implementa LecturaPeso
    balanza = nueva BalanzaVieja()

    metodo leerPeso()
        retornar self.balanza.obtenerKilos()  # adapto la interfaz
    fin
fin
```

Es el típico caso del adaptador de enchufe: viajás a otro país, el enchufe no entra en la pared, y un adaptador hace que conectes tu equipo igual.

#### Facade (Fachada)

**Propósito**: ofrecer una **interfaz simple** hacia un subsistema complejo de clases.

**Cuándo usarlo**: cuando hay un sistema con muchas partes y querés esconder su complejidad detrás de una sola puerta de entrada.

**Código conceptual**:

```
clase FachadaSistemaGanadero
    registrar = nueva RegistroAnimales()
    sanidad = nueva ControlSanitario()
    ventas = nueva GestorVentas()

    metodo operacionDiaria(animal)
        self.registrar.actualizar(animal)
        self.sanidad.verificar(animal)
        self.ventas.cotizar(animal)
    fin
fin
```

El resto del programa llama a un solo método (`operacionDiaria`) en lugar de coordinar tres clases internas. Es como el mostrador de un banco: vos no conocés todo el sistema interno del banco, solo hablás con un empleado que hace todo por vos.

#### Decorator (Decorador)

**Propósito**: **agregar responsabilidades a un objeto dinámicamente**, sin modificar su clase ni usar herencia.

**Cuándo usarlo**: cuando tenés combinaciones de funcionalidades opcionales y la herencia generaría una explosión de clases.

**Código conceptual**:

```
interfaz Animal
    metodo descripcion() -> texto
fin

clase Vaca implementa Animal
    metodo descripcion() -> "Vaca"
fin

clase AnimalDecorado implementa Animal
    animal = null

    metodo AnimalDecorado(animal) -> self.animal = animal
    metodo descripcion() -> self.animal.descripcion()
fin

clase ConChipDecorado hereda AnimalDecorado
    metodo descripcion() -> self.animal.descripcion() + " con chip"
fin

vaca = nueva VacaConChip(nueva Vaca())
# descripcion() devuelve "Vaca con chip"
```

Podés ir "enrollando" decoradores como capas de una cebolla: base, con chip, con vacuna, con pedigree... sin tocar la clase `Vaca`.

### Patrones de comportamiento (behavioral)

Se ocupan de **la comunicación y distribución de responsabilidades** entre objetos.

#### Observer (Observador)

**Propósito**: definir una **dependencia de uno a muchos**, de modo que cuando un objeto cambia, todos sus dependientes sean notificados y actualizados automáticamente.

**Cuándo usarlo**: cuando un cambio en un objeto debe reflejarse en varios otros sin acoplarlos entre sí.

**Código conceptual**:

```
interfaz Observador
    metodo notificar(evento)
fin

clase AlertaSanitaria implementa Observador
    metodo notificar(evento)
        # dispara alerta si evento == "fiebre"
    fin
fin

clase Animal
    observadores = []

    metodo agregarObservador(o) -> observadores.agregar(o)
    metodo cambiarTemperatura(valor)
        por cada obs en observadores:
            obs.notificar("temperatura=" + valor)
    fin
fin
```

Es como la red de grupos de WhatsApp: cuando el dueño publica un cambio, todos los que están en el grupo se enteran al instante, sin que el dueño tenga que avisar a cada uno por separado.

#### Strategy (Estrategia)

**Propósito**: definir una familia de algoritmos, **encapsular cada uno** y hacerlos intercambiables en tiempo de ejecución.

**Cuándo usarlo**: cuando tenés varias formas de hacer lo mismo y querés elegir cuál usar sin llenar el código de condicionales.

**Código conceptual**:

```
interfaz EstrategiaPesaje
    metodo calcular(animal) -> numero
fin

clase PesajePorFormula implementa EstrategiaPesaje
    metodo calcular(animal) -> animal.alto * 0.5
fin

clase PesajePorBalanza implementa EstrategiaPesaje
    metodo calcular(animal) -> animal.pesoMedido
fin

clase SistemaPesaje
    estrategia = null
    metodo setEstrategia(e) -> self.estrategia = e
    metodo calcular(animal) -> self.estrategia.calcular(animal)
fin
```

El sistema puede cambiar de estrategia en pleno funcionamiento: hoy se pesa con balanza, mañana por fórmula, sin reescribir nada.

#### Command (Comando)

**Propósito**: **encapsular una petición como un objeto**, permitiendo parametrizar, encolar, registrar y deshacer operaciones.

**Cuándo usarlo**: cuando querés que las acciones sean reversibles (deshacer) o se puedan encolar/agendar.

**Código conceptual**:

```
interfaz Comando
    metodo ejecutar()
    metodo deshacer()
fin

clase ComandoVacunar implementa Comando
    animal = null

    metodo ejecutar() -> self.animal.aplicarVacuna()
    metodo deshacer() -> self.animal.retirarVacuna()
fin

clase BotonAccion
    comando = null

    metodo setComando(c) -> self.comando = c
    metodo presionar() -> self.comando.ejecutar()
fin
```

Es como el control remoto del televisor: cada botón es un comando que puede ejecutarse, programarse o deshacerse, sin que el control sepa qué hay del otro lado.

### Introducción a los principios SOLID

SOLID es un acrónimo de cinco principios de diseño que te ayudan a escribir código más mantenible. Se los menciona porque muchos patrones de diseño existen justamente para cumplir estos principios.

- **S — Single Responsibility (Responsabilidad Única)**: cada clase debe tener una única razón para cambiar. Un `Animal` no debería encargarse también de imprimir reportes.
- **O — Open/Closed (Abierto/Cerrado)**: el código debe estar abierto a extensión pero cerrado a modificación. Se agregan funciones nuevas sin tocar el código existente (ahí entran patrones como Decorator o Strategy).
- **L — Liskov Substitution (Sustitución de Liskov)**: las subclases deben poder reemplazar a sus clases base sin romper el programa. Si usás `Vaca` donde se espera `Animal`, todo debe seguir funcionando.
- **I — Interface Segregation (Segregación de Interfaz)**: es mejor tener varias interfaces chicas y específicas que una grande y genérica. No obligues a una clase a implementar métodos que no usa.
- **D — Dependency Inversion (Inversión de Dependencias)**: hay que depender de abstracciones, no de clases concretas. Esto se conecta directamente con "programar a interfaz, no a implementación".

## Analogía

Pensá en una **constructor** que arma una casa. Un patrón de diseño es como un **plano de referencia aprobado**: no es la casa exacta que vas a construir, pero te dice cómo resolver el problema de "que las paredes aguanten el techo" sin reinventar la rueda cada vez.

- Los patrones **creacionales** son como las fábricas de materiales: te dan el ladrillo, el cemento y el vidrio ya preparados, según la obra.
- Los patrones **estructurales** son como los andamios y las conexiones: cómo se unen las vigas, cómo se adapta una puerta de otra medida.
- Los patrones de **comportamiento** son como el protocolo entre los albañiles: quién avisa a quién, qué plan de trabajo se elige, qué orden de tareas se ejecuta.

O, en términos de cocina: los creacionales son las recetas de masa, los estructurales son las formas de armar el plato y los de comportamiento son las órdenes de la brigada en una cocina profesional ("fuego", "mise en place", "a la plancha").

## Ejemplo práctico

Vamos a aplicar los patrones a un **sistema de gestión ganadera** para que veas cómo conviven todos juntos.

- **Singleton**: la conexión a la base de datos del establecimiento. Todas las pantallas comparten la misma conexión, nunca se abre una por cada operación.
- **Factory Method**: la fábrica que crea el animal según su tipo (`vaca`, `toro`, `ternero`) según los datos que ingresa el usuario.
- **Abstract Factory**: al elegir una raza (Angus, Hereford, Brahman), el sistema crea una familia completa: fórmula de alimento + calendario sanitario + tabla de reproducción, todas coherentes entre sí.
- **Adapter**: la balanza digital vieja que entrega datos en otra unidad de medida. Un adaptador la convierte para que el sistema nuevo la entienda sin tocar la balanza.
- **Facade**: el módulo "operación diaria" que detrás coordina registro, sanidad y ventas, y le presenta al veterinario una sola pantalla simple.
- **Decorator**: al animal base le vas agregando capas dinámicas: con chip, con vacuna, con certificado de pedigree. Cada capa se agrega sin modificar la clase `Animal`.
- **Observer**: cuando un animal registra fiebre, todos los módulos suscriptos (sanidad, nutrición, reportes) se notifican automáticamente.
- **Strategy**: el cálculo de peso puede usar balanza, fórmula por medidas o estimación por edad; el sistema elige la estrategia según el contexto.
- **Command**: la acción "vacunar" queda encapsulada como comando, permitiendo encolarla para el turno de la tarde y deshacerla si el veterinario se equivoca.

## Comparativas

### Creacionales vs Estructurales vs Comportamiento

| Familia | Pregunta que responde | Patrones | Analogía |
|:--------|:----------------------|:---------|:---------|
| Creacionales | ¿Cómo se crean los objetos? | Singleton, Factory Method, Abstract Factory | La fábrica que produce materiales |
| Estructurales | ¿Cómo se componen las clases y objetos? | Adapter, Facade, Decorator | Los andamios y conexiones |
| Comportamiento | ¿Cómo se comunican y reparten tareas? | Observer, Strategy, Command | El protocolo entre trabajadores |

### Cuándo usar Singleton vs Factory Method

| Aspecto | Singleton | Factory Method |
|:--------|:----------|:---------------|
| Objetivo | Garantizar una única instancia | Crear objetos sin conocer su clase concreta |
| Cantidad de objetos | Uno solo, compartido | Muchos, de distintos tipos |
| Ejemplo típico | Conexión a base de datos | Crear `Vaca` o `Toro` según el tipo |
| Riesgo | Estado global oculto | Más clases que mantener |

### Resumen de los nueve patrones

| Patrón | Familia | Problema que resuelve |
|:-------|:--------|:----------------------|
| Singleton | Creacional | Una única instancia compartida |
| Factory Method | Creacional | Crear un objeto de varios tipos posibles |
| Abstract Factory | Creacional | Crear familias de objetos relacionados |
| Adapter | Estructural | Interfaces incompatibles |
| Facade | Estructural | Esconder complejidad detrás de una interfaz simple |
| Decorator | Estructural | Agregar responsabilidades sin herencia |
| Observer | Comportamiento | Notificar cambios a varios objetos |
| Strategy | Comportamiento | Intercambiar algoritmos en tiempo de ejecución |
| Command | Comportamiento | Encapsular acciones (encolar/deshacer) |

## Fuentes

### Refactoring.Guru — "Patrones de diseño" (fuente principal, en español, completa y gratuita)

https://refactoring.guru/es/design-patterns

### Sourcemaking — "Design Patterns" (en español)

https://sourcemaking.com/design_patterns

### Head First Design Patterns (sitio del libro)

https://www.oreilly.com/library/view/head-first-design/0596007124/

## Para practicar

1. Identificá, en cualquier aplicación que uses a diario, al menos un patrón de cada familia. Por ejemplo: ¿dónde hay un Singleton en tu celular? ¿dónde un Observer cuando recibís notificaciones?

2. Tomá el sistema ganadero del ejemplo y respondé: ¿qué pasaría si quiero agregar un nuevo tipo de animal sin romper el código existente? ¿Qué patrón me ayuda y por qué?

3. Programá en el lenguaje que prefieras un `Strategy` que calcule el área de distintas figuras geométricas (cuadrado, círculo, triángulo) usando una interfaz común.

4. Diferenciá con tus palabras: ¿en qué se distingue `Adapter` de `Facade`? (Pista: uno traduce una interfaz para que encaje; el otro simplifica un sistema complejo.)

5. Describí un caso donde aplicar `Singleton` sea una buena decisión y otro donde sea perjudicial. Justificá ambas respuestas.

6. Conectá los patrones con SOLID: elegí tres patrones del material y explicá qué principio de SOLID ayudan a respetar.

7. Leé la explicación de `Abstract Factory` en Refactoring.Guru y explicá con tus palabras la diferencia frente a `Factory Method`, apoyándote en la analogía de las familias de productos.
