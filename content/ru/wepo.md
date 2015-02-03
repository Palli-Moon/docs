WEPO - Web Programming II
====
Notes from the web programming II course (wepo) spring 2015.

###### Feb 2, 2015

## npm
### Installing
``` javascript
npm install -g <toolname>
```
The `-g` flag installs the tool globally, rather than for the current project only. It should be used sparingly, most tools should be installed on a project to project basis.

### package.json

A `package.json` file can be created in the project directory listing what packages the project uses.

If a `package.json` file exists, simply running `npm install` will install all the packages specified in the file.

Running the command `npm init` will allow npm to guide you through creating the `package.json` file opting for sensible default options.

By using the `--save-dev` flag when installing a tool with npm, it will automatically add it to the `package.json` dependency list. This is not always recommended since some packages may get updated frequently and manually writing in the version (or range of versions), may be preferred.


## Grunt
Grunt is a taskrunner that can create automated tasks for a project. Grunt should be specified in the `package.json` file and the cli can then be installed using the command below.
``` javascript
npm install -g grunt-cli
```
The Grunt cli is not the Grunt application in itself. It's only a *command-line interface*, used to run the Grunt application located in the project's directory. It should therefore be installed with the `-g` flag.

It is possible to run Grunt without installing the cli by running `node -e "require('grunt').tasks(['test']);"`, substituting `test` with the task(s) to run. For obvious reasons it is in most cases easier to just install the cli.

### The Gruntfile
The `Gruntfile` should then be created as `Gruntfile.js` or `Gruntfile.coffee` in the root of the project. The `Gruntfile` contains every task that should be runnable in the project. An example of a very basic `Gruntfile` with a jshint task would be:
``` javascript
module.exports = function(grunt) {
    grunt.loadNpmTasks('grunt-contrib-jshint');
    var taskConfig = {
        jshint: {
            src: ['**/*.js'],
            gruntfile: ['Gruntfile.js'],
            options: {}
        }
    };
    grunt.initConfig(taskConfig);
};
```
This Grunt task would run jshint (provided it's installed in the project) on every JavaScript file (`*.js`), in every folder (`**`) in the project.

## Notes
#### File structure
When creating large applications large JavaScript applications it's conventional to keep all the source code in a directory named `src`. This separates the application code from configure files like the `package.json` file, or `Grintfile`.