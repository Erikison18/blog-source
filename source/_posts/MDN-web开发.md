---
title: MDN-web开发
date: 2018-03-04 21:04:43
categories: 
  - js
tags: js
---

### 变量
声明变量 var myName;

初始化变量 myName = 'Chris';

更新变量 myName = 'Bob';

变量命名的规则：（略）

变量类型 ：Number String Boolean Array Object

松散类型
### 数字和操作符
数字类型：整数 浮点数 双精度

二进制 八进制 十六进制

算数运算符：+ - * / %

运算符优先：（略）


递增和递减运算符：++ --

操作运算符：=  +=   -=   *  /=
 
比较运算符：===   ！==   >  <  >=  <=  ==  !=

### 字符串
创建一个字符串：

单引号和双引号：注意关闭

转义字符串中的字符：var bigmouth = 'I\'ve got no right to take my place...';

连接字符串：var response = one + 'I am fine — ' + two;

数字与字符：Number（）  toString()

### String方法
字符串是对象

获得字符串的长度：browserType.length

检索特定字符串字符：browserType[browserType.length-1]

在字符串中查找子字符串并提取它：browserType.indexOf('zilla')   browserType.indexOf('mozilla') !== -1

browserType.slice(2)

转换为大写或大写：radData.toLowerCase()   radData.toUpperCase()

更新字符串的部分：browserType.replace('moz','van')

### 数组
创建数组：var shopping = ['bread', 'milk', 'cheese', 'hummus', 'noodles'];

访问和修改数组项：shopping[0] = 'tahini'

数组中的数组称为多维数组：random[2][2]

查找数组长度:sequence.length

字符串和数组之间的转换:

```
var myData = 'Manchester,London,Liverpool,Birmingham,Leeds,Carlisle'
var myArray = myData.split(',');
myArray.length;    myArray[0];
var myNewString = myArray.join(',');
Array.toString()
```
添加和删除数组项:

数组尾添加或删除一个项目使用push()和pop()

数组首添加或删除一个项目使用unshift()和shift()
### 例子：故事生成器
### 条件语句
if ... else 语句：如果（if）条件（condition）返回true，运行代码A，否则（else）运行代码B

比较运算符：===     !==    <   >    <=   >=

任何不是 false, undefined, null, 0, NaN 的值，或一个空字符串（''）在作为条件语句进行测试时实际返回true

else if：嵌套if ... else

逻辑运算符：AND，OR和NOT

switch 语句：

三元运算符：( condition ) ? run this code : run this code instead

### 循环
循环条件：开始条件   结束条件   容器

确保初始化程序被迭代，以便最终达到退出条件 or 无限循环

退出循环: - break语句将立即退出循环 - continue语句跳过迭代继续


```
for (initializer; exit-condition; final-expression) {
  // code to run
}

initializer
while (exit-condition) {
  // code to run

  final-expression
}

initializer
do {
  // code to run

  final-expression
} while (exit-condition)
```
### 函数-可复用代码块
浏览器内置函数:   浏览器API的一部分

```
var myText = 'I am a string';
var newString = myText.replace('string', 'sausage');

var myArray = ['I', 'love', 'chocolate', 'frogs'];
var madeAString = myArray.join(' ');

var myNumber = Math.random()
```
函数与方法:方法是在对象内定义的函数

自定义函数:

```
function random(number) {
  return Math.floor(Math.random()*number);
}
```
调用函数:括号来完成的

匿名函数:主要使用匿名函数来运行负载的代码以响应事件触发（如点击按钮）使用事件处理程序

```
myButton.onclick = function() {
  alert('hello');
}
```
匿名函数分配为变量的值

```
var myGreeting = function() {
  alert('hello');
}
```
函数参数：一些函数需要在调用它们时指定参数；多个参数时，它们以逗号分隔；有时参数是可选的

作用域  ：函数的外层被称为全局作用域。在全局作用域内定义的值可以被任意地方访问；局部作用域

函数内部的函数：可以从任何地方调用函数，只需确保在函数内使用的值正确的范围.
### 创建函数实例
### 函数返回值
函数执行完毕后返回的值,函数是某种计算中的中间步骤

函数不返回返回值,返回值被列为void或undefined
### 事件
事件是系统中发生的动作或事件，系统会告诉您，以便您可以以某种方式对其进行响应

每个可用的事件都会有一个事件处理器(事件监听器)，也就是事件触发时会运行的代码块。

Node.js 使用像 on ( ) 这样的函数来注册一个事件监听器，使用 once ( ) 这样函数来注册一个在运行一次之后注销的监听器。

  btn.onclick / btn.onfocus / btn.onblur / btn.ondblclick / window.onkeypress/ window.onkeydown/ window.onkeyup/ btn.onmouseover / btn.onmouseout
  
一些元素就只能在特定场景下使用，比如我们只能在 video 元素上使用 onplay 

addEventListener() and removeEventListener()
两个参数——处理器应用的事件名称，和包含我们用来回应事件的函数的代码

在不同环境下运行不同的事件处理器，只需要恰当地删除或者添加事件处理器

时候在事件处理函数内部，您可能会看到一个固定指定名称的参数，例如event，evt或简单的e。这被称为事件对象，它被自动传递给事件处理函数，以提供额外的功能和信息。

事件对象 e 的target属性始终是事件刚刚发生的元素的引用。

事件不执行它的默认行为.例子:Web表单，自定义注册表单。

