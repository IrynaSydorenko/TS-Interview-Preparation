<details>
<summary><strong>1. What are the main differences between TypeScript and JavaScript?</strong></summary>

### 1. Static Typing
TypeScript adds **static typing**, allowing developers to specify types for variables, function parameters, and return values. 
JavaScript uses **dynamic typing**, so types are inferred at runtime.

```ts
// TypeScript
let age: number = 25;
let name: string = "Iryna";
```

```js
// JavaScript
let age = 25; // type is inferred at runtime
let name = "Iryna";
```

---

### 2. Compilation vs Interpretation
- **TypeScript** code must be compiled into JavaScript to run in browsers or Node.js.
- **JavaScript** is interpreted directly by the engine.

---

### 3. Modern JS Features Support
- **TypeScript** supports all modern JS features (like ES6+), even in environments that don’t support them natively.
- **JavaScript** depends on the runtime environment (e.g., browser, Node.js) for feature support.

---

### 4. Interfaces and Classes
- **TypeScript** supports **interfaces** and has extended capabilities for classes.
- **JavaScript** lacks interfaces and only added basic class syntax with ES6.

```ts
interface Person {
  name: string;
  age: number;
}

let person: Person = {
  name: "Iryna",
  age: 25
};
```

---

### 5. Development Experience
- **TypeScript** offers better editor support with **autocompletion**, **IntelliSense**, and **type-checking**.
- **JavaScript** provides limited static analysis capabilities.

---

### 6. Error Detection
- **TypeScript** can catch many errors at **compile time**.
- **JavaScript** errors usually appear only at **runtime**, making debugging harder.

---

### Conclusion
TypeScript is a **superset of JavaScript** that enhances developer experience with static typing, error checking, and modern JS support. However, it requires a compilation step before execution.

</details>

<details>
<summary><strong>2. What are the advantages and disadvantages of using TypeScript?</strong></summary>

### ✅ Advantages

#### 1. Static Typing
TypeScript allows you to define types for variables, function parameters, and return values. This helps catch errors during development.

```ts
let count: number = 10;
count = "text"; // Compilation error
```

---

#### 2. Better Editor Support
Thanks to type annotations, editors provide better autocomplete, IntelliSense, and refactoring tools.

---

#### 3. Early Error Detection
TypeScript detects many errors during compilation, reducing bugs in production.

```ts
function add(a: number, b: number): number {
  return a + b;
}

add(5, "3"); // Compilation error
```

---

#### 4. Modern JavaScript Features
TypeScript supports all ES6+ features (like classes, arrow functions, async/await), even in older environments.

```ts
class Person {
  constructor(public name: string, public age: number) {}
}

const iryna = new Person("Iryna", 25);
```

---

#### 5. Scalability
TypeScript improves maintainability and scalability in large projects due to type safety and modular code organization.

---

#### 6. Compatibility with JavaScript
All valid JavaScript code is valid TypeScript. You can gradually adopt TS in existing JS projects.

```ts
const greet = (name) => console.log("Hello, " + name); // Valid JS in TS
```

---

### ❌ Disadvantages

#### 1. Compilation Step
TypeScript must be compiled to JavaScript before execution, adding complexity to the build process.

---

#### 2. Learning Curve
For beginners or JS-only developers, understanding types, interfaces, generics, and access modifiers can be challenging.

---

#### 3. More Boilerplate Code
Declaring types and interfaces can make code more verbose.

```ts
interface User {
  name: string;
  age: number;
}

const user: User = { name: "Iryna", age: 25 };
```

---

#### 4. Configuration Overhead
You need to set up `tsconfig.json` and possibly other tools like Webpack or Babel for TS integration.

---

#### 5. Overhead in Small Projects
For quick prototypes or small scripts, static typing might feel unnecessary and slow down development.

---

### 🔚 Conclusion
TypeScript enhances code safety, tooling, and scalability, making it ideal for large or long-term projects. However, it introduces extra setup and a steeper learning curve compared to plain JavaScript.

</details>

<details>
<summary><strong>3. What are data types in TypeScript and how are they used?</strong></summary>

