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

## Topic 1:

- Question 1 💡

Some Quesiton ?
    
    
```jsx



```

  ### Solution: ✅
  
```jsx



```
