## Naming

  ### Nombres con sentido

  Una de las tareas más difícil de programar es dar con buenos nombres a las variables y funciones, debe ser corto pero a la vez explicativo. Evitar nombres que no sean explicativos:

  ##### No hacer
  ```javascript
  const theThing = '';
  const a = '...'; 
  ```

  ### Evitar abreviaciones

  Se deben evitar abreviaciones o iniciales. Estas dificultan la lectura, lo que para uno puede ser unas iniciales y-o abreviaciones obvia para otro no tiene por qué serlo:

  ##### No hacer
  ```javascript
  const msg= 'message'; 
  const upi = 'user profile image'; 
  ```

  ##### Hacer
  ```javascript
  const message= 'message'; 
  const userProfileImage = 'user profile image'; 
  ```

  Siendo honestos esta regla no está libre de excepciones, existen casos en que usar abreviaciones o iniciales está bien, por ejemplo `bbdd` o usar un iterador `i` en vez de `index`. Sin embargo, como regla general se deben reducir al mínimo las abreviaciones.
  

  ### Inglés

  ¡Se programa en inglés! Esto es algo medio contra-intuitivo considerando que somos Chilenos y hablamos Chileno. Entonces, ¿por qué en inglés? La principal razón es porque la programación es un lenguaje universal que no depende del país. Acá un listado de más razones:

  * A la mente le cuesta leer spanglish, el proceso mental de saltar de un idioma a otro es difícil. Los lenguajes de programación de por si son en inglés, por lo que programar en español te genera confusión. 
  * Expandiendo sobre el mismo tema, las librerías y frameworks son en inglés, por lo que mezclar idiomas dificulta la lectura. 
  * Pueden haber colegas que hablan distintos idiomas (hoy o en el futuro), por lo que se tiene que programar en un idioma común: inglés.
  * Por último es una buena opción para practicar inglés :)
  
  [Acá](https://softwareengineering.stackexchange.com/questions/1483/do-people-in-non-english-speaking-countries-code-in-english) hay una interesante discusión al respecto, donde se debate para ambos lados.

  :::tip Consejo Personal
  Para los programadores que no se manejen bien en inglés esto puede algo muy difícil, pero mi recomendación es que intenten de familiarizarse en inglés. Las documentaciones, las mejores preguntas/respuestas de los foros, los blogs, etc. suelen estar en inglés. 
  :::

  ### Boolean

  La convención más común sobre booleans es una el prefijo "is" o "has", por ejemplo, `isActive` o `hasAccess`. Se asemeja más al lenguaje natural que si la llamamos `active`. 

  Como segunda ley: ¡Piensa positivo! las variables boolean tienen que ser positivas, por ejemplo llamar la variable `isActive` y no `isNotActive`. Y la razón es simple, la negación de una variable negativa es confusa: `!isNotActive`, a nuestro cerebro le cuesta procesar una doble negación.

  Más sobre booleans [acá](https://dev.to/michi/tips-on-naming-boolean-variables-cleaner-code-35ig#:~:text=There%20is%20a%20convention%20to,just%20thrown%20out%20the%20window).


  ### Funciones

  Cada función es una accion, por ende el nombre debe contener al menos un verbo. No está de más repetir que los nombres deben ser auto explicativos y evitar abreviaciones.


  #### no hacer

  ```javascript
  function absoluteDifference() { ... } // falta un verbo
  function inc() { ... } // Abreviación, es increase, increment, include?
  function getAbsoluteDifferrenceOfTwoNumbers() { ... } // innecesariamente largo
  ``` 

  #### hacer

  ```javascript
  function getAbsoluteDifference() { ... }
  function increase() { ... } 
  ``` 

  Para más sobre nombrando funciones, recomiendo [este](https://dmitripavlutin.com/coding-like-shakespeare-practical-function-naming-conventions/) artículo.


  ### Array

  Los nombres de los arreglos deben ser en plural. `students.forEach((student) => {... })`;



  ### Conclusión

  Como conclusión, al programar hay que intentar de imitar el lenguaje natural. Esto va a facilitar la lectura y comprensibilidad del código ¡Tómate un minuto para pensar los nombres!


## Cases

  Lo más importante con los cases es ser consistentes, esta consistencia muchas veces depende del lenguaje, es decir distintos lenguajes usan distintos cases, Existen distintos tipos de cases:

  * camelCase
  * PascalCase
  * TRAIN-CASE
  * snake_case
  * kebab-case
  * MACRO_CASE


  ### Variables y Funciones

  En javascript las variables y funciones se escriben en camelCase. 

  ### Constantes Globales

  Las variables que son una constante "global" se escriben en MACRO_CASE. No confundir con variables definidas con `const`, por constante global nos referimos a variables cuyo valor es una verdad absoluta, está fijo, jamás será cambiado y, normalmente, no depende de parámetros. Por lo general estas constantes son declaradas al comienzo del archivo.

  #### No Hacer

  ```javascript
  const STUDENT_NAME = getStudentName(studentId);
  ```

  Si bien `STUDENT_NAME` es una constante y que no va a ser cambiada, depende de parametros y no es una constante "global", por ende debería estar en camelCase.

  #### Hacer

  ```javascript
  const GRAVITY = 9.8;
  const TIMEOUT = 5000;
  const ONE_DAY = 24 * 60 * 60 * 1000;
  ```

  En todos estos casos estas variables son "verdades absolutas".

  ### Clases

  Las clases se declaran en PascalCase y las instancias en camelCase:

  ```javascript
  class VikingWarrior { .... }

  const ragnarLothbrok = new VikingWarrior();
  ```

  ### Archivos

  En Accionet se ha optado por usar kebab-case para los archivos y directorios. Esta resolución es relativamente reciente, por lo que varios archivos están en camelCase.


  ### BBDD

  Por lo general las base de datos, y en particular postgreSQL, no son case sensitive, por lo que camelCase no es opción. La convensión que usamos en Accionet es usar snake_case. 
 

  ### Propiedades de JSON - Javascript Objects

  Si bien acá no existe una convención general y depende del caso, en Accionet preferimos camelCase. Sin embargo, existen varias excepciones, por ejemplo cuando el objeto representa una entrada de la base de datos, el case correcto sería snake_case para ser consistente con la BB.DD.

  ### css y html

  Las variables de css y html se escriben con kebab-case.

  ### Variables de Entorno

  Las variables de entorno por naturaleza son Constantes Globales, por ende se deben escribir en MACRO_CASE.

  
## Usar Variables

  Esto puede sonar como obvio, pero es muy importante evitar el uso de variables no definidas. Supongamos que queremos calcular la energía potencial gravitacional, nos podemos ver tentado a escribir lo siguiente:

  ```javascript
  const calculateGravitationPotentialEnergy = (mass, height) => {
    return mass * 10 * height;
  }
  ```

  ¿El problema? 

  Para partir si no estamos familiarizados con la formula no tenemos por qué asumir que 10 hace alusión a la gravedad. Segundo ¿qué pasa si decidimos usar 9.8 en vez de 10? Tendríamos que entrar a bucear en el código buscando cada vez que usamos la gravedad y cambiarla manual, suena a posible error. Mejor guardarlo una vez en una variable global:

  ```javascript
  const GRAVITY = 10;
  
  const calculateGravitationPotentialEnergy = (mass, height) => {
    return mass * GRAVITY * height;
  }
  ```

## Linter

  En Accionet se utiliza [ESLint](https://eslint.org/). Este nos permite definir un estilo de programación, es muy importante que todo el equipo utilize el mismo estilo, esto facilatará la compresión del código de otro miembro. El linter será responsable de ir indicando ciertos errores y advertencias. No podremos mergear una [Pull Request](/git.html#pull-request-code-review) si el linter está arrojando errores.

## Comentarios

  Esto es algo muy controversial, ¿se debe comentar el código? En Accionet desincentivamos el uso de comentarios, es preferible un código sin cometarios que uno con. Esto es un concepto contra-intuitivo, los comentarios ayudan a entender mejor el código ¿por qué vetar su uso?

  * **"El código nunca mienta, los comentarios a veces si"** Es muy común encontrarse con comentarios desactualizados, esto puede llevar a confusión. Los comentarios requieren un trabajo muy prolijo de mantención, en la practica esto rara vez ocurre, por ende mejor evitarlos.
  * **"El código es cómo un chiste, si hay que explicarlo es malo"** Un buen código no debiese requerir de comentarios. Si no se entiende por si solo es un indicio de que se debe reescribir o modificar.

  Dicho todo lo anterior, hay excepciones pero son las menos. Un clásico contra ejemplo son casos bordes no esperables, aveces uno debe agregar un código para cubrir un caso borde no obvio, por muy auto-explicativo puede requerir un comentario para ponerlo en contexto.
  

## Logs

  En producción no deben haber `console.log()`. Por dos razones: 

  1. Es lento imprimir a la consola.
  2. Los logs pueden exponer información sensible.

  Sin embargo los logs tienen un uso importante en Accionet, pero se deben utilizar a través de una alerta de `codemaster`:

  ```javascript
    const codemaster = require('codemaster');

    codemaster.alert.print('esto es una alerta');
  ```

  Todos los servidores de Accionet están configurados de tal manera que se mande una notificación vía email cada vez que se imprime una alerta. Usar sabiamente las alerta para poder monitorear la salud de los servidores, ser notificados frente a bugs inesperados y contar con la información necesaria para poder debuggear. 

## Tests

  ### ¿Por qué testear?

  En un software es muy importante que sea flexible, que se le puedan agregar y/o modificar funcionalidades. Sin embargo cuando tenemos un código en producción el riesgo de agregar algo y que se rompa todo es gigantesco. Los tests nos permiten ir verificando que todo siga funcionando correctamente. 

  ### Qué Tests Hacer

  Existe tres tipos de tests:

  * Test Unitarios: Son test atómicos. Deben revisar que un método haga lo esperado.
  * Test Integración: Estos tests son de más alto nivel y buscan revisar que la interacción entre distintas partes del código funcionen bien.
  * Test Funcionales: Estos ya se preocupan más de la funcionalidad que del código. Revisa que el software haga lo esperado.

  En Accionet los desarrolladores son los responsables de hacer los tests unitarios y los tests de integración. [Continuous Integration](/git.html#continuous-integration) va a revisar que estos tests pasen para permitir mergear una [Pull Request](/git.html#pull-request-code-review).

 ### Cómo 

  A la hora de hacer tests uno debe preocuparse que todos los caminos estén cubiertos. Es decir, que entre a cada if, else if, else, a cada loop, a cada switch etc.

  Lo segundo que uno debe preocuparse son los parámetros. Por ejemplo:

  ```javascript
    const openEachWindow = (house) => {
      for(let i = 0; i < house.windows.length; i++) {
        const window = house.windows[i];
        window.open();
      }
    }
  ```

  ¿Qué pasa si `house` es null? ¿Qué pasa si `house.windows` es null?

  Otro elemento importante es pensar en casos bordes y posibles errores que puedan surgir. Por ejemplo: 
  
  ```javascript
    const calculateHousesPerTrees = (houses, trees) => {
      return houses.length / trees.length;
    }
  ```

  ¿Qué pasa si `trees` es un arreglo vacío (length = 0)?

 ### Dónde

  Los tests se guardan en el directorio `/test/integration-unit-testing`. La estructura de los archivo debe emular a la del servidor. Es decir, los tests del método `openMainDoor()`, del archivo `/server/models/house`, deben ser escritos en el archivo `/test/integration-unit-testing/server/models/house/openMainDoor.js`.


 ### Cobertura 

 Para medir que los tests tengan una cobertura adecuada, [Continuous Integration](/git.html#continuous-integration) va a revisar que % de las líneas de código, de las funciones, de las branches y de los statements están siendo testeadas.


  ### Método intesteable

  Si en algún momento te encuentras frente a un método y llegas a la conclusión "este método es imposible de testear", esto significa que ese método debe ser sub dividido en métodos más simples y fáciles de testear.