onsubmit事件处理程序来实现一个简单的检查，用于测试文本字段是否为空。如果是，我们在事件对象上调用preventDefault（）函数，这样就停止了表单提交,显示一条错误消息

 

Event bubbling and capture事件冒泡捕获: bubbling and capture 是描述在同一个元素上同时激活两个相同事件类型的不同的事件处理程序时会发生什么的两种机制

捕获阶段：
浏览器检查元素的最外层祖先html是否在捕获阶段中注册了一个onclick事件处理程序，如果是，则运行它。
然后，它移动到html中的下一个元素，并执行相同的操作，然后是下一个元素，依此类推，直到到达实际点击的元素。

冒泡阶段:
浏览器检查实际点击的元素是否在冒泡阶段中注册了一个onclick事件处理程序，如果是，则运行它
然后它移动到下一个直接的祖先元素，并做同样的事情，然后是下一个，等等，直到它到达html元素

现代浏览器中，默认情况下，所有事件处理程序都在冒泡阶段进行注册。标准事件对象具有可用的名为 stopPropagation()的函数, 当在事件对象上调用该函数时，它只会让当前事件处理程序运行，但事件不会在bubble链上进一步扩大，因此不会再有任何以外的事件处理程序运行

Event delegation事件委托:
Bubbling使我们能够利用事件委托，如果你想要一些代码运行当你点击大量子元素中的任何一个，你可以设置事件监听器对父母和事件监听器到每个孩子的效果，而不是单独设置事件侦听器在每个孩子上

从Web API等不同的浏览器到webextensions和Node .js不同的语境中，JavaScript的使用往往有不同的事件模型
### 例子：相片走廊

### 对象基础
一个对象是一个包含相关资料和功能的集体（通常由一些变量和函数组成，我们称之为对象里面的属性和方法）

创建一个对象通常先定义初始化变量。var person = {};

```
var person = {
  name : ['Bob', 'Smith'],
  age : 32,
  gender : 'male',
  interests : ['music', 'skiing'],
  bio : function() {
    alert(this.name[0] + ' ' + this.name[1] + ' is ' + this.age + ' years old. He likes ' + this.interests[0] + ' and ' + this.interests[1] + '.');
  },
  greeting: function() {
    alert('Hi! I\'m ' + this.name[0] + '.');
  }
};
```
一个对象由许多的成员组成，每一个成员都拥有一个名字（像上面的name、age），和一个值（如['Bob', 'Smith']、32）。每一个名字/值（name/value）对被逗号分隔开，并且名字和值之间由冒号（:）分隔

前4个成员是资料项目，被称为对象的属性(property)，后两个成员是函数，允许对象对资料做一些操作，被称为对象的方法(method)

上示的对象被称之为对象的字面量(literal)——手动的写出对象的内容来创建一个对象。不同于从类实例化一个对象

点表示法：点表示法(dot notation)来访问对象的属性和方法

```
person.age
person.interests[1]
```
括号表示法

```
person['age']
person['name']
```
子命名空间：
```
name : {
  first : 'Bob',
  last : 'Smith'
},
```
设置对象成员：
```
person.age = 45
person['name']['last'] = 'Cratchit'
```
创建新的成员：

```
person['eyes'] = 'hazel'
person.farewell = function() { alert("Bye everybody!") }
```
**括号表示法一个有用的地方是它不仅可以动态的去设置对象成员的值，还可以动态的去设置成员的名字。点表示法只能接受字面量的成员的名字，不接受变量作为名字。**

"this"的含义：**关键字"this"指向了当前代码运行时的对象**

每个页面在加载完毕后，会有一个Document的实例被创建，叫做document，它代表了整个页面的结构，内容和一些功能，比如页面的URL。同样的，这意味document有一些可用的方法和属性。

注意内建的对象或API不会总是自动地创建对象的实例，需要为每一个想发起的通知都使用构造器进行实例化。
### 面向对象
最基本的 OOP 思想就是我们想要在我们的程序中使用对象来表示现实世界模型, 并提供一个简单的方式来访问它的功能,否则很难甚至不能实现.

对象可以包含相关的数据和代码,这些代表现实世界模型的一些信息或者功能,或者它特有的一些行为. 对象数据(也经常称为函数) 可以有结构的存储 (官方术语为 封装) 在对象包内 (也可以给一个特殊的名字来表示,有时候也叫做命名空间), 可以使它容易组织和访问; 对象也通常用于存储数据,这样就可以很容易的在网络上传输.
##### 定义一个对象模板：
抽象-为了我们编程的目标而利用事物的一些重要特性去把复杂的事物简单化。一些面向对象的语言中，我们用类（class）的概念去描述一个对象（你在下面就能看到JavaScript使用了一个完全不同的术语）。类并不完全是一个对象，它更像是一个定义对象特质的模板。
##### 创造一个真正的对象：
从上面我们创建的class中， 我们能够基于它创建出一些对象实例-一些拥有class中属性及方法的对象。基于我们的Person类，我们可以创建出许许多多的真实的人：person1、person2
##### instantiation：
当一个对象实例 要从类中创建出来时，类的构造函数就会运行来创建这个实例。这种创建对象实例的过程我们称之为实例化-实例对象被类实例化。
##### Specialist classes：
需要类型更为具体，在 OOP 里，我们可以创建基于其它类的新类，这些新的子类可以继承（inherited）它们父类的数据和功能。比起复制来说这样能够使用父对象共有的功能。再从子类从创建对象实例

