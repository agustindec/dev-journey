# Variables y Tipos en JavaScript / TypeScript

Las variables y los tipos son una base especialmente importante en JavaScript porque el lenguaje funciona de una manera bastante diferente a Java.

```Java
String nombre = "Agustin";
int edad = 27;
boolean activo = true;
```

En JavaScript, una variable no tiene un tipo fijo asociado. El tipo pertenece al **valor que contiene**.

```JavaScript
let nombre = "Agustin";
let edad = 27;
let activo = true;
```

Incluso esto es válido en JavaScript:

```JavaScript
let valor = 10;
valor = "Hola";
valor = true;
```

Primero `valor` contiene un `number`, después un `string` y finalmente un `boolean`.  
JavaScript es un lenguaje de **tipado dinámico**.

TypeScript agrega una capa de tipado estático sobre JavaScript:

```TypeScript
let valor: number = 10;

valor = 20;      // válido
valor = "Hola";  // error de TypeScript
```

## 1. Declarar variables: `let` y `const`

En JavaScript moderno se debería trabajar principalmente con `const` y `let`.

`let` declara una variable cuyo valor puede cambiar:

```JavaScript
let intentos = 0;

intentos = 1;
intentos = 2;
```

Es conceptualmente parecido a una variable normal de Java:

```Java
int intentos = 0;
intentos = 1;
```

En cambio, `const` indica que la variable **no puede recibir otro valor después de ser inicializada**.

```JavaScript
const nombre = "Agustin";

nombre = "Juan";  // Error
```

Una `const` además debe inicializarse inmediatamente:

```JavaScript
const nombre; // Error
```

En desarrollo profesional moderno existe una regla práctica bastante útil:

> Utiliza `const` por defecto. Usa `let` solamente 
> cuando sepas que la variable tendrá que ser reasignada.

Por ejemplo:

```JavaScript
const porcentaje = 20;
const totalLlamadas = 150;

let llamadasCalculadas = 0;

llamadasCalculadas = (totalLlamadas * porcentaje) / 100;
```

Esto hace que el código sea más fácil de razonar porque, cuando ves `const`, sabes que esa referencia no será reemplazada posteriormente.

`const` **no significa objeto inmutable**.

Esta es una confusión muy habitual.

```JavaScript
const usuario = {
  nombre: "Agustin",
  edad: 27
};

usuario.edad = 28;
```

Esto es completamente válido.

Lo que `const` impide es cambiar el valor almacenado en `usuario` por otro objeto:

```JavaScript
usuario = {
  nombre: "Juan",
  edad: 27
}; // Error
```

Por tanto, `const` protege la **reasignación de la variable**, no el contenido interno del objeto.

## 2. ¿Por qué evitar `var`?

Antes de ES6 se utilizaba principalmente `var`:

```JavaScript
var nombre = "Agustin";
```

Todavía funciona y probablemente se puede encontrar en código legacy, pero en código moderno se debería utilizar de preferencia `const` y `let`.

Una de las diferencias más importante está en el alcance (scope).

`let` y `const` tienen un **scope de bloque**:

```JavaScript
if(true){
  const nombre = "Agustin";
}

console.log(nombre); // Error
```

El bloque delimitado por `{ }` determina dónde existe esa variable.

Con `var`, esto no ocurre de la misma manera:

```JavaScript
if (true) {
  var nombre = "Agustin";
}

console.log(nombre); // "Agustin"
```

`var` tiene scope de función, no de bloque. Esto puede producir variables disponibles en lugares donde no esperabas encontrarlas.

También permite situaciones poco deseables como volver a declarar una variable:

```JavaScript
var edad = 27;
var edad = 30;
```

Con `let`:

```JavaScript
let edad = 27;
let edad = 30; // Error
```

Además, `var` tiene comportamientos relacionados con *hoisting* que pueden resultar confusos.

`const` -> opción predeterminada
`let` -> cuando necesitas reasignar
`var` -> evitar en código nuevo

## 3. Tipos primitivos

JavaScript tiene varios tipos primitivos. Los que se utilizan constantemente son `string`, `number`, `boolean`, `undefined` y `null`. `bigint` aparece en situaciones específicas y `symbol` es bastante menos frecuente en Backend cotidiano.

### `string`

Representa texto.

```JavaScript
const nombre = "Agustin";
const apellido = 'Perez';
```

Se puede utilizar comillas simples o dobles.

