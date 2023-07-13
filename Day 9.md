# Day 9:

## Summary of the course ✍️

### Classes & Prototypes:

#### Object Dot Notation

```javascript
const user1 = { // initialize object

name: "Will",
score: 3,
increment: function() { user1,score++; }
};

user1.increment();

// ---------------- Add properties later

const user2 = {}; // initialize empty object


user2.name = "Tim";
user.score = 6;
user2.increment = funciton() {
   user2.score++;
}
```

#### Factory Functions: Example

```javascript
// ----------------------- Breaking the DRY Principle ------------------------
// DRY : Don't Repeat Yourself

function userCreator(name, score) {
   const newUser = {};
newUser.name = name;
newUser.score = score;
newUser.increment = function() {
  newUser.score++;
};
  return newUser;
};

const user1 = userCreator("Will", 3);
const user2 = userCreator("Tim", 5);
user1.increment();

// ----------------------- Problem ------------------------
// The problem here that we always store a new function with the same code
// for each user.
```

#### Prototype Chain Example: Prototypal Link

```javascript
// ----------------------- Breaking the DRY Principle ------------------------
// DRY : Don't Repeat Yourself

function userCreator(name, score) {
const newUser = { Object.create(userFunctionStore) }; // Craete the object and bond it with userFunctionsTORE()
newUser.name = name;
newUser.score = score;
  return newUser;
};


// ----------------------- Problem  Solveed------------------------
const userFunctionStore = {
  newUser.increment = function() { newUser.score++; };
login: function() { console.log("Logged in"); }
};
// ----------------------- Problem  Solveed------------------------

const user1 = userCreator("Will", 3);
const user2 = userCreator("Tim", 5);
user1.increment();

```

#### Prototype Chain Example: Implicit Parameters ( this )

```javascript
// ----------------------- Breaking the DRY Principle ------------------------
// DRY : Don't Repeat Yourself

function userCreator(name, score) {
const newUser = { Object.create(userFunctionStore) }; // Craete the object and bond it with userFunctionsTORE()
newUser.name = name;
newUser.score = score;
  return newUser;
};


// ----------------------- Problem  Solveed------------------------
const userFunctionStore = {
  newUser.increment = function() { newUser.score++; };
login: function() { console.log("Logged in"); }
};
// ----------------------- Problem  Solveed------------------------

const user1 = userCreator("Will", 3);
const user2 = userCreator("Tim", 5);
user1.increment();
  
```

#### has Own Property Method

Note: Every Object in JS has a hidden property called “Proto” by default to link the objects to the “Object.prototype”

Note: Object.prototype has a Proto : null; Which breaks the chain.

```javascript

```
#### 

```javascript
// ----------------------- Breaking the DRY Principle ------------------------
// DRY : Don't Repeat Yourself

function userCreator(name, score) {
const newUser = { Object.create(userFunctionStore) }; // Craete the object and bond it with userFunctionsTORE()
newUser.name = name;
newUser.score = score;
  return newUser;
};


// ----------------------- Problem  Solveed------------------------
const userFunctionStore = {
  newUser.increment = function() { newUser.score++; };
login: function() { console.log("Logged in"); }
};
// ----------------------- Problem  Solveed------------------------

const user1 = userCreator("Will", 3);
const user2 = userCreator("Tim", 5);
user1.increment();

  
```
#### new Key Word ( function object combo → that what a function is )


#### Code1: 
```javascript
class userCretor {
constructor (name, score) {
  this.name = name;
  this.score = score;
}

increment () { this.score++; };
login () { console.log("login"); };
}
const user1 = new userCreator("Eva", 9)

user.increment()
```

```javascript
function userCretor(name, score) {
  this.name = name;
  this.score = score;
}

userCreator.prototype.increment = function(){ this.score++; };
userCreator.prototype.login = function() { console.log("login"); };

const user1 = new userCreator("Eva", 9)

user.increment()
```


### General Notes:


## Coding Exercises 👨‍💻

---

- Question 1 💡
    
Answer all the Object related questions in FreeCodeCamp.
    
    ### Solution: ✅
    

[OOP FreeCodeCamp Profile](www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/object-oriented-programming/)

    ---
