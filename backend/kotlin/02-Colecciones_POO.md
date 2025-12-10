<div align="center">
  <img src="../../assets/kotlin_logo.svg">
</div>

## Índice
- [Introducción](#introducción)
- [Arrays y Colecciones](#arrays-y-colecciones)
  - [Arrays](#arrays)
  - [List](#list)
  - [Sets](#sets)
  - [Maps](#maps)
- [Programacion orientada a objetos (POO)](#programacion-orientada-a-objetos-poo)
  - [Modificadores de acceso](#modificadores-de-acceso)
  - [Constructores](#constructores)
  - [Inicialización `init`](#inicialización-init)
  - [Encapsulación (get/set)](#encapsulación-getset)
  - [Herencia](#herencia)
  - [Abstracciones](#abstracciones)
  - [Interfaces](#interfaces)
  - [Polimorfismo](#polimorfismo)
  - [Clases](#clases)
    - [Clases data](#clases-data)
    - [Clases Object (singleton)](#clases-object-singleton)
    - [Clases anidadas y clases internas](#clases-anidadas-y-clases-internas)
    - [Clases selladas (`sealed`)](#clases-selladas-sealed)
    - [Sobrecarga y sobreescritura](#sobrecarga-y-sobreescritura)

# Introducción

Esta sección profundiza en dos pilares cruciales para la construcción de software: la organización de datos y el diseño modular. Exploraremos las diferentes estructuras de colecciones estándar de Kotlin (Listas, Sets y Maps) y la implementación de la POO, incluyendo clases, constructores, herencia, abstracción, interfaces y el uso especializado de clases como data class y sealed class.

# Arrays y Colecciones

Las colecciones estándar tienen variantes **inmutables** y **mutables**.

## Arrays 

```kotlin
val elementos = Array<Int>(3){100}
val numeros = arrayOf(1, 2, 3, 4, 5)
val edades = intArrayOf(10, 20, 30)
val notas = doubleArrayOf(8.5, 7.0, 9.2)
val vacio = arrayOfNulls<String>(3) // null, null, null
val cuadrados = Array(5) { i -> i * i }  // [0, 1, 4, 9, 16]

val matriz = arrayOf(
    arrayOf(1, 2, 3),
    arrayOf(4, 5, 6),
    arrayOf(7, 8, 9)
)
```

## List

Es una agrupación de objetos ordenada que permite elementos duplicados.

```kotlin
val lista = listOf("Lunes", "Martes")
val mutable = mutableListOf("A")
mutable.add("B")
```

**Tipos**

- `listOf`  inmutable
- `mutableListOf` mutable

```kotlin
val lista = listOf("Lunes", "Martes")
val mutable = mutableListOf("A")
mutable.add("B")

// Elimina y ordenar de manera descendente
val listNum = mutableListOf(1, 2, 3)
listNum.removeAt(0)
listNum.sortDescending()
```

**Principales métodos para listas**

- Add
- Remove
- sort
- contains
- indexOf

**Recorrer una lista**

- Un bucle estándar for
- Un bucle forEach

## Sets

No permite elementos duplicados, puede o no estar ordenada, dependiendo de su implementación.

**Tipos**

- `setOf`  inmutable
- `mutableSetOf` mutable

```kotlin
val conjunto = setOf(1, 2, 2)  // [1, 2]
```

**Principales métodos para listas**

- Add
- Remove
- contains

**Recorrer un Set**

- Un bucle estándar for
- Un bucle forEach

## Maps

Es una colección de pares: clave → valor. Cada clave debe ser única.

**Tipos**

- `mapOf`  inmutable
- `mutableMapOf` mutable

**Principales métodos para listas**

- put
- Remove
- keys
- values
- entries

**Recorrer un Map**

- Un bucle estándar for
- Un bucle forEach

```kotlin 
val mapa = mapOf("nombre" to "Ana", "edad" to 30)

val mapaMutable = mutableMapOf<String, Int>()
mapaMutable.put("uno", 1)
mapaMutable.put("dos", 2)

for ((clave, valor) in mapa) {
    println("$clave → $valor")
}
```

# Programacion orientada a objetos (POO)

Clases, herencia, abstracciones e interfaces funcionan como en Java, pero con _syntactic sugar_:
- `data class` genera automáticamente métodos de utilidad.  
- Clases son `final` por defecto → usa `open` para heredar.  
- `sealed class` restringe jerarquías y permite exhaustividad en `when`.

## Modificadores de acceso

| Modificador | Significado                                   |
| ----------- | --------------------------------------------- |
| `public`    | Accesible desde cualquier lugar (por defecto) |
| `private`   | Accesible solo dentro de la clase             |
| `protected` | Solo accesible en la clase y sus subclases    |
| `internal`  | Accesible dentro del mismo módulo             |

```kotlin
class Persona {
    private var secreto = "1234"
    public var nombre = "Juan"
}
```

## Constructores

* **Definición básica**

```kotlin
class Persona {
    var nombre: String = ""
    var edad: Int = 0
}

val persona = Persona()
persona.nombre = "Ana"
persona.edad = 30
```

* **Primario**

```kotlin
class Persona(val nombre: String, var edad: Int)

val p = Persona("Luis", 25)
println(p.nombre)  // Luis
```

* **Secundario**

```kotlin
class Alumno {
    var nombre: String
    var edad: Int

    constructor(nombre: String, edad: Int) {
        this.nombre = nombre
        this.edad = edad
    }
}
```

## Inicialización `init`

El bloque init se ejecuta justo después del constructor primario

```kotlin
class Estudiante(val nombre: String) {
    init {
        println("Creando estudiante con nombre: $nombre")
    }
}
```

## Encapsulación (get/set)

```kotlin
class Usuario {
    var edad: Int = 0
        set(value) {
            field = if (value < 0) 0 else value // field hace referencia al campo edad
        }
        get() field
}
```

## Herencia

En Kotlin, las clases son final por defecto, así que deben marcarse con open para permitir herencia.

```kotlin
open class Animal(val nombre: String) {
    open fun hablar() {
        println("$nombre hace un sonido")
    }
}

class Perro(nombre: String) : Animal(nombre) {
    override fun hablar() {
        println("$nombre dice: Guau")
    }
}

val perro = Perro("Max")
perro.hablar()  // Max dice: Guau
```

## Abstracciones

```kotlin
abstract class Figura {
    abstract fun area(): Double
}

class Circulo(val radio: Double) : Figura() {
    override fun area(): Double = Math.PI * radio * radio
}
```

## Interfaces

Kotlin permite herencia múltiple de interfaces

```kotlin
interface Vehiculo {
    fun encender()
}

class Auto : Vehiculo {
    override fun encender() {
        println("Auto encendido")
    }
}
```

## Polimorfismo

Permite tratar objetos diferentes a través de un mismo tipo base

```kotlin
val lista: List<Figura> = listOf(Circulo(3.0), Circulo(5.0))

for (f in lista) {
    println(f.area())
}

```

## Clases
### Clases data

Se usan para almacenar datos, y automáticamente generan: equals, hashCode, toString, copy, etc

```kotlin
data class Producto(val nombre: String, val precio: Double)

val prod1 = Producto("Pan", 1.0)
val prod2 = prod1.copy(precio = 1.2)
```

### Clases Object (singleton)

```kotlin
object Config {
    val version = "1.0.0"
    fun imprimir() = println("Versión: $version")
}
```

### Clases anidadas y clases internas

```kotlin
class Externa {
    private val mensaje = "Hola"

    class Anidada {
        fun saludar() = "Desde clase anidada"
    }

    inner class Interna {
        fun saludar() = mensaje
    }
}
```

### Clases selladas (`sealed`)

Usadas para modelar tipos restringidos (como enums, pero con más poder):

```kotlin
sealed class Resultado
class Exito(val datos: String) : Resultado()
class Error(val mensaje: String) : Resultado()

fun manejar(r: Resultado) {
    when (r) {
        is Exito -> println("OK: ${r.datos}")
        is Error -> println("Error: ${r.mensaje}")
    }
}
```

### Sobrecarga y sobreescritura

* **Sobrecarga**: varios métodos con el mismo nombre pero diferentes parámetros
* **Sobreescritura**: redefinir comportamiento heredado (`override`)

```kotlin
class Calculadora {
    fun sumar(a: Int, b: Int): Int = a + b
    fun sumar(a: Double, b: Double): Double = a + b
}
```