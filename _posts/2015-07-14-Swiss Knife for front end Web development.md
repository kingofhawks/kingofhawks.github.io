Swiss Knife for front end Web development

## Scaffolding

### Yeoman

[Yeoman](http://yeoman.io/) provide a generator ecosystem, helps you to kickstart new projects, prescribing best practices and tools to help you stay productive.

A generator is basically a plugin that can be run with the `yo` command to scaffold complete projects or useful parts.Yeoman provided official generators for the most pupular frameworks,such as AnguarJS,Backbone, Polymer etc.

The Yeoman workflow comprises three types of tools for improving your productivity and satisfaction when building a web app: the scaffolding tool (yo), the build tool (Grunt, Gulp, etc) and the package manager (like Bower and npm).

It is rather hard to install Yeoman under Windows and China, something to be comment here:

* change npm registry source: npm config set registry https://registry.npm.taobao.org

* install yo: npm install -g yo

* Manually add this path to Windows PATH: C:\Users\Simon\AppData\Roaming\npm



## Dependency management

### Bower

[Bower](http://bower.io/) is the package manager for Web.


### NPM

[NPM](https://www.npmjs.com/) is the package manager for Node.It comes with Node now.


### NPM browserify

Browsers don't have the require method defined, but Node.js does. With [Browserify](http://browserify.org/) you can write code that uses require in the same way that you would use it in Node.


### WebPack

[webpack](http://webpack.github.io/docs/) is a module bundler.

webpack takes modules with dependencies and generates static assets representing those modules.



## Build Systems

### Grunt

[Grunt](https://github.com/gruntjs/grunt) is the JS task runner, same as Ant for Java.The less work you have to do when performing repetitive tasks like minification, compilation, unit testing, linting, etc, the easier your job becomes. 

Grunt use the Gruntfile.js or Gruntfile.coffee configuration file, which is a valid JavaScript or CoffeeScript file that belongs in the root directory of your project.


### Gulp

[Gulp](https://github.com/gulpjs/gulp) is another JS task runner, which use Node streaming build system and aims to replace Grunt.

By preferring code over configuration, gulp keeps things simple and makes complex tasks manageable.


### Brunch
[Brunch](https://github.com/brunch/brunch) is a builder. Not a generic task runner, but a specialized tool focusing on the production of a small number of deployment-ready files from a large number of heterogenous development files or trees.

Brunch also support Skeletons which is basically an application boilerplate that provides a good starting point for new applications, same as Yeoman generator does.


### Broccoli
[Broccoli](https://github.com/broccolijs/broccoli) is a less popular, fast, reliable asset pipeline, supporting constant-time rebuilds and compact build definitions. 


### Reference
- [Task Runner Compare](https://github.com/brunch/brunch-guide/blob/master/content/en/chapter01-whats-brunch.md#brunch-vs-others)
- [Task Runner Compare2](http://brunch.io/compare.html)
- [Grunt vs Gulp](http://sixrevisions.com/web-development/grunt-vs-gulp/)
- [Module System](http://webpack.github.io/docs/motivation.html)
- [Install Yoeman on Windows](https://github.com/joyent/node/issues/4356)

