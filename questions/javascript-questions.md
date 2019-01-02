# JS Questions:

* Explain event delegation
Event delegation is the concept of not adding event listeners to several sibling elements within a common parent element, instead add the event listener on the parent, and use event.target to determine which child element was clicked, then run the desired function using the child element clicked on as an argument.
* Explain how `this` works in JavaScript
this points to the object calling a function. The value of this within Global execution context will be the window. If the execution context isn't global, then this will point to a different object than the window. If the function is a method on an object, and is called directly from the object, this will refer to the object. If the object method is assigned to a global variable and then invoked on that global variable, this will refer to the window. You can use .bind() to explicitly bind the context of this to a specific object. Arrow functions bind any instance of "this" used in them to the enclosing lexical context, since they are bound .call() or .apply() cannot be used to change the execution context and value of "this".
* Explain how prototypal inheritance works
Prototypal inheritance works by nature of objects in javascript. If a piece of data inherits from an object such as String, Number, Function, or Object, each of the Objects have a prototype which the piece of data has access to. This is why you can call methods on any string, number, function, or object. A prototype is simply an object storing properties and values that can be accessed by any pieces of data inheriting from it. Prototypes, or the __proto__ object will exist on a piece of data if the data was created using Object.create() or the "new" keyword. Prototypal inheritance is useful because if an object doesn't have a property that is trying to be accessed it will look all the way up its prototype chain until it finds the piece of data. Every prototype chain eventually leads to the null Object which has no properties to access. 
* What do you think of AMD vs CommonJS?
* Explain why the following doesn't work as an IIFE: `function foo(){ }();`.
  * What needs to be changed to properly make it an IIFE?
  It doesn't work as an IIFE because it all needs to be wrapped in parentheses.
* What's the difference between a variable that is: `null`, `undefined` or undeclared?
  * How would you go about checking for any of these states?
  null refers to the null object, which is an object with no properties, representing no value.
  undefined is the value of a variable when it is accessed but has not been assigned a value yet.
  undefined is also the value returned from a function that doesn't return anything.
  An undeclared value is when a variable is defined without using const, let, or var.
  null === null
  typeof x returns undefined.