多态(polymorphic)——这个高大上的词正是用来描述多个对象拥有实现共同方法的能力。

##### 构建函数和对象实例:
JavaScript 用一种称为构建函数的特殊函数来定义对象和它们的特征。构建函数非常有用，因为很多情况下你不知道实际需要多少个对象（实例）。构建函数提供了创建你所需对象（实例）的有效方法，将对象的数据和特征函数按需联结至相应对象。从构建函数创建的新实例的特征并非全盘复制，而是通过一个叫做原形链的参考链链接过去的。
##### 一个简单的例子

```
function createNewPerson(name) {
  var obj = {};
  obj.name = name;
  obj.greeting = function () {
    alert('Hi! I\'m ' + this.name + '.');
  }
  return obj;
}

var salva = createNewPerson('salva');
salva.name;
salva.greeting();
```
上述代码运行良好，但是有点冗长；如果我们知道如何创建一个对象，就没有必要创建一个新的空对象并且返回它。

```
function Person(name) {
  this.name = name;
  this.greeting = function() {
    alert('Hi! I\'m ' + this.name + '.');
  };
}
//调用构建函数创建新的实例
var person1 = new Person('Bob');
var person2 = new Person('Sarah');

person1.name
person1.greeting()
person2.name
person2.greeting()
```
这个构建函数是 JavaScript 版本的类。你会发现，它只定义了对象的属性和方法，除了没有明确创建一个对象和返回任何值和之外，它有了你期待的函数所拥有的全部功能。这里使用了this关键词，即无论是该对象的哪个实例被这个构建函数创建，它的 name 属性就是传递到构建函数形参 name 的值，它的 greeting() 方法中也将使用相同的传递到构建函数形参  name 的值。


ps:一个构建函数通常是**大写字母开头**，这样便于区分构建函数和普通函数。

person1或者 person2尽管它们有着相同的 name 属性和 greeting() method 它们是各自独立的。实际的方法仍然是定义在类里面， 而不是在对象实例里面

关键字 new 跟着一个含参函数，用于告知浏览器我们想要创建一个对象实例，非常类似函数调用，并把结果保存到变量中

##### 创建我们最终的构造函数:

```
function Person(first, last, age, gender, interests) {
  this.name = {
    first,
    last
  };
  this.age = age;
  this.gender = gender;
  this.interests = interests;
  this.bio = function() {
    alert(this.name.first + ' ' + this.name.last + ' is ' + this.age + ' years old. He likes ' + this.interests[0] + ' and ' + this.interests[1] + '.');
  };
  this.greeting = function() {
    alert('Hi! I\'m ' + this.name.first + '.');
  };
};

var person1 = new Person('Bob', 'Smith', 32, 'male', ['music', 'skiing']);

person1.name.first
person1['age']
person1.interests[1]
person1.bio()
```
##### 创建对象实例的其他方式
到现在为止，我们了解到了两种不同的创建对象实例的方式 —— **声明一个对象的语法， 与使用构造函数**

Object()构造函数:使用Object()构造函数来创建一个新对象。 是的， 一般对象都有构造函数，它创建了一个空的对象。

```
var person1 = new Object();

person1.name = 'Chris';
person1['age'] = 38;
person1.greeting = function() {
  alert('Hi! I\'m ' + this.name + '.');
}
//还可以将对象文本传递给Object() 构造函数作为参数， 以便用属性/方法填充它。
var person1 = new Object({
  name : 'Chris',
  age : 38,
  greeting : function() {
    alert('Hi! I\'m ' + this.name + '.');
  }
});
```
使用create()方法:允许您基于现有对象创建新的对象实例

```
var person2 = Object.create(person1);

person2.name
person2.greeting()
```
person2是基于person1创建的， 它们具有相同的属性和方法。这非常有用， 因为它允许你创建新的对象实例而无需定义构造函数。缺点是比起构造函数，浏览器在更晚的时候才支持create()方法（IE9,  IE8 或甚至以前相比）， 加上一些人认为构造函数让你的代码看上去更整洁

### 对象原型
通过原型这种机制，JavaScript 中的对象从其他对象继承功能特性；这种继承机制与经典的面向对象编程语言的继承机制不同。

JavaScript 常被描述为一种基于原型的语言 (prototype-based language)——每个对象拥有一个原型对象，对象以其原型为模板、从原型继承方法和属性。原型对象也可能拥有原型，并从中继承方法和属性，一层一层、以此类推。这种关系常被称为原型链 (prototype chain)，它解释了为何一个对象会拥有定义在其他对象中的属性和方法。

准确地说，这些属性和方法定义在 Object 的构造器函数之上，而非对象实例本身。

在传统的 OOP 中，首先定义“类”，此后创建对象实例时，类中定义的所有属性和方法都被复制到实例中。在 JavaScript 中并不如此复制——而是在对象实例和它的构造器之间建立一个连接（作为原型链中的一节），以后通过上溯原型链，在构造器中找到这些属性和方法。

##### 理解原型对象：

```
//定义一个构造器函数：
function Person(first, last, age, gender, interests) {
  
  // 属性与方法定义
  
};
//创建一个对象实例：
var person1 = new Person('Bob', 'Smith', 32, 'male', ['music', 'skiing']);
//JavaScript 控制台输入 "person1."
person1.valueOf()

```
调用 person1 的“实际定义在 Object 上”的方法时，会发生什么？

