---
title: JavaScript 分析代码
date: 2019-03-26 11:08:06
tags: JavaScript
categories: 面试题
---
### 1、`Javascript`中, 以下哪条语句一定会产生运行错误？      答案(    )
A、`var _变量=NaN;`
B、`var 0bj = [];`
C、`var obj = //;`	
D、`var obj = {};`
<!--more-->
```js
b. Uncaught SyntaxError: Invalid or unexpected token
c. Uncaught SyntaxError: Unexpected end of input
```
### 2、以下两个变量a和b，a+b的哪个结果是NaN？      答案(    )
A、`var a=undefind; b=NaN`
B、`var a=‘123’; b=NaN`
C、`var a =undefined , b =NaN`
D、`var a=NaN , b='undefined'`
```js
a. Uncaught ReferenceError: undefind is not defined
b. 123NaN
c. NaN
d.NaNundefined
```
### 3、var a=10; b=20; c=4;  ++b+c+a++ 以下哪个结果是正确的？答案(    )
A、34   
B、35  
C、36 
D、37
```js
var a=10; b=20; c=4;  
++b+c+a++ 
	=> 
21+4+10=35;
```
### 4、下面的JavaScript语句中，（ D ）实现检索当前页面中的表单元素中的所有文本框，并将它们全部清空
```js
A. for( var i=0; i <  form1.elements.length; i++) {
	if(form1.elements.type==”text”)
	form1.elements.value=”";
}
B. for(var i=0;i < document.forms.length; i++) {
	if(forms[0].elements.type==”text”)
	forms[0].elements.value=”";
}
C. if(document.form.elements.type==”text”) form.elements.value=”";
D. for(var i=0;i < document.forms.length;  i++){
	for(var j=0; j< document.forms.elements.length; j++) {
		if(document.forms.elements[j].type==”text”)
		document.forms.elements[j].value=”";
	}
}
```
### 5、要将页面的状态栏中显示“已经选中该文本框”，下列JavaScript语句正确的是（ A ）
A. `window.status=”已经选中该文本框”`
B. `document.status=”已经选中该文本框”`
C. `window.screen=”已经选中该文本框”`
D. `document.screen=”已经选中该文本框”`
### 6、以下哪个单词不属于javascript保留字：（B） 
A.	`with` 
B.	`parent` 
C.	`class `
D.	`void`
### 7、请选择结果为真的表达式：（C） 
A. `null instanceof Object `
B. `null === undefined` 
C. `null == undefined` 
D. `NaN == NaN`
### 8、分析代码，得出正确的结果。
```javascript
var a=10, b=20 , c=30;
++a;
a++;
e=++a+(++b)+(c++)+a++;
alert(e);
```
弹出提示对话框：77
```javascript
var a=10, b=20 , c=30;
++a;//a=11
a++;//a=11
e=++a+(++b)+(c++)+a++;
//a=12  13+21+30+13=77
alert(e);
```
### 9、写出函数DateDemo的返回结果，系统时间假定为今天(2010.8.17)
```javascript
function DateDemo(){
	var d, s="今天日期是：";
	d = new Date();
	s += d.getMonth() + "/";
	s += d.getDate() + "/";
	s += d.getFullYear();
	return s;
}
结果：今天日期是：7/17/2010
```
### 10、写出程序运行的结果？
```javascript
for(i=0, j=0; i<10, j<6; i++, j++){
	k = i + j;
}
//结果：10
for(i=0, j=0; i<10, j<6; i++, j++){
    //j=5 i=5
    k = i + j;//k=10
}
//结果：10
```
### 11、阅读以下代码，请分析出结果：
```javascript
var arr = new Array(1,3,5);
arr[4]='z';//[1,3,5,undefined,’z’]
arr2 = arr.reverse();//arr2=[’z’,undefined,5,3,1];arr=[’z’,undefined,5,3,1]
arr3 = arr.concat(arr2);
alert(arr3);
弹出提示对话框：z,,5,3,1,z,,5,3,1
//reverse方法颠倒数组中元素的位置，并返回该数组的引用。该方法会改变原数组。
```

### 下午和兄弟一起讨论了用 JavaScript 写一个输入小时和分钟，判断时针和分针的夹角问题
```js
//我的思路
//一圈360° 一分钟的度数等于 360/60 = 6° 一小时的度数 360/12 = 30°  分针走的是小时的一部分 重贴部分 30°/60 = 0.5° 没有处理24小时
var getAngle = function(hour,min) {
    var angle = 0;
    if(min == 0) {
        angle = hour > 6 ? (12 - hour) * 30 : hour * 30
    }else{
        angle = min * (6 - 0.5) - (hour * 30) > 180 ? 360 - (min * (6 - 0.5) - hour * 30) : min * (6 - 0.5) - (hour * 30)
    }
    return Math.abs(angle);
}
//兄弟的思路
//分针走的度数 min/60*360 时钟走的度数 (h%12 + m/60)/12*360 支持24小时
var getAngle = function(h,m) {
    var angle = m/60*360 - ((h%12 + m/60)/12*360)
    angle = angle > 180 ? 360 - angle : angle 
    return Math.abs(angle) 
}
```