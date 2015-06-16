Python supports an interesting syntax that lets you define one-line mini-functions on the fly. Borrowed from Lisp, these so-called lambda functions can be used anywhere a function is required.

### Example: Introducing lambda Functions

>>> def f(x):
...     return x*2

>>> f(3)
6

>>> g = lambda x: x*2
>>> g(3)
6

This is a lambda function that accomplishes the same thing as the normal function above it. Note the abbreviated syntax here: there are no parentheses around the argument list, and the return keyword is missing (it is implied, since the entire function can only be one expression). Also, the function has no name, but it can be called through the variable it is assigned to.

To generalize, a lambda function is a function that takes any number of arguments (including optional arguments) and returns the value of a single expression. lambda functions can not contain commands, and they can not contain more than one expression. Don't try to squeeze too much into a lambda function; if you need something more complex, define a normal function instead and make it as long as you want.

### Some links for reference:
* [Dive into Python](http://www.diveintopython.net/power_of_introspection/lambda_functions.html)
* [Stackoverflow](http://stackoverflow.com/questions/890128/why-python-lambdas-are-useful)