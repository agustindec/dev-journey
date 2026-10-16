# Fundamentos de Objetos

Los objetos son una de las estructuras fundamentales de JavaScript y TypeScript. Permiten representar
entidades del mundo real agrupando información y comportamientos dentro de una misma estructura.

En ambos lenguajes, los objetos funcionan prácticamente de la misma manera. La principal diferencia es que
TypeScript incorpora un sistema de tipos que permite verificar qué propiedades existen y qué valores pueden almacenar.

## 1. Object Literals (Literales de objeto)

Un **literal de objeto** es una forma de crear un objeto directamente mediante llaves `{}`, sin necesidad de definir previamente una clase o utilizar un constructor. Dentro de estas llaves se declara un conjunto de propieades que permiten representar y organizar información relacionada con una misma entidad. Cada propiedad está formada por una clave, que identifica el dato, y un valor, que contiene la información asociada.

Los literales de objeto se utilizan constantemente para representar usuarios, productos, configuraciones, pedidos o cualquier otra entidad que necesite agrupar distintos datos. En JavaScript, las propiedades pueden contener valores de diferentes tipos, como cadenas de texto, números, booleanos, arreglos, funciones e incluso otros objetos.

**Ejemplo: Registrar un producto**

```TypeScript
const producto = {
    nombre: "Notebook Lenovo",
    precio: 35000,
    disponible: true
};
```

En este ejemplo:

* `producto` es la variable que contiene el objeto.
* `{}` son las llaves que delimitan el literal de objeto.
* `nombre`, `precio` y `disponible` son las propiedades.
* `"Notebook Lenovo"`, `35000` y `true` son sus respectivos valores.

TypeScript interpreta automáticamente que `nombre` es de tipo `string`, `precio` es de tipo `number` y `disponible` es de tipo `boolean`.

**Importante**: Aunque utilizamos `const`, las propiedades del objeto pueden modificarse. `const` impide reasignar la variable a otro objeto, pero no hace que su contenido sea inmutable.

## 2. Acceso con `.` (Dot Notation)

La **notación de punto** es un mecanismo que permite acceder a las propiedades de un objeto utilizando su nombre directamente después de un punto. Esta sintaxis establece una relación entre el objeto y la propiedad que queremos consultar o modificar, proporcionando una manera clara y sencilla de trabajar con sus datos.

Se utiliza principalmente cuando conocemos de antemano el nombre de la propiedad que necesitamos. Es una de las formas de acceso más habituales en JavaScript y TypeScript, especialmente porque facilita la lectura del código. Además, TypeScript puede comprobar si la propiedad existe en el tipo de objeto y detectar posibles errores durante el desarrollo.

**Ejemplo: Consultar información de un cliente**

```TypeScript
const cliente = {
    nombre: "Agustin",
    email: "agustin@gmail.com",
    edad: 27
};

console.log(cliente.nombre); // "Agustin"
console.log(cliente.email); // "agustin@gmail.com"
```

La expresión `cliente.nombre` indica que queremos acceder a la propiedad `nombre` del objeto `cliente`.

También podemos utilizar esta notación para modificar sus valores:

```TypeScript
cliente.edad = 28;

console.log(cliente.edad); // 28
```

Si intentáramos acceder a `cliente.telefono`, TypeScript mostraría un error porque esa propiedad no está definida en el tipo inferido del objeto.

## 3. Acceso con `[]` (Bracket Notation)

La **anotación de corchetes** es otra forma de acceder a las propiedades de un objeto, pero, a diferencia de la notación de punto, permite indicar el nombre de la propiedad mediante una expresión que se evalúa durante la ejecución del programa. Dentro de los corchetes podemos escribir directamente una cadena de texto o utilizar una variable que contenga el nombre de la propiedad.

Esta característica resulta especialmente útil cuando el nombre de la propiedad no se conoce de antemano o depende de algún dato externo, como una selección del usuario, un parámetro recibido o una configuración dinámica. En TypeScript, es importante asegurarse de que la expresión utilizada para acceder al objeto corresponda a una propiedad válida según su tipo.

**Ejemplo: Consultar un dato seleccionado**

```TypeScript
const usuario = {
    nombre: "Lucía",
    email: "lucia@gmail.com",
    ciudad: "Montevideo"
};

const campo: string = "email";

console.log(usuario["nombre"]); // "Lucía"
console.log(usuario["email"]);    // "lucia@gmail.com"
```

Hasta acá se utilizan cadenas de texto directamente. Sin embargo, la principal ventaja aparece cuando necesitamos trabajar con variable:

```TypeScript
const campoSeleccionado: keyof typeof usuario = "email";

console.log(usuario[campoSeleccionado]); // "lucia@gmail.com"
```

En este caso, `campoSeleccionado` contiene el nombre de la propiedad que queremos consultar.

La expresión `keyof typeof usuario` es propia de TypeScript y permite indicar que la variable solamente puede contener nombres de propiedades existentes en `usuario`.

