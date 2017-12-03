使用 gulp 编译 Sass
==================

## gulp-sass


请务必理解如下章节后阅读此章节：

1. [安装 Node 和 gulp](chapter1.md)
2. [使用 gulp 压缩 JS](chapter3.md)


----------

> Sass 是一种 CSS 的开发工具，提供了许多便利的写法，大大节省了开发者的时间，使得 CSS 的开发，变得简单和可维护。

本章使用 `ruby-sass` 编译 css,若你没有安装 ruby 和 sass 请移步 [使用ruby.taobao安装 Sass](https://github.com/nimojs/blog/issues/14)

安装
---

```
cnpm install gulp-ruby-sass
```

基本用法
-------


```js
// 获取 gulp
var gulp = require('gulp')
// 获取 gulp-ruby-sass 模块
var sass = require('gulp-ruby-sass')

// 编译sass
// 在命令行输入 gulp sass 启动此任务
gulp.task('sass', function() {
    return sass('sass/') 
    .on('error', function (err) {
      console.error('Error!', err.message);
   })
    .pipe(gulp.dest('dist/css'))
});


// 在命令行使用 gulp auto 启动此任务
gulp.task('auto', function () {
    // 监听文件修改，当文件被修改则执行 images 任务
    gulp.watch('sass/**/*.scss', ['sass'])
});

// 使用 gulp.task('default') 定义默认任务
// 在命令行使用 gulp 启动 sass 任务和 auto 任务
gulp.task('default', ['sass', 'auto'])
```


Sass 代码和编译后的 CSS 代码
----------


```css
.sass{
	a{
        color:pink;
    }
}
```



```css
@import "a.scss";
.import{
	a{
		color:red;
    }
}
```


```css
.sass a {
  color: pink;
}
```



```css
.sass a {
  color: pink;
}
.import a{
  color: red;
}
```


[接着阅读：使用 gulp 开发一个项目](chapter8.md)
