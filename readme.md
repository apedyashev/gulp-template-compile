# [gulp](https://github.com/wearefractal/gulp)-template-compile-commonjs

> Compile [Lo-Dash templates](http://lodash.com/docs#template) (should work with [Underscore templates](http://underscorejs.org/#template) too). Allows to require templates

## Synopsis

This plugin isModified version of [gulp-template-compile](https://github.com/ingro/gulp-template-compile) plugin, that allows to require templates in commonjs style.

## Install
Plugin is not on npm yet, but you can install it using npm

```
  npm i https://github.com/apedyashev/gulp-template-compile-commonjs.git#0.0.1 --save-dev
```

## Example

### `gulpfile.js`

```js
var gulp = require('gulp');
var template = require('gulp-template-compile-commonjs');
var concat = require('gulp-concat');

gulp.task('default', function () {
	gulp.src('src/*.html')
		.pipe(template())
		.pipe(concat('templates.js'))
		.pipe(gulp.dest('dist'));
});
```

## API

See the [Lo-Dash `_.template` docs](http://lodash.com/docs#template).


### template(options)

### options

Type: `Object`

#### options.name

Type: `Function`
Default: *Relative template path. Example: `templates/list.html`*

You can override the default behavior by supplying a function which gets the current [File](https://github.com/wearefractal/vinyl#constructoroptions) object and is expected to return the name.

Example:

```js
{
	name: function (file) {
		return 'tpl-' + file.relative;
	}
}
```

#### options.namespace
Type: `String`
Default: 'JST'

The namespace in which the precompiled templates will be assigned. Starting from version **1.0** you could also provide a dotted namespace that will be correctly handled, thanks to **fhawkes**. For example 'custom.namespace' will result in `window['custom']['namespace']`.

#### options.templateSettings
Type: `Object`
Default: null

[Lo-Dash `_.template` options](http://lodash.com/docs#template).

## License

MIT © Emanuele Ingrosso
