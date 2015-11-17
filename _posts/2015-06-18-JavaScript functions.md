Java Script functions

## Defining functions

A function definition (also called a function declaration, or function statement) consists of the function keyword, followed by:

The name of the function.
A list of arguments to the function, enclosed in parentheses and separated by commas.
The JavaScript statements that define the function, enclosed in curly brackets, { }.

For example, the following code defines a simple function named square:

> function square(number) {
>  return number * number;
> }

Primitive parameters (such as a number) are passed to functions by value; the value is passed to the function, but if the function changes the value of the parameter, this change is not reflected globally or in the calling function.

If you pass an object (i.e. a non-primitive value, such as Array or a user-defined object) as a parameter and the function changes the object's properties, that change is visible outside the function.


## Function expressions

While the function declaration above is syntactically a statement, functions can also be created by a function expression. Such a function can be anonymous; it does not have to have a name. For example, the function square could have been defined as:

> var square = function(number) { return number * number };
> var x = square(4) // x gets the value 16

However, a name can be provided with a function expression and can be used inside the function to refer to itself, or in a debugger to identify the function in stack traces:

> var factorial = function fac(n) { return n<=2 ? 1 : n*fac(n-1) };

> console.log(factorial(3));

In JavaScript, a function can be defined based on a condition. For example, the following function definition defines myFunc only if num equals 0:
<pre><code>
 var myFunc;
 if (num == 0){
  myFunc = function(theObject) {
    theObject.make = "Toyota"
  }
 }
</code></pre>

In addition to defining functions as described here, you can also use the Function constructor to create functions from a string at runtime, much like eval().

A method is a function that is a property of an object. Read more about objects and methods in Working with objects.

## Nested functions and closures
You can nest a function within a function. The nested (inner) function is private to its containing (outer) function. It also forms a closure. A closure is an expression (typically a function) that can have free variables together with an environment that binds those variables (that "closes" the expression).

Since a nested function is a closure, this means that a nested function can "inherit" the arguments and variables of its containing function. In other words, the inner function contains the scope of the outer function.

### To summarize

* The inner function can be accessed only from statements in the outer function.
* The inner function forms a closure: the inner function can use the arguments and variables of the outer function, while the outer function cannot use the arguments and variables of the inner function.

The following example shows nested functions:
<pre><code>
 function addSquares(a,b) {
   function square(x) {
    return x * x;
  }
  return square(a) + square(b);
 }
a = addSquares(2,3); // returns 13
b = addSquares(3,4); // returns 25
c = addSquares(4,5); // returns 41
</code></pre>


Since the inner function forms a closure, you can call the outer function and specify arguments for both the outer and inner function:
<pre><code>
function outside(x) {
  function inside(y) {
    return x + y;
  }
  return inside; //return the inner function!
}
fn_inside = outside(3); // Think of it like: give me a function that adds 3 to whatever you give it
result = fn_inside(5); // returns 8

result1 = outside(3)(5); // returns 8
</code></pre>


## Multiply-nested functions

Functions can be multiply-nested, i.e. a function (A) containing a function (B) containing a function (C). Both functions B and C form closures here, so B can access A and C can access B. In addition, since C can access B which can access A, C can also access A. Thus, the closures can contain multiple scopes; they recursively contain the scope of the functions containing it. This is called *scope chaining*. (Why it is called "chaining" will be explained later.)

Consider the following example:
<pre><code>
function A(x) {
  function B(y) {
    function C(z) {
      console.log(x + y + z);
    }
    C(3);
  }
  B(2);
}
A(1); // logs 6 (1 + 2 + 3)
</code></pre>

In this example, C accesses B's y and A's x. This can be done because:

1. B forms a closure including A, i.e. B can access A's arguments and variables.
2. C forms a closure including B.
3. Because B's closure includes A, C's closure includes A, C can access both B and A's arguments and variables. In other words, C chains the scopes of B and A in that order.


## Using the arguments object
The arguments of a function are maintained in an array-like object. Within a function, you can address the arguments passed to it as follows:

> arguments[i]

where i is the ordinal number of the argument, starting at zero. So, the first argument passed to a function would be arguments[0]. The total number of arguments is indicated by arguments.length.

