# gulp-untar

Extract tarballs in your [gulp](http://gulpjs.com) build pipeline

Accepts source files with either stream or Buffer contents. Outputs files with
Buffer contents.

## Install

```bash
$ npm install --save-dev gulp-untar2
```
## Usage

```js
  var gulp = require('gulp')
  var untar = require('gulp-untar2')

  gulp.task('extract-archives', function () {
    return gulp.src('./archive/*.tar')
      .pipe(untar())
      .pipe(gulp.dest('./extracted'))
  })
```

In combination with [gulp-gunzip](https://github.com/jmerrifield/gulp-gunzip) and
[vinyl-source-stream](https://github.com/hughsk/vinyl-source-stream):

```js
var gulp = require('gulp')
var request = require('request')
var source = require('vinyl-source-stream')
var gunzip = require('gulp-gunzip')
var untar = require('gulp-untar2')

gulp.task('default', function () {
  return request('http://example.org/some-file.tar.gz')
  .pipe(source('some-file.tar.gz'))
  .pipe(gunzip())
  .pipe(untar())
  .pipe(gulp.dest('output'))
})
```

## License

[MIT](http://opensource.org/licenses/MIT)

© [Jon Merrifield](http://www.jmerrifield.com)
