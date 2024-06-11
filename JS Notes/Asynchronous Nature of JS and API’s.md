# Asynchronous Nature of JS and API’s

Level: Moderate
ID: ACJ-1
Last edited time: September 25, 2023 8:31 AM
Status: Not started

## Table of Content

JSON

- JSON.parse()
    
    ```jsx
    // to convert the data from string to JS Object
    const obj = JSON.parse('{"name":"John", "age":30, "city":"New York"}');
    ```
    
- JSON.stringify()
    
    ```jsx
    // to convert JS object into string
    const obj = {name: "John", age: 30, city: "New York"};
    
    const myJSON = JSON.stringify(obj);
    
    ```
    

[JSON Formatter & Validator](https://jsonformatter.curiousconcept.com/)

Single Threaded/ Multi-threaded

Basically, JS uses single execution thread to perform all its operation. 

This threads executes your code line-by-line, one at a time, in a sequential manner. 

To avoid blocking behavior, JavaScript makes extensive use of asynchronous programming. Functions like **`setTimeout`**, **`setInterval`**, and AJAX requests are examples of asynchronous operations. These operations allow the main thread to continue executing other tasks while waiting for the asynchronous operations to complete.

In python, lib like “threading” helps to use multiple threads of operations. 

Callback: setTimeout (Web Browser API’s)

```jsx
function printHello(){
 console.log(“Hello”);
}
setTimeout(printHello,1000);
console.log(“Me first!”);
```

Promises

A promise is an object returned by an asynchronous function, which represents the current state of the operation.

pending, fulfilled, rejected

```jsx
// Promise example: Fetch data from an API
function fetchDataWithPromise() {
  return fetch('https://api.example.com/data')
    .then(response => response.json())
    .then(data => {
      console.log('Data fetched successfully:', data);
      return data;
    })
    .catch(error => {
      console.error('Error while fetching data:', error);
      throw error;
    });
}

// Using the Promise
fetchDataWithPromise()
  .then(data => {
    // Process the fetched data
    // Do something with data...
  })
  .catch(error => {
    // Handle errors
    // Show an error message to the user...
  });
```

Async/Await

```jsx
// Async/Await example: Fetch data from an API
async function fetchDataWithAsyncAwait() {
  try {
    const response = await fetch('https://api.example.com/data');
    const data = await response.json();
    console.log('Data fetched successfully:', data);
    return data;
  } catch (error) {
    console.error('Error while fetching data:', error);
    throw error;
  }
}

// Using the async function with await
async function processData() {
  try {
    const data = await fetchDataWithAsyncAwait();
    // Process the fetched data
    // Do something with data...
  } catch (error) {
    // Handle errors
    // Show an error message to the user...
  }
}

processData();
```

> Basically, the syntax difference is the major difference in Promises and async/await. As the async/await code is more readable and, have a more elegant way to work with asynchronous code as it is built on top of Promises.
> 

Using promises and async/await together: There are times some  third party api’s return promises so, in that time we use it as

```jsx
// Using Promises
function getDataWithPromise() {
  return fetch('https://api.example.com/data')
    .then(response => response.json())
    .then(data => {
      console.log('Data fetched successfully:', data);
      return data;
    })
    .catch(error => {
      console.error('Error while fetching data:', error);
      throw error;
    });
}

// Using async/await with Promises
async function getDataWithAsyncAwait() {
  try {
    const response = await fetch('https://api.example.com/data');
    const data = await response.json();
    console.log('Data fetched successfully:', data);
    return data;
  } catch (error) {
    console.error('Error while fetching data:', error);
    throw error;
  }
}
```

The Event Loop:
JavaScript's event loop is responsible for handling asynchronous operations and managing the execution of callbacks. When an asynchronous operation is initiated, it is moved to the background, and the event loop continues executing other tasks. Once the asynchronous operation is complete, its corresponding callback is placed in a queue. The event loop continuously checks this queue for pending callbacks and executes them in the order they were added.

While JavaScript is single-threaded, it can leverage non-blocking I/O, allowing it to handle concurrent tasks efficiently, even with a single execution thread. However, it also means that CPU-intensive tasks or long-running synchronous operations can negatively impact the user experience.