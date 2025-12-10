<div align="center">
  <img src="../../assets/kotlin_logo.svg">
</div>

## Índice
- [Introducción](#introducción)
- [Características principales](#características-principales)
- [Variables](#variables)
  - [Ámbito de variables y duración de variables](#ámbito-de-variables-y-duración-de-variables)
  - [Inicialización por defecto](#inicialización-por-defecto)
  - [Variables primitivas y Variables de objeto](#variables-primitivas-y-variables-de-objeto)
  - [Inicialización diferida (`lateinit` y `lazy`)](#inicializacióndiferida-lateinitylazy)
- [Tipos de datos](#tipos-de-datos)
  - [Básicos](#básicos)
  - [Conversiones](#conversiones)
    - [Numéricas](#numéricas)
    - [Conversiones: SmartCast, UnSafeCast y SafeCast](#conversiones-smartcast-unsafecast-y-safecast)
- [String](#string)
  - [String templates](#string-templates)
  - [Raw Strings (""" ... """)](#raw-strings---)
- [Operadores](#operadores)
  - [Aritméticos](#aritméticos)
  - [Asignación compuesta](#asignación-compuesta)
  - [Comparación](#comparación)
  - [Lógicos](#lógicos)
- [Null Safety](#null-safety)
- [Estructuras de control](#estructuras-de-control)
  - [Condicional `if`](#condicional-if)
  - [Expresión `when`](#expresión-when)
  - [Bucles](#bucles)
  - [Break y continue](#break-y-continue)

# Introducción

Kotlin es un lenguaje de programación moderno, seguro, expresivo y totalmente interoperable con Java. Fue desarrollado por JetBrains y se convirtió en lenguaje oficial para Android en 2017.

**Ventajas:**
* Sintaxis concisa
* Seguridad ante `null`
* Interoperabilidad con Java
* Compatible con múltiples plataformas (JVM, JavaScript, iOS)

# Características principales

| Característica    | Descripción                                                            |
| ----------------- | ---------------------------------------------------------------------- |
| Conciso           | Menos líneas de código que Java                                        |
| Seguro            | Sistema de tipos que evita errores comunes como `NullPointerException` |
| Interoperable     | Reutiliza código Java sin problemas                                    |
| Multiplataforma   | Puede usarse en Android, backend, navegador (Kotlin/JS) y iOS          |
| Soporte funcional | Soporta funciones lambda y de orden superior                           |

# Variables

```kotlin
val nombre = "Kotlin"   // Inmutable
var edad = 10           // Mutable
```

En Kotlin hay dos formas de declarar variables:
- `val`: para variables de solo lectura (inmutables).
- `var`: para variables mutables.

**Inferencia de tipos:** Kotlin detecta el tipo de la variable al asignar un valor, aunque también puedes declararlo explícitamente:

```kotlin
val activo: Boolean = true
```

## Ámbito de variables y duración de variables

* **Locales**: dentro de funciones o bloques
* **De instancia**: declaradas en clases
* **Estáticas (companion object)**: compartidas por toda la clase
* **Parámetros**: en funciones

## Inicialización por defecto

* Enteros: `0`
* Flotantes: `0.0`
* Booleanos: `false`
* Char: `\u0000`
* Objetos: `null` (si son declarados como opcionales)

## Variables primitivas y Variables de objeto

* **Primitivas**: en Kotlin todos los tipos son objetos, pero el compilador los optimiza como 
tipos primitivos donde es posible.
* **Variables de objeto**: referencian instancias de clases. Al asignar una variable a otra,
ambas apuntan al mismo objeto en memoria.

## Inicialización diferida (`lateinit` y `lazy`)

Es una característica muy útil cuando no puedes o no quieres inicializar una variable en el
momento de su declaración.

* **`lateinit var`**: pospone la asignación de una propiedad **mutable** no nula hasta antes de su primer uso; se comprueba en _runtime_.

```kotlin
lateinit var nombre: String

class Usuario {
    lateinit var nombre: String

    fun inicializar() {
        nombre = "Carlos"
    }

    fun mostrar() {
        println("Nombre: $nombre")
    }
}

fun main() {
    val u = Usuario()
    u.inicializar()
    u.mostrar()  // Nombre: Carlos
}
```

* **`val by lazy { … }`** evalúa la expresión **una sola vez** la primera vez que se accede; es _thread‑safe_ por defecto.

```kotlin
val mensaje: String by lazy {
    println("Inicializando...")
    "Hola Kotlin"
}

fun main() {
    println("Antes del acceso")
    println(mensaje)     // Se inicializa aquí
    println(mensaje)     // Ya no se vuelve a calcular
}
```

# Tipos de datos

## Básicos

| Tipo    | Descripción             | Ejemplo  |
| ------- | ----------------------- | -------- |
| Boolean | true / false            | `true`   |
| Int     | Entero 32 bits          | `42`     |
| Long    | Entero largo            | `42L`    |
| Float   | Decimal simple          | `3.14f`  |
| Double  | Decimal doble precisión | `2.718`  |
| Char    | Carácter Unicode        | `'A'`    |
| String  | Cadena de caracteres    | `"Hola"` |

Versiones sin signo

| Tipo    | Descripción        |
| ------- | ------------------ |
| UByte   | Entero de 8 bits   | 
| UShort  | Entero de 16 bits  |
| UInt    | Entero de 32 bits  |
| ULong   | Entero de 64 bits  |


## Conversiones

### Numéricas
Las conversiones son **explícitas** para prevenir pérdida de precisión:

```kotlin
val x: Int = 10
val y: Long = x.toLong() // Correcto
```

Funciones de conversión comunes:
* `toByte()`, `toShort()`, `toInt()`, `toLong()`
* `toFloat()`, `toDouble()`
* `toChar()`

```kotlin
fun main() {
    val valor: Int = 42
    val largo: Long = valor.toLong()
    val decimal: Double = valor.toDouble()
    val floatVal: Float = 3.14f
    val intFromFloat: Int = floatVal.toInt() // Float → Int (pierde decimales)
    println("Long: $largo, Double: $decimal")
    println("Int desde Float: $intFromFloat")
}
```

### Conversiones: SmartCast, UnSafeCast y SafeCast

Hacer cast (o type casting) significa decirle al compilador que trate un valor de un tipo como si fuera de otro.
En Kotlin hay tres grandes formas de lograrlo

* **Smart-Cast** (`is`) permite al compilador inferir el tipo tras una comprobación
  
```kotlin
fun procesar(x: Any) {
    if (x is String) {        // comprueba el tipo
        println(x.length)     // aquí x es tratado como String automáticamente
    }
}
```

* **Un-Safe-Cast** Obliga al compilador a tratar el valor como otro tipo

```kotlin
val animal: Any = "Gato"
val texto: String = animal as String
val numero: Int   = animal as Int
```

* **Safe-Cast** Devuelve el objeto casteado o null si no se puede.
Evita excepciones y funciona bien con el sistema null–safety.

```kotlin
val dato: Any = 42
val texto: String? = dato as? String   // resultado → null
println(texto?.length ?: "No era String")
```

# String 

Un String es una secuencia inmutable de caracteres. Kotlin utiliza la clase String de la JVM, 
lo que significa que puedes acceder a todos los métodos que Java ofrece.

**Declaración y operaciones básicas**

```kotlin
val mensaje = "Hola, Kotlin"
println(mensaje.length)         // Tamaño: 12
println(mensaje[0])             // 'H'
println(mensaje.substring(0, 4)) // "Hola"
println(mensaje.contains("Kot")) // true
```

**Comparaciones**

```kotlin
val nombre = "Ana"
println(nombre == "Ana")                     // true
println(nombre.equals("ana", ignoreCase=true)) // true
```

## String templates

Kotlin permite interpolación de variables en cadenas con $ y expresiones con ${}:

```kotlin
val edad = 30
val saludo = "Tienes $edad años"
val futuro = "En 5 años tendrás ${edad + 5} años"
```

## Raw Strings (""" ... """)
Cadenas multilínea, sin necesidad de escapar caracteres especiales
Preserva saltos de línea, No necesita escapar caracteres especiales como \n o \",
Ideal para escribir texto multilínea, JSON, SQL, etc.

```kotlin
val texto = """
    Línea 1
    Línea 2
    Línea 3
""".trimIndent() // elimina los espacios comunes al inicio de cada línea
println(texto)
```

# Operadores

## Aritméticos

- Operador de suma (`+`)
- Operador de resta (`-`)
- Operador de multiplicación (`*`)
- Operador división (`/`)
- Operador módulo de la división (`%`)
- Operador de incremento (`++`): se utiliza para aumentar el valor de una variable en uno.
- Operador de decremento (`--`): se utiliza para restar el valor de una variable en uno.
  * Delante de la variable: se realiza primero la operación y luego se lo asigna a la variable el resultado.
  * Detrás de la variable: primero se asigna el valor a la variable y luego se opera.

## Asignación compuesta

- Operador de asignación de suma (`+=`). 
- Operador de asignación de resta (`-=`). 
- Operador de asignación de multiplicación (`*=`). 
- Operador de asignación de división (`/=`). 
- Operador de asignación de modulo (`%=`).

```kotlin
var contador = 5
contador += 3  // contador = 8
```

## Comparación

- Operador menor (`<`). 
- Operador mayor (`>`). 
- Operador menor o igual (`<=`). 
- Operador mayor o igual (`>=`). 
- Operador igual (`==`). 
- Operador distinto de igual (`!=`).

## Lógicos

- and `&&`
- or `||`
- distinto `!`

# Null Safety

Evita errores por referencias nulas:
* `?.`: llamada segura
* `?:`: operador Elvis
* `!!`: asume que no es null (no recomendado)
* `let`: Ejecuta un bloque de código solo si la variable no es null (cuando se combina con `?.`)

```kotlin
val nombre: String? = null
val longitud = nombre?.length ?: 0
println("$longitud")

val saludo = nombre ?: "Desconocido"
println("Hola, $saludo")

val nombre: String? = null
nombre?.let {
    println("El nombre tiene ${it.length} letras")
}  // No imprime nada si es null

```

# Estructuras de control

Las instrucciones de control son sentencias que permiten controlar el flujo de ejecución de un programa. Estas instrucciones se dividen en tres categorías:
- Instrucciones de selección o condicionales
- Instrucciones de iteración o de bucle.
- Instrucciones de acceso o salto.

## Condicional `if`

```kotlin
val max = if (a > b) a else b
```

## Expresión `when`

Es el reemplazo moderno del switch de Java, pero mucho más flexible, limpio y expresivo. 
Puedes usarla tanto como expresión (retorna un valor) como estructura de control.

```kotlin
when (x) {
    x < 0 -> println("Negativo")
    1 -> println("Uno")
    in 2..5 -> println("Rango")
    else -> println("Otro")
}

val vocal = 'a'
when (vocal) {
    'a', 'e', 'i', 'o', 'u' -> println("Es una vocal")
    else -> println("No es una vocal")
}

when (valor) {
    is Int -> println("Es un entero")
    is String -> println("Es un texto")
    is Boolean -> println("Es un booleano")
    else -> println("Tipo desconocido")
}
```

## Bucles

```kotlin
for (i in 1..5) println(i)

// Saltando posiciones
for (i in 1..10 step 2) {
    println(i) // 1, 3, 5, 7, 9
}

//  Inverso
for (i in 5 downTo 1) {
    println(i) // 5, 4, 3, 2, 1
}

// Omitir ultimo valor
for (i in 0 until 5) {
    println(i) // 0, 1, 2, 3, 4
}

// Recorrer una lista
val frutas = listOf("Manzana", "Banana", "Naranja")
for (fruta in frutas) {
    println(fruta)
}

while (x < 10) x++

do {
    println(x)
} while (x < 10)
```

## Break y continue

- `Break` fuerza la salida del bucle
- `Continue` fuerza a pasar la siguiente iteración
- Puedes etiquetar un bucle y luego usar break o continue para controlar bucles anidados

En caso de usar estas sentencias en la ejecución de bucles anidados debemos de tener en 
cuenta que si no indicamos nada la sentencia break/continue afecta al bucle mas interno pero 
si queremos cambiar este comportamiento deberemos de indicar un alias/etiqueta para que 
afecte al bucle que queramos.

```kotlin
// Cuando i es 5, el bucle se rompe y se sale del for.
for (i in 1..10) {
    if (i == 5) break
    println(i)
}

// Cuando i es 3, se salta la impresión y continúa con el siguiente número.
for (i in 1..5) {
    if (i == 3) continue
    println(i)
}

// Uso de etiquetas
outer@ for (i in 1..3) {
    for (j in 1..3) {
        if (i == 2) break@outer
    }
}
```