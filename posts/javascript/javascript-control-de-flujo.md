# Control de Flujo

Las estructuras de control permiten determinar **cómo se ejecutan las instrucciones de un programa**. Gracias a ellas, podemos tomar decisiones, ejecutar acciones dependiendo de determinadas condiciones y repetir operaciones sin necesidad de escribir el mismo código varias veces.

En JavaScript y TypeScript, estas estructuras funcionan exactamente de la misma manera. La principal diferencia es que TypeScript permite definir tipos de datos, lo que ayuda a detectar ciertos errores durante el desarrollo.

## 1. `if` - Condicionales simple

La sentencia `if` es una estructura de control condicional que permite ejecutar un bloque de código únicamente cuando se cumple una condición determinada. Su funcionamiento consiste en evaluar una expresión y, si su resultado es verdadero (`true`), ejecuta las instrucciones que se encuentran dentro de sus llaves `{}`. Si la condición es falsa (`false`), el programa omite ese bloque y continúa ejecutando las instrucciones siguientes.

Esta estructura se utiliza cuando necesitamos que una acción dependa del cumplimiento de una condición. Por ejemplo, comprobar si un usuario tiene permisos para acceder a una funcionalidad, verificar si un producto tiene existencias o determinar si una persona cumple con una edad mínima.

**Ejemplo: verificar el stock de un producto**

```JavaScript
const stock = 10;

if(stock > 0){
  console.log("El producto está disponible");
}
```

```TypeScript
const stock: number = 10;

if(stock > 0){
  console.log("El producto está disponible");
}
```

En ambos casos, la condición `stock > 0` comprueba si existen unidades disponibles. Como tenemos 10 unidades, la condición es verdadera y el mensaje se muestra en la consola.

## 2. `else` - Condicional alternativo

La sentencia `else` permite establecer un bloque de instrucciones alternativo que se ejecutará cuando la condición definida es un `if` sea falsa. Ambas estructuras trabajan de una manera conjunta y permiten determinar qué acción debe realizarse dependiendo del resultado de una condición.

Esta estructura resulta útil cuando existen dos caminos posibles y necesitamos ejecutar uno de ellos de manera exclusiva. Por ejemplo, permitir o rechazar una operación, mostrar un mensaje de éxito o error, o determinar si un usuario puede acceder a un recurso.

**Ejemplo: comprobar el saldo de una cuenta**

```JavaScript
const saldo = 1500;
const precio = 2000;

if (saldo >= precio) {
  console.log("Compra realizada correctamente");
} else {
  console.log("Saldo insuficiente");
}
```

```TypeScript
const saldo: number = 1500;
const precio: number = 2000;

if (saldo >= precio) {
  console.log("Compra realizada correctamente");
} else {
  console.log("Saldo insuficiente");
}
```

La condición `saldo >= precio` comprueba si el dinero disponible es suficiente para realizar la compra.

Como el saldo es inferior al precio, la condición es falsa y se ejecuta el bloque `else`, mostrando el mensaje de `"Saldo insuficiente"`.

**Es importante comprender que `if` y `else` son excluyente**: es una misma evaluación, solamente se ejecutará uno de los dos bloques.

## 3. `else if` - Condicional múltiple

La sentencia `else if` permite evaluar condiciones adicionales cuando la condición es un `if` anterior no se cumple. A diferencia de `else`, que proporciona una alternativa sin evaluar una nueva condición, `else if` incorpora otra expresión que debe evaluarse antes de decidir si se ejecuta el bloque de código.

Esta estructura se utiliza cuando una operación puede tener varios resultados posibles y cada uno depende de una condición diferente. Las condiciones se evalúan de arriba hacia abajo y, cuando se encuentra la primera que resulta verdadera, se ejecuta el bloque y se omite las demás alternativas de la cadena.

**Ejemplo: calcular descuentos**

