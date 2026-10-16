# Funciones Fundamentos

Las funciones son uno de los fundamentos más importantes de JavaScript y TypeScript.  
Permiten organizar el código en bloques reutilizables, dividir problemas complejos en tareas más pequeñas y evitar la repetición de instrucciones.

Ambos lenguajes comparten las mismas formas de declarar y utilizar funciones. La principal diferencia es que TypeScript permite definir los tipos de los parámetros y de los valores que devuelve una función, proporcionando mayor seguridad durante el desarrollo.

## 1. Function Declaration (Declaración de funciones)

Una **Function Declaration** es una de las formas tradicionales de definir funciones en JS y TS. Consiste en declarar una función utilizando la palabra reservada `function`, seguida de un nombre, una lista de parámetros entre paréntesis y un bloque de código delimitado por llaves. Las instrucciones que contiene solamente se ejecutan cuando la función es invocada, lo que permite reutilizar una misma operación tantas veces como sea necesario.

Una característica importante de las funciones declaradas es su comportamiento durante el proceso conocido como *hoisting*. JavaScript registra estas declaraciones antes de comenzar a ejecutar el código, permitiendo invocar una función incluso antes de que aparezca su declaración dentro del mismo ámbito.

**Ejemplo**

```TypeScript
function calcularTotal(precio: number, cantidad: number): number {
    return precio * cantidad;
}

const total = calcularTotal(150, 3);

console.log(total); // 450
```

En ambos casos, la función recibe el precio y la cantidad, realiza una multiplicación y devuelve el resultado mediante `return`.


## 2. Function Expression (Expresión de funciones)

Una **Function Expression** consiste en crear una función como parte de una expresión, generalmente asignándola a una variable. A diferencia de una Function Declaration, la función no necesita tener un nombre propio, ya que puede ser identificada y utilizada mediante la varaible que la contiene. Esta característica permite tratar las funciones como valores, almacenarlas en variables y pasarlas como argumentos a otras funciones.

Una diferencia importante es que las funciones asignadas mediante `const` o `let` no pueden utilizarse antes de que se ejecute su inicialización. Esto ocurre porque, aunque estas variables pertenecen al proceso de *hoisting*, permanecen inaccesibles hasta alcanzar su declaración. Habitualmente se utiliza `const` cuando no necesitamos reasignar la función a otra variable.

**Ejemplo**

```TypeScript
const calcularDescuento = function(
    precio: number,
    descuento: number
): number {
    return precio - (precio * descuento / 100);
};

const precioFinal = calcularDescuento(1000, 20);

console.log(precioFinal); // 800
```

En este caso, creamos una función anónima mediante `function` y la asignamos a la constante `calcularDescuento`.

Aunque utilizamos una sintaxis diferente, su comportamiento al ejecutarla es equivalente al de una función declarada tradicionalmente.

**Diferencia fundamental**:

* **Function Declaration**: declaramos una función directamente mediante `function nombre()` .
* **Function Expression**: creamos una función y la asignamos a una variable mediante `const nombre = function()`.

## 3. Arrow Functions (Funciones flecha)

Las **Arrow Functions** son una forma más concisa de escribir funciones, introducida en ECMAScript 2015 (ES6). Se caracterizan por utilizar el operador `=>` en lugar de la palabra reservada `function`. Su objetivo es ofrecer una sintaxis más sencilla, especialmente cuando necesitamos funciones pequeñas o funciones que se pasan como argumentos a otras operaciones. Si el cuerpo contiene una única expresión, podemos omitir las llaves y la palabra `return`, ya que el resultado se devuelve automáticamente.

Sin embargo, las Arrow Functions no son solamente una versión abreviada de las funciones tradicionales. Una de sus principales diferencias es que no tienen su propio contexto de `this`, sino que utilizan el contexto del ámbito donde fueron creadas. Este comportamiento resulta especialmente útil al trabajar con callbacks y operaciones asíncronas, aunque también significa que no son adecuadas para todos los escenarios, como ciertos métodos de objetos que necesitan utilizar su propio `this`.

**Ejemplo**

```TypeScript
const precio: number[] = [100, 200, 300];

const aplicarDescuento = (precio: number): number => precio * 0.90;

const preciosFinales = precio.map(aplicarDescuento);

console.log(preciosFinales); // [90, 180, 270]
```

La función `aplicarDescuento` recibe un precio y devuelve su valor reducido en un 10%.

Posteriormente, utilizamos `map()` para aplicar esa función a cada elemento del arreglo, obteniendo una nueva lista con los precios actualizados.

También podemos escribir una Arrow Function utilizando llaves:

```TypeScript
const aplicarDescuento = (precio: number): number => {
    return precio * 0.90;
};
```

Cuando utilizamos llaves, debemos escribir explícitamente `return` si queremos devolver un resultado.

## 4. Parámetros (Parameters)

Los **parámetros** son variables declaradas dentro de los paréntesis de una función que permiten escribir información desde el lugar donde se realiza su llamada. Gracias a ellos, una misma función puede trabajar con diferentes datos sin necesidad de modificar su implementación. Es importante distinguir entre parámetros y argumentos: los parámetros son los nombres definidos al declarar la función, mientras que los argumentos son los valores concretos proporcionados cuando se invoca.

En JavaScript, los parámetros no tienen restricciones de tipo establecidas por el lenguaje, por lo que pueden recibir distintos tipos de valores. TypeScript permite definir explícitamente qué tipo de dato acepta cada parámetro, lo que facilita detectar errores durante el desarrollo. Estos tipos solamente existen durante el análisis y la compilación de TypeScript; no generan validaciones automáticas en el código JavaScript resultante.

**Ejemplo**

```JavaScript
function registrarReserva(nombre, personas, horario){
    console.log(`Reserva para: ${nombre}`);
    console.log(`Cantidad de personas: ${personas}`);
    console.log(`Horario: ${horario}`);
}

registrarReserva("Agustín", 4, "21:00");
```

```TypeScript
function registrarReserva(
    nombre: string, 
    personas: number, 
    horario: string
): void {
    console.log(`Reserva para: ${nombre}`);
    console.log(`Cantidad de personas: ${personas}`);
    console.log(`Horario: ${horario}`);
}

registrarReserva("Agustín", 4, "21:00");
```

En este ejemplo:

* `nombre`, `personas` y `horario` son los **parámetros**.
* `"Agustín"`, `4` y `"21:00"` son los **argumentos**.
* `string` y `number` indican los tipos que espera TypeScript.
* `void` indica que la función no está diseñada para devolver un valor útil.

## 5. Parámetros opcionales (Optional Parameters)

Los **parámetros opcionales** permiten definir funciones en las que determinados datos no son obligatorios para realizar una operación. Esto significa que podemos invocar una función proporcionando solamente la información necesaria, mientras que los parámetros adicionales pueden omitirse. En JavaScript, cualquier parámetro puede quedar sin un argumento correspondiente y, cuando esto sucede, su valor será `undefined`.

TypeScript incorpora una sintaxis específica para presentar este comportamiento mediante el operador `?`, colocado después del nombre del parámetro. De esta manera, podemos indicar explícitamente qué información es opcional. Como un parámetro opcional puede contener `undefined`, debemos considerar esa posibilidad antes de utilizarlo en operaciones que necesitan un valor concreto. Además, un parámetro obligatorio no puede declararse después de uno opcional en la lista de parámetros de TypeScript.

**Ejemplo**

```TypeScript
function registrarCliente(
    nombre: string,
    telefono?: string
): void {
    console.log(`Cliente: ${nombre}`);

    if(telefono !== undefined){
        console.log(`Telefono: ${telefono}`);
    }
}

registrarCliente("Agustín");
registrarCliente("Olga", "099123456");
```

En TypeScript, `telefono?: string` indica que el parámetro puede recibir un texto o no recibir ningún valor.

Conceptualmente, dentro de la función podemos considerar que su tipo es:

```TypeScript
string | undefined
```

Esto significa que el valor puede ser una cadena de texto o `undefined`.

## 6. Default Parameters (Parámetros con valores predeterminados)

Los **Default Parameters** permiten asignar un valor predeterminado a un parámetro cuando el argumento correspondiente no se proporciona al invocar una función. Esta característica resulta especialmente útil cuando existe un comportamiento habitual que queremos aplicar automáticamente, pero también necesitamos permitir que quien utiliza la función pueda modificarlo proporcionando otro valor.

En JavaScript y TypeScript, los valores predeterminados se establecen mediante el operador `=` dentro de la declaración de los parámetros. El valor predeterminado se utiliza cuando el argumento es omitido o cuando se proporciona explícitamente `undefined`, pero no cuando recibe `null`. En TypeScript, además, el compilador puede inferir el tipo del parámetro a partir de su valor inicial, por lo que no siempre es necesario especificarlo manualmente.

**Ejemplo**

```TypeScript
function calcularTotal(
    precio: number,
    costoEnvio: number = 150
): number {
    return precio + costoEnvio;
};

console.log(calcularTotal(1000));          // 1150
console.log(calcularTotal(1000, 250));     // 1250
console.log(calcularTotal(1000, 0));       // 1000
``` 