1、浏览器首先检查，person1 对象是否具有可用的 valueOf() 方法。

2、如果没有，则浏览器检查 person1 对象的原型对象（即 Person）是否具有可用的 valueof() 方法。

3、如果也没有，则浏览器检查 Person() 构造器的原型对象（即 Object）是否具有可用的 valueOf() 方法。Object 具有这个方法，于是该方法被调用。

ps:必须重申，原型链中的方法和属性没有被复制到其他对象——它们被访问需要通过前面所说的“原型链”的方式。

ps:没有官方的方法用于直接访问一个对象的原型对象——原型链中的“连接”被定义在一个内部属性中，在 JavaScript 语言标准中用 [[prototype]] 表示（参见 ECMAScript）。然而，大多数现代浏览器还是提供了一个名为 __proto__ （前后各有2个下划线）的属性，其包含了对象的原型。你可以尝试输入 person1.__proto__ 和 person1.__proto__.__proto__

##### prototype 属性：继承成员被定义的地方
继承的属性和方法是定义在 prototype 属性之上的（你可以称之为子命名空间 (sub namespace) ）——那些以 Object.prototype. 开头的属性，而非仅仅以 Object. 开头的属性。prototype 属性的值是一个对象，我们希望被原型链下游的对象继承的属性和方法，都被储存在其中。

于是 Object.prototype.watch()、Object.prototype.valueOf() 等等成员，适用于任何继承自 Object() 的对象类型，包括使用构造器创建的新的对象实例。

Object.is()、Object.keys()，以及其他不在 prototype 对象内的成员，不会被“对象实例”或“继承自 Object() 的对象类型”所继承。这些方法/属性仅能被 Object() 构造器自身使用。

你可以尝试从 String、Date、Number 和 Array 全局对象的原型中寻找方法和属性。它们都在原型上定义了一些方法，因此当你创建一个字符串时，myString 立即具有了一些有用的方法，如 split()、indexOf()、replace() 等。

原型对象是一个内部对象，应当使用 __proto__ 访问。prototype 属性包含（指向）一个对象，你在这个对象中定义需要被继承的成员。

Object.create() 方法创建新的对象实例：

```
var person2 = Object.create(person1);
//create() 实际做的是从指定原型对象创建一个新的对象
person2.__proto__
//结果返回 person1 对象
```
每个对象实例都具有 constructor 属性，它指向创建该实例的构造器函数：

```
person1.constructor
person2.constructor
//将返回 Person() 构造器

var person3 = new person1.constructor('Karen', 'Stephenson', 26, 'female', ['playing drums', 'mountain climbing']);
// constructor 属性的末尾添加一对圆括号（括号中包含所需的参数），从而用这个构造器创建另一个对象实例

person3.name.first
person3.age
person3.bio()

//如果你刚好因为某些原因没有原始构造器的引用，那么这种方法就很有用了

instanceName.constructor.name
person1.constructor.name
//获得某个对象实例的构造器的名字
```
修改原型：

```
Person.prototype.farewell = function() {
  alert(this.name.first + ' has left the building. Bye for now!');
}
//为构造器的 prototype 属性添加一个新的方法
person1.farewell();
//整条继承链动态地更新了，任何由此构造器创建的对象实例都自动获得了这个方法

function Person(first, last, age, gender, interests) {

  // 属性与方法定义

};

var person1 = new Person('Tammi', 'Smith', 32, 'neutral', ['music', 'skiing', 'kickboxing']);

Person.prototype.farewell = function() {
  alert(this.name.first + ' has left the building. Bye for now!');
}
//继承模型下，上游对象的方法不会复制到下游的对象实例中；
//下游对象本身虽然没有定义这些方法，但浏览器会通过上溯原型链、从上游对象中找到它们。
//这种继承模型提供了一个强大而可扩展的功能系统。

Person.prototype.fullName = 'Bob Smith';
//很少看到属性定义在 prototype 属性中，因为如此定义不够灵活
Person.prototype.fullName = this.name.first + ' ' + this.name.last;
//本例中 this 引用全局范围，而非函数范围。
//访问这个属性只会得到 undefined undefined。
//但这个语句若放在先前定义的 prototype 的方法中则有效
//因为此时语句位于函数范围内，从而能够成功地转换为对象实例范围。

```
常见的对象定义模式是，在构造器（函数体）中定义属性、在 prototype 属性上定义方法：

```
// 构造器及其属性定义

function Test(a,b,c,d) {
  // 属性定义
};

// 定义第一个方法

Test.prototype.x = function () { ... }

// 定义第二个方法

Test.prototype.y = function () { ... }

// 等等……
```
### JavaScript 中的继承
介绍如何创建“子”对象类别（构造器）并从“父”类别中继承功能
##### 原型式的继承
avaScript并不是真正的面向对象语言，在经典的面向对象语言中，你可能倾向于定义类对象,然后你可以简单地定义哪些类继承哪些类（参考C++ inheritance里的一些简单的例子），JavaScript使用了另一套实现方式，继承的对象函数并不是通过复制而来，而是通过原型链继承（通常被称为 原型式继承 —— prototypal inheritance）

具体的例子：

```
//定义了一些属性的Person构造器
function Person(first, last, age, gender, interests) {
  this.name = {
    first,
    last
  };
  this.age = age;
  this.gender = gender;
  this.interests = interests;
};
//所有的方法都定义在构造器的prototype上
Person.prototype.greeting = function() {
  alert('Hi! I\'m ' + this.name.first + '.');
};
```
创建一个Teacher类，这个类会继承Person的所有成员

