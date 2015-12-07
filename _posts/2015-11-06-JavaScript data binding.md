Data binding is rather different than what jQuery did(DOM manipulation). 

The most popular frameworks for now

## React
[React](http://facebook.github.io/react/) is One-way data binding library. 

* Lots of people use React as the V in MVC. 

* Virtual DOM to boost performance

* one-way reactive data flow: React will automatically manage all UI updates when your underlying data changes. It uses a fast, internal mock DOM to perform diffs and computes the most efficient DOM mutation for you.

* Composable Components: With React the only thing you do is build components. Since they're so encapsulated, components make code reuse, testing, and separation of concerns easy.

* JSX: a JavaScript syntax extension that looks similar to XML which lets you create JavaScript objects using HTML syntax

* props vs state: "props" which is immutable parameter passed from parent, "state" is internal state of component.

* What Components Should Have State?
Most of your components should simply take some data from props and render it. However, sometimes you need to respond to user input, a server request or the passage of time. For this you use state.

Try to keep as many of your components as possible stateless. By doing this you'll isolate the state to its most logical place and minimize redundancy, making it easier to reason about your application.

A common pattern is to create several stateless components that just render data, and have a stateful component above them in the hierarchy that passes its state to its children via props. The stateful component encapsulates all of the interaction logic, while the stateless components take care of rendering data in a declarative way.


## AngularJS

[AngularJS](https://angularjs.org) is a full MVC framework

* two-way data binding

* reusable components


## Polymer

Google Polymer is the de-factor starndard for JS web components SPEC.


### Reference

* [why react](http://facebook.github.io/react/docs/why-react.html)

* [JSX in depth](http://facebook.github.io/react/docs/jsx-in-depth.html)

* [react props vs state](http://facebook.github.io/react/docs/interactivity-and-dynamic-uis.html)

* [AngularJS vs jQuery](http://stackoverflow.com/questions/14994391/thinking-in-angularjs-if-i-have-a-jquery-background)

* [AngularJS vs jQuery2](http://stackoverflow.com/questions/13151725/how-is-angularjs-different-from-jquery)

* [AngularJS data binding](http://stackoverflow.com/questions/9682092/angularjs-how-does-databinding-work)

* [React and jQuery](http://hackflow.com/blog/2015/03/08/boiling-react-down-to-few-lines-in-jquery/)

* [virtual DOM](https://github.com/Matt-Esch/virtual-dom)

* [Polymer](https://www.polymer-project.org/1.0/)