TypeScript uses static typing, which means variables, function parameters, return values, and object properties can all have defined types. This makes code more predictable, easier to debug, and safer in large-scale projects.

---

### 🔤 Basic Types

#### `number`
Used for numeric values (both integers and floats).
```ts
let age: number = 25;
let pi: number = 3.14;
```

#### `string`
Text values, either in quotes or template literals.
```ts
let name: string = "Iryna";
let greeting: string = `Hello, ${name}!`;
```

#### `boolean`
Logical true/false.
```ts
let isLoggedIn: boolean = true;
```

#### `array`
List of values of a specific type.
```ts
let numbers: number[] = [1, 2, 3];
let names: Array<string> = ["Anna", "Iryna"];
```

#### `tuple`
Fixed-length array with defined types for each element.
```ts
let person: [string, number] = ["Iryna", 25];
```

#### `enum`
A set of named constants.
```ts
enum Direction {
  Up,
  Down,
  Left,
  Right,
}
let move: Direction = Direction.Up;
```

#### `any`
Disables type checking — use with caution.
```ts
let randomValue: any = "Hello";
randomValue = 42; // allowed
```

#### `void`
Function that returns no value.
```ts
function logMessage(message: string): void {
  console.log(message);
}
```

#### `null` and `undefined`
Represent the absence of a value.
```ts
let emptyValue: null = null;
let notAssigned: undefined = undefined;
```

#### `object`
Defines an object with key-value pairs.
```ts
let person: { name: string; age: number } = {
  name: "Iryna",
  age: 25,
};
```

---

### 🧩 Advanced Types

#### Interfaces
Custom object type definitions.
```ts
interface Car {
  brand: string;
  model: string;
  year: number;
}

let car: Car = {
  brand: "Tesla",
  model: "Model 3",
  year: 2020,
};
```

#### Union Types
Allows a variable to be one of several types.
```ts
let value: number | string;
value = 10;
value = "Hello";
```

#### Literal Types
Restrict values to a specific set.
```ts
let status: "active" | "inactive" | "pending";
status = "active";
```

#### Function Types
Specify parameter and return types for functions.
```ts
function add(a: number, b: number): number {
  return a + b;
}

let multiply: (x: number, y: number) => number = (x, y) => x * y;
```

---

### 📌 Conclusion
Using TypeScript's type system helps reduce runtime errors, improves code clarity, and supports large-scale development through better tooling and readability.

</details>

<details>
<summary><strong>4. What is the difference between <code>type</code> and <code>interface</code> in TypeScript?</strong></summary>

In TypeScript, both <code>type</code> and <code>interface</code> are used to define custom types. However, they serve slightly different purposes and have different capabilities.

---

### 🧱 <code>type</code> Keyword

<code>type</code> is used to define a type alias — a name for any type, including:
- primitives
- unions/intersections
- object types
- functions

```ts
export type User = {
  name: string;
  age: number;
  isActive: boolean;
};

const user: User = {
  name: "Iryna",
  age: 25,
  isActive: true,
};
```

### 🧩 <code>interface</code> Keyword

<code>interface</code> is used to describe the shape of objects and is typically used when designing class or object structures.

```ts
interface Person {
  name: string;
  age: number;
}

const person: Person = {
  name: "Anna",
  age: 30,
};
```

---

### 🔍 Key Differences

| Feature | <code>type</code> | <code>interface</code> |
|--------|------------------|------------------------|
| **Extends** | Can use intersections (<code>&</code>) | Can use <code>extends</code> keyword |
| **Unions** | ✅ Supports union types | ❌ Not supported |
| **Declaration merging** | ❌ Not supported | ✅ Interfaces with same name are merged |
| **Complex types** | ✅ Supports tuples, unions, intersections, primitives | ❌ Only for object shapes |

---

### 📌 Examples

#### Intersection with <code>type</code>
```ts
type Vehicle = {
  brand: string;
};

type Car = Vehicle & {
  model: string;
};
```

#### Extending with <code>interface</code>
```ts
interface Employee extends Person {
  position: string;
}
```

