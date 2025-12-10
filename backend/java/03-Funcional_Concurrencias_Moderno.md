<div align="center">
  <img src="../../assets/java_logo.svg">
</div>

# Índice

- [Índice](#índice)
- [Introducción](#introducción)
- [Modularidad](#modularidad)
  - [Module-info.class](#module-infoclass)
  - [Compilación de un módulo](#compilación-de-un-módulo)
  - [Abreviatura de argumentos](#abreviatura-de-argumentos)
  - [Comando jdeps](#comando-jdeps)
  - [Módulos anónimos](#módulos-anónimos)
  - [Otras características](#otras-características)
- [Clase Optional](#clase-optional)
- [Expresiones lambda](#expresiones-lambda)
  - [¿Qué es una interfaz funcional?](#qué-es-una-interfaz-funcional)
  - [¿Qué es?](#qué-es)
  - [Inferencia de tipos](#inferencia-de-tipos)
  - [Interfaces funcionales asociadas a expresiones lambda](#interfaces-funcionales-asociadas-a-expresiones-lambda)
    - [Interfaz Predicate](#interfaz-predicate)
    - [Interfaz Function](#interfaz-function)
    - [Interfaz Consumer](#interfaz-consumer)
    - [Interfaz Supplier](#interfaz-supplier)
    - [Interfaz UnaryOperator](#interfaz-unaryoperator)
- [Referencia a métodos](#referencia-a-métodos)
- [Stream](#stream)
  - [Principales métodos de Stream](#principales-métodos-de-stream)
  - [Collect](#collect)
  - [Stream en paralelo](#stream-en-paralelo)
    - [Referencias a métodos](#referencias-a-métodos)
    - [Stream de tipos primitivos](#stream-de-tipos-primitivos)
- [Serialización](#serialización)
- [Base de datos (Acceso a datos con JDBC)](#base-de-datos-acceso-a-datos-con-jdbc)
- [Concurrencia/Multitarea](#concurrenciamultitarea)
  - [Condiciones de carrera](#condiciones-de-carrera)
  - [Threads](#threads)
  - [Runnable](#runnable)
  - [Executors](#executors)
    - [ExecutorService](#executorservice)
    - [Interfaz Callable](#interfaz-callable)
    - [Interfaz Future](#interfaz-future)
    - [Lock, semáforos y sincronización](#lock-semáforos-y-sincronización)
    - [Colecciones para concurrencia](#colecciones-para-concurrencia)
- [Atomic](#atomic)
  - [AtomicInteger/AtomicLong](#atomicintegeratomiclong)
  - [AtomicBoolean](#atomicboolean)
- [CyclicBarrier](#cyclicbarrier)
- [Localización e Internalización](#localización-e-internalización)
  - [Archivos de recursos](#archivos-de-recursos)
  - [Clase Locale](#clase-locale)
- [Formateado de datos](#formateado-de-datos)
- [Pautas para codificación segura](#pautas-para-codificación-segura)
  - [Denegación del servicio](#denegación-del-servicio)
  - [Confidencialidad](#confidencialidad)
  - [Inyección](#inyección)
  - [Accesibilidad](#accesibilidad)
  - [Validación de datos](#validación-de-datos)
  - [Mutabilidad](#mutabilidad)
  - [Construcción objetos](#construcción-objetos)
  - [Serialización](#serialización-1)
  - [Control de acceso](#control-de-acceso)
- [Novedades en versiones posteriores a Java 11](#novedades-en-versiones-posteriores-a-java-11)
  - [Instrucción switch](#instrucción-switch)
    - [Expresiones switch](#expresiones-switch)
    - [Sintaxis expresiones switch](#sintaxis-expresiones-switch)
  - [Bloques de texto](#bloques-de-texto)
    - [Espacios](#espacios)
    - [Indentación](#indentación)
    - [StripIndent](#stripindent)
  - [Coincidencias de patrones con instanceof](#coincidencias-de-patrones-con-instanceof)
  - [Records](#records)
    - [Constructor compacto](#constructor-compacto)
    - [Sobrecarga de constructores](#sobrecarga-de-constructores)
  - [Sealed clases](#sealed-clases)
  - [Manipulación de fechas con java.time](#manipulación-de-fechas-con-javatime)


# Introducción

Este documento finaliza la guía con temas avanzados y las características de Java moderno, esenciales para el desarrollo de aplicaciones robustas y de alto rendimiento. Cubre la programación funcional con Expresiones Lambda, Referencias a Métodos y la API de Streams. Además, aborda la Concurrencia y Multitarea para optimizar el rendimiento, el acceso a datos externos con JDBC, la Serialización, y el uso de la Clase Optional para manejo seguro de nulos. Finalmente, se exploran las novedades de Java 11+, incluyendo la modularidad y las mejoras en la sintaxis.

# Modularidad

La modularidad en Java se refiere a la capacidad de dividir una aplicación Java en módulos o unidades lógicas independientes y bien definidas, lo que permite una mejor organización del código y una mayor facilidad de mantenimiento y escalabilidad del sistema. La modularidad en Java se introdujo en la versión 9 de la plataforma Java como una característica importante, y se basa en el concepto de "Java Platform Module System" (JPMS).

La modularidad en Java se logra mediante la creación de módulos que contienen un conjunto de paquetes relacionados, y que pueden ser exportados o importados por otros módulos. Cada módulo tiene su propio espacio de nombres y se puede definir como un conjunto de requisitos y capacidades, lo que significa que los módulos pueden especificar qué otros módulos necesitan para funcionar correctamente y qué servicios ofrecen a otros módulos.

En resumen, la modularidad en Java es una forma de dividir una aplicación en componentes lógicos separados, lo que permite una mejor organización del código y una mayor facilidad de mantenimiento y escalabilidad.

Las ventajas de usar la modularidad son las siguientes:
-	Mejorar el control de acceso. Permite que ciertos paquetes sean utilizados solo por otros paquetes.
-	Claridad en las dependencias. A través de module-info, se especifica claramente las dependencias entre módulos, que son evaluadas al compilar y al lanzar la aplicación.
-	Paquetes de distribución mas pequeños. Facilita la distribución de aplicaciones y mejora el rendimiento.
-	Existencia de paquetes únicos. No puede haber dos módulos que expongan el mismo paquete.

## Module-info.class

Es un archivo de clase que se genera cuando se compila un módulo en Java 9 o posterior. Este archivo contiene la información sobre el módulo, como su nombre, versión, dependencias y paquetes que exporta. El propósito principal del archivo es permitir la modularidad en Java. La ubicación de este documento debe de ser la raíz del directorio modulo.

## Compilación de un módulo

Desde el directorio raíz, el que contiene al módulo a compilar

```
Javac -- module-path dir_modulo_dep -d dir_destino ficheros 
javac -d modulo2 modulo2/*.java (no necestia module-path pues no depende de ningún)
```

## Abreviatura de argumentos
--module-path = -p
--module = -m
Ejemplo: javac -p . -m modulo1/com.cliente.Test
Empaqueta en archivos
Para empaquetar un modulo en un .jar debemos hacer uso del comando

```Jar –c –file=dir_destrino|nombre_archivo.jar –C path_modulo.```

Dir destino es el directorio de destino del modulo y path_modulo el directorio raíz del modulo. El punto “.” Indica que se incluya todo el contenido del directorio

```
Modulo2: jar –c –file=ejecutables/modulo2.jar –C modulo2
Modulo1: jar –c –file=ejecutables/modulo1.jar –C modulo1
Para ejecutar com.module1 desde ejecutables
Java –p  . –m com.module1/com.cliente.Test
```

Otro sistema de empaquetado pero no es muy común es el archivo .jmod, es muy similar a .jar, si bien debe ser utilizado para librerías nativas en lugar de modulos en generar. Debemos de tener en cuenta que no se puede utilizar el formato en la ejecución de modulos.

```
Jmod create –class-path dir_modulo fichero.jmod
Modulo2: jmod create –class-paht modulo2 ejecutables/modulo2.jmod
Modulo1: jmod create –class-paht modulo1 ejecutables/modulo1.jmod
```

## Comando jdeps

Se emplea para obtener información sobre la dependencia de modulos
-	Jdeps –s dir_modulo O jdeps –s dir_modulo/archivo.jar
Si depende de algún modulo extra
-	Jedps –module-path dir_mod_dependiente –s dir_modulo

## Módulos anónimos

Conjunto de paquetes de clases de una aplicación que no forma parte de un modulo. Habitualmente, se distribuyen en un .jar
Desde estas clases, se puede acceder a cualquier paquete de clases que se encuentre en el classpath, incluyendo tanto otros módulos anónimos como estándares.
Solo pueden acceder a las clases de un modulo anónimos las clases de otros módulos anónimos.

Cuando un modulo anónimo se incluye en el module-path de una aplicación modular, se convierte en un modulo automático. Desde estos, se puede acceder a cualquier paquete de clases, tanto de módulos anónimos/automáticos como de estándares.
Exportan implícitamente todas sus clases, que podrán ser utilizadas por otros módulos que lo requieran

## Otras características

Se puede  indicar que un determinado paquete de un modulo sea accesible únicamente por cierto modulo. Se emplea la palabra reservado to.
- Dependencias Transitivas:
Los módulos pueden tener dependencias transitivas, esto quiere decir, evitar redundancias a la hora de requerir dos módulos en los que, a su vez, uno requiere a otro. Usaríamos la palabra reservada transitive.
- Servicios:
Funcionalidad que expone una funcionalidad y la usan otros aplicaciones. Los servicios se describen a través de una interfaz de java. Por lo que tendremos que tener en cuenta 3 conceptos:
- Servicio: interfaz que define el modulo
-	Proveedor: Modulo que implementa la interfaz (provides com.interfaz1 with com.Clase1)
-	Consumidor: Modulo que utiliza el servicio (uses com.Interfaz1)

-	Acceso por reflexión:
Es posible especificar que los paquetes especificados del modulo son accesibles vía reflexión a otros módulos (opens com.paquete). Incluso, que lo sean solo a ciertos módulos (opens com.paquete to moda, modB).


# Clase Optional

La clase Optional en Java es una clase introducida en Java 8 que se utiliza para representar un valor que puede o no estar presente. Es decir, es una forma de indicar que un valor puede ser nulo o no existir, es decir, encapsula el resultado de una operación final.

La clase Optional se utiliza para evitar excepciones de tipo NullPointerException que pueden ocurrir al trabajar con referencias nulas. Al usar Optional, en lugar de devolver un valor nulo, se devuelve una instancia de Optional que puede contener un valor nulo o no nulo.
La clase Optional tiene métodos para verificar si el valor está presente o no, para obtener el valor si está presente, o para obtener un valor predeterminado si el valor no está presente.

-	Get: Devulebe el valor encapsulado. So no hay ningún valor, lanza una excepción de tipo NoSuchElementException.
-	orElse. Devuelve el valor encapsulado. Si no hay ninguno, entonces devuelve el valor pasado como parámetro.
-	isPresent: Permite comprobar si contiene o no algún valor.

Existen las variantes OptionalInt y OptionalDouble que encapsulan los tipos primitivos.

# Expresiones lambda

## ¿Qué es una interfaz funcional?

Una interfaz funcional es una interfaz de Java que contiene solo un método abstracto, también conocido como "método de función única". Esta característica es clave para el uso de funciones lambda en Java. Las interfaces funcionales se utilizan en el contexto de la programación funcional para permitir que una función sea tratada como un objeto y, por lo tanto, sea pasada como argumento a otra función. En otras palabras, se utilizan como un medio para permitir la programación funcional en Java. La anotación @FunctionalInterface se utiliza para indicar que una interfaz es una interfaz funcional. Esta anotación no es obligatoria, pero es recomendable para evitar errores.

## ¿Qué es?

En Java, las funciones lambda son una característica introducida en Java 8 que permite crear funciones anónimas de una manera más concisa y fácil de leer. Una función lambda se define como una expresión que representa una función sin nombre que se puede pasar como argumento a otro método o función. Las funciones lambda son funciones de un solo método que no requieren una declaración formal, un modificador de acceso o un nombre.
Las funciones lambda son útiles para simplificar el código al evitar la necesidad de crear clases anónimas para implementar interfaces funcionales. Además, permiten una programación funcional más natural y menos verbosa en Java.
Las funciones lambda se definen utilizando una sintaxis reducida que hace uso de la flecha 
"->". La parte izquierda de la flecha representa los parámetros de la función y la parte derecha representa el cuerpo de la función.

Por ejemplo, la siguiente expresión lambda toma dos argumentos y devuelve la suma de ellos: 
```java (int a, int b) -> a + b.```


Los parámetros pueden indicar o no el tipo. 
La lista de parámetros se puede indicar o no entre paréntesis (obligatorio si hay dos o más) y también si se indica el tipo. En caso de devolver un resultado la implementación puede omitir la palabra return si consta de una sola instrucción.

## Inferencia de tipos

La utilidad de la indiferencia se usa principalmente para determinados tipos de anotaciones en la definición de los parámetros del método, por ejemplo @NotNull var c.

Es posible inferir el tipo en los parámetros de las expresiones lambda, aunque no se puede combinar inferencia de tipos y tipos específicos en una misma expresión.

## Interfaces funcionales asociadas a expresiones lambda 

Conjunto de interfaces funcionales incorporadas en Java SE 8 dentro del paquete java.util.function. Utilizadas como argumentos en métodos que manipulas datos para el establecimiento de criterios de filtrado, operación sobre elementos, transformación etc.
Existen variantes para los datos primitivos sobre todo para int, long y double. Estas variaciones son:
-	IntPredicate
-	IntFunction
-	IntConsumer
-	IntSupplier
-	IntUnaryOperator.

### Interfaz Predicate

La interfaz Predicate es una interfaz funcional en Java que se utiliza para representar una función que toma un objeto y devuelve un valor booleano. Esta interfaz se utiliza comúnmente para la evaluación de condiciones y filtrado de datos en colecciones.
La interfaz Predicate tiene un único método abstracto llamado test().

La interfaz Predicate también tiene varios métodos predeterminados (default methods) que se pueden utilizar para combinar o negar predicados. Estos métodos incluyen:

-	and(Predicate<? super T> other): devuelve un predicado que representa la combinación lógica AND de este predicado y otro predicado dado.
-	or(Predicate<? super T> other): devuelve un predicado que representa la combinación lógica OR de este predicado y otro predicado dado.
-	negate(): devuelve un predicado que representa la negación lógica de este predicado.
Tiene una variante que es BiPredicate con dos parametros.

### Interfaz Function

La interfaz Function es una interfaz funcional en Java que se utiliza para representar una función que toma un objeto de entrada de un tipo y produce un objeto de salida de otro tipo. En otras palabras, se utiliza para transformar un objeto de un tipo a otro.
La interfaz Function tiene un único método abstracto llamado apply() que toma un objeto de entrada y devuelve un objeto de salida.
Tiene varios métodos predeterminados que se pueden utilizar para combinar funciones. Estos métodos incluyen:
-	andThen(Function<? super T, ? extends V> after): devuelve una función que representa la composición de esta función y otra función dada.
-	compose(Function<? super V, ? extends T> before): devuelve una función que representa la composición de esta función y otra función dada, en orden inverso.
-	identity(): devuelve una función identidad que simplemente devuelve su argumento sin transformación.

Tiene una variante que es BiFunction con dos parametros.

### Interfaz Consumer

La interfaz Consumer es una interfaz funcional en Java que se utiliza para representar una operación que toma un objeto de entrada de un tipo y no devuelve nada. En otras palabras, se utiliza para realizar alguna operación o efecto secundario en un objeto sin producir ningún resultado. La interfaz Consumer tiene un único método abstracto llamado accept() que toma un objeto de entrada y no devuelve nada.

Tiene varios métodos predeterminados que se pueden utilizar para combinar o encadenar consumidores. Estos métodos incluyen:
-	andThen(Consumer<? super T> after): devuelve un consumidor que representa la composición de este consumidor y otro consumidor dado.

Tiene variante BiConsumer.

### Interfaz Supplier

La interfaz Supplier es una interfaz funcional en Java que se utiliza para representar una función que no toma ningún argumento y devuelve un objeto de un tipo determinado. En otras palabras, se utiliza para generar o proveer un valor sin tomar ningún parámetro de entrada. La interfaz Supplier tiene un único método abstracto llamado get() que no toma argumentos y devuelve un objeto de un tipo determinado.

### Interfaz UnaryOperator

La interfaz UnaryOperator es una interfaz funcional en Java que extiende la interfaz Function. Se utiliza para representar una función que toma un objeto de un tipo determinado y devuelve un objeto del mismo tipo. En otras palabras, se utiliza para realizar una operación en un objeto y devolver el mismo objeto actualizado. Tiene versión para datos primitivos.
La interfaz UnaryOperator tiene un único método abstracto llamado apply() que toma un objeto de un tipo determinado y devuelve el mismo objeto actualizado
Tiene varios métodos predeterminados que se pueden utilizar para combinar o encadenar operadores. Estos métodos incluyen:
-	compose(Function<? super T, ? extends T> before): devuelve una función que representa la composición de este operador y otra función dada.
-	andThen(Function<? super T, ? extends T> after): devuelve una función que representa la composición de este operador y otra función dada.

Posee una variante BinaryOperator equivalente a BIFunction.

# Referencia a métodos

Es una funcionalidad que puede sustituir a una expresión lambda cuya única instrucción consiste en la llamada a un método. El compilador infiera las variables dadas por parámetro en el argumento del método
<table>
  <tr>
    <th>Tipo de referencia</th>
    <th>Referencia método</th>
    <th>Expresion lambda</th>
  </tr>
  <tr>
    <th>Método estático</th>
    <td>String::valueOf</td>
    <td>s->String.valueOf(s)</td>
  </tr>
  <tr>
    <th>Método de un objeto especifico</th>
    <td>Var r = new Random()
    r::nextInt</td>
    <td>Var r = new Random()
    n -> r::nextInt(n)</td>
  </tr>
  <tr>
    <th>Método arbitrario</th>
    <td>Stirng::equals</td>
    <td>(s1,s2) -> s1.equals(s2)</td>
  </tr>
  <tr>
    <th>Método constructor</th>
    <td>Person::new</td>
    <td>a -> person(A)</td>
  </tr>
</table>

# Stream

Un stream es una secuencia de datos que se procesa de manera secuencial. Los streams proporcionan una forma de trabajar con colecciones de datos de manera más flexible, legible y concisa, utilizamos la interfaz Stream de java.util.stream.
En términos generales, un stream se compone de tres elementos principales:
- Origen de datos: Es la fuente de datos, como un arreglo, una lista o una fuente de entrada / salida.
-	Operaciones intermedias: Son las operaciones que se realizan en los datos mientras se procesan en el stream, como filtrar, mapear o ordenar.
-	Operaciones terminales: Son las operaciones finales que se realizan en los datos del stream, como contar, reducir o recolectar los elementos en una colección.

Los streams en Java permiten el procesamiento de grandes cantidades de datos de manera eficiente y efectiva, utilizando el paradigma de programación funcional. También permiten el procesamiento de datos de forma paralela y asíncrona, mejorando aún más el rendimiento y la eficiencia en la manipulación de grandes volúmenes de datos.

Los stream tiene versiones para los datos primitivos, estas versiones son IntStream, LongStream y DoubleStream.

Su funcionamiento es simple, recorre los datos desde el principio hasta el final y durante el recorrido realiza algún tipo de cálculo u operación. Una vez realizado el recorrido, el stream se cierra y no puede volver a utilizarse.

Los stream se pueden crear a partir de una colección, un array (Arrays.stream(array)), una seride discreta de datos (Stream.of(2.4,7.4,9.1)) o a partir de un rango de datos(IntStream.range(1,10)).

## Principales métodos de Stream

Métodos intermedios: El resultado de su ejecución es un nuevo Stream. Esto sucede cuando se filtra y transforma datos, ordenación…
Métodos finales: Generan un resultado. Puede ser void o devolver un valor resultado de alguna operación. Esto sucede con cálculo de operaciones, búsquedas reducción…
- Conteo y procesado (métodos finales)
  *	Long count. Devuelve el número de elementos de un Stream
  *	Void forEach. Realiza una acción para cada elemento del stream.
-	Extracción de datos (métodos intermedios)
  *	Stream Distinct. Devuelve un Stream eliminado los elementos duplicados, según aplicación de equals().
  * Stream limit. Devuelve un nuevo Stream con lo n primeros elementos del mismo.
  * Stream skip. Devuelve un nuevo Stream, saltándose los n primeros elementos.
-	Comprobaciones (métodos finales)
Funcionan en modo cortocircuito, es decir, si encuentra un elemento que cumple la condición no comprueba más.
  *	Boolean anyMatch: Devuelve true si algún elemento del Stream cumple con la condición del predicado.
  *	Boolean allMatch: Devuelve true si todos cumplen con la condición del predicado.
  *	Boolean noneMatch: Devuelve true si ninguno cumple con la condifcion del predicado.
- Filtrado (Método Intermedio)
  *	Stream filter: Aplica un filtro sobre el Stream, devolviendo un nuevo Stream con los elementos que cumplen el predicado.
- Búsquedas (Métodos finales)
  *	Optional findFirst(): Devuelve el primer elemento del Stream, o un Optional vacio si no hay nada
  *	Optional findAny(): Devuelbe cualquiera de los elementos del Stream.Normalmente, el primero
-	Obtención de extremos (Métodos finales)
  *	Optional max: Devuelve el mayor de lo elementos, según el criterio de compracion del objeto Comparator.
  *	Optional mix: Operación contraria a max.
-	Transformacion (Métodos intermedios)
  *	Stream map: Transforma cada elemento del Stream en otro según el criterio definido por el objeto Function que se le pasa como parámetro.
  *	IntStream mapToInt: Aplica una función a cada elemento del Stream que genera un int de cada elemento. El resultado se devuelve como IntStream.
  *	flatMap: Devuelve un nuevo Stream, resultante de unir los Streams generados por la aplicación de una función sobre cada elemento.
- Procesamiento intermedio (Método intermedio)
  *	Stream Peek: Aplica el consumer a cada elemento del Stream, devolviendo un nuevo stream idéntico para continuar con la manipulación de los elementos. Las operaciones se aplican en modo Lazy(se queda en memoria) y solo serán operativas tras una operación final.
-	Ordenacion (Métodos intermedios)
  *	Stream sorted: Devuelbe un Stream con los elementos ordenados, según el orden natural de los mismos
  *	Stream sorted(Comparator): Devuelve un Stream con los elementos ordenados según el criterio de comparación especificado.
-	Reducción (Método final)
  *	Optional reduce: Realiza la reducción de los elementos del stream a un único valor, utilizando la función proporcionada como parámetro.

## Collect

-	Reducción
  *	 R collect: Devuelve un List, Map, o Set con los datos del Stream, en función de la implementación de Collector proporcionada.
-	Agrupación 
  *	Collector groupingBy: Devuelve un Collector que implementa una agrupación de tipo  groupBy. El método recibe como parámetro un objeto Function con el crtiterio de agrupación. Con este tipo de Collector la llamada a collect devolverá un Map de listad. Cada elemento map a tiene una clave, que es el dato por el que se hace la agrupación y un valor con la lista de objetos de cada grupo. 
-	Partición
  *	Collector partitioningBy: Devuelve un Collector para generar una agrupación Map de clave boolean y valor lista de objetos. El método recibe como parámetro un predícate para aplicar la condición a cada elemento, de modo que los que la cumplan serán agregados en una lista con clave true, y los que no en otra lista con clave false.
-	Otros usos
  *	Podemos convertir un Stream en un colección inmutable gracias al método toUnmodifiableList o toUnmodifiableSet
  *	Collector averagingDouble: Permite calcular la media a partir de los valores devueltos por la función. Existe también averagingInt y averagingLong.
  *	Collector summingInt: Permite calcular la suma a partir de los valores devueltos por la función. Existe summingLong y summingDouble.
  *	Collector joining: Devuelve un Collector que concatena en un único String todos los String resultantes de la llamada a toString sobre cada objeto del Stream.

## Stream en paralelo

Un stream paralelo en Java es una secuencia de datos que se procesa en paralelo mediante múltiples hilos de ejecución, en lugar de un solo hilo como en un stream secuencial. Esto permite un procesamiento más rápido de grandes volúmenes de datos en situaciones en las que el rendimiento es crítico. Los Stream paralelos siguen siendo objetos Stream, que utilizan los mismos métodos estudiados, pero operando de forma más eficiente. Debemos preocuparnos en operaciones que requieran realizarse en un determinado orden. Los stream paralelos se crean al usar el método parallelStream en lugar de stream en el caso de collection y para el propio stream será el método parallel.

Para las operaciones finales de ordenación los stream paralelos devuelen los datos ordenados según los datos almacenados que posea cada hilo, provocando que los datos no salgan en el orden esperado. Para evitar esto podemos realizar las operaciones intermedias de manera asíncrona y usar el método sequential para transformar el stream paralelo en un stream secuencial.

### Referencias a métodos

Las referencias a métodos sustituyen a expresiones lambda cuya única instrucción consiste en una llamada a un método. Indica que método debe ser llamado en circunstancias donde los parámetros y objeto al que aplicarlo pueden ser deducidos por el contexto.
Sintaxis: Clase/objeto::nombre_metodo
Existen 4 tipos

Tipo	Expresión lambda equivalente	Referencia a método
Referencia a método estatico	s->String.valueOf(s)	String::valueOf
Referencia a método de objeto especifico	s-> System.out.println(s)	System.out::println
Referencia a método de objeto arbitrario	(a,b)->a.equals(b)	String::equals
Referencia a constructor	a->new MiClase(a)	MiClase::new

### Stream de tipos primitivos

Las interfaces IntStream, DoubleStream y LongStream, cuyos objetos son obtenidos los métodos mapToInt, mapToDouble y mapToLong, respectivamente, proprcionan los siguientes métodos de cálculo:
-	Sum: Método final que devueleve la suma de todos los elementos del stream.
-	Average:Metodo final que devuelve la media encapsulada en un OptionalDouble en los tres casos.
-	Max y min: Devuelve el mayor y menos de los números respectivamente. En DoubleStream  y LongStream el tipo de devolución es OptionalDouble y OptionalLong, respectivamente.

# Serialización

La serialización en Java se refiere al proceso de convertir un objeto Java en un formato que pueda ser almacenado o transmitido a través de una red, y luego restaurarlo nuevamente a su forma original de objeto cuando sea necesario. En otras palabras, la serialización en Java es el proceso de convertir un objeto en una secuencia de bytes que puede ser guardada en un archivo o enviada a través de una red, y la deserialización es el proceso inverso de convertir esa secuencia de bytes nuevamente en un objeto Java.

La serialización en Java es útil en situaciones en las que se necesita guardar objetos complejos en un archivo o enviarlos a través de una red. También se utiliza en tecnologías como Java RMI (Remote Method Invocation) y Java Messaging Service (JMS) para transmitir objetos Java entre diferentes sistemas.

En Java, la serialización se puede implementar mediante la implementación de la interfaz Serializable en la clase del objeto que se desea serializar. La interfaz serializable no contiene ningún método. Las clases de envoltorio, String y las clases de colección ya implementan esta interfaz. Los objetos de clases que implementan Serializable se pueden convertir en una secuencia de bytes utilizando la clase ObjectOutputStream y se pueden restaurar utilizando la clase ObjectInputStream.

El atributo transient es una palabra clave que se puede utilizar para indicar que un campo o propiedad de una clase no debe ser serializado durante el proceso de serialización. Cuando se marca un campo como transient, se excluye de la serialización y no se guarda en el archivo o se transmite a través de una red. 

La razón por la que se utiliza la palabra clave transient es porque hay ciertos campos que no tienen sentido ser serializados. Por ejemplo, si una clase tiene un campo que contiene una conexión a una base de datos o un recurso de sistema, no tiene sentido serializarlo porque la conexión se perderá y no se podrá reconstruir en el momento de la deserialización. 
Además, los campos marcados como transient pueden ser inicializados por un constructor o mediante lógica personalizada en el método readObject() durante la deserialización.

# Base de datos (Acceso a datos con JDBC)

JDBC (Java Database Connectivity) es una API (Application Programming Interface) de Java que proporciona una interfaz común para acceder a una amplia variedad de bases de datos relacionales. Con JDBC, los programadores de Java pueden escribir aplicaciones que interactúen con bases de datos, independientemente del sistema de gestión de bases de datos (DBMS) subyacente.

JDBC proporciona un conjunto de clases e interfaces que permiten a los programadores de Java conectarse a una base de datos, enviar consultas y actualizar datos. Estas clases e interfaces se encuentran en el paquete java.sql y sus subpaquetes. Los programadores pueden utilizar JDBC para ejecutar consultas SQL y procesar los resultados, lo que les permite acceder a los datos almacenados en una base de datos.

Principales clases:
-	DriverManager: Proporciona un método estatico para poder obtener conexiones contra la base de datos.
-	Connection: Representa una conexión contra la base de datos. La obtención de una conexión es un paso previo para poder operar contra la misma
-	Statement: A través de este objeto podemos enviar consultas SQL a la base de datos
-	PreparedStatement: Es una versión alternativa de Statement, con la que podemos precompilar consultas SQL antes de enviarlas a la BD.
-	ResultSet: Cuando una consulta devuelve resultados (caso de las instrucciones Select), la manipulación de los mismos se realiza a través de un objeto ResultSet.

Paso para operar contra una BD

-	Cargar el driver 
  - es una librería .jar que se incluye dentreo del classpath de la aplicacion.
  - Desde JDBC 4 no es necesario realizar esta operación
  - Versiones anteriores ```Class.forName(“com.mysql.jdbc.Driver”)```
-	Establecimiento de la conexión con la BD.
  -	La conexión con la base de datos se establece a través del método getConnection de DriverManager, que devuelve un objeto Connection
  -	La cadena de conexión tiene el siguiente formato ```jdbc:<subprotocolo>:subname```. Donde suprotocolo es el tipo de base de datos y súbame depende de la base de datos.
  -	El nombre de las properties se les puede suministrar usando la clase properties
-	Ejecución de la consulta SQL.
  -	Statement ejecuta las consultas usando el mentodo execute.
  -	PreparedStatement ejecutamos consultas parametrizadas siendo 1 el primer parámetro usando el método executeQuery.
-	Manipulación de resultados, si procede.
  -	Para la lectura de datos y manipularlos usaremos la clase ResultSet
  -	Next se desplaza al siguiente registro, si no hay niguno devolverá false
  -	getXxxx(int col): Obtenemos el valor de la columna indicada. La posición de la primera columna es la 1.
  -	getXXX(String col): Igual que el anterior, utilizando el nombre de la columna
-	Cierre de la conexión.
  -	Utilizando el método close
  -	Mediante un try con recursos que cerrara automáticamente cuando salga del try

# Concurrencia/Multitarea

En Java, la multitarea se refiere a la capacidad de un programa para realizar varias tareas o procesos simultáneamente, también conocido como programación concurrente. La multitarea en Java se puede lograr de varias formas, entre ellas:

-	Hilos (Threads): un hilo es un subproceso dentro de un programa que se ejecuta de forma independiente y concurrente con otros hilos. La programación de hilos en Java se puede realizar a través de la clase Thread o mediante la implementación de la interfaz Runnable.
-	Executor framework: el framework Executor proporciona una forma de ejecutar tareas en segundo plano utilizando hilos en un conjunto predefinido de hilos. El framework también proporciona una forma de administrar los hilos y controlar su ejecución.
-	Locks y semáforos: se utilizan para establecer una exclusión mutua entre los hilos para que solo uno de ellos pueda acceder al recurso compartido en un momento dado.

## Condiciones de carrera

Una condición de carrera (race condition) en Java se produce cuando dos o más hilos intentan acceder y manipular un recurso compartido al mismo tiempo, lo que puede provocar resultados impredecibles y errores en el programa. Las condiciones de carrera pueden ocurrir cuando los hilos comparten recursos, como variables, objetos o archivos, y estos recursos no están protegidos mediante técnicas de sincronización. Al no tener un mecanismo de sincronización adecuado, los hilos pueden leer y escribir en el recurso compartido al mismo tiempo, lo que puede provocar inconsistencias en los datos.

Métodos y bloques sincronizados: se utilizan para asegurar que solo un hilo pueda acceder al recurso compartido a la vez.

Es importante tener en cuenta que la sincronización en Java puede afectar el rendimiento del programa, por lo que se debe utilizar de manera adecuada y solo en los recursos que realmente lo requieran. En general, se recomienda utilizar la sincronización solo cuando sea necesario y siempre que sea posible utilizar estructuras de datos inmutables o evitando el uso de recursos compartidos en la medida de lo posible.

## Threads

La clase Thread en Java es una clase incorporada que proporciona una forma de crear y controlar hilos en un programa. Para utilizar la clase Thread, se debe crear una subclase que extienda la clase Thread y luego implementar el método run(). El método run() es el punto de entrada para el hilo y contiene el código que se ejecutará en segundo plano.

A parte de run Thread proporciona otros métodos
-	Start: para iniciar la ejecución del hilo
-	Sleep: para hacer que el hilo se detenga durante un periodo de tiempo determinado
-	Join: para esperar a que otro hilo termine antes de continuar.

## Runnable

La interfaz Runnable en Java es una interfaz funcional que define un solo método llamado run(). Esta interfaz se utiliza para crear hilos en Java de una manera más flexible que utilizando la clase Thread.

Para utilizar la interfaz Runnable, se debe crear una clase que implemente la interfaz Runnable y luego implementar el método run(). Al igual que con la clase Thread, el método run() es el punto de entrada para el hilo y contiene el código que se ejecutará en segundo plano.

Una vez que se ha creado una clase que implementa Runnable, se puede crear un objeto de esa clase y pasarlo como argumento al constructor de la clase Thread. Luego, se puede llamar al método start() en el objeto Thread para iniciar la ejecución del hilo.

La principal ventaja de utilizar la interfaz Runnable en lugar de la clase Thread es que se puede extender una clase existente en Java y, al mismo tiempo, implementar la interfaz Runnable. Esto no es posible con la clase Thread, ya que Java no admite la herencia múltiple.
Además, utilizar la interfaz Runnable permite separar la lógica de ejecución del hilo de la lógica de gestión de hilos. Esto puede hacer que el código sea más claro y fácil de entender, especialmente en aplicaciones grandes y complejas.

## Executors

La clase Executors en Java es una clase de utilidad que proporciona una forma fácil de crear y administrar hilos en un programa. Esta clase se utiliza para crear y gestionar un conjunto de hilos conocido como "pool de hilos".

El pool de hilos es un grupo de hilos que están disponibles para realizar tareas en segundo plano en un programa. Al utilizar el pool de hilos, se pueden realizar varias tareas en paralelo sin tener que crear un nuevo hilo cada vez que se necesita realizar una tarea.

La clase Executors proporciona varios métodos estáticos para crear diferentes tipos de pool de hilos, como newFixedThreadPool(), newSingleThreadExecutor(), newCachedThreadPool(), etc. Cada uno de estos métodos crea un pool de hilos con diferentes características.
Por ejemplo, el método newFixedThreadPool() crea un pool de hilos con un número fijo de hilos, mientras que el método newCachedThreadPool() crea un pool de hilos que aumenta o disminuye su tamaño según la carga de trabajo.

Una vez que se ha creado un pool de hilos, se pueden enviar tareas al pool para su ejecución utilizando el método execute() o submit(). El método execute() se utiliza para enviar tareas que no devuelven ningún resultado, mientras que el método submit() se utiliza para enviar tareas que devuelven un resultado.

Además de los métodos para crear y enviar tareas al pool de hilos, la clase Executors también proporciona métodos para configurar la forma en que se manejan las tareas que no se pueden ejecutar debido a la falta de hilos disponibles en el pool de hilos.

### ExecutorService

Proporciona  métodos para el lanzamiento y ejecución de tareas de forma concurrente, utilizando un pool de threads (solo se cierran si se invoca al método shutdown).

 Los métodos principales son:
-	Submit(Runnable tarea): Lanza la tarea y la pone en ejecución concurrente con el resto.
-	Submit(Callable tarea): Lo mismo que el anterior, pero para objetos Callable.
-	Shutdown:Inicia el final del pool de hilos, por lo que no se aceptaran nuevas tareas.

Se pueden crear implementaciones de ExecutorService a partir de los siguientes métodos estáticos de Executors:
-	newCachedThreadPools: Crea un ExecutorService con un pool de threads variable que se crean a demanda.
-	newFixedThreadPools(int hilos): Crea un pool con un número fijo de threads.
-	newSingleThreadExecutors: Crea un ExecutorService que utiliza un único thread.
-	newScheduledThreadPool(int corePoolSize): Devuelve un ScheduledExecutorService que permite ejecutar tareas periódicamente.

### Interfaz Callable

Al igual que Runnable, implementa una tara que va a ser ejecutada concurrentemente con otras. Su único método, call(), devuelve un resultado, permite declarar checked exceptions. Esta interfaz se usa principalmente para operaciones matematicas.

### Interfaz Future

Implementación que permite obtener el resultado de una operación asíncrona sin necesidad de que esté terminada.

-	El método submit(Callable tarea) de ExecutorService devuelve un objeto Future que puede ser utilizado para acceder al resultado de la tarea y controlar su ejecución.
-	isDone: Permite conocer si la tarea ha finalizado.
-	Get: Devuelve el valor generado por Callable. Si aun no ha terminado la tarea a la espera del resultado.

### Lock, semáforos y sincronización

Interfaz que proporciona un mecanismo de bloqueo de hilos (también conocido como bloqueo de exclusión mutua) para controlar el acceso a recursos compartidos en entornos de programación multihilo.

Un objeto Lock actúa como un monitor de exclusión mutua que permite que solo un hilo acceda a un recurso compartido a la vez, mientras que los demás hilos deben esperar hasta que se libere el bloqueo.

La interfaz Lock proporciona métodos como "lock()" y "unlock()" para adquirir y liberar un bloqueo, respectivamente. Además, también proporciona métodos para intentar adquirir un bloqueo, que se pueden utilizar para evitar que un hilo se bloquee indefinidamente si no puede adquirir un bloqueo.

Lock también puede ser utilizado para implementar patrones de sincronización más complejos que no son posibles con la palabra clave "synchronized" de Java. Por ejemplo, se puede usar Lock para implementar bloqueos justos (donde los hilos se adquieren el bloqueo en el mismo orden en que lo solicitaron) y bloqueos reentrantes (donde un hilo puede adquirir el mismo bloqueo varias veces sin bloquearse).

Se puede obtener una implementación de Lock instanciando ReentrantLock, ReadLock o WriteLock.
-	Lock: Bloquea el acceso al código a otros hilos
-	Unlock: Desbloquea el acceso al código.

### Colecciones para concurrencia

Las colecciones para la concurrencia en Java son una serie de clases que se utilizan para manejar y procesar datos de manera segura en entornos concurrentes. Estas colecciones están diseñadas específicamente para ser utilizadas en aplicaciones en las que varios hilos acceden y manipulan los mismos datos al mismo tiempo

-	ConcurrentMap: Subinterfaz de Map que garantiza operaciones thread safe en un entorno multitarea. Su principal implementacion es ConcurrentHashMap. Utiliza una técnica de segmentación para dividir el mapa en múltiples segmentos, cada uno de los cuales puede ser bloqueado de forma independiente para permitir un acceso concurrente seguro. Además, se utiliza un mecanismo de bloqueo de grano fino para garantizar que solo un hilo pueda modificar un segmento en un momento dado.
-	CopyOnWriteArrayList: Variable de ArrayList para entornos de thread safe. Esta colección garantiza que las operaciones de lectura sean seguras sin necesidad de utilizar técnicas de bloqueo, ya que se crea una copia de la lista cada vez que se realiza una operación de escritura. De esta manera, los hilos pueden leer la lista sin preocuparse por las modificaciones que se están realizando al mismo tiempo
-	CopyOnWriteArraySet: Variante de HasSet para entornos thread safe. Internamente utiliza un CopyOnWriteArrayList para realizar las operaciones.

# Atomic

La clase Atomic en Java se refiere a un conjunto de clases que proporcionan operaciones atómicas, es decir, operaciones que se ejecutan como una sola unidad indivisible y no pueden ser interrumpidas por otras operaciones. Estas clases se utilizan para garantizar la integridad de los datos en entornos de concurrencia, donde varios hilos de ejecución pueden acceder y modificar los mismos datos al mismo tiempo (thread-safe).

La clase Atomic proporciona varios tipos de variables que pueden ser utilizadas de manera segura en entornos de concurrencia, tales como AtomicBoolean, AtomicInteger, AtomicLong, AtomicReference, entre otros. Cada uno de estos tipos de variables proporciona métodos para realizar operaciones atómicas, como incrementar o reducir un valor, cambiar el valor actual, comparar y establecer valores, y más. Utilizan internamente variables volatile (acceso directo a memoria) para garantizar la integridad de los datos.

El uso de estas clases puede mejorar el rendimiento y la escalabilidad de aplicaciones que tienen que manejar concurrencia, ya que evitan la necesidad de sincronización manual en el código.

## AtomicInteger/AtomicLong
Adecuada para aplicaciones de tipo contador global
Sus principales métodos son:
-	incrementAndGet: Incrementa el contador interno y devuelve su valor.
-	decrementAnGet: Disminuye el contador interno y devuelve su valor.
-	Int addAndGet(int delta):  Añade el valor especificado a la variable interna y devuelve el valor de la misma.
-	Get: Devuelve el valor actual del contador.

## AtomicBoolean
Adecuada para ser utilizado como flag o indicador global.

Sus principales métodos son:
-	Set(boolean new value): Establece el nuevo valor al indicador.
-	Get: Devuelve el valor actual del indicador.
-	compareAndSet(boolean expeted, boolean newValue): Si el valor actual es igual a expected, se asigna newValue como valor actual.
 
# CyclicBarrier

Clase que permite que un grupo de threads se sincronicen en un punto de control determinado, esperando uno al otro antes de continuar con su ejecución. Una vez que todos los threads han alcanzado el punto de barrera, se liberan y pueden continuar ejecutándose.

CyclicBarrier se puede utilizar en una variedad de situaciones en las que se necesita sincronización entre threads, como en problemas de paralelismo y concurrencia en los que se desea que varios threads trabajen en paralelo en tareas independientes y luego esperen a que se completen todas las tareas antes de continuar.

CyclicBarrier se crea mediante la instancia de la clase CyclicBarrier y se puede inicializar de dos maneras:
-	CyclicBarrier(int hilos): Crea un CyclicBarrier que permite sincronizar el numero de hilos indicados en el constructor.
-	CyclicBarrier(int hilos, Runnable action): Cuando todos los hilos alcanzan la barrera, se ejecuta la acción indicada en el segundo parámetro del constructor.

La sincronización de los hilos se realiza a través del método await() de la clase. Cuando un hilo llama a este método, queda en espera en ese punto. Cuando el total de hilos que han realizado la llamada a await es igual al valor indicado en el constructor, se librean todos los hilos y se ejecuta el Runnable. El contador vuelve a poner a 0 tras alcanzar todos los hilos de la barrera.

# Localización e Internalización

Consiste en desarrollar aplicaciones para múltiples idiomas y adaptadas a determinadas localizaciones geográficas. Los textos se incluyen en archivos de recursos que son cargados dinámicamente en tiempo de ejecución.
La clase Locale permite establecer la localización geográfica e idioma con el que se va a trabajar.

## Archivos de recursos

Para cada idioma, se creara un archivo de texto .properties con parejas clave = valor que incluyan los diferentes textos a mostrar. Todos los códigos de prefijo según norma ISO 639-1. Nombrearchivo_prefijo.properties -> mensajes_es.properties ; mensajes_en.properties

## Clase Locale

Es una clase que se utiliza para representar información sobre una región geográfica, como el idioma y la ubicación. Esta clase proporciona una manera de especificar la configuración regional para la internacionalización de aplicaciones Java. Se puede utilizar para representar diferentes configuraciones regionales, como idioma, país y variante. Por ejemplo, la configuración regional "en_US" representa el idioma inglés y los Estados Unidos como el país.

Se puede crear un objeto Local con los constructores:
-	Locale (idioma)
-	Locale(String idioma, String pais).
-	Locale(String idioma, String país, String variante).

Se pueden usar las constantes de Locale como Locale.US, Locale.CANADA…
En caso de no querer usar la configuración por defecto del idioma detectada por el propio programa, podemos modificarla usando el método estático setDefgault donde le pasaremos el Local que queramos que sea por defecto.

Para poder realizar la carga de un recurso asociado con una determinada localización debemos crear un objeto ResouirceBundle y para poder obtener los textos usaremos el metodo getString(String clave). En caso de no existir el archivo para la localización indicada, intenta el de la localización por defecto, sino el predeterminado (sin prefijo).

# Formateado de datos

Se refiere a la manipulación de cadenas de texto para que se presenten de una manera específica y legible.

Para el formateo de fechas y números se usan las siguientes clases:
-	NumberFormat: Establece un formato para numero.
-	DateFormat: Permite formatear fechas.
-	SimpleDateFormat: Subclase de DateFormat.
- DateTimeFormatter: Formateado de nuevas clases de fecha.
  
# Pautas para codificación segura

Son un conjunto de reglas que evitan efectos indeseados ante posibles ataques externos. Se organizan en nueve secciones
-	Denegación de servicio
-	Confidencialidad.
-	Inyección e inclusión
-	Accesibilidad
-	Validación de datos
-	Mutabilidad
-	Construcción de objetos
-	Serialización
-	Control de acceso.

## Denegación del servicio

Comprobar la entrada de datos en un sistema para evitar que causen un consumo excesivo de recursos y que pueda afectar a la CPU o la memoria.
Liberar recursos en todas las situaciones.
Sistema robusto de gestiones de error y excepciones.

## Confidencialidad

Los datos confidenciales solo deberían ser visibles dentro de un contexto limitado.
Eliminar información sensible de volcado de errores.
No realizar registros de log de información sensible.
Considerar eliminar información sensible de la memoria después de su uso.

## Inyección

Es la inserción de código maligno en las peticiones sobre nuestra aplicación, la inyección más conocida es la SQL. Para evitar la inyección SQL usaremos la interfaz PreparedStatement.
Evitar la inyección de valores excepcionales en un punto flotante (validación de datos antes de enviar la petición).

## Accesibilidad

Limitar la accesibilidad de clases, métodos y atributos al mínimo requerido por nuestro código.
Limitar la extensiblidad de clases y métodos. Para evitar herencias y sobrescrituras malicisas, debemos definirlos como final. Si una clase debe usar otra, preferible composión a herencia.
Evitar cambios en una super clase para que las subclases no se vean afectadas.

## Validación de datos

Validar siempre datos de entrada, a fin de evitar que puedan alterar el flujo de nuestro código o corromper el estado de objetos.
No se debe confiar solo en la validación del lado cliente.
Definir envoltorios alrededor de métodos nativos.

## Mutabilidad

Crear copias de valores de salida mutables. Cuando un método devuelve un dato que es mutable, preferible devolver una copia.
No exponer colecciones modificables.
Definir atributos públicos estáticos como finales. 

## Construcción objetos

Evitar constructores públicos de clases sensibles.
No establecer valores de atributos en el constructor, hasta que todas las comprobaciones se hayan realizado.
Evitar desde los constructores llamadas a métodos que pueden ser sobrescritos.

## Serialización

Evitar la serialización de clases sensibles.
Proteger datos sensibles durante la serialización.
Evitar serializar determinados datos durante el proceso de serialización, definiéndolos como transient.
Ser conscientes de que, durante el proceso de deserialización, se crea un objeto de la clase sin invocar a constructor alguno.

## Control de acceso

Invocaciones seguras mediante doPrivileged (permite la lectura y escritura de propiedades y ubicaciones que normalmente no se pueden).

# Novedades en versiones posteriores a Java 11

Se incorporan los siguientes tópicos/objetivos en este examen, correspondientes a novedades introducidas desde java 12 a java 17
-	Mejoras en instrucciones switch
-	Bloque de texto
-	Coincidencia de patrones en instance of
-	Records
-	Clases e interfaces sealed
-	Manipulación de fechas con java.time

## Instrucción switch

Múltiples valores en case.
Desde la versión Java 14, la clausula case de un switch puede incluir varios valores separados por “,”
Al igual que un case simple, lo valores del case múltiple deben ser literales, constantes o tipos enumerados.
Ejemplo case 2, 3, 4

### Expresiones switch

Desde java 14, es posible utilizar la instrucción switch para devolver un resultado en una expresión.
Ejemplo 
```java 
String resultado = switch (nota){ case 1, 2, 3, 4 -> “Suspenso”;};
```

### Sintaxis expresiones switch

Se utiliza -> en lugar de “:” para indicar las instrucciones de cada bloque case.
Si hay más de una instrucción, se delimita por llaves y el valor se devuelve mediante la instrucción yield:
No se utiliza la instrucción break.
Es obligatorio el uso de default, salvo que estén contemplados todos los posibles valores en los case.

## Bloques de texto

Es posible representar un texto que contenga caracteres especiales, como saltos de línea y comillas, delimitándolo entre tripes comillas “””y”””.
Es muy útil, por ejemplo, para JSON.
Se representan todos los caracteres der la cadena, incluidos saltos de línea.
Importante, el delimitador de inicio en línea debe der ser independiente.

### Espacios

En bloques de texto multilínea, los espacios antes del salto de línea son eliminados automáticamente, a no ser que se indiquen explícitamente (carácter \s).
Si no queremos que se introduzca un salto al final de cada línea, se utilizara el símbolo (\)
No podrá indicarse ningún carácter después de dicho símbolo.

### Indentación

En java 12 la clase String incorpora el método indent(int) para añadir espacios en una cadena.
Añade tantos espacios al principio de cada línea como se indiquen en el número, si ese es negativo los elimina.
Incluye un salto de línea final si no existe.

### StripIndent

Método incorporado a la clase String en java 15 que, tras una concatrenacion, elimina los espacios existentes antes de un salto de línea.

## Coincidencias de patrones con instanceof

Es un operador que se utiliza para comprobar si un objeto es de un determinado tipo. El operador devuelve un valor booleano que indica si el objeto dado es una instancia de la clase especificada, o una instancia de una subclase de la clase especificada. En caso de no existir una relación de herencia entre el tipo del objeto y la clase indicada como segundo operador, se dará un error de compilación.
Desde Java 16 se puede realizar instanceof para asignar el objeto a una variable del tipo específico, sin realizar un cast.

```java
If(obj instanceof String s) sysout(s.length());
```

## Records

Es un tipo de dato introducido en la versión 16 de Java, que se utiliza para representar datos inmutables en forma de objetos. Un record se define mediante la palabra clave "record" seguida del nombre del tipo y una lista de campos separados por comas.

Los records se utilizan para representar datos que tienen un conjunto fijo de campos y que no cambian después de su creación. Los registros son inmutables por defecto, lo que significa que una vez creados, no se pueden modificar sus campos, no puede ser heredado y no pueden heredar ninguna clase existente.

Además de los campos, un registro también puede tener constructores, métodos y otros elementos típicos de una clase en Java. Los registros son una alternativa a las clases de Java para representar datos inmutables, pero se diferencian en que se diseñan para tener menos verbosidad y para ser más fáciles de escribir y leer que las clases convencionales.

Genera de forma automática:
-	Los atributos de la clase
-	La implementación del constructor
-	Métodos para recuperación de valores
-	Implementación de toString y equals

### Constructor compacto

Es una forma abreviada y más concisa de definir un constructor para una clase. Este tipo de constructor se utiliza comúnmente con los "records" en Java, aunque también puede ser utilizado en otros tipos de clases.
El constructor compacto permite inicializar los campos de una clase de manera más sencilla y legible, ya que evita tener que escribir el código de asignación para cada campo en una línea separada. Además, cuando se utilizan "records" en Java, el constructor compacto se genera automáticamente a partir de los campos de la clase, lo que reduce aún más la cantidad de código necesario.

### Sobrecarga de constructores

Se pueden incluir constructores adicionales, pero siempre tendrán que llamar al canónico (creado por defecto).

## Sealed clases

Una clase sellada (sealed class) es una clase que se define con una restricción sobre las subclases que se pueden crear. En otras palabras, una clase sellada especifica qué clases pueden ser subclases directas de ella y, por lo tanto, restringe la jerarquía de herencia de la clase.

Para declarar una clase sellada en Java, se utiliza la palabra clave "sealed" antes de la palabra clave "class", seguida de la lista de clases permitidas para heredar de esta clase.
-	Las subclases, deben ser declaradas como non-sealed, sealed o final.
-	Todas las clases implicadas deben formar parte del mismo modulo o, en caso de ser módulos anónimos, deben de estar en el mismo paquete.
-	Cada clase permitida, debe extender directamente la sealed class.
-	Las subclases deben ser definidas obligatoriamente con alguno de los modificadores: non-sealed, sealed, final.
-	Si una subclase permitida se define como non-sealed, todas las subclases de esta tendrían acceso a la clase base.
-	Sealed también puede ser aplicado a interfaces, permitiendo la herencia e implementación solo a ciertas interfaces y clases. 
-	En el caso de una interfaz permitida esta solo podrá ser declarada como non-sealed o sealed, nunca final.
 
## Manipulación de fechas con java.time

Desde java 8, se incluyen las siguientes clases en java.time, para la manipulación de fechas y horas.
No disponen de constructores públicos.
Se crean a través del métodos estáticos (of).
Los valores erróneos provocarían una excepción.
-	LocalDate: Manipulación de fechas, formato local.
-	LocalTime: Manipulación de horas.
-	LocalDateTime: Manipulación de fechas más horas.
-	ZonedDateTime: Manipulación de fechas y horas en zona horaria.
-	Instant: Instante de tiempo concreto.
-	Period: Manipulación de periodo de tiempos.
-	Duration: Manipulación de periodo de horas.

Se pueden crear objetos de fecha-hora, a partir de una cadena de caracteres con el formato estándar de fecha/hora. Si la cadena tiene un formato incorrecto se produce una excepción de tipo DateTimeException (por defecto la fechas son yyyy-MM-ddTHH:mm:ss). Aunque se puede indicar que la cadena tiene un formato especifico usando DateTimeFormatter.ofPattern
Para manipular las calses anterirores, disponemos de métodos para obtener una nueva fecha resultante de la suma-resta de una cantidad. Estos métodos no modifican el valor original, dado que los objetos son inmutables ya que retornan un valor.

La clase instant se encarga de representar un momento de tiempo concreto en la zona GMT, se pueden crear a partir de un ZonedDateTime.

La clase Period representa un periodo de tiempo, medido en años, meses y días, se pueden sumar/restar periodos de tiempo a objetos de fecha, pero no a LocalTime (UnsupportedTemporalTypeException). Mediante el método estático between de Period se puede obtener el intervalo de tiempo entre dos fechas en formato Period. Únicamente puede utilizarse con objetos LocalDate.

La clase duration, representa un intervalo de tiempo medido en horas, minutos, segundos. Se puede sumar/restar duraciones a objetos de hora, pero no a objetos LocalDate. Mediante el método estático between de Duration se puede obtener el intervalo de tiempo entre dos fechas en formato Duration. Se puede utilizarse con objetos que contengan datos de hora.

Los cambios de hora se tienen en cuenta la manipulación de objetos ZonedDateTime. 