# JavaScript Preguntas y Respuestas

### Tabla de Contenido

| No. | Preguntas |
|---- | ---------|
|1  | [Cuales son las formas posibles de crear un objeto en JavaScript?](#cuales-son-las-posibles-maneras-de-crear-un-objeto-en-javascript) |

1. ### Cuales son las posibles maneras de crear un objeto en JavaScript?

   Existen muchas maneras de crear un bojecto en JavaScript.

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
