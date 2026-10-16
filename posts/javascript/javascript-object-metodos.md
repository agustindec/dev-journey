# Métodos importantes en Objetos

Los métodos `Object.keys()`, `Object.values()`, `Object.entries()`, `Object.fromEntries()` y `Object.assign()` permiten trabajar con las propiedades de los objetos en JavaScript.

## 1. Object.keys()

El método `Object.keys()` permite obtener los nombres de las propiedades de un objeto. Recibe un objeto como argumento y devuelve un array que contiene sus claves en forma de cadenas de texto (`string`). Es importante entender que este método únicamente devuelve los nombres de las propiedades, no sus valores.

Se utiliza principalmente cuando necesitamos conocer qué propiedades contiene un objeto, recorrerlas o realizar operaciones basadas en ellas. Por ejemplo, en una aplicación podemos utilizarlo para identificar qué campos de un formulario contienen errores, comprobar si un objeto tiene propiedades o generar dinámicamente una lista de campos.

Este método solamente considera las **propiedades propias y enumerables del objeto cuya claves son string**, por lo que no incluye propiedades heredadas ni claves de tipo `Symbol`.

**Ejemplo**

```TypeScript
interface ErroresFormulario {
    nombre?: string;
    email?: string;
    password?: string;
}

const errores: ErroresFormulario = {
    email: "El correo electrónico no es válido",
    password: "La contraseña debe tener al menos 8 caracteres"
};

const camposConErrores = Object.keys(errores);

console.log(camposConErrores); // ["email", "password"]
```

En este ejemplo, `Object.keys()` nos permite identificar cuáles son los campos que presentan errores, sin necesidad de conocerlos previamente.

Esto resulta especialmente útil cuando necesitamos recorrer los campos inválidos para mostrar mensajes o aplicar estilos visuales.

**Importante**: En TypeScript, `Object.keys()` devuelve un `string[]`, incluso cuando las propiedades del objeto están definidas mediante una interfaz.

## 2. Object.values()

El método `Object.values()` permite obtener los valores de las propiedades de un objeto.
A diferencia de `Object.keys()`, que devuelve los nombres de las propiedades, este método devuelve un array compuesto exclusivamente por sus valores, sin incluir las claves a las que pertenecen.

Es especialmente útil cuando necesitamos procesar la información almacenada en un objeto sin importar el nombre de cada propiedad. Por ejemplo, podemos utilizarlo para calcular el total de productos disponibles en un inventario, sumar los importes de distintas categorias, obtener estadisticas o verificar si determinados valores cumplen alguna condición.

Al igual que `Object.keys()`, únicamente considera las propiedades propias y enumerables del objeto que tienen claves de tipo `string`.

**Ejemplo**

```TypeScript
const inventario: Record<string, number> = {
    teclados: 10,
    mouse: 5,
    monitores: 8
};

const cantidad = Object.values(invetario);

console.log(cantidad); // [10, 5, 8]
```

Ahora que tenemos los valores en un array, podemos utilizar métodos como `reduce()` para calcular el total.

```TypeScript
const totalProductos = cantidades.reduce(
    (total, cantidad) => total + cantidad, 0
);

console.log(totalProductos); // 23
```

De esta manera, obtenemos la cantidad total de unidades disponibles sin tener que acceder individualmente a cada propiedad.

**Concepto adicional**: `Record<string, number>` es un tipo de TypeScript que representa un objeto cuyas claves son cadenas de texto y cuyos valores son números.

## 3. Object.entries()

El método `Object.entries()` permite obtener tanto las claves como los valores de un objeto de manera conjunta. Para ello, transforma las propiedades propias y enumerables con claves de tipo `string` en un array de pares, donde cada par contiene dos elementos: el nombre de la propiedad y su valor. Su estructura es `[[clave, valor], [clave, valor]]`.

Este método resulta especialmente útil cuando necesitamos recorrer un objeto y trabajar simultáneamente con el nombre de cada propiedad y su información. Por ejemplo, en un sistema de inventario podemos utilizarlo para identificar productos agotados, generar reportes de existencias o mostrar una lista de productos junto con sus precios.

Una de sus principales ventajas es que permite utilizar métodos de arrays, como  `map()`, `filter()` y `forEach()`, para procesar los datos de un objeto de manera sencilla.

**Ejemplo**

```TypeScript
const invetario: Record<string, number> = {
    teclado: 10,
    mouse: 0,
    monitor: 5,
    auriculares: 0
};

const productos = Object.entries(inventario);

console.log(productos);
```

Resultado:

```TypeScript
[
    ["teclado", 10],
    ["mouse", 0],
    ["monitor", 5],
    ["auriculares", 0]
]
```

Cada elemento del array contiene el nombre del producto y su cantidad disponible.

Ahora podemos recorrerlo para identificar los productos agotados.

```TypeScript
const productosAgotados = Object.entries(inventario)
    .filter(([nombre, cantidad]) => cantidad === 0)
    .map(([nombre]) => nombre);

console.log(productosAgotados); // ["mouse", "auriculares"]
```

