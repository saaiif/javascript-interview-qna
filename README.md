
![Logo](https://iili.io/Uipb1t.png)


## 🔗 Links
[![portfolio](https://img.shields.io/badge/my_portfolio-000?style=for-the-badge&logo=ko-fi&logoColor=white)](https://saif-mujawar-5643a.web.app/portfolio)
[![linkedin](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/saif-mujawar/)
[![twitter](https://img.shields.io/badge/twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white)](https://twitter.com/saif_mujawar7)


# JavaScript Commonly Asked Interview Questions & Answers

> Click :star:if you like my work. Pull Requests are highly appreciated. Follow me on above metioned platform's for technical updates.

### Table of Contents

| No. | Questions                                                                                                                                                         |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | [What is Hoisting in JavaScript and how to avoid it](#what-is-hoisting-in-javascript-and-how-to-avoid-it)
| 2   | [What is the difference between Call, Apply and Bind](#what-is-the-difference-between-call-apply-and-bind)                                                                                                           |                                                 
| 3   | [What is JSON and its common operations](#what-is-json-and-its-common-operations)                                                                                 |
| 4  | [What is debouncing](#what-is-debouncing)  
| 5  | [What is throttling](#what-is-throttling)  
| 6  | [What is optional chaining](#what-is-optional-chaining)  
| 7  | [What is an event flow](#what-is-an-event-flow)   
| 8  | [What is event bubbling](#what-is-event-bubbling)        
| 9  | [What is event capturing](#what-is-event-capturing)  
| 10  | [What is a promise](#what-is-a-promise) 
| 11  | [Why do you need a promise](#why-do-you-need-a-promise)  
| 12  | [What are the three states of promise](#what-are-the-three-states-of-promise)  
              

1. ### What is Hoisting in JavaScript and how to avoid it

   Hoisting in JavaScript is the behavior by which the declaration of variables and functions are moved to the top. This means that    the variable or function declaration need not be done before initializing and calling them.
	
   Hoisting will happen only if ```var``` is used for declaration and not with ```const``` or ```let``` declarations. To avoid hoisting in JavaScript,    the strict mode can be used.

   **Example (Variable Hoisting)**

      Without Hoisting:

      ```javascript
      var num = 4;    // num is declared and then initialized

      console.log(num);    // num is called
      ```

    With Hoisting:

      ```javascript
      num = 4;    // num is declared and then initialized

      console.log(num);    // num is called

      var num // num is declared after initializing it. During execution, this will be moved to the top
      ```
    **Example (Function Hoisting)**

      Without Hoisting:

      ```javascript
      function functionName() {

        console.log("workattech");

    }

    functionName();     // function is called after declaring it
      ```

    With Hoisting:

      ```javascript
      functionName();   // function is called before declaring it

      function functionName() {

        console.log("workattech");

    }
      ```
  

      **[⬆ Back to Top](#table-of-contents)**
      
2. ### What is the difference between Call, Apply and Bind

   The difference between Call, Apply and Bind can be explained with below examples,

   **Call:** The call() is a method in JavaScript that helps us to call a function with a given object as the 'this' value. The ```call()``` method takes all the arguments individually.
   
   **Syntax**
   ```javascript
   functionName.call(thisArgument, ...functionArgs);
   ```

   ```javascript
   const personOne = {
  		firstName : "Elon",
  		secondName : "Musk"
	}

	const getFullName = function(company, country) {
 		console.log(this.firstName + " " + this.secondName + ", " + company + ", " + country);
	}

	const personTwo = {
  		firstName : "Mark",
  		secondName : "Zuckerburg"
	}

	getFullName.call(personOne, "Tesla", "United States");    // outputs Elon Musk, Tesla, United States
	getFullName.call(personTwo, "Facebook", "United States");    // outputs Mark Zuckerberg, Facebook, United States
   ```
   **Apply:** The apply() method is similar to the call() method. The only difference is that the apply() method takes an array as the argument whereas they were taken individually as arguments in the case of the call() method.

   **Syntax**
    ```javascript
      functionName.apply(thisArgument, functionArgsArray);
    ```

   ```javascript
   const personOne = {
      firstName : "Elon",
      secondName : "Musk"
   }

   const getFullName = function(company, country) {
     console.log(this.firstName + " " + this.secondName + ", " + company + ", " + country);
   }

   const personTwo = {
     firstName : "Mark",
     secondName : "Zuckerburg"
   }

   getFullName.apply(personOne, ["Tesla", "United States"]);    // outputs Elon Musk, Tesla, United States
   getFullName.apply(personTwo, ["Facebook", "United States"]);    // outputs Mark Zuckerberg, Facebook, United States
   ```
   In the above example, the company and country parameters were passed as a single array. It was passed individually in the case of the call() method. 

   **bind:** The bind() method is used to create a new function from another function with a given object as the this argument. It creates a copy of the function and then binds it to the object for which it was called. It does not immediately invoke the function and the new copy needs to be invoked separately.

   ```javascript
    const personOne = {
     firstName : "Elon",
     secondName : "Musk"
   }

    const getFullName = function(company, country) {
     console.log(this.firstName + " " + this.secondName + ", " + company + ", " + country);
    }

    const getPersonOneDetails = getFullName.bind(personOne, ["Tesla", "United States"]); 
     getPersonOneDetails();    // outputs Elon Musk, Tesla, United States
   ```
   In the above example, calling the bind method on 'getFullName' creates a copy of it, which is assigned to 'getPersonOneDetails'. When the 'getPersonOneDetails' is called separately, we will get the desired output.

   Call and apply are pretty interchangeable. Both execute the current function immediately. You need to decide whether it’s easier to send in an array or a comma separated list of arguments. You can remember by treating Call is for **comma** (separated list) and Apply is for **Array**.
   

   Whereas Bind creates a new function that will have `this` set to the first parameter passed to bind().

   **[⬆ Back to Top](#table-of-contents)**
   
3. ### What is JSON and its common operations?
	
	**JSON** is a text-based data format following JavaScript object syntax, which was popularized by `Douglas Crockford`. It is useful when you want to transmit data across a network and it is basically just a text file with an extension of .json, and a MIME type of application/json

   **Parsing:** Converting a string to a native object

   ```javascript
   JSON.parse(text);
   ```

   **Stringification:** converting a native object to a string so it can be transmitted across the network

   ```javascript
   JSON.stringify(object);
   ```

   **[⬆ Back to Top](#table-of-contents)**
   
   
4. ### What is debouncing?

  	Debouncing is a programming pattern that allows delaying execution of some piece of code until a specified time to avoid unnecessary _CPU cycles, API calls and improve performance_. The debounce function make sure that your code is only triggered once per user input. The common usecases are Search box suggestions, text-field auto-saves, and eliminating double-button clicks.

     Let's say you want to show suggestions for a search query, but only after a visitor has finished typing it. So here you write a debounce function where the user keeps writing the characters with in 500ms then previous timer cleared out using `clearTimeout` and reschedule API call/DB query for a new time—300 ms in the future.

     ```js
     function debounce(func, timeout = 500) {
       let timer;
       return (...args) => {
         clearTimeout(timer);
         timer = setTimeout(() => {
           func.apply(this, args);
         }, timeout);
       };
     }
     function fetchResults() {
       console.log("Fetching input suggestions");
     }
     const processChange = debounce(() => fetchResults());
     ```

     The _debounce()_ function can be used on input, button and window events

     **Input:**

     ```html
     <input type="text" onkeyup="processChange()" />
     ```

     **Button:**

     ```html
     <button onclick="processChange()">Click me</button>
     ```

     **Windows event:**

     ```html
     window.addEventListener("scroll", processChange);
     ```

     **[⬆ Back to Top](#table-of-contents)**

5. ### What is throttling?

     Throttling is a technique used to limit the execution of an event handler function, even when this event triggers continuously due to user actions. The common use cases are browser resizing, window scrolling etc.

     The below example creates a throttle function to reduce the number of events for each pixel change and trigger scroll event for each 100ms except for the first event.

     ```js
     const throttle = (func, limit) => {
       let inThrottle;
       return (...args) => {
         if (!inThrottle) {
           func.apply(this, args);
           inThrottle = true;
           setTimeout(() => (inThrottle = false), limit);
         }
       };
     };
     window.addEventListener("scroll", () => {
       throttle(handleScrollAnimation, 100);
     });
     ```
 
     **[⬆ Back to Top](#table-of-contents)**

6. ### What is optional chaining?

     According to MDN official docs, the optional chaining operator (?.) permits reading the value of a property located deep within a chain of connected objects without having to expressly validate that each reference in the chain is valid.

     The ?. operator is like the . chaining operator, except that instead of causing an error if a reference is nullish (null or undefined), the expression short-circuits with a return value of undefined. When used with function calls, it returns undefined if the given function does not exist.

     ```js
      const adventurer = {
        name: 'Alice',
        cat: {
          name: 'Dinah'
        }
      };

      const dogName = adventurer.dog?.name;
      console.log(dogName);
      // expected output: undefined

      console.log(adventurer.someNonExistentMethod?.());
      // expected output: undefined
     ```

      **[⬆ Back to Top](#table-of-contents)**
 
 7. ### What is an event flow

    Event flow is the order in which event is received on the web page. When you click an element that is nested in various other elements, before your click actually reaches its destination, or target element, it must trigger the click event for each of its parent elements first, starting at the top with the global window object.
    There are two ways of event flow

    1. Top to Bottom(Event Capturing)
    2. Bottom to Top (Event Bubbling)

    **[⬆ Back to Top](#table-of-contents)**

8. ### What is event bubbling

    Event bubbling is a type of event propagation where the event first triggers on the innermost target element, and then successively triggers on the ancestors (parents) of the target element in the same nesting hierarchy till it reaches the outermost DOM element.

    **[⬆ Back to Top](#table-of-contents)**

9. ### What is event capturing

    Event capturing is a type of event propagation where the event is first captured by the outermost element, and then successively triggers on the descendants (children) of the target element in the same nesting hierarchy till it reaches the innermost DOM element.

    **[⬆ Back to Top](#table-of-contents)**

10. ### What is a promise

    A promise is an object that may produce a single value some time in the future with either a resolved value or a reason that it’s not resolved(for example, network error). It will be in one of the 3 possible states: fulfilled, rejected, or pending.

    The syntax of Promise creation looks like below,

    ```javascript
    const promise = new Promise(function (resolve, reject) {
      // promise description
    });
    ```

    The usage of a promise would be as below,

    ```javascript
    const promise = new Promise(
      (resolve) => {
        setTimeout(() => {
          resolve("I'm a Promise!");
        }, 5000);
      },
      (reject) => {}
    );

    promise.then((value) => console.log(value));
    ```
      below,
    
     <p>
       Find more details on promise <a href=https://www.linkedin.com/posts/saif-mujawar_promises-activity-6962982433537343488-pVxU?utm_source=share&utm_medium=member_desktop target=_blank>
	here
      </a>
    </p>
   
    **[⬆ Back to Top](#table-of-contents)**

11. ### Why do you need a promise

    Promises are used to handle asynchronous operations. They provide an alternative approach for callbacks by reducing the callback hell and writing the cleaner code.

    **[⬆ Back to Top](#table-of-contents)**

12. ### What are the three states of promise

    Promises have three states:

    1. **Pending:** This is an initial state of the Promise before an operation begins
    2. **Fulfilled:** This state indicates that the specified operation was completed.
    3. **Rejected:** This state indicates that the operation did not complete. In this case an error value will be thrown.

    **[⬆ Back to Top](#table-of-contents)**
