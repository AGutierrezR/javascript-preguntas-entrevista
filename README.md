# JavaScript Preguntas y Respuestas

### Tabla de Contenido

| No. | Preguntas                                                                                                                             |
| --- | ------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [¿Cuales son las formas posibles de crear un objeto en JavaScript?](#cuales-son-las-posibles-maneras-de-crear-un-objeto-en-javascript) |
| 2  | [¿Cual es la diferencia entre Call, Apply y Bind?](#cual-es-la-diferencia-entre-call-apply-y-bind)                              |
| 3   | [¿Cual es el propósito del metodo slice de array?](#cual-es-el-propósito-del-método-slice-de-array)                               |
| 4  | [¿Cual es el propósito de el metodo splice de array?](#cual-es-el-propósito-del-método-splice-de-array)                             |
| 5  | [¿Cual es la diferencia entre slice y splice?](#cual-es-la-diferencia-entre-slice-y-splice)                              |
| 6 | [¿Qué es JSON y sus operaciones comunes?](#qué-es-JSON-y-sus-operaciones-comunes)                              |
| 7 | [¿Como se comparan Object y Map?](#como-se-comparan-Object-y-Map)                              |
| 8 | [¿Cual es la diferencia entre los operadores === y ==?](#Cual-es-la-diferencia-entre-los-operadores-===-y-==)                              |
| 9 | [¿Que es lambda o funciones de flecha?](#Que-es-lambda-o-funciones-de-flecha)                              |

1. ### ¿Cuales son las posibles maneras de crear un objeto en JavaScript?

   Existen muchas maneras de crear un objeto en JavaScript.

   1. **Object constructor:**
      La manera mas sencilla de crear un objeto vacío es usando el Object constructor. Esta forma no es recomendada.

      ```js
      var object = new Object();
      ```

   2. **Object's create method:**
      El método `create` de Object crea un nuevo objeto pasando el prototype object como un parámetro.

      ```javascript
      var object = Object.create(null);
      ```

   3. **Object literal syntax:**
      La sintaxis Object literal es equivalente al método `create` cuando se le pasa `null` como parámetro.

      ```javascript
      var object = {};
      ```

   4. **Function constructor:**
      Crea una función y aplica el operador `new` para crear una instancia de un Objeto.

      ```javascript
      function Person(name){
        var object = {};
        object.name=name;
        object.age=21;
        return object;
      }
      var object = new Person("Sudheer");
      ```

   5. **Function constructor with prototype:**
      Esta es similar al function constructor pera usa `prototype` para las propiedades y métodos.

      ```javascript
      function Person(){}
      Person.prototype.name = "Sudheer";
      var object = new Person();
      ```

      Esto es equivalente a una instancia creada con un método `create` con una función prototype y luego llamando esa función con una instancia y parámetros como argumentos.

      ```javascript
      function func {};

      new func(x, y, z);

      // **(O)**

      // Crea una nueva instancia usando la función prototype
      var newInstance = Object.create(func.prototype)

      // Llamando la función
      var result = func.call(newInstance, x, y, z),

      // Si el resultado es un objeto non-null entonces úsalo de lo contrario usa una nueva instancia
      console.log(result && typeof result === 'object' ? result : newInstance);
      ```

   6. **ES6 Class syntax:**
      ES6 presenta la características de classes para crear objetos

      ```javascript
      class Person {
        constructor(name) {
        this.name = name;
        }
      }

      var object = new Person("Sudheer");
      ```

   7. **Singleton pattern**

      Un Singleton es un objeto que solo puede ser inicializado una vez. Llamada repetidas a su constructor retornan la misma instancia y de esta manera se puede asegurar que no se crean varias instancias accidentalmente

      ```js
      var object = new function(){
      this.name = "Sudheer";
      ```

   **[⬆ Ir Arriba](#tabla-de-contenido)**

2. ### ¿Cual es la diferencia entre Call, Apply y Bind?

   La diferencia entre `call()`, `apply()` y `bind()` se explica a continuación:

   **Call:** El método `call()` invoca una función con un valor `this` dado y arguments previstos uno por uno

   ```js
   var employee1 = {firstName: 'John', lastName: 'Rodson'};
   var employee2 = {firstName: 'Jimmy', lastName: 'Baily'};

   function invite(greeting1, greeting2) {
   	console.log(greeting1 + ' ' + this.firstName + ' ' + this.lastName+ ', '+ greeting2);
   }

   invite.call(employee1, 'Hello', 'How are you?'); // Hello John Rodson, How are you?
   invite.call(employee2, 'Hello', 'How are you?'); // Hello Jimmy Baily, How are you?
   ```

   **Apply:** El método `apply()` invoca la función y permite pasar argumentos como array

   ```js
   var employee1 = {firstName: 'John', lastName: 'Rodson'};
   var employee2 = {firstName: 'Jimmy', lastName: 'Baily'};

   function invite(greeting1, greeting2) {
   	console.log(greeting1 + ' ' + this.firstName + ' ' + this.lastName+ ', '+ greeting2);
   }

   invite.apply(employee1, ['Hello', 'How are you?']); // Hello John Rodson, How are you?
   invite.apply(employee2, ['Hello', 'How are you?']); // Hello Jimmy Baily, How are you?
   ```

   **Bind:** El método `bind()` retorna una nueva función, permitiendo pasar un array y cualquier numero de argumentos

   ```js
   var employee1 = {firstName: 'John', lastName: 'Rodson'};
   var employee2 = {firstName: 'Jimmy', lastName: 'Baily'};

   function invite(greeting1, greeting2) {
   	console.log(greeting1 + ' ' + this.firstName + ' ' + this.lastName+ ', '+ greeting2);
   }

   var inviteEmployee1 = invite.bind(employee1);
   var inviteEmployee2 = invite.bind(employee2);
   inviteEmployee1('Hello', 'How are you?'); // Hello John Rodson, How are you?
   inviteEmployee2('Hello', 'How are you?'); // Hello Jimmy Baily, How are you?
   ```
  
   **[⬆ Ir Arriba](#tabla-de-contenido)**

3. ### ¿Cual es el propósito del método slice de array?

   El método `slice()` retorna los elementos seleccionados de un array como un nuevo array. Selecciona los elementos comenzando por el argumento *start*, y terminando por el elemento *end* que es opcional. Si se omite el argumento *end* entonces selecciona hasta el final del array. Algunos ejemplos:

   ```js
   let arrayIntegers = [1, 2, 3, 4, 5];
   let arrayIntegers1 = arrayIntegers.slice(0,2); // returns [1,2]
   let arrayIntegers2 = arrayIntegers.slice(2,3); // returns [3]
   let arrayIntegers3 = arrayIntegers.slice(4); //returns [5]
   ```

   **Nota:** El método `slice()` no mutara el array original sino que retorna un nuevo sub conjunto como nuevo array

   **[⬆ Ir Arriba](#tabla-de-contenido)**

4. ### ¿Cual es el propósito del método splice de array?

   El método `splice()` es usado para agregar/remover items desde/hacia un array, y luego retorna el item removido. El primer argumento especifica la posición de inserción o borrado del array y el segundo argumento indica el numero de elementos que serán borrados. cada argumento adicional sera agregado al array. Algunos ejemplos:

   ```js
   let arrayIntegersOriginal1 = [1, 2, 3, 4, 5];
   let arrayIntegersOriginal2 = [1, 2, 3, 4, 5];
   let arrayIntegersOriginal3 = [1, 2, 3, 4, 5];

   let arrayIntegers1 = arrayIntegersOriginal1.splice(0,2); // returns [1, 2]; original array: [3, 4, 5]
   let arrayIntegers2 = arrayIntegersOriginal2.splice(3); // returns [4, 5]; original array: [1, 2, 3]
   let arrayIntegers3 = arrayIntegersOriginal3.splice(3, 1, "a", "b", "c"); //returns [4]; original array: [1, 2, 3, "a", "b", "c", 5]
   ```

   **Nota:** El método `splice()` modifica el array original y retorna el array borrado.

   **[⬆ Ir Arriba](#tabla-de-contenido)**

5. ### ¿Cual es la diferencia entre slice y splice?

   Alguna de las mayores diferencias están en esta tabla

   | Slice                                     | Splice                                                       |
   | ----------------------------------------- | ------------------------------------------------------------ |
   | No modifica el array original (inmutable) | Modifica el array original (mutable)                         |
   | Retorna un subconjunto del array original | Retorna los elementos eliminados como un array               |
   | Se usa para extraer elementos de un array | Se usa para insertar o eliminar elementos desde/hacia un array |

   **[⬆ Ir Arriba](#tabla-de-contenido)**

6. ### ¿Qué es JSON y sus operaciones comunes?

   **JSON** es un formato de dato que sigue la sintaxis de objeto de JavaScript. Es muy util cuando se quiere transmitir datos a traves de la red y básicamente solo un fichero de texto con la extension .json y un MIME type de application/json

   **Parsing:** Convierte un string a native object

   ```js
   JSON.parse(text)
   ```

   **Stringification:** Convierte un native object a string para que puede ser transmitido a traves de la web

   ```js
   JSON.stringify(object)
   ```

   **[⬆ Ir Arriba](#tabla-de-contenido)**

7. ### ¿Como se comparan Object y Map?

   **Object** son muy similares a **Maps** en el sentido que ambos permiten usar keys y values, recuperar values, borrar keys, y detectar si alguna key fue declarada. Por esta razón, Objects han sido usados como Maps. Pero existen diferencias que hacen preferible el uso de Maps en ciertos casos

   1. Los keys en un Object son Strings y Symbols, pero en Maps puede ser cualquier valor, incluyendo funciones, objetos y cualquier primitivo.
   2. Los keys en un Map son ordenados mientras que los keys agregados a un objeto no. Por lo que, al iterar sobre el Map, este retornara los keys en orden de inserción
   3. Se puede obtener el tamaño de un Map con la propiedad `size`, mientras el numero de propiedades en un Object debe ser terminado manualmente (`Object.keys(myObj).length;`)
   4. Un Map es iterable y puede ser directamente iterado, mientras que para iterar un Object require que obtengamos los keys de alguna manera e iterar sobre ellos.
   5. Un Object tiene un prototype, por lo que existen algunos keys por defecto que puede coincidir con los keys que establezcas, por lo que hay que ser cuidadoso.
   6. Un Map puede actuar mejor en escenarios que involucren adiciones y sustracciones de pares.

   **[⬆ Ir Arriba](#tabla-de-contenido)**
   
8. ### ¿Cual es la diferencia entre los operadores === y ==?

   JavaScript proporciona ambos tipos de comparaciones, la estricta (`===`, `!==`) y type-converting (`==`, `!=`). Los operadores strict toman el tipo de la variable ne consideración, mientras que el operador no-strict hace una corrección/conversion del tipo basándose en el valor de la variable. Los operadores strict siguen las siguientes condiciones para diferentes tipos:

   1. Dos cadenas son estrictamente iguales cuando tiene la misma secuencia de caracteres, misma longitud y el mismo carácteres en las posiciones respectivas.
   2. Dos números son estrictamente iguales cuando son numéricamente iguales, por ejemplo, Tienen el mismo valor numérico. Existen dos casos especiales.
      1. `NaN` no es igual a nada, incluyendo `NaN`.
      2. Cero positivo y negativo son iguales el uno con el otro.
   3. Dos booleanos son estrictamente iguales si ambos son `true` o ambos son `false `
   4. Dos objetos son estrictamente iguales si refieren al mismo Object
   5. `Null` y `Undefined` no son iguales con `===` pero si son iguales con `==`, por ejemplo, `null === undefined -> true` pero `null == undefined -> true`

   Otros casos serian:

   ```
   0 == false   // true
   0 === false  // false
   1 == "1"     // true
   1 === "1"    // false
   null == undefined // true
   null === undefined // false
   '0' == false // true
   '0' === false // false
   []==[] or []===[] //false, se refieren a distintos objectos en memoria
   {}=={} or {}==={} //false, se refieren a distintos objectos en memoria
   ```

   **[⬆ Ir Arriba](#tabla-de-contenido)**

9. ### ¿Que es lambda o funciones de flecha?

   Una función de flecha es un sintaxis corta de una function expression y no posee su propio `this`, `arguments`, `super` o `new.target`. Estas funciones son mas adecuadas para funciones non-method, y no puede usadas como constructores.

   **[⬆ Ir Arriba](#tabla-de-contenido)**

