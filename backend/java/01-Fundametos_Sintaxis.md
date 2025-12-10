<div align="center">
  <img src="../../assets/java_logo.svg">
</div>

# Índice
- [Índice](#índice)
- [Introducción](#introducción)
  - [Términos principales de java](#términos-principales-de-java)
  - [La programación orientada a objetos (OOP)](#la-programación-orientada-a-objetos-oop)
  - [Técnica de sangrado](#técnica-de-sangrado)
  - [Palabras reservadas de java](#palabras-reservadas-de-java)
- [Variables](#variables)
  - [Definir una variable](#definir-una-variable)
  - [Ámbito de variables y duración de variables](#ámbito-de-variables-y-duración-de-variables)
    - [Variables primitivas y Variables de objeto](#variables-primitivas-y-variables-de-objeto)
- [Tipos de datos](#tipos-de-datos)
  - [Básicos](#básicos)
    - [Enteros](#enteros)
    - [Flotantes (Float)](#flotantes-float)
    - [Carácter](#carácter)
    - [Boolean](#boolean)
    - [Literales](#literales)
  - [Complejos (Objetos)](#complejos-objetos)
    - [Creación de un objeto y ciclo de vida de los objetos](#creación-de-un-objeto-y-ciclo-de-vida-de-los-objetos)
  - [Conversión de tipos](#conversión-de-tipos)
    - [Clases envoltorio](#clases-envoltorio)
    - [Secuencia de escape de caracteres](#secuencia-de-escape-de-caracteres)
- [Inicialización por defecto](#inicialización-por-defecto)
- [La indiferencia de tipo](#la-indiferencia-de-tipo)
- [Operadores aritméticos, asignación, envoltorio, ternarios y lógicos.](#operadores-aritméticos-asignación-envoltorio-ternarios-y-lógicos)
  - [Operadores aritméticos](#operadores-aritméticos)
  - [Operadores asignación](#operadores-asignación)
  - [Operadores envoltorio](#operadores-envoltorio)
  - [Operadores ternario](#operadores-ternario)
  - [Operadores lógicos](#operadores-lógicos)
- [String](#string)
  - [Igualdad de StringBuilder](#igualdad-de-stringbuilder)
  - [Pool de objetos (caracteres, integer, double)](#pool-de-objetos-caracteres-integer-double)
- [Estructuras de control](#estructuras-de-control)
  - [Instrucción IF.](#instrucción-if)
  - [Instrucción Switch.](#instrucción-switch)
- [Estructuras de repetición](#estructuras-de-repetición)
  - [Bucle for](#bucle-for)
    - [Variantes del bucle for: Enhanced for (foreach)](#variantes-del-bucle-for-enhanced-for-foreach)
  - [Bucle while](#bucle-while)
  - [Break y continue](#break-y-continue)


# Introducción

Java es un lenguaje de programación orientado a objetos que fue desarrollado por Sun Microsystems en la década de 1990 y gestionado actualmente por Oracle Corporation. Java es un lenguaje de programación de alto nivel y es conocido por su portabilidad, lo que significa que el código Java puede ser ejecutado en cualquier plataforma que tenga una máquina virtual Java (JVM) instalada.

## Términos principales de java

<table>
  <tr>
    <td>Simple</td>
    <td>Java dispone de un conjunto conciso y coherente de características que facilitan su aprendizaje y su uso.</td>
  </tr>
  <tr>
    <td>Seguro</td>
    <td>Java constituye un medio seguro para crear aplicaciones de Internet</td>
  </tr>
  <tr>
    <td>Portable</td>
    <td>Los programas de Java se pueden ejecutar en cualquier entorno para el que exista un sistema de tiempo de ejecución de Java (JVM)</td>
  </tr>
  <tr>
    <td>Orientado a Objetos</td>
    <td>Java aplica la filosofía moderna de programación orientada a Objetos</td>
  </tr>
  <tr>
    <td>Robusto</td>
    <td>Java aboga por una programación sin errores gracias a sus tipos estrictos y las comprobaciones en tiempo de ejecución</td>
  </tr>
  <tr>
    <td>Subprocesos múltiples</td>
    <td>Java ofrece compatibilidad con programación de subprocesamiento múltiple.</td>
  </tr>
  <tr>
    <td>Neutralidad arquitectónica</td>
    <td>Java no se limita a un equipo o sistema operativo en concreto.</td>
  </tr>
  <tr>
    <td>Interpretado</td>
    <td>Java admite código compatible entre plataformas gracias al uso de código de bytes</td>
  </tr>
  <tr>
    <td>Alto rendimiento</td>
    <td>El código de bytes de Java esta optimizado para acelerar la ejecución</td>
  </tr>
  <tr>
    <td>Distribuido</td>
    <td>El diseño de Java se orientas al entrono distribuido de Internet</td>
  </tr>
  <tr>
    <td>Dinámico</td>
    <td>Los programas de Java incluyen abundante información de tiempo de ejecución que se usa para verificar y resolver el acceso a objetos en tiempo de ejecución</td>
  </tr>
</table>

## La programación orientada a objetos (OOP)

La Programación Orientada a Objetos (POO) es un paradigma de programación que se enfoca en el concepto de "objetos", los cuales son instancias de una clase y que tienen propiedades (atributos) y acciones (métodos) asociados.
En POO, se modelan los problemas como una colección de objetos que interactúan entre sí para lograr un objetivo. Cada objeto es una entidad independiente que tiene su propio estado interno y puede realizar acciones específicas. Estos objetos pueden ser agrupados en clases, las cuales son modelos que describen las propiedades y acciones que los objetos de una determinada categoría deben tener. La POO se basa en cuatro principios fundamentales:
- Encapsulamiento: Es un mecanismo de programación que combinan el código con los datos que manipula, al tiempo que los protege de interferencias externas.
Los atributos y métodos de un objeto están encapsulados en su propia clase, lo que significa que no pueden ser accedidos directamente desde fuera de la clase.
-	Herencia: permite la creación de nuevas clases a partir de clases ya existentes, adquiriendo las propiedades y métodos de la clase padre.
-	Polimorfismo: la capacidad de un objeto para tomar diferentes formas o comportamientos dependiendo del contexto.
-	Abstracción: el proceso de identificar las características esenciales de un objeto o sistema y eliminar todo lo que no es relevante para el problema que se está resolviendo.

## Técnica de sangrado

Java es un lenguaje libre, lo que significa que no importa la posición de las instrucciones en una línea. No obstante, con el paso del tiempo, se ha desarrollado un estilo de sangrado común que permite crear programas más legibles.
El estilo más común de sangrado es después de cada llave, es decir, aplicamos un nivel de sangrado.
Tendremos que tener en cuenta que existen instrucciones especiales que requieren un sangrado adicional.

## Palabras reservadas de java

Una palabra reservada en Java es una palabra clave que tiene un significado especial y está reservada por el lenguaje Java para realizar una función específica. No se pueden utilizar como identificadores para nombres de variables, nombres de clases, nombres de métodos u otros identificadores definidos por el usuario en el código fuente de Java.

Las palabras reservadas de Java se utilizan para declarar variables, estructuras de control de flujo, métodos, clases y otras construcciones del lenguaje de programación Java. Debido a que estas palabras tienen un significado especial en el lenguaje, no se pueden usar para otros fines que no sean los definidos por el lenguaje Java.

Es importante conocer y entender las palabras reservadas de Java para poder escribir un código fuente válido en Java y evitar errores de sintaxis.

# Variables

Es un contenedor que se utiliza para almacenar datos que pueden cambiar a lo largo de la ejecución de un programa. Cada variable tiene un tipo de datos específico que define qué tipo de valor puede almacenar, como números enteros, caracteres, cadenas de texto, etc.

## Definir una variable

La estructura a la hora de definir una variable siempre es el mismo, el tipo de variable, el nombre de la variable y el valor de la variable, siendo este último optativo ya que, por defecto según el tipo y ámbito de la variable, aunque normalmente suele ser null. Ejemplos de definición de variables

- Declaración: int mivar;
- Declaración e inicialización:  int p =10;
- Declaración múltiple con inicialización: int p, s, a=5;
  
Los identificadores de las variables (nombres) se pueden utilizar cualquier tipo combinación de letras, número y los símbolos $ y _. Pero existen unas excepciones, estas excepciones son:
-	No se pueden usar palabras reservadas, ni la palabra goto.
-	No pueden comenzar por un carácter numérico. 

## Ámbito de variables y duración de variables

En Java, el ámbito y la duración de una variable dependen del tipo de variable que se esté utilizando. Hay cuatro tipos principales de variables en Java: variables locales, variables de instancia, variables de clase y variables de parámetros.

- Variables locales: Son variables que se declaran dentro de un método o bloque de código y su ámbito está limitado a ese bloque. Estas variables se crean cuando se ejecuta el bloque y se eliminan cuando el bloque se completa.
- Variables de instancia: Son variables que se declaran dentro de una clase, pero fuera de cualquier método. Estas variables se crean cuando se crea un objeto de la clase y se eliminan cuando el objeto es eliminado.
- Variables de clase: Son variables que se declaran dentro de una clase y fuera de cualquier método con la palabra clave static. Estas variables se crean cuando se carga la clase en la memoria y se eliminan cuando la clase es eliminada de la memoria.
  
- Variables de parámetros: Son variables que se utilizan para pasar valores a un método. Estas variables se crean cuando se llama al método y se eliminan cuando el método se completa.
Pero también existe el ámbito de visibilidad:
  *	A nivel de clase compartidas por todos los métodos (se les conoce como atributos o campos).
  *	A nivel de método solo visibles dentro de ese método (se les conoce como locales).
  *	A nivel de bloque solo visibles dentro de esa estructura (se les conoce como locales).

### Variables primitivas y Variables de objeto

- Variables primitivas
Las variables primitivas o tipo elementan, son variables de datos originales de un lenguaje, esto es, aquellas que nos proporciona el lenguaje con los que podemos en ocasiones construir tipos de datos abstractos y estructuras de datos.La ventaja de estas variables es que a hora de crearlas asigna directamente un espacio de memoria para almacenar el dato con el que se inicializo.
A la hora de asignar el valor de una variable a otra se realizará una copia del dato. 

- Variables Objeto
Las variables de tipo referencia a objetos (Variables objeto), son variables más complejas ya que hacen referencia al espacio de memoria destinado a almacenar la información de dicha variable. A la hora de crear este tipo de variable se necesita el operador new.
A la hora de asignar el valor de un objeto a otro objeto del mismo tipo no se realiza una copia de los datos, sino que ambas variables apuntan al mismo espacio de memoria. Esto quiere decir que si se modifica el dato en una en la otra también (no se tienen dos objetos).

# Tipos de datos

## Básicos
Los tipos de datos primitivos en Java son aquellos que se definen por el lenguaje y que se utilizan para representar valores simples. Hay ocho tipos de datos primitivos en Java:

<table>
  <tr>
    <th>Tipo</th>
    <th>Valores</th>
    <th>Intervalo</th>
    <th>Ejemplo</th>
  </tr>
  <tr>
    <td>boolean</td>
    <td>True/False</td>
    <td>-</td>
    <td>true</td>
  </tr>
  <tr>
    <td>byte</td>
    <td>Entero 8 bits</td>
    <td>-128 a 127</td>
    <td>39</td>
  </tr>
  <tr>
    <td>short</td>
    <td>Entero de 16 bits</td>
    <td>-32768 a 32768</td>
    <td>780</td>
  </tr>
  <tr>
    <td>int</td>
    <td>Entero de 32 bits</td>
    <td>-2147483648 a 2147483647</td>
    <td>59400</td>
  </tr>
  <tr>
    <td>long</td>
    <td>Entero de 64 bits</td>
    <td>-9223372036854775808 a 9223372036854775808</td>
    <td>20000000</td>
  </tr>
  <tr>
    <td>float</td>
    <td>Decimal de 32 bits</td>
    <td>-</td>
    <td>45.6f</td>
  </tr>
  <tr>
    <td>double</td>
    <td>Decimal de 64 bits</td>
    <td>-</td>
    <td>80.4</td>
  </tr>
  <tr>
    <td>char</td>
    <td>Código Unicode de 16 bits</td>
    <td>-</td>
    <td>´@´</td>
  </tr>
<table>

### Enteros

Es el tipo básico encargado de almacenar datos numéricos. El tipo básico más usado es el de tipo INT, ya que principalmente se usan para controlar bucles, indexar matrices o realizar operaciones matemáticas enteras generales. En caso de necesitar un intervalo mayor lo más recomendable de usar es el tipo long.

### Flotantes (Float)

Tipo básico encargado de almacenar y representar los números con componentes fraccionales, divididos en dos tipos float y double. El tipo más recomendado para usar es el tipo double ya que casi todas las funciones matemáticas devuelven valores double.

### Carácter

Java no almacena los caracteres en unidades de 8bits como hace otros lenguajes, java almacena dicha información usando el sistema Unicode, el cual define un conjunto de caracteres asociados al valor de una letra humana (código ASCII)

### Boolean 

El tipo básico boolean se encarga de almacenar los valores true/false mediante el uso de las palabras reservadas (true/false).

### Literales

Los literales son representaciones directas y concretas de valores en el código fuente. 
Los literales numéricos se puede representar de manera decimal, octal, hexadecimal y binario. 
Se puede usar el carácter _ a la hora de definir el valor numérico de una variable, pero tenemos que tener en cuenta las siguientes reglas.
- No se puede usar ni al principio, al final o junto al punto decimal
  *	Int n = _345;
  * double d =45._9;
  *	long in = 234_;
-	Los literales numéricos por defecto son int, para que lo sean debemos de indicarlo con la letra l, ej. 345l
-	Los literales decimales por defecto son double, si queremos que sean float debemos de indicarlo con una f

## Complejos (Objetos)

Son cualquier objeto de cualquier clase java, se maneja igual que los tipos básicos (mediante el uso de variables, cuyo tipo es la clase). Los valores que almacenan son la referencia del espacio de memoria que está asociado al objeto. Mediante el uso de variables se puede acceder a los métodos de los objetos. No se puede hacer conversión ni implícita ni explicita entre los tipos primitivos y los objetos.

### Creación de un objeto y ciclo de vida de los objetos

Para poder crear un objeto se debe de usar el operador new seguido del constructor de la clase. Al realizar esta operación obtenemos la referencia al objeto almacenado en nuestra variable de clase.

¿Qué es un constructor de una clase?

Un constructor es un método especial en una clase de Java que se utiliza para inicializar objetos de la clase recién creados. El constructor tiene el mismo nombre que la clase y no devuelve ningún valor, ni siquiera void. Se llama automáticamente cuando se crea una instancia de la clase utilizando la palabra clave "new".

En general, los constructores se utilizan para inicializar los campos de datos de la clase y para realizar cualquier otro tipo de inicialización que pueda ser necesaria antes de que el objeto esté listo para ser utilizado. Por ejemplo, un constructor puede inicializar valores predeterminados para los campos de la clase o puede tomar argumentos y utilizarlos para inicializar los campos de datos de la clase.

Es importante tener en cuenta que, si no se proporciona un constructor en una clase de Java, se creará un constructor predeterminado automáticamente. El constructor predeterminado no realiza ninguna acción específica y simplemente inicializa todos los campos de datos con sus valores predeterminados.

Puede darse el caso de que se den constructores sobrecargado es un constructor que tiene el mismo nombre que otro constructor en la misma clase, pero con diferentes parámetros. Es decir, se define un constructor sobrecargado cuando se quiere proporcionar varias maneras de inicializar un objeto de una clase.

Cuando se llama al constructor, el compilador de Java determina cuál constructor se debe utilizar basándose en el número y tipo de argumentos proporcionados en la llamada al constructor. Si se proporcionan argumentos que coinciden con la firma de un constructor sobrecargado, entonces ese constructor será el que se utilizará para crear el objeto.

Los constructores sobrecargados permiten que una clase tenga múltiples formas de crear un objeto, cada una con diferentes combinaciones de valores iniciales. Por ejemplo, una clase de "Coche" puede tener un constructor que tome el modelo, la marca y el año de fabricación como argumentos, y otro constructor que tome solo el modelo y la marca como argumentos. En este caso, el primer constructor se utilizaría si se conocen todos los detalles del coche, mientras que el segundo constructor podría utilizarse si solo se conocen el modelo y la marca

¿Cómo se destruye un objeto?

Para destruir un objeto en Java, es necesario que el objeto ya no sea referenciado por ninguna variable y no esté siendo utilizado en ningún lugar del programa.

Java tiene un mecanismo de recolección de basura automático que se encarga de eliminar los objetos que ya no son utilizados. Cuando un objeto queda sin referencias, es decir, no hay ninguna variable que apunte a él, el recolector de basura lo identifica como un objeto que puede ser eliminado y lo elimina de la memoria, es decir, se pone en marcha el recolector de basura (Garbage Collector).

Sin embargo, también se puede destruir un objeto manualmente usando el método finalize(). Este método es llamado por el recolector de basura justo antes de eliminar el objeto. Si un objeto tiene un método finalize() definido, éste puede ser utilizado para realizar tareas de limpieza o liberar recursos antes de que el objeto sea eliminado. Deberemos de tener en cuenta que este método puede ser llamado una o ninguna vez.
 
¿Qué es el recolector de basura?

El Garbage Collector (recolector de basura, en español) es un componente de la máquina virtual de Java (JVM) que se encarga de administrar la memoria en tiempo de ejecución y liberar la memoria utilizada por objetos que ya no están siendo referenciados por el programa.

En Java, los objetos se crean en el heap, una región de memoria dinámica que está separada del stack, que se utiliza para almacenar variables locales y otros datos de la pila. A medida que se crean objetos, se van asignando espacios de memoria en el heap, y a medida que el programa utiliza estos objetos, el heap va creciendo en tamaño. Sin embargo, cuando un objeto ya no es referenciado por el programa, es decir, ninguna variable apunta a ese objeto, ese espacio de memoria ya no se utiliza y se puede liberar para otros usos.

Es aquí donde entra en acción el Garbage Collector. El Garbage Collector es un proceso en segundo plano que se encarga de monitorear los objetos que están siendo utilizados por el programa. Cuando detecta un objeto que ya no está siendo referenciado por ninguna variable, marca ese objeto como elegible para ser eliminado. Luego, en algún momento posterior, el Garbage Collector se encargará de liberar la memoria utilizada por ese objeto y de recuperar el espacio en el heap.

## Conversión de tipos

El objetivo de las conversiones son la transformación de un tipo a otro tipo, existen dos tipos de conversión. Solo el tipo boolean no puede ser convertido de ninguna manera.

-	Conversión implícita: La conversión implícita se realiza automáticamente por el compilador de Java cuando un tipo de dato se asigna a otro tipo compatible.  En caso de no poder realizarse se lanzará una excepción.
Por ejemplo: 
```java
int x = 10; 
double y = x; // conversión implícita de int a double
```
- Conversión explícita: La conversión explícita se realiza mediante una operación de casting y se usa cuando se requiere convertir un tipo de dato en otro tipo no compatible. El casting se realiza colocando el tipo de destino entre paréntesis antes de la variable a convertir.

Por ejemplo:
```java
double x = 3.14;
int y = (int) x; // conversión explícita de double a int mediante casting
```

Es importante tener en cuenta que la conversión explícita puede provocar la pérdida de información o la truncación de datos en algunos casos, por lo que se debe usar con precaución.

### Clases envoltorio

En Java, las clases envoltorio (también conocidas como clases wrapper) son clases que envuelven tipos de datos primitivos para permitir que se comporten como objetos.

Esto significa que los tipos de datos primitivos, como int, boolean y float, pueden ser convertidos en objetos utilizando las clases envoltorio correspondiente, como Integer, Boolean y Float, respectivamente. Estas clases envoltorio proporcionan métodos útiles para trabajar con estos tipos de datos de una manera más orientada a objetos, como la conversión de valores, la comparación de valores y la realización de operaciones matemáticas.

Además, las clases envoltorio también son útiles para trabajar con colecciones de datos en Java, ya que las colecciones, como List y Set, requieren objetos en lugar de tipos de datos primitivos. Al utilizar las clases envoltorio, los tipos de datos primitivos pueden ser encapsulados en objetos y almacenados en colecciones. Por norma general los objetos de las clases de envoltorio son inmutables, no se pueden modificar.Las clases envoltorio cuentan con métodos estáticos que permiten la conversión explicita a otros tipos de datos.

¿Qué es el autoboxing/unboxing?

El autoboxing es un proceso automático en Java que convierte tipos de datos primitivos en objetos de las clases envoltorio correspondiente sin necesidad de realizar una conversión explícita. En otras palabras, cuando se utiliza una variable de tipo primitivo en un contexto en el que se espera un objeto de una clase envoltorio, el autoboxing convierte automáticamente el tipo de datos primitivo en un objeto de la clase envoltorio correspondiente.
Ejemplos 
```java
  Integer ent = 200;
  Double db = 45.7;
```
El unboxing en Java es el proceso mediante el cual un objeto de una clase envoltorio es convertido de nuevo a su tipo de dato primitivo correspondiente. En otras palabras, cuando se tiene un objeto de una clase envoltorio y se necesita utilizar su valor primitivo, el unboxing convierte automáticamente el objeto en su valor primitivo correspondiente. Ej. Int n = ent;

### Secuencia de escape de caracteres

En Java, una secuencia de escape de caracteres es una combinación de caracteres que se utiliza para representar caracteres especiales en una cadena de texto. Las secuencias de escape comienzan con un carácter de escape (una barra invertida ""), seguido de uno o más caracteres que representan el carácter especial deseado.

<table>
  <tr>
    <th>Secuencia de escape</th>
    <th>Descripcion</th>
  </tr>
  <tr>
    <td>\'</td>
    <td>Comilla simple</td>
  </tr>
  <tr>
    <td>\"</td>
    <td>Comilla doble</td>
  </tr>
  <tr>
    <td>\\</td>
    <td>Barra invertida</td>
  </tr>
  <tr>
    <td>\r</td>
    <td>Retorno de carro</td>
  </tr>
  <tr>
    <td>\n</td>
    <td>Nueva línea</td>
  </tr>
  <tr>
    <td>\f</td>
    <td>Salto de formulario</td>
  </tr>
  <tr>
    <td>\t</td>
    <td>Tabulación horizontal</td>
  </tr>
  <tr>
    <td>\b</td>
    <td>Retroceso</td>
  </tr>
  <tr>
    <td>\ddd</td>
    <td>Constante octal (donde ddd es la constante octal)</td>
  </tr>
  <tr>
    <td>\uxxxx</td>
    <td>Constante hexadecimal (donde xxxx es la constante hexadecimal)</td>
  </tr>
</table>

# Inicialización por defecto

Las variables dependiendo del ámbito de uso se pueden inicializar por defecto o no.
Cuando se tratan de variables locales, NO se inicializan por defecto, ya que es necesario asignarles un valor antes de utilizarlas.

Cuando se tratan de variables de clase o de atributo si se inicializan por defecto, según el tipo de variable se inicializan con estos valores:

-	Enteros: 0
-	Decimales 0.0
- Boolean false.
-	Char ‘\u0000’ (carácter nulo).
-	Objeto null.

# La indiferencia de tipo

La indiferencia de tipo, también conocida como "type erasure" en inglés, es un concepto importante en Java que se refiere a la forma en que se manejan los tipos genéricos en tiempo de compilación y en tiempo de ejecución. En Java, los tipos genéricos son una característica que permite a los programadores escribir código que pueda funcionar con diferentes tipos de datos. Por ejemplo, en lugar de escribir un método que funcione solo con listas de enteros, se puede escribir un método genérico que funcione con listas de cualquier tipo de objeto.

No pueden ser valores nulos, siempre tienen que venir inicializadas, ya que si no tiene valor el compilador no es capaz de saber o identificar el tipo que almacena la variable.

No se puede realizar las inicializaciones múltiples (var a, c = 10 ó var b=5, x=30), tampoco vale con la inicialización abreviada de los arrays.
Fue incorporada en Java 10 y consiste en declarar variables locales usando la palabra reservada var, Ej. var num = 100; 

# Operadores aritméticos, asignación, envoltorio, ternarios y lógicos.

## Operadores aritméticos

Los operadores aritméticos son aquellos que se utilizan para realizar operaciones matemáticas básicas.

- Operador de suma (+)
- Operador de resta (-).
- Operador de multiplicación (*).
- Operador división (/).
- Operador módulo de la división (%).
- Operador de incremento (++): se utiliza para aumentar el valor de una variable en uno.
- Operador de decremento (--): se utiliza para restar el valor de una variable en uno.
  * Delante de la variable: se realiza primero la operación y luego se lo asigna a la variable el resultado.
  * Detrás de la variable: primero se asigna el valor a la variable y luego se opera.

## Operadores asignación

Los operadores de asignación de resultados, son operadores que se encargan de realizar las operaciones y asignarles el resultado directamente a la variable
- Operador de asignación de suma (+=). 
- Operador de asignación de resta (-=). 
- Operador de asignación de multiplicación (*=). 
- Operador de asignación de división (/=). 
- Operador de asignación de modulo (%=).

## Operadores envoltorio

Los operadores lógicos de igualdad que se utilizan a la hora de usarlo con objetos son == o equals.

Operador == se encarga de comparar la referencia de los objetos, es decir, solo retornara el valor true cuando ambas variables apuntan a la misma instancia de objeto.

Operador/método equals:  lo tienen todas las clases objeto java, ya que es un método propio de la clase objetc. Su función es comparar el contenido de dos variables y retorna verdadero sin son iguales. Deberemos de tener en cuenta que detecta entre mayúsculas y minúsculas.

Operador/método equalsIgnoreCase: realiza la misma función que equal salvo que aquí ignora las mayúsculas y minúsculas, solo lo posee la clase String, no es propio de la clase object.


## Operadores ternario

El operador ternario es una forma abreviada de escribir una instrucción condicional if-else en una sola línea del código. La sintaxis del operador ternario es la siguiente 

- Variable = (expresión booleana) ? valor si verdadero : valor si falso;

El principal motivo del uso del operador ternario es hacer que el código sea más conciso y fácil de leer en situaciones donde una instrucción condicional simple es suficiente, sin embargo, se debe de tener cuidado al utilizarlo en situaciones más complejas, ya que puede hacer que el código sea menos legible si se usa en exceso o se anida demasiado.

## Operadores lógicos

Los operadores de condicionales son operadores ternarios que permiten evaluar una expresión booleana y producir un resultado en función del resultado de la evaluación.
- Operador menor (<). 
- Operador mayor (>). 
- Operador menor o igual (<=). 
- Operador mayor o igual (>=). 
- Operador igual (==). 
- Operador distinto de igual (!=).

Los operadores lógicos son símbolos especiales que se utilizan para combinar expresiones lógicas y producir un resultado lógico. Hay tres operadores lógicos principales en Java: AND lógico (&&), OR lógico (||) y NOT lógico (!).

El operador new encargado de obtener la referencia del espacio de memoria de un objeto.

El operador instanceof encargado de evaluar si un objeto es del tipo dado, retorna un boolean.

Los operadores lógicos de cortocircuito son aquellos operadores que permiten evaluar una expresión booleana de manera eficiente y rápida, deteniendo la evaluación de la expresión en cuanto se determina el resultado final. Los operadores lógicos de cortocircuito son && (AND lógico de cortocircuito) y || (OR lógico de cortocircuito).

La diferencia entre los operadores lógicos de cortocircuito y los operadores lógicos normales (& y |) es que los operadores de cortocircuito no evalúan el segundo operando si el primer operando ya proporciona suficiente información para determinar el resultado de la expresión completa. Esto puede ser útil para mejorar la eficiencia y evitar errores en la evaluación de expresiones complejas. Por ejemplo, si se tiene la siguiente expresión:

```java 
if (a > 0 && b < 10) {
    // código si se cumple la expresión
}
```
El operador && permite cortocircuitar la evaluación de la expresión en cuanto se determina que a es menor o igual a cero, ya que independientemente del valor de b, la expresión completa no puede ser verdadera. De esta manera, se evita la evaluación innecesaria de la segunda parte de la expresión, lo que puede mejorar la eficiencia del código.
De manera similar, si se tiene la siguiente expresión:

``` java
if (a == null || a.isEmpty()) {
    // código si se cumple la expresión
}
```

El operador || permite cortocircuitar la evaluación de la expresión en cuanto se determina que a no es nulo y no está vacío, ya que independientemente del valor de la segunda parte de la expresión, la expresión completa ya es verdadera. De esta manera, se evita la evaluación innecesaria de la segunda parte de la expresión, lo que puede mejorar la eficiencia del código.

# String
En Java, los objetos String son inmutables, lo que significa que una vez creados, no se pueden modificar. Si se intenta modificar un objeto String, lo que realmente ocurre es que se crea un nuevo objeto String con el resultado de la operación de modificación.

Por ejemplo, en el siguiente código:
``` java
String str = "Hola";
str = str + " Mundo";
```

Primero se crea un objeto String con el valor "Hola", y luego se crea un nuevo objeto String con el resultado de concatenar " Mundo" al final de "Hola". Finalmente, la variable str se actualiza para apuntar al nuevo objeto String creado.

Esta inmutabilidad de los objetos String tiene algunas ventajas, por ejemplo:
- Seguridad en la programación concurrente: como los objetos String son inmutables, no es posible que varios hilos de ejecución modifiquen el mismo objeto String al mismo tiempo, lo que puede evitar problemas de concurrencia.
- Facilidad de uso: al ser inmutables, los objetos String pueden ser usados de manera segura sin preocuparse de que su contenido sea modificado inesperadamente.

Sin embargo, también puede tener algunas desventajas en situaciones donde se realizan muchas operaciones de modificación de cadena, ya que en estos casos se pueden generar muchos objetos String temporales, lo que puede afectar el rendimiento del programa.

Esto no funciona para las cadenas usadas con StringBuilder ya que tiene que ser a través de sus métodos.
 
## Igualdad de StringBuilder
StringBuilder es una clase en Java que se utiliza para crear y manipular cadenas de texto de manera eficiente. La clase StringBuilder es similar a la clase String, pero en lugar de crear una nueva instancia de cadena cada vez que se realiza una operación de concatenación o modificación de cadena, la clase StringBuilder modifica la misma instancia de cadena, lo que puede mejorar significativamente el rendimiento y la eficiencia en situaciones donde se realizan muchas operaciones de concatenación o modificación de cadena.

No sobrescribe el método equals por lo que el resultado == y equals producen el mismo efecto. Solo es verdadero cuando apuntan al mismo objeto.

```java
StringBuilder sb1 = new StringBuilder("Hola");
StringBuilder sb2 = new StringBuilder("Hola");
StringBuilder sb3 = sb1;
System.out.println(sb1.equals(sb2)); // Imprime false, porque los contenidos de los objetos son iguales, pero las referencias son diferentes
System.out.println(sb1 == sb2); // Imprime false, porque las referencias apuntan a objetos diferentes
System.out.println(sb1 == sb3); // Imprime true, porque ambas referencias apuntan al mismo objeto.
```
## Pool de objetos (caracteres, integer, double)
En Java, un pool de caracteres (también conocido como String pool o pool de cadenas) es un espacio en memoria donde se almacenan las cadenas de texto que son creadas en un programa Java. Es una optimización de Java que permite reutilizar cadenas de texto que ya han sido creadas previamente, en lugar de crear nuevas instancias de esas cadenas cada vez que se necesitan. 

Cuando se crea una cadena de texto en Java utilizando comillas dobles (") o el operador de concatenación (+), Java busca en el pool de caracteres si ya existe una cadena con el mismo valor. Si existe, en lugar de crear una nueva instancia de la cadena, Java devuelve una referencia a la instancia existente en el pool de caracteres. Si no existe, Java crea una nueva instancia de la cadena y la agrega al pool de caracteres.

El uso del pool de caracteres puede mejorar significativamente el rendimiento y la eficiencia de una aplicación Java que utiliza cadenas de texto, ya que evita la creación innecesaria de nuevas instancias de cadenas de texto que ya existen en el pool.
Por ejemplo, si se tiene el siguiente código:
``` java
String a = "Hola";
String b = "Hola";
String c = new String("Hola");
System.out.println(a == b); // imprime true
System.out.println(a == c); // imprime false
```
En este caso, se crea la cadena "Hola" dos veces: una vez utilizando comillas dobles y otra vez utilizando el constructor new String(). Sin embargo, debido al pool de caracteres, las variables a y b apuntan a la misma instancia de la cadena "Hola" en el pool, mientras que la variable c apunta a una nueva instancia de la cadena "Hola" creada utilizando el constructor new String(). Por lo tanto, la comparación a == b devuelve true, mientras que la comparación a == c devuelve false.

# Estructuras de control

Las instrucciones de control son sentencias que permiten controlar el flujo de ejecución de un programa. Estas instrucciones se dividen en tres categorías:
- Instrucciones de selección o condicionales
-	Instrucciones de iteración o de bucle.
-	Instrucciones de acceso o salto.

## Instrucción IF.

La función principal del if es evaluar la condición de tipo boolean y ejecutar el bloque de la sentencia si cumple la condición boolean. Las llaves solo serán obligatorias solo si el bloque contiene más de una instrucción. 

Opcionalmente una sentencia if puede contener un bloque else. Bloque que solo se ejecutara cuando la condición evaluada en el if no sea correcta.
Pueden darse el caso del uso de if anidados, es decir, múltiples if seguidos.
Puede combinarse el uso de if con condiciones if-else-if

## Instrucción Switch.
Permite la evaluación múltiple de una expresión insertada como parámetro.
Switch es más óptimo y legible frente a la anidación de múltiples if, porque principalmente lee todos los resultados del condicional switch y si encuentra uno ejecuta el bloque de código que este asociado a ese resultado de evaluación. En versión anterior de JDK7 el parámetro de evaluación era un tipo básico numérico, pero a partir de esa versión se pueden evaluar también cadenas de caracteres. 

Cuando una expresión coincide con uno de los valores indicados en los case, se ejecutará el bloque correspondiente de la sentencia, sino se ejecutará el bloque default que ejecutara el bloque cuando se produce este tipo de situaciones, este bloque es opcional.

Dentro de cada bloque case se puede indicar la salida de la instrucción (break) de manera opcional, esto permite finalizar la ejecución del switch. Se pueden tener switch anidados. El valor de los case solo podrán ser literales o constantes.

# Estructuras de repetición

## Bucle for
Un bucle for es una estructura de control de flujo en la programación que permite iterar sobre un conjunto de valores conocido previamente. En otras palabras, es una forma de repetir un bloque de código varias veces, una vez por cada elemento de un conjunto.
Deberemos de tener en cuenta los siguientes aspectos:
-	Las llaves son obligatorias si hay más de una instrucción
-	La sentencia de control siempre debe de ser el resultado un boolean.
-	Las instrucciones de control pueden contener más de una sentencia, separada por una coma. Ej. 
```java
for(int a =0, b =10; a<b; a++, b--)
```
- Las tres instrucciones de control son opcionales
```java
int i = 1;
for (;i<10;) {
	System.out.println(i);
	i++;
}
```
### Variantes del bucle for: Enhanced for (foreach)

En Java, el bucle foreach (también conocido como "bucle for-each") es una forma simplificada de iterar sobre los elementos de un arreglo o una colección, sin necesidad de utilizar un contador o un índice para acceder a cada elemento.
Ej. 
```java
for (tipoDeDato variable : arreglo o colección) {}
```

## Bucle while

El bucle while es una estructura de control de flujo que permite repetir un bloque de código mientras se cumple una determinada condición. El bucle while se utiliza cuando no se sabe el número exacto de veces que se debe repetir un bloque de código, pero se sabe que la repetición debe continuar mientras se cumpla una determinada condición. La condición puede evaluarse al principio, o después de ejecutar el bloque de instrucciones (variante do-While). Las acciones dentro del bloque provocaran que en algún momento la condición deje de cumplirse, sino se considerara un bloque infinito.

La sintaxis básica del bucle while es la siguiente:
```java
while (condición) {
  // instrucciones
}

do {
  //instrucciones
}while(condición)
```
## Break y continue
Son operaciones que alteran el funcionamiento básico de un bucle.
- Break fuerza la salida del bucle
- Continue fuerza a pasar la siguiente iteración
En caso de usar estas sentencias en la ejecución de bucles anidados debemos de tener en cuenta que si no indicamos nada la sentencia break/continue afecta al bucle mas interno pero si queremos cambiar este comportamiento deberemos de indicar un alias/etiqueta para que afecte al bucle que queramos.