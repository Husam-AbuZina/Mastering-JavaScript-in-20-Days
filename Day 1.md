
# Day 1:

## Summary of the course ✍️

### DOM (Document Object model)

### Finding Elements in a Web Page:

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
- “Husam “ + “Abu Zina” → “Husam Abu Zina” ( Concatenation )

---

### Operators

### Operators

- typeof → Operator Gets us the data type of a variable
- `→ Concatenate | Sum`
- / * ()
- *

### Comparasion & Equality

- = > = < =
- = == === // = assign // == check value // === check value and type
- & || ++

---

### Expressions

### What are Variables

Just a container for some value with a name of out creation.

### Statements vs Expressions

Statement: are Actions.

Expression: are Values.

- let ten = 6 + 4; | Statement
- Arrays
- 4 / 2 * 10
- “Husam ” + “Abu Zina”

---

## Coding Exercises 👨‍💻

### [Compound Assignment With Augmented Multiplication](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/compound-assignment-with-augmented-multiplication)

#### My Solution ✅

```javascript
let a = 5;
let b = 12;
let c = 4.6;

// Only change code below this line
a *= 5;
b *= 3;
c *= 10;

```

---



### [Concatenating Strings with the Plus Equals Operator](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/concatenating-strings-with-the-plus-equals-operator)

#### My Solution ✅

```javascript
let myStr="This is the first sentence. ";

myStr += "This is the second sentence.";

```

---


### [Use Bracket Notation to Find the Nth-to-Last Character in a String](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/use-bracket-notation-to-find-the-nth-to-last-character-in-a-string)

#### My Solution ✅

```javascript
// Setup
const lastName = "Lovelace";

// Only change code below this line
const secondToLastLetterOfLastName = lastName[lastName.length - 2];

```

---

