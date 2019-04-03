---
title: 关于 Object 和局部变量的理解
date: 2019-03-28 10:26:16
tags: JavaScript
---

# 在面试题中看到一个题目（如下）
```js
function setN(obj){
    obj.num='1';
    obj = new Object();
    obj.num = '2';
};
var per = new Object();
setN(per);
console.log(per.num); //1
```
<!--more-->
- 最开始看到这个题目的时候，看了一下这不应该打印 2 嘛！后来一运行发现是输出 1 ，自己的表情是？？？？ 
- 后来仔细分析了一下才发现其中的端倪，在 setN 函数中重写了形参 obj 的时候就已经和实参的 per 没有关系了，让 obj 变成了一个局部变量
- 所以输出 per.num 的结果才会是 1 后续的赋值仅仅是赋值给了 setN 函数内的局部变量 obj 其中 obj.num 为 2 。