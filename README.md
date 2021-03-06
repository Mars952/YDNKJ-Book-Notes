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

### Lexical Scope

**Lexical Scope** is the Scope model that Javascript Employs, as opposed to **Dynamic Scope** (Which is used by some other languages), **Lexical Scope** is determined when the code is compiled, i.e: lexical scope means that scope is defined by author-time decisions of where functions are declared.   

<br/>
<br/>


### Closure

Closure is when a function is able to remember and access its lexical scope even when that function is executing outside its lexical scope.

Consider the code below as an example of closure:

```js
function foo() {
   var a = 2;
   
   function bar() {
      console.log( a );
   }
   
   return bar;
}

var baz = foo();

baz(); // 2 -- Whoa, closure was just observed, man.

```

Function **foo();** is executed in the background as soon as it is passed to **var baz** as a value, (var baz = foo();)

Even though **var baz** references **foo()** (var baz = foo();), when **baz();** is called it is not running **foo();** at all, what it is doing is going into **foo();** and running the **bar();** function which was declared inside **foo();** and returned by **foo();** (return bar;).

So when we run **baz();** we can consider that it is the same as running **bar();** outside its enclosing / lexical scope.

As we are not running **foo();** anymore and it had already executed, run and had returned, we would usually assume that the scope of **foo();** would be garbage collected like any normal function to free up memory, but this does not happen, the scope of **foo();** is still saved/retained in memory because the scope of **foo();** is still being used by the **bar();** function to reference the **var a** every time **bar();** it is called.

This retention/memory of **bar();** is considered a closure. **bar();** still has reference to the scope of **foo();** and this reference is called a closure.

Closure lets the function **bar();** continue to access the lexical scope (scope of foo();) it was defined in at author time.

How do we know that calling **baz();** references **bar();** directly and does not run **foo();** first? 

Consider the folowing example:

```js
function foo(b) {
   var a = b;
   
   function bar() {
      console.log( a );
   }
   
   return bar;
}

var baz = foo(b);

baz(3); // ReferenceError: Cant find variable b

```

if **baz();** was running **foo();** first and then running **bar();** we could assume that this code would have worked and changed the **console.log();** output to **3**, because from the looks of it **baz(3);** has an argument of **3** which we would assume would get passed over to the variable **b** of **foo(b);** eventually changing **a** to **b** within the function **foo();** (var a = b;).

But that is not the case as we can see in the error **Cant find variable b**, so we can see that **baz();** does not reference **foo();** at all, it references **bar();** directly and calls it, as if we were calling **bar();** from outside the **foo();** scope.

How can we really prove this? 

Consider the folowing code:

```js
function foo() {
   var a = 2;
   
   function bar(b) {
      console.log( a + b );
   }
   
   return bar;
}

var baz = foo();

baz(3); // 5
```

As we can see this time the output is **5** because in the **console.log();** of **bar();** we had added together **var a** and **var b** (a + b). As **var a** was set to **2** in the scope of **foo();** and **var b** was set to **3** when we called **baz(3);** we ended up with a result of **5**.

This shows us that **baz();** had referenced **bar();** directly and calling **baz(3);** was just like calling **bar(3);** directly, so the **var b** in **bar(b);** was directly set to **3** and then through closure **bar();** had referenced the scope of **foo();** and grabbed the **var a**.

I mentioned calling **baz();** is like calling **bar();** directly, some people might ask, why not just call **bar();** directly then!?

Well we cannot call **bar();** directly because you cannot call a function from outside of the scope it was declared in. 

Why? 

Because function scopes are private, so the only way to call **bar();** (or any function) from outside the scope it was declared in is to return it from the function it was declared in and asign it to another variable **(in this case baz();)** which will be called when we want to execute **bar();** from outside the scope it was declared in.

<br/>
<br/>


### Loops + Closure

Why does this output **6** and not **1, 2, 3, 4, 5**:

```js
for (var i=1; i<=5; i++) {
setTimeout( function timer(){
console.log( i );
}, i*1000 );
}
//6
//6
//6
//6
//6
//6
```

This outputs **6** because Javascript is single threaded, which means it runs one **thread/process** at a time stacking the others in a que, so when javascript runs it puts all its **functions/processes** in a que.