```
//定义 Teacher() 构造函数
function Teacher(first, last, age, gender, interests, subject) {
  Person.call(this, first, last, age, gender, interests);

  this.subject = subject;
}
```
call()函数，这个函数允许你调用一个在这个文件里别处定义的函数。第一个参数指明了在你运行这个函数时想对“this”指定的值，也就是说，你可以重新指定你调用的函数里所有“this”指向的对象。其他的变量指明了所有目标函数运行时接受的参数。

创建一个新的对象实例时同时指派了继承的所有属性，但是注意你需要在构造器里将它们作为参数来指派，即使实例不要求它们被作为参数指派

在Teacher()构造函数里运行了Person()构造函数（见上文），得到了和在Teacher()里定义的一样的属性，但是用的是传送给Teacher()，而不是Person()的值（我们简单使用这里的this作为传给call()的this，意味着this指向Teacher()函数）。

继承没有参数的构造函数：

```
function Brick() {
  this.width = 10;
  this.height = 20;
}

function BlueGlassBrick() {
  Brick.call(this);

  this.opacity = 0.5;
  this.color = 'blue';
}
```
##### 设置 Teacher() 的 prototype 和 constructor引用

我们已经定义了一个新的构造器，这个构造器默认有一个空的原型属性。我们需要让Teacher()从Person()的原型对象里继承方法。


```
Teacher.prototype = Object.create(Person.prototype);

//我们用这个create函数来创建一个和Person.prototype一样的新的原型属性值
//（这个属性指向一个包括属性和方法的对象），
//然后将其作为Teacher.prototype的属性值。
//这意味着Teacher.prototype现在会继承Person.prototype的所有属性和方法。

//现在Teacher()的prototype的constructor属性指向的是Person()
//这是因为我们生成Teacher()的方式决定的。

//将其正确设置
Teacher.prototype.constructor = Teacher;
//输入Teacher.prototype.constructor就会得到Teacher()
```
ps：每一个函数对象（Function）都有一个prototype属性，并且只有函数对象有prototype属性，因为prototype本身就是定义在Function对象下的属性。当我们输入类似var person1=new Person(...)来构造对象时，Javascript实际上参考的是Person.prototype指向的对象来生成person1。另一方面，Person()函数是Person.prototype的构造函数，也就是说Person===Person.prototype.constructor

定义新的构造函数Teacher时，我们通过function.call来调用父类的构造函数，但是这样无法自动指定Teacher.prototype的值，这样Teacher.prototype就只能包含在构造函数里构造的属性，而没有方法。因此我们利用Create方法将Person的原型对象复制给Teacher的原型对象，并改变其构造器指向，使之与Teacher关联。

任何你想要被继承的方法都应该定义在构造函数的prototype对象里，并且永远使用父类的prototype来创造子类的prototype，这样才不会打乱类继承结构。

##### 向 Teacher() 增加新的函数 greeting()
在Teacher的原型上定义它：

```
Teacher.prototype.greeting = function() {
  var prefix;

  if(this.gender === 'male' || this.gender === 'Male' || this.gender === 'm' || this.gender === 'M') {
    prefix = 'Mr.';
  } else if(this.gender === 'female' || this.gender === 'Female' || this.gender === 'f' || this.gender === 'F') {
    prefix = 'Mrs.';
  } else {
    prefix = 'Mx.';
  }

  alert('Hello. My name is ' + prefix + ' ' + this.name.last + ', and I teach ' + this.subject + '.');
};

//范例尝试
var teacher1 = new Teacher('Dave', 'Griffiths', 31, 'male', ['football', 'cookery'], 'mathematics');

teacher1.name.first;
teacher1.interests[0];
teacher1.bio();
teacher1.subject;
teacher1.greeting();

//前面三个进入到从 Person() constructor 继承的属性和方法
//后面两个则是只有 Teacher() constrcuort 才有的属性和方法
```
例子为创建继承类的一种方式，一个常用的方法是使用 JavaScript 语言库——最热门的一些库提供一些方法让我们更快更好地实行继承。

##### 基本了解了以下三种属性或者方法：

1、那些在对象实例赋予的构造函数内定义的。通常通过使用new关键字调用构造函数创建的，例如var myInstance = new myConstructor()

2、那些直接在构造函数上定义的，仅在构造函数上可用。通常仅在内置的浏览器对象中可用，并被直接链接到构造函数而不是实例来识别。例如，Object.keys()。

3、那些在构造函数原型上定义的，由所有实例继承并继承对象类。例如myConstructor.prototype.x()
##### 何时在 JavaScript 中使用继承？
原型和继承代表了Javascript这门语言里最复杂的一些方面，但是Javascript的强大和灵活性正是来自于它的对象体系和继承方式

无论你是使用WebAPI的不同特性还是调用字符串、数组等浏览器内置对象的方法和属性的时候，你都在隐式地使用继承。

果你开始创建一系列拥有相似特性的对象时，那么创建一个包含所有共有功能的通用对象，然后在更特殊的对象类型中继承这些特性，将会变得更加方便有用。