Cuando llamamos a `calcularTotal(1000)`, la función utiliza automáticamente el costo de envío predeterminado de $150.

Si proporcionamos un segundo argumento, este reemplaza el valor predeterminado. Por ejemplo, podemos cobrar $250 por un envío especial o utilizar `0` para representar un envío gratuito.

## 7. Return Values (Valores de retorno)

Los **valores de retorno** representan el resultado que una función entrega al código que la invocó. Para devolver un valor utilizamos la palabra reservada `return`, seguida de una expresión cuyo resultado queremos proporcionar. Este mecanismo permite que una función realice un cálculo, una comparación o cualquier otra operación y entregue información que posteriormente puede almacenarse en una variable, utilizarse en una condición o enviarse a otra función.

Una característica fundamental de `return` es que finaliza inmediatamente la ejecución de la función, por lo que cualquier instrucción ubicada después de un `return` ejecutado no será alcanzada. En JavaScript, cuando una función termina sin devolver explícitamente un valor, su resultado es `undefined`. TypeScript permite definir el tipo del valor de retorno después de los parámetros, mediante `: tipo`, y utiliza habitualmente `void` para representar funciones cuyo resultado no está destinado a ser utilizado.

**Ejemplo**

```TypeScript
function verificarStock(
    stockDisponible: number,
    cantidadSolicitada: number
): boolean {
    return cantidadSolicitada <= stockDisponible
}

const disponible = verificarStock(10, 5);

console.log(disponible); // true
```

La función compara la cantidad solicitada con las unidades disponible. Si el cliente solicita más unidades de las existentes, devuelve `false` y finaliza su ejecución inmediatamente.
En caso contrario, devuelve `true`.

En TypeScript, `: boolean` establece que el resultado de la función debe ser un valor booleano.

**Funciones sin valores de retorno**

No todas las funciones necesitan devolver información. Algunas solamente realizan acciones, como mostrar mensajes, actualizar elementos de una interfaz o registrar información.

```TypeScript
function mostrarMensaje(mensaje: string): void {
    console.log(mensaje);
}

mostrarMensaje("Compra realizada correctamente");
```

En este caso, la función ejecuta una instrucción, pero no utiliza `return` para devolver un resultado.

Por eso, en TypeScript utilizamos `void`, indicando que no esperamos utilizar un valor devuelto por esta función.

## 8. Guardar funciones en variables

En JavaScript, las funciones son consideradas **valores de primera clase (first-class functions)**. Esto significa que pueden manipularse de manera similar a otros valores del lenguaje, como números, cadenas de texto u objetos. Gracias a esta característica, podemos almacenar una función dentro de una variable y posteriormente utilizar esa variable para ejecutarla.

Cuando asignamos una función a una variable, no estamos ejecutando su contenido, sino almacenando una referencia a ella. Esto permite que una misma función pueda utilizarse desde diferentes variables sin necesidad de duplicar su implementación. Para ejecutar la función almacenada, simplemente debemos utilizar los paréntesis `()` después del nombre de la variable.

Este comportamiento resulta útil cuando necesitamos seleccionar dinámicamente qué operación ejecutar, organizar diferentes comportamientos o trabajar con funciones que serán utilizadas posteriormente.

**Ejemplo: Sistema de descuento**

En este ejemplo, almacenamos una función anónima dentro de la variable `calcularDescuento`.

Cuando ejecutamos `calcularDescuento(1500)`, la función recibe el precio y retorna el 10 % correspondiente al descuento.

```TypeScript
const calcularDescuento = function (precio: number): number {
    return precio * 0.10;
};

const descuento: number = calcularDescuento(1500);

console.log(descuento); // 150
```

También podemos definir explícitamente el tipo de la variable que almacena la función:

```TypeScript
const calcularDescuento: (precio: number) => number = function (precio) {
    return precio * 0.10;
};
```

La expresión `(precio: number) => number` describe la firma de la función: recibe un número y retorna otro número.

## 9. Pasar funciones como argumentos

En JavaScript y TypeScript, una función puede recibir otra función como argumento, de la misma manera que recibe números, cadenas de texto u objetos. Esto permite que una función delegue parte de su comportamiento a otra, sin necesidad de conocer previamente las instrucciones que esta última ejecutará.

Esta característica es especialmente útil cuando queremos desarrollar funciones reutilizables cuyo comportamiento pueda cambiar dependiendo de la operación recibida. En lugar de crear diferentes funciones que repitan una misma estructura, podemos definir una función principal y proporcionarle las operaciones específicas que debe realizar.

