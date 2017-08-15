# gulp-template-inline-js
## 作用 
	在js文件中嵌入template文件,编译成underscore模板语法的生成函数
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

#从JS里引入test.tpl模板文件

	var tpl = __template("../tpl/test.tpl");
	var html = tpl({data:[1,3,4,5]});

	test.tpl文件
 
	<% for (var i = 0; i < data.length; i++) { %>
		<li><%= data[i] %></li>
	<% } %>

#编译后可得

	var tpl = function(obj){
	var __t,__p='',__j=Array.prototype.join,print=function(){__p+=__j.call(arguments,'');};
	with(obj||{}){
		__p+='';
		 for (var i = 0; i < data.length; i++) { 
			__p+='<li>'+
			((__t=( data[i] ))==null?'':__t)+
			'</li>';
		 } 
		__p+='';
	}
	return __p;
	};

	var html = tpl({data:[12,3,4,5]});
# 具体可参考[underscore](http://http://www.css88.com/doc/underscore/#template "underscore") 

#也可在JS里内联JS文件

	__inline("../js/foo.js");

编译可得，

	function foo () { 
		bar();
	}

注意，不要__inline模板文件，否则会引起js报错

#changelog

v1.06 修复遇到模板'符号报错的bug
v1.07 修复模板多次调用报错的问题