* What is a closure, and how/why would you use one?
A closure is the set of a function declared inside of a function combined with its lexical context. Meaning that the function declared inside of the outer function maintains access to the variables within the outer function even after the outer function has finished executing. This is useful because you can emulate private data which isn't innately built into javascript without the use of closures. You can create different instances of data that are separate from eachother using a closure.
* Can you describe the main difference between a `forEach` loop and a `.map()` loop and why you would pick one versus the other?
The main difference is that a map is used to create a copy of the array after running a function on each element, where a forEach just calls a function for each element in an array without making a copy of the array. If you want to alter data then re-render an array of data, a .map would be appropriate. If you just want to call a function that doesn't directly affect each element in the array, a forEach should be used.
* What's a typical use case for anonymous functions?
Anonymous functions are used frequently in function expressions. They are also typically used as callback functions within higher order functions.
* How do you organize your code? (module pattern, classical inheritance?)
I prefer the module pattern, because it makes better use of the javascript prototype object. You can use modules to add functionality to, to empower an object, where with classical inheritance it is hard to later alter the hierarchy of inheritance without having children classes that have a lot of unnecessary functionality, thus creating the "You want a banana but you got a gorilla holding a banana in a jungle" problem. The module pattern emphasizes objects having a has-a or can-do relationship with other objects, but classical inheritance causes an object to have an is-a relationship with its parents. Classical inheritance generally shouldn't be used more than 1 layer deep if possible.
* What's the difference between host objects and native objects?
Native objects are objects provided by javascript such as the String object, but host objects are provided by the browser such as the window.
* Difference between: `function Person(){}`, `var person = Person()`, and `var person = new Person()`?
The new keyword must be used to create an instance of a Person object.
* What's the difference between `.call` and `.apply`?
* Explain `Function.prototype.bind`.
bind is used to explicitly bind the context of this in a function to whatever object it was called on.
* What's the difference between feature detection, feature inference, and using the UA string?
* Explain Ajax in as much detail as possible.
* What are the advantages and disadvantages of using Ajax?
Advantages: Improved user experience because you can render other parts while waiting for data to arrive. Network load and bandwidth load can be decreased thus improving speed. Disadvantages: Older browsers are incompatible. There are security threats associated.
* Explain how JSONP works (and how it's not really Ajax).
* Have you ever used JavaScript templating?
  * If so, what libraries have you used?
* Explain "hoisting".
Variable declarations are 'hoisted' to the top of the code so they are available when the code initializes. Meaning that you can invoke a function above where it was declared because when the line of code invoking the function is processed, the engine already knows where to find the function to run.
* Describe event bubbling.
Dom events within a child element will bubble up to the parent element and further. If a child and parent both have event handlers, the event of the child if activated will execute first, then the event on the parent will execute all the way up to the outermost parent with an event handler.
* Describe event capturing.
You can use an event handler on a parent then use e.target to run code on the specific child element that you want to change based on the event.
* What's the difference between an "attribute" and a "property"?
An attribute comes from an HTML tag and will only create DOM properties if the attribute is a standard attribute for the specified tag recognized by the DOM suchas "type" for an input field. An attribute can only have a value of a string, and their name is case insensitive. Properties on the otherhand do not need to be a string, they can be other data types too. Because attributes become properties, properties are more flexible and useful than attributes.
* Why is extending built-in JavaScript objects not a good idea?
More than anything, it causes confusion for other people reading your code. Developers will expect JS native objects to not have anything added to them, so other variables should be created and used for the sake of other developers who need to understand your code.
* Difference between window load event and document DOMContentLoaded event?
* What is the difference between `==` and `===`?
== does a loosely equals and coerces values to try to find a match between the two items being compared. === is a strict equals and will also compare data type and memory allocation. The === should always be used over the == for more clear code.
* Explain the same-origin policy with regards to JavaScript.
* Make this work:
```javascript
duplicate([1,2,3,4,5]); // [1,2,3,4,5,1,2,3,4,5]
```
* What is `"use strict";`? what are the advantages and disadvantages to using it?
use strict causes errors to be thrown for several things considered to be bad syntax. It prevents the usage of undeclared variables, so that global scope is not polluted by variables that were accidentally not declared using var, let, or const. The benefit to this is that if you mistype a variable name during a reassignment of a variable, it will not create a variable of that misspelled name in global scope, instead it will throw an undeclared variable error. The biggest disadvantage of use strict is that adding to code that was written poorly may cause the code to not work until you refactor it.
* Create a for loop that iterates up to `100` while outputting **"fizz"** at multiples of `3`, **"buzz"** at multiples of `5` and **"fizzbuzz"** at multiples of `3` and `5`
* Why is it, in general, a good idea to leave the global scope of a website as-is and never touch it?
Global scope has a lot of objects on it already so to not overwrite any of those objects, variable shouldn't be made in global scope.
* Why would you use something like the `load` event? Does this event have disadvantages? Do you know any alternatives, and why would you use those?
* Explain what a single page app is and how to make one SEO-friendly.
A single page app doesn't require different html documents to load per different URL as websites did in the past. They use one html document and render different html into it conditionally, which greatly improves load time across a website.
* What is the extent of your experience with Promises and/or their polyfills?
* What are the pros and cons of using Promises instead of callbacks?
* What are some of the advantages/disadvantages of writing JavaScript code in a language that compiles to JavaScript?
* What tools and techniques do you use debugging JavaScript code?
* What language constructions do you use for iterating over object properties and array items?
* Explain the difference between mutable and immutable objects.
  * What is an example of an immutable object in JavaScript?
  * What are the pros and cons of immutability?
  * How can you achieve immutability in your own code?
* Explain the difference between synchronous and asynchronous functions.
* What is event loop?
  * What is the difference between call stack and task queue?
* Explain the differences on the usage of `foo` between `function foo() {}` and `var foo = function() {}`
* What are the differences between variables created using `let`, `var` or `const`?
* What are the differences between ES6 class and ES5 function constructors?
* Can you offer a use case for the new arrow `=>` function syntax? How does this new syntax differ from other functions?
* What advantage is there for using the arrow syntax for a method in a constructor?
* What is the definition of a higher-order function?
* Can you give an example for destructuring an object or an array?
* ES6 Template Literals offer a lot of flexibility in generating strings, can you give an example?
* Can you give an example of a curry function and why this syntax offers an advantage?
* What are the benefits of using `spread syntax` and how is it different from `rest syntax`?
* How can you share code between files?
* Why you might want to create static class members?