ps：考虑到Javascript的工作方式，由于原型链等特性的存在，在不同对象之间功能的共享通常被叫做 委托 - 特殊的对象将功能委托给通用的对象类型完成。这也许比将其称之为继承更为贴切，因为“被继承”了的功能并没有被拷贝到正在“进行继承”的对象中，相反它仍存在于通用的对象中。

在使用继承时，建议你不要使用过多层次的继承总之，对象是另一种形式的代码重用，就像函数和循环一样，有他们特定的角色和优点。如果你发现自己创建了一堆相关的变量和函数，还想一起追踪它们并将其灵活打包的话，对象是个不错的主意。对象在你打算把一个数据集合从一个地方传递到另一个地方的时候非常有用。

总之，对象是另一种形式的代码重用，就像函数和循环一样，有他们特定的角色和优点。如果你发现自己创建了一堆相关的变量和函数，还想一起追踪它们并将其灵活打包的话，对象是个不错的主意。对象在你打算把一个数据集合从一个地方传递到另一个地方的时候非常有用。

### JSON
JavaScript对象表示法（JSON）是用于将结构化数据表示为JavaScript对象的标准格式，通常用于在网站上表示和传输数据 (i.e. 从服务器向客户端发送一些数据，因此可以将其显示在网页上)

##### 什么是 JSON?
JSON 是一种按照JavaScript对象语法的数据格式，虽然它是基于 Javascript 语法，但它独立于javaScript，这也是为什么许多程序环境能够读取（解读）和生成 JSON

JSON可以作为一个**对象或者字符串**存在，前者用于解读 JSON 中的数据，后者用于通过网络传输 JSON 数据。 这不是一个大事件——JavaScript 提供一个全局的 可访问的 JSON 对象来对这两种数据进行转换。

 JSON 对象可以被储存在它自己的文件中，这基本上就是一个文本文件，扩展名为 .json， 还有 MIME type 用于 application/json.
 
#####  JSON 结构：
avaScript 对象原原本本的写入 JSON 数据——字符串，数字，数组，布尔还有其它的字面值对象。这允许你构造出一个对象树
 
```
{
  "squadName" : "Super hero squad",
  "homeTown" : "Metro City",
  "formed" : 2016,
  "secretBase" : "Super tower",
  "active" : true,
  "members" : [
    {
      "name" : "Molecule Man",
      "age" : 29,
      "secretIdentity" : "Dan Jukes",
      "powers" : [
        "Radiation resistance",
        "Turning tiny",
        "Radiation blast"
      ]
    },
    {
      "name" : "Madame Uppercut",
      "age" : 39,
      "secretIdentity" : "Jane Wilson",
      "powers" : [
        "Million tonne punch",
        "Damage resistance",
        "Superhuman reflexes"
      ]
    },
    {
      "name" : "Eternal Flame",
      "age" : 1000000,
      "secretIdentity" : "Unknown",
      "powers" : [
        "Immortality",
        "Heat Immunity",
        "Inferno",
        "Teleportation",
        "Interdimensional travel"
      ]
    }
  ]
}

superHeroes.hometown
superHeroes["active"]
//简单地链式访问（通过属性名和数组索引）
superHeroes["members"][1]["powers"][2]

1、首先我们有变量名 superHeroes，储存对象 。
2、在对象中我们想访问 members 属性，所以我们使用 ["members"].
3、members 包含有对象数组，我们想要访问第二个元素，所以我们使用 [1].
4、在对象内，我们想访问 powers 属性，所以我们使用 ["powers"].
5、 powers 属性是一个包含英雄技能的数组。我们想要第三个，所以我们使用[2].
```
##### JSON 数组
数组对象也是一种合法的 JSON 对象，例如：

```
[
  {
    "name" : "Molecule Man",
    "age" : 29,
    "secretIdentity" : "Dan Jukes",
    "powers" : [
      "Radiation resistance",
      "Turning tiny",
      "Radiation blast"
    ]
  },
  {
    "name" : "Madame Uppercut",
    "age" : 39,
    "secretIdentity" : "Jane Wilson",
    "powers" : [
      "Million tonne punch",
      "Damage resistance",
      "Superhuman reflexes"
    ]
  }
]
```
过数组索引就可以访问数组元素，如[0]["powers"][0]

##### 其他注意事项
1、JSON 是一种纯数据格式，它只包含属性，没有方法。

2、JSON 要求有两头的 { } 来使其合法。最安全的写法是有两边的括号，而不是一边。

3、甚至一个错位的逗号或分号就可以导致  JSON 文件出错。你应该小心的检查你想使用的数据(虽然计算机生成的 JSON 很少出错，只要生成程序正常工作)。你可以通过像 JSONLint 的应用程序来检验 JSON。

4、JSON 可以将任何标准合法的 JSON 数据格式化保存，不只是数组和对象。比如，一个单一的字符串或者数字可以是合法的 JSON 对象。虽然不是特别有用处……

5、不像 JavaScript 标识符可以用作属性，在 JSON 中，只有字符串才能用作属性。
 
##### 一个JSON 示例
加载我们的JSON：
载入 JSON 到页面中，我们将使用 一个名为 XMLHttpRequest 的API（常称为XHR）。这是一个非常有用的 JavaScript 对象，使我们能够通过代码来向服务器请求资源文件(如：图片，文本，JSON，甚至HTML片段)，意味着我们可以更新小段内容而不用重新加载整个页面。

