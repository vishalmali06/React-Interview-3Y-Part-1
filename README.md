# React-Interview-3Y-Part-1
## JavaScript Questions
### 1.Question: Explain the concept of closures in JavaScript. Provide an exampl ?
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