```TypeScript
const totalCompra: number = 3500;

if (totalCompra >= 5000) {
  console.log("Descuento del 20%");
} else if (totalCompra >= 2000) {
  console.log("Descuento del 10%");
} else {
  console.log("Sin descuento");
}
```

El programa comienza comprobando si la compra alcanza los $5000. Como esa condición es falsa, continúa evaluando la siguiente.

La segunda condición es verdadera porque el importe supera los $2000. Por lo tanto, se muestra el descuento dedl 10% y las condiciones restantes ya no se evalúan.

**El orden de las condiciones es importante**, especialmente cuando sus rangos pueden coincidir.

## 4. `switch` - Selección múltiple

La sentencia `switch` es una estructura de control que permite seleccionar qué bloque de instrucciones ejecutar según el valor de una expresión. Su funcionamiento consiste en evaluar dicha expresión una sola vez y comparar su resultado con los valores definidos mediante las cláusulas `case`. Cuando encuentra una coincidencia, comienza a ejecutar las instrucciones correspondientes.

Esta estructura resulta especialmente útil cuando necesitamos realizar diferentes acciones dependiendo del valor concreto de una variable, como el estado de un pedido, el rol de un usuario o una opción seleccionada de un menú. Habitualmente, cada `case` finaliza con `break` para evitar que la ejecucción continúe hacia los casos siguientes, mientras que `default` permite establecer una acción cuando ningún caso coincide.

**Ejemplo: gestionar el estado de un pedido**

```TypeScript
const estadoPedido: string = "enviado";

switch (estadoPedido) {

  case "pendiente":
    console.log("El estado está pendiente");
    break;
  case "enviado":
    console.log("El pedido está en camino");
    break;
  case "entregado":
    console.log("El pedido fue entregado");
    break;
  default:
    console.log("Estado desconocido");
}
```

El programa evalúa el contenido de `estadoPedido` y lo compara con cada uno de los valores definidos en los `case`.

Como su valor es `"enviado"`, se ejecuta el bloque correspondiente y se muestra `"El pedido está en camino"`.

La instrucción `break` finaliza la ejecución del `switch`. Si ningún caso coincidiera, se ejecutaría el bloque `default`.

**Diferencia con** `else if`: mientras que `else if` permite evaluar condiciones diferentes, como rangos numéricos o comparaciones, `switch` resulta especialmente adecuado cuando queremos comparar una misma expresión con diferentes valores concretos. Las comparaciones de `switch` utilizan igualdad estricta.

## 5. `for` - Bucle con contador

El bucle `for` es una estructura de control iterativa que permite ejecutar repetidamente un bloque de instrucciones mientras se cumpla una condición determinada. Su estructura tradicional se compone de tres elementos: una inicialización, que establece el valor inicial de una variable; una condición, que determina si el bucle debe continuar; y una actualización, que modifica dicha variable después de cada iteración.

Este bucle se utiliza principalmente cuando conocemos cuántas veces necesitamos repetir una operación o cuando queremos recorrer una colección de elementos mediante sus índices. Es habitual encontrarlo en operaciones como procesar listas, generar secuencias numéricas o realizar cálculos repetitivos.

**Ejemplo: calcular el total de varias compras**

```TypeScript
const precios: number[] = [100, 250, 150];
let total: number = 0;

for (let i = 0; i < precios.length; i++) {
  total += precios[i];
}

console.log(`Total: $${total}`);
```

El bucle comienza inicializando la variable `i` con el valor `0`, que corresponde al índice del primer elemento del arreglo.

Antes de cada iteración, comprueba si `i` es menor que `precios.length`. Mientras esa condición sea verdadera, suma el precio correspondiente al total y aumenta el contador mediante `i++`.

Una vez procesados todos los elementos, el bucle finaliza y el programa muestra:

```bash
Total: $500
```

**Descomposición del `for`**:

```JavaScript
for (let i = 0; i < precios.length; i++)
```

