# Day 13:

## Summary of the course ✍️

## Advanced Scope

### Hoisting:

look ahead of the code and use all the possible variables in that scope.

This means that regardless of where a variable is declared within a function or a block of code, it behaves as if it were declared at the top of that scope.

```jsx
var student;
var teacher;

student; // undefined.
teacher; // undefined.
var student = "you";
var teacher = "Kyle";
```

In the above code, **`var x`** is hoisted to the top of the current scope during the compilation phase. So, the first **`console.`**


```jsx
var teacher = "Kyle";
otherTeacher();       // ??

function otherTeacher() {
   console.log(teacher);
   var teacher = "Suzy";
}

// -------------------------------------------

teacher = "Kyle";
var teacher;

getTeacher();

function getTeacehr() {
    return teacher;
}
```

### let Doesn’t Hoist

```jsx
// let and sonst only hoist to a block
// whereas vars hoist to a function.

// var: When the scope starts, intialize it to undefined.
// let: Create a place called "VariableName", but do not initialize it.

{
  teacher = "Kyle"; // TDZ error!
  let teacher;
}

var teacher = "Kyle";

{
  console.log(teacher); // TDZ error!
  let teacher = "Suzy";
}
```

---

## Closure

### Closure

is when a function “remembers” it’s lexical scope ,even when the function is executed outside that lexical scope.


```jsx
function ask(qustion) {
   setTimeout(function waitASec() {
    console.log(question);
  }, 100);
}

ask("What is closure?");

// -----------------------------

function ask(question) {
   return function holdYourQuestion() {
   console.log(question);
  };
}

var myQuestion = ask("What is closure?");

myQuestions();
```

### Closing Over Variables

```jsx
// Closure: is a preservation of the linkage to a variable, not the capturing of the value. 

var teacher = "" // you close over a variable : Closure.

var myTeacher = function() {
  console.log(treacher);
};

teacher = "Suzy";

myTeacher(); // Suzy

// -----------------------------------

for (var i = 1; i <= 3; i++) { // prints after the loop ends.
   setTimeout (funciton() {
     console.log(`i: ${i}`);
}, i * 1000);
}
// i: 4
// i: 4
// i: 4

// ------------------------------------

for (var i = 1; i <= 3; i++) {
   let j = i; // block scoped // 3 seperate J
   setTimeout (funciton() {
     console.log(`j: ${j}`);
}, i * 1000);
}
// i: 1
// i: 2
// i: 3

// ------------------------------------

for (let i = 1; i <= 3; i++) { // make new i for each loop. Automatically  
   setTimeout (funciton() {
     console.log(`i: ${i}`);
}, i * 1000);
}
// i: 1
// i: 2
// i: 3
```


### Module Pattern

```jsx
var workshop = {
  teacher: "Kyle",
   ask(question) {
  console.log(this.teacher, question);
  },
};

workshop.ask("Is this a module?"); 

// Modules encapsulate data and behaviour (methods) together.
// The state (data) of a module is helpd by it's methods via closure.

var workshop = (function Module(teacher){
   var publicAPI = {ask,}

return publicAPI;

// -------------

   function ask(question) {
  console.log(teacher, question);
  }
}) ("Kyle");

workshop.ask("Is this a module?, right?");  // Only expose what is necessary.
```

### ES6 Modules & Node.js

```jsx
// npm: is the largest code repository ever invented.
// When use ES6 Modules you have to use files with extention "file.mjs"

// export  ----> make things public

var teacher = "Kyle";

export default funciton ask(question) {
   console.log(teacher, question);
};
```

### ES6 Module Syntax

```jsx
// ------------ workshop.mjs -----------

var teacher = "Kyle";
export default function ask (question {
   console.log(teacher, question);
});

import ask from "workshop.mjs";

asl("It's a default import, right?");

import * as workshop from "workshop.mjs";

workshop.ask("It's a name space import, right?")
```

## Coding Exercises 👨‍💻


---

## ADVANCED SCOPE:

- Question 1 💡

Given the following code snippet and explain what's happening.

    
```jsx

for (var i = 0; i < 5; i++) {
    setTimeout(function() {
      console.log("value of [i] is: ", i);
    }, 100);
}
```

The current output is: "value of [i] is: 5" five times.

The output should be:

"value of [i] is: ", 0 "value of [i] is: ", 1 "value of [i] is: ", 2 "value of [i] is: ", 3 "value of [i] is: ", 4

