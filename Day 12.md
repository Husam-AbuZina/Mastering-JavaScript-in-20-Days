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

## STATIC TYPING QUESTIONS:

- Question 1 💡
    
Given the following promisesArray, convert the array into an object using the convertToObj function.

You should apply typescript types to every promise, the input of convertToObj, and the output of convertToObj.

Build interfaces and types as needed.
    
  ### Solution: ✅
    
```jsx

// Define the interface for the element of an array of promises
interface PromiseItem {
  identifier: string;
  promise: Promise<any>;
}

// Define the interface for the output object
interface OutputObject {
  [key: string]: any;
}

// Define the input type for the convertToObj function
type PromisesArray = PromiseItem[];

// Define the convertToObj function
async function convertToObj(promisesArray: PromisesArray): Promise<OutputObject> {
  const result: OutputObject = {};

  await Promise.all(
    promisesArray.map(async ({ identifier, promise }) => {
      result[identifier] = await promise;
    })
  );

  return result;
}

// Example usage
const arrayOfPromises: PromisesArray = [
  { identifier: 'one', promise: Promise.resolve(1) },
  { identifier: 'two', promise: Promise.resolve(2) },
  { identifier: 'three', promise: Promise.resolve(3) },
];

convertToObj(arrayOfPromises).then((result) => {
  console.log(result); // Output: { one: 1, two: 2, three: 3 }
});

```

---

## SCOPE & HOISTING QUESTIONS:

- Question 1 💡
    
What will be the output of the following code snippet? Pick the right choice then justify your answer with an explanation.
    
```jsx

function testScope1() {
  if (true) {
    var a = 1;
    let b = 2;
    const c = 3;
  }
  console.log(a);
  console.log(b);
  console.log(c);
}

testScope1();

```

## Choices:

A) undefined, undefined, undefined
B) 1, undefined, ReferenceError
C) 1, ReferenceError, ReferenceError
D) 1, ReferenceError

  ### Solution: ✅
  
C) 1, ReferenceError, ReferenceError

 Because, variable "a" is declared as var, which can be hoisted iwth scope of global even before the interpeter reaches it, it's value is in the memory at the compile time.

---

- Question 2 💡
    
Write a function called isEmptyValue that checks if a given input is an empty value (undefined, null, or empty string).
    
```jsx

function testScope2() {
  console.log(a);
  console.log(b);
  console.log(c);
  if (true) {
    var a = 1;
    let b = 2;
    const c = 3;
  }
}

testScope2();

```

### Choices:

A) undefined, ReferenceError
B) 1, undefined, ReferenceError
C)undefined, undefined, ReferenceError
D) 1, ReferenceError

  ### Solution: ✅
  
C)undefined, undefined, ReferenceError

 Both a and b are hoisted to the top of their respective scopes, but only the var variable a is initialized with undefined. The let variable b and the const variable c remain in the temporal dead zone and are not accessible before their declarations.


---

- Question 3 💡
    
Write a function called isEmptyValue that checks if a given input is an empty value (undefined, null, or empty string).
    
```jsx


function testScope3() {
  var a = 36;
  let b = 100;
  const c = 45;

  console.log([a, b, c]);

  if (true) {
    var a = 1;
    let b = 2;
    const c = 3;

    console.log([a, b, c]);
  }

  console.log([a, b, c]);
}

testScope3();


```
    
  ### Solution: ✅

  B) [ 36, 100, 45 ] | [ 1, 2, 3 ] | [ 36, 100, 45 ]

the output will be [36, 100, 45] (for the first console.log), [1, 2, 3] (for the second console.log inside the if block), and [36, 100, 45] (for the third console.log after the if block).
