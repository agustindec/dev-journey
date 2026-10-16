# 🧑‍💻 JavaScript / TypeScript Backend Roadmap

> Base recomendada: **JavaScript ES6 / ES2015 + JavaScript moderno hasta ES2026**  
> TypeScript: **TypeScript moderno**  
> Enfoque: **Backend profesional**

---

# 1. JavaScript — Fundamentos

## 1.1 Variables y tipos

- [ ] `let`
- [ ] `const`
- [ ] Entender por qué evitar `var`
- [ ] `string`
- [ ] `number`
- [ ] `boolean`
- [ ] `bigint`
- [ ] `symbol`
- [ ] `undefined`
- [ ] `null`
- [ ] Objetos
- [ ] Arrays
- [ ] `typeof`

## 1.2 Operadores

- [ ] Operadores aritméticos
- [ ] Operadores de asignación
- [ ] Operadores lógicos
- [ ] Operadores relacionales
- [ ] `===`
- [ ] `!==`
- [ ] Diferencia entre `==` y `===`
- [ ] Operador ternario
- [ ] Optional chaining `?.`
- [ ] Nullish coalescing `??`

## 1.3 Truthy y Falsy

- [ ] Qué significa truthy
- [ ] Qué significa falsy
- [ ] `false`
- [ ] `0`
- [ ] `""`
- [ ] `null`
- [ ] `undefined`
- [ ] `NaN`

## 1.4 Control de flujo

- [ ] `if`
- [ ] `else`
- [ ] `else if`
- [ ] `switch`
- [ ] `for`
- [ ] `for...of`
- [ ] `while`
- [ ] `do...while`
- [ ] `break`
- [ ] `continue`

---

# 2. Funciones

## 2.1 Fundamentos

- [ ] Function declaration
- [ ] Function expression
- [ ] Arrow functions
- [ ] Parámetros
- [ ] Parámetros opcionales conceptualmente
- [ ] Default parameters
- [ ] Return values

## 2.2 Funciones como ciudadanos de primera clase

- [ ] Guardar funciones en variables
- [ ] Pasar funciones como argumentos
- [ ] Retornar funciones
- [ ] Callbacks
- [ ] Higher-order functions

## 2.3 Rest y Spread

- [ ] Rest parameters `...args`
- [ ] Spread en arrays
- [ ] Spread en objetos
- [ ] Diferencia entre Rest y Spread

## 2.4 Closures

- [ ] Closures
- [ ] Casos reales de closures

---

# 3. Objetos

## 3.1 Fundamentos

- [ ] Object literals
- [ ] Acceso con `.`
- [ ] Acceso con `[]`
- [ ] Propiedades
- [ ] Métodos
- [ ] Computed properties

## 3.2 Destructuring

- [ ] Object destructuring
- [ ] Renombrar variables
- [ ] Default values
- [ ] Nested destructuring

## 3.3 Métodos importantes

- [ ] `Object.keys()`
- [ ] `Object.values()`
- [ ] `Object.entries()`
- [ ] `Object.fromEntries()`
- [ ] `Object.assign()`

## 3.4 Mutabilidad

- [ ] Referencias a objetos
- [ ] Shallow copy
- [ ] Spread copy
- [ ] Diferencia entre shallow y deep copy
- [ ] Inmutabilidad como concepto

---

# 4. Arrays

## 4.1 Fundamentos

- [ ] Crear arrays
- [ ] Acceder por índice
- [ ] Modificar elementos
- [ ] `length`
- [ ] Iterar arrays

## 4.2 Métodos principales

- [ ] `push()`
- [ ] `pop()`
- [ ] `shift()`
- [ ] `unshift()`
- [ ] `slice()`
- [ ] `splice()`

## 4.3 Métodos funcionales

- [ ] `map()`
- [ ] `filter()`
- [ ] `find()`
- [ ] `findIndex()`
- [ ] `some()`
- [ ] `every()`
- [ ] `reduce()`
- [ ] `sort()`
- [ ] `includes()`
- [ ] `flat()`
- [ ] `flatMap()`

## 4.4 Destructuring de arrays

- [ ] Array destructuring
- [ ] Rest en arrays
- [ ] Swap de variables

---

# 5. Cómo funciona JavaScript

## 5.1 Runtime

