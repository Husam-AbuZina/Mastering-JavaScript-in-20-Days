# Mastering-JavaScript-in-20-Days

### DOM (Document Object model)

##### Finding Elements in a Web Page:
- document.title
- document.body
- document.body.children
- document.getElementById(”board”)
- document.querySelector(”#board”) // This can select IDs and Classes
- document.getElementByTagName(”h1”)
- document.querySelectorAll(”h1”)
- document.getElementByClassName(”player”)
- document.querySelectorAll(”.player”)

---

### Values & Data Types
- document.title
- document.body
- document.body.children
- document.getElementById(”board”)
- document.querySelector(”#board”) // This can select IDs and Classes
- document.getElementByTagName(”h1”)
- document.querySelectorAll(”h1”)
- document.getElementByClassName(”player”)
- document.querySelectorAll(”.player”)

### Index
- “Husam”[2] → S
- “Husam”.indexOf(”s”) → 2
- “Husam”.indexOf(”sa”) → 2
- “Husam”.indexOf(”F”) → -1 // If it does not exist it gives us -1.
- “Husam”.includers(”Hus”) → true
- Husam”.includers(”oo”) → false
- Husam”.startWith(”Hus”) → true
- Husam”.startWith(”us”) → false
- “Husam “ + “Abu Zina” → “Husam Abu Zina”  ( Concatenation )
  
---

### Operators

##### Operators
- typeof  →  Operator Gets us the data type of a variable
- +          →  Concatenate | Sum
- + - / *   ()
- **

##### Comparasion & Equality
- =     > =     < =
- = == === // = assign // == check value // === check value and type
- & || ++

---

### Expressions

###### What are Variables
Just a container for some value with a name of out creation.

##### Statements vs Expressions

Statement: are Actions.

Expression: are Values.

- let ten = 6 + 4; | Statement
- Arrays
- 4 / 2 * 10
- “Husam ” + “Abu Zina”

---

### Arrays

##### Arrays 
- let arr = [ ”Husam”, “Sandy”, “Bob”];
- let lastItem = arr.pop();
- console.log(lastItem) → Bob
- console.log(lastItem) → [ Husam, Sandy]
- let mixedArray = [ ”Husam”, 6 , SomeObj];

  ##### Mutability
  - Mutable → Array
  - Immutable → Strings & other primitives
 
  ##### Mutable & immutable Data Exercise
  Example1:

- let numbers1 = [1, 2, 3];
- let result1 = numbers1.push(4);
- numbers1 = [1, 2, 3, 4]                                    |  Original array Changed
- let numbers1 = [1, 2, 3];
- let result1 = numbers1.concat(4);
- numbers1 = [1, 2, 3]                                        | Original array UnChanged

  #### Example :
  
  let array1 = [1, 2, 3];
  let array2 = array1;
  array1[2] = 999;
  console.log(array2) // [1, 2, 999]

---

### Objects
When we change an attribute value, it changes the original values in the original object.

###### Example:

let Human = {
name: "Husam",
age: 20,
city: "Hebron"
};

Human.name // Husam

###### Example(2): ( Build-in Objects )

- Math.pi // will give us 3.14 constant
- Math.random() // will give us a random number from 0 - 1

  ---

  ### Functions
Group of lines of code that are executed on demand!.

### Normal Functions:

#### Example:

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

#### Example(2):

const divide = (x, y) => { // Has no name and are uses Arrow
return x/y;
}

const whisper = (x) => {
return x.toLowerCase();
}

const shorterThan = (arr1, arr2) => {
return arr1.length > arr2.length
}

---

### Event Listeners

##### Event Listeners:
- Event Listeners is in short, a function we tie to some element to do a certain action when clicked or howverd over or the user interacted with it in some way...
  
##### Example:
document.addEventListener("click", () => {
console.log("clicked! ");
});

##### Event object
document.addEventListener("click", (event) => {
console.log(event.target);
});

- “click”
- “dblclick”
- “mouseover”
- “mouseout”
- …

---

### Conditionals
Definition: is user made conditions to control the flow of the program excurtion depending on the variables it faces.

##### Example:
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

##### Example:

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

### Map & Filter

##### Filter()
Simply, Filters the array!.
it makes a new array with the conditioned elements only.

Example:

const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

const oddNumbers = numbers.filter((num) => num % 2 !== 0);
console.log(oddNumbers); // Output: [1, 3, 5, 7, 9]

##### Map()
It maps each element into a function written by us, and make changes to each element. Then Creates a new array with these new modified elemnts.

Example:

const numbers = [1, 2, 3, 4, 5];
const doubledNumbers = numbers.map((num) => num * 2);
console.log(doubledNumbers); // Output: [2, 4, 6, 8, 10]

##### spread Operator (...):

Example:
console.log(skills); // ["HTML", "CSS", "JS"]
console.log(...skills); // HTML CSS JS

---

### Data Fetching & Promises
fetch() // get info from JSON array.

##### Example:
let response = await fetch(”https://dog.ceo/api/breed/hound/list”)

console.log(response);

response.json();


let response = await fetch(”https://dog.ceo/api/breed/hound/list”)
let body = await response.json();

fetch(”https://dog.ceo/api/breed/hound/list”).then((value) => console.log(value));
 
---

### Destructing Data
Definitnion: Get a spicific piece of data from a group of data structure.

##### Example:
Note: Object properties are not ordered.
	const spices = [
  {name: "Emma", nickname: "Baby"},
]

let { name, nickname } = spices[0];

name -> "Emma"
nickname -> "Baby"

let {nickname} = spices[0];

---

Note: Array properties are ordered.

let [one, two, three] = [1, 2, 3]

let [ten, twenty] = [10, 20, 30, 40, 50]

ten -> 10
twenty -> 20

const [,,thirty] = [10, 20 30, 40] // Commas skip info in arrays

thirty -> 30


cosnt [one, ...others] = [1, 2, 3, 4]

one -> 1
others -> [2, 3, 4 ]

  ---
  
  ### Scope
  * If two Variabels has the same name (Global, Local), Local variables take the precedence.
  * A variable decleared inside a finction is a local variable inside the variable block, and the program cannot 
    recognize the variable outside the function's scope.
  * Create a simple function with the return statement
    Example:
    
    function timesFive (x) {
  return x * 5;
}
// Learned about creating a simple function in JS.

* Use special functions to manipulate arrays's data easily.
  EXample:

  function nextInLine(arr, item) {
  arr.push(item);
  return arr.shift();
}

---

### Compund Operator
1. Concatenating Strings
Example:

let Info = "The Sky is Blue? ";
Info += ",Because of the special gases in the atmosphere that interacts with the light coming from sun, Different gases may could have gave us a purple Sky O_O  :D";

2. Short cut for simple arithmatic operations
   
   Example:
   x = x + 99;
   is completly equal to
   x += 99;
   This will matter more the larger your proram are.

4. Bracket Notation

   Examples:
   // Setup
const lastName = "Lovelace";
const secondToLastLetterOfLastName = lastName[lastName.length - 2];

// This will get a certain element in the array of characteres, in or case it is the letter "s".

---

  ### Scope
  * If two Variabels has the same name (Global, Local), Local variables take the precedence.
  * A variable decleared inside a finction is a local variable inside the variable block, and the program cannot recognize the variable outside the function's scope.
  * Create a simple function with the return statement
    Example:
    
    function timesFive (x) {
  return x * 5;
}
// Learned about creating a simple function in JS.

* Use special functions to manipulate arrays's data easily.
  EXample:

  function nextInLine(arr, item) {
  arr.push(item);
  return arr.shift();
}

---
  
### Async





