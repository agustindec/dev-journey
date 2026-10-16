# Destructuring de Objetos

La **desestructuración de objetos (Object Destructuring)** es una característica de JavaScript que permite extraer propiedades de un objeto y almacenarlas directamente en variables. Es una técnica muy utilizada en el desarrollo moderno porque simplifica el acceso a los datos y permitir escribir código más limpio y legible.

La sintaxis de desestructuración es exactamente la misma en JavaScript y TypeScript. La diferencia es que TypeScript incorpora un sistema de tipos que permite verificar que las propiedades que intentamos extraer existen y que los valores obtenidos corresponden a los tipos esperados.

## 1. Object Destructuring

Cuando trabajamos con objetos, normalmente accedemos a sus propiedades utilizando la notación de punto (`objeto.propiedad`). Sin embargo, cuando necesitamos utilizar varias propiedades de un mismo objeto, repetir continuamente su nombre puede resultar innecesario. La desestructuración permite extraer esas propiedades mediante una única declaración, creando variables independientes que contienen sus valores.

Para realizar una desestructuración se utilizan llaves `{}` a la izquierda de una asignación, indicando los nombres de las propiedades que queremos extraer. JavaScript busca esas propiedades dentro del objeto y asigna sus valores a las variables correspondientes. **Es importante comprender que la desestructuración no modifica el objeto original**, simplemente obtiene los valores de sus propiedades.

**Ejemplo práctico**

```TypeScript
interface Cliente {
  nombre: string;
  email: string;
  edad: number;
}

const cliente: Cliente = {
  nombre: "Agustín",
  email: "agustin@gmail.com",
  edad: 27
};
```

Sin desestructuración:

```TypeScript
const nombre = cliente.nombre;
const email = cliente.email;

console.log(nombre); // Agustín
console.log(email);  // agustin@gmail.com
```

Con desestructuración:

```TypeScript
const { nombre, email } = cliente;

console.log(nombre); // Agustín
console.log(email);  // agustin@gmail.com
```

En el segundo ejemplo, JavaScript identifica las propiedades nombre y email dentro del objeto cliente y crea automáticamente dos variables con esos nombres.

No es necesario extraer todas las propiedades. Podemos seleccionar únicamente aquellas que necesitamos, dejando las demás intactas.

## 2. Renombrar variables (Renaming Variables)

La desestructuración permite asignar nombres diferentes a las variables que se crean a partir de las propiedades de un objeto. Esta funcionalidad resulta especialmente útil cuando el nombre original de una propiedad es demasiado genérico, cuando queremos utilizar una denominación más descriptiva o cuando ya existe una variable con el mismo nombre dentro del ámbito en el que estamos trabajando.

Para renombrar una variable se utiliza la sintaxis propiedad: nuevoNombre dentro de las llaves de desestructuración. El nombre situado antes de los dos puntos identifica la propiedad que queremos obtener del objeto, mientras que el nombre posterior representa la variable que se creará. **Este procedimiento no cambia el nombre de la propiedad dentro del objeto original**, únicamente modifica el nombre de la variable que utilizaremos para acceder a su valor.

**Ejemplo práctico**

```TypeScript
interface Pedido {
  id: number;
  total: number;
}

const pedido: Pedido = {
  id: 150,
  total: 2500
};
```

Sin renombrar:

```TypeScript
const { id, total } = pedido;

console.log(id);    // 150
console.log(total); // 2500
```

Aunque este código funciona, la variable `id` podría resultar poco destrictiva si estamos trabajando simultáneamente con clientes, productos y pedidos.

Renombrando las variables:

```TypeScript
const {
  id: idPedido,
  total: totalPedido
} = pedido;

console.log(idPedido);    // 150
console.log(totalPedido); // 2500
```

Ahora tenemos variables cuyos nombres representan claramente la información que contienen.

Es importante comprender que:

```TypeScript
const { id: idPedido } = pedido;
```

No significa que `idPedido` sea una propiedad del objeto `pedido`.

Significa que estamos extrayendo la propiedad `id` y almacenando su valor en una nueva variable llamada `idPedido`.

```TypeScript
console.log(idPedido);    // 150
console.log(pedido.id);   // 150
```

