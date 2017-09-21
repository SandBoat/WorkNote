# 前端面试题目
@[面试]

--------------------------

[TOC]

--------------------------

## this指向
### 普通this

- 总是指向调用者
- 在默认情况(非严格模式下,未使用 'use strict'),没找到直接调用者,则this指的是 window
- 在严格模式下,没有直接调用者的函数中的this是 undefined
- 使用call,apply,bind(ES5新增)绑定的,this指的是 绑定的对象

### 箭头函数this

- 默认指向在定义它时,它所处的对象(宿主对象),而不是执行时的对象, 定义它的时候,可能环境是window

### 使用场景

``` javascript
var People = {
    age:1,
    sayAge:function(){
        console.log(this.age);
    },
    sayAge2:() => {
        console.log(this.age);
    }
}

var p = People.sayAge;
People.sayAge();    // 1
p();                // undefined
People.sayAge2();   // undefined
```
``` javascript
window.val = 1;
var obj = {
    val: 2,
    dbl: function() {
        this.val *= 2;
        val *= 2;
        console.log(val);
        console.log(this.val);
    }
};

obj.dbl();  // 2 4
var func = obj.dbl;
func(); // 8 8
```
``` javascript
var obj = {
  say: function () {
    var f1 = function () {
      console.log(this);    // window, f1调用时,没有宿主对象,默认是window
      setTimeout(() => {
        console.log(this); // window
      })
    };
    f1();
  }
}
obj.say()
```

## 说一下你对 CSS 盒模型的理解？

- 盒模型包括的属性
- box-sizing

## 对于一个未知宽高的盒子，如何让它水平垂直居中于父元素？

- table
- JS 计算
- transform
- flexbox
- grid

## 简单说下 flexbox 布局？

- flexbox 布局解决的问题（未出现之前，布局的缺陷）
- flexbox 的兼容性
- flexbox 的局限（引出 grid 布局）

## 说下你对 CSS3 动画的理解？

- transition
- animation
- 动画性能（transform、3D等）

## 简单说下你对一些小图标的处理？

- 雪碧图
- iconfont
- svg sprites

## 浏览器缓存的头字段有哪些，缓存的逻辑是怎样的？

- 缓存
- 引申：200 和 304 的区别

## 创建一个有十行十列的表格（不准 innerHTML），并给每个单元格绑定事件。

- DOM 操作
- 事件委托

## 写个 Person 类，属性 name 公有，属性 age 私有；写个 Student 继承 Person，并有自己的公有属性 grade 和公有方法 getTeacher。

- 面向对象（变量，方法，私有/公有，继承...）

## HTTP 常见的状态码，301，302 等；POST 和 GET 的区别。

- 网络（状态码，请求方法...）

## 有没有碰到过跨域请求，你是怎么处理的？

- 跨域（jsonp，CORS...）

## 写个正则匹配下邮箱、手机号

- 正则

## 接触过哪些构建工具；现在用的是啥；写出你现在项目的目录结构，并解释构建工具的运作方式；有否写过插件？

- 构建（fis3、gulp、webpack...）

## 你写代码的时候是怎么考虑安全因素的？

- 安全（xss、csrf...）

## 给你的代码写过单元测试吗；为了更好地单测你是怎么组织你的代码的；我这里有份代码，你看怎么给每个函数写个单测？

- 单元测试（Mocha...）

## 有没有做过性能优化，都有哪些手段？

- 雅虎35条