#### Union with <code>type</code>
```ts
type Status = "active" | "inactive" | "pending";
```

#### Declaration Merging with <code>interface</code>
```ts
interface User {
  name: string;
}

interface User {
  age: number;
}

const user: User = {
  name: "Iryna",
  age: 25,
};
```

---

### 🧠 Conclusion
- Use <code>interface</code> when describing object shapes or when you need declaration merging.
- Use <code>type</code> for unions, intersections, or when aliasing primitives and tuples.

Both are powerful tools, and in many cases, the choice is a matter of style or preference.

</details>

<details>
<summary><strong>5. What is a type intersection in TypeScript?</strong></summary>

Type intersections in TypeScript allow you to combine multiple types into one. This is done using the <code>&</code> operator.

---

### 🔗 What is a type intersection?

A type intersection creates a new type that includes **all** properties from the intersected types. It's like merging multiple type definitions into one:

```ts
type Car = {
  brand: string;
  model: string;
};

type Engine = {
  horsepower: number;
};

type Vehicle = Car & Engine & {
  year: number;
};

const myVehicle: Vehicle = {
  brand: "Tesla",
  model: "Model S",
  horsepower: 670,
  year: 2021
};
```

In this example, the new type <code>Vehicle</code> includes properties from <code>Car</code>, <code>Engine</code>, and an additional <code>year</code> field.

---

### 🔍 Type Intersection vs Union

| Concept | Intersection (<code>&</code>) | Union (<code>|</code>) |
|--------|--------------------------|----------------------|
| Meaning | Must satisfy **all** types | Can satisfy **any one** type |
| Example |
<pre><code>type A = { name: string };
type B = { age: number };
type AB = A & B;
// AB must have both name and age</code></pre> |
<pre><code>type A = { name: string };
type B = { age: number };
type AB = A | B;
// AB can have just name, just age, or both</code></pre> |

---

### 🧠 Summary
- <strong>Intersection types</strong> merge all members from multiple types — useful when an object must conform to multiple constraints.
- They are commonly used with <code>type</code> and not <code>interface</code>.

This is exactly what happens in:
```ts
type Vehicle = Car & { year: number };
```
You're creating a new type that includes everything from <code>Car</code> and adds <code>year</code>.

</details>

<details>
<summary><strong>6. What are interfaces in TypeScript?</strong></summary>

Interfaces in TypeScript are used to define the structure of an object. They act as contracts in your code, helping ensure that objects adhere to a specific shape.

---

### 📌 Key Features of Interfaces

- **Describe object shape:** Define the required and optional properties and methods.
- **Inheritance:** Interfaces can extend one or more other interfaces using `extends`.
- **Declaration merging:** Multiple declarations with the same name are automatically merged.

---

### 🧱 Basic Example

```ts
interface User {
  name: string;
  age: number;
  isActive: boolean;
  greet(): string;
}

const user: User = {
  name: "Iryna",
  age: 25,
  isActive: true,
  greet() {
    return `Hello, my name is ${this.name}`;
  }
};

console.log(user.greet()); // "Hello, my name is Iryna"
```

---

### 🧬 Inheriting from Another Interface

```ts
interface Person {
  name: string;
  age: number;
}

interface Employee extends Person {
  position: string;
}

const employee: Employee = {
  name: "Iryna",
  age: 25,
  position: "Frontend Developer"
};
```

The `Employee` interface inherits `name` and `age` from `Person` and adds a `position` property.

---

### ❓ Optional Properties

Use `?` to mark a property as optional:

```ts
interface Car {
  brand: string;
  model: string;
  year?: number;
}

const car1: Car = { brand: "Tesla", model: "Model S" };
const car2: Car = { brand: "Tesla", model: "Model X", year: 2021 };
```

---

### 🔁 Function Interfaces

Interfaces can describe function signatures:

```ts
interface MathOperation {
  (a: number, b: number): number;
}

const add: MathOperation = (a, b) => a + b;
const multiply: MathOperation = (a, b) => a * b;
```

---

### 🔄 Declaration Merging

Interfaces with the same name get merged:

```ts
interface User {
  name: string;
}

interface User {
  age: number;
}

const user: User = {
  name: "Iryna",
  age: 25
};
```

Both declarations are combined into a single interface.

---

### 🧠 Summary
- Interfaces are contracts for object structure.
- They can include methods, optional properties, and support inheritance.
- Use interfaces when designing reusable object types and APIs.
- Prefer interfaces over type aliases for object shapes when using declaration merging.

</details>

<details>
<summary><strong>7. When should you use <code>type</code> vs <code>interface</code> in TypeScript?</strong></summary>

Choosing between <code>type</code> and <code>interface</code> in TypeScript depends on the structure you're defining and how you intend to use or extend it. Both can describe the shape of objects, but they have differences in capabilities and syntax.

---

### ✅ Use <code>interface</code> when:

#### 1. **Describing object shapes or class structures**
Interfaces are ideal for describing the structure of an object or class, especially when you want to leverage inheritance.

```ts
interface Person {
  name: string;
  age: number;
}

interface Employee extends Person {
  position: string;
}
```

#### 2. **You need declaration merging**
You can declare the same interface multiple times, and TypeScript will merge them.

```ts
interface User {
  name: string;
}

interface User {
  age: number;
}

const user: User = { name: "Iryna", age: 25 };
```

#### 3. **Working in ecosystems like React**
Interfaces are commonly used for typing props, state, and context in React projects.

---

### ✅ Use <code>type</code> when:

#### 1. **You need unions, intersections, or primitives**
<code>type</code> aliases are better suited for combining types or describing primitives, tuples, or functions.

```ts
// Union
type ID = string | number;

// Intersection
type Car = {
  brand: string;
};

type Vehicle = Car & {
  year: number;
};

// Tuple
type Coordinates = [number, number];

const point: Coordinates = [10, 20];
```

#### 2. **Typing functions directly**
<code>type</code> can define function signatures more flexibly:

```ts
type MathOperation = (a: number, b: number) => number;

const multiply: MathOperation = (a, b) => a * b;
```

#### 3. **You don't need to extend or merge**
<code>type</code> cannot be reopened to add new properties, unlike <code>interface</code>.

---

### 📊 Summary Table

| Feature | <code>interface</code> | <code>type</code> |
|--------|--------------------------|--------------------|
| Inheritance | ✅ via <code>extends</code> | ✅ via intersections (&) |
| Declaration merging | ✅ | ❌ |
| Unions / intersections | ❌ | ✅ |
| Describes functions | ✅ (less commonly used) | ✅ |
| Tuples / primitives | ❌ | ✅ |

---

### 🧠 Recommendation
- Use <strong><code>interface</code></strong> for objects, class structures, and when declaration merging is needed.
- Use <strong><code>type</code></strong> for primitives, tuples, function types, and when working with unions or intersections.
- When in doubt, follow your team’s convention. If no convention exists, prefer <code>interface</code> for objects.

</details>

<details>
<summary><strong>8. Can you intersect a primitive type with an object type in TypeScript?</strong></summary>

No, you cannot intersect a primitive type (like <code>string</code>) with an object type (like <code>{ age: number }</code>) in a meaningful or useful way. TypeScript will not allow this because these types are incompatible by nature.

---

### 🚫 Example of incompatible intersection

```ts
type A = string; // primitive type
type B = { age: number }; // object type

type AB = A & B; // ❌ Invalid: TypeScript will error here
```

TypeScript will produce an error similar to:

```
Type 'string' is not assignable to type '{ age: number; }'.
```

---

### ✅ Example of compatible intersection (only object types)

If both types are object types, the intersection works as expected:

```ts
type A = { name: string };
type B = { age: number };

type AB = A & B;

const person: AB = {
  name: "Iryna",
  age: 25,
};
```

In this case, the resulting type <code>AB</code> must contain both <code>name</code> and <code>age</code>.

---

### 🧠 Summary

- Intersection (<code>&</code>) combines all properties from both types.
- This only works when types are compatible—typically both being object types.
- You **cannot** intersect a primitive type (like <code>string</code>) with an object type, because primitives do not have properties.

</details>

