# 前端笔试题目
@[笔试]

--------------------------

[TOC]

--------------------------

## Ajax

> AJAX 是一种在无需重新加载整个网页的情况下，能够更新部分网页的技术。
> AJAX = 异步 JavaScript 和 XML。

### 1. 创建 XMLHttpRequest 对象的语法

``` javascript
var xmlhttp;
if(window.XMLHttpRequest){
    // for IE7+, Firefox, Chrome, Opera, Safari
    xmlhttp = window.XMLHttpRequest();
}else{
    // code for IE6, IE5
    xmlhttp = new ActiveXObject("Microsoft.XMLHTTP");
}
```

### 2. 向服务器发送请求

> open() 和 send() 方法用于向服务器发送请求 

``` javascript
xmlhttp.open("GET","test1.txt",true);
xmlhttp.send();
```

``` javascript
/**
* 规定请求的类型、URL 以及是否异步处理请求。
* method：请求的类型；GET 或 POST
* url：文件在服务器上的位置
* async：true（异步）或 false（同步）
*/
open(method,url,async)
```

``` javascript
/**
* 将请求发送到服务器。
* string：仅用于 POST 请求
*/
send(string)
```

### 3. 服务器的响应

> XMLHttpRequest 对象的 responseText 或 responseXML 属性可获得服务器的响应
> responseText： 获得字符串形式的响应数据。
> responseXML：获得 XML 形式的响应数据。

### 4. onreadystatechange 事件

> onreadystatechange    
>> 存储函数（或函数名），每当 readyState 属性改变时，就会调用该函数。

> readyState    
>> 存有 XMLHttpRequest 的状态。从 0 到 4 发生变化。
>> 0. 请求未初始化
>> 1. 服务器连接已建立
>> 2. 请求已接收
>> 3. 请求处理中
>> 4. 请求已完成，且响应已就绪

> status    
> >200: "OK"
>> 404: 未找到页面

``` javascript
xmlhttp.onreadystatechange = function(){
    if (xmlhttp.readyState ==4 && xmlhttp.status == 200){
        console.log(xmlhttp.responseText);
    }
}
```

## jquery bind() live() delegate() on() 区别
### 介绍
- bind(type,[data],fn) 为每个匹配元素的特定事件绑定事件处理函数
- live(type,[data],fn) 给所有匹配的元素附加一个事件处理函数，即使这个元素是以后再添加进来的
- delegate(selector,[type],[data],fn) 指定的元素（属于被选元素的子元素）添加一个或多个事件处理程序，并规定当这些事件发生时运行的函数
- on(events,[selector],[data],fn) 在选择元素上绑定一个或多个事件的事件处理函数
### 区别
- .bind()是直接绑定在元素上
- .live()则是通过冒泡的方式来绑定到元素上的。更适合列表类型的，绑定到document DOM节点上。和.bind()的优势是支持动态数据。
- .delegate()则是更精确的小范围使用事件代理，性能优于.live()
- on()则是最新的1.9版本整合了之前的三种方式的新事件绑定机制

## 浏览器内核
- Trident内核：代表作品是IE
- Gecko内核：代表作品是Firefox
- Webkit内核：代表作品是Safari、曾经的Chrome
- Presto内核：代表作品是Opera，Presto是由Opera Software开发的浏览器排版引擎，它是世界公认最快的渲染速度的引擎。在13年之后，Opera宣布加入谷歌阵营，弃用了
- Blink内核：由Google和Opera Software开发的浏览器排版引擎，2013年4月发布。现在Chrome内核是Blink

## contact、String

``` javascript
var a = [1,2,3];
var b = a.contact([4,5]);// a:[1,2,3] b:[1,2,3,4,5]
```

## typeof String null
``` javascript
var s = new String(); // typeof s === "object"
var n = null; // typeof n === "object"
```

## :link :vistited :hover :active 顺序

- :link 未被访问的链接样式
- :vistited 已访问页面的的链接样式
- :hover  鼠标指针浮动到链接样式
- :active 点击链接时的样式
``` css
a:link { color: #aaa; } 
a:visited { color: #f30000; } 
a:hover { color: #eee; } 
a:active { color: #d312e8; }
```