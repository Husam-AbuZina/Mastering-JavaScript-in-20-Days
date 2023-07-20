# Day 12:

## Summary of the course ✍️

### Function Expressions

```jsx
function teacher() { } // function declaration // add their marble name to the enclosing scope

var myTeacher = function anotherTeacher() { // function expression // add their marble to their own scope
   console.log(anotherTeacher);
}

console.log(teacher);
console.log(myTeacher);
console.log(anotherTeacher); // ReferenceError 

// --------------------------------------------------------------------

var clickHandler = function() { // function declaration
    // ..
};

var keyHandler = function keyHandler() { // function expression // this is "better".
   // .. 
}
```

### Naming Function Expressions

```jsx
// --------------------------------------------------------------------

var clickHandler = function() { // function declaration
    // ..
};

var keyHandler = function keyHandler() { // function expression // this is better.
   // .. 
}

// ------------------------ Because ----------------------------

// 1. Reliable function self-reference (recursion, etc)
// 2. More debuggable stack trace ( function name show up in the stack trace )
// 3. More self-documenting code

// 4. Name all your anonymous funcitons (arrow, normal, ...)

```


## Arrow Functions

```jsx
var ids = people.map(person => person.id);

var ids = people.map(function getId(person) {
    return person.id;
)};

// The Shorter the suntax the More corner cases they have.

// even if it is an arrow function, give it an explicit name.

var getId = person => person.id;
var ids = people.map(getId);

// -------------------

car getDataFrom = person => getData (person.id);
getPerson()
.then(getDataFrom);
.then(renderData);

```

## Functions Types Hierarchy

