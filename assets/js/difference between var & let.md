# Assignment: Difference Between `var` and `let` & Defensive Programming

## 1. Difference Between `var` and `let`

### Scope

-   **var** is function-scoped.
-   **let** is block-scoped.

Example:

``` javascript
if (true) {
  var x = 10;
  let y = 20;
}

console.log(x); // 10
console.log(y); // Error
```

### Re-declaration

-   `var` allows redeclaration in the same scope.
-   `let` does not allow redeclaration.

``` javascript
var a = 5;
var a = 8; // allowed

let b = 5;
let b = 8; // Error
```

### Hoisting

Both `var` and `let` are hoisted, but: - `var` is initialized with
`undefined`. - `let` stays in the **Temporal Dead Zone** until declared.

``` javascript
console.log(m); // undefined
var m = 7;

console.log(n); // Error
let n = 7;
```

### Best Practice

Modern JavaScript recommends using: - `let` for variables that may
change. - `const` for variables that should not change. - Avoid using
`var` in modern development.

------------------------------------------------------------------------

## 2. Defensive Programming

### Definition

Defensive programming is a coding practice where developers anticipate
possible errors or invalid inputs and handle them properly to prevent
system crashes or unexpected behavior.

### Goals

-   Reduce bugs
-   Prevent crashes
-   Improve reliability
-   Handle invalid user input safely

### Techniques

#### 1. Input Validation

``` javascript
function divide(a, b) {
  if (typeof a !== "number" || typeof b !== "number") {
    return "Invalid input";
  }

  if (b === 0) {
    return "Cannot divide by zero";
  }

  return a / b;
}
```

#### 2. Null or Undefined Checks

``` javascript
function printName(user) {
  if (!user || !user.name) {
    console.log("Name not found");
    return;
  }

  console.log(user.name);
}
```

#### 3. Error Handling

``` javascript
try {
  let data = JSON.parse('{"name":"Mahmoud"}');
  console.log(data.name);
} catch (error) {
  console.log("Invalid JSON");
}
```

### Advantages

-   Safer programs
-   Fewer runtime errors
-   Easier maintenance

### Disadvantages

-   Slightly more code
-   Extra development time

------------------------------------------------------------------------

## Conclusion

`var` and `let` are used to declare variables in JavaScript, but they
behave differently. `let` provides block-level scope and prevents
redeclaration errors, making it safer for modern development. Defensive
programming helps developers write more reliable and secure code by
validating inputs, checking conditions, and handling unexpected errors
properly.