Using the arguments object, you can call a function with more arguments than it is formally declared to accept. This is often useful if you don't know in advance how many arguments will be passed to the function. You can use arguments.length to determine the number of arguments actually passed to the function, and then access each argument using the arguments object.

For example, consider a function that concatenates several strings. The only formal argument for the function is a string that specifies the characters that separate the items to concatenate. The function is defined as follows:

> function myConcat(separator) {
>   var result = "", // initialize list
>      i;
>   // iterate through arguments
>   for (i = 1; i < arguments.length; i++) {
>      result += arguments[i] + separator;
>   }
>   return result;
> }


You can pass any number of arguments to this function, and it concatenates each argument into a string "list":
<code><pre>
// returns "red, orange, blue, "
myConcat(", ", "red", "orange", "blue");

// returns "elephant; giraffe; lion; cheetah; "
myConcat("; ", "elephant", "giraffe", "lion", "cheetah");

// returns "sage. basil. oregano. pepper. parsley. "
myConcat(". ", "sage", "basil", "oregano", "pepper", "parsley");
</code></pre>

## IIFE Pattern: Introducing a New Scope

This pattern is very important and adopted by most popular JavaScript libraries.

Sometimes you want to introduce a new variable scope—for example, *to prevent a variable from becoming global*. In JavaScript, you can’t use a block to do so; you must use a function. But there is a pattern for using a function in a block-like manner. It is called *IIFE* (immediately invoked function expression, pronounced “iffy”):
<code><pre>
(function () {  // open IIFE
    var tmp = ...;  // not a global variable
}());  // close IIFE

//alternative with less parentheses
!function () {
    console.log('watch out!');
}();
</code></pre>