![FunctionsTypesHierarchy](https://github.com/Husam-AbuZina/Mastering-JavaScript-in-20-Days/assets/109718076/bf338047-1901-4032-94a9-3600cf73d09e)


## Function Expression Solution: Functions

```jsx
// ---------------------- Normal funcitons ----------------------

function getStudentById(studentId) {
    return studentRecords.find(function matchId(record) {
        return record.id == studentId;
    });
}

function printRecords(recordIds) {
    var records = recordIds.map(getStudentById);
    
    records.sort(function sortByNameAsc(record1, record2) {
        if (record1.name < record2.name) {
            return -1;
        } else if (record1.name > record2.name) {
            return 1;
        } else {
            return 0;
        }
    });
    
    records.forEach(function printRecord(record) {
        console.log(`${record.name} (${record.id}): ${record.paid ? "Paid" : "Not Paid"}`);
    });
}

function paidStudentsToEnroll() {
    var idsToEnroll = studentRecords.filter(function needsToEnroll(record) {
        return (record.paid && !currentEnrollments.includes(record.id));
    }).map(function getStudentId(record){
        return record.id;
    });
    
    return [...currentEnrollments, ...idsToEnroll];
}

function remindUnpaid(recordIds) {
    var unpaidIds = recordIds.filter(function isUnpaid(studentId) {
        var record = getStudentById(studentId);
        return !record.paid;
    });
    
    printRecords(unpaidIds);
}
```

## Function Expression Solution: Arrow Functions

```jsx
// ---------------------- Arrow funcitons ----------------------

const getStudentById = (studentId) => studentRecords.find(record => record.id === studentId);

const printRecords = (recordIds) => {
    const records = recordIds.map(getStudentById);

    records.sort((record1, record2) => {
        if (record1.name < record2.name) {
            return -1;
        } else if (record1.name > record2.name) {
            return 1;
        } else {
            return 0;
        }
    });

    records.forEach(record => {
        console.log(`${record.name} (${record.id}): ${record.paid ? "Paid" : "Not Paid"}`);
    });
};

const paidStudentsToEnroll = () => {
    const idsToEnroll = studentRecords
        .filter(record => record.paid && !currentEnrollments.includes(record.id))
        .map(record => record.id);

    return [...currentEnrollments, ...idsToEnroll];
};

const remindUnpaid = (recordIds) => {
    const unpaidIds = recordIds.filter(studentId => {
        const record = getStudentById(studentId);
        return !record.paid;
    });

    printRecords(unpaidIds);
}
```

---

## Advanced Scope

### lexical scope:

 Decision I made at compile time.
 
###  dynamic scope:
   Decision I made at run time.

 ## IIFE Pattern
 
 IIFE : Immediately Invoked Function Expression.

 ![IIFE](https://github.com/Husam-AbuZina/Mastering-JavaScript-in-20-Days/assets/109718076/6d034625-3b88-42d8-9045-ca4b538cdff6)

- it does not start with the keyword “function”, that’s why it is called expression and not a function declaration.

```jsx
var teacher = "Kyle";

// this IIFE is anonymous : 
( function (teacher) {
   console.log(teacher); // Suzy
}) ("Suzy");

console.log(teacher);

// ------------------------------------------------------------

var teacher;
try {
   taecher = fetchTeacher(1);
}
catch (err) {
   teacher = "Kyle";
}

// ------------------------------------------------------------

var teacher = (function getTeacher() {
try {
   taecher = fetchTeacher(1);
}
catch (err) {
   teacher = "Kyle";
}
}) ();

```

## Block Scoping

```jsx
var teacher = "Kyle";

{
  let teacher = "Suzy"; // you can use them instead of a statement
  console.log(teacher);
}

console.log(teacher);

// -----------------------

function diff(x, y) {  // Just a tmp variable we won't use it later.
   if (x > y) {
      var tmp = x;
      x = y;
      y = tmp;
    }
   return y - x;
}
```

## const

```jsx
var teacher = "suzy";
teacher = "Kyle";   // OK

constmyTeacher =teacher;
myTeacher = "Suzy";    // TypeError

const teachers = ["Kyle", "Suzy"];
teachers[1] = "Brain";    // Allowed!  // Mutate the array even though it is const xD.

// const: for the rest of this block, i am not going to be re-assigned.

// Advice: use var -> let -> const // Advice of the author of the course, Kyle Simpson.
```


## Coding Exercises 👨‍💻

---

## Scope & Function Expressions:

- Question 1 💡

Create a function called arrowHOF that takes an arrow function as input and returns a new arrow function that enhances the behavior of the input function.

The enhanced function should accept additional arguments and execute the input function multiple times based on these arguments.
    
    
```jsx


const exampleNormalFunc1 = (a, b, c) => {
  return a * (b + c);
}

const exampleNormalFunc2 = (x, y) => {
  return x * y;
}

const exampleNormalFunc3 = (string) => {
  return string + " " + string + " " + string + "!";
}


const arrowHOF = (normalFunc) => {
  // write your code here;
}

const hofNormalFunc1 = arrowHOF(exampleNormalFunc1);
const hofNormalFunc2 = arrowHOF(exampleNormalFunc2);
const hofNormalFunc3 = arrowHOF(exampleNormalFunc3);

console.log(hofNormalFunc1(3, 4, 5)(2)); // logs 60 twice
console.log(hofNormalFunc2(20, 35))(4); // logs 700 four times
console.log(hofNormalFunc3("Meow")()); // logs "Meow Meow Meow!" once


```
  ### Solution: ✅
  
```jsx

const exampleNormalFunc1 = (a, b, c) => {
  return a * (b + c);
};

const exampleNormalFunc2 = (x, y) => {
  return x * y;
};

const exampleNormalFunc3 = (string) => {
  return string + " " + string + " " + string + "!";
};

const arrowHOF = (normalFunc) => {
  return (...args) => {
    return (count) => {
      let result = normalFunc(...args);
      for (let i = 1; i < count; i++) {
        console.log(result);
      }
      return result;
    };
  };
};

const hofNormalFunc1 = arrowHOF(exampleNormalFunc1);
const hofNormalFunc2 = arrowHOF(exampleNormalFunc2);
const hofNormalFunc3 = arrowHOF(exampleNormalFunc3);

console.log(hofNormalFunc1(3, 4, 5)(2)); // logs 60 twice
console.log(hofNormalFunc2(20, 35)(4)); // logs 700 four times
console.log(hofNormalFunc3("Meow")()); // logs "Meow Meow Meow!" once


```


- Question 1 💡
  
Create a function called arrowHOF that takes an arrow function as input and returns a new arrow function that enhances the behavior of the input function.

The enhanced function should accept additional arguments and execute the input function multiple times based on these arguments.
    
  ### Solution: ✅
    
```jsx



```

- Question 2 💡
  
Build a function called preserveThis that takes a function as input and returns a new arrow function that behaves the same way as the input function but preserves the original this context when used as a method of an object.
    

    
```jsx


// Example object
const obj = {
  name: 'John',
  greet: function (greeting) {
    console.log(`${greeting}, ${this.name}!`);
  }
};

const preserveThis = (func) => {
  // write your code here;
  return func;
}

// Wrap the greet function using preserveThis
const preservedGreet = preserveThis(obj.greet);

// Call the wrapped function as a method of the object
preservedGreet('Hello'); // Output: "Hello, John!"


```

  ### Solution: ✅

  ```jsx

const obj = {
  name: 'John',
  greet: function (greeting) {
    console.log(`${greeting}, ${this.name}!`);
  }
};

const preserveThis = (func) => {
  return func.bind(func.__this);
};

// Wrap the greet function using preserveThis
const preservedGreet = preserveThis(obj.greet);

// Call the wrapped function as a method of the object
preservedGreet('Hello'); // Output: "Hello, John!"


```

- Question 3 💡
  
Consider the 2 following examples and distinguish the different output in each one with them with a reasoning.

  ```jsx



```

Example 1:
      
    
```jsx

function outer1() {
  var x = 10;

  var inner1 = function() {
    console.log(x);
  };

  inner1();
}

outer1(); // Output: 10

```

  ### Solution Example 1: ✅

  ```jsx

// 20

```

Because, by returning the inner2 function from outer2, we create a closure that preserves access to the variable y, allowing us to invoke closureFunc() later and still access the value of y, which is 20.

Example 2:
      
    
```jsx

function outer2() {
  var x = 10;

  var inner2 = function() {
    var x = 20;
    console.log(x);
  };

  inner2();
}

outer2(); // Output: 20

```


  ### Solution Example 2: ✅

  ```jsx

// 20

```

Because, he inner function inner2 has its own local variable x, which is distinct from the outer variable x. When we invoke inner2() inside outer2, it logs the value of its local variable x, which is 20, due to variable shadowing. The outer variable x, defined in outer2, remains unaffected and retains its value 10.