Al pasar una función como argumento, normalmente utilizamos su nombre sin paréntesis, porque queremos entregar la referencia para que pueda ejecutarse posteriormente. Si utilizamos los paréntesis, estaremos ejecutando la función inmediatamente y pasando su resultado, salvo que ese sea precisamente el comportamiento que buscamos.

**Ejemplo: Procesamiento de pagos**

La función `procesarPago` recibe dos argumentos: el monto de la operación y una función que representa el método de pago.

Cuando ejecutamos `metodoPago(monto)`, estamos invocando la función que recibimos como argumento.

De esta manera, `procesarPago` no necesita conocer los detalles de cada método de pago.

```TypeScript
function pagarConTarjeta(monto: number): void {
    console.log(`Pagando $${monto} con tarjeta`);
}

function pagarConEfectivo(monto: number): void {
    console.log(`Pagando $${monto} en efectivo`);
}

function procesarPago(
    monto: number,
    metodoPago: (monto: number) => void
): void {
    metodoPago(monto);
}

procesarPago(1500, pagarConTarjeta);
procesarPago(800, pagarConEfectivo);
```

En TypeScript encontramos una declaración importante:

```TypeScript
metodoPago: (monto: number) => void
```

Esta expresión indica que `metodoPago` debe ser una función que reciba un número y no retorne ningún valor significativo.

## 10. Retornar funciones

Además de retornar valores tradicionales, como números, cadenas de texto u objetos, una función también puede retornar otra función. Esto significa que, al ejecutar una función, podemos obtener como resultado una nueva función que posteriormente podremos almacenar, ejecutar o pasar como argumento.

Una característica especialmente importante de este comportamiento es que las funciones internas pueden conservar el acceso a las variables del entorno donde fueron creadas, incluso después de que la función externa haya terminado su ejecución. Este mecanismo se conoce como closure (clausura) y permite construir funciones que recuerdan determinados valores o configuraciones.

Retornar funciones resulta útil cuando necesitamos crear operaciones personalizadas, reutilizar configuraciones o generar comportamientos específicos a partir de parámetros iniciales.

**Ejemplo: Crear descuentos personalizados**

```TypeScript
function crearDescuento(
    porcentaje: number
): (precio: number) => number {

    return function (precio: number): number {
        return precio * porcentaje / 100;
    };

}

const descuento10 = crearDescuento(10);
const descuento20 = crearDescuento(20);

console.log(descuento10(1500)); // 150
console.log(descuento20(1500)); // 300
```

Primero ejecutamos:

```TypeScript
const descuento10 = crearDescuento(10);
```

La función `crearDescuento` recibe el valor `10` y retorna una nueva función.

Esa función queda almacenada dentro de la variable `descuento10`.

Posteriormente ejecutamos:

```TypeScript
descuento10(1500);
```

La función interna recibe el precio `1500` y utiliza el porcentaje `10` que había quedado almacenado en su entorno.

Esto es posible gracias al mecanismo de `closure`.

Observemos el tipo de retorno:

```TypeScript
(precio: number) => number
```

En este caso, `crearDescuento` no retorna directamente un número, sino una función que recibe un número y retorna otro número.

Esta distinción es fundamental para comprender cómo TypeScript representa funciones que generan otras funciones.

## 11. Callbacks

Un **callback** es una función que se proporciona a otra función para que esta pueda ejecutarla en un momento determinado. En otras palabras, es una función cuyo momento de ejecución queda bajo el control de otra función. Este mecanismo permite separar una operación principal de las acciones que deben realizarse durante su ejecución o una vez que se haya completado.

Los callbacks se utilizan frecuentemente para procesar resultados, responder a eventos del usuario y ejecutar operaciones cuando se cumple determinada condición. También son habituales en operaciones asíncronas, como solicitudes HTTP o temporizadores, donde necesitamos ejecutar instrucciones después de que ocurra algún acontecimiento.

Es importante comprender que **un callback no necesariamente es asíncrono**. Existen callbacks síncronos, que se ejecutan inmediatamente durante una operación, y callbacks asíncronos, cuya ejecución ocurre posteriormente. Lo que define a un callback no es cuándo se ejecuta, sino el hecho de que una función se entrega a otra para que esta decida cuándo invocarla.

**Ejemplo: Confirmación de compra**

En este ejemplo, `mostrarConfirmacion` funciona como callback porque se entrega como argumento a `realizarCompra`.

La función principal registra la compra y posteriormente ejecuta el callback.

Esto permite que la confirmación pueda cambiar sin modificar la lógica principal.

```TypeScript
function mostrarConfirmacion(): void {
    console.log("Compra realizada correctamente");
}

function realizarCompra(
    producto: string,
    callback: () => void
): void {

    console.log(`Registrando compra de: ${producto}`);

    callback();
}

realizarCompra("Notebook", mostrarConfirmacion);
```

