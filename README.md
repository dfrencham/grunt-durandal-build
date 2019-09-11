
Grunt task to build Durandal projects using a custom require config with a custom almond

This is a fork of **grunt-durandal**

## Getting Started

Install this grunt plugin next to your project's gruntfile with: `npm install grunt-durandal-build --save-dev`

Then add this line to your project's `Gruntfile.js` :

```javascript
grunt.loadNpmTasks("grunt-durandal");
```

Then specify your config:

```javascript
grunt.initConfig({
    durandal: {
        dist: {
            src: [
				"app/**/*.*",
				"scripts/durandal/**/*.*"
			],
            options: {
                baseUrl: "app/",
                mainPath: "app/main.js",
                out: "app/main-built.js",

                uglify2: {
                    compress: {
                        global_defs: {
                            DEBUG: false
                        }
                    }
                }
            }
        }
    }
});
```

To stop a require statement being added to the end of the file, pass in
the **insertRequire: false** option.

Using the configuration above, consider the following app structure :

* App
    * viewmodels
        * shell.js
        * home.js
    * views
        * shell.html
        * home.html
    * main.js
* Scripts
    * durandal 
        * all durandal files
	* require.js
	* text.js
	* almond-custom.js

After running the grunt task, a main-built file will be created in your app folder.
This file contains a custom almond, and all your modules inlined (views included as text!...)

## Release History
* 0.0.1 Initial Release
* 0.1.0 Update to Durandal 2.0
* 0.1.1 Fix issue with path separator on Windows
* 0.1.2 Fix naming path issue by renaming path for forced includes
* 0.1.3 Append a includeMain options which allow to disable automatic main include
* 2.0.0 Add Grunt 1.x compatibility
* 2.1.0 Fix logic for insertRequire option

[grunt]: https://github.com/gruntjs/grunt
[doc-options]: https://github.com/dfrencham/grunt-durandal-build/wiki/Task-Options