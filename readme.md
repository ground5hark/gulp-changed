# [gulp](http://gulpjs.com)-changed-old

Forked for compatibility with node 0.8.0, based off of the original [gulp-changed](https://github.com/sindresorhus/gulp-changed)

> Only pass through changed files

No more wasting precious time on processing unchanged files.


## Install

Install with [npm](https://npmjs.org/package/gulp-changed-old)

```
npm install --save-dev gulp-changed-old
```


## Example

```js
var gulp = require('gulp');
var changed = require('gulp-changed-old');
var ngmin = require('gulp-ngmin'); // just as an example

var SRC = 'src/*.js';
var DEST = 'dist';

gulp.task('default', function () {
	gulp.src(SRC)
		.pipe(changed(DEST))
		// ngmin will only get the files that
		// changed since the last time it was run
		.pipe(ngmin())
		.pipe(gulp.dest(DEST));
});
```

## API

### changed(dest, options)

#### dest

Type: `String`

The destination directory. Same as you put into `gulp.dest()`.

This is needed to be able to compare the current files with the destination files.

#### options

Type: `Object`

Set `options.extension` value to specify extension of the destination files.

```
gulp.task('jade', function() {
	gulp.src('./src/**/*.jade')
		.pipe(changed('./app/', { extension: '.html' }))
		.pipe(jade())
		.pipe(gulp.dest('./app/'))
});
```

## License

MIT © [Sindre Sorhus](http://sindresorhus.com)