JavaScript también dispone de **template literals**, utilizando backticks:

```JavaScript
const nombre = "Agustin";
const edad = 27;

const mensaje = `Mi nombre es ${nombre} y tengo ${edad} años`;
```

Esto suele ser preferible a concatenaciones como:

```JavaScript
const mensaje = "Mi nombre es " + nombre + " y tengo " + edad + " años";
```

En TypeScript puedes indicar explícitamente el tipo:

```TypeScript
const nombre: string = "Agustin";
```

Aunque normalmente TypeScript puede inferirlo:

```TypeScript
const nombre = "Agustin";
```

TypeScript ya sabe que `nombre` es un `string`.

### `number`

JavaScript utiliza principalmente un único tipo:

```TypeScript
number
```

Por ejemplo:

```JavaScript
const edad = 27;
const precio = 199.99;
const temperatura = -5;
```

Todos son `number`.

```JavaScript
typeof edad;        // "number"
typeof precio;      // "number"
typeof temperatura; // "number"
```

Además existen valores numéricos especiales como:

```TypeScript
Infinity
-Infinity
NaN
```

`NaN` significa *Not a Number* y aparece cuando una operación numérica no produce un número válido.

```JavaScript
const resultado = Number("hola");

console.log(resultado); // NaN
```

Un detalle extraño pero importante:

```JavaScript
typeof NaN; // "number"
```

Es uno de esos comportamientos de JavaScript que conviene conocer para no sorprenderse.

### `bigint`

`bigint` existe para representar enteros que pueden superar el rango entero seguro de `number`.

Se crea normalmente agregando `n`:

```JavaScript
const numeroGrande = 9007199254740993n; 
```

Su tipo es:

```JavaScript
typeof numeroGrande; // "bigint"
```

No puedes mezclar directamente `number` y `bigint`:

```JavaScript
const resultado = 10n + 5; // Error
```

Tendría que ser:

```JavaScript
const resultado = 10n + 5n;
```

En Backend puede aparecer al trabajar con identificadores o enteros muy grandes provenientes de bases de datos.

### `boolean`

Representa los valores:

```JavaScript
true
false
```

Por ejemplo:

```JavaScript
const activo = true;
const administrador = false;
```

En TypeScript:

```TypeScript
const activo: boolean = true;
```

### `undefined` y `null`

JavaScript distingue dos conceptos que inicialmente parecen representar lo mismo.

`undefined`: normalmente significa que **todavía no existe un valor definido**.

```JavaScript
let nombre;

console.log(nombre);
```

El resultado es: `undefined`

La variable existe, pero todavía no tiene un valor asignado.

También puede aparecer al intentar acceder a una propiedad inexistente:

```JavaScript
const usuario = {
  nombre: "Agustin"
};

console.log(usuario.edad); // undefined
```

JavaScript está diciendo esencialmente:

> No existe un valor definido aquí.

`null`: normalmente representa una **ausencia intencional de valor**.

```JavaScript
const usuario = {
  nombre: "Agustin",
  telefono: null
};
```

Aquí estás indicando explícitamente que `telefono` no tiene un valor.

La diferencia conceptual que conviene recordar es:

`undefined` -> el valor no está definido
`null` -> explícitamente no hay valor

En aplicaciones Backend esta diferencia puede ser importante. Por ejemplo, una API podría devolver:

```JSON
{
  "nombre": "Agustin",
  "telefono": null
}
```

Para expresar que el campo existe pero actualmente no posee información.

TypeScript además permite representar explícitamente estas posibilidades:

```TypeScript
let telefono: string | null = null;

telefono = "099123456";
```

Esto se denomina **union type**. 

### `symbol`

`symbol`: es un tipo primitivo que permite crear valores únicos.

```JavaScript
const id1 = Symbol("id");
const id2 = Symbol("id");

console.log(id1 === id2); // false
```

Aunque ambos tengan la descripción `"id"`, cada `Symbol` es único.

Pueden utilizarse como claves especiales dentro de objetos:

```JavaScript
const id = Symbol("id");

const usuario = {
  nombre: "Agustin",
  [id]: 123
};
```

JavaScript también utiliza símbolos internamente para determinados protocolos del lenguaje.

No es un tipo que se vaya a utilizar constantemente en aplicaciones comunes, a diferencia de `string`, `number`, `boolean`, objetos o arrays.

## 4. Objetos

