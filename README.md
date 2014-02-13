# gulp-dot-precompiler

[Gulp](https://github.com/gulpjs/gulp) plugin for precompilation of [doT](https://github.com/olado/doT) templates. Forked from [titarenko/gulp-dotify](https://github.com/titarenko/gulp-dotify) but with more control and much more logical.

## Status

[![Build Status](https://secure.travis-ci.org/kentliau/gulp-dot-precompiler.png?branch=master)](https://travis-ci.org/kentliau/gulp-dot-precompiler)
[![NPM version](https://badge.fury.io/js/gulp-dot-precompiler.png)](http://badge.fury.io/js/gulp-dot-precompiler)
[![Coverage Status](https://coveralls.io/repos/kentliau/gulp-dot-precompiler/badge.png)](https://coveralls.io/r/kentliau/gulp-dot-precompiler)

[![NPM](https://nodei.co/npm/gulp-dot-precompiler.png)](https://nodei.co/npm/gulp-dot-precompiler/)

## Example

If we have following folder structure:

```
app/views/users/list.dot
app/views/users/detail.dot
app/views/products/list.dot
app/views/products/detail.dot
app/views/layout.dot
```

Then, running this code:

```js
var dot = require('gulp-dot-precompiler'),
    concat = require('gulp-concat'), // npm install gulp-concat --save
    header = require('gulp-header'); // npm install gulp-header --save

gulp.task('templates', function() {
  gulp.src('app/views/**/*.dot')
  .pipe(dot())
  .pipe(concat('templates.js'))
  .pipe(header('window.render = {};'))
  .pipe(gulp.dest('public/js'));
});
```

Will produce `public/js/templates.js`:

```js
window.render = {};
render['users.list'] = function ...
render['users.detail'] = function ...
...
render['layout'] = function ...
```

## Options

* root --  prepend a name for the template name, default ''
* extension -- append a name for the template name, default ''
* separator -- separator for the name, default '.'
* dictionary -- template function name, default 'render'
* varname -- refer [doT](https://github.com/olado/doT), default 'data'
* strip -- refer [doT](https://github.com/olado/doT), default true
* append -- refer [doT](https://github.com/olado/doT), default true
* selfcontained -- refer [doT](https://github.com/olado/doT), default false

## License

MIT