- [ ] Execution Context
- [ ] Global Execution Context
- [ ] Function Execution Context
- [ ] Call Stack

## 5.2 Scope

- [ ] Lexical Environment
- [ ] Scope Chain
- [ ] Block Scope
- [ ] Function Scope

## 5.3 Hoisting

- [ ] Hoisting de funciones
- [ ] Hoisting de `var`
- [ ] `let` y `const`
- [ ] Temporal Dead Zone

## 5.4 Memoria

- [ ] Stack vs Heap conceptualmente
- [ ] Valores primitivos
- [ ] Referencias
- [ ] Garbage Collection conceptualmente

---

# 6. `this`

- [ ] Qué representa `this`
- [ ] `this` en funciones normales
- [ ] `this` en métodos
- [ ] `this` en arrow functions
- [ ] `bind()`
- [ ] `call()`
- [ ] `apply()`
- [ ] Errores comunes con `this`

---

# 7. Prototypes y clases

## 7.1 Prototype system

- [ ] Qué es un prototype
- [ ] Prototype chain
- [ ] Herencia prototípica
- [ ] `Object.getPrototypeOf()`
- [ ] Entender que `class` es una abstracción sobre prototypes

## 7.2 Classes

- [ ] `class`
- [ ] `constructor`
- [ ] Métodos
- [ ] `extends`
- [ ] `super`
- [ ] Métodos `static`
- [ ] Private fields `#`
- [ ] Getters
- [ ] Setters

---

# 8. Manejo de errores

- [ ] `Error`
- [ ] `throw`
- [ ] `try`
- [ ] `catch`
- [ ] `finally`
- [ ] Custom Errors
- [ ] Propagación de errores
- [ ] `Error.cause`
- [ ] Errores síncronos
- [ ] Errores asíncronos

---

# 9. JavaScript asíncrono

## 9.1 Callbacks

- [ ] Qué es un callback
- [ ] Callbacks síncronos
- [ ] Callbacks asíncronos
- [ ] Callback hell conceptualmente

## 9.2 Promises

- [ ] Qué es una Promise
- [ ] `pending`
- [ ] `fulfilled`
- [ ] `rejected`
- [ ] `.then()`
- [ ] `.catch()`
- [ ] `.finally()`
- [ ] Encadenamiento de Promises

## 9.3 Async / Await

- [ ] `async`
- [ ] `await`
- [ ] Manejo de errores con `try/catch`
- [ ] Operaciones secuenciales
- [ ] Operaciones concurrentes

## 9.4 Promise utilities

- [ ] `Promise.all()`
- [ ] `Promise.allSettled()`
- [ ] `Promise.race()`
- [ ] `Promise.any()`

---

# 10. Event Loop

> Tema fundamental para Node.js.

- [ ] Call Stack
- [ ] Event Loop
- [ ] Task Queue
- [ ] Microtask Queue
- [ ] Macrotasks
- [ ] Microtasks
- [ ] Promises y microtasks
- [ ] `setTimeout`
- [ ] Orden de ejecución
- [ ] Qué significa bloquear el Event Loop
- [ ] I/O-bound
- [ ] CPU-bound
- [ ] Concurrencia vs paralelismo

---

# 11. Módulos

## 11.1 ES Modules

- [ ] `export`
- [ ] Named exports
- [ ] `export default`
- [ ] `import`
- [ ] Default imports
- [ ] Dynamic `import()`
- [ ] Top-level await

## 11.2 CommonJS

> Principalmente para poder leer proyectos legacy.

- [ ] `require()`
- [ ] `module.exports`
- [ ] `exports`
- [ ] Diferencias CommonJS vs ESM
- [ ] `"type": "module"` en `package.json`

---

# 12. Estructuras de datos

- [ ] Array
- [ ] Object
- [ ] Map
- [ ] Set
- [ ] WeakMap
- [ ] WeakSet
- [ ] Cuándo usar Object vs Map
- [ ] Cuándo usar Array vs Set

---

# 13. JavaScript moderno

> ES6/ES2015 como base + características importantes posteriores.

- [ ] Template literals
- [ ] Arrow functions
- [ ] Destructuring
- [ ] Rest
- [ ] Spread
- [ ] Classes
- [ ] Modules
- [ ] Promises
- [ ] Async/Await
- [ ] Optional chaining `?.`
- [ ] Nullish coalescing `??`
- [ ] Logical assignment operators
- [ ] Private class fields
- [ ] Dynamic imports
- [ ] Top-level await
- [ ] Iterators
- [ ] Generators
- [ ] `for await...of`