Los objetos son fundamentales en JavaScript. Gran parte del lenguaje gira alrededor de ellos.

Un objeto agrupa propiedades relacionadas:

```JavaScript
const usuario = {
  id: 1,
  nombre: "Agustin",
  activo: true
};
```

Puedes acceder a sus propiedades mediante:

```JavaScript
console.log(usuario.nombre);
console.log(usuario.id);
```

También existe la notación con corchetes:

```JavaScript
console.log(usuario["nombre"]);
```

La primera suele utilizarse cuando conoces directamente el nombre de la propiedad. La segunda resulta especialmente útil cuando el nombre de la propiedad es dinámico:

```JavaScript
const propiedad = "nombre";

console.log(usuario[propiedad]);
```

JavaScript permite crear objetos directamente sin definir previamente una clase.

Esto hace que trabajar con estructuras de datos sea muy flexible.

TypeScript permite agregar estructura y seguridad de tipos a estos objetos:

```TypeScript

interface Usuario {
  id: number;
  nombre: string;
  activo: boolean;
}

const usuario: Usuario = {
  id: 1,
  nombre: "Agustin",
  activo: true
};
```

## 5. Arrays

Un array representa una colección ordenada de valores.

```JavaScript
const numeros = [10, 20, 30];
```

Puedes acceder a los elementos mediante índices:

```JavaScript
console.log(numeros[0]); // 10
console.log(numeros[1]); // 20
```

Los índices comienzan en `0`.

Sin embargo, los arrays JavaScript son dinámicos:

```JavaScript
const numeros = [10, 20];

numeros.push(30);

console.log(numeros);
```

Resultado:

```JavaScript
[10, 20, 30]
```

En JavaScript puro, incluso podrías mezclar tipos:

```JavaScript
const valores = [10, "Hola", true];
```

En TypeScript normalmente se van a tipar esos arrays:

```TypeScript
const numeros: number[] = [10, 20, 30];

const nombres: string[] = ["Ana", "Juan", "Pedro"];
```

Entonces esto sería incorrecto:

```TypeScript
numeros.push("Hola"); // Error
```

## 6. `typeof`

JavaScript proporciona el operador `typeof` para consultar el tipo de un valor.

```JavaScript
const nombre = "Agustin";
const edad = 27;
const activo = true;

console.log(typeof nombre); // "string"
console.log(typeof edad);   // "number"
console.log(typeof activo); // "boolean"
```

También:

```JavaScript
typeof undefined; // "undefined"
typeof 10n;       // "bigint"
```

Con objetos:

```JavaScript
const usuario = {
  nombre: "Agustin"
};

typeof usuario; // "object"
```

Pero hay dos casos que se deben conocer:

El primero:

```JavaScript
typeof null; // "object"
```

Aunque `null` conceptualmente representa ausencia de valor, `typeof null` devuelve `"object"`. Es una peculiaridad histórica del lenguaje. No se debe utilizar esto:

```JavaScript
if (typeof valor === "object"){
  // no garantiza que realmente tengas un objeto útil
}
```

porque `valor` podría ser `null`.

Puedes comprobarlo así:

```JavaScript
if (valor !== null && typeof valor === "object"){
  // objeto
}
```

El segundo caso son los arrays:

```JavaScript
const numeros = [1, 2, 3];

typeof numeros; // "object"
```

`typeof` no distingue arrays de otros objetos.

Para comprobar un array utiliza:

```JavaScript
Array.isArray(numeros); // true
```

## 7. JavaScript frente a TypeScript

La diferencia fundamental empieza a verse claramente con este estema.

JavaScript permite:

```JavaScript
let edad = 27;

edad = "veintisiete";
```
El error, si lo hubiera, aparecerá posteriormente cuando el programa intente utilizar `edad` como un número.

TypeScript intenta detectar el problema antes:

```TypeScript
let edad: number = 27;

edad = "veintisiete"; // Error
```

Además, TypeScript suele inferir el tipo:

```TypeScript
let edad = 27;
```

No necesitas escribir siempre:

```TypeScript
let edad: number = 27;
```

TypeScript ya deduce que es un `number`.

Donde si conviene ser explícito es cuando el tipo forma parte del contrato o ayuda a entender la intención:

```TypeScript
function buscarUsuario(id: number): Usuario | null {
  // ...
}
```

Ahí los tipos de parámetros y retorno ayudan mucho a seguir el flujo.

