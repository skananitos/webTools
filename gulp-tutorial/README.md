# GULP tutorial

Create the following package.json file in the project's folder with the following content:

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


### Installing Gulp

At the command prompt, type the following to install Gulp command-line interface (CLI) globally:

```
npm install -g gulp
```

After that, install Gulp to use within your project. To do this, go to the prject's folder and type the following at the prompt:

```
npm install gulp --save-dev
```

### Install Gulp Plugins

Install all the Gulp plugins that you will need for this example. To do this, type the following at the command prompt:

```
npm install jshint gulp-jshint jshint-stylish gulp-imagemin gulp-concat gulp-uglify gulp-minify-css gulp-usemin gulp-cache gulp-changed gulp-rev gulp-rename gulp-notify  browser-sync del --save-dev
```


### Creating a Gulp File

1. Create a Gulp file containing the tasks to be run when you use Gulp. To do this, create a file named *gulpfile.js* in the project's folder.

2. Load in all the Gulp plugins by including the proper code in the Gulp file.

3.Add the code for the JSHint task, the Clean task, the default task, the usemin, imagemin and copyfonts tasks and the watch and browserSync tasks.


### Running the Gulp Tasks

At the command prompt, if you type gulp it will run the default task: `gulp`


### Using BrowserSync and Watch

We configured the BrowserSync and the Watch tasks in the Gulp file. To use them, type the following at the command prompt:
     
```
gulp watch
```