El tipo:

```TypeScript
callback: () => void
```

Indica que el callback es una función que no recibe parámetros y no retorna ningún valor significativo.

**Ejemplo de callback asíncrono**

En este caso, setTimeout recibe una función que se ejecutará después de que transcurra el tiempo establecido, siempre que el entorno de ejecución pueda atenderla.

Cuando se ejecuta esa función, invoca nuestro callback para enviar la confirmación.

```TypeScript
function procesarCompra(callback: () => void): void {

    console.log("Procesando compra...");

    setTimeout((): void => {
        console.log("Compra procesada");

        callback();
    }, 2000);

}

procesarCompra((): void => {
    console.log("Enviando confirmación al cliente");
});
```

Este ejemplo permite observar cómo los callbacks se utilizan para organizar operaciones que no se completan inmediatamente.

En aplicaciones reales, este tipo de comportamiento aparece al trabajar con eventos, temporizadores y operaciones asíncronas.

## 12. Higher-order functions

Las **higher-order functions**, también conocidas como funciones de orden superior, son funciones que cumplen al menos una de estas dos condiciones: reciben una o más funciones como argumentos o retornan una función como resultado. Este concepto es posible porque JavaScript permite tratar las funciones como valores de primera clase.

Su principal utilidad consiste en construir operaciones más flexibles y reutilizables, separando la lógica general de los comportamientos específicos. En lugar de implementar repetidamente una misma estructura para realizar diferentes operaciones, podemos desarrollar funciones capaces de recibir el comportamiento que necesitan ejecutar.

JavaScript incorpora numerosas funciones de orden superior, especialmente en el trabajo con arreglos. Métodos como `map()`, `filter()` y `reduce()` permiten transformar, seleccionar y acumular elementos mediante funciones proporcionadas como argumentos. Estas herramientas son fundamentales para procesar colecciones de datos en aplicaciones modernas.

**Ejemplo: Filtrar productos por precio**

En este ejemplo, `filter()` es una función de orden superior porque recibe una función como argumento.

La función que proporcionamos es un callback que se ejecuta para cada producto del arreglo.

Si el callback retorna `true`, el producto se incluye en el nuevo arreglo. Si retorna `false`, se descarta.

```TypeScript
interface Producto {
    nombre: string;
    precio: number;
}

const productos: Producto[] = [
    { nombre: "Mouse", precio: 500 },
    { nombre: "Teclado", precio: 1500 },
    { nombre: "Monitor", precio: 8000 },
    { nombre: "Auriculares", precio: 900 }
];

const productosCaros: Producto[] = productos.filter(
    (producto: Producto): boolean => {
        return producto.precio > 1000;
    }
);

console.log(productosCaros);
```

En TypeScript definimos una interfaz `Producto` para establecer la estructura que deben cumplir los objetos.

El callback recibe un objeto de tipo `Producto` y retorna un booleano que determina si el elemento debe incluirse en el resultado.

**Crear nuestra propia higher-order function**

No estamos limitados a utilizar las funciones de orden superior que proporciona JavaScript. También podemos desarrollar nuestras propias implementaciones.

Supongamos que necesitamos ejecutar diferentes operaciones matemáticas sobre dos números.

La función `ejecutarOperacion` es una función de orden superior porque recibe otra función como argumento.

Las funciones `sumar` y `multiplicar` actúan como callbacks.

```TypeScript
type Operacion = (a: number, b: number) => number;

function ejecutarOperacion(
    a: number,
    b: number,
    operacion: Operacion
): number {
    return operacion(a, b);
}

function sumar(a: number, b: number): number {
    return a + b;
}

function multiplicar(a: number, b: number): number {
    return a * b;
}

console.log(ejecutarOperacion(10, 5, sumar));
// 15

console.log(ejecutarOperacion(10, 5, multiplicar));
// 50
```

En esta implementación utilizamos:

```TypeScript
type Operacion = (a: number, b: number) => number;
```

Esto permite definir un alias de tipo llamado `Operacion`, que representa cualquier función que reciba dos números y retorne un número.

De esta manera, evitamos repetir la misma definición de tipo cada vez que necesitamos recibir una función con esas características.

## 13. Diferencia entre callbacks y higher-order functions

Aunque estos conceptos están relacionados, no representan exactamente lo mismo.

Una **higher-order function** es una función que recibe otras funciones como argumentos o retorna funciones como resultado.

Un **callback**, en cambio, es la función que entregamos como argumento para que otra función la ejecute.

Observemos el siguiente ejemplo:

