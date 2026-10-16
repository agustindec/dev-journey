# Operadores

Los operadores son símbolos que permiten realizar operaciones sobre valores. Algunos sirven para hacer cálculos, otros para comparar datos, combinar condiciones, asignar valores o acceder de forma segura a propiedades que podrían no existir.

JavaScript tiene algunas particularidades importantes. La más relevantes para Backend son las conversión implícita de tipos, la diferencia entre `==` y `===`, y operadores modernos como `?.` y `??`.

## 1. Operadores Aritméticos

Los operadores aritméticos realizan operaciones matemáticas sobre valores numéricos.  
Los principales son:

```JavaScript
const a = 10;
const b = 3;

const suma = a + b;           // 13
const resta = a - b;          // 13
const multiplicacion = a * b; // 13
const division = a / b;       // 13
const resto = a % b;          // 13
const potencia = a ** b;      // 13
```

También existen los operadores de incremento y decremento:

```JavaScript
let contador = 0;

contador++;
contador--;

console.log(contador);
```

Son equivalente a:

```JavaScript
contador = contador + 1;
contador = contador - 1;
```

Existen diferencias entre `contador++` y `++contador` cuando el resultado de la expresión se utiliza inmediatamente.

```JavaScript
let contador = 5;

const a = contador++;
```

Aquí `a` recibe 5 y después `contador` pasa a valer `6`.

```JavaScript
let contador = 5;

const a = ++contador;
```

Ahora primero se incrementa `contador`, por lo que ambos terminan valiendo `6`.

## 2. Operadores de asignación

El operador básico de asignación es `=`.

```JavaScript
let edad = 27;
```

No significa "igual a", sino "asigna el valor de la derecha a la variable de la izquierda".

También existen operadores que combinan una operación con una asignación.

```JavaScript
let total = 10;

total += 5;
```

Es equivalente a:

```JavaScript
total = total + 5;
```

Lo mismo ocurre con:

```JavaScript
total -= 5;
total *= 2;
total /= 2;
total %= 3;
```

Por ejemplo:

```JavaScript
let total = 100;

total += 50;
total -= 20;

console.log(total); // 130
```

Son particularmente comunes en contadores y acumuladores.

```JavaScript
let totalVentas = 0;

totalVentas += 150;
totalVentas += 200;
totalVentas += 75;
```

JavaScript moderno incorpora además operadores de asignación relacionados con valores nulos y condiciones, aunque no son imprescindibles para empezar. Uno especialmente útil es `??=`:

```JavaScript
let nombre;

nombre ??= "Desconocido";

console.log(nombre);
```

Esto significa aproximadamente:

```JavaScript

if(nombre === null || nombre === undefined){
  nombre = "Desconocido";
}
```
## 3. Operadores relacionales

Los operadores relacionales comparan dos valores y producen siempre un `boolean`.

```JavaScript
const edad = 27;

console.log(edad > 18); // true
console.log(edad < 18); // false
console.log(edad >= 18); // true
console.log(edad <= 18); // true
```
Los operadores básicos son:

```
>
<
>=
<=
```

Son muy utilizados en validaciones:

```JavaScript
const stock = 5;

if (stock > 0){
  console.log("Producto disponible");
}
```

En TypeScript podrías encontrar algo como:

```TypeScript
function puedoComprar(stock: number, cantidad: number): boolean {
  return cantidad > 0 && cantidad <= stock;
}
```

Esto ya combina operadores relacionales y operadores lógicos.

## 4. Igualdad estricta `===`

Uno de los hábitos más importantes al trabajar profesionalmente con JavaScript es utilizar generalmente `===` para comparar valores.

```JavaScript
const edad = 20;

console.log(edad === 20); // true
```

`===` comprueba dos cosas:

1. que los valores sean iguales;
2. que sus tipos también sean iguales.

Por ejemplo:

```JavaScript
console.log(10 === 10);   // true
console.log(10 === "10"); // false
```

El segundo resultado es `false` porque tenemos:

```
10    -> number
"10"  -> string
```

Aunque visualmente representen algo parecido, son valores de diferente tipo.

En código Backend esto es especialmente importante porque una gran cantidad de datos externos llegan originalmente como texto.

Por ejemplo, un parámetro HTTP podría conceptualmente llegar como:

```JavaScript
const id = "10";
```

Entonces:

```JavaScript
id === 10;
```

Produce: `false`.

