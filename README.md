# You Don't Know JS Book Series Notes
The Series: https://github.com/getify/You-Dont-Know-JS

Good **Reference** for Javascript and Programing Jargon: https://www.computerhope.com/jargon/jc.htm


# Book: Up & Going


## Functions

More Info: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions




### Function Expression

```js
//Not Named
var name = function() {
   console.log('bar');
};

name();
```

or

```js
//Named "name2"
var name = function name2() {
   console.log('bar');
};

name();
```


In a function expression the function `name` can be omited to create an anonymous function. A function expression can be used as an **IIFE** (Immediately Invoked Function Expression) which runs as soon as it is defined.

<br/>
<br/>
<br/>

**Not Hoisted**<br/>
Function expressions are not **hoisted** unlike function declerations. You cannot use/call a function expression before it is defined.

```js
notHoisted(); // TypeError: notHoisted is not a function

var notHoisted = function() {
   console.log('bar');
};
```

<br/>
<br/>
<br/>

**Named function expression**<br/>
A function expression can have a name (optional), without an name it is refered to as a unnamed function expression, we can use the name as a reference, example: 

```js
var foo = function() {}
foo.name // "foo"

var foo2 = foo
foo2.name // "foo"

var bar = function baz() {}
bar.name // "baz"
```

<br/>
<br/>
<br/>

**Calling a Function Expression**<br/>
A function expression will always be called by the variable (var) it was declared on for example:

```js
var bar = function baz() {
console.log("foo");
}

bar(); // foo

baz(); // Uncaught ReferenceError: baz is not defined
```

<br/>
<br/>
<br/>

**IFEE**<br/>
A function expression can be used as an **IIFE** (Immediately Invoked Function Expression) which runs as soon as it is defined.

```js
(function() {
    statements
})();
```

<br/>
<br/>
<br/>

**Callback**<br/>
They are usually used as a callback, the ```function(event)``` in this example:

```js
button.addEventListener('click', function(event) {
    console.log('button is clicked!')
})
```



More Info: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/function



<br/>
<br/>
<br/>



### Function Decleration

```js
function name() {
   console.log('bar');
};

name();
```




**Hoisted** <br/>
Function Declerations are hoisted, so you can call the fucntion before it is declared:

```js
name();

function name() {
   console.log('bar');
};
```

<br/>
<br/>
<br/>

**Calling a Function Decleration** <br/>
A function Decleration will always be called by the name specified after the **function** keyword ```function bar() {}```:

```js
function bar() {
console.log("foo");
}

bar(); // foo

```



More Info: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function



<br/>
<br/>
<br/>


### Callback function or just "Callback"

A "callback" is a function, procedure, or method, which is passed as an argument to another function.

A Callback function, also known as a higher-order-function, is a function that is passed to another function ( called *otherFunction* just for this example) as a parameter, and the callback function is called/executed inside the *otherFunction*.

An example of a callback function:

```js
var cars = ["Toyota", "BMW", "Porsche", "Ferari", "Mini", "Ford"];
​
cars.forEach(function (car, index){
console.log(index + 1 + ". " + car); // 1. Toyota, 2. BMW, 3. Porsche, 4. Ferari, 5.Mini, 6.Ford
});

```
Here we passed an anonymous function ```function (car, index)``` to the forEach method (a *method* is a function that is inside an object / that is owned by an object) as a parameter.

Another example:

```js
// This function logs/prints an name parameter into the console eg:
// greeting("Charlie"); // Hello Charlie

function greeting(name) {
  console.log('Hello ' + name);
}

//This function accepts a function as a parameter which it calls (callback).
//When the processUserInput function is run/called the user is prompted
//to enter their name in the prompt box, and that name is passed as a
//value to the *name* variable.
//The name variable is passed to the *callback* function and the *callback*
//function is executed logging/printing to the console *"Hello Charlie"*


function processUserInput(callback) {
  var name = prompt('Please enter your name.');
  callback(name);
}

//This is how the *processUserInput* function is called, with the *greeting* 
//function as the parameter.

processUserInput(greeting);
```