```
//保存一个即将访问的 URL 作为变量
var requestURL = 'https://mdn.github.io/learning-area/javascript/oojs/json/superheroes.json';

//创建一个Http请求
var request = new XMLHttpRequest();

//使用 open() 函数打开一个新的请求
request.open('GET', requestURL);
//需要两个强制参数：
//HTTP 方法，网络连接时使用。这个示例中 GET 就可以了，因为我们只要获得简单的数据。
//URL，用于指向请求的地址。我们使用之前保存的变量。

//设定 responseType 为 JSON
request.responseType = 'json';
request.send();

//服务器的返回数据，然后处理它
request.onload = function() {
  var superHeroes = request.response;
  populateHeader(superHeroes);
  showHeroes(superHeroes);
}
```
把代码包在事件处理函数中，当请求对象 load 事件触发时执行代码(见onload)，这是因为请求对象 load 事件只有在请求成功时触发；这种方式可以保证事件触发时 request.response 是绝对可以访问的。

获得的JSON数据，让我们利用它来写两个我们使用的函数
```
function populateHeader(jsonObj) {
  var myH1 = document.createElement('h1');
  myH1.textContent = jsonObj['squadName'];
  header.appendChild(myH1);

  var myPara = document.createElement('p');
  myPara.textContent = 'Hometown: ' + jsonObj['homeTown'] + ' // Formed: ' + jsonObj['formed'];
  header.appendChild(myPara);
}

function showHeroes(jsonObj) {
  var heroes = jsonObj['members'];
      
  for(i = 0; i < heroes.length; i++) {
    var myArticle = document.createElement('article');
    var myH2 = document.createElement('h2');
    var myPara1 = document.createElement('p');
    var myPara2 = document.createElement('p');
    var myPara3 = document.createElement('p');
    var myList = document.createElement('ul');

    myH2.textContent = heroes[i].name;
    myPara1.textContent = 'Secret identity: ' + heroes[i].secretIdentity;
    myPara2.textContent = 'Age: ' + heroes[i].age;
    myPara3.textContent = 'Superpowers:';
        
    var superPowers = heroes[i].powers;
    for(j = 0; j < superPowers.length; j++) {
      var listItem = document.createElement('li');
      listItem.textContent = superPowers[j];
      myList.appendChild(listItem);
    }

    myArticle.appendChild(myH2);
    myArticle.appendChild(myPara1);
    myArticle.appendChild(myPara2);
    myArticle.appendChild(myPara3);
    myArticle.appendChild(myList);

    section.appendChild(myArticle);
  }
}
```
##### 对象和文本间的转换
1、parse(): 以文本字符串形式接受JSON对象作为参数，并返回相应的对象。

2、stringify(): 接收一个对象作为参数，返回一个对应的JSON字符串。
### 面向对象实践(屏幕上画小球)

