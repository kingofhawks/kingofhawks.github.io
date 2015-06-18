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

### To summarize:

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
  return inside;
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

* 1. B forms a closure including A, i.e. B can access A's arguments and variables.
* 2. C forms a closure including B.
* 3. Because B's closure includes A, C's closure includes A, C can access both B and A's arguments and variables. In other words, C chains the scopes of B and A in that order.


## Using the arguments object
The arguments of a function are maintained in an array-like object. Within a function, you can address the arguments passed to it as follows:

> arguments[i]

where i is the ordinal number of the argument, starting at zero. So, the first argument passed to a function would be arguments[0]. The total number of arguments is indicated by arguments.length.

Using the arguments object, you can call a function with more arguments than it is formally declared to accept. This is often useful if you don't know in advance how many arguments will be passed to the function. You can use arguments.length to determine the number of arguments actually passed to the function, and then access each argument using the arguments object.

For example, consider a function that concatenates several strings. The only formal argument for the function is a string that specifies the characters that separate the items to concatenate. The function is defined as follows:
<code><pre>
function myConcat(separator) {
   var result = "", // initialize list
       i;
   // iterate through arguments
   for (i = 1; i < arguments.length; i++) {
      result += arguments[i] + separator;
   }
   return result;
}
</code></pre>

You can pass any number of arguments to this function, and it concatenates each argument into a string "list":

<code><pre>
// returns "red, orange, blue, "
myConcat(", ", "red", "orange", "blue");

// returns "elephant; giraffe; lion; cheetah; "
myConcat("; ", "elephant", "giraffe", "lion", "cheetah");

// returns "sage. basil. oregano. pepper. parsley. "
myConcat(". ", "sage", "basil", "oregano", "pepper", "parsley");
</code></pre>

References:
* [Mozilla MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions)
* [Self-Executing Anonymous Functions](http://markdalgleish.com/2011/03/self-executing-anonymous-functions/)


