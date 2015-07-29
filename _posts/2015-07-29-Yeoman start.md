[Yeoman](http://yeoman.io/) is a great scaffolding tool for web development.

But it will take you some time to start on Windows:

1. Install node.js

2. Install ruby if you need Compass support

3. Install bower and grunt

> npm install -g yo bower grunt-cli

4. Install generator for Karma and Angular project

> npm install -g generator-karma generator-angular

5. Generate scaffolding project for AngularJS
> mkdir hello
> cd hello 
> yo angular

6. start project

> grunt serve

If you encounter error about bower packages:

> Running "wiredep:app" (wiredep) task 
> Warning: Error: Cannot find where you keep your Bower packages. Use --force to continue.
> Aborted due to warnings.

you need to install packages manually:

> bower install