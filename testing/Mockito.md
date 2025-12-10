<div align="center">
  <img src="../assets/Mockito_logo.png">
</div>

## Índice
- [Introducción](#introducción)
  - [Dependencias necesarias](#dependencias-necesarias)
  - [Conceptos clave](#conceptos-clave)
  - [Características y Limitaciones](#características-y-limitaciones)
  - [Inyección de Mocks (Anotaciones)](#inyección-de-mocks-anotaciones)
    - [Activación de Anotaciones (JUnit 5)](#activación-de-anotaciones-junit-5)
    - [Anotaciones Esenciales](#anotaciones-esenciales)
    - [Ejemplo Básico de Anotaciones](#ejemplo-básico-de-anotaciones)
    - [Simulación de Valor de Retorno](#simulación-de-valor-de-retorno)
    - [Simulación de Excepciones](#simulación-de-excepciones)
  - [Verificación y Captura de Argumentos](#verificación-y-captura-de-argumentos)
    - [Verificación de Llamadas (verify)](#verificación-de-llamadas-verify)
    - [Argument Matchers](#argument-matchers)
    - [Captura de Argumentos (ArgumentCaptor)](#captura-de-argumentos-argumentcaptor)
  - [Spy](#spy)
  - [Comportamiento Personalizado (Answer)](#comportamiento-personalizado-answer)
  - [Mocks en Clase (Mocking Static/Final/Private Methods)](#mocks-en-clase-mocking-staticfinalprivate-methods)
    - [Mocking de Métodos Estáticos y Finales (Mockito Inline)](#mocking-de-métodos-estáticos-y-finales-mockito-inline)
    - [Manejo de Métodos Privados](#manejo-de-métodos-privados)
  - [Buenas prácticas recomendadas](#buenas-prácticas-recomendadas)
  
# Introducción

Mockito es el framework de mocking más utilizado en el ecosistema Java, orientado a pruebas unitarias con JUnit 5.
Permite:
- Simular dependencias complejas.
- Controlar comportamientos de datos externos, APIs o sistemas no deterministas.
- Aislar la lógica de negocio para pruebas precisas y reproducibles.

- **Objetivo**: Simular el comportamiento de componentes/capas de servicio, APIs o datos sobre cuyo funcionamiento o casuísticas no tenemos control.
- **Metodología**: Facilita la implementación de la capa Arrange-Act-Assert (AAA) en las pruebas unitarias, que se alinea con el Desarrollo Impulsado por el Comportamiento (BDD - Behavior Driven Development).

## Dependencias necesarias

```xml
<dependency>
    <groupId>org.mockito</groupId>
    <artifactId>mockito-core</artifactId>
    <version>5.10.0</version>
    <scope>test</scope>
</dependency>

<dependency>
    <groupId>org.mockito</groupId>
    <artifactId>mockito-junit-jupiter</artifactId>
    <version>5.10.0</version>
    <scope>test</scope>
</dependency>

<dependency>
    <groupId>org.mockito</groupId>
    <artifactId>mockito-inline</artifactId>
    <version>5.10.0</version>
    <scope>test</scope>
</dependency>
```

## Conceptos clave

| Concepto     | Descripción                                                                  |
| ------------ | ---------------------------------------------------------------------------- |
| **Mock**     | Objeto simulado totalmente controlado por Mockito.                           |
| **Spy**      | Envuelve un objeto real, permitiendo mockear parcialmente su comportamiento. |
| **Stubbing** | Definir qué debe devolver un mock ante una llamada.                          |
| **Verify**   | Confirmar si un método fue invocado y cuántas veces.                         |
| **Captor**   | Capturar valores pasados a un mock para validarlos.                          |
| **Answer**   | Simulación avanzada basada en los parámetros recibidos.                      |

## Características y Limitaciones

- **Métodos Mockeables**: Solo se pueden simular métodos de carácter público o default.
- **Creación Manual de Mocks**:
    - **Sintaxis Completa**: MiClase mock = Mockito.mock(MiClase.class);
    - **Sintaxis Abreviada** (con importación estática de Mockito.mock): MiClase mock = mock(MiClase.class);
- **Limitaciones y Recomendaciones**
  - **Métodos privados**: Mockito no permite simularlos directamente. La **práctica estándar recomendada** es la **refactorización** del código de producción (cambiar la visibilidad del método o extraer la lógica a un colaborador inyectable) para mejorar la testeabilidad. **PowerMock** se considera una solución de **último recurso** para código legado, debido a su complejidad y falta de mantenimiento activo.
  - **Métodos estáticos y finales**: Se pueden simular usando la extensión `mockito-inline`

## Inyección de Mocks (Anotaciones)

Para simplificar la inicialización y la inyección de dependencias, Mockito proporciona varias anotaciones.

### Activación de Anotaciones (JUnit 5)

Para que las anotaciones funcionen, debes activar la extensión de Mockito:

```java
@ExtendWith(MockitoExtension.class)
class MiTest { }
```

### Anotaciones Esenciales

| Anotación        | Propósito                                                                  |
| ---------------- | -------------------------------------------------------------------------- |
| **@Mock**        | Crea un objeto simulado (mock). Equivale a usar Mockito.mock()|
| **@Spy**         | Crea un espía de un objeto real. Llama a los métodos reales por defecto|
| **@InjectMocks** | Crea una instancia de la clase bajo prueba e inyecta automáticamente los campos @Mock y @Spy necesarios. Nota: La clase debe ser una implementación (no una interfaz)|
| **@Captor**      |Crea una instancia de ArgumentCaptor para capturar argumentos pasados a un método de un mock |


### Ejemplo Básico de Anotaciones

```java
@ExtendWith(MockitoExtension.class)
class AddServiceTest {

    @InjectMocks
    private Add addService; // Clase bajo prueba (real)

    @Mock
    private ValidNumber validNumberMock; // Dependencia (simulada)

    @Test
    void addTest(){
        // Usamos el servicio real, que internamente usa el mock.
        addService.add(3, 2); 
        
        // Verificamos que el mock haya sido llamado.
        Mockito.verify(validNumberMock).check(3);
    }
}
```

### Simulación de Valor de Retorno

Se utiliza la estructura when(llamada-al-mock).thenReturn(resultado).

```java
@Test
void addCalculadoraTest(){
    // Cuando el mock de calculadora llama a sumar(2, 3), devuelve 5.
    when(calculadoraMock.sumar(2, 3)).thenReturn(5);
    
    assertEquals(5, calculadoraMock.sumar(2, 3));
}
```

### Simulación de Excepciones

Se utiliza thenThrow para simular llamadas que lanzan excepciones.

```java
@Test
void addMockExceptionTest(){
    // Cuando se llama a checkZero(0), lanza una ArithmeticException.
    when(validNumberMock.checkZero(0)).thenThrow(new ArithmeticException("msg"));
    
    // Verificamos que la excepción se lance.
    assertThrows(ArithmeticException.class, () -> {
        validNumberMock.checkZero(0);
    });
}
```

## Verificación y Captura de Argumentos

El método verify es crucial para asegurar que la lógica del código interactúa correctamente con sus dependencias simuladas.

### Verificación de Llamadas (verify)

| Concepto |  Descripción      |  Sintaxis (Ejemplo) |
|----------|-------------------|---------------------|
| **Llamada Simple** | Asegura que un método fue llamado exactamente una vez.| verify(mock).metodo(parametros);|
| **Número Específico** | Asegura que un método fue llamado n veces. | verify(mock, times(2)).metodo(parametros);|
| **Nunca Llamado** | Asegura que un método nunca fue llamado. |verify(mock, never()).metodo(parametros);|
| **Al Menos n Veces** | Asegura que fue llamado al menos n veces.|verify(mock, atLeast(2)).metodo(parametros);|
| **Al Menos Una Vez** | Asegura que fue llamado al menos una vez.|verify(mock, atLeastOnce()).metodo(parametros);|
| **Como Máximo n Veces** | Asegura que fue llamado como máximo n veces.|verify(mock, atMost(4)).metodo(parametros);|
| **Sin Interacciones** | Asegura que no hubo ninguna interacción con ninguno de los mocks.|verifyNoInteractions(mock1, mock2);|

### Argument Matchers

Permiten hacer coincidir los argumentos de métodos simulados de manera flexible, sin especificar valores exactos. Son útiles cuando el valor exacto del argumento es irrelevante o difícil de predecir.
- **Comodines Comunes**: anyInt(), anyString(), any(Clase.class), eq("valor") (para mezclar un valor exacto con un matcher).

```java
@Test
void argumentMatcherTest(){
    // Simula el retorno TRUE si se llama con CUALQUIER entero.
    when(validNumberMock.check(anyInt())).thenReturn(true);
    
    assertTrue(validNumberMock.check(4));
    assertTrue(validNumberMock.check(100));

    // Verificación con matcher:
    verify(validNumberMock).check(anyInt());
}
```

### Captura de Argumentos (ArgumentCaptor)

Se utiliza para capturar e inspeccionar el valor exacto de un argumento que se pasó a un método de un mock, lo cual es útil si el valor es generado internamente por la clase bajo prueba.

```java
@Test
void testProcesarGuardaDatoProcesado(@Captor ArgumentCaptor<String> captor) {
    // ... setup
    servicio.procesar("dato");

    // 1. Verificamos que se llamó al método y capturamos el argumento.
    verify(repositorioMock).guardar(captor.capture());

    // 2. Obtenemos el valor capturado y hacemos aserciones sobre él.
    String valorCapturado = captor.getValue();
    assertEquals("dato_procesado", valorCapturado);
}
```

## Spy

Un **Spy** es un híbrido entre un objeto real y un mock. Por defecto, un Spy llama a los métodos reales de la clase (a diferencia de un Mock que devuelve valores por defecto).

- **Uso**: Es ideal cuando solo quieres simular el comportamiento de algunos métodos de una clase real, manteniendo el comportamiento original en los demás.
- **Restricción**: Solo se puede crear un spy en clases no-finales.

**Importante**: Usar doReturn
Cuando se simula un método en un Spy, es altamente recomendable usar doReturn en lugar de when. Usar when puede causar la ejecución del método real dos veces (una real y una simulada), lo cual puede llevar a efectos secundarios no deseados.

```java
@Spy
private Calculadora calculadoraSpy = new Calculadora(); // Crea una instancia real

@Test
void spyTest() {
    // Recomendado para Spy: Evita la ejecución doble del método real.
    doReturn(100).when(calculadoraSpy).sumar(10, 5); 
    
    assertEquals(100, calculadoraSpy.sumar(10, 5)); // Retorna 100 (simulado)
    
    // Si llama a otro método que no ha sido simulado, ejecuta el real.
    assertEquals(5, calculadoraSpy.restar(10, 5)); // Retorna 5 (real)
}
```

## Comportamiento Personalizado (Answer)

Answer se utiliza para definir un comportamiento personalizado y dinámico cuando se invoca un método en un mock. Es útil si el resultado simulado depende de los parámetros de entrada o si se necesita una lógica más compleja que thenReturn.

```java
@Test
void addDoubleToIntTest(){
    // Definición del comportamiento personalizado
    Answer<Integer> answer = invocation -> {
        // Lógica: Se accede a los argumentos pasados
        double arg = invocation.getArgument(0);
        return (int) Math.floor(arg);
    };

    // Asignamos el Answer
    when (validNumberMock.dobleToInt(anyDouble())).thenAnswer(answer);
    
    assertEquals(7, validNumberMock.dobleToInt(7.7));
    assertEquals(5, validNumberMock.dobleToInt(5.9));
}

when(validNumber.dobleToInt(anyDouble()))
    .thenAnswer(invocation -> {
        double valor = invocation.getArgument(0);
        return (int) Math.floor(valor);
    });
```

## Mocks en Clase (Mocking Static/Final/Private Methods)

Por defecto, Mockito está diseñado para trabajar con buenas prácticas de orientación a objetos, donde las dependencias se inyectan y la lógica privada no se prueba directamente.

### Mocking de Métodos Estáticos y Finales (Mockito Inline)

Mockito no permite mockear métodos estáticos y finales por defecto. Para estas situaciones, se requiere la extensión **Mockito Inline**, incluida en la dependencia `mockito-core` desde la versión 3.x, que permite realizar estas simulaciones sin librerías externas complejas.

Se utiliza la clase `Mockito.mockStatic()`:

```java
@Test
void mockStaticMethodTest() {
    // 1. Activar el mock para la clase estática.
    // El bloque try-with-resources es crucial para deshabilitar el mock automáticamente.
    try (MockedStatic<UtilidadesEstaticas> mockedStatic = Mockito.mockStatic(UtilidadesEstaticas.class)) {

        // 2. Simular el comportamiento estático.
        mockedStatic.when(UtilidadesEstaticas::obtenerFechaActual).thenReturn("2025-01-01");

        // 3. Prueba
        assertEquals("2025-01-01", UtilidadesEstaticas.obtenerFechaActual());
    } 
    // Al salir del bloque try, el mock estático se deshabilita automáticamente.
}
```

### Manejo de Métodos Privados

Mockito no tiene soporte nativo para mockear métodos privados. Esto se debe a que la prueba unitaria debe enfocarse en el comportamiento público de la unidad (la clase) y no en su implementación interna.

- **Opción Recomendada (Refactorización)**: La solución moderna y preferida es refactorizar el código de producción:
  - Extraer la lógica del método privado a una clase de colaboración y inyectarla en la clase bajo prueba.
  - Cambiar la visibilidad del método (a protected o default) si es necesario para pruebas, manteniendo el encapsulamiento en lo posible.
- **Solución para Código Legado (PowerMock)**: La librería **PowerMock** permitía el mocking de métodos privados. Sin embargo, su uso está **fuertemente desaconsejado** en proyectos nuevos o activos, ya que añade gran complejidad, interfiere con las API de Mockito/JUnit 5 y carece de mantenimiento activo.

## Buenas prácticas recomendadas

- Mockea solo lo necesario
  - No mockees objetos simples (POJOs, DTOs).
  - No mockees colecciones, Strings o tipos primitivos.
  - No mockees métodos que ya son deterministas y baratos
- Mockea solo las dependencias externas de la clase bajo prueba
  - La clase bajo prueba debe ser real, no mockeada
  - Mockear repositorios, API clients, servicios externos.
  - No mockear tu propia lógica interna.
- Evita usar any() sin necesidad
- Usa eq() cuando mezcles ArgumentMatchers
- Usa doReturn() en spies
- Evita el uso excesivo de verify()
- Mantén el patrón AAA (Arrange – Act – Assert)
- Escribe pruebas independientes y deterministas
  - No dependas del orden de ejecución.
  - Evita el uso de datos aleatorios.
  - No dependas del tiempo real (mock estáticos para fechas).
- Usa nombres de test descriptivos
- Mantén los tests cortos y con una sola responsabilidad