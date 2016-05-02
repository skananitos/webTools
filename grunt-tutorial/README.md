# GRUNT tutorial

This is a sample of how to use Grunt and the exetentions you need to install.


### Installing Grunt

At the command prompt, type the following to install Grunt command-line interface (CLI):

```npm install -g grunt-cli```

This will install the Grunt CLI globally so that you can use them in all projects.

Next, create the package.json file in the project's folder with the following content:

```
{
  "name": "projectFolder",
  "private": true,
  "devDependencies": {

  },
  "engines": {
    "node": ">=0.10.0"
  }
}
```

Next install Grunt to use within your project. To do this, go to the project's folder and type the following at the prompt:

```npm install grunt --save-dev```

This will install local per-project Grunt to use within your project.


### Creating a Grunt File

Create a Grunt file containing the configuration for all the tasks to be run when you use Grunt. To do this, create a file named *Gruntfile.js
* in the project's folder. Add the following code to Gruntfile.js to set up the file to configure Grunt tasks:

```
'use strict';

module.exports = function (grunt) {

  // Define the configuration for all the tasks
  grunt.initConfig({

  });

};
```

This sets up the Grunt module ready for including the grunt tasks inside the function above.


### Configuring the Project

We need to configure the home page (home.html) file for this example. In the home.html file we have to update the CSS import lines in the head of the page as follows:

```
<!-- build:css styles/main.css -->
    <link href="styles/style.css" rel="stylesheet">
<!-- endbuild -->
```

We are surrounding the links with some specially formatted comment lines, the purpose of which will become clear in a later step.

Similarly, replace all the script at the bottom of the page with the following code:

```
<!-- build:js scripts/main.js -->
    <script src="../bower_components/angular/angular.min.js"></script>
    <script src="scripts/app.js"></script>
<!-- endbuild -->
```

### The JSHint Task

We are going to set up our first Grunt task. The *JSHint task* validates our JavaScript code and points out errors and gives warnings about minor violations. To do this, you need to include some Grunt modules that help us with the tasks. Install the following modules by typing the following at the prompt:

```
npm install grunt-contrib-jshint --save-dev
npm install jshint-stylish --save-dev
npm install time-grunt --save-dev
npm install jit-grunt --save-dev
```

The first one installs the Grunt module for JSHint, and the second one adds further to print out the messages from JSHint in a better format. The time-grunt module generates time statistics about how much time each task consumes, and jit-grunt enables us to include the necessary downloaded Grunt modules when needed for the tasks.

After that we have to configure the JSHint task in the Gruntfile.js. In this code, we have set up time-grunt and jit-grunt to time the tasks, and load Grunt modules when needed. The JSHint task is set to examine all the JavaScript files in the app/scripts folder, and the Gruntfile.js and generate any reports of JS errors or warnings. We have set up a Grunt task named build, that runs the jshint task and the build task is also registered as the default task.

Following this we have to create a file named .jshintrc in the project's folder. Now we can run the grunt task by typing the following at the prompt: `grunt`


### Copying the Files and Cleaning Up the Dist Folder

We have to install the Grunt modules to copy over files to a distribution folder named dist, and clean up the dist folder when needed. To do this, we need to install the following Grunt modules:

```
npm install grunt-contrib-copy --save-dev
npm install grunt-contrib-clean --save-dev
```

After that, we add the proper code to perform the copying of files to the dist folder, and cleaning up the dist folder to Gruntfile.js. (this should be added right after the configuration of the JSHint task).


### Preparing the Distribution Folder and Files

We are now going to use the Grunt usemin module together with concat, cssmin, uglify and filerev to prepare the distribution folder. To do this, we have to install the following Grunt modules:

```
npm install grunt-contrib-concat --save-dev
npm install grunt-contrib-cssmin --save-dev
npm install grunt-contrib-uglify --save-dev
npm install grunt-filerev --save-dev
npm install grunt-usemin --save-dev
```

Then, we update the task configuration within the Gruntfile.js to introduce the new tasks and the jit-grunt configuration, to inform it that useminPrepare task depends on the usemin package. Finally, we have to update the Grunt build task. Now if we run Grunt, it will create a dist folder with the files structured correctly to be distributed to a server to host your website.


### Watch, Connect and Serve Tasks

The final step is to use the Grunt modules **watch, connect and serve**, to spin up a web server and keep a watch on the files and automatically reload the browser when any of the watched files are updated. To do this, we need to install the following grunt modules:

```
npm install grunt-contrib-watch --save-dev
npm install grunt-contrib-connect --save-dev
```

After this, we will configure the connect and watch tasks by adding the proper code to the Grunt file. Then, we add the following task to the Grunt file: 

```
grunt.registerTask('serve',['build','connect:dist','watch']);
```

Now if we type the following at the command prompt, it will build the project, and open the web page in your default browser. It will also keep a watch on the files in the app folder, and if we update any of them, it will rebuild the project and load the updated page into the browser (livereload):

```
grunt serve
```