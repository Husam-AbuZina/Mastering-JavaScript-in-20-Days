# Day 8:

## Summary of the course ✍️

### Asynchronous JavaScript:

```javascript
function printHello() {
    console.log("Hello");
}

setTimeout(printHello, 1000);

console.log("Me first!");

// --------------- OutPut -------------

// Me first!
// Hello
```

```javascript
function printHello() {
    console.log("Hello");
}

setTimeout(printHello, 0);

console.log("Me first!");

// --------------- OutPut ------------- // The same output?? Why???

// Me first!
// Hello
```

#### here is why:

##### Browser Features:

1. sockets
2. Network requests ( Fetch() )
3. HTML DOM ( document )
4. Timer ( setTimeout() )
5. Console


```javascript
function printHello() { console.log("Hello"); }
function blockFor1Sec() {
}

setTimeout(printHello, 0);

blockFor1Sec();
console.log("Me first!");

// --------------- OutPut ------------- Still the same result! <3
// Because, it is the time for (printHello() to get from the callback Queue 
// to the Call stack Queue)
// Once Call Stack is Empty,
// Then we can send the function the CallBack Queue to the Call Stack.

// --------------- This Feature is known as the "EVENT LOOP" ------------- 

// Me first!
// Hello
```

---

### Promises:

#### Fetch()
1. Initiate  background web browser work 
2. return a placeholder object  ( Promise ) immediately in JavaScript

```javascript
function display(data) {
   console.log(data)
}

const futureData = fetch('https://twitter.com/will/tweets/l');
futureData.then(display); // the fullfilled array object value will be 
//  the "display" word.

	console.log("Me first!"); 
```


```javascript
function display(data) { console.log(data);}
function printHello() { console.log("Hello"); }

setTimeout(printHello, 0);

const futureData = fetch('https://twitter.com/will/tweets/l');
futureData.then(display); // the fullfilled array object value will be 
//  the "display" word.]

// Attributes of Object of fetch is (value: , onFullFilled:[])

// as soon as the value attribute is updated,
//  will trigger the function inside the onFullFill Array.

// fetch web browser, wil ltake the 1. Domain name , 2. the path of the folder.

// the value of the background operation will be updated 
// when the backgorund browser operation is completed.

// .then function will run the function inside it, inside the onFullFill Array.

// Prioriy first better for the ( main thread, then for the Callback Queue )

// Microtask Queue has the display funciton.

// Microtask Queue has the most priority to go the global queue more than
// Callback Queue.


// Global Queue: is the main thread and has the highest priority.

// Microtask Queue: is the second priority to go to the main thread ( Globa Queue )
// it contains the functions that comes as a result of a promise.

 // Callback Queue: is the third priority to go to the main thread ( Global Queue )
 // it contains the functions that comes as a result of the background browser operations.
  blockFor300ms()
	console.log("Me first!"); 
```

### General Notes:


## Coding Exercises 👨‍💻

---

- Question 1 💡
    
    You are given a function `executeInSequenceWithCBs` and some code. The task is to modify the `executeInSequenceWithCBs` function so that it runs and executes all the tasks inside the asyncTasks array.

The function should return an array of messages obtained from each task's execution.

You are only allowed to change the `executeInSequenceWithCBs` function or add new functions/code. You cannot modify the tasks' functions.
    
    ### Solution: ✅
    
    ```jsx
    // Online Javascript Editor for free
// Write, Edit and Run your Javascript code using JS Online Compiler

const task1 = (cb) => setTimeout(() => {
  const message = "Task 1 has executed successfully!";
  cb(message);
}, 3000)

const task2 = (cb) => setTimeout(() => {
  const message = "Task 2 has executed successfully!";
  cb(message);
}, 0)

const task3 = (cb) => setTimeout(() => {
  const message = "Task 3 has executed successfully!";
  cb(message);
}, 1000)

const task4 = (cb) => setTimeout(() => {
  const message = "Task 4 has executed successfully!";
  cb(message);
}, 2000)

const task5 = (cb) => setTimeout(() => {
  const message = "Task 5 has executed successfully!";
  cb(message);
}, 4000)

const asyncTasks = [task1, task2, task3, task4, task5];

const executeInSequenceWithCBs = (tasks, callback) => {
  const results = []; // Array to store the results of each task

  // Helper function to execute a task and return a promise
  const executeTask = (task) => {
    return new Promise((resolve) => {
      task((result) => {
        results.push(result);
        console.log(`Task ${results.length} completed!`); // Print completion message
        resolve();
      });
    });
  };

  // Execute tasks in sequence using async/await
  (async () => {
    for (const task of tasks) {
      await executeTask(task);
    }

    // All tasks completed, invoke the final callback with the results
    callback(results);
  })();
};



executeInSequenceWithCBs(asyncTasks, (results) => {
  console.log("All tasks completed!");
  console.log(results);
});
    ```
    
- Question 2 💡
    
    You are given a function called `executeInParallelWithPromises`, which takes an array of APIs (represented by objects).

Your task is to write code that fetches the data of each API in parallel using promises. In Parallel means that the api which resolves first, returns its value first, regardless of the execution order.

The output of the `executeInParallelWithPromises` function should be an array containing the results of each API's execution.

Each result should be an object with three keys: `apiName`, `apiUrl`, and `apiData`..
    
    ### Solution: ✅
    
    ```jsx
   const executeInParallelWithPromises = (apis) => {
  const promises = apis.map((api) =>
    fetch(api.apiUrl)
      .then((response) => response.json())
      .then((data) => ({
        apiName: api.apiName,
        apiUrl: api.apiUrl,
        apiData: data,
      }))
  );

  return Promise.all(promises);
};

const apis = [
  {
    apiName: "products",
    apiUrl: "https://dummyjson.com/products",
  },
  {
    apiName: "users",
    apiUrl: "https://dummyjson.com/users",
  },
  {
    apiName: "posts",
    apiUrl: "https://dummyjson.com/posts",
  },
  {
    apiName: "comments",
    apiUrl: "https://dummyjson.com/comments",
  },
];

executeInParallelWithPromises(apis)
  .then((results) => console.log(results))
  .catch((error) => console.error(error));
    ```
    
- Question 3 💡
    
    You are given a function called `executeInSequenceWithPromises`, which takes an array of APIs (represented by objects).

Your task is to write code that fetches the data of each API sequentially (one after the other) using promises.

In Sequence means that the api which executes first, returns its value first.

The output of the `executeInSequenceWithPromises` function should be an array containing the results of each API's execution.

Each result should be an object with three keys: `apiName`, `apiUrl`, and `apiData`.
    
    ### Solution: ✅
    
    ```jsx
// Solution in Progress [To-Do Question]
    ```

    ---