Ambas expresiones permiten acceder al mismo valor.

## 3. Default Values (Valores por defecto)

Los valores por defecto permiten establecer un valor alternativo cuando una propiedad que intentamos extraer mediante desestructuración contiene `undefined` o no existe dentro del objeto. Esta funcionalidad resulta especialmente útil cuando trabajamos con propiedades opcionale, configuraciones de usuario o información recibida desde una API, donde determinados datos pueden no estar disponibles.

Para establecer un valor por defecto se utiliza el operador de asignación `=` después del nombre de la propiedad. Si la propiedad contiene un valor distinto de `undefined`, JavaScript conservará ese valor; en caso contrario, utilizará el definido en la desestructuración. **Es importante destacar que los valores por defecto no reemplazan valores como** `null`, `false`, `0` **o una cadena vacía (**`""`**)**, ya que estos no son equivalentes a `undefined`.

**Ejemplo práctico**

```TypeScript
interface Preferencias {
  idioma?: string;
  notificaciones?: boolean;
  tema?: string;
}

const preferencias: Preferencias = {
  idioma: "es",
  notificaciones: false
};
```

Observamos que las propiedades de la interfaz utilizan el símbolo `?`, indicando que son opcionales.

Esto significa que un objeto de tipo `Preferencias` puede no contener alguna de esas propiedades.

**Sin valores por defecto**:

```TypeScript
const {
  idioma = "es",
  notificaciones = true,
  tema = "claro"
} = preferencias;

console.log(idioma);          // es
console.log(notificaciones);  // false
console.log(tema);            // claro
```

* `idioma`: mantiene `"es"` porque la propiedad contiene un valor.
* `notificaciones`: mantiene `false` porque es un valor válido.
* `tema`: utiliza `"claro"` porque la propiedad no existe en el objeto.

Esto permite trabajar con configuraciones opcionales sin necesidad de comprobar manualmente cada propiedad.

**Una particularidad importante en TypeScript**

Los valores por defecto también influyen en los tipos que TypeScript infiere.

Por ejemplo:

```TypeScript
const {tema} = preferencias;
```

TypeScript interpreta que `tema` puede ser:

```TypeScript
string | undefined
```

Sin embargo:

```TypeScript
const { tema = "claro" } = preferencias;
```

TypeScript interpreta que `tema` es de tipo:

```TypeScript
string
```

## 4. Nested Destructuring (Desestructuración anidada)

En aplicaciones reales es habitual trabajar con objetos que contienen otros objetos en su interior. Por ejemplo, un pedido puede contener información del cliente, y ese cliente puede tener un objeto que representa su dirección. La desestructuración anidada permite acceder directametne a las propiedades de esos objetos internos sin necesidad de realizar múltiples asignaciones independientes.

Para utilizarla se combinan distintos niveles de llaves `{}`, siguiendo la estructura del objeto original. Cada nivel representa el acceso a un objeto interno y permite seleccionar las propiedades que queremos extraer.
**Un aspecto importante es que las propiedades utilizadas como rutas de acceso no se convierten automáticamente en variables**. Solamente se crean variables para aquellas propiedades que extraemos explícitamente. Además, si algún objeto intermedio es `null` o `undefined`, intentar desestructurarlo provocará un error en tiempo de ejecución.

**Ejemplo práctico**

```TypeScript
interface Direccion {
  calle: string;
  ciudad: string;
}

interface Cliente {
  nombre: string;
  direccion: Direccion;
}

interface Compra {
  numero: number;
  cliente: Cliente;
}

const compra: Compra = {
  numero: 150,
  cliente: {
    nombre: "Agustín",
    direccion: {
      calle: "Av. Italia",
      ciudad: "Montevideo"
    }
  }
};
```

**Sin desestructuración**:

```TypeScript
const nombre = compra.cliente.nombre;
const ciudad = compra.cliente.direccion.ciudad;

console.log(nombre); // Agustín
console.log(ciudad); // Montevideo
```

**Con desestructuración anidada**:

```TypeScript
const {
  cliente: {
    nombre,
    direccion: {
      ciudad
    }
  }
} = compra;

console.log(nombre); // Agustín
console.log(ciudad); // Montevideo
```