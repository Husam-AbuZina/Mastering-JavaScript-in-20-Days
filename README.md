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