More Info: http://javascriptissexy.com/understand-javascript-callback-functions-and-use-them/

More Info: https://developer.mozilla.org/en-US/docs/Glossary/Callback_function

More info: https://www.computerhope.com/jargon/c/callback.htm


<br/>
<br/>
<br/>

### First-class Function / First-class Object

This means that javascript functions are just a special type of object that can do all the things that regular objects can do.

Basically, it means that you can do with functions everything that you can do with all other elements in the programming language. 

So, in the case of JavaScript, it means that everything you can do with an Integer, a String, an Array or any other kind of Object, you can also do with functions. 

(**First-class values / first calss objects** - In computer programming, a **first-class object**, also known as a **first-class citizen** or a **first-class value**, is a language entity — a number, a function, or a variable, for instance — that can be operated on in the same way as any other entity in the language.

More Info: https://www.computerhope.com/jargon/f/firstclass-object.htm )

More info : http://helephant.com/2008/08/19/functions-are-first-class-objects-in-javascript/

<br/>
<br/>



<br/>
<br/>
<br/>

### Function constructor

More Info: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function

<br/>
<br/>
<br/>

## Other

<br/>
<br/>
<br/>


# Book: Scope & Closures

### Scope

In JavaScript, scope is the set of variables, objects, and functions you have access to.

Javascript has function scope, meaning each function has its own scope. 

The **global scope** is the scope that contains all your code.

In Javascript functions have private scope, meaning  functions, variables or objects cannot access the functions, variables or objects contained in another function if they are sitting in the same scope.

Example 1: If function 1 and function 2 both sit on the global scope, they cannot enter each others scope and read the containing functions, variables or objects.

Example 2: If function 2 (fn2) sits inside function 1 (fn1) then fn2 can access the scope of fn1 because it sits inside the scope of fn1, but fn1 cannot access the scope of fn2. 

Both fn1 and fn2 can access the global scope, because fn1 sits on the global scope and fn2 sits within fn1, but the global scope cannot access the scope of either of the 2 functions.

In other words scope access is a one way process.

```
GS   <<<   fn1   <<<   fn2   <<<   fn3
      >/          >/          >/
```
   
In this simple example, imagine that **fn3** sits in **fn2** which itself sits within **fn1** which sits within **GS**; In this case **fn3** can assess the scope of **fn2**, **fn2** can access the scope of **fn1** and **fn1** can access the scope of **GS** as illustrated by the (<<<) symbols, this also means that **fn3** can access the scope of **fn1** by flowing through the scope of **fn2** and it can also access the scope of **GS** by flowing through the socpe of **fn2** and then flowing through the scope of **fn1**, but it is not possible to go forwards from **GS** to **fn1** etc... as illustrated by the (>/) symbol.

If **fn3** is looking for a particular variable it will first look within its own scope, if it cannot find it within itself it will go up through the rest of the functions it sits within in order **fn2** then **fn1** etc... untill it finds the variable it is looking for, at which point it will stop and use that variable. 

For example, if **fn3** is looing for a **var a** and there is a **var a** in both **fn2** and **fn1**, **fn3** will look in its own socpe first, if a **var a** is not found then **fn3** will move into the scope of **fn2**,  because **fn2** has a **var a** **fn3** will use this **var a** never needing to access the scope of **fn1** so the **var a** within **fn1** will never be used by **fn3**

```js
function fn1() {
   var a = 3:
   
   function fn2() {
   var a = 33;
   
      function fn3() {
        console.log(a); // 33
      }
      
   }
   
}
   
```
As we can see in this example **fn3** did not have a **var a** inside its own scope, but the **fn3** was tasked with printing an **a** variable, so **fn3** had to jump up into the scope of **fn2** and us the **var a** contained within the scope of **fn2**, once that variable within the scope of **fn2** was found **fn3** stoped searching and used thet variable, so the **var a** within **fn1** was never reached by **fn3**.

<br/>
<br/>
<br/>


### Closure