In this example the **for loop** calls the **setTimeout**, so the **setTimeout** gets put in a que to run after the **for loop** has finished executing, as the **for loop** has been told to output code only while **var i** is less than **5** the loop will run untill **var i** becomes **6** at which point the loop will end, meaning **var i** will be set to **6**.

After the **for loop** has run the **setTimeout** functions will start running, at this point all the **setTimeout** have closure over the for loop and the **var i** variable and all will output **6** as the **var i** had been set to **6** before the **setTimeout** had run.

How to fix this:

```js
for (var i=1; i<=5; i++) {
	let j = i; // yay, block-scope for closure!
	setTimeout( function timer(){
		console.log( j );
	}, j*1000 );
}
```
or

```js
for (let i=1; i<=5; i++) {
	setTimeout( function timer(){
		console.log( i );
	}, i*1000 );
}
```

Why does this work then?

This works because the **let** decleration creates a new **block scope** every time the **for loop** loops, and as each **setTimeout** is defined within its own **block scope** it will only reference the **let** that was int he scope it was defined in, and **let** will be initialized at each subsequent iteration with the value from the end of the previous iteration.

<br/>
<br/>


### Modules

Modules are a code parrerns /design patterns in javascript which leverage the power of closure.

Modules divide programs into clusters of code that, by some criterion, belong together.

Example of a Module: 

```js
function CoolModule() {
	var something = "cool";
	var another = [1, 2, 3];

	function doSomething() {
		console.log( something );
	}

	function doAnother() {
		console.log( another.join( " ! " ) );
	}

	return {
		doSomething: doSomething,
		doAnother: doAnother
	};
}

var foo = CoolModule();

foo.doSomething(); // cool
foo.doAnother(); // 1 ! 2 ! 3
```

As we can see here Modules employ closure to function.

Learn More: Learn More: https://toddmotto.com/mastering-the-module-pattern/
Learn More: https://medium.freecodecamp.org/javascript-modules-a-beginner-s-guide-783f7d7a5fcc

<br/>
<br/>
<br/>


# Book: this & Object Prototypes

### This

`this` is actually a binding that is made when a function is invoked, and *what* it references is determined entirely by the call-site where the function is called.

More Info: https://github.com/gnovakov/You-Dont-Know-JS/blob/master/this%20%26%20object%20prototypes/ch2.md#call-site

<br/>
<br/>
<br/>

### Default Binding

Default binding applies to where the function was called from, so in the following case `this` points to the global object:

```js
function foo() {
	console.log( this.a );
}

var a = 2;

foo(); // 2
```

As we can see the **foo();** was called on the global object thus **foo's** `this` is set to the global object.

<br/>

If we are using **strict mode**, the global object is not eligible for the default binding:

```js
"use strict";
function foo() {
	console.log( this.a );
}

var a = 2;

foo(); // TypeError: `this` is `undefined`
```
<br/>
<br/>

### Implicit Binding

Does the call-site have a context object, is the function call located within an object:

```js
function foo() {
	console.log( this.a );
}

var obj = {
	a: 2,
	foo: foo
};

obj.foo(); // 2
```
As we can see here, it looks like we are calling **foo** on the global object through `obj.foo();`, but because `foo()` is located inside the **var obj** object, what we are actually doing is calling `foo()` through the **var obj** object, (i.e. accessing *obj* and calling `foo();`) so `obj.foo();` is just a reference to the **foo** within the **var obj** so theoretically `foo()` is being called from within the **var obj** object, thus *binding* the `this` of **foo** to **var obj** which is why `console.log( this.a );` logs **2**, because **a** is located within **var obj**.

<br/>

Consider this: 

```js
function foo() {
	console.log( this.a );
}

var obj2 = {
	a: 42,
	foo: foo
};

var obj1 = {
	a: 2,
	obj2: obj2
};

obj1.obj2.foo(); // 42
```

As we can see in this example, the `this` of **foo** is *bound* to the **var obj2** object, because that is where the **foo** is immediately bound to `var obj2 = { a: 42, foo: foo };`, and the fact that we are calling **foo** through **obj1** and then **obj2** (`obj1.obj2.foo();`) doesnt matter because these are references to the **foo** within the **var obj1** thus `console.log( this.a );` logs **42**, because the **a** variable where **foo's** `this` is located is *42*.

