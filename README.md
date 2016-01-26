# TypeScript development with Gulp Automation

<pre>
Introduce TypeScript into web application is easy.
1, go to web dictionary
2, npm install -g gulp
3, npm install typescript -g
4, create a gulpfile.js file as below

var gulp = require('gulp'); 
var jshint = require('gulp-jshint');
var sass = require('gulp-sass');
var concat = require('gulp-concat');
var uglify = require('gulp-uglify');
var rename = require('gulp-rename');
var tsc = require('gulp-typescript-compiler');

 gulp.task('tsc', function () {
    return gulp
      .src('ts/*.ts')
      .pipe(tsc({
          module: '',
          target: 'ES5',
          sourcemap: false,
          logErrors: true
      }))
      .pipe(gulp.dest('dist'));
});

 gulp.task('lint', function() {
    return gulp.src('js/*.js')
        .pipe(jshint())
        .pipe(jshint.reporter('default'));
});

 gulp.task('sass', function() {
    return gulp.src('scss/*.scss')
        .pipe(sass())
        .pipe(gulp.dest('css'));
});

 gulp.task('scripts', function() {
    return gulp.src('js/*.js')
        .pipe(concat('all.js'))
        .pipe(gulp.dest('dist'))
        .pipe(rename('all.min.js'))
        .pipe(uglify())
        .pipe(gulp.dest('dist'));
});

 gulp.task('watch', function() {
    gulp.watch('js/*.js', ['lint', 'scripts']);
    gulp.watch('scss/*.scss', ['sass']);
});

 gulp.task('default', ['tsc','lint', 'sass', 'scripts', 'watch']);
 
 5, run gulp 
 6, check the result
 7, typescript can be teached in http://www.typescriptlang.org/ 
 
</pre>