|Elemento|Función|
|--------|-------|
|`let i = 0`|Inicializa el contador.|
|`i < precios.length`|Establece la condición de continuación.|
|`i++`|Incrementa el contador después de cada iteración.|
|`precios[i]`|Accede al elemento ubicado en el índice actual.|

## 6. `for...of` - Recorrido de elementos

El bucle `for...of` es una estructura iterativa que permite recorrer directamente los valores de un objeto iterable, como un arreglo o una cadena de texto. A diferencia del `for` tradicional, no requiere declarar manualmente un contador ni acceder a los elementos mediante índices, ya que en cada iteración proporciona directamente el siguiente valor de la colección.

Esta estructura es especialmente útil cuando necesitamos procesar todos los elementos de una colección y no nos interesa conocer sus posiciones. Su sintaxis permite escribir código más sencillo y legible, especialmente al trabajar con listas de productos, usuarios, pedidos u otros conjuntos de información.

**Ejemplo: mostrar productos de un carrito**

```TypeScript
const productos: string[] = [
  "Notebook",
  "Mouse",
  "Teclado"
];

for (const producto of productos) {
  console.log(`Productos: ${producto}`);
}
```

El bucle comienza tomando el primer elemento del arreglo y asignándolo temporalmente a la variable `producto`. Después ejecuta las instrucciones del bloque y continúa con el siguiente elemento hasta recorrer la colección completa.

El resultado será:

```Bash
Producto: Notebook
Producto: Mouse
Producto: Teclado
```

**La diferencia fundamental es que `for` permite controlar las iteraciones mediante un contador, mientras que `for...of` proporciona directamente los valores de una colección**.

## 7. `while` - Bucle condicional

El bucle `while` es una estructura de control iterativa que ejecuta repetidamente un bloque de instrucciones mientras una condición sea verdadera. A diferencia del `for` tradicional, no incorpora obligatoriamente una inicialización ni una actualización dentro de su propia declaración, por lo que el programador debe gestionar los elementos necesarios para que la condición pueda cambiar.

Esta estructura se utiliza principalmente cuando no conocemos de antemano la cantidad exacta de iteraciones necesarias, pero sí sabemos qué condición debe cumplirse para continuar. Es frecuente utilizarla en procesos que dependen de un estado cambiante, como esperar a que se complete una operación, procesar elementos pendientes o repetir una acción mientras existan recursos disponibles.

**Ejemplo: procesar pedidos pendientes**

```TypeScript
let pedidosPendientes: number = 3;

while (pedidosPendientes > 0) {
  console.log("Procesando pedido...");

  pedidosPendientes--;
}

console.log("Todos los pedidos fueron procesados");
```

Amtes de comenzar cada iteración, el bucle comprueba si todavía existen pedidos pendientes.

Mientras la cantidad sea mayor que cero, ejecuta el procesamiento y disminuye el contador. Cuando la variable alcanza el valor `0`, la condición deja de cumplirse y el programa continúa con las instrucciones posteriores.

**Una característica importante de `while` es que pueda no ejecutarse ninguna vez**, porque evalúa la condición antes de entrar al bloque.

También debemos asegurarnos de que la condición pueda volverse falsa; de lo contrario, podríamos generar un bucle infinito.

## 8. `do...while` - Bucle con ejecución inicial

El bucle `do...while` es una estructura iterativa similar a `while`, pero con una diferencia fundamental: primero ejecuta el bloque de instrucciones y después evalúa la condición que determina si debe repetirse.  
Esto significa que las instrucciones contenidas en su interior siempre se ejeuctarán al menos una vez, independientemente del resultado inicial de la condición.

Esta estructura se utiliza cuando necesitamos realizar una acción antes de comprobar si debe repetirse. Es habitual encontrarla en sistemas que solicitan información al usuario, validaciones que requieren un primer intento o procesos que deben ejecutarse inicialmente antes de decidir si necesitan repetirse.