It might look like `foo()` is being called from the global object, but what `obj1.obj2.foo();` does in theory is it says *OK, go into **obj1** and find **obj2** once you have found **obj2** go into it and find **foo**, once you have found **foo** call foo `foo()`. So `foo();` is called from within **obj2** thus the `this` is bound to **obj2**.

<br/>
<br/>

### Loosing the `this` Binding

Depending how `foo();` is called it might result in the `this` binding being lost, consider the following example:
```js
function foo() {
	console.log( this.a );
}

var obj = {
	a: 2,
	foo: foo
};

var bar = obj.foo; // function reference/alias!

var a = "oops, global"; // `a` also property on global object

bar(); // "oops, global"
```

From this example we can see that when calling `bar();` the **foo** function logs us the **a** *"oops, global"* from the *global* scope, instead of the one from the **var obj** object scope, it might seem strange as the `var bar = obj.foo;` is referencing **obj.foo;** but as we can see that in `var bar = obj.foo;` **foo** is not being called, and we know this because it is missing the **()** brackets i.e `obj.foo();`. Instead **foo** is being asigned to the **var bar** `var bar = obj.foo;`, so when we do call `bar();` it is as if we are calling `foo();` directly from the *global* object, thus our `this` is now bound to the *global* object.

This exact example is just that an *example* but this is a common mistake that could happen, where you might assign a function to something instead of calling the function by accidentally forgetting the brackets `()` after the function fname; `foo;` vs `foo();`.

The more common way this might happen is when we are working with callback functions (wehere we are using functions as arguments):

```js
function foo() {
	console.log( this.a );
}

function doFoo(fn) {
	// `fn` is just another reference to `foo`

	fn(); // <-- call-site!
}

var obj = {
	a: 2,
	foo: foo
};

var a = "oops, global"; // `a` also property on global object

doFoo( obj.foo ); // "oops, global"
```
As we can see here, we are calling the **doFoo** function with the parameter of **obj.foo** `doFoo( obj.foo );`, what this does is asign the **obj.foo** to to the *argument* **fn** on the **doFoo** function `function doFoo(fn)`, so that **fn** becomed **foo**, just like in the previous example where we asigned **obj.foo;** to **var bar** (`var bar = obj.foo;`) thus calling `bar();` became exactly like calling `foo();` directly, similarly here when the `fn();` is called it is just as if we are calling `foo();` within the **doFoo** function.

This unbinds **foo's** `this` from the object and sets it to the *global* object because the `foo();` is being called within the **doFoo** function, and the closest **a** variable to the **doFoo** function is on the *global* scope.

**Solution**
So if we were writing the above code with the purpose to still call the **a** variable that is located within the **obj** object and keep **foo's** `this` bound to **obj**, we would not pass **obj.foo** to the **doFoo** function, instead we would just pass the **obj** by itself (`dofoo(obj);`), which would asign the  **obj** to the **fn** instead of the **foo**, and then to call the **foo** from within the **dooFoo** function we would call `fn.foo()` (`function doFoo(fn) { fn.foo(); }`), which would output the **a** from **obj** and not the *global* scope, because as we explained **fn** would be set to **obj**.

<br/>
<br/>

### Explicit Binding

Previously we looked at ***implicit*** binding which means *suggested though not directly expressed*, but here we will talk about ***explicit*** binding which means *stated clearly and in detail, leaving no room for confusion or doubt.* and we call it **explicit** because functions have `call();` and `apply()` methods that allow you to *explicitly* specify where `this` will be bound.

So the diference is with *implicit* we had to be carefull where the `this` was being specified and bound to, while with *explicit* we specify directly where we want the `this` to be specified and bound.

Consider this example:

```js
function foo() {
	console.log( this.a );
}

var obj = {
	a: 2
};

foo.call( obj ); // 2
```

Here we are not asigning **foo** to the **obj** object, as we did in the previous examples, so if we wanted to bind the `this` of **foo** to **obj** we could not do it by calling `obj.foo()` because there is no **foo** within the **obj**, in this case to bing the `this` of **foo** to the **obj** we would use the `call();` method and pass the **obj** to the `call();` ( `foo.call(obj);` ) which will **explicitly** bind the `this` of **foo** to the **obj** object, thus outputting the **a** variable of the **obj** object.

So here we are not calling foo, but we are calling the **call();** method that belongs to **foo** and we are passing it the **obj** as an argument, the call method then executes **foo** and binds **foos** `this` to **obj** thus allowing us to access the **a** variable of **obj**.

