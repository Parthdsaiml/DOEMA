
### 1. **Functions in JavaScript**
#### What is a Function?
A function is a block of code designed to perform a specific task. It can be defined once and reused throughout your code, improving efficiency and readability.

- **Function Declaration**: Traditional way of defining a function.
  ```javascript
  function add(a, b) {
    return a + b;
  }
  ```

- **Function Expression**: Functions can also be created as expressions and assigned to variables. These can be anonymous or named.
  ```javascript
  const multiply = function(a, b) {
    return a * b;
  };
  ```

- **Named Function Expression**: A function expression that has a name (helpful for debugging).
  ```javascript
  const divide = function divideNumbers(a, b) {
    return a / b;
  };
  ```

#### Why Use Functions?
- **Reusability**: Instead of repeating logic, write it once and call it multiple times.
- **Modularity**: Break down the code into smaller, more manageable blocks.
- **Abstraction**: Hides complex logic, making the code cleaner and easier to understand.

---

### 2. **Parameters vs Arguments**
- **Parameters**: Variables in the function declaration that define the input.
- **Arguments**: The actual values passed when calling the function.

```javascript
function greet(name, age) { // Parameters: name, age
  console.log(`Hello, ${name}, you are ${age} years old.`);
}

greet('John', 30); // Arguments: 'John', 30
```

When you call `greet('John', 30)`, `'John'` and `30` are **arguments**, while `name` and `age` are **parameters**.

---

### 3. **Parameters in JavaScript**
#### a. **Required Parameters**
A function expects certain arguments. If not provided, `undefined` is assigned.

```javascript
function greet(name) {
  console.log(`Hello, ${name}`);
}
greet(); // Hello, undefined
```

#### b. **Destructured Parameters**
You can destructure objects or arrays in the function parameters for easier access.

```javascript
// Object Destructuring
function displayUser({ name, age = 25 }) {
  console.log(`${name} is ${age}`);
}

displayUser({ name: 'Alice' }); // Alice is 25
```

#### c. **Rest Parameters (`...`)**
Use `...` to gather all remaining arguments into an array.

```javascript
function sumAll(...numbers) {
  return numbers.reduce((total, num) => total + num, 0);
}

console.log(sumAll(1, 2, 3, 4)); // 10
```

#### d. **Default Parameters**
Provide default values for parameters that are not passed.

```javascript
function createUser(name = 'Guest', isAdmin = false) {
  console.log(`${name} is an admin: ${isAdmin}`);
}

createUser(); // Guest is an admin: false
createUser('Alice'); // Alice is an admin: false
createUser('Bob', true); // Bob is an admin: true
```

---

### 4. **Arguments in JavaScript**
#### a. **Positional Arguments**
The order of arguments matters when calling a function.

```javascript
function createUser(firstName, lastName) {
  return `${firstName} ${lastName}`;
}

console.log(createUser('John', 'Doe')); // John Doe
```

#### b. **Spread Syntax (`...`)**
Use the spread operator to spread elements of an array as individual arguments.

```javascript
function multiply(a, b, c) {
  return a * b * c;
}

const numbers = [2, 3, 4];
console.log(multiply(...numbers)); // 24
```

---

### 5. **Classic vs Nested Functions**
#### a. **Classic Function**
The basic function declaration or expression, as shown earlier.

#### b. **Nested Function**
Functions can be nested inside one another, forming a **scope chain**.

```javascript
function outer() {
  const outerVar = 'Outer variable';
  
  function inner() {
    console.log(outerVar); // Access outerVar from the outer scope
  }

  inner();
}

outer(); // Outer variable
```

The inner function has access to variables in its **outer scope** (closure).

---

### 6. **Immediately Invoked Function Expression (IIFE)**
An IIFE is a function that runs immediately after being defined. It's often used to create a new scope.

```javascript
(function() {
  console.log('This runs immediately!');
})(); 
```

IIFE is helpful for creating **isolated scopes** to prevent polluting the global namespace.

---

### 7. **More Function Types**
#### a. **Arrow Functions**
Arrow functions provide a shorter syntax and lexical `this` behavior, meaning `this` is inherited from the surrounding context.

