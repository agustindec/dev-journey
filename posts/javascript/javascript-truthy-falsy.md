# Truthy y Falsy

En JavaScript, una expresión no necesita ser literalmente `true` o `false` para poder utilizarse dentro de una aplicación. El lenguaje puede convertirse automáticamente prácticamente cualquier valor a un booleano cuando necesita decidir si una condición se cumple.

De ahí aparecen los conceptos de **truthy** y **falsy**.

Un valor **truthy** es un valor que en JavaScript interpreta como `true` cuando se evalúa en un contexto booleano. Un valor **falsy** es uno que se interpreta como `false`.

Por ejemplo:

```JavaScript
const name = "Agustin";

if (name) {
  console.log("Existe un nombre");
}
```

`name` no contiene `true`. Contiene un `string`. Sin embargo, `"Agustin"` es un valor `truthy`, por lo que la condición se cumple.

Esto es equivalente conceptualmente a:

```JavaScript
if (Boolean(name)){
  console.log("Existe un nombre");
}
```

## Valores falsy

Los valores falsy más importantes son:

```JavaScript
false
0
""
null
undefined
NaN
```

Cuando cualquiera de ellos aparece dentro de una condición, JavaScript lo interpreta como `false`.

```JavaScript
if (0) {
  console.log("Esto no se ejecuta");
}

if ("") {
  console.log("Esto no se ejecuta");
}

if (null) {
  console.log("Esto no se ejecuta");
}
```

En cambio, la mayoría de los demás valores son truthy:

```JavaScript
if (10) {
  console.log("Esto se ejecuta");
}

if ("Hello") {
  console.log("Esto se ejecuta");
}

if (-5) {
  console.log("Esto se ejecuta");
}
```

Una regla práctica bastante útil es: **si el valor no pertenece al pequeño grupo de valores falsy, normalmente será truthy**.

## ¿Para qué sirve?

Principalmente permite escribir condiciones más simples.

En lugar de:

```JavaScript
const username = "Agustin";

if (username !== null && username !== undefined && username !== ""){
  console.log(username);
}
```

Puedes escribir:

```JavaScript
if (username) {
  console.log(username);
}
```

Esto aparece constantemente al validar datos opcionales:

```JavaScript
function printEmail(email){
  if (email) {
    console.log(email);
  }
}
```

Si `email` es `undefined`, `null` o `""`, no entra en la condición.