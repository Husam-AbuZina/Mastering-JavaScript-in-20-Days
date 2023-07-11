# Day 7:

## Summary of the course ✍️

### Closure:
Is a function that remembers it’s previous runs.

```javascript
// const Closure = outer()
// fun() = inner() // with permanent memory.

// -------------------------- Example: --------------------------
function  Outer(){
    
    let counter= 0;
    
    function Inner(){
        counter++;
        return counter;
    }
    
    return Inner;
    
}

const squared = Outer(); // Has it's own BackBag


console.log(squared()); // 1
console.log(squared()); // 2

const third = Outer(); // Has it's own BackBag, That's why it started from 0 again.

console.log(third()); // 1
console.log(third()); // 2


// --------------------- OutPut ---------------------

1
2
1
2

```

### General Notes:

1. Call Stack. ( global() THEN ->  Function() THEN -> SomeOtherFunction() )
2. Execution Context. ( scope inside the function )
3. BackBag ( Each Closure saved variables are stored in a BackBag of their Own )


## Coding Exercises 👨‍💻

---

- Question 1 💡
    
    Write a closure named createCounter that takes an initial value start and returns a function. The returned function, when invoked, should increment the counter by 1 and return the updated value.
    
    ### Solution: ✅
    
    ```jsx
    function OuterFunc () {
      function increment(counter) {
          counter++
        return counter;  
      };
        return increment;
    };
    
    const createCounter = OuterFunc();
    console.log(createCounter(9)); // 10  :)
    ```
    
- Question 2 💡
    
    Write a closure named calculateAverage that takes an array of numbers, nums, and returns a function. The returned function, when invoked, should calculate and return the average of the numbers in the array.
    
    ### Solution: ✅
    
    ```jsx
    function calAvg() {
      function avg(nums) {
        let sum = 0;
        for (let i = 0; i < nums.length; i++) {
          sum += nums[i];
        }
        const average = sum / nums.length;
        return average;
      }
    
      return avg;
    }
    
    const calculateAverage = calAvg();
    console.log(calculateAverage([5, 5, 5, 5, 5])); // 5  :)
    ```
    
- Question 3 💡
    
    Write a closure named powerOf that takes a base number base and returns a function. The returned function, when invoked with an exponent exp, should calculate and return the result of base raised to the power of exp.
    
    ### Solution: ✅
    
    ```jsx
    function result() {
      function exponent(base) {
        let exp = 3;
        return Math.pow(base, exp);
      }
      return exponent;
    }
    
    const powerOf = result();
    console.log(powerOf(3)); // 27  :)
    ```
    
- Question 4 💡
    
    Write a closure named compose that takes multiple functions as arguments and returns a new function. The returned function should apply the provided functions in reverse order, passing the result of each function as an argument to the next function.
    
    ### Solution: ✅
    
    ```jsx
    function outer() {
        
        function callback1 (x) {
            return x + x;
        }
        
        function callback2 (x) {
            return x + x;
        }
        
        function callback3 (x) {
            return x + x;
        }
        
      function callback(callback1, callback2, callback3) {
          return function (y){
          let a = callback3(y);
          let b = callback2(a);
          let c = callback1(b);
          
          return c;
          };
      }
      
      return callback(callback1, callback2, callback3);
    }
    
    const compose = outer();
    console.log(compose(2)); // 16  :)
    ```