Lo correcto normalmente sería convertir explícitamente el valor.

```JavaScript
const id = Number("10");

console.log(id === 10); // true
```

Esto hace que la intención sea clara: quieres trabajar con un número.

## 5. Desigualdad estricta `!==`

`!==` es simplemente el equivalente negativo de `===`.

```JavaScript
const status = "ACTIVE";

if (status !== "INACTIVE"){
  console.log("El usuario no está inactivo");
}
```

También compara tanto el valor como tipo.

```JavaScript
console.log(10 !== "10"); // true
```

Porque `number` y `string` son tipos diferentes.

## 6. Diferencia entre `==` y `===`

El operador `==` realiza una comparación con conversión implícita de tipos.

Por ejemplo:

```JavaScript
console.log(10 == "10");
```

Produce: `true`.

JavaScript detecta que está comparando un `number` con un `string` e intenta convertir los valores para poder compararlos.

Conceptualmente sucede algo parecido a:

```
10 == Number("10")
```

A lo contrario que `===`, este no hace conversión y compara el tipo de datos también.

Existen casos confusos:

```JavaScript
console.log(0 == false);  // true
console.log("" == false); // true
```

Este comportamiento de `==` puede introducir bugs difíciles de detectar.

Por ese motivo, como regla profesional:

```JavaScript
valor === otroValor
valor !== otroValor
```

## 7. Operadores lógicos

Los tres operadores lógicos fundamentales son:

```
&& AND
|| OR
!  NOT
```

Se utilizan principalmente para combinar condiciones.

**AND**: `&&`

`&&` significa que ambas condiciones deben cumplirse.

```JavaScript
const edad = 27;
const activo = true;

if (edad >= 18 && activo){
  console.log("Usuario habilitado");
}
```

La expresión solamente será verdadera si:

```
edad >= 18
```

y:

```
activo
```

son verdaderas.

**OR**: `||`

`||` significa que al menos una condición debe cumplirse.

```JavaScript
const role = "ADMIN";

if (role === "ADMIN" || role === "MODERATOR"){
  console.log("Tiene permisos");
}
```

Si cualquiera de las dos comparaciones es verdadera, toda la expresión será verdadera.

**NOT**: `!`

`!` niega un valor booleano

```JavaScript
const activo = true;

console.log(!activo); // false
```

Es habitual encontrar:

```JavaScript
if (!activo) {
  console.log("Usuario deshabilitado");
}
```

En lugar de:

```JavaScript
if (activo === false) {
  
}
```

Ambas funcionan, pero la primera suele resultar más natural.

## 8. Truthy y falsy

JavaScript convierte muchos valores automáticamente a booleanos.

Por ejemplo:

```JavaScript
const nombre = "Agustin";

if (nombre) {
  console.log("Hay nombre");
}
```

Esto funciona porque `"Agustin"` es considerado un valor `truthy`.

Algunos valores se consideran `"falsy"`, principalmente:

```JavaScript
false
0
""
null
undefined
NaN
```

Por ejemplo:

```JavaScript
const nombre = "";

if (!nombre) {
  console.log("Nombre vacío");
}
```

Este comportamiento es útil, pero hay que entenderlo porque afecta especialmente a `||` y `??`.

## 9. Short-circuit evaluation

Los operadores `&&` y `||` no siempre evalúan ambos lados.

En:

```JavaScript
condicionA && condicionB
```

Si `condicionA` ya es falsa, JavaScript ni siquiera necesita evaluar `condicionB`.

Por ejemplo:

```JavaScript
const user = null;

if (user && user.active){
}
```

Como `user` es `null`, la segunda parte:

```JavaScript
user.active
```

No se ejecuta.

## 10. El operador `||` y los valores por defecto

Una técnica clásica en JavaScript consiste en utilizar `||` para proporcionar un valor alternativo.

```JavaScript
const nombre = input || "Desconocido";
```

Si `input` es falsy, se usa `"Desconocido"`.

El problema es precisamente que `||` considera falsy valores que podrían ser perfectamente válidos.

Por ejemplo:

```JavaScript
const cantidad = 0;

const resultado = cantidad || 10;

console.log(resultado); // 10
```

Pero tal vez `0` era un valor completamente válido.

Este problema es una de las razones por las que existe `??`.

## 11. Operador ternario

El operador ternario permite elegir entre dos valores dependiendo de una condición.