Be sure to type the preceding example exactly as shown (apart from the comments). An IIFE is a function expression that is called immediately after you define it. Inside the function, a new scope exists, preventing tmp from becoming global. Consult [Introducing a New Scope via an IIFE](http://speakingjs.com/es5/ch16.html#iife) for details on IIFEs.


## Invoking Functions

There are four methods to invoke functions

* as functions

* as methods: call functions on object

* as constructs: new FunctionName()

* indirectly through call() and apply() methods


## Function Parameters

You can access function parameters with "arguments" array.

ES6 brings us default&rest parameters.

### Default Parameter
<pre>
<code>
//ES5 style
function hello(name){
    name = name || 'simon';
    console.log('hello'+name);
}

//ES6 style
function hello(name='simon'){
    console.log('hello'+name);
}
hello()
</code>
</pre>

### Rest Parameters
Rest replaces the need for *arguments* and addresses common cases more directly
<pre>
<code>
function push(array, ...items) {
  items.forEach(function(item) {
    array.push(item);
    console.log(item);
  });
}

var a = [];
push(a, 1, 2, 3)
</code>
</pre>

### Three main Difference between rest parameters and "arguments" object

* rest parameters are only the ones that haven't been given a separate name, while "arguments" contains all arguments passed to the function;

* "arguments" is not a real array, while rest parameters are Array instances, meaning methods like sort, map, forEach etc can be applied on it;

* "arguments" has additional functionality specific to itself (like the callee property).


### Spread Parameters

"Spread" seems inversion for Rest parameters, it turns array into consecutive arguments.
<pre>
<code>
function add(x, y) {
  return x + y;
}

var numbers = [4, 38];
add(...numbers) // 42

// good
const itemsCopy = [...numbers];
</code>
</pre>



## Arrow Functions

An arrow function expression (also known as fat arrow function) has a shorter syntax compared to function expressions and lexically binds the this value (does not bind its own this, arguments, super, or new.target). Arrow functions are always anonymous.

<pre>
<code>
// Basic syntax:
(param1, param2, paramN) => { statements }
(param1, param2, paramN) => expression
   // equivalent to:  => { return expression; }

// Parentheses are optional when there's only one argument:
singleParam => { statements }
singleParam => expression

// A function with no arguments requires parentheses:
() => { statements }

// Advanced:
// Parenthesize the body to return an object literal expression:
params => ({foo: bar})

// Rest parameters are supported
(param1, param2, ...rest) => { statements }
</code>
</pre>


## Method Chaining
When working with jQuery, you will find code like:
<pre>
<code>
// Find all headers, map to their ids, convert to an array and sort them
$(":header").map(function() { return this.id }).get().sort();
</code>
</pre>


## "this" keyword 
Note that *this* is a keyword, not a variable or property name. JavaScript syntax does
not allow you to assign a value to this.

Unlike variables, the this keyword does not have a scope, and nested functions do not
inherit the this value of their caller. If a nested function is invoked as a method, its
this value is the object it was invoked on. If a nested function is invoked as a function
then its this value will be either the global object (non-strict mode) or undefined (strict
mode). It is a common mistake to assume that a nested function invoked as a function
can use this to obtain the invocation context of the outer function. If you want to access
the this value of the outer function, you need to store that value into a variable that is
in scope for the inner function. It is common to use the variable self for this purpose.

<pre>
<code>
var o = {                           // An object o.
    m: function() {                 // Method m of the object.
        var self = this;            // Save the this value in a variable.
        console.log(this === o);    // Prints "true": this is the object o.
        f();                        // Now call the helper function f().
        function f() {              // A nested function f
           console.log(this === o); // "false": this is global or undefined
           console.log(self === o); // "true": self is the outer this value.
        }
    }
};
o.m(); 
</code>
</pre>

<pre>
<code>
function counter() {
var n = 0;
return {
count: function() { return n++; },
reset: function() { n = 0; }
};
}
var c = counter(), d = counter(); // Create two counters
c.count() // => 0
d.count() // => 0: they count independently
c.reset() // reset() and count() methods share state
c.count() // => 0: because we reset c
d.count() // => 1: d was not reset
</code>
</pre>


## call() & apply()

call() and apply() allow you to indirectly invoke a function as if it were a method of some other object.It seems to dynamically implement method on any object.

The call() method calls a function with a given this value and arguments provided individually.In ECMAScript 5 strict mode the first argument to call() or apply() becomes the value of this, even if it is a primitive value or null or undefined.

> fun.call(thisArg[, arg1[, arg2[, ...]]])

<pre>
<code>
function greet() {
  var reply = [this.person, 'Is An Awesome', this.role].join(' ');
  console.log(reply);
}

var o = {
  person: 'Douglas Crockford', role: 'Javascript Developer'
};

greet.call(o); // Douglas Crockford Is An Awesome Javascript Developer


//Effect same as
o.m = greet; // Make f a temporary method of o.
o.m(); // Invoke it, passing no arguments.
delete o.m; // Remove the temporary method.
</code>
</pre>

<pre>
<code>
var animals = [
  { species: 'Lion', name: 'King' },
  { species: 'Whale', name: 'Fail' }
];

for (var i = 0; i < animals.length; i++) {
  (function(i) {
    this.print = function() {
      console.log('#' + i + ' ' + this.species
                  + ': ' + this.name);
    }
    this.print();
  }).call(animals[i], i);
}
</code>
</pre>

While the syntax of this function is almost identical to that of apply(), the fundamental difference is that call() accepts an argument list, while apply() accepts a single array of arguments.

<pre>
<code>
    array_of_numbers = [3,5,2]
    var biggest = Math.max.apply(Math, array_of_numbers);
</code>
</pre>


## bind()

The bind() method creates a new function that, when called, has its this keyword set to the provided value, with a given sequence of arguments preceding any provided when the new function is called.

> fun.bind(thisArg[, arg1[, arg2[, ...]]])


References:
* [Mozilla MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions)

* [Self-Executing Anonymous Functions](http://markdalgleish.com/2011/03/self-executing-anonymous-functions/)

* [Immediately-Invoked Function Expression (IIFE)](http://benalman.com/news/2010/11/immediately-invoked-function-expression/)

* [speakingjs](http://speakingjs.com/es5/ch01.html#_functions)

* [exploring-es6](https://leanpub.com/exploring-es6/read)

* [essentialjsdesignpatterns](https://github.com/addyosmani/essential-js-design-patterns)

* [Design-Patterns-in-Javascript](https://github.com/tcorral/Design-Patterns-in-Javascript)

* [Arrow Functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)

* [Arrow Functions in depth](https://hacks.mozilla.org/2015/06/es6-in-depth-arrow-functions/)

* [ES6 Tutorial](https://github.com/ruanyf/es6tutorial)

* [JavaScript: The Definitive Guide]


