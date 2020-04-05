# JavaScript Preguntas y Respuestas

### Tabla de Contenido

| No. | Preguntas                                                                                                                             |
| --- | ------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [Cuales son las formas posibles de crear un objeto en JavaScript?](#cuales-son-las-posibles-maneras-de-crear-un-objeto-en-javascript) |
| 2   | [Cual es el proposito del metodo slice de array?](#cual-es-el-proposito-del-metodo-slice-de-array)                                |
| 3  | [Cual es el proposito de el metodo splice de array?](#cual-es-el-proposito-del-metodo-splice-de-array)                              |

1. ### Cuales son las posibles maneras de crear un objeto en JavaScript?

   Existen muchas maneras de crear un objecto en JavaScript.

   1. **Object constructor:**
      La manera mas sencilla de crear un objeto vacio es usando el Object constructor. Esta forma no es recomendada.

      ```js
      var object = new Object();
      ```

   2. **Object's create method:**
      El metodo `create` de Object crea un nuevo objecto pasando el prototype object como un parametro.

      ```javascript
      var object = Object.create(null);
      ```

   3. **Object literal syntax:**
      La sintaxis Object literal es equivalente al metodo `create` cuando se le pasa `null` como parametro.

      ```javascript
      var object = {};
      ```

   4. **Function constructor:**
      Crea una funcion y aplica el operador `new` para crear una instancia de un Objeto.

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
      Esta es similar al function constructor pera usa `prototype` para las propiedades y metodos.

      ```javascript
      function Person(){}
      Person.prototype.name = "Sudheer";
      var object = new Person();
      ```

      Esto es equivalente a una instancia creada con un metodo `create` con una funcion prototype y luego llamando esa funcion con una instancia y parametros como argumentos.

      ```javascript
      function func {};

      new func(x, y, z);

      // **(OR)**

      // Crea una nueva intancia usando la funcion prototype
      var newInstance = Object.create(func.prototype)

      // Llamando la funcion
      var result = func.call(newInstance, x, y, z),

      // Si el resultado es un objeto non-null entonces usalo de lo contrario usa una nueva instancia
      console.log(result && typeof result === 'object' ? result : newInstance);
      ```

   6. **ES6 Class syntax:**
      ES6 presenta la caracteristicas de classes para crear objetos

      ```javascript
      class Person {
        constructor(name) {
        this.name = name;
        }
      }

      var object = new Person("Sudheer");
      ```

   7. **Singleton pattern**

      Un Singleton es un objecto que solo puede ser inicializado una vez. Llamada repetidas a su contructor retornan la misma instancia y de esta manera se puede asegurar que no se crean varias intancias accidentalemente

      ```js
      var object = new function(){
      this.name = "Sudheer";
      ```

   **[⬆ Ir Arriba](#tabla-de-contenido)**

2. ### Cual es el proposito del metodo slice de array?

   El metodo `slice()` returna los elementos seleccionados de un array como un nuevo array. Selecciona los elementos comenzando por el argumento *start*, y terminando por el elemento *end* que es opcional. Si se omite el argumento *end* entonces selecciona hasta el final del array. Algunos ejemplos:

   ```js
   let arrayIntegers = [1, 2, 3, 4, 5];
   let arrayIntegers1 = arrayIntegers.slice(0,2); // returns [1,2]
   let arrayIntegers2 = arrayIntegers.slice(2,3); // returns [3]
   let arrayIntegers3 = arrayIntegers.slice(4); //returns [5]
   ```

   **Nota:** El metodo `slice()` no mutara el array original sino que retorna un nuevo sub conjunto como nuevo array

3. ### Cual es el proposito del metodo splice de array?

   El metodo `splice()` es usado para agregar/remover items desde/hacia un array, y luego retorna el item removido. El primer argumento especifica la posicion de insercion o borrado del array y el segundo argumento indica el numero de elementos que seran borrados. cada argumento adicional sera agregado al array. Algunos ejemplos:

   ```js
   let arrayIntegersOriginal1 = [1, 2, 3, 4, 5];
   let arrayIntegersOriginal2 = [1, 2, 3, 4, 5];
   let arrayIntegersOriginal3 = [1, 2, 3, 4, 5];

   let arrayIntegers1 = arrayIntegersOriginal1.splice(0,2); // returns [1, 2]; original array: [3, 4, 5]
   let arrayIntegers2 = arrayIntegersOriginal2.splice(3); // returns [4, 5]; original array: [1, 2, 3]
   let arrayIntegers3 = arrayIntegersOriginal3.splice(3, 1, "a", "b", "c"); //returns [4]; original array: [1, 2, 3, "a", "b", "c", 5]
   ```

   **Nota:** El metodo `splice()` modifica el array original y retorna el array borrado.