---

# 14. Iterators y Generators

> Prioridad media/baja, pero conviene comprenderlos.

- [ ] Iterator protocol
- [ ] Iterable protocol
- [ ] `Symbol.iterator`
- [ ] Generator functions
- [ ] `yield`
- [ ] Async iterators
- [ ] Casos de uso

---

# 15. Introducción a TypeScript

- [ ] Qué problema resuelve TypeScript
- [ ] TypeScript vs JavaScript
- [ ] TypeScript compila a JavaScript
- [ ] Instalar TypeScript
- [ ] `tsc`
- [ ] `tsconfig.json`
- [ ] Compilar `.ts` a `.js`
- [ ] Type inference
- [ ] Explicit typing
- [ ] Structural typing

---

# 16. Tipos fundamentales de TypeScript

- [ ] `string`
- [ ] `number`
- [ ] `boolean`
- [ ] Arrays
- [ ] Tuples
- [ ] Objects
- [ ] Literal types
- [ ] Union types
- [ ] Intersection types
- [ ] Enums
- [ ] `readonly`

---

# 17. Tipos especiales

- [ ] `any`
- [ ] Entender por qué evitar `any`
- [ ] `unknown`
- [ ] Diferencia `any` vs `unknown`
- [ ] `never`
- [ ] `void`
- [ ] `undefined`
- [ ] `null`

---

# 18. Type Aliases

- [ ] Crear tipos con `type`
- [ ] Object types
- [ ] Union types
- [ ] Intersection types
- [ ] Literal types
- [ ] Reutilización de tipos

Ejemplo conceptual:

```typescript
type PaymentStatus =
  | "PENDING"
  | "PARTIALLY_PAID"
  | "PAID"
  | "OVERDUE";
```

---

# 19. Interfaces

- [ ] Crear `interface`
- [ ] Propiedades
- [ ] Propiedades opcionales
- [ ] `readonly`
- [ ] Extender interfaces
- [ ] Interfaces para objetos
- [ ] Interfaces para clases
- [ ] Declaration merging
- [ ] `interface` vs `type`
- [ ] Cuándo usar cada uno

---

# 20. Funciones en TypeScript

- [ ] Tipado de parámetros
- [ ] Return types
- [ ] Optional parameters
- [ ] Default parameters
- [ ] Rest parameters
- [ ] Function types
- [ ] Call signatures
- [ ] Callbacks tipados
- [ ] Function overloads

---

# 21. Clases en TypeScript

- [ ] Classes
- [ ] Constructors
- [ ] `public`
- [ ] `private`
- [ ] `protected`
- [ ] `readonly`
- [ ] Parameter properties
- [ ] `static`
- [ ] Abstract classes
- [ ] `implements`
- [ ] `extends`
- [ ] Getters
- [ ] Setters

Ejemplo importante para NestJS:

```typescript
constructor(
  private readonly customerService: CustomerService
) {}
```

---

# 22. Generics

> Tema importante para TypeScript profesional.

- [ ] Generic functions
- [ ] Generic interfaces
- [ ] Generic classes
- [ ] Múltiples parámetros genéricos
- [ ] Generic constraints
- [ ] `extends`
- [ ] Generic defaults
- [ ] Generics con arrays
- [ ] Generics con Promises

Ejemplo:

```typescript
interface Page<T> {
  content: T[];
  totalElements: number;
}
```

---

# 23. Type Narrowing

> Una de las características más importantes de TypeScript.

- [ ] `typeof`
- [ ] `instanceof`
- [ ] `in`
- [ ] Equality narrowing
- [ ] Truthiness narrowing
- [ ] Control-flow analysis
- [ ] Type predicates
- [ ] User-defined type guards
- [ ] Discriminated unions

---

# 24. `keyof` y `typeof`

- [ ] `keyof`
- [ ] `typeof` aplicado a tipos
- [ ] `keyof typeof`
- [ ] Indexed access types

---

# 25. Utility Types

