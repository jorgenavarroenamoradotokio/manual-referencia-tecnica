<div align="center">
  <img src="../../assets/kotlin_logo.svg">
</div>

## Índice
- [Introducción](#introducción)
- [Funciones](#funciones)
- [Funciones de ámbito (`let`, `also`, `run`, `apply`, `with`)](#funciones-de-ámbito-let-also-run-apply-with)
- [Lambdas](#lambdas)
- [Excepciones](#excepciones)
- [Corrutinas](#corrutinas)
  - [Conceptos clave](#conceptosclave)
- [Anotaciones comunes](#anotacionescomunes)

# Introducción

Este documento aborda los temas más avanzados y expresivos de Kotlin, centrándose en la programación funcional y la concurrencia. Cubrirás el uso avanzado de funciones (extensiones, orden superior), la potencia de las expresiones lambda y las funciones de ámbito (let, run, apply, with), el manejo de excepciones, y la solución moderna de Kotlin para la programación asíncrona y no bloqueante: las Corrutinas.

# Funciones 

```kotlin
fun saludar(nombre: String): String  = return "Hola, $nombre"
```

**Valores por defecto**:

```kotlin
fun saludar(nombre: String = "Invitado")
```

* **Sobrecarga de funciones**: 
 
```kotlin
mostrar("Programador", "Kotlin")
mostrar("Programador")
mostrar(language = "Kotlin")

fun mostrar(job: String) = println(job)
fun mostrar(job: String = "Administrador", language: String) = println("Trabajo $job - Lenguaje $language")
```

* **Funciones infix**:

Las funciones infix permiten un estilo más natural de lectura, como 5 por 3 en lugar de 5.por
(3).

```kotlin
infix fun Int.por(x: Int) = this * x
println(5 por 3) // 15
```

* **Parámetros variables (`vararg`)**:

```kotlin
fun imprimir(vararg mensajes: String)
```

* **Extensiones**:

```kotlin
fun String.mayusculas(): String = this.uppercase()

val msg: String = "hola"
println(msg.mayusculas())
```

* **Orden superior**:

```kotlin
fun operar(a: Int, b: Int, f: (Int, Int) -> Int): Int = f(a, b)
val suma = operar(2, 3) { x, y -> x + y }
```

# Funciones de ámbito (`let`, `also`, `run`, `apply`, `with`)

Las scope functions ejecutan un bloque dentro del contexto de un objeto y devuelven, según el caso, el resultado del bloque o el propio objeto.

| Función | Receptor (this/it) | Devuelve        | Uso típico |
|---------|-------------------|-----------------|------------|
| `let`   | `it`              | Resultado bloque| Ejecutar lógica si no es null; transformar |
| `also`  | `it`              | Objeto          | Side‑effects (logging, debug)              |
| `run`   | `this`            | Resultado bloque| Calcular y devolver valor                  |
| `apply` | `this`            | Objeto          | Configurar/ inicializar objeto             |
| `with`  | `this`            | Resultado bloque| Agrupar operaciones sobre un objeto        |


```kotlin
// let
val nombre: String? = "Kotlin"
nombre?.let {
    println("La longitud es ${it.length}")
}

// also
val lista = mutableListOf("A", "B")
lista
    .also { println("Antes: $it") }
    .add("C")

// run
val texto: String? = "Texto"
val longitud = texto?.run { length } // solo si texto no es null

// apply
data class Person(var nombre: String = "", var edad: Int = 0)
val usuario = Person().apply {
    nombre = "Carlos"
    edad = 25
}
println(usuario) // Person(nombre=Carlos, edad=25)

// with
val builder = StringBuilder()
val resultado = with(builder) {
    append("Hola, ")
    append("mundo!")
    toString()
}
println(resultado) // Hola, mundo!
```

# Lambdas

Una lambda es una función anónima (sin nombre) que puedes
* Guardar en una variable
* Pasar como argumento a otra función
* Devolver como resultado desde otra función
* No puedes usar `return` para salir directamente de una función externa dentro de una lambda.
En ese caso se puede usar `return@nombreEtiqueta` o una función anónima

```kotlin
val nombreLambda: Tipo = { parámetros -> cuerpo }

// Anonima
val saludar = { println("Hola Kotlin") }
saludar() // Imprime: Hola Kotlin

// Con parametros
val cuadrado: (Int) -> Int = { x -> x * x }
println(cuadrado(4))  // 16

// Con multiples parametros
val suma: (Int, Int) -> Int = { a, b -> a + b }
println(suma(2, 3))  // 5

// inferencia automatica de tipos
val resta = { a: Int, b: Int -> a - b }


// Uso en función de orden superior
fun procesarLista(lista: List<Int>, operacion: (Int) -> Int): List<Int> {
    return lista.map(operacion)
}
```

**Parametro it**: Cuando hay solo un parámetro, Kotlin permite usar la palabra clave it
automáticamente

```kotlin
val triple = { it: Int -> it * 3 }
val resultado = triple(4)  // 12

val triple: (Int) -> Int = { it * 3 }
```

**Lambdas como argumentos a funciones**

```kotlin
fun operar(a: Int, b: Int, operacion: (Int, Int) -> Int): Int {
    return operacion(a, b)
}

val resultado = operar(5, 3) { x, y -> x * y }
println(resultado)  // 15
```

**Lambdas en colecciones**

```kotlin
// Filter
val lista = listOf(1, 2, 3, 4, 5)
val pares = lista.filter { it % 2 == 0 }  // [2, 4]

// map
val dobles = lista.map { it * 2 }  // [2, 4, 6, 8, 10]

// forEach
lista.forEach { println(it) }
```

**Lambdas como retorno de funciones**

```kotlin
fun generadorDeMultiplicador(factor: Int): (Int) -> Int {
    return { numero -> numero * factor }
}

val porTres = generadorDeMultiplicador(3)
println(porTres(4))  // 12
```

# Excepciones

```kotlin
try {
    val resultado = 10 / 0
} catch (e: ArithmeticException) {
    println("Error: ${e.message}")
} finally {
    println("Finalizando")
}

val edad = 2
if (edad < 18) {
    throw IllegalArgumentException("Debe ser mayor de edad")
} else {
    println("Edad válida")
}
```

# Corrutinas

Las corrutinas son la solución de Kotlin para la **concurrencia asíncrona y no bloqueante**.

## Conceptos clave

| Término | Qué hace | Ejemplo |
|---------|----------|---------|
| `suspend` | Marca una función que puede **suspenderse** sin bloquear el hilo. | `suspend fun fetch(): String` |
| `CoroutineScope` | Alcance donde viven las corrutinas; gestiona su cancelación. | `scope.launch { … }` |
| `launch` | Inicia una corrutina que no devuelve resultado. | `scope.launch { actualizarUI() }` |
| `async/await` | Devuelve un `Deferred<T>` para obtener un valor futuro. | `val datos = async { api.get() }.await()` |
| `Dispatcher` | Decide en qué hilo/hilos se ejecuta. | `withContext(Dispatchers.IO) { … }` |

```kotlin
fun main() = runBlocking {
    val tiempo = measureTimeMillis {
        val uno = async { tareaPesada(1) }
        val dos = async { tareaPesada(2) }
        println("Resultado = ${uno.await() + dos.await()}")
    }
    println("Completado en $tiempo ms")
}
```

> **Tip**: Usa **`SupervisorJob`** para que el fallo de una corrutina hija no cancele sus hermanas.

# Anotaciones comunes

| Anotación | Propósito |
|-----------|-----------|
| `@JvmStatic` | Expone método/propiedad como `static` para Java. |
| `@JvmOverloads` | Crea sobrecargas para parámetros con valor por defecto. |
| `@JvmField` | Expone propiedad como campo público. |
| `@Serializable` (kotlinx.serialization) | Genera _serializers_ en tiempo de compilación. |
| `@Parcelize` | Implementa automáticamente `Parcelable` en Android. |
| `@Inject` / `@HiltAndroidApp` | DI con Dagger/Hilt. |
| `@OptIn` | Habilita APIs experimentales. |
