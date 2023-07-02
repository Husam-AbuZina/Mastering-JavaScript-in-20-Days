# Mastering-JavaScript-in-20-Days

# Compund Operator
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
# Arrays
* How to Concatenate Arrays using the "Spread Operator"
  Example:
  function spreadOut() {
  let fragment = ['to', 'code'];
  let sentence = ['learning', ...fragment, 'is', 'fun'];
  return sentence;
}
console.log(spreadOut());
---
* Prtitioning the Array using the "Slice()" funciton.
  Example:
function forecast(arr) {
  let weather = arr.slice(2, 4); 

  return weather;
}

// Only change code above this line
console.log(forecast(['cold', 'rainy', 'warm', 'sunny', 'cool', 'thunderstorms']));

  ---
  # Scope
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

// Setup
let testArr = [1, 2, 3, 4, 5];

// Display code
console.log("Before: " + JSON.stringify(testArr));
console.log(nextInLine(testArr, 6));
console.log("After: " + JSON.stringify(testArr));
//I learned how to manipulate items in the array

//Note: The best in this Doc's Orientation is yet to come...
---
# Filter()
Simply, Filters the array!.
it makes a new array with the conditioned elements only.

Example:

const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

const oddNumbers = numbers.filter((num) => num % 2 !== 0);
console.log(oddNumbers); // Output: [1, 3, 5, 7, 9]

---
# Map()
It maps each element into a function written by us, and make changes to each element. Then Creates a new array with these new modified elemnts.

Example:

const numbers = [1, 2, 3, 4, 5];
const doubledNumbers = numbers.map((num) => num * 2);
console.log(doubledNumbers); // Output: [2, 4, 6, 8, 10]

---
# Conditional Ternary Operators
Is simply a short cut for a conditional if else / else if statements!

Example:

const Major_Years = 4;
const isProgrammer = Major_Years = 5 ? "Computer Engineer" : "Computer Scientist";

console.log(isProgrammer); // Output: "Computer Scientist"



