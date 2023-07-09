# Day 6:

## Summary of the course

---

## Coding Exercises

### [Use Higher-Order Functions map, filter, or reduce to Solve a Complex Problem](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/functional-programming/use-higher-order-functions-map-filter-or-reduce-to-solve-a-complex-problem)

#### My Solution 

```javascript
const squareList = arr => {
  // Only change code below this line

  const FilteredArray = arr.filter((number) => {
    return (number % 1 == 0 && number > 0);
  });

  const Result = FilteredArray.map(number => {
    return number * number;
  }) ;

  return Result;
  // Only change code above this line
};

const squaredIntegers = squareList([-3, 4.8, 5, 3, -3.2]);
console.log(squaredIntegers);
```

---



### [Apply Functional Programming to Convert Strings to URL Slugs](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/functional-programming/apply-functional-programming-to-convert-strings-to-url-slugs)

#### My Solution 

```javascript
// Only change code below this line
function urlSlug(title) {
  const words = title.toLowerCase().trim().split(/\s+/);
  const TitleWithHyphens = words.join("-");
  return TitleWithHyphens;
}
// Only change code above this line
urlSlug("A Mind Needs Books Like A Sword Needs A Whetstone");
```

---


### Question 1: 
Implement a JavaScript function called mapAsync that takes an array and a callback function. The function should map each element of the array to a new value using the callback function asynchronously.

The final result should be returned as a Promise.

#### My Solution 

```javascript
 const mapAsync = async (arr, callback) => {
  try {
    const result = await callback(arr);
    return result;
  } catch (error) {
    console.log("There is some error.", error);
  } finally {
    console.log("I will be executed anyways");
  }
};

const callback = (arr) => {
  return new Promise((resolve, reject) => {
    const mappedArray = arr.map((number) => {
      return number * number;
    });
    if (mappedArray) {
      resolve(mappedArray);
    } else {
      reject("Error has occurred");
    }
  });
};

const arr = [1, 2, 3, 4, 5];

mapAsync(arr, callback)
  .then((result) => {
    console.log(result);
  })
  .catch((error) => {
    console.error(error);
  });
```

---

### Question 2: 
Write a JavaScript function called sumRange that calculates the sum of all integers in a given range. The function should use recursion to handle the calculation and demonstrate understanding of the call stack.

#### My Solution 

```javascript
function sumRangee(start, end) {
  if (start === end) {
    return start;
  } else if (start < end) {
    return start + sumRangee(start + 1, end);
  } else {
    return end + sumRangee(end + 1, start);
  }
}

console.log(sumRangee(1, 5));
```

---
