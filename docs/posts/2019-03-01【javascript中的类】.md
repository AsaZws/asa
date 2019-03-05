---
title: 2019-03-01【javascript中的类】
date: 2019-03-01 09:01:08
tags: [javascript》]
categories: [javascript]
---

### ES5中的类
在ES5中，我们把 new 理解成 javascript 面向对象的一部分，下面我们就来看一下 new 操作具体为我们做了那些事情。 


new运算符接收一个构造器和一组调用参数，实际上做了几件事：
    1.以构造器的prototype属性（注意与私有字段[[prototype]]的区分）为原型，创建新对象；
    2.将this和调用参数传给构造器，执行；
    3.如果构造器返回的是对象，则返回，否则返回第一步创建的对象。
new这样的行为，试图让函数对象在语法上跟类变得相似，但是，它客观上提供了两种方式，一是在构造器中添加属性，二是在构造器的prototype属性上添加属性。


下面代码展示了用构造器模拟类的两种方法：
```js
function c1() {
this.p1 = 1;
this.p2 = function (){
    console.log(this.p1);
}
}
var o1 = new c1;
o1.p2();


function c2(){
}
c2.prototype.p1 = 1;
c2.prototype.p2 = function (){
console.log(this.p1);
}
var o2 = new c2;
o2.p2();
```
第一种方法是直接在构造器中修改this，给this添加属性。  
第二种方法是修改构造器的prototype属性指向的对象，它是从这个构造器构造出来的所有对象的原型。  
### ES6中的类  
ES6中引入了classES6 中引入了 class 关键字，并且在标准中删除了所有[[class]] 相关的私有属性描述，类的概念正式从属性升级成语言的基础设施，从此，基于类的编程方式成为了 JavaScript 的官方编程范式。  


我们先看下类的基本写法：  
```js
class Rectangle {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
  // Getter
  get area() {
    return this.calcArea();
  }
  // Method
  calcArea() {
    return this.height * this.width;
  }
}

```
在现有的类语法中，getter/setter 和 method 是兼容性最好的。  
我们通过 get/set 关键字来创建 getter，通过括号和大括号来创建方法，数据型成员最好写在构造器里面。  
类的写法实际上也是由原型运行时来承载的，逻辑上 JavaScript 认为每个类是有共同原型的一组对象，类中定义的方法和属性则会被写在原型对象之上。