**Ejemplo: reintentar el envío de información**

```TypeScript
let intentos: number = 0;
let enviado: boolean = false;

do {
  intentos++;

  console.log(`Intento de envío: ${intentos}`);

  enviado = intentos === 2;
} while (!enviado && intentos < 3);

console.log("Proceso finalizado");
```

El programa comienza ejecutando el bloque sin comprobar ninguna condición previa. Después de cada intento, verifica si la información todavía no fue enviada y si no se alcanzó el límite de tres intentos.

La expresión `!enviado` significa que el envío no se realizó correctamente. Cuando `enviado` pasa a ser `true`, la condición completa resulta falsa y el bucle finaliza.

El resultado será:

```
Intento de envío: 1
Intento de envío: 2
Proceso finalizado
```

**La diferencia principal entre `while` y `do...while` es el momento en que se evalúa la condición: `while`** lo hace antes de ejecutar el bloque, mientras que `do...while` lo hace después.

## 9. `break` - Interrupción de ejecución

La sentencia `break` es una instrucción de control que permite finalizar inmediatamente la ejecucióndel bucle o `switch` más cercano que la contiene. Cuando el programa encuentra esta instrucción, abandona dicha estructura y continúa ejecutando el código que se encuentra después de ella, sin importar si todavía quedan iteraciones o casos pendientes.

Esta instrucción resulta especialmente útil cuando necesitamos detener un proceso al encontrar un resultado determinado. Por ejemplo, fianliza la búsqueda de un elemento, interrumpir una operación cuando se detecta un error o evitar que un `switch` continúe ejecutando otros casos.

**Ejemplo: buscar un pedido**

```TypeScript
const pedidos: number[] = [101, 102, 103, 104];
const pedidoBuscado: number[] = 103;

for (const pedido of pedidos) {
  if(pedido === pedidoBuscado) {
    console.log("Pedido encontrado");

    break;
  }

  console.log(`Revisando pedido ${pedido}`);
}
```

El bucle comienza recorriendo los identificadores de los pedidos. En cada iteración, compara el identificador actual con el pedido que estamos buscando.

Cuando encuentra el pedido `103`, muestra el mensaje correspondiente y ejecuta `break`, lo que provoca que el bucle termine inmediatamente.

Como consecuencia, el pedido `104` nunca llega a procesarse.

**Es importante comprender que `break` no finaliza la ejecución de todo el programa, sino únicamente la estructura de control más cercana a la que pertenece**.

## 10. `continue` - Salto de iteración

La sentencia `continue` es una instrucción de control que permite omitir las instrucciones restantes de la iteración actual y continuar con la siguiente iteración de un bucle. A diferencia de `break`, no provoca la finalización completa del ciclo, sino que modifica su flujo para evitar ejecutar determinadas operaciones bajo ciertas condiciones.

Esta instrucción es especialmente útil cuando necesitamos recorrer una colección y excluir temporalmente aquellos elementos que no cumplen determinados requisitos. Por ejemplo, ignorar registros inactivos, omitir productos sin existencias o descartar datos que no cumplen con una validación.

**Ejemplo: procesar usuarios mayores de edad**

```TypeScript
const edades: number[] = [16, 22, 17, 30];

for (const edad of edades) {
    if (edad < 18) {
        continue;
    }

    console.log(`Usuario habilitado: ${edad}`);
}
```

El bucle recorre cada una de las edades y comprueba si su valor es inferior a 18.

Cuando encuentra una persona menor de edad, ejecuta `continue`, omitiendo las instrucciones restantes de esa iteración y pasando directamente al siguiente elemento.

El resultado será:

```
Usuario habilitado: 22
Usuario habilitado: 30
```

A diferencia de `break`, que habría terminado por completo el bucle al encontrar la primera edad no permitida, `continue` permite seguir procesando los demás elementos.