```JavaScript
function procesarDatos(callback) {
    const datos = [10, 20, 30];

    callback(datos);
}

function mostrarDatos(datos) {
    console.log(datos);
}

procesarDatos(mostrarDatos);
```

En este caso:

* `procesarDatos` es un **higher-order function**, porque recibe una función como argumento.
* `mostrarDatos` actúa como **callback**, porque se entrega a otra función para que esta la ejecute.
* `callback(datos)` representa la ejecución del callback.
* `procesarDatos(mostrarDatos)` representa el momento en que pasamos la referencia de la función.

También es importante recordar que una función de orden superior no necesita recibir callbacks para ser considerada como tal. Es suficiente con que retorne otra función.

## 14. Rest Parameters (`...args`)

Los **Rest Parameters** son una característica de JavaScript que permite definir funciones capaces de recibir una cantidad variable de argumentos sin necesidad de declarar un parámetro para cada uno. Para utilizarlos, se coloca el operador `...` delante del nombre del último parámetro de una función. De esta manera, todos los argumentos adicionales que recibe la función se agrupan automáticamente dentro de un array.

Esta característica resulta especialmente útil cuando no conocemos de antemano cuántos valores recibirá una función. Por ejemplo, podemos necesitar calcular el total de una cantidad variable de productos, procesar múltiples identificadores o registrar una serie de mensajes. En lugar de crear funciones diferentes para cada cantidad de argumentos, podemos utilizar Rest Parameters para desarrollar una única función que se adapte a todos esos escensarios.

Es importante comprender que **Rest Parameters siempre genera un array**, incluso cuando la función recibe un único argumento o ninguno. Además, solamente puede existir un parámetro Rest por función y debe encontrarse al final de la lista de parámetros.

**Ejemplo: calcular el total de una compra**

```TypeScript
function calcularTotal(...precios: number[]): number {
    let total: number = 0;

    for (const precio of precios) {
        total += precio;
    }

    return total;
}

console.log(calcularTotal(100, 200, 300)); // 600
```

Cuando ejecutamos:

```TypeScript
calcularTotal(100, 200, 300);
```

JavaScript agrupa automáticamente los argumentos dentro de un array:

```TypeScript
precios = [100, 200, 300];
```

La diferencia principal es que TypeScript nos permite especificar que todos los argumentos recibidos deben ser números mediante `number[]`.

Por ejemplo:

```TypeScript
calcularTotal(100, "200", 300); // Error de TypeScript
```

**Combinar parámetros normales con Rest**

También podemos combinar parámetros tradicionales con Rest Parameters.

```TypeScript
function registrarVenta(
    cliente: string,
    ...productos: string[]
): void {
    console.log(`Cliente: ${cliente}`);
    console.log(`Productos: ${productos.join(", ")}`);
}

registrarVenta("Juan", "Teclado", "Mouse", "Monitor");
```

Resultado:

```
Cliente: Juan
Productos: Teclado, Mouse, Monitor
```

En este caso:

* `cliente` recibe el primer argumento.
* `...productos` agrupa todos los argumentos restantes.

**Concepto clave**: Rest Parameters permite que una función reciba múltiples argumentos y los agrupe dentro de un array.

## 15. Spread en arrays

El operador **Spread** permite expandir los elementos de un array para utilizarlos individualmente dentro de otra estructura o como argumentos de una función. Se representa mediante los mismos tres puntos (`...`) utilizados por Rest Parameters, pero su comportamiento es diferente: mientras Rest agrupa múltiples valores, Spread toma una colección existente y expande sus elementos.

Una de sus aplicaciones más habituales consiste en combinar arrays, agregar elementos a una colección o crear copias de arrays existentes. Esto resulta especialmente útil cuando queremos construir nuevas estructuras de datos sin modificar directamente las originales, una práctica frecuente en el desarrollo de aplicaciones JavaScript y TypeScript.

Sin embargo, debemos tener presente que Spread realiza una **copia superficial (shallow copy)**. Esto significa que crea un nuevo array, pero si alguno de sus elementos contiene objetos u otros arrays, las referencias a esas estructuras internas se mantienen compartidas.

**Ejemplo: combinar productos de diferentes categorías**

```TypeScript
const electronica: string[] = [
    "Notebook",
    "Monitor",
    "Teclado"
];

const accesorios: string[] = [
    "Mouse",
    "Auriculares"
];

const productos: string[] = [
    ...electronica,
    ...accesorios
];

console.log(productos);
```

Resultado:

```TypeScript
[
    "Notebook",
    "Monitor",
    "Teclado",
    "Mouse",
    "Auriculares"
]
```

Cuando escribimos:

```TypeScript
[...electronica, ...accesorios]
```

Spread expande los elementos de ambos arrays y los incorpora dentro de uno nuevo.

Los arrays originales permanecen intactos.

**Agregar elementos sin modificar el array original**

Otra aplicación muy frecuente consiste en agregar elementos a un array.

```TypeScript
const productos: string[] = [
    "Notebook",
    "Monitor"
];

const nuevosProductos: string[] = [
    ...productos,
    "Teclado"
];

console.log(productos);
console.log(nuevosProductos);
```

Resultado:

```TypeScript
["Notebook", "Monitor"]

["Notebook", "Monitor", "Teclado"]
```

`producto` no fue modificado. En su lugar, creamos un nuevo array con sus elementos y agregamos uno adicional.


**Copiar un array**

También podemos utilizar Spread para crear una copia superficial:

```TypeScript
const numeros: number[] = [10, 20, 30];

const copia: number[] = [...numeros];

copia.push(40);

console.log(numeros); // [10, 20, 30]
console.log(copia);   // [10, 20, 30, 40]
```

Ambos arrays son estructuras independientes, aunque los objetos anidados que pudieran contener seguirían compartiendo referencias.

**Concepto clave**: Spread permite expandir los elementos de un array para combinarlos, copiarlos o utilizarlos individualmente.

## 16. Spread en objetos

El operador **Spread aplicado a objetos** permite copiar las propiedades propias y enumerables de un objeto dentro de otro. Su funcionalidad es similar al Spread utilizado en arrays, pero en lugar de expandir elementos, expande propiedades junto con sus respectivos valores. Esto permite construir nuevos objetos a partir de otros existentes de una manera sencilla y legible.

Esta característica se utiliza frecuentemente para actualizar información, combinar configuraciones o crear nuevas versiones de un objeto sin modificar el original. Por ejemplo, cuando un usuario actualiza su perfil, podemos conservar todas sus propiedades actuales y reemplazar únicamente aquellas que hayan cambiado.

Una característica importante es que **cuando dos objetos contienen propiedades con el mismo nombre**, **prevalece el último valor asignado**. Además, al igual que ocurre con los arrays, Spread realiza una copia superficial, por lo que los objetos anidados continúan compartiendo referencias.

**Ejemplo: actualizar los datos de un usuario**

```TypeScript
interface: Usuario {
    id: number;
    nombre: string;
    email: string;
    activo: boolean;
}

const usuario: Usuario = {
    id: 1,
    nombre: "Juan",
    email: "juan@gmail.com",
    activo: true
};

const usuarioActualizado: Usuario = {
    ...usuario,
    email: "juan@hotmail.com"
};
```

**Combinar objetos**

Spread también permite combinar propiedades provenientes de diferentes objetos.

```TypeScript
const datosPersonales = {
    nombre: "Juan",
    apellido: "Pérez"
};

const datosContacto = {
    email: "juan@gmail.com",
    telefono: "099123456"
};

const usuario = {
    ...datosPersonales,
    ...datosContacto
};

console.log(usuario);
```

Resultado:

```TypeScript
{
    nombre: "Juan",
    apellido: "Pérez",
    email: "juan@gmail.com",
    telefono: "099123456"
}
```

De esta manera, podemos construir objetos más completos a partir de estructuras más pequeñas.

**Cuidado con los objetos anidados**

```TypeScript
const usuario = {
    nombre: "Juan",
    direccion: {
        ciudad: "Montevideo"
    }
};

const copia = { ...usuario };

copia.direccion.ciudad = "Maldonado";

console.log(usuario.direccion.ciudad);
```

Resultado:

```
Maldonado
```

Esto ocurre porque Spread copió la referencia al objeto `direccion`, no creó una copia independiente de él.

Para evitarlo, podemos copiar también el objeto anidado:

```TypeScript
const copia = {
    ...usuario,
    direccion: {
        ...usuario.direccion
    }
};
```

Ahora `copia.direccion` es un objeto independiente del original.

**Concepto clave:** Spread en objetos permite copiar, combinar y actualizar propiedades, creando nuevos objetos sin modificar directamente los originales, siempre teniendo presente que la copia es superficial.

## 17. Diferencia entre Rest y Spread

Aunque Rest y Spread utilizan exactamente la misma sintaxis (`...`), representan operaciones conceptualmente opuestas.
**Rest se utiliza para agrupar múltiples valore dentro de una única estructura, mientras que Spread se utiliza para expandir los valores contenidos en una estructura existente**. Por lo tanto, su comportamiento depende del contexto en el que aparece el operador.

