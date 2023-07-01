# Mastering-JavaScript-in-20-Days

Arrays
* How to Concatenate Arrays using the "Spread Operator"
  Example:
  function spreadOut() {
  let fragment = ['to', 'code'];
  let sentence = ['learning', ...fragment, 'is', 'fun'];
  return sentence;
}

console.log(spreadOut());

* Prtitioning the Array using the "Slice()" funciton.
  Example:
  
function forecast(arr) {
  let weather = arr.slice(2, 4); 

  return weather;
}

// Only change code above this line
console.log(forecast(['cold', 'rainy', 'warm', 'sunny', 'cool', 'thunderstorms']));
  
