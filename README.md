# gulp-template-inline-js
在js文件中嵌入template文件
## 安装
    npm i gulp-template-inline-js --save-dev
## 使用方法
    var gulp = require('gulp'),
        templateInline = require('gulp-template-inline-js');

    gulp.task('js',function() {
      return gulp.src(['src/js/*.js'])
        .pipe(templateInline())
        .pipe(gulp.dest('dest/js'))  
    });

## JS使用方法
可引入模板
var tpl = __template("../tpl/xxx.tpl");
var html = tpl();
可内联JS
__inline("../tpl/xxx.tpl");
