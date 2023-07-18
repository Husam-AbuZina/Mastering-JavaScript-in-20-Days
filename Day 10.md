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
    
Write a function called convertStringToNumber that converts a string to a number using the unary plus operator.

If the input is not a string, return an object of the input's value and type.
    
  ### Solution: ✅
    
```jsx

function convertStringToNumber(input) {
  if (typeof input === 'string') {
    const number = +input; 
    if (!isNaN(number)) {
      return number;
    }
  }

  // -------------------------------------------------------------------------------
  // If input is not a string or couldn't be converted to a number, return an object with value and type
  // ---------------------------------------------------------------------------------

  return { value: input, type: typeof input };
}

// --------------------------- Examples ---------------------------
console.log(convertStringToNumber('42')); // Output: 42
console.log(convertStringToNumber('Hello')); // Output: NaN
console.log(convertStringToNumber(123)); // Output: { value: 123, type: 'number' }

```

---

- Question 2 💡
    
Write a function called checkNaN that takes a single argument and returns true if the argument is NaN and false otherwise.
    
  ### Solution: ✅
    
```jsx

const checkNaN = (value) => {
  if(isNaN(value)){
      return true;
  } else {
      return false;
  }
}




// --------------------------- Examples ---------------------------
checkNaN(9);
checkNaN('Husam');

console.log(checkNaN('Husam')); // true
console.log(checkNaN(9));  // false

```

---

- Question 3 💡
    
Write a function called isEmptyValue that checks if a given input is an empty value (undefined, null, or empty string).
    
  ### Solution: ✅
    
```jsx

function isEmptyValue(value) {
  return value === undefined || value === null || value === '';
}

// --------------------------- Examples ---------------------------
console.log(isEmptyValue(undefined)); // Output: true
console.log(isEmptyValue(null)); // Output: true
console.log(isEmptyValue('')); // Output: true
console.log(isEmptyValue('Hello')); // Output: false


```

---

- Question 4 💡
    
Write a function called isEmptyValue that checks if a given input is an empty value (undefined, null, or empty string).
    
  ### Solution: ✅
    
```jsx

function compareObjects(obj1, obj2) {
  if (typeof obj1 !== 'object' || typeof obj2 !== 'object') {
    return [obj1, obj2];
  }

  const keys1 = Object.keys(obj1);
  const keys2 = Object.keys(obj2);

  if (keys1.length !== keys2.length) {
    return false;
  }

  for (const key of keys1) {
    if (obj1[key] !== obj2[key]) {
      return false;
    }
  }

  return true;
}


// --------------------------- Examples ---------------------------
const person1 = { name: 'Husam', age: 20 };
const person2 = { name: 'Hani', age: 20 };
const person3 = { name: 'Sara', age: 30 };
const num1 = 66;
const num2 = 66;

console.log(compareObjects(person1, person2)); // Output: true
console.log(compareObjects(person1, person3)); // Output: false
console.log(compareObjects(num1, num2)); // Output: [66, 66]


```