We can see why it is called ***explicit*** because we are directly choosing what we want to bind the `this` of **foo** to, because we are making the choice ourselves.

<br/>
<br/>

### Hard Binding

Unfortunately explicit binding alone does not solve for functions losing its intended `this` binding, but the following variation does:

```js
function foo() {
	console.log( this.a );
}

var obj = {
	a: 2
};

var bar = function() {
	foo.call( obj );
};

bar(); // 2
setTimeout( bar, 100 ); // 2

// `bar` hard binds `foo`'s `this` to `obj`
// so that it cannot be overriden
bar.call( window ); // 2
```

As we can see here, the **bar** function contains the binding of **foo's** `this` and **obj** ( `foo.call( obj );` ), so whenever we can `bar();` we will always automatically hard bind the `this` of **foo** to **obj**. No matter how you later invoke the function bar, it will always manually invoke foo with obj.

***Variations:***
```js
function foo(something) {
	console.log( this.a, something );
	return this.a + something;
}

var obj = {
	a: 2
};

var bar = function() {
	return foo.apply( obj, arguments );
};

var b = bar( 3 ); // 2 3
console.log( b ); // 5
bar(4);// 2 4
       //6
```
Here we are also binding the `this` of **foo** with the **obj** within the **bar** function like in the previous example, but we are allowing for extra arguments to be thrown in, in this case calling `bar(4);` is like we are calling `foo(4)` which outputs for us the **a** variable ( *2* ) from the **obj** where the `this` of **foo** is bound, and the ***something*** argument which we set to **4** when we called `foo(4);` and also returns to us the sum of the **a** variable and the **something** argument (`return this.a + something;`).

Another way to express this pattern is to create a reusable helper where the object we want to bind the `this` to is not ***explicitly*** set as in the previous example ( `var bar = function() { return foo.apply( obj, arguments ); };` > *explicitly* and unchangeably set to **obj** also *explicitly* and unchangeably set to **foo** ), but can be set as the **bar** function is called to whatever we want incase we want to set the `this` to different functions or reuse the helper for different objects and functions:

```js
function foo(something) {
	console.log( this.a, something );
	return this.a + something;
}

// simple `bind` helper
function bind(fn, obj) {
	return function() {
		return fn.apply( obj, arguments );
	};
}

var obj1 = {
	a: 2
};

var obj2 = {
	a: 44
};

var bar1 = bind( foo, obj1 );
var bar2 = bind( foo, obj2 );

var b = bar1( 3 ); // 2 3 
console.log( b ); // 5

var c = bar2( 3 ); // 44 3
console.log( c ); // 47
```
As we can see here we can reuse the **bind** functrion as a reusable function where we can bind any other functions `this` to any object we want, thus needing to only write the **bind** function once and reuse it multiple times, instead of wriging a new function for every new binding we want to create.


<br/>
<br/>

### The `bind();` method

Since hard binding is such a common pattern, the `bind();` method was provided in ES5 to make it easier to use:

```js
function foo(something) {
	console.log( this.a, something );
	return this.a + something;
}

var obj1 = {
	a: 2
};

var obj2 = {
	a: 44
};

var bar = foo.bind( obj1 );
var baz = foo.bind( obj2 );

var b = bar( 3 ); // 2 3
console.log( b ); // 5
var c = baz( 8 ); // 44 8
console.log( c ); // 52
```

As we can see here, instead of writing out the long bind helper function:

```js
function bind(fn, obj) {
	return function() {
		return fn.apply( obj, arguments );
	};
}
```
and then :
```js
var bar1 = bind( foo, obj1 );
```
to make the bind, we were able to just use the new built in `bind();` methodthat did the whole job for us ```var bar = foo.bind( obj1 );```

<br/>
<br/>

### `new` binding

If we create a *object type* that we want to use in the future, the `this` of any object we create from said *object type* by invoking the `new` keyword will be bound to the new object that was created, example:

```js
function foo(a) {
	this.a = a;
}

var bar = new foo( 2 );
console.log( bar.a ); // 2

var baz = new foo( 88 );
console.log( baz.a ); // 88
```
As we can see, we created two objects from the **foo** object type, ***bar*** and ***baz*** and as we can also see the `this` for each of these objects was set to the object itself, so when calling `bar.a` or `baz.a` the `this` binding is set to **bar** and **baz** respectively.

