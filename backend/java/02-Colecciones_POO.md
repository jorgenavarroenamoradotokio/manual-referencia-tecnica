<div align="center">
  <img src="../../assets/java_logo.svg">
</div>

# Índice

- [Índice](#índice)
- [Introducción](#introducción)
- [Programación Orientada a objetos](#programación-orientada-a-objetos)
  - [Métodos.](#métodos)
    - [Paso de parámetros](#paso-de-parámetros)
  - [Miembros estáticos](#miembros-estáticos)
  - [Variables y bloques estáticos](#variables-y-bloques-estáticos)
  - [Constructores](#constructores)
  - [This](#this)
  - [Modificadores de acceso](#modificadores-de-acceso)
  - [Encapsulación](#encapsulación)
  - [Clases abstractas](#clases-abstractas)
  - [Método abstracto vs final](#método-abstracto-vs-final)
  - [Interfaces](#interfaces)
    - [Interfaces posteriores a Java 8 y 9](#interfaces-posteriores-a-java-8-y-9)
  - [Herencia](#herencia)
    - [Herencia de Object](#herencia-de-object)
    - [Los constructores por herencia.](#los-constructores-por-herencia)
    - [Sobreescritura de métodos](#sobreescritura-de-métodos)
    - [Uso de protected](#uso-de-protected)
    - [Instancias por referencia.](#instancias-por-referencia)
  - [Clases anidadas](#clases-anidadas)
  - [Enumeraciones](#enumeraciones)
  - [Clases Genéricas](#clases-genéricas)
  - [Clases Anónimas](#clases-anónimas)
- [Arrays y Colecciones](#arrays-y-colecciones)
  - [Arrays unidimensionales y multidimensionales](#arrays-unidimensionales-y-multidimensionales)
  - [Genéricos](#genéricos)
    - [Iterables](#iterables)
    - [Collection](#collection)
    - [Listas](#listas)
    - [Tablas](#tablas)
      - [TreeMap](#treemap)
    - [Conjuntos](#conjuntos)
    - [Colas dobles (Cola y pila)](#colas-dobles-cola-y-pila)
  - [Ordenar arrays y listas](#ordenar-arrays-y-listas)
    - [La interfaz comparable](#la-interfaz-comparable)
    - [La interfaz Comparator](#la-interfaz-comparator)
    - [Búsqueda binaria](#búsqueda-binaria)
- [Entrada/Salida](#entradasalida)
  - [java.io](#javaio)
    - [Escritura por consola](#escritura-por-consola)
    - [Escritura a ficheros](#escritura-a-ficheros)
      - [Métodos principales de  FileWriter](#métodos-principales-de--filewriter)
    - [Metodos principales BufferedWriter](#metodos-principales-bufferedwriter)
      - [Entrada](#entrada)
      - [Lectura por teclado](#lectura-por-teclado)
      - [Lectura de fichero](#lectura-de-fichero)
  - [java.nio](#javanio)
    - [Inertfaz Path](#inertfaz-path)
- [Clase Files](#clase-files)
- [Excepciones. Conceptos y tipos](#excepciones-conceptos-y-tipos)
  - [Clasificación](#clasificación)
  - [Errores](#errores)
    - [Captura de excepciones](#captura-de-excepciones)
  - [Métodos de exception](#métodos-de-exception)
  - [Lanzamiento y propagación de excepciones](#lanzamiento-y-propagación-de-excepciones)
  - [Excepciones personalizadas](#excepciones-personalizadas)
  - [Try con recursos](#try-con-recursos)
  - [Interfaz AutoCloseable](#interfaz-autocloseable)
- [Anotaciones](#anotaciones)
  - [Metaanotacion Target](#metaanotacion-target)
  - [Metaanotacion Retention](#metaanotacion-retention)
  - [Metaanotacion Repetable](#metaanotacion-repetable)
  - [Metaanotacion SuppressWarnings](#metaanotacion-suppresswarnings)
  - [Metaanotacion Override](#metaanotacion-override)
  - [Metaanotacion Deprecated](#metaanotacion-deprecated)
  - [Metaanotacion SafeVarargs](#metaanotacion-safevarargs)

# Introducción

El nivel intermedio te sumerge en el paradigma central de Java: la Programación Orientada a Objetos (POO). Este documento detalla conceptos cruciales como el uso de Clases, Métodos y Constructores, y los pilares de la POO: Encapsulación, Herencia, Polimorfismo y Abstracción (a través de clases abstractas e interfaces). Además, aprenderás a gestionar colecciones de datos de forma eficiente, a manejar errores de tiempo de ejecución con Excepciones, y a interactuar con el sistema de archivos mediante la Entrada/Salida (java.io y java.nio).

# Programación Orientada a objetos

## Métodos.
Son funciones que se encargan de realizar una tarea. Pueden recibir parámetros y devolver un resultado.

Su estructura es (visibilidad) modificador tipo de retorno (si no retorna nada será void) nombre del método(parámetros) {}.

Los métodos se definen dentro de clases, para llamarlo se debe de crear un objeto de la clase y utilizar la sintaxis objeto.metodo(argumentos). En caso de que el método que queramos usar está dentro de la misma clase no es necesario crear un objeto.

Un método se puede sobrecargar, que quiere decir esto, que podemos tener el mismo método, pero con diferentes parámetros de entrada (en cantidad o tipo). El tipo de devolución no afecta en la sobrecarga, puede ser el mismo o diferente. 

Cuando hay varios posibles métodos que se pueden ejecutar con la llamada, primero se intenta obtener una coincidencia exacta, después promoción de tipos (por ejemplo, de int buscar long) y en último lugar autoboxing.

### Paso de parámetros

Al pasar un tipo primitivo a un método, estamos pasando una copia del dato, si el método modifica su contenido, solo afecta a la copia no al original. Al pasar un tipo objeto a un método, estamos pasando la referencia del objeto, esto quiere decir que si modificamos algún dato tanto la copia como el original se actualizara la información, para el caso de los String no funciona igual ya que son inmutables.
 
## Miembros estáticos

Los métodos estáticos (también conocidos como métodos de clase) son aquellos que pertenecen a una clase en particular en lugar de pertenecer a una instancia (objeto) de la clase. Estos métodos son llamados "estáticos" porque su comportamiento y resultado son predecibles y no dependen del estado de los objetos creados a partir de la clase.

Los métodos estáticos se pueden utilizar para realizar cálculos, manipulaciones de datos o cualquier otra tarea que no dependa del estado actual de los objetos de la clase. Debido a que no dependen del estado de los objetos, los métodos estáticos no tienen acceso a las variables de instancia y no pueden hacer referencia al operador "this" en el cuerpo del método.

Un método estático solo puede llamar a métodos y atributos que también sean estáticos (no se pueden usar en su interior ni this ni super).

Para llamar a un método estático, no es necesario crear una instancia de la clase. En su lugar, el método se llama directamente en la clase, seguido del nombre del método y cualquier argumento que se requiera, aunque se puede usar con una instancia de la clase. Se declaran con la palabra static.

## Variables y bloques estáticos

Las variables estáticas compartidas por todos los objetos de la clase, se definen con la palabra static. Todos los objetos inicializados comparten el mismo valor.
Los bloques estáticos se ejecutan una vez durante la vida de una clase, solo pueden acceder a otros miembros estáticos.

## Constructores

Un constructor es un método especial que se llama automáticamente cuando se crea una instancia (objeto) de una clase. El constructor se utiliza para inicializar los valores de los atributos de la clase cuando se crea un objeto de esa clase.

Cuando creamos un objeto no es necesario definir un constructor, ya que de forma explícita en una clase el compilador agrega uno por defecto, que no tiene parámetros y tampoco ninguna instrucción. Pero si se define explícitamente un constructor, el compilador no crea el constructor por defecto.

Los constructores tienen el mismo nombre que la clase y no tienen tipo de retorno. Pueden tener parámetros o no, y se pueden sobrecargar (tener varios constructores con diferentes parámetros).

Un constructor puede llamara a otro constructor de la misma clase utilizando la expresión this(argumentos), debe de ser la primera instrucción del constructor.

Se pueden definir bloques de inicialización de instancia. Son bloques de código que se ejecutan cada vez que se crea un objeto de la clase, antes del constructor, se delimita por llaves.

## This

"this" es una palabra clave que se utiliza dentro de una clase para hacer referencia al objeto actual (la instancia de la clase en la que se está trabajando).

La palabra clave "this" se utiliza principalmente en dos situaciones:
Para referirse a un atributo o método de la clase actual: Cuando hay un atributo o método con el mismo nombre que un parámetro local, se puede utilizar "this" para hacer referencia al atributo o método de la clase actual.

Para llamar a otro constructor de la misma clase: Cuando una clase tiene varios constructores, se puede utilizar "this" para llamar a otro constructor de la misma clase.

## Modificadores de acceso

Los modificadores de acceso determinan la visibilidad de una clase y sus miembros.

<table>
  <tr>
    <th>Public</th>
    <hd>Protected</th>
    <th>Default</th>
    <th>Private</th>
  </tr>
  <tr>
    <td>SI</td>
    <td>NO</td>
    <td>SI</td>
    <td>NO</td>
  </tr>
  <tr>
    <td>SI</td>
    <td>SI</td>
    <td>SI</td>
    <td>SI</td>
  </tr>
  <tr>
    <td>SI</td>
    <td>SI</td>
    <td>SI</td>
    <td>SI</td>
  </tr>
  <tr>
    <td>SI</td>
    <td>SI</td>
    <td>SI</td>
    <td>SI</td>
  </tr>
</table>

- Public
Si una clase o miembro de la misma es public, puede utilizarse desde cualquier clase que esté en su mismo paquete o en cualquier otro. Es poco común ver que los atributos sean públicos ya que no cumplirían la encapsulación, solo son públicos si se trata de constantes.

-	Default
Es el ámbito que se aplica cuando no se indica ningún modificador. El elemento que lo lleve solo será visible desde clases de su mismo paquete.

- Private
Solo es accesible desde el interior de la clase. Muy habitual en atributos para encapsulación.

## Encapsulación

Principio que se basa en mantener como privados los atributos que definen características de un objeto, proporcionando acceso a los datos a través de métodos y constructores, evitando así corromper los objetos.

Se accede a los atributos mediante los métodos getter y setter y mediante el constructor permite inicializar los atributos durante la creación del objeto.
 
## Clases abstractas

Es una clase que cuenta, al menos, con un método abstracto, que es aquel que esta declarado en la clase, pero no implementado. Las clases abstractas se definen con la palabra reservada abstract. 
Las clases abstractas tienen una serie restricciones, estas son:
- No es posible crear objetos de una clase abstracta
-	Pueden incluir atributos, constructores, métodos estándar aparte de los métodos abstractos.
-	Una clase que herede una clase abstracta esta obligada a sobrescribir los métodos
abstractos heredados (o declararse también como abstract).
-	El objetivo de los métodos abstractos es forzar a que todas las subclases tengan el mismo
formato de método.

## Método abstracto vs final

Un método final es lo contrario a un método abstracto, ya que un método final es aquel que no puede ser sobrescrito, ya que utiliza la palabra reservada final.

## Interfaces

Una interfaz es un conjunto de métodos abstractos y su objetivo es definir el formato de ciertos métodos, que posteriormente las clases se encargan de implementar. También puede incluir constantes que serán públicas y estáticas. Aunque no se especifique los métodos puede ser abstractos y públicos., en el caso de las constantes se omiten las palabras public final y static.

Las interfaces se definen usando la pablara reservada interface. Todas las clases que implemente una interfaz está obligada a sobrescribir(implementar) todos los métodos de la misma. Para implementar una interfaz deberemos de usar la palabra reservada implements.

Las interfaces nos dan una flexibilidad enorme ya que podemos implementar varias interfaces o heredar de una clase padre que implemente una o varias interfaces. 

Además, una interfaz puede heredar de otra interfaz. En caso de que una clase la implemente tendrá que sobrescribir todos los métodos de las interfaces que herede dicha interfaz.
Todos los métodos de la interfaz deben de ser públicos, en caso de no estar definida la palabra public su comportamiento por defecto es public.

### Interfaces posteriores a Java 8 y 9

Las nuevas versiones de java han proporcionado una implementación por defecto, que puede ser utilizada por las clases que implementan la interfaz, estos métodos se definen usando la palabra reservada default. Se usan para métodos genéricos que no queremos que las clases que la implementen tengan que volver a realizarlo, pero en caso de que no se desee este funcionamiento se puede sobrescribir.

Existe un problema de herencia múltiple, este caso se da cuando tu clase implementa dos interfaces con dos métodos default iguales en cada interfaz, esto va a provocar un error de compilación, para solventarlo deberemos de sobrescribir el método en nuestra clase.

Se pueden definir métodos estáticos en las interfaces, pero no están disponibles en la clase que implementa (sobrescribir) la interfaz y no podemos llamarlo con la propia clase ni con la instancia, solo puede llamarse usando la propia interfaz.

Se pueden definir métodos privados en las interfaces. Esta funcionalidad se aplica principalmente para dar soporte a los métodos default que tiene nuestra interfaz.
Interfaces funcionales

Las interfaces funcionales son aquellas interfaces que solo poseen un método abstracto, lo curioso de esta nueva funcionalidad es la implementación de las mismas sin necesidad de crear clases, sino a través de expresiones lambda. Para detectar que nos encontramos ante una interfaz funcional deberemos de buscar la anotación @FunctionalInterface (no es obligatorio).

Si una interfaz cuenta con métodos que heredan de la clase objeto no cuentan para determinar si una interfaz es funcional o no. 

## Herencia

La herencia es un concepto fundamental de la programación orientada a objetos que permite crear nuevas clases basadas en clases existentes. En la herencia, una clase de hija (subclase) hereda características y comportamientos de una clase padre (superclase), ya que esta primera puede utilizar todos los campos y métodos de su clase padre, además de poder agregar nuevos campos y métodos o sobrescribir (modificar) los que ya existen.

La herencia en java se implementa utilizando la palabra clave extends, debemos de tener en cuenta que solo se puede heredar de una sola clase, aunque una superclase puede heredar a su vez a otra y así hasta n niveles, creando una jerarquía de clases. Por otro lado, solo se podrá usar el concepto de herencia en aquellas clases que no sean final.

A la hora de la privacidad una hija nunca va a poder ver los miembros privados de la superclase.

### Herencia de Object

Por defecto java aplica a la hora de crear objeto la herencia de la clase Object de manera directa o indirectamente. Como se aplica este concepto de la siguiente manera. Si la clase no hereda explícitamente de otra clase implícitamente heredará de Object. Esta herencia nos permite el uso de los métodos toString, equals y hashCode.

### Los constructores por herencia.

Todas las clases incluyen de forma implícita en sus constructores como primera línea de código la instrucción super();, que es una línea de ejecución que permite realizar la llamada al constructor de la clase padre en la clase hija. 

Podemos seleccionar a que constructor padre podemos ejecutar usando la instancia super y le pasamos el número de parámetros que necesite con su tipo correspondiente.

### Sobreescritura de métodos
Es un concepto importante de la programación orientada a objetos que permite a una clase hija proporcionar una implementación diferente para un método que ya esta definido en su clase padre.

A la hora de sobrescribir un método deberemos de seguir una serie de normas:
-	se debe de definir un método con el mismo nombre, parámetros y tipo de retorno del método
-	debe poseer el mismo modificador de acceso o más permisivo (menos restrictivo).
-	La nueva implementación no debe de propagar ninguna excepción que no estén definidas en el original (no afecta a las excepciones Runtime)

Para que el compilador detecte esta nueva implementación tenemos que usar la anotación @Override.

### Uso de protected

El modificador de acceso protected puede utilizarse en la declaración de atributos y métodos. Si uno de estos elementos se declara como protected, significa que es accesible desde cualquier clase de su mismo paquete y de sus subclases, independientemente de donde estas se encuentren. Por tanto, el modificador protected establece una visibilidad a los miembros de una clase que es superior a la default (ámbito de paquete), pero inferior a la public. El acceso desde una subclase a un miembro protected de la superclase se debe hacer siempre dentro del contexto de la herencia.

Sin embargo, si desde una subclase que se encuentre en otro paquete distinto a p1 creamos un objeto de la clase Prueba, no tendremos acceso a los miembros protegidos a través de este objeto. Esto es lo que significa que el acceso solo sea a través del contexto de la herencia.
Instancias por referencia.

### Instancias por referencia.

La instancia por referencia por herencia en Java se refiere a la creación de un objeto de una subclase y asignar una referencia a ese objeto a una variable de referencia de la clase padre. En otras palabras, se crea un objeto de una subclase y se asigna a una variable de referencia de la clase padre, lo que permite que el objeto de la subclase se trate como un objeto de la clase padre.

La instancia por referencia por herencia es útil cuando se quiere utilizar una clase padre como tipo de referencia para objetos de sus subclases, lo que permite una mayor flexibilidad y modularidad en el diseño del programa. Además, esto también facilita la implementación de polimorfismo en Java.

Tendremos que tener en cuenta que el compilador permite a ver casting der una referencia de un tipo a cualquier tipo de sus subclases, pero si el objeto no es de ese tipo se producirá una ClassCastException

## Clases anidadas

En Java, una clase anidada es una clase que se define dentro de otra clase. Las clases anidadas pueden ser de dos tipos: clases internas y clases estáticas anidadas.

Clases internas (Inner classes): Son clases que se definen dentro de otra clase y pueden tener acceso a los miembros (atributos y métodos) de la clase que las envuelve, incluso a los miembros privados. Las clases internas se utilizan principalmente para encapsular la implementación de una clase dentro de otra, y se pueden dividir en cuatro tipos:

-	Clases internas regulares (Member inner classes): Son clases que se definen como miembros de una clase y están asociadas a una instancia de la clase que las envuelve. Pueden acceder a todos los miembros de la clase que las envuelve, incluyendo los miembros privados.
A la hora de instanciar la clase se realiza de la siguiente forma: 
Externa ext = new Externa();
Externa.Interna inter = new ext.new Interna();

-	Clases internas estáticas (Static nested classes): Son clases internas que se definen con la palabra clave static y no están asociadas a una instancia de la clase que las envuelve. Pueden ser accedidas directamente desde la clase que las envuelve, sin necesidad de crear una instancia de la clase externa. A la hora de instancia la clase se realiza de la siguiente forma: Externa.Interna inter = new Externa.Interna();

-	Clases internas locales a métodos: Son clases que se definen dentro de un método o un bloque de código, y solo son accesibles dentro de ese método o bloque de código. Son útiles cuando se necesita una clase que sea local a un método específico, solo tiene acceso a variables que sean finales.

-	Clases internas anónimas (Anonymous inner classes): Son clases internas que se definen sin un nombre y se crean y se instancian al mismo tiempo en que se necesitan. Son útiles para implementar interfaces o clases abstractas de forma rápida y concisa.

Clases estáticas anidadas (Static nested classes): Son clases anidadas que se definen con la palabra clave static y no están asociadas a una instancia de la clase que las envuelve. Son similares a las clases internas estáticas, pero no pueden acceder a los miembros no estáticos de la clase que las envuelve.

Las clases anidadas en Java proporcionan una forma de organizar y encapsular la lógica relacionada en una misma unidad de código, y se utilizan en situaciones específicas donde se requiere una relación cercana entre las clases.
 
## Enumeraciones

Una enumeración (enum) es un tipo de dato especial que permite definir un conjunto fijo de constantes con nombre en un tipo de dato enumerado. Una enumeración en Java se define usando la palabra clave enum y puede contener un conjunto de constantes llamadas "valores enumerados" o "elementos enumerados". Son tipos de datos estáticos y final, lo que significa que las constantes enumeradas son inmutables y no se pueden cambiar una vez que se definen. Las enumeraciones se utilizan comúnmente para representar un conjunto fijo de opciones o valores posibles en un dominio específico.

Las variables de tipo enumerado se pueden utilizar con el operador == para comprobar la igualdad. También pude utilizar en un switch.

Existen enumeraciones compuestas, estas enumeraciones son aquellas que almacenan mas de un dato, para ello se usan los constructores (que son de ámbito privado)
Los enumerados cuentas con métodos propios como:
-	Values(). Método estatico que devuelve un array con todos los valores de la enumeración.
-	Name(). Cadena de caracteres con el nombre del valor.
-	Ordinal(). Posicion del valor dentro de la enumeración, siendo 0 la posición del primero.
-	toString(). Devuelve el mismo resultado que name().

## Clases Genéricas

La programación genérica tiene como objetivo facilitar el desarrollo de algoritmos (o métodos en la POO) de manera tal que el tipo de datos especifico manipulado por el algoritmo sea especificado al momento de ejecutarlo y no al momento de desarrollarlo.
-	Se decalran en clases abstractas o interfaces
-	Pdemos especificar que los tipos extienda de una interfaz con T extends myInterfaces
-	La convención para nombrar los parámetros de tipo es
  *	E – Elemento
  *	K – Llave
  *	N – Numeros
  *	T – Tipo
  *	V – Valor

## Clases Anónimas

Una clase anónima es Java es una solución rápida para implementar una clase abstracta o una interface que solo se va a usar una vez sin necesidad de crea un archivo separado

# Arrays y Colecciones

Conjuntos de datos de un misto tipo a los que se les accede mediante una única variable. Cada dato tiene asociado un índice dentro del array empezando por la posición 0. 

## Arrays unidimensionales y multidimensionales

Un array es una estructura de datos estática una vez definido su tamaño no se puede modificar. Los arrays se declaran de la siguiente manera tipoDato[posiciones] nombre.
Un array se crea como cualquier objeto a través del operador new, indicando entre corchetes el tamaño.
```java
int [] s = new int [20]; // Cada posición del array se inicializa con el valor por defecto (0) o null.
Int [] datos:
int vals [];
```

Para acceder al contenido de una posición se le indica entre corchetes el índice del elemento

El tamaño de un array se obtiene usando el método length, pero la última posición de este será array.lenght -1.

Los array se recorren usando estructuras repetitivas como for y foreach.
Los array multidimensionales es una red de varias dimensiones como su nombre nos indica en dos, tres, cuatro… dimensiones, funcionan igual que los unidemsionales, pero usando dos punteros.
Se pueden declarar de la siguiente manera Int[][] ar; int[]ar1[]; int [][][]ar2;
Existen arrays irregulares, que son aquellos que a la hora de crear un array multidimensionales, se puede dejas las ultimas dimensiones sin asignar tamaño.
A cada posición definida se le puede asignar un array con tantas dimensiones como queden sin tamaño. Importante no se pueden dejar dimensiones intermedias sin asignar tamaño  
ej. 
```java 
Int [][][] h = new int [6][][4]; 
```
Si se inicializa asi en cada posición deberemos de asignar las dimensiones de cada fila
Igual que con los array de una dimensión, un array multidimensional puede declararse, crearse e inicializarse en una única instrucción. Se puede dejar las últimas dimensiones sin asignar tamaño e inicializarlas después.
 
## Genéricos

Los genéricos son aquellas clases que permiten trabajar con cualquier tipo de objeto en lugar de un tipo de objeto específico, es decir una clase genérica puede tomar un tipo de objeto como parámetro de tipo y luego trabajar con ese tipo de objeto dentro de la clase. No pueden ser primitivos. Una clase genérica se define usando el operador diamante con la letra T (<T>).

Ej. 
```java
MyClass<String> mc = new MyClass<>();
```

A la hora de definir un parámetro de tipo genérico, se debe emplear el operador comodín. El método podrá ser llamado con un objeto Bean de cualquier tipo.
Se puede definir una clase que solo admita objetos de un determinado subtipo 
MyClass<T extends Number>{}. Esto quiere decir que la clase no pueda trabajar con cualquier tipo de Java sino solamente con el tipo definido.
Se puede definir parámetros de tipo genéricos se puede utilizar tanto extends como super para establecer restricciones.

Una clase no genérica puede incluir métodos que utilicen un tipo genérico (en parámetros o como resultados). Se incluirá la expresión <T> en la definición del método.

### Iterables

Es un objeto que puede ser recorrido mediante un enhanced for. Los objetos iterables implementan la interfaz java.lang.Iterable, que entre sus métodos más destacados esta Iterator<T> iterato(). Devueleve un objeto Iterator. Las listas y los conjuntos de son ejemplos de objetos iterables.

El objeto tipo cursor que permite recorrer el contenido de un Iterable es Iterator del cual destacan los métodos hasNext (Indica si hay más elementos que recorrer) y next se desplaza al siguiente elemento y devuelve una referencia al mismo.

### Collection

Una colección (Collection) en Java es un objeto que agrupa elementos similares en una estructura de datos única y que se puede utilizar para manipular y almacenar los datos de manera eficiente. Las colecciones proporcionan una manera flexible y conveniente para trabajar con grupos de objetos, como matrices o listas, y ofrecen una amplia gama de funcionalidades para agregar, eliminar, buscar y modificar elementos.

Las colecciones se utilizan comúnmente en Java para almacenar datos de manera dinámica, es decir, sin tener que especificar el tamaño de la colección de antemano. Algunos ejemplos de colecciones incluyen Listas (List), Conjuntos (Set), Mapas (Map), Colas (Queue) y Pilas (Stack). Cada tipo de colección tiene sus propias características y métodos específicos, lo que las hace útiles en diferentes situaciones y aplicaciones.
 
### Listas

Es una agrupación de objetos donde cada elemento tiene una posición asociada a partir del orden de llegada, siendo 0 la posición del primer elemento. Las listas implementa la interfaz List que a su vez implementa Collection. Son colecciones de tipo genérico (preparadas para admitir cualquier objeto Java), La principal clase de colección que se usa es ArrayList.

Las listas generadas con Arrays.asList son listas fijas que no admite inserciones ni eliminaciones.
Las listas generadas con List.of y con List.copyOf(copiar de otra lista) son listas Inmutables, no admite la eliminación, modificación e inserciones de elementos, ni valores null, no permite ordenarlo.

Principales métodos para listas
-	Add(dato): añade el dato a la colección y lo colocal al final de la misma.
-	Add(int pos, dato):  añade el elemento a la posición indicada, desplazando hacia adelante los que se encuentren en dicha posición(las posiciones deben de existir).
-	Set(int pos, dato): sustituye el elemento existente en la posición indicada por el nuevo dato suministrado como parámetro. Devuelve el elemento sustituido.
-	Size(): Devuelve el total de elementos de la colección.
-	Get(int pos): Devuelve el elemento que ocupa la posición indicada. Si la posición es menor que 0 o mayor o igual que size(), se producirá una excepción.
-	Remove(int pos): Elimina el elemento que ocupa la posición indicada y lo devuelve. Si la posición es menor que 0 o mayor o igual que size, se producirá una excepción.
-	Remove(objeto): Elimina el elemento indicado en caso de que exista. Devuelve true si dicho elemento estaba presente en la colección. Si hay más de un elemento, elimina la primera ocurrencia.

Recorrer una lista
-	Un bucle estándar for
-	Un bucle for each
-	Método forEach (usando programación funcional)


### Tablas

En Java, un Map es una colección de elementos que se almacenan como pares clave-valor. Cada elemento en un Map consiste en una clave única que se utiliza para acceder a su valor correspondiente. Los Map son útiles para asociar una clave con un valor, y para recuperar rápidamente el valor asociado con una clave determinada.

Java proporciona varias implementaciones de la interfaz Map, cada una de las cuales tiene diferentes características y se utiliza para diferentes propósitos. Algunas de las implementaciones más comunes incluyen HashMap, TreeMap(ordenados por clave), LinkedHashMap, Hashtable.
 
Los Map se puede generar usando Map.ofEntries() o Map.copyOf(), ambos son inmutables, no admiten la eliminación, modificación e inserción de elemento. No admite ni calves ni valores null.

Principales métodos para mapas
-	Put(clave, valor):Añade el dato a la colección y le asocia la clave indicada como primer parámetro. Si ya existiera esa clave, el valor existente será sustituido por el nuevo. Admite claves null.
-	putIfAbsent(clave, valor): Añade la entrada en caso de que la clave no exista o tenga asociado el valor null.
-	Get(clave): Devuelve el dato que tenga asociada dicha clave. Si no hay ninguno , devolverá null
-	Size(): devuelve el tamaño de la colección
- Remove(clave): elimina el dato que tenga dicha clave asociada y devuelve el elemento eliminado.
-	containsKy(clave):Indica si hay algún elemento en la colección con dicha clave asociada.
-	ContainsValue(valor): Indica si el elemento está presente en la colección.

Recorrer una tabla
-	Usando values (): retorna una lista de los valores, se recorren con for each.
-	Usando keySet(): devuelve el conjunto de claves de la tabla, se recorren con for each.
-	Metodo forEach (usando lambdas).

#### TreeMap

Es similar a HashMap, con la diferencia de que los objetos están ordenados por la clave. Si la clave es numérica se ordenaría de menor a mayor.

### Conjuntos

En Java, un Set es una colección que no permite elementos duplicados. Esto significa que si agregas un elemento a un Set que ya se encuentra en él, el Set no se modificará. La interfaz Set es parte del framework de colecciones de Java y extiende la interfaz Collection. Algunas de las características que distinguen a un Set de otras colecciones son:

-	No se permiten elementos duplicados: si intentas agregar un elemento que ya se encuentra en el Set, no se agregará.
-	No tiene orden específico: los elementos del Set no tienen un orden definido.
-	Operaciones de conjunto: la interfaz Set proporciona métodos para realizar operaciones comunes de conjunto, como la unión, intersección y diferencia.

Existen varias implementaciones de la interfaz Set en Java, como HashSet, LinkedHashSet, y TreeSet. Cada implementación tiene sus propias características y ventajas, por lo que es importante seleccionar la implementación correcta para la tarea que se está realizando.

Los Set se pueden generar usando of y copy, ambos son inmutables, no admiten la eliminación, modificación e inserción de elementos, tampoco valores null.

Principales métodos para los set
-	Add (dato): añade el dato a la colección si no está presente. Devuelve true si lo ha podido añadir
-	Remove(dato): Elimina el elemento si se encuentra en la colección
-	Size: Devuelve el tamaño de la colección
-	Contains: Devuelve true si el objeto existe en la colección.

Recorrer un set
-	Usando for each.
-	Método forEach (usando lambdas).
 
### Colas dobles (Cola y pila)

Un "Deque" (también conocido como "Double Ended Queue") en Java es una estructura de datos que permite la inserción y eliminación de elementos en ambos extremos de la cola. La clase Java "Deque" es parte del paquete "java.util" y se puede usar para implementar una cola doblemente terminada. Esta clase extiende la interfaz "Queue" y proporciona métodos adicionales para agregar y eliminar elementos tanto en el frente como en la parte posterior de la cola. Los métodos "addFirst()" y "addLast()" se utilizan para agregar elementos al principio y al final de la cola, respectivamente. Los métodos "removeFirst()" y "removeLast()" se utilizan para eliminar elementos del principio y del final de la cola, respectivamente. Además de los métodos de cola estándar, la interfaz Deque también proporciona métodos adicionales para acceder a los elementos en ambas direcciones, como "getFirst()" y "getLast()".
 
A la hora de crear un Deque no tenemos métodos de factorías sino que se crean directamente usando el operador new

Principales métodos para los deque
-	Add (dato): añade el dato al final de Deque, comportándose como una cola.
-	Push (dato): Añade el elemento a la cabecera del Deque comportándose como una  pila.
-	poll: Extrae y elimina el elemento de la cabecera.
-	Remove: extra y elimina el elemento de la cabecera.
-	Peek y element: Devuelven el elemento de cabecera, pero sin eliminarlo.
-	Size: Indica el tamaño de la colección.

Recorrer un deque
-	Usando for each.
-	Método forEach (usando lambdas).
 
## Ordenar arrays y listas

Este tipo de colecciones pueden ser ordenados según el orden natural de los objetos. Este orden natural se define a través de la interfaz Comparable, que deberá ser implementada por los objetos que ordena. Si las clases no implementan Comparable, se deberá definir el orden natural en otra interfaz llamada Comparator.

### La interfaz comparable

Es una interfaz con un único método llamado compareTo donde se define la lógica de aplicación. Esta interfaz es implementa por clases de envoltorio y String. Para poder ordenar listas y arrays de otro tipo de objetos, sus clases deberán implementar esta interfaz.

Métodos de ordenación
-	Para los arrays usamos el método sort.

### La interfaz Comparator

Utilizada para poder definir el orden natural para aquellos tipos de objetos cuyas clases no implementan Comparable. Esta interfaz es implementa por clases de envoltorio y String. Para poder ordenar listas y arrays de otro tipo de objetos, sus clases deberán implementar esta interfaz Métodos de ordenación

-	Para arrays usamos Arrays.sort
-	Para List usamos sort.

### Búsqueda binaria

Los Arrays proporcionan el siguiente método para realizar una búsqueda en un array.

-	binarySearch(int array, int valor):Devuelve la posición del valor dentro del array, que previamente debe de estar ordenado. Debemos de tener en cuenta lo siguiente, si el array no está ordenado, el resultado es impredecible. Si el array esta ordenado y el elemento no se encuentra, se devuelve –plns-l. Donde plns es la posición que le correspondería al elemento.
-	Comparate(array1, array2): Devuelve el resultado de la comparación lexicográfica de ambos arrays. 
  *	El resultado de la comparación seria -1 si array1 es menor que array2
  * El resultado de la comparación es 0 si ambos arrays son iguales
  *	El resultado de la comparación es 1 si array1 es mayor que array2.
-	Mismatch(array1, array2):Devuelve la posición de la primera diferencia entre los dos arrays, o -1 si no hay diferencias.

# Entrada/Salida
La entrada y salida se refiere a operaciones de recuperación de datos desde una fuente externa (entrada) y envió de datos desde el programa al exterior (salida).
Salida

## java.io

-	OutputStream: Clase abstracta que representa un flujo de salida
-	PrintStream: Subclase que proporciona métodos para enviar datos a cualquier flujo de salida
-	FileOutStream: Subclase de OutputStream que representa un flujo de salida asociado a un fichero.
-	FileWriter: Clase específica para escritura de texto en un fichero.

### Escritura por consola

System.out es un objeto de la clase PrintStream que nos permite realizar las siguientes operaciones
-	Print: Escritura de cualquier tipo de dato Java, sin incluir salto de línea al final
-	Println: Escritura de cualquier tipo de dato Java, con salto de línea al final.
-	Printf(String forrmat, object…args): Escritura de datos con formato

### Escritura a ficheros

Para la escritura de información en un fichero usaremos la propia clase PrintStream a la cual le pasaremos en el constructor la ruta del documento o un FileOutputStream.
-	Constructor ruta del documento: 
  *	Se graba la información en modo sobrescritura
  *	Si no existe el fichero se crea
  *	Escritura con formato.
-	 Constructor FileOutputStream (con ruta y boolean): 
  *	Si el boolean es true se indica que se escribirá el documento agregando el contenido.
 
#### Métodos principales de  FileWriter

-	Constructor ruta del documento
  *	Graba los datos en modo sobrescritura
  *	Crea el fichero si no existe
-	Constructor ruta del documento mas boolean
  *	Graba los datos en mod append si es true el boolean
  *	Crea el fichero si no existe

### Metodos principales BufferedWriter

Permite la escritura a través de un buffer mejorando el rendimiento
-	Constructor con FileWriter.

#### Entrada

Principales clases para operaciones de entrada de datos
-	InputStream: Clase abstracta que representa un flujo de entrada de bytes.
-	FileInputStream: Subclase de InputStream que representa un flujo de entrada asociado a un fichero.
-	FileReader: Clase específica para lectura de texto en un fichero
-	BufferedReader: Proporciona un mecanismo eficiente para la lectura de cadenas de texto de una fuente externa.

#### Lectura por teclado

-	Usando BufferedReader: Se debe crear un InputStreamReader asociado a la entrada estándar(System.in)
-	Lectura mediante Scanner

#### Lectura de fichero

-	Usando BufferedReader:
  *	Lectura de todas las línea del fichero
  *	Si el fichero no existe se produce una excepción
  *	Se Inicializa con una clase FileReader
-	FileInputStream
  *	Utilizado para lectura de ficheros binarios
  *	Se inicializa con un File.

## java.nio

Nuevo paquete de entradsa/salida para lectura y escritura en ficheros

-	Path: Representa una ruta a un fichero o directorio
-	Paths: Clase utilizad apara crear instancias de Path
-	Files: Dispone de diversos métodos estáticos para operar contra un fichero o directorio

### Inertfaz Path

Es parte de la API de manejo de archivos introducida en la versión 7 de Java. Esta interfaz se encuentra en el paquete java.nio.file y se utiliza para representar una ruta o dirección a un archivo o directorio en el sistema de archivos.

La interfaz Path proporciona una forma de trabajar con rutas de archivos independientemente del sistema operativo subyacente. Es decir, se puede trabajar con rutas de archivos en Windows, Linux, macOS u otros sistemas operativos, utilizando los mismos métodos y propiedades de la interfaz Path.

Algunos de los métodos que se pueden utilizar con Path incluyen la creación de una nueva instancia de Path, la obtención de información sobre la ruta, la concatenación de rutas, la verificación de si una ruta existe o no, y la obtención de los componentes de una ruta, como el nombre del archivo o directorio.

Para crear una implementación de path usaremos el método of o el método get de la clase Paths.

Principales métodos
-	getFileName: Nombre del fichero o ultimo elemento del Path
-	toAbsolutePath: Ruta completa del fichero o directorio.
-	Normalize: Resuelve las rultas relativas y devuelve el path normalizado
-	Relativize: Devuelve la ruta relativa de other respecto al path principal.
-	Resolve: Resuelve la ruta de other frente a la principal
-	getNameCount: Devuelve el numero de elementos del path, sin incluir el raíz
-	genaName(index): Devuelve la parte del path que ocupa la posición indicada. El primer elemento (sin incluir la raiz)tiene índice 0.

# Clase Files

Es parte de la API de manejo de archivos introducida en la versión 7 de Java. Esta clase se encuentra en el paquete java.nio.file y se utiliza para realizar operaciones de bajo nivel en archivos y directorios, como copiar, mover, borrar, crear y modificar archivos.

La clase Files proporciona una amplia gama de métodos útiles para trabajar con archivos y directorios, incluyendo la creación de nuevos archivos y directorios, la lectura y escritura de archivos, la verificación de la existencia de un archivo o directorio, la obtención de información de metadatos del archivo, como la fecha de creación y la última fecha de modificación, y la realización de operaciones de archivos en paralelo.
Además, la clase Files también proporciona métodos para trabajar con enlaces simbólicos y para realizar operaciones atómicas en archivos, lo que significa que las operaciones se realizan como una sola unidad y no se pueden interrumpir por otras operaciones en el sistema.

Principales métodos:
- exist: Devuelve un boolean indicando si existe o no el documento.
- isFile: Devuelve un booelan indicando si es un documento o no.
- isDirectory: Devuelve un boolean indicando si es un directorio o no.
-	lines: Devuelve un Stream con todas las líneas del fichero. A partir de ahí, se pueden aplicar los métodos stream para realizar búsquedas, transformaciones, filtrados, etc.
-	readAllLines: Devuelve una lista con las cadenas del fichero, donde cada elemento corresponde con una línea
-	newBufferedReader: Devuelve un objeto BufferedReader para realizar la lectura de forma clásica.
-	writeString: Escribe en el fichero indicado como primer parámetro, la cadena especificada en el segundo, utilizando el juego de caracteres del tercero y las opciones de escritura del cuarto.
-	Write: Escribe en el fichero indicado como primer parámetro la conleccion de cadenas especificas en el segundo, utilizando el juego de caraceteres del tercero y las opciones de escritura del cuarto.
-	Copy: Copia el contenido del un fichero en otro.
  *	Si el fichero target ya existe y no se indica opción, se produce una excepción. Aunque si ambas rutas son iguales, el método se ejecutara sin cambios
  *	Si Source es un directorio, se creara en taget un directorio vacio
  *	Si target es un directorio, FileAlreadyExistsException
  *	Si el tercer parámetro es StanderdCopyOption.REPLACE_EXISTING, en fichero target será sustituido en caso de que exista
  *	Si el tercer parámetro incluye StandarCopyOption.COPY_ATTIBUTES, se copiaran tamibien las propiedades del fichero origen en el destino.
-	Move: Mueve un fichero de origen a otro de destino
  *	Si el fichero target ya existe y no se indica opción, se produce una excepción. Aunque si ambas rutas son iguales, el método se ejecuta sin cambios
  *	Si Source es un directorio, se creara en target un directorio vacio
  *	Si target es un directorio, FileAreadyExistsException
  *	Si el tercer parámetro es StandardCopyOption.REPLACE_EXISTING, en fichero target será sustituido en caso de que exista.
-	Delete: Elimina el fichero si existe, si no se produce una excepción, Si es un directorio, deberá estar vacio
-	Delete ifExists: Elimina el fichero si existe, sino no hace nada. Si es un directorio, deberá estar vacio.
-	createFile: Si el fichero existe, se produce una excepción.

# Excepciones. Conceptos y tipos

Una excepción es una situación anómala que se pude producir durante la ejecución de un programa. Esto se produce debió a fallos de programación o situaciones que escapan al control del programador.  Para evitar la finalización del programa, se usa la gestión de excepciones para gestionar estos errores y reconducir el programa.
Las excepciones están organizadas de la siguiente manera

## Clasificación

Según su naturaleza, una excepción puede ser
-	Unchecked: Conocidas también como excepciones de sistema, son todas las excepciones subclase de RuntimeException. Se produce por errores de programación y no es obligatorio capturarlas.
-	Checked: Son lanzadas por métodos de clases del API Java, especificas de cada clase. Es obligatorio capturarlas.
Excepciones unchecked
-	ArrayIndexOutOfBoundsException: Intento de acceder fuera de los límites de un array.
-	NullPointerException: Acceso a métodos de un objeto con referencia a null
-	SecurityException: Producida por una violación de seguridad.
-	ClassCastException: Error al realizar una conversación de tipos.
-	ArithmeticException: Operación matemática incorrecta
-	IllegalArgumentException: Un método recibe como parámetro un valor que no es válido.

## Errores

Los errores son situaciones que se producen en un programa de la que no se puede recuperar, como un fallo en la JVM, falta de espacio en memoria…
Sin embargo, lo errores también están representado por clases que heredan Error: OutOfMemoryError, StackOverFlowError, InternaError….

### Captura de excepciones

Las excepciones se capturan en un programa java a través de los bloques try catch.
Podemos poner tantos bloques catch como posible excepciones se pudieran dar.
En la zona try ira el código que ejecutaremos y en el catch el tratamiento de la excepción.

No puede haber ninguna instrucción entre los bloques try y catch. Si se capturas varios tipos de excepciones que tienen relación de herencia entre ellas, los catch de las subclases deben ir antes que los que de las super clases.

Desde la versión 7 de java existe la opción de multicatch, tenemos que tener en cuenta que no pueden tener relación de herencia, sino se producirá un error de compilación.

Las excepciones se pueden complementar usando el bloque finally. Este bloque se ejecuta siempre, tanto si se produce la excepción como si no. Si se produce una excepción y no hay ningún catch para capturarla, se propagará la excepción al punto de llamada, pero antes ejecutará el bloque finally.

## Métodos de exception

Todas las clases de excepción heredan los siguientes métodos
-	getMessage: Devuelve una cade de caracteres con un mensaje de error asociado a la excepción
-	printStackTrace: Genera un volcado de error que es enviado a la consola.

## Lanzamiento y propagación de excepciones

La propagación de excepciones en Java se refiere a la capacidad de una excepción de ser lanzada desde un método a otro método superior en la pila de llamadas, en busca de un manejador de excepciones que pueda procesarla.

Cuando se produce una excepción en un método, la excepción se envía a todos los métodos que lo llamaron, hasta que se encuentra un método que tiene un manejador de excepciones adecuado para procesar la excepción. Este proceso se conoce como propagación de excepciones.

La propagación de excepciones en Java es importante para manejar situaciones de error que ocurren en un nivel inferior del código, pero que necesitan ser manejadas en un nivel superior. Por ejemplo, si un método en una clase no puede abrir un archivo, podría lanzar una excepción para indicar el error. Si el método que llama a este método no puede manejar la excepción, la excepción se propagará a otro método superior que pueda manejarla.

En Java, la propagación de excepciones se realiza mediante la utilización de la cláusula "throws" en la firma del método. Al agregar "throws" seguido del tipo de excepción, se indica que el método puede lanzar una excepción de ese tipo y que los métodos que lo llamen deben manejar la excepción o propagarla a su vez.

Podemos lanzar nosotros manualmente una excepción  según los requisitos que hemos programado en nuestra aplicación (debemos propagarla también uso de throws). En caso de propagar una excepción de tipo checked no hace falta usar throws en la firma del método.

## Excepciones personalizadas

Se puede crear una excepción personalizada definiendo una clase que herede Exception.

## Try con recursos

Los "try con recursos" o "try-with-resources" en Java son una estructura de control de flujo que se utiliza para asegurar que los recursos se cierren correctamente después de ser utilizados, incluso en caso de excepciones.

En Java, es común que un programa utilice recursos externos como archivos, conexiones a bases de datos, sockets de red, entre otros. Es importante cerrar estos recursos correctamente después de usarlos, para evitar que queden abiertos y causen problemas en la aplicación o consuman recursos del sistema de manera innecesaria.

Antes de la introducción de la estructura "try con recursos", la forma común de manejar el cierre de recursos era utilizando bloques "finally" después del bloque "try". Esto era propenso a errores y hacía el código más complejo.

En este caso, la variable "recurso" es un objeto que implementa la interfaz "AutoCloseable", que se encarga de cerrar el recurso automáticamente después de que el bloque "try" termine, incluso en caso de excepciones.

La estructura "try con recursos" garantiza que los recursos se cierren de manera adecuada y segura, y ayuda a hacer el código más claro y fácil de entender. Además, a partir de Java 9, es posible utilizar esta estructura con recursos que no sean de tipo "AutoCloseable", gracias a la introducción de la interfaz "java.lang.Cleaner"

La creación del objeto puede realizarse antes del try, indicando después la variable entre paréntesis. En este caso, la variable se trata como constante efectiva, si modificas el contenido antes de usarla en el try data un error de compilación.

## Interfaz AutoCloseable

La interfaz "AutoCloseable" es una interfaz funcional introducida en Java 7, que se utiliza para implementar recursos que deben ser cerrados después de su uso.

La interfaz "AutoCloseable" define un único método llamado "close()", que se utiliza para liberar los recursos asociados con un objeto después de su uso. Los recursos que se deben cerrar pueden ser, por ejemplo, archivos, sockets de red, conexiones a bases de datos, entre otros.

Al implementar la interfaz "AutoCloseable", se garantiza que los recursos se cerrarán automáticamente cuando se utilizan en un bloque "try-with-resources", eliminando así la necesidad de tener que cerrar los recursos manualmente.

# Anotaciones

Las anotaciones personalizadas, también conocidas como anotaciones de usuario o anotaciones definidas por el programador, son una característica de Java que permite a los desarrolladores definir sus propias anotaciones con metadatos específicos para sus programas.

Las anotaciones personalizadas son útiles para los desarrolladores que desean agregar metadatos a sus programas sin tener que crear una nueva clase o interfaz. Pueden ser utilizados para definir características específicas de una clase o método, como la documentación, la validación de entrada o la seguridad. Además, las anotaciones personalizadas también pueden ser procesadas por herramientas de compilación o frameworks para automatizar tareas repetitivas o agregar funcionalidades adicionales a un programa.

Se pueden indicar delante de clases, métodos o atributos. Siempre deben de ir delante del nombre del tipo. Las anotaciones personalizadas se definen utilizando la sintaxis de anotación de Java, que comienza con el símbolo "@" seguido del nombre de la anotación. Los desarrolladores pueden definir sus propias anotaciones personalizadas utilizando la palabra clave "interface". La interfaz debe de estar siempre anotada a su vez con dos anotaciones especiales, conocidas como metaanotaciones que son @Target y @Retention. En cuanto al interior de la interfaz, ésta está formada por una serie de métodos que determinan los atributos expuestos por la anotación.
 
## Metaanotacion Target

Sirve para especificar los elementos de programa a los que se puede aplicar una anotación personalizada y garantizar que solo se use en el contexto adecuado de la anotación.

-	ElementType.TYPE: Se aplica a un tipo (clase, interface, enumeración)
-	ElementType.FIELD: Se aplica a un miembro de la clase.
-	ElementType.METHOD: Se aplica a un método.
-	ElementType.PARAMETER: Se aplica a parámetros de un método.
-	ElementType.CONSTRUCTOR: Se aplica a constructores.
-	ElementType.LOCAL_VARIABLE: Se aplica a variables locales.
-	ElementType.ANNOTATION_TYPE: Indica que el tipo declarado en si es un tipo de anotación

## Metaanotacion Retention

Sirve para especificar la duración de una anotación personalizada, es decir, hasta qué punto la anotación debe ser retenida y accesible en tiempo de ejecución

-	RetentionPolicy.SOURCE: Retenida solo a nivel de código, por lo que es ignorada por el compilador.
-	RetentionPolicy.CLASS: Retenida en tiempo de compilación, pero ignorada en tiempo de ejecución.
-	RetentionPolicy.RUNTIME: Retenida en tiempo de ejecución y solo se puede acceder a ella en este tiempo.

## Metaanotacion Repetable

Sirve para permitir que una anotación personalizada se aplique múltiples veces en el mismo elemento de programa.

## Metaanotacion SuppressWarnings

Sirve para suprimir los warnings (advertencias) del compilador en un elemento de programa específico, como una variable, método o clase.

Los nombres de los warnings que se pueden suprimir varían según la versión del compilador Java, pero algunos ejemplos comunes incluyen:

-	unchecked: para suprimir warnings sobre el uso de tipos genéricos sin verificación adecuada.
-	deprecation: para suprimir warnings sobre el uso de elementos de programa que han sido marcados como obsoletos.
-	rawtypes: para suprimir warnings sobre el uso de tipos sin parámetros de tipo.

## Metaanotacion Override

Se utiliza delante de un método de instancia para indicar que dicho método esta siendo sobreescrito. Es utilizada por el compilador.

## Metaanotacion Deprecated

Se utiliza para indicar que una clase, atributo o metodo esta deprecated y no se recomiendoa su uso. Es utilizada en tiempo de ejecución.

## Metaanotacion SafeVarargs

Utilizada sobre métodos y constructores para afirmar que el parámetro vaarargs no realiza operaciones potencialmente inseguras.