# Day 10:

## Summary of the course ✍️

## Types 

### primitive Types:

- “in JavaScript, everything is an object” is FALSE
- Truth is: everything in JS can behave like an object, but not everything is an object.

### Primitive Types

- undefined
- string
- number
- boolean
- object
- symbol

### What are these?

- undeclared?
- null?
- function?
- array?
- bigint?

---

### Typeof Operator

```javascript
typeof doesntEXist; // undefined

var v = null;
typeof v; // "object" // that is not true, it is a bug. be carful when you find typeof "object", accidently being null

v= function(){};  
typeof v;               // function

v = [1, 2, 3];          // object 
typeof v;
```
---

### undefined vs. undeclared. vs. uninitialized (aka TDZ)

### undeclared:

means the variable have never been created.

### uninitialized:

never initially set to undefined. and you cannot ever change it’s value

### undefined:

means there is a variable but at the moment has no value.


### Nan: is invalid number. (Not “not a number”) (it is a number, but an invalid one.)

NaN operationed with anything will only return another NaN.

```jsx
var myAge = Number("0o46");    // 38
var myNextAge = Number("39");  // 39
var myCatsAge = Number("n/a"); // NaN
myAge - "my son's age";        // Nan

myCatsAge === myCatsAge;       // false // OOPS! // deos not have the "identity" property -> does not equal to itself.
 
isNaN(myAge);                  // false
isNan(myCatsAge);              // true
isNan("my son's age");         // true // OOPS! // coers the value to a number before checking if it is a NaN type

Number.isNaN(myCatsAge);       // true // OOPS! // Tells us for sure if it's a NaN or not.
Number.isNan("my son's age";)  // false
```

### Negative Zero:

```jsx
var trendRate = -0;          // -0
trendRate === -0;            // true

trendRate.toString();        // "0" // OOPS! // when they made the languege, they thought it would be wierd to return a "-0" as a string and the developers will get confused. so they "Helped" the developers :D ?????
trendRate === 0;             // true // OOPS !
trendRate < 0;               // true
trendRate > 0;               // true

Object.is(trendRate, -0);    // true 
Object.is(trendRate, 0);     // false
```

### Use new:

- Object()
- Array()
- Function()
- Date()
- RegExp()
- Error()

### Don’t use new:

- String()
- Number()
- Boolean()


## Coding Exercises 👨‍💻

---

- Question 1 💡
    
// Some Question
    
  ### Solution: ✅
    
```jsx
// Solution in progress...
```
