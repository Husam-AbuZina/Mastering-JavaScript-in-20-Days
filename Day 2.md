
# Day 2:

## Summary of the course ✍️

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

### Arrow Functions:

### Example(2):

const divide = (x, y) => { // Has no name and are uses Arrow
return x/y;
}

const whisper = (x) => {
return x.toLowerCase();
}

const shorterThan = (arr1, arr2) => {
return arr1.length > arr2.length
}

### Conditionals

Definition: is user made conditions to control the flow of the program excurtion depending on the variables it faces.

### Example:

if(age < 20) {
console.log("You Are young!");
} else if {
console.log("You are old!");
} else {
console.log("You are old!");
}

### Logical & Ternary Operators

if (!happy) {
console.log("drink coffee");
}

&& // Both conditions must be satisfied to get the result.
|| // At least one condition must ve satisfied to get the result.
! // Negation Operator. !false = true // !true = false

### Loops

Definition: loops let you execute lines of code repeatdly without the need to rewrite all these lines of code.

### Example:

const numbers = [1, 2, 3];

for (let i = 0; i < numbers.length; i++) {
console.log(numbers[i]);
}

### Conditional Ternary Operators

Is simply a short cut for a conditional if else / else if statements!

Example:

const Major_Years = 4;
const isProgrammer = Major_Years = 5 ? "Computer Engineer" : "Computer Scientist";

console.log(isProgrammer); // Output: "Computer Scientist"

---

---

## Coding Exercises 👨‍💻

### [Profile Lookup](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/profile-lookup)

#### My Solution ✅

```javascript
// Setup
const contacts = [
  {
    firstName: "Akira",
    lastName: "Laine",
    number: "0543236543",
    likes: ["Pizza", "Coding", "Brownie Points"],
  },
  {
    firstName: "Harry",
    lastName: "Potter",
    number: "0994372684",
    likes: ["Hogwarts", "Magic", "Hagrid"],
  },
  {
    firstName: "Sherlock",
    lastName: "Holmes",
    number: "0487345643",
    likes: ["Intriguing Cases", "Violin"],
  },
  {
    firstName: "Kristian",
    lastName: "Vos",
    number: "unknown",
    likes: ["JavaScript", "Gaming", "Foxes"],
  },
];

function lookUpProfile(name, prop) {
  for (let i = 0; i < contacts.length; i++) {
    if (contacts[i].firstName === name) {
      if (contacts[i].hasOwnProperty(prop)) {
        return contacts[i][prop];
      } else {
        return "No such property";
      }
    }
  }
  return "No such contact";
}

console.log(lookUpProfile("Akira", "likes")); // Output: ["Pizza", "Coding", "Brownie Points"]


```

---



### [Copy Array Items Using slice()](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-data-structures/copy-array-items-using-slice)

#### My Solution ✅

```javascript

function forecast(arr) {
  let weather = arr.slice(2, 4);  // Only change code below this line

  return weather;
}

// Only change code above this line
console.log(forecast(['cold', 'rainy', 'warm', 'sunny', 'cool', 'thunderstorms']));

```

---


### [Combine Arrays with the Spread Operator](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-data-structures/combine-arrays-with-the-spread-operator)

#### My Solution ✅

```javascript
function spreadOut() {
  let fragment = ['to', 'code'];
  let sentence = ['learning', ...fragment, 'is', 'fun']; // Change this line
  return sentence;
}

console.log(spreadOut());
```

---