Rest se utiliza principalmente en la declaración de parámetros de funciones y en operaciones de desestructuración, donde necesitamos reunir varios elementos en una variable. Spread, por el contrario, se utiliza en llamadas a funciones, arrays y objetos, donde necesitamos distribuir los elementos o propieades de una estructura.

## 18. Closures

Un **closure (clausura)** es el mecanismo que permite que una función conserve acceso a las variables de su ámbito léxico exterior, incluso cuando la función que contenía esas variables ya terminó de ejecutarse. Esto sucede porque JavaScript mantiene las referencias necesarias para que la función interna pueda continuar utilizando la información de su entorno original. Los closures no requieren una sintaxis especial: aparecen naturalmente cuando una función utiliza variables de un ámbito exterior.

Este comportamiento permite crear funciones que mantienen un estado privado entre diferentes ejecuciones. En lugar de almacenar información en variables globales, podemos declarar variables dentro de una función y devolver otra función que tenga acceso a ellas.

De esta manera, conseguimos controlar cómo se consulta o modifica esa información, evitando que otras partes del programa pueda manipularla directamente.

Aunque todas las funciones de JavaScript se crean con un entorno léxico asociado, los closures resultan especialmente evidentes cuando una función interna continúa utilizándose después de que sun función exterior haya finalizado. Este patrón es habitual en contadores, configuraciones personalizadas, callbacks, manejadores de eventos y diferentes mecanismos de encapsulación.

**Ejemplo**

```TypeScript
function crearContadorVentas(): () => number {
    let ventas: number = 0;

    return function(): number => {
        ventas++;

        return ventas;
    };
}

const registrarVentas: () => number = crearContadorVentas();

console.log(registrarVenta()); // 1
console.log(registrarVenta()); // 2
console.log(registrarVenta()); // 3
```

**¿Qué está sucediendo?**

**Paso 1. Ejecutamos la función exterior.**

```TypeScript
const registrarVentas: () => number = crearContadorVentas();
```

JavaScript ejecuta `crearContadorVentas()`.

Dentro de ella se declara:

```TypeScript
let ventas: number = 0;
```

Después, la función devuelve otra función que utiliza esa variable.

**Paso 2. La función exterior termina.**

Normalmente, las variables locales dejan de ser necesarias cuando finaliza la ejecución de una función.

Sin embargo, en este caso existe una función interna que todavía neceesita acceder a `ventas`.

Por ese motivo, JavaScript conserva el entorno necesario para mantener esa referencia.

**Paso 3. Ejecutamos la función interna.**

```TypeScript
registrarVenta(); //1
```

La función incrementa `ventas` de `0` a `1`.

Cuando volvemos a ejecutarla:

```TypeScript
registrarVenta(); //2
```

No se crea nuevamente la variable `ventas`.

La función utiliza la misma variable que quedó asociada a su closure.

**¿Qué sucede si creamos dos contadores?**

```TypeScript
const contadorA: () => number = crearContadorVentas();
const contadorB: () => number = crearContadorVentas();

console.log(contadorA()); // 1
console.log(contadorA()); // 2

console.log(contadorB()); // 1

console.log(contadorA()); // 3
```

Cada ejecución de `crearContadorVentas()` crea un entorno independiente.

Los contadores no comparten la variable `ventas`.

**Concepto clave**: un closure permite que una función conserve acceso a la variables de su entorno original y mantenga información entre diferentes ejecuciones.

**Caso 1: Administrar un carrito de compras**

Supongamos que desarrollamos un comercio electrónico y necesitamos administrar los productos agregados a un carrito.

Queremos permitir que se agreguen productos y consultar el total, pero sin exponer directamente la colección interna.

```TypeScript
interface Producto {
    nombre: string;
    precio: number;
}

interface Carrito {
    agregarProducto(producto: Producto): void;
    obtenerTotal(): number;
}

function crearCarrito(): Carrito {
    const productos: Producto[] = [];

    return {
        agregarProducto(producto: Producto): void {
            productos.push(producto);
        },
        obtenerTotal(): number {
            return productos.reduce(
                (total, producto) => total + producto.precio, 0
            );
        }
    };
}

const carrito = crearCarrito();

carrito.agregarProducto({
    nombre: "Teclado",
    precio: 1500
});

carrito.agregarProducto({
    nombre: "Mouse",
    precio: 800
});

console.log(carrito.obtenerTotal()); // 2300
```

**¿Dónde está el closure?**

El closure aparece en los métodos `agregarProducto()` y `obtenerTotal()`.

Ambos utilizan la variable `productos`, que fue declarada dentro de `crearCarrito()`.

Aunque `crearCarrito()` ya terminó de ejecutarse, los métodos continúan teniendo acceso a esa colección.
