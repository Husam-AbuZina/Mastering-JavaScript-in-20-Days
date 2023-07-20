# Day 11:

## Summary of the course ✍️

# Static Typing

### Typescript & Flow

##### Benefits:

1. catch type-related mistakes.
2. Communicate type intent.
3. Provide IDE feedback

##### Caveats:

1. Inferencing is best-guess, not a gurunted.
2. Annotations are optional.
3. Any part of the application that isn’t  typed introduce uncertainty.

## Validating Operand Types

Validation of the subtraction operand:


```jsx
var studentName: string = "Franl";

var studentCount: number = 16 - studentName; // ERROR: can't subtract string
```

## Static Typing Pros
- They make types moee obvious in code.
- Familiarity: they look like other language’s type systems. ( like other languages )
- Extremely popular these days.
- They’re very sophisticated and good at what they do.

  ## Static Typing Cons
- They use “non-JS-standard” syntax .( or code comments )
- They require a build process, which raises the barrier to entry. ( it is just nice to run cod e right away )
- Their sophistication can be intimidating to those without prior formal types experience. ( syntax become so unfamiliar over time and complexity of using them )
- They focus more on “static types” (variables, parameters, returns, properties, etc) than value types. ( they seem to unrespect JS and changing it’s nature! )

## Understanding Your Types
- You simply cannot write quality JS programs without knowing the types involved in your ooperatios.
- Alternately, many choose to adopt a different “static types” systems layered on top while certainly helpful in some respects, this is “avoidance” of a different sort

---

# Scope

### Scope:

is where to look for things (Varibles, Functions, ...)

### Compilation & Scope:

- Red Circle = Global Scope.
- Blue Circle = otherClass Scope.
- Green Circle = ask() Scope.

![Pockets_explaing](https://github.com/Husam-AbuZina/Mastering-JavaScript-in-20-Days/assets/109718076/287bbd82-c95c-4fe9-89b7-611239a17746)

### Shadowing:

is when Two variables have the same name but different scopes.

### TypeError:

Illegal to execute an undefined function.

### RunTimeError:

Value that is not allower for that type.

## Lexical Scope:

- Red Circle = Global Scope.
- Blue Circle = otherClass Scope.
- Green Circle = ask() Scope.


![Scope](https://github.com/Husam-AbuZina/Mastering-JavaScript-in-20-Days/assets/109718076/7f9751fd-ee75-4184-8f9f-32530dbe0bee)

## Nested Scope

- Red Circle = Global Scope.
- Blue Circle = otherClass Scope.
- Green Circle = ask() Scope.

![NestedScope](https://github.com/Husam-AbuZina/Mastering-JavaScript-in-20-Days/assets/109718076/096f4f28-9167-4c48-8aad-589c32d63503)


## Undefined Vs. Undeclared

### Undefined:

Exist and has no value.

### Undeclared:

Does not exist and has no value. ( Never formally declared. we has no marble for them. )


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
    
  ### Solution: ✅
    
```jsx

// Code in pogress

```


