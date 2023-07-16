# Day 3:

## Summary of the course ✍️

### Operators

- typeof → Operator Gets us the data type of a variable
- `→ Concatenate | Sum`
- (+) (-) (/) (*)
- the star for multiplication (*)

### Comparasion & Equality

- = > = < =
- = == === // = assign // == check value // === check value and type
- & || ++

---

### Expressions

### What are Variables

Just a container for some value with a name of out creation.

### Statements vs Expressions

Statement: are Actions.

Expression: are Values.

- let ten = 6 + 4; | Statement
- Arrays
- 4 / 2 * 10
- “Husam ” + “Abu Zina”

---

Functions

Group of lines of code that are executed on demand!.

### Normal Functions:

### Example:

function Mul(x, y) {
return x * y;
}

function yell(x) {
return x.toUpperCase();
}

function longerthan(arr1, arr2) {
return arr1.length  > arr2.length
}

### Functions

Group of lines of code that are executed on demand!.

### Normal Functions:

### Example:

function Mul(x, y) {
return x * y;
}

function yell(x) {
return x.toUpperCase();
}

function longerthan(arr1, arr2) {
return arr1.length  > arr2.length
}

---

## Coding Exercises 👨‍💻

### [Stand in Line](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/stand-in-line)

#### My Solution ✅

```javascript
function nextInLine(arr, item) {
  // Only change code below this line
  arr.push(item);
  return arr.shift();
  // Only change code above this line
}

// Setup
let testArr = [1, 2, 3, 4, 5];

// Display code
console.log("Before: " + JSON.stringify(testArr));
console.log(nextInLine(testArr, 6));
console.log("After: " + JSON.stringify(testArr));
```

---



### [Global vs. Local Scope in Functions](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/global-vs--local-scope-in-functions)

#### My Solution ✅

```javascript 
// Setup
const outerWear = "T-Shirt";

function myOutfit() {
  // Only change code below this line
  const outerWear = "sweater";

  // Only change code above this line
  return outerWear;
}

myOutfit();
```

---


### [Local Scope and Functions](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/local-scope-and-functions)

#### My Solution ✅

```javascript
function myLocalScope() {
  // Only change code below this line
  const myVar = "foo";
  console.log(myVar);
  // Only change code above this line
}

myLocalScope();
console.log(typeof myVar); // This will throw a ReferenceError, but the tests will not fail

```

---

### [Global Scope and Functions](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/global-scope-and-functions)

#### My Solution ✅

```javascript
// Declare the myGlobal variable below this line
let myGlobal = 10;

function fun1() {
  // Assign 5 to oopsGlobal here
  oopsGlobal = 5;
}

// Only change code above this line

function fun2() {
  let output = "";
  if (typeof myGlobal != "undefined") {
    output += "myGlobal: " + myGlobal;
  }
  if (typeof oopsGlobal != "undefined") {
    output += " oopsGlobal: " + oopsGlobal;
  }
  console.log(output);
}

```

---

### [Return a Value from a Function with Return](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/return-a-value-from-a-function-with-return)

#### My Solution ✅

```javascript
function timesFive (x) {
  return x * 5;
}
```