- [ ] `Partial<T>`
- [ ] `Required<T>`
- [ ] `Readonly<T>`
- [ ] `Pick<T>`
- [ ] `Omit<T>`
- [ ] `Record<K, T>`
- [ ] `Exclude<T, U>`
- [ ] `Extract<T, U>`
- [ ] `NonNullable<T>`
- [ ] `ReturnType<T>`
- [ ] `Parameters<T>`
- [ ] `Awaited<T>`

---

# 26. Advanced Type Manipulation

> Aprender a leerlos es más importante que inventar tipos extremadamente complejos.

- [ ] Conditional Types
- [ ] Mapped Types
- [ ] Indexed Access Types
- [ ] Template Literal Types
- [ ] `infer`
- [ ] Recursive types conceptualmente

---

# 27. Type Assertions

- [ ] `as`
- [ ] Casos válidos de type assertion
- [ ] Riesgos de abusar de `as`
- [ ] Non-null assertion `!`
- [ ] `satisfies`
- [ ] Preferir narrowing cuando sea posible

---

# 28. Decorators

> Importante antes de aprender NestJS.

- [ ] Qué es un Decorator
- [ ] Class decorators
- [ ] Method decorators
- [ ] Property decorators
- [ ] Parameter decorators
- [ ] Decorator factories
- [ ] Metadata conceptualmente
- [ ] Reflection conceptualmente

Ejemplos que luego aparecerán en NestJS:

```typescript
@Controller()
@Injectable()
@Get()
@Post()
@Body()
@Param()
```

---

# 29. TypeScript Config

## `tsconfig.json`

- [ ] `strict`
- [ ] `target`
- [ ] `module`
- [ ] `moduleResolution`
- [ ] `rootDir`
- [ ] `outDir`
- [ ] `sourceMap`
- [ ] `declaration`
- [ ] `types`
- [ ] `paths`
- [ ] `baseUrl`
- [ ] `noImplicitReturns`
- [ ] `noUncheckedIndexedAccess`
- [ ] `exactOptionalPropertyTypes`
- [ ] ESM
- [ ] NodeNext

---

# 30. Package Management

## npm

- [ ] `npm init`
- [ ] `package.json`
- [ ] `package-lock.json`
- [ ] `npm install`
- [ ] `npm uninstall`
- [ ] dependencies
- [ ] devDependencies
- [ ] peerDependencies
- [ ] npm scripts
- [ ] Semantic Versioning
- [ ] `^`
- [ ] `~`
- [ ] Versiones exactas
- [ ] `npm audit`

---

# 31. Tooling

- [ ] ESLint
- [ ] Prettier
- [ ] ESLint + TypeScript
- [ ] Ignorar archivos
- [ ] Source Maps
- [ ] Debugging
- [ ] VS Code debugging
- [ ] Environment variables
- [ ] `.env`
- [ ] `.gitignore`

---

# 32. Testing básico con TypeScript

> El testing profundo se puede estudiar junto con Node.js y NestJS.

- [ ] Qué es unit testing
- [ ] Arrange / Act / Assert
- [ ] Test cases
- [ ] Assertions
- [ ] Mocks
- [ ] Stubs
- [ ] Spies
- [ ] Testing de funciones
- [ ] Testing de Promises
- [ ] Testing de errores
- [ ] Vitest
- [ ] Coverage

---

# 33. Buenas prácticas de JavaScript / TypeScript

- [ ] Preferir `const`
- [ ] Usar `let` solamente cuando existe reasignación
- [ ] Evitar `var`
- [ ] Evitar `any`
- [ ] Preferir `unknown` cuando el tipo es desconocido
- [ ] Usar `===`
- [ ] Funciones pequeñas
- [ ] Nombres descriptivos
- [ ] Evitar mutación innecesaria
- [ ] No abusar de clases
- [ ] No abusar de herencia
- [ ] Preferir composición
- [ ] No abusar de type assertions
- [ ] Manejar Promises correctamente
- [ ] No ignorar Promise rejections
- [ ] Mantener TypeScript en `strict`
- [ ] Separar tipos de dominio de DTOs cuando corresponda

---

# 34. Temas especialmente importantes para Backend

Estos deberían quedar particularmente sólidos antes de entrar profundamente en Node.js.