```javascript
const square = (x) => x * x;
console.log(square(5)); // 25

const person = {
  name: 'Alice',
  greet: function() {
    setTimeout(() => {
      console.log(this.name); // "Alice" (lexical `this`)
    }, 1000);
  }
};

person.greet();
```

Arrow functions do not have their own `this`, `arguments`, or `super`. They use the `this` from their lexical scope.

#### b. **Anonymous Functions**
Functions without names. Typically used as arguments to other functions.

```javascript
const numbers = [1, 2, 3];
numbers.forEach(function(num) {
  console.log(num); // Logs 1, 2, 3
});
```

#### c. **Higher-Order Function (HOF)**
A higher-order function takes a function as an argument or returns a function.

```javascript
function multiplyBy(factor) {
  return function(num) {
    return num * factor;
  };
}

const double = multiplyBy(2);
console.log(double(3)); // 6
```

Here, `multiplyBy` returns a function that multiplies any number by the given factor.

#### d. **Callback Functions**
A function passed as an argument to another function and executed later.

```javascript
function fetchData(callback) {
  setTimeout(() => {
    callback("Data loaded!");
  }, 2000);
}

fetchData((message) => {
  console.log(message); // "Data loaded!" after 2s
});
```

#### e. **First-Class Functions**
Functions are treated as first-class citizens in JavaScript. They can be assigned to variables, passed as arguments, or returned from other functions.

```javascript
const sayHello = function() { console.log("Hello!"); };
sayHello(); // Hello!

function execute(func) {
  func(); // Call the passed function
}

execute(sayHello); // Hello!
```

#### f. **Pure vs Impure Functions**
- **Pure Function**: Always returns the same output for the same input and has no side effects.
  ```javascript
  function add(a, b) {
    return a + b; // Pure function
  }
  ```
  
- **Impure Function**: Modifies external state or relies on it.
  ```javascript
  let count = 0;
  function increment() {
    count++; // Impure function
  }
  ```

---

### 8. **Scoping in JavaScript**
#### a. **Global Scope**
Variables declared outside any function or block have a global scope.

```javascript
const globalVar = "I'm global!";

function checkGlobal() {
  console.log(globalVar); // Accessible inside the function
}

checkGlobal();
```

#### b. **Function Scope**
Variables declared with `var` are scoped to the function in which they are declared.

```javascript
function funcScope() {
  var localVar = "I'm function-scoped!";
  console.log(localVar); // Accessible inside the function
}

funcScope();
// console.log(localVar); // Error: localVar is not accessible
```

#### c. **Block Scope**
Variables declared with `let` and `const` are block-scoped, meaning they are only accessible within the block they are defined.

```javascript
if (true) {
  let blockVar = "I'm block-scoped!";
  const PI = 3.14;
}

console.log(blockVar); // Error: blockVar is not defined
```

---

### 9. **Closures**
A closure is a function that retains access to its lexical scope even after the function has executed.

```javascript
function makeCounter() {
  let count = 0;
  return function() {
    count++;
    return count;
  };
}

const counter = makeCounter();
console.log(counter()); // 1
console.log(counter()); // 2
```

Here, the returned function "remembers" the `count` variable from the `makeCounter` function, even after it's executed.

---

### 10. **Hoisting**
In JavaScript, **hoisting** means that function and variable declarations are moved to the top of their scope during compilation.

#### a. **Variable Hoisting**
- `var`: Hoisted and initialized to `undefined`.
- `let`/`const`: Hoisted but not initialized, leading to a **Temporal Dead Zone** (TDZ) where accessing them before declaration results in an error.

```javascript
console.log(hoistedVar); // undefined (due to hoisting)
var hoistedVar = 5;

// console.log(hoistedLet); // Error (TDZ)
let hoistedLet = 10;
```

#### b. **Function Hoisting**
Function declarations are fully hoisted, meaning they can be called before their definition.

```javascript
hoistedFunc(); // Works

function hoistedFunc() {
  console.log("I'm hoisted!");
}
```

---

### Key Takeaways:
- Functions provide reusability and modularity.
- **Parameters** are the placeholders, while **arguments** are the actual values passed.
- JavaScript offers flexible function definitions like arrow functions, higher-order functions, and closures.
- **Scoping** and **hoisting** are crucial concepts in managing variable visibility.
- **Closures** allow you to maintain state in a function even after it finishes execution.