Without changing anything in the for loop's code itself, provide a solution to fix it.


  ### Solution: ✅
  
```jsx

for (let i = 0; i < 5; i++) {
  setTimeout(function() {
    console.log("value of [i] is: ", i);
  }, 100);
}

"value of [i] is: " 0
"value of [i] is: " 1
"value of [i] is: " 2
"value of [i] is: " 3
"value of [i] is: " 4


```

---

- Question 2 💡

Given the following code snippet and explain what's happening.

```jsx

for (let i = 0; i < 5; i++) {
   let array = [];
   array.push(i);
   console.log("Current array is: ", array)
}


```

The current output is:

"Current array is: [ 0 ]" "Current array is: [ 1 ]" "Current array is: [ 2 ]" "Current array is: [ 3 ]" "Current array is: [ 4 ]".

The output should be: "Current array is: [0, 1, 2, 3, 4]".

Provide a solution to fix it.

    

  ### Solution: ✅
  
```jsx

let array = []; // Move the array declaration outside the loop

for (let i = 0; i < 5; i++) {
  array.push(i);
  console.log("Current array is: ", array);
}

"Current array is: [ 0 ]"
"Current array is: [ 0, 1 ]"
"Current array is: [ 0, 1, 2 ]"
"Current array is: [ 0, 1, 2, 3 ]"
"Current array is: [ 0, 1, 2, 3, 4 ]"


```

---


- Question 3 💡

Given the following code snippet and explain what's happening.
    
```jsx


let functions = [];

for (var i = 0; i < 5; i++) {
  functions.push(() => {
    console.log("Current value of i is:", i);
  });
}

functions.forEach((func) => func());


```

The current output is:

"Current value of i is: 5" "Current value of i is: 5" "Current value of i is: 5" "Current value of i is: 5" "Current value of i is: 5"

The output should be:

"Current value of i is: 0" "Current value of i is: 1" "Current value of i is: 2" "Current value of i is: 3" "Current value of i is: 4"

Provide a solution to fix it.


  ### Solution: ✅
  
```jsx

let functions = [];

for (let i = 0; i < 5; i++) {
  functions.push(() => {
    console.log("Current value of i is:", i);
  });
}

functions.forEach((func) => func());

"Current value of i is: 0"
"Current value of i is: 1"
"Current value of i is: 2"
"Current value of i is: 3"
"Current value of i is: 4"


```

---


## CLOSURE:

- Question 1 💡
  
Create a function called privateCounter() that behaves like a private counter. The function should not have any public variables, and the count should only be accessible through a closure. It should have two methods: increment() and getCount(). The increment() method should increment the count, and getCount() should return the current count.


  ### Solution: ✅
  
```jsx

function privateCounter() {
  let count = 0; // Private variable accessible only inside the closure

  // Increment the count
  function increment() {
    count++;
  }

  // Get the current count
  function getCount() {
    return count;
  }

  // Return the methods as an object
  return {
    increment,
    getCount,
  };
}

// Example usage
const counter = privateCounter();

console.log(counter.getCount()); // Output: 0

counter.increment();
console.log(counter.getCount()); // Output: 1

counter.increment();
counter.increment();
console.log(counter.getCount()); // Output: 3


```

--- 


- Question 2 💡
  
Write a JavaScript function called generateFibonacci(count) that returns a closure. The closure should generate the next number in the Fibonacci sequence each time it is called. The generateFibonacci function should take a parameter count that determines how many times the closure will generate the next number, and it should use recursion for this purpose.


  ### Solution: ✅
  
```jsx

function generateFibonacci(count) {
  let currentCount = 0;
  let fibonacciArray = [];

  function calculateFibonacci(n) {
    if (n <= 1) return n;
    return calculateFibonacci(n - 1) + calculateFibonacci(n - 2);
  }

  function generateNextFibonacci() {
    if (currentCount < count) {
      const nextFibonacci = calculateFibonacci(currentCount);
      fibonacciArray.push(nextFibonacci);
      currentCount++;
      return nextFibonacci;
    } else {
      return "No more Fibonacci numbers.";
    }
  }

  return generateNextFibonacci;
}

// Example usage:
const generateNextFib = generateFibonacci(10);
console.log(generateNextFib()); // Output: 0
console.log(generateNextFib()); // Output: 1
console.log(generateNextFib()); // Output: 1
console.log(generateNextFib()); // Output: 2
// ...and so on, up to the 10th Fibonacci number


```


