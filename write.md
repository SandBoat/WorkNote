# 笔试题目

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