- [ ] Objects
- [ ] Arrays
- [ ] `map`
- [ ] `filter`
- [ ] `reduce`
- [ ] Functions
- [ ] Closures
- [ ] Scope
- [ ] Promises
- [ ] `async/await`
- [ ] Event Loop
- [ ] Error handling
- [ ] ESM
- [ ] TypeScript strict
- [ ] Interfaces
- [ ] Type aliases
- [ ] Union types
- [ ] Generics
- [ ] Type narrowing
- [ ] Utility Types
- [ ] Decorators
- [ ] `tsconfig.json`

---

# 35. Proyecto práctico — JavaScript

Antes de pasar completamente a TypeScript:

## Sistema simple de pagos en memoria

- [ ] Crear clientes
- [ ] Crear cargos
- [ ] Registrar pagos
- [ ] Calcular deuda
- [ ] Filtrar cargos pendientes
- [ ] Calcular total cobrado
- [ ] Calcular total pendiente
- [ ] Manejar errores

Sin:

- [ ] Base de datos
- [ ] HTTP
- [ ] Framework

Objetivo: practicar JavaScript.

---

# 36. Proyecto práctico — TypeScript

Rehacer el proyecto anterior utilizando TypeScript.

Modelos:

```text
Customer
Charge
Payment
```

Implementar:

- [ ] Interfaces
- [ ] Type aliases
- [ ] Union types
- [ ] Classes cuando tenga sentido
- [ ] Generics
- [ ] Error types
- [ ] Repository interfaces
- [ ] Services
- [ ] Type guards
- [ ] Async functions
- [ ] Tests

Ejemplo de estructura:

```text
src/
├── customer/
├── charge/
├── payment/
├── shared/
└── main.ts
```

Todavía sin NestJS.

---

# 37. Nivel necesario antes de pasar a Node.js

Debería poder explicar sin consultar documentación:

- [ ] Diferencia entre `let`, `const` y `var`
- [ ] Diferencia entre `==` y `===`
- [ ] Diferencia entre `null` y `undefined`
- [ ] Qué es un closure
- [ ] Qué es lexical scope
- [ ] Cómo funciona `this`
- [ ] Qué es una Promise
- [ ] Qué hace `async/await`
- [ ] Diferencia entre ejecución secuencial y concurrente
- [ ] Qué hace `Promise.all`
- [ ] Qué es el Event Loop
- [ ] Diferencia entre microtask y macrotask
- [ ] Qué es ESM
- [ ] Diferencia ESM vs CommonJS
- [ ] Diferencia `interface` vs `type`
- [ ] Diferencia `any` vs `unknown`
- [ ] Qué es un union type
- [ ] Qué es narrowing
- [ ] Qué es un generic
- [ ] Para qué sirven Utility Types
- [ ] Qué hace TypeScript y qué ocurre cuando se ejecuta el programa
- [ ] Qué es `tsconfig.json`

---

# Orden recomendado

```text
JavaScript ES6+
      ↓
Funciones / Objetos / Arrays
      ↓
Scope / Closures / this
      ↓
Promises / Async Await
      ↓
Event Loop
      ↓
ES Modules
      ↓
TypeScript básico
      ↓
Interfaces / Types
      ↓
Generics
      ↓
Narrowing
      ↓
Utility Types
      ↓
Decorators
      ↓
TypeScript profesional
      ↓
Node.js
```

---

# Prioridades

## 🔴 CORE — Imprescindible

- [ ] JavaScript moderno
- [ ] Objects
- [ ] Arrays
- [ ] Functions
- [ ] Scope
- [ ] Closures
- [ ] Promises
- [ ] Async/Await
- [ ] Event Loop
- [ ] Error handling
- [ ] ESM
- [ ] TypeScript strict
- [ ] Interfaces
- [ ] Types
- [ ] Union Types
- [ ] Generics
- [ ] Narrowing
- [ ] Utility Types

## 🟡 PRO — Profesional

- [ ] Prototype system
- [ ] `this`
- [ ] Advanced generics
- [ ] Conditional Types
- [ ] Mapped Types
- [ ] Decorators
- [ ] Type guards
- [ ] Configuration avanzada
- [ ] ESLint
- [ ] Testing

## 🟢 ADV — Aprender posteriormente

- [ ] Generators avanzados
- [ ] Async iterators
- [ ] Advanced template literal types
- [ ] Recursive types
- [ ] Metaprogramming
- [ ] Manipulación avanzada de prototypes