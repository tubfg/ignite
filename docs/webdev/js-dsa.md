# JavaScript Algorithms and Data Structures
This is a bit of a surprise. It's a deviation from the original plan of learning front-end web development with React. Why deviate? JavaScript is used there and I'm no expert in it. It will be good to get back to CSS after a small break so that I can remember it better. My aim is to be comfortable writing JS programs, as comfortable as I am with Python. JS is used everywhere on the web and it feels so powerful. Time to use it well! It seems that this certification doesn't cover async JS. That's alright but I need to find resources for it by the time I finish this.  
Notes guideline : Something fundamental and important or new (preferrably with links to explore). It should be short and complete.

## Basic JavaScript
* Variable names in JS can contain $, \_, letters, and numbers but cannot start with a number. Declaring a variable without initalizing it will make it an `undefined` type object and it will have the value `undefined`.
* People like writing JS variable names in camelCase.
* Variables declared with `var` can be declared multiple times. Trying to re-declare a variable declared with `let` results in a SyntaxError. `const` is like `let` but the variable is read-only.
* JS has the `++` and `--` increment and decrement operators. The `%` in JS is not a modulo operator, it's a remainder operator and can return negative remainders.
* Values of type `String` are immutable. Like Python.
* Constant variables cannot have their value changed, they cannot be re-declared or re-assigned a different value. In this case : `const a = [1, 2, 3]`, the variable `a` holds the reference to the array (since it is not a primitive type). Therefore the array itself can be modified (e.g. `a.push(1)` or `a[2] = 7`) since the reference won't change and the "const-ness" still holds.
* The `push` function of an `array` takes in one or more arguments and appends them to the end of the array.
* `shift` and `unshift` remove and add values to the beginning to the start of the array just like `pop` and `push` do to the end of the array.
* If a variable is declared without `let`, `const`, or `var` it will have global scope regardless of where it is declared. **Explanation**: [There aren't any "global variables" in JS](http://blog.niftysnippets.org/2008/03/horror-of-implicit-globals.html) (They are there when declared by `let` or `const`). When you do `wowNiceGlobal = 5` where `wowNiceGlobal` is being referenced for the first time thus making it a "global variable" and giving it global scope, it really just creates and assigns to a property (with the same name) of **the** global object. In a browser, the `window` variable is a reference to the global object. You can stop this property setting from happening by adding "use strict" to your code.
* **Scope**. A variable, declared with `var`, `let`, or `const` at the top level of your code is given global scope. `var` has a function scope. If a `var` variable is defined in some block in a function it will be available throughout the function. `let` is block scoped. It does not exist outside the block. Within their scopes both `let` and `var` variables are "hoisted". This means they are defined at the top of their scopes. `var` variables are initialized with `undefined` while `let` variables are not initialized and will cause a ReferenceError if you try to access them. `const` has the same scoping rules as `let`.
* The `==` operator will perform type coercion if the operands aren't of the same type. The `===` operator doesn't convert types and will return false if the types are different. Like that there are also the `!=` and `!==` operators.
* **Type Coercion**. Primitive types are `number`, `string`, `null`, `undefined`, `boolean` and `symbol`(new, added in ES6). Using [this article about type coercion for reference](https://www.freecodecamp.org/news/js-type-coercion-explained-27ba3d9a2839/) we see that you can explicitly convert and that the only implicit conversion allowed (for primitives and others) is "to string", "to number", and "to boolean".
    * Boolean conversion happens with logical operators (but the result of the expression is still the original type). Objects are always truthy values.
    * String conversion happens with the `+` operator when either operands are of the string type.
    * Number and object conversions are complex. Must check the blog post.
* In a switch statement, once a case has been matched, all statements from there on are executed till a break is encountered (regardless of curly braces). Cases are matched with `===`.
* **Objects**. They are a collection of key: value elements. The keys are called properties. All properties are converted to a string and stored. You can access values of properties of objects via `.` (in case the property string is also a valid identifier) or `[]` (works for all properties).
* You can **delete properties** from objects. Just add the keyword `delete` before accessing the property either via the dot notation or bracket notation.
* To check if an object has a property, use this function: `objkt.hasOwnProperty(propname)` which returns a boolean value.
* The `while` loop and the `for` loops are like C's. The `do{}while()` loop too.
* The RNG for JS is `Math.random` which returns numbers in the range [0, 1).

## ES6 (Modern JavaScript)
* You can prevent an object from being modified by passing it to `Object.freeze(objkt)` (Not by making a `const` object).
* You can extend an array (a1) with another array (a2) by using `arr1.concat(arr2)`.
* Variable argument functions are possible using the rest parameter. You specify a parameter as `...paraName` and when you pass multiple arguments they are all available in array with that name (paraName here).
* Similarly, there is the "spread" operator to unpack an array into multiple elements, this can be useful when the function expects multiple parameters instead of an array. It follows the same syntax. Given an array arr, you can do `console.log(...arr)`.
* The object destructuring operator is a clean shortcut to extract multiple values from an object at once. The most basic way to do it is : `{param1, param2} = objkt`. Suppose you want to use variables of different names you can do this : `{"param1": var1, "param2": var2} = objkt`. Nested objects call for nested destructuring. You can destructure in the function arguments.
* Similarly, there is also array destructuring. You can unpack particular values from the array. Like so, `[a, b,,,, c, d,, e] = [1,2,3,4,5,6,7,8,9,0]`. For the last elements, you can also unpack them into a separate array using the rest operator. So if you want a new array but without the first 4 values you would do : `[,,,, ...new_arr] = arr`.
* Format strings are available as template literals. They are used as \` any text \`. In a template literal you use `${ any expression }` to place run-time values. They preserve all whitespace.
* There is also a shorthand for creating objects. You can just do `{x, y}`. The keys will be `x` and `y` (in string format) respectively.
* When defining functions in objects you can omit the `function` keyword and just do `prop_name(arg1, arg2){}`.
* You can use the `class` keyword to have a `constructor`, `get` and `set` methods, and you can create an object of that type with `new className(constructor args)`.
* You can make the variables, functions, and whatnot of one JS file available to others by "exporting" it. You do this by either adding the `export` keyword to it during delcaration or later on, where you can export multiple vars like `export {var1, func1, var2}`.
* To make use of them in another file you can "import" them like this : `import {var2, func1} from "relative_path_to_other_js_file"`. Or you can import everything from that file and place it under an object like this : `import * as containah from "that_other_file"`. Then access them like `containah.var1`.
* There are also "default exports". This means that you can have one export which is the default thing that will be imported from a file when you do this : `import something from "file"`. To set something as a default export you can do `export default var`. They are useful when a file represents one item and you want to import that in some other file. It isn't particulary useful when a file is meant to do multiple things and has multiple items.
* The **new operator** can be used to create objects from **functions** or **classes**. To use it with a function the function must act like a constructor and set properties to `this`. To use it with a class, the class must have a constructor.
* **Promise** is a feature to execute code asynchronously. You can create a `Promise` object with the `Promise` function. It expects you to take in two arguments (both of which are callbacks). As a convention we create a new promise object like this : `let prms = new Promise((resolve, reject) => {});`.
* A promise can be in one of three states: `pending`, `fulfilled`, and `failed`. It is `pending` when the promise is created, `fulfilled` when the `resolve` function is called, and `failed` when the `reject` function is called. Both `resolve` and `reject` take one argument each.
* You can also set additional functions for a promise. You can set the `then` property to a function (executed when the promise enters the "fulfilled" state) which takes in the argument passed to `resolve` (executed when the promise enters the "failed" state) and you can set the `catch` property to a function which takes in the argument passed to `reject`.

## Regular Expressions
* You can specify a required number of matches, more specific than `*` or `+`. The format is `(some matching pattern){min, max}`. You can omit min or max if you don't want a lowerbound or upperbound, respectively. To specify a particular number of matches, use `(pattern){exactNum}`.

## Debugging
console.clear() is useful

## Basic Data Structures
* `Array.splice(indexToStartRemoving, numberOfElementsToRemove, ...itemsToAdd);` allows you to remove elements from anywhere in the array and it returns a subarray of elements removed.
* The third and later arguments of spilce allow you to specify elements that should be put in the place of elements that were removed (can be more or less than the number of elements that were removed)
* `Array.slice(indexToStart[inclusive], indexToEnd[exclusive]);` allows you to extract a part of an array without modifying the array
* `Array.indexOf(elem)` returns the first index of an element in an array or -1 if it is not found.
* A shortcut way to check if an object has a property is `propName in objkt` which returns a boolean value.
* An Array is also really just an object where the keys are indices.
* To loop over the keys of an object there is a convenient format : `for(let keyVar in objkt) { }`
* To get all the keys in an array you can do `object.Keys(objkt);`

## Basic Algorithm Scripting
* `String.prototype.toUpperCase()` is nice

## Object Oriented Programming
* The `this` keyword when used within an object defintion refers to the object itself. You can access other properties of the object with this.
* A constructor function can be used to create similar objects. By convention these functions' names start with an uppercase letter and they don't return anything. They make use of `this` to set the object's properties. They are used along with the `new` operator which creates an object so that the use of `this` inside the function makes sense.
* `instaceof` can be used like `objkt instaceof Constrktr` which returns a boolean value to see if an object was instantiated with a particular constructor.
* By default all objects have their own instances of each property, which takes up memory. To have a common instance for all objects of a particular type you can use a **prototype**. Like so : `Cars.prototype.speed = 60;` and all objects of the type Cars will have a property `speed` that is equal to 60.
* There are two types of properties : **own** and **prototype**. You can check which category a property belongs to by using `objkt.hasOwnProperty(propName)`
* It is convenient to set the `prototype` of a type to a new object with the required properties. Remember to set the `constructor` property of `prototype`.

### Prototype chain and inheritance
All objects in JS have properties and then a link to another object (called the **prototype** of this object). Since the prototype itself is an object, it will have a link to its own prototype. This is called the prototype chain and it ends when an object's prototype is set to `null` as `null` has no prototype.  
When you try to access a property of an object, it is first checked in the object's properties, then the properties of its prototype and so on until it hits `null`.  
* Primitives (Number, undefined, null, etc) don't have methods
* Objects are stored in a variable by reference to the location in memory
* **FUNCTIONS ARE OBJECTS.** They are constructed by the function `Function` which has properties like `call`, `name`, `arguments`, and so on, which was constructed by the function `Object` which has properties like `toString`, `hasOwnProperty`, and so on.
* Let `Car` be a function object that can be used as a constructor. Let `maserati` be an object created by that function. `Car.prototype` is the prototype object of all objects created by `Car`. `maserati.__proto__` points to `Car.prototype`. 
* All functions, just like `Car`, have a `prototype` property. Other than anonymous functions. That is why anonymous functions are not constructors and cannot be used create objects.
* Since Object is a function (i.e. an object that is callable) `Object.prototype` is `{constructor: ƒ, __defineGetter__: ƒ, __defineSetter__: ƒ, hasOwnProperty: ƒ, __lookupGetter__: ƒ, …}`  
* Some objects and their prototypes:
```js
var o = {a: 1};
var b = ['yo', 'whadup', '?'];
function f() {
  return 2;
}
```  
    * The prototype of `o` is `Object.prototype`
    * The prototype of `b` is `Array.prototype`
    * The prototype of `f` is `Function.prototype`
* If an object is created with `let newob = Object.create(objkt)`, the prototype of the new object is the argument passed to `Object.create`. In this case `newob.__proto__` is `objkt`.
* Object creation, when done like this:
```js
var o = new Foo();
```  
is essentially this:
```js
var o = new Object();
o.[[Prototype]] = Foo.prototype;
Foo.call(o); // this is defined as Function.prototype.call(thisArg, ...otherArgs) { ... }
```
* To perform "inheritance" between function `A` and function `B`, i.e. to make A inherit from B, you just need to set `A.prototype = Object.create(B.prototype); A.prototype.constructor = A`.
* **Mixin** is a way to add properties to objects without multiple inhertiance. It can be done like this: 
```js
function flyMixin(obj) {
    obj.altitude = obj.wingspan * 3;
    obj.fly = function() {
        console.log("I believe I can fly...");
    }
}
```
* **IIFE** (Immediately Invoked Function Expression) is an anonymous function that is called right where it is defined. Like this `( () => {...} )()`.

## Functional Programming
A key point of FP is that functions don't rely on external parameters (global states) and they don't change those parameters. The same input gives the same output.  
* Functions that take in other functions as arguments or return functions are known as **higher order functions**.
* `Array.prototype.map(callback)` is useful for FP. Using it on an array applies the callback function on each element and returns a new array with the new elements. The arguments passed to the callback function are: **the current element, the index of the element, and the array that map is operating on.**
* Even if a function takes in **n** arguments you can pass it more args (in which case it will ignore the extra args) or fewer args (in which case the other ones will have be of the type `undefined`).
* `Array.prototype.filter(callback)` is also useful for FP. The returned array will only contain the elements for which the callback function returned true. The arguments passed to the callback function are the same as the map function.
* `Array.prototype.concat(otherArray)` returns a new array which has all the elements of the array on which it is called followed by the elements of the array which is passed as an argument.
* `Array.prototype.reduce(callback, initValue(optional))` can be implemented like this (example): 
```js
Array.prototype.redush = function(callback, initValue=undefined) {
  let start = 0;
  if(initValue === undefined) {
    initValue = this[0];
    start = 1;
  }
  for(let i=start; i<this.length; i++)
    initvalue = callback(initValue, this[i], i, this);
  return initValue;
}
```
* `Array.prototype.sort(callback)` returns a new array which is the array, sorted using the callback function. The rule for sorting is defined by callback(a, b):
    * Less than 0 => a will be before b
    * Equal to 0 => positions will not be modified
    * Greater than 0 => b will be before a
Sorting also modifies the original array.
* `Array.prototype.every(callback)` returns a boolean value which tells if all the elements in the array return true for the callback. There's also `Array.prototype.some(callback)`.

### `this` ?
`this` is a keyword that has different values depending on the scope it is accessed from. When accessed inside a free function it has the value of the global `this` (or `undefined` when strict mode is activated). When the function is a property of an object and called like `objkt.funk(...args)` `this` will be the object. If it's an **arrow function** `this` will be the same as `this` in the parent scope.  
You can also set what `this` will be used inside a function. One way to change `this` is using `funk.call(newThis)` which will call that function with a new `this` for that invocation only.  
Like `.call(newThis)`, there's also `.bind(newThis)` which returns a function which calls the original function but while setting its `this` to `newThis`. E.g. `funk.bind(newThis)()`.  
`.bind(newThis, ...args)` can also be used to create partial functions. You can set some parameters of the function and those won't be required in the new function that `bind` returns.