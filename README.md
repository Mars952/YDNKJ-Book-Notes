# You Don't Know JS Book Series Notes
The Series: https://github.com/getify/You-Dont-Know-JS

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

**Not Hoisted**<br/>
Function expressions are not **hoisted** unlike function declerations. You cannot use/call a function expression before it is defined.

```js
notHoisted(); // TypeError: notHoisted is not a function

var notHoisted = function() {
   console.log('bar');
};
```

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

**IFEE**<br/>
A function expression can be used as an **IIFE** (Immediately Invoked Function Expression) which runs as soon as it is defined.

```js
(function() {
    statements
})();
```

<br/>

**Callback**<br/>
They are usually used as a callback:

```js
button.addEventListener('click', function(event) {
    console.log('button is clicked!')
})
```

More Info: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/function



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


### Callback function

More Info: https://developer.mozilla.org/en-US/docs/Glossary/Callback_function



<br/>


### Function constructor

More Info: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function







# Book: Scope & Closures

