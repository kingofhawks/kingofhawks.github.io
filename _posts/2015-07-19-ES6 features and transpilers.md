ES6 is coming, but still a long way till all popular browsers full support it.

There are some ES6 to ES5 transpiler for now.

## Babel

[Babel](http://babeljs.io/) formerly known as 6t05, is the most popular JavaScript compiler:

* ES2015 and beyond

* JSX and React support

* Babel supports user plugins

Install Babel is rather easy:

> npm install -g babel

Then you can compile ES6 JavaScript to ES5 code:

> babel es6-source.js --out-file es5-build.js


## Traceur

[Traceur](https://github.com/google/traceur-compiler) is a JavaScript.next-to-JavaScript-of-today compiler.

It is rather simple to use Traceur in browser:

<pre><code>
<!DOCTYPE html>
<html>
  <body>
    <h1 id="message"></h1>
    <script src="https://google.github.io/traceur-compiler/bin/traceur.js"></script>
    <script src="https://google.github.io/traceur-compiler/src/bootstrap.js"></script>
    <script type="module">
      class Greeter {
        constructor(message) {
          this.message = message;
        }

        greet() {
          var element = document.querySelector('#message');
          element.innerHTML = this.message;
        }
      };

      var greeter = new Greeter('Hello, world!');
      greeter.greet();
    </script>
  </body>
</html>
</code></pre>




### Reference:

* [es6features](https://github.com/lukehoban/es6features)

* [next ES](https://github.com/google/traceur-compiler/wiki/LanguageFeatures)

* [Babel Tutorial](http://www.tutorialsavvy.com/2015/05/next-generation-javascript-with-babel.html/)
