<div align="center">
  <img src="../assets/JUnit_logo.svg">
</div>

## Índice
- [Introducción](#introducción)
- [Fundametos basicos de una clase unitaria (TestCase)](#fundametos-basicos-de-una-clase-unitaria-testcase)
  - [Anotaciones](#anotaciones)
  - [Anotaciones especiales](#anotaciones-especiales)
  - [Asserts](#asserts)
    - [Grupo Assertions.](#grupo-assertions)
  - [Nested](#nested)
  - [Repetir el numero de test](#repetir-el-numero-de-test)
  - [Tag](#tag)
  - [Parametrizar un test](#parametrizar-un-test)
  - [Inyeccion de dependencias mediante testInfo y testReport](#inyeccion-de-dependencias-mediante-testinfo-y-testreport)
  - [Limitar tiempo de ejecución](#limitar-tiempo-de-ejecución)
- [Ciclo de vida de un Test](#ciclo-de-vida-de-un-test)
- [TDD](#tdd)
  
# Introducción

JUnit se trata de un framework Open Source para la automatización de pruebas (tanto unitarias, como de integración) en los proyectos de Software. JUnit provee al usuario de herramientas, clases y métodos que facilitan la tarea de realizar pruebas en sus sistemas y así asegurar su consistencia y funcionalidad. 

JUnit 5 está compuesto por 3 subproyectos:

- **JUnit Platform**: Sirve como base para lanzar el framework sobre la JVM. Define la API `TestEngine` para descubrir y ejecutar los tests.
  - **API TestEngine**: Es una interfaz para frameworks de pruebas que permite que la Plataforma JUnit descubra y ejecute tests (JUnit Jupiter y JUnit Vintage son ejemplos de TestEngine).
  - **JUnit Platform Suite Engine**: Permite la ejecución de pruebas agrupadas o personalizadas utilizando varios motores de prueba.
  - **Integración con IDEs y Herramientas**: La Plataforma es la capa que permite que IDEs (IntelliJ, Eclipse) y herramientas de *build* (Maven, Gradle) ejecuten las pruebas.
- JUnit Jupiter: Es la combinación del nuevo modelo de programación y el modelo de extensiones para escribir pruebas. Este subproyecto proporciona su  propia TestEngine para ejecutar las pruebas en la plataforma.
- JUnit Vintage: Proporciona un TestEngine para ejecutar pruebas basadas en JUnit 3 y JUnit 4

# Fundametos basicos de una clase unitaria (TestCase)

La principal funcion es realizar test unitarios.
Estos test unitarios los podemos definir como  metodos de pruebas de software mediante el cual se prueban unidades individuales de codigo fuente para determinar si realiza el funcionamiento esperado. 

La principal razon para el uso de estas clases es la verificacion en un futuro lejano que el codigo siga funcionando correctamente

Estas clases tienen la siguiente estructura basica:
- La clase de prueba que contiene uno o más metodos de prueba
- Los métodos no necesitan que sean públicos para ejecutarse.
- Anotaciones y anotaciones especiales
- Asercciones (Assertions).

## Anotaciones

- @Test: Se usa para indicar que metodo se va a usar para ejecutar una prueba unitaria
- @BeforeEach se ejecuta antes de cada método @Test.
- @AfterEach se ejecuta después de cada método @Test.
- @BeforeAll se ejecuta antes de todos los @Test y una sola vez
- @AfterAll se ejecuta después de todos los @Test y una sola vez.

## Anotaciones especiales

Utilidad que nos permite agregar funcionalidades extra que no son obligatorias de usar

- DisplayName: sirve para agregar un texto más explicativo al test
- Disabled: sirve para skiped un test unitario

## Asserts

Las Aserciones son una colección de métodos de utilidad que admite afirmaciones de condiciones en las pruebas. Para ello se usan los siguientes métodos:

- **assertEquals**: Afirma que lo esperado y lo real sean iguales. Se usa para objeto primitivos ya que su función es parecida al usar ==, importante, admite un tercer parametro denominado delta que nos facilita para el tema de numeros un rango mas amplio de verificacion (importante para los decimales)
- **assertSame**: Afirma que lo esperado y lo real se refieren al mismo objeto.
- **assertNotSame**: Afirma que lo esperado y lo real se refieren a diferentes objeto.
- **assertTrue**: Afirma que el valor esperado sea True.
- **assertFalse**: Afirma que el valor esperado sea False.
- **assertNull**: Afirma que el valor esperado sea null.
- **assertNotNull**: Afirma que el valor esperado no sea null.
- **assertTimeout**: Permite verificar si la prueba unitaria a tardado en el tiempo estimado.
- **assertThrows**: Permite verificar que se ha lanzado la excepción esperada. 
```java  
assertThrows(ArithmeticException.class,() -> 1/0, "No se puede dividir entre 0");
```

### Grupo Assertions.

Es la agrupación de multiples assert que se ejecutan de manera individual y si falla alguna de ellas no impide que la ejecución se termine, ya se informara del error posteriormente. Para agrupar todas las aserciones usaremos el método assertAll en el que le pasaremos una descripción y posteriormente los diferentes assert. 

```java
assertAll(
    ()-> assertEquals(20, 10+10),
    ()-> assertEquals(0, 10-10)
);
```

## Nested

Nos permite separar el código de pruebas y agruparlo en bloques que se ejecutaran de manera independiente unos de otros, se puede agregar el displayName

## Repetir el numero de test

Se usa cuando queremos que un test se repita varias veces ya que algunos test pueden cambiar las propiedades o atributos globales y lo que hacemos es que se reinicien. Podemos indicar el numero de veces, para ello usaremos la anotación @RepeatedTest(numero de veces), importante este tipo de métodos no deben de llevar la anotación @Test y pueden recibir como parámetro de método RepetitionInfo.

## Tag

Sirve para clasificar los test y agruparlos para que se ejecuten todas aquellas que tengan asociadas a ellas

## Parametrizar un test

La parametrización de un test es una funcionalidad que nos permite realizar múltiples pruebas sobre un método gracias a que se le pasa una lista de valores. Los parámetros de entrada pueden ser tan sencillos como una lista de valores usando @ValueSource, o más complejos, pasándole un documento csv @CSVSource - @CSVFile, un método @MethodSource o un Enum @EnumSource.

Para que sean mas descriptivos las pruebas se ParameterizedTest tiene los siguientes placeholders
- {DisplayName} y {DisplayNameGeneration} para personalizar los nombres de las pruebas
    ```java
    @ParameterizedTest(name= "Check blank {displayName}")
    ``` 
- {index}: El índice de la ejecución del test (comienza en 1).
    ```java
    @ParameterizedTest(name= "Check blank {index}")
    ``` 
- {arguments}: Una representación basada en toString() de todos los argumentos.
    ```java
    @ParameterizedTest(name= "Check blank {arguments}")
    ``` 
- {0}, {1}, ..., {n}: Representaciones basadas en toString() de los argumentos individuales.
    ```java
    @ParameterizedTest(name= "Check blank {0}")
    ``` 

Parametros de entrada
- Parametrizacion mediante @ValueSource
    ```java
    @ParameterizedTest
    @ValueSource(strings = {"abc","asd",""})
    void checkBlanks(String value){
        assertTrue(StringsUtils.isBlank(value));
    }
    ``` 
- Parametrizacion mediante @EnumSource
    ```java
    enum EnumValues{
        ABC, ASD, WXY
    }

    @ParameterizedTest
    @EnumSource(value = EnumValues.class, names = {"ABC"}, mode = EnumSource.Mode.EXCLUDE)
    public void excludeEnumValue(Object value){
        System.out.println(value.toString());
    }

    @ParameterizedTest
    @EnumSource(value = EnumValues.class, names = {"A.."}, mode = EnumSource.Mode.MATCH_ALL)
    public void matchAllEnumValue(Object value){
        System.out.println(value.toString());
    }
    ```

- Parametrizacion mediante @MethodSource
    ```java
    @ParameterizedTest(name = "{index} => a={0}, b={1}, sum={2}")
    @MethodSource("addProviderData")
    public void addTest(int a, int b, int sum){
        assertEquals(sum, a + b);
    }

    private static Stream<Arguments> addProviderData(){
        return Stream.of(
            Arguments.of(6,2,8),
            Arguments.of(-6,-2,-8),
            Arguments.of(6,-2,4)
        );
    }
    ```
- Parametrizacion mediante @CsvSource
    ```java
    @ParameterizedTest
    @CsvSource({
        "Audi,55", 
        "Tesla,99",
        "Ferrari,101"
    })
    public void csvSourceMethod(String car, int quantity){
        System.out.println(car + ": "+quantity);
    }
    ```
- Parametrizacion mediante @CsvFileSource
    ```java
    @ParameterizedTest
    @CsvFileSource(files = "src/test/java/resources/input.csv")
    public void csvFileSource(String car, int quantity){
        System.out.println(car + ": "+quantity);
    }
    ```

## Inyeccion de dependencias mediante testInfo y testReport

- TestInfo: Es un componente de unit que nos permite mostrar mensajes por consola mas detallados como puede ser el nombre del método, el displayname, los parámetros, los tags….
- TestReport: Es un componente de unit que nos permite registrar en el log información que queramos anexar en la salida junto un timestamp, algo mas elaborado que un simple mensaje por consola

## Limitar tiempo de ejecución

Junit 5 ofrece dos mecanismos principales para limitar el tiempo de ejecución

**1. Anotación de Time-out (@Timeout):**
Se aplica al método `@Test` y detiene la ejecución del test si excede el tiempo especificado. Es una forma **agresiva** de terminar una prueba que se queda "colgada".

```java
// Unidad de tiempo por defecto: segundos
@Test
@Timeout(5)
void testConTimeoutDe5Segundos() { /* ... */ } 

// Unidad de tiempo explícita
@Test
@Timeout(value = 500, unit = TimeUnit.MILLISECONDS)
void testConTimeoutDe500Milisegundos() { /* ... */ }
```

**2. Aserción de Time-out (assertTimeout):**
Se utiliza dentro del método @Test para verificar que una porción específica de código se ejecuta dentro de un límite de tiempo. Es una verificación suave que informa si la duración fue excedida.
```java
@Test
void assertTimeoutTest(){
    // Verifica que el bloque de código se ejecute en menos de 500ms
    assertTimeout(Duration.ofMillis(500), ()->{
        // operacion a realizar
    });
}
```

# Ciclo de vida de un Test

La vida útil de un test la podemos definir por método o por clase indicando el ciclo de vida o según las propiedades del sistema donde se ejecute.

Si forzamos la vida útil de un test por entorno tendremos las siguientes casuísticas:

- Habilitar o deshabilitar un Test según el sistema operativo instalado. @EnabledOnOS(org.junit.jupiter.api.condition.os.x)@DisabledOnOs(org.junit.jupiter.api.condition.os.x)
- Habilitar o deshabilitar un test por una versión concreta de un sistema operativo @EnabledIfSystemProperty(matches = “Windows 7”, named = ”os.name”) @DisabledIfSystemProperty(matches = “Windows 7”, named = ”os.name”)
- Habilitar o deshabilitar un Test por versión del JRE @EnabledOnJre(org.junit.jupiter.api.condition.JRE.JAVA_9) @DisabledOnJre(org.junit.jupiter.api.condition.JRE.JAVA_9)
- Habilitar un test por varible de entorno @EnabledIfEnvironmentVariable @DisabledIfEnvironmentVariable 

Si forzamos un test por ciclo de vida, definimos cómo JUnit crea la instancia de la clase de prueba:

- **Por defecto (PER_METHOD):** Se crea una **nueva instancia** de la clase de prueba para *cada* método `@Test`. Esto garantiza el aislamiento entre pruebas, pero obliga a que los métodos `@BeforeAll` y `@AfterAll` sean `static`.
- **Por Clase (PER_CLASS):** Se crea **una única instancia** de la clase de prueba para *todos* los métodos `@Test`. Esto es útil cuando la configuración inicial (`@BeforeAll`) es muy costosa, y además permite que `@BeforeAll` y `@AfterAll` sean métodos de instancia (no `static`).

Se define usando la anotación `@TestInstance(Lifecycle.x)`:

```java
@TestInstance(Lifecycle.PER_CLASS)
class MiTestSuite {
    // @BeforeAll no necesita ser static
    @BeforeAll
    void setupGlobal() { /* ... */ }
}
```

# TDD

TDD o Test-Driven Development (desarrollo dirigido por tests) es una práctica de programación que consiste en escribir primero las pruebas (generalmente unitarias), después escribir el código fuente para que pase la prueba de manera satisfactoria y por último refactorizar el código escrito.
Con este patrón de diseño nos permite crear un código más robusto, más seguro y más mantenible.
La implementación de este patrón en metodologías agiles seria de la siguiente manera:
- El cliente escribe su historia de usuario.
- Se escribe junto al cliente los criterios de aceptación.
- Se selecciona un criterio de aceptación para su implementación (prueba unitaria).
- Se comprueba que esta falla.
- Se escribe el código para que pase la prueba.
- Se ejecutan las pruebas automatizadas.
- Se refactoriza y limpia el código 
- Se vuelven a pasar todas las pruebas automatizadas para comprobar que todo funciona.
- Volvemos al punto 3 y repetimos todo el proceso hasta acabar con los criterios de acceptacion.

Los principales puntos negativos de este patrón de diseño son los siguientes:
- Problemas sobre interfaces gráficas
- Base de datos, ya que debemos de contar con unos datos conocidos y verificar que el contenido de la base de datos sea el esperado, para esto la solución es usar objetos simulados (MockObject).
- Saber entender el correcto funcionamiento de este patrón para que realmente sea productivo. Saber refactorizar el código correctamente para que sea más optimo y consistente.

Para un correcto funcionamiento e implementación de los test debemos de tener encuenta lo siguiente:
- Deben de ser cortos.
- No deben de modificar o crear información para otros test.
- Deben de ser independientes (orden de ejecución al azar).
- Implementar test con datos que sean fáciles de leer y entender.
- Implementar métodos staticos de carga, para evitar que los datos que se puedan actalizar en nuestros objetos se pasen a otros test unitarios

Uso de datos reales o similares cuando sea necesario.