## 4. Propiedades (Properties)

Las propiedades son los elementos que almacenan y describen la información asociada a un objeto. Cada propiedad posee una clave que la identifica y un valor que representa alguna característica o dato de la entidad. En conjunto, las propiedades permiten definir el estado de un objeto, es decir, la información que contiene en un momento determinado.

En JavaScript, las propiedades pueden agregarse, modificarse o eliminarse dinámicamente. TypeScript introduce un control adicional mediante su sistema de tipos, que permite establecer qué propiedades deben existir y qué tipo de valores pueden recibir. Esto ayuda a mantener una estructura consistente y evita errores, como intentar asignar una cadena de texto a una propiedad definida como numérica.

**Ejemplo: Actualizar el precio de un producto**

```TypeScript
const producto = {
    nombre: "Mouse Logitech",
    precio: 1500,
    disponible: true
};

// Modificamos sus propiedades
producto.precio = 1200;
producto.disponible = false;

console.log(producto);
```

Resultado:

```TypeScript
{
    nombre: "Mouse Logitech",
    precio: 1200,
    disponible: false
}
```
Las propiedades permiten representar los cambios que experimenta un producto a lo largo del tiempo.

TypeScript también verifica que los nuevos valores sean compatibles con los tipos definidos:

```TypeScript
producto.precio = 2000;    // Correcto
producto.precio = "Gratis"; // Error de TypeScript
```

El segundo caso produce un error porque TypeScript infirió que `precio` debe almacenar un número.

## 5. Métodos (Methods)

Un método es una función que pertenece a un objeto y representa una acción o comportamiento asociado a este. Mientras que las propiedades suelen describir las características o el estado de una entidad, los métodos permiten realizar operaciones sobre esa información. En JavaScript, las funciones son valores que pueden almacenarse en propiedades, por lo que un método es, esencialmente, una propiedad cuyo valor es una función.

Los métodos se utilizan para organizar comportamientos relacionados con una entidad y evitar que su lógica quede distribuida en distintas partes del programa. Pueden recibir parámetros, devolver resultados y acceder a otras propiedades del mismo objeto mediante la palabra reservada `this`. En TypeScript, además, podemos definir los tipos de sus parámetros y valores de retorno para garantizar que se utilicen correctamente.

**Ejemplo: Administrar un carrito de compras**

```TypeScript
const carrito = {
    productos: ["Mouse", "Teclado"],

    agregarProducto(producto: string): void {
        this.productos.push(producto);
    },

    obtenerCantidad(): number {
        return this.productos.length;
    }
};

// Agregamos un producto
carrito.agregarProducto("Monitor");

// Consultamos la cantidad
console.log(carrito.obtenerCantidad()); // 3
```

En este ejemplo, `productos` es una propiedad que almacena un arreglo, mientras que `agregarProducto()` y `obtenerCantidad()` son métodos que permiten realizar operaciones relacionadas con el carrito.

La palabra reservada `this` permite acceder a las propiedades del propio objeto cuando estos métodos se invocan mediante `carrito`.

## 6. Computed Properties (Propiedades calculadas)

Las propiedades calculadas permiten definir dinámicamente el nombre de una propiedad al momento de crear un objeto. A diferencia de una propiedad tradicional, cuyo nombre se escribe directamente, una propiedad calculada utiliza una expresión encerrada entre corchetes []. JavaScript evalúa esa expresión y utiliza el resultado como clave de la propiedad dentro del nuevo objeto.

Este mecanismo resulta útil cuando necesitamos construir objetos cuya estructura depende de variables, parámetros o información obtenida durante la ejecución del programa. Es habitual encontrarlo en formularios dinámicos, configuraciones y transformaciones de datos. Aunque utiliza los mismos corchetes que la notación de acceso, su finalidad es diferente: **la notación de acceso consulta o modifica una propiedad existente, mientras que una propiedad calculada define una clave al crear el objeto.**

**Ejemplo: Crear un objeto con campos dinámicos**

```TypeScript
const tipoContacto = "telefono";
const valorContacto = "099123456";

const cliente = {
    nombre: "Martín",
    [tipoContacto]: valorContacto
};

console.log(cliente);
```

Resultado:

```TypeScript
{
    nombre: "Martín",
    telefono: "099123456"
}
```

La expresión `[tipoContacto]` indica que el nombre de la propiedad debe obtenerse del valor almacenado en la variable `tipoContacto`.

Como esa variable contiene `"telefono"`, JavaScript utiliza ese texto como nombre de la propiedad.

También podemos utilizar expresiones más elaboradas:

```TypeScript
const idioma = "es";

const configuracion = {
    [`mensaje_${idioma}`]: "Bienvenido"
};

console.log(configuracion);
```

Resultado:

```TypeScript
{
    mensaje_es: "Bienvenido"
}
```

En este caso, utilizamos un *template literal* para construir dinámicamente el nombre `mensaje_es`.