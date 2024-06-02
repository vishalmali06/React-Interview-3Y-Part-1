# React-Interview-3Y-Part-1
## JavaScript Questions
### 1.Question: Explain the concept of closures in JavaScript. Provide an exampl?
    Answer: A closure is a feature in JavaScript where an inner function has access to the outer (enclosing) function's variables, even after the outer function has returned.
```javascript
function outerFunction() {
    let outerVariable = 'I am from outer scope';

    function innerFunction() {
        console.log(outerVariable);
    }

    return innerFunction;
}

const myInnerFunction = outerFunction();
myInnerFunction(); // Output: I am from outer scope
```
### 2.Question: What is the event loop in JavaScript and how does it work?
    Answer: The event loop is a mechanism that allows JavaScript to perform non-blocking operations, despite being single-threaded. It uses a queue, where asynchronous operations are placed, and a call stack, where the code is executed. The event loop checks the queue and moves tasks to the call stack when it is empty.

### 3.Question: Given an array of numbers, write a function to find the second largest number?
```javascript
function secondLargest(arr) {
    let first = -Infinity, second = -Infinity;
    for (let num of arr) {
        if (num > first) {
            second = first;
            first = num;
        } else if (num > second && num < first) {
            second = num;
        }
    }
    return second;
}
console.log(secondLargest([10, 20, 4, 45, 99])); // Output: 45
```
### 4.Question: Explain how this keyword works in JavaScript with an example?
    Answer: The this keyword refers to the object it belongs to. It has different values depending on where it is used. In a method, this refers to the owner object. In a function, this refers to the global object (or undefined in strict mode).
    
```javascript
const obj = {
    name: 'John',
    getName: function() {
        console.log(this.name);
    }
};
obj.getName(); // Output: John

function show() {
    console.log(this);
}
show(); // Output: [object Window] (or undefined in strict mode)
```

### 5.Question: Write a function to debounce a given function?
```javascript
function debounce(func, wait) {
    let timeout;
    return function(...args) {
        clearTimeout(timeout);
        timeout = setTimeout(() => func.apply(this, args), wait);
    };
}
const debouncedFunc = debounce(() => console.log('Debounced!'), 1000);
window.addEventListener('resize', debouncedFunc);
```
