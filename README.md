# gulp-add-less-variables

Add variables to less files in gulp-plugin config options.

[![Package Quality](http://npm.packagequality.com/badge/gulp-add-less-variables.png)](http://packagequality.com/#?package=gulp-add-less-variables)

## Examples

### Prepend

`var1, var2, var3` will be added at beginning of file:

```JavaScript

var gulp     = require('gulp');
var concat   = require("gulp-concat");
var less     = require('gulp-less');
var lessVars = require('gulp-add-less-variables');

gulp.task('less', function() {
    gulp.src(lessFiles)
        .pipe(lessVars({
            var1: '10px', // => @var1: '10px'
            var2: '20px', // => @var2: '20px'
            var3: ['#000000', '#ffffff', '#acacac'] // => @var3: '#000000, #ffffff, #acacac'
        }))
        .pipe(less())
        .pipe(concat('style.css'))
        .pipe(gulp.dest('./public/css'));
});

```

### Append

By setting the second argument to `true`, you can override any variables already defined in your less files.

`var1, var2, var3` will be appended to end of file:

```JavaScript

var gulp     = require('gulp');
var concat   = require("gulp-concat");
var less     = require('gulp-less');
var lessVars = require('gulp-add-less-variables');

gulp.task('less', function() {
    gulp.src(lessFiles)
        .pipe(lessVars({
            var1: '10px', // => @var1: '10px'
            var2: '20px', // => @var2: '20px'
            var3: ['#000000', '#ffffff', '#acacac'] // => @var3: '#000000, #ffffff, #acacac'
        }, true))
        .pipe(less())
        .pipe(concat('style.css'))
        .pipe(gulp.dest('./public/css'));
});

```