Su estructura es:

```JavaScript
condicion ? valorSiTrue : valorSiFalse
```

Por ejemplo:

```JavaScript
const edad = 20;

const estado = edad >= 18 ? "Adulto" : "Menor";
```

Sería conceptualmente equivalente a:

```JavaScript
let estado;

if (edad >= 18) {
  estado = "Adulto";
} else {
  estado = "Menor";
}
```

El ternario es especialmente útil cuando necesitas obtener un valor dependiendo de una condición.

Por ejemplo:

```JavaScript
const role = isAdmin ? "ADMIN" : "USER";
```

El error habitual consiste en intentar meter demasiada lógica dentro del ternario.

Esto todavía es razonable:

```JavaScript
const message = active ? "Activo" : "Inactivo";
```

Esto ya empieza a perjudicar la lectura:

```JavaScript
const value = active
  ? age > 18
    ? "A"
    : "B"
  : condition
    ? "C"
    : "D";
```

Cuando aparecen varios ternarios anidados suele ser mejor utilizar `if`.

## 12. Optional chaining `?.`

Optional chaining es una de las características modernas más útiles de JavaScript y TypeScript.

El problema que resuelve aparece cuando quieres acceder a una propiedad de algo que podría ser `null` o `undefined`.

Ejemplo:

```JavaScript
const user = {
  name: "Agustin"
};
```

Si intentamos:

```JavaScript`
console.log(user.address.city);
```

JavaScript lanzaría un error porque:

```JavaScript
user.address
```

es `undefined`.

Entonces terminaríamos intentando hacer:

```JavaScript
undefined.city
```

Lo cual no es válido.

Con optional chaining podemos escribir:

```JavaScript
const city = user.address?.city;
```

Si `address` existe, accede a `city`.

Si `address` es `null` o `undefined`, devuelve: `undefined`

Sin lanzar una excepción.

También se puede encadenar:

```JavaScript
const country = user?.address?.country?.name;
```

Esto es extremadamente común trabajando con DTOs, APIs, configuraciones y estructuras anidadas.

En TypeScript podríamos tener:

```TypeScript
interface Address {
  city: string;
}

interface User {
  name: string;
  address?: Address;
}
```

Ahora TypeScript sabe que:

```TypeScript
user.address
```

podría no existir.

Por eso:

```TypeScript
const city = user.address?.city;
```

es una solución natural.

## 13. Optional chaining en métodos

También se puede utilizar para ejecutar un método solamente si existe.

```JavaScript
logger?.log("Proceso terminado");
```

También:

```JavaScript
callback?.();
```

Esto es especialmente útil con callbacks opcionales.

En TypeScript:

```TypeScript
function process(callback?: () => void): void {
  callback?.();
}
```

## 14. Nullish coalescing `??`

`??` sirve para proporcionar un valor alternativo cuando un valor es específicamente:

```JavaScript
const nombre = undefined;

const resultado = nombre ?? "Desconocido";
```

El resultado será: `"Desconocido"`

También:

```JavaScript
const nombre = null;

const resultado = nombre ?? "Desconocido";
```

produce lo mismo.

Pero aquí está la diferencia fundamental respecto a `||`.

Supongamos:

```JavaScript
const intentos = 0;
```

Con `||`:

```JavaScript
const resultado = intentos || 3;

console.log(resultado); // 3
```

JavaScript interpreta `0` como falsy.

Pero con:

```JavaScript
const resultado = intentos ?? 3;

console.log(resultado); // 0
```

se conserva el `0`.

La regla práctica es:

```
|| -> dame otro valor si esto es falsy

?? -> dame otro valor solamente si esto no existe realmente (null o undefined)
```

## 15. Combinando `?.` y `??`

Estos dos operadores aparecen constantemente juntos.

Supongamos:

```TypeScript
interface User {
  profile?: {
    displayName?: string;
  };
}
```

Podemos hacer:

```TypeScript
const displayName =
  user.profile?.displayName ?? "Usuario";
```

El flujo es sencillo.

Primero:

```TypeScript
user.profile?.displayName;
```

intenta obtener el nombre de forma segura.

Si el resultado es: `null`

o: `undefined`

entonces:

```TypeScript
?? "Usuario"
```

proporciona el valor alternativo.

Esto permite escribir código bastante expresivo:

```TypeScript
const city = customer.address?.city ?? "Sin Ciudad";
```