```
var canvas = document.querySelector('canvas');

var ctx = canvas.getContext('2d');

var width = canvas.width = window.innerWidth;
var height = canvas.height = window.innerHeight;

//使用变量代指了 <canvas> 元素, 然后对其调用 getContext() 从而我们获得一个开始画画的环境。
//存储以上操作结果的变量（ctx）是一个对象，直接代指 canvas 上的一块允许我们绘制 2D 图形的区域。

//返回一个这两个数字之间的一个随机数。
function random(min, max) {
  var num = Math.floor(Math.random() * (max - min + 1)) + min;
  return num;
}

//通过一个对象实例化
//x 和 y 坐标 — 小球在屏幕上最开始时候的坐标。坐标的范围从 0 （左上角）到浏览器视窗的宽和高（右下角）。
//水平和竖直速度（velX 和 velY）— 我们会给每个小球一个水平和竖直速度。
//实际上，当我们让这些球开始运动时候，每过一帧都会给小球的 x 和 y 坐标加一次这些值。
//color — 每一个小球会有自己的颜色。
//size — 每一个小球会有自己的大小 — 也就是小球的半径，以像素为单位。
function Ball(x, y, velX, velY, color, size) {
  this.x = x;
  this.y = y;
  this.velX = velX;
  this.velY = velY;
  this.color = color;
  this.size = size;
}
//画小球,小球的原型加上 draw( ) 方法
Ball.prototype.draw = function() {
  ctx.beginPath();
  ctx.fillStyle = this.color;
  ctx.arc(this.x, this.y, this.size, 0, 2 * Math.PI);
  ctx.fill();
}
//首先，我们使用 beginPath()来声明我们现在要开始在纸上画一个图形了。
//然后，我们使用 fillStyle 来定义这个形状的颜色我们把这个加到小球的颜色属性。
//接下来，我们使用 arc() 方法来在纸上画出一段圆弧。有这些参数：
//x 和 y 是 arc 中心的坐标 — 也就是小球的中心坐标。
//arc 的半径 — 小球的半径。
//最后两个参数是开始和结束的角度，也就是圆弧对应的夹角。
//这里我们用的是 0 和 2 * PI，也就是 360 度
//最后，我们使用 fill() 方法，也就是声明我们结束了以 beginPath()开始的绘画,
//并且使用我们之前设置的颜色进行填充。 

//创建一个小球实例
var testBall = new Ball(50, 100, 4, 4, 'blue', 10);

testBall.x
testBall.size
testBall.color
testBall.draw()

//更新小球的数据
Ball.prototype.update = function() {
  if ((this.x + this.size) >= width) {
    this.velX = -(this.velX);
  }

  if ((this.x - this.size) <= 0) {
    this.velX = -(this.velX);
  }

  if ((this.y + this.size) >= height) {
    this.velY = -(this.velY);
  }

  if ((this.y - this.size) <= 0) {
    this.velY = -(this.velY);
  }

  this.x += this.velX;
  this.y += this.velY;
}

//让球动起来
var balls = [];

function loop() {
  ctx.fillStyle = 'rgba(0, 0, 0, 0.25)';
  ctx.fillRect(0, 0, width, height);

  while (balls.length < 25) {
    var ball = new Ball(
      random(0,width),
      random(0,height),
      random(-7,7),
      random(-7,7),
      'rgb(' + random(0,255) + ',' + random(0,255) + ',' + random(0,255) +')',
      random(10,20)
    );
    balls.push(ball);
  }

  for (var i = 0; i < balls.length; i++) {
    balls[i].draw();
    balls[i].update();
  }

  requestAnimationFrame(loop);
}

//loop（）函数做了下面的事情：
//1、将整个画布的颜色设置成半透明的黑色。使用  fillRect() 
//2、当且仅当小球数量小于 25 时，将 random( ) 函数产生的数字传入新的小球实例从而创建一个新的小球，并且加入到数组中
//3、遍历数组中的所有小球，并且让每个小球都调用 draw( ) 和 update( ) 函数来将自己画出来，并且再接下来的每一帧都按照其速度进行必要的跟新。
//4、使用 requestAnimationFrame() 方法再运行一次函数，
//当一个函数正在运行时传递相同的函数名，从而每隔一小段时间都会运行一次这个函数，从而得到一个平滑的动画效果。
//这主要是通过递归完成的 — 也就是说函数每次运行的时候都会调用自己，从而可以一遍又一遍得运行。

loop();

//增加撞击侦察
Ball.prototype.collisionDetect = function() {
  for (var j = 0; j < balls.length; j++) {
    if (!(this === balls[j])) {
      var dx = this.x - balls[j].x;
      var dy = this.y - balls[j].y;
      var distance = Math.sqrt(dx * dx + dy * dy);

      if (distance < this.size + balls[j].size) {
        balls[j].color = this.color = 'rgb(' + random(0, 255) + ',' + random(0, 255) + ',' + random(0, 255) +')';
      }
    }
  }
}

//1、每个小球，我们都要检查其他的小球是否和当前这个小球相撞了。
//为了达到此目的，我们构造另外一个循环来遍历数组中的小球。
//2、一个条件判断来检查当前遍历的小球是否与当前的小球相同。
//3、用了一个常见的算法来检测两个小球是否相撞了，
//两个小球中心的距离是否小于量小球的半径之和。
//4、如果两个小球真的相撞了，会运行 if 下的代码。
//我们会将两个小球的颜色都设置成随机的一种。

//在 balls[i].update() 加上下面的代码：
balls[i].collisionDetect();
```
### 弹跳球演示添加功能
工程概要：添加一个用户控制的邪恶圈子，使它变得更加互动，如果它捕捉到它，它会吃掉球。我们还想通过创建Shape()我们的球和邪恶的圈子可以继承的通用对象来测试您的对象构建技能。最后，我们要添加一个分数计数器来跟踪剩下的球数。

更改现有的Ball()构造函数，使其成为一个Shape()构造函数并添加一个新的Ball()构造函数：

1、该Shape()构造函数应该定义x，y，velX，并velY以同样的方式属性的Ball()构造做了最初，但不是color和size性能。

2、它还应该定义一个新的属性exists，用于跟踪程序中是否存在球（没有被邪恶的圈子吃掉）。这应该是一个布尔值（true/ false）。

3、该Ball()构造应该继承x，y，velX，velY，和exists性质与Shape()构造。

4、它还应该定义一个color和一个size属性，就像原始的Ball()构造函数一样。

5、记住设置Ball()构造函数prototype和constructor适当的。

draw()，update()和collisionDetect()方法定义应该能够保持与之前完全相同的。
您还需要在new Ball() ( ... )构造函数调用中添加一个新参数- exists参数应该是第5个参数，并且应该赋予一个值true。

定义EvilCircle（）：
该EvilCircle()构造应该继承x，y以及exists从Shape()。

还应该定义自己的属性：color - 'white' / size - 10 / velX - 20 / velY - 20

定义EvilCircle（）的方法：

draw()

checkBounds()

setControls()

```
var _this = this;
window.onkeydown = function(e) {
    if (e.keyCode === 65) {
      _this.x -= _this.velX;
    } else if (e.keyCode === 68) {
      _this.x += _this.velX;
    } else if (e.keyCode === 87) {
      _this.y -= _this.velY;
    } else if (e.keyCode === 83) {
      _this.y += _this.velY;
    }
  }
```

collisionDetect()

把邪恶的圈子带入程序：

首先，创建一个新的邪恶圈子对象实例（指定必要的参数），然后调用它的setControls()方法。你只需要做这两件事情，而不是循环的每一次迭代。

在你绕过每一个球的地方，调用每个球的draw()，update()和，和collisionDetect()每个的功能，使它们只有当当前球存在时才调用这些功能。

调用邪恶球情况下的draw()，checkBounds()以及collisionDetect()在循环的每次迭代方法。

实施分数计数器：
创建一个存储对段落引用的变量。以某种方式保留屏幕上的球数。每次将球添加到场景时，增加计数并显示更新的球数。减少计数，并在每次恶魔圈吃球时显示更新的球数（使其不存在）。
