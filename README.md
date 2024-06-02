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
## React Questions
### 1.Question: Explain the difference between state and props in React?

    Answer: State is a local data storage that is private to a component and can be changed within the component. Props are read-only data that are passed from a parent component to a child component. Props cannot be modified by the receiving component.

### 2.Question: How would you handle state management in a large-scale React application?

    Answer: In a large-scale React application, state management can be handled using libraries like Redux or Context API. These tools allow for centralized state management and help to maintain a single source of truth, making it easier to manage and debug state changes across the application.

### 3.Question: Write a React component that fetches data from an API on mount and displays it?

```javascript
import React, { useEffect, useState } from 'react';

function DataFetcher() {
    const [data, setData] = useState([]);
    const [loading, setLoading] = useState(true);

    useEffect(() => {
        fetch('https://jsonplaceholder.typicode.com/posts')
            .then(response => response.json())
            .then(data => {
                setData(data);
                setLoading(false);
            });
    }, []);

    if (loading) {
        return <div>Loading...</div>;
    }

    return (
        <div>
            <ul>
                {data.map(item => (
                    <li key={item.id}>{item.title}</li>
                ))}
            </ul>
        </div>
    );
}

export default DataFetcher;
```

### 4.Question: What are hooks in React? Name a few commonly used hooks?

    Answer: Hooks are functions that let you use state and other React features without writing a class. Commonly used hooks include useState for managing state, useEffect for side effects, useContext for context API, and useReducer for complex state management.

### 5.Question: Explain the purpose of useEffect hook and provide an example of its usage?

    Answer: The useEffect hook allows you to perform side effects in function components. It's equivalent to lifecycle methods like componentDidMount, componentDidUpdate, and componentWillUnmount in class components.
    
```javascript
import React, { useState, useEffect } from 'react';

function Timer() {
    const [seconds, setSeconds] = useState(0);

    useEffect(() => {
        const interval = setInterval(() => {
            setSeconds(prevSeconds => prevSeconds + 1);
        }, 1000);

        return () => clearInterval(interval);
    }, []);

    return (
        <div>
            Seconds: {seconds}
        </div>
    );
}

export default Timer;
```

## HTML Questions

### 1.Question: What are the new form input types introduced in HTML5?

    Answer: HTML5 introduced several new form input types including email, url, number, range, date, month, week, time, datetime-local, search, and color.
    
### 2.Question: Explain the difference between <section>, <div>, and <article> tags in HTML5?

    Answer: The <section> tag is used to define a section in a document, such as chapters, headers, footers, or any other sections of the document. The <div> tag is a generic container for flow content and has no semantic meaning. The <article> tag specifies independent, self-contained content that could be distributed independently (e.g., blog post, news article).

## CSS3 Coding Questions

### 1.Question: Write a CSS snippet to create a responsive grid layout with three columns that stack vertically on screens narrower than 600px?
    Q. https://codepen.io/vishalmali06/pen/pomeqXm | Answer : https://codepen.io/vishalmali06/pen/mdYWaZp

### 2.Question: How can you center a div both horizontally and vertically using CSS flexbox?
    Q. https://codepen.io/vishalmali06/pen/wvbJNwY | Answer : https://codepen.io/vishalmali06/pen/MWdpLWg

### 3.How do you create a CSS Grid layout with a fixed header and footer and a scrollable content area in between?
    Q. https://codepen.io/vishalmali06/pen/pomeGJM | Answer : https://codepen.io/vishalmali06/pen/KKLWJpj
    
### 4.How can you create a responsive navigation bar using CSS Flexbox?
    Q. https://codepen.io/vishalmali06/pen/abrJXdB | Answer : https://codepen.io/vishalmali06/pen/wvbJNMR

### 5.How can you create a CSS animation that fades an element in and out?
    Q. https://codepen.io/vishalmali06/pen/ZENewWG | Answer : https://codepen.io/vishalmali06/pen/qBGrgZm
    
## MongoDB Questions

### 1.Question: How would you find all documents in a MongoDB collection where the age field is greater than 25?

```javascript
db.collection.find({ age: { $gt: 25 } });
```

### 2.Question: What is an index in MongoDB and why is it important?
    Answer: An index in MongoDB is a data structure that improves the speed of data retrieval operations on a collection. It is important because it allows for faster query execution and can significantly improve the performance of read operations. Without indexes, MongoDB has to perform a collection scan, which is slower.
    