1. `Object.entries()` transforma el objeto en un array de pares `[clave, valor]`.
2. `filter()` conserva únicamente los productos cuya cantidad es igual a cero.
3. `map()` obtiene solamente los nombres de esos productos.

La sintaxis `[nombre, cantidad]` corresponde a la **desestructuración de arrays**.

## 4. Object.fromEntries()

El método `Object.fromEntries()` permite construir un objeto a partir de una colección de pares clave-valor. Cada par contiene dos elementos: el primero representa el nombre de la propiedad y el segundo representa el valor que tendrá esa propiedad en el nuevo objeto.
Es, en cierta medida, la operación inversa de `Object.entries()`, ya que transforma pares de datos en un objeto.

Se utiliza principalmente cuando necesitamos construir objetos dinámicamente o transformar sus propiedades. Por ejemplo, podemos utilizarlo para aplicar descuentos a los precios de un catálogo, convertir datos recibidos como pares clave-valor en un objeto o generar una nueva configuración a partir de información existente.

Una característica importante es que `Object.fromEntries()` **siempre crea un objeto nuevo**, por lo que no modifica directamente el objeto original del cual pudieron obtenerse los datos.

**Ejemplo**

```TypeScript
const precios: Record<string, number> = {
    teclado: 1200,
    mouse: 500,
    monitor: 8000
};
```

Podemos utilizar `Object.entries()` para obtener los productos junto con sus precios, aplicar el descuento mediante `map()` y finalmente convertir el resultado nuevamente en un objeto con `Object.fromEntries()`.

```TypeScript
const preciosConDescuentos: Record<string, number> = 
    Object.fromEntries(
        Object.entries(precios).map(([producto, precio]) => [
            producto,
            precio * 0.9
        ])
    );

console.log(preciosConDescuento);
```

Resultado:

```TypeScript
{
    teclado: 1080,
    mouse: 450,
    monitor: 7200
}
```

El proceso ocurre en tres etapas:

1. `Object.entries(precios)` convierte el objeto original en pares de productos y precios.
2. `map()` recorre esos pares y calcula los nuevos precios aplicando el descuento.
3. `Object.fromEntries()` convierte los pares modificados en un nuevo objeto.

De esta manera, podemos transformar todos los valores de un objeto y conservar sus claves originales.

Además, como se construye un objeto nuevo, el objeto `precios` mantiene sus valores originales.

## 5. Object.assign()

El método `Object.assign()` permite copiar las propiedades de uno o varios objetos hacia un objeto de destino. Recibe como primer argumento el objeto que será modificado y, a continuación, uno o más objetos de origen cuyas propiedades serán copiadas. Si existen propiedades con el mismo nombre, los valores de los últimos objetos sobrescriben los anteriores.

Este método se utiliza principalmente para combinar objetos, actualizar configuraciones o copiar propiedades sin necesidad de asignarlas individualmente. Por ejemplo, podemos definir una configuración predeterminada para nuestra aplicación y posteriormente combinarla con las preferencias de un usuario. A diferencia de `Object.fromEntries()`, `Object.assign()` modifica el objeto de destino y devuelve ese mismo objeto.

Es importante comprender que realiza una copia superficial (shallow copy). Esto significa que copia los valores de las propiedades, pero, si alguna contiene un objeto o array, no crea una copia independiente de ese objeto o array, sino que conserva su referencia.
También copia propiedades propias y enumerables cuyas clave sean strings o símbolos.

**Ejemplo**

```TypeScript
interface Configuracion {
    tema: string;
    idioma: string;
    notificaciones: boolean;
}

const configuracionDefault: Configuracion = {
    tema: "claro",
    idioma: "es",
    notificaciones: true
};
```

Ahora supongamos que un usuario decidió utilizar el tema oscuro y desactivar las notificaciones.

```TypeScript
const preferenciasUsuario: Partial<Configuracion> = {
    tema: "oscuro",
    notificaciones: false
};
```

Podemos combinar ambas configuraciones utilizando `Object.assign()`.

```TypeScript
const configuracionFinal: Configuracion = Object.assign(
    {},
    configurationDefault,
    preferenciasUsuario
);

console.log(configuracionFinal);
```

Resultado:

```TypeScript
{
    tema: "oscuro",
    idioma: "es",
    notificaciones: false
}
```

En este ejemplo, `Object.assign()` comienza con un objeto vacío `{}` y copia sobre él las propiedades de `configuracionDefault`. Posteriormente, incorpora las propiedades de `preferenciasUsuario`, sobrescribiendo los valores que coinciden.

Como utilizamos `{}` como destino, evitamos modificar el objeto `configuracionDefault`.

**Concepto adicional**: `Partial<Configuracion>` es un tipo utilitario de TypeScript que convierte todas las propiedades de `Configuracion` en opcionales. Esto permite que el usuario modifique solamente algunas preferencias sin necesidad de proporcionar la configuración completa.


