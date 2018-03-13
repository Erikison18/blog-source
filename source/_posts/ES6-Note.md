---
layout: blog
title: ES6 Note
date: 2018-03-13 22:47:07
tags: js
categories: 
  - js
---
# 1.ECMAScript 6 简介
### 1. ECMAScript 和 JavaScript 的关系
ECMAScript 和 JavaScript的关系是，前者是后者的规格，后者是前者的一种实现
### 2.ECMAScript 和 JavaScript 的关系是，前者是后者的规格，后者是前者的一种实现
ES6 既是一个历史名词，也是一个泛指，含义是 5.1 版以后的 JavaScript 的下一代标准，涵盖了 ES2015、ES2016、ES2017 等等
### 3.语法提案的批准流程
### 4.ECMAScript 的历史
### 5.部署进度 
### 6.Babel 转码器 
将 ES6 代码转为 ES5 代码，从而在现有环境执行。
### 7.Traceur 转码器
# 2.let 和 const 命令
### 1.let 命令
声明的变量，只在let命令所在的代码块内有效。

不存在变量提升

暂时性死区

不允许重复声明
### 2.块级作用域
###### 没有块级作用域问题：
1.内层变量可能会覆盖外层变量.

2.用来计数的循环变量泄露为全局变量

ES6 允许块级作用域的任意嵌套

内层作用域可以定义外层作用域的同名变量

###### 块级作用域与函数声明:

ES6 规定，块级作用域之中，函数声明语句的行为类似于let，在块级作用域之外不可引用。

允许在块级作用域内声明函数。
函数声明类似于var，即会提升到全局作用域或函数作用域的头部。
同时，函数声明还会提升到所在的块级作用域的头部
### 3.const 命令 
一旦声明，常量的值就不能改变
###### ES6 声明变量的六种方法:
var命令和function命令;

let和const命令;

import命令和class命令;
### 4.顶层对象的属性
浏览器环境指的是window对象，在 Node 指的是global对象。ES5 之中，顶层对象的属性与全局变量是等价的。
### 5.global 对象

```
// 方法一
(typeof window !== 'undefined'
   ? window
   : (typeof process === 'object' &&
      typeof require === 'function' &&
      typeof global === 'object')
     ? global
     : this);

// 方法二
var getGlobal = function () {
  if (typeof self !== 'undefined') { return self; }
  if (typeof window !== 'undefined') { return window; }
  if (typeof global !== 'undefined') { return global; }
  throw new Error('unable to locate global object');
};
```
# 3.变量的解构赋值
### 1.数组的解构赋值
按照一定模式，从数组和对象中提取值，对变量进行赋值，这被称为解构

本质上，这种写法属于“模式匹配”，只要等号两边的模式相同，左边的变量就会被赋予对应的值。

如果解构不成功，变量的值就等于undefined

只要某种数据结构具有 Iterator 接口，都可以采用数组形式的解构赋值

解构赋值允许指定默认值

默认值可以引用解构赋值的其他变量，但该变量必须已经声明。
### 2.对象的解构赋值
对象的属性没有次序，变量必须与属性同名，才能取到正确的值。

与数组一样，解构也可以用于嵌套结构的对象。

默认值生效的条件是，对象的属性值严格等于undefined

### 3.字符串的解构赋值
字符串被转换成了一个类似数组的对象
### 4.数值和布尔值的解构赋值
解构赋值时，如果等号右边是数值和布尔值，则会先转为对象

解构赋值的规则是，只要等号右边的值不是对象或数组，就先将其转为对象。
### 5.函数参数的解构赋值
函数的参数也可以使用解构赋值。

函数参数的解构也可以使用默认值。
### 6.圆括号问题 
ES6 的规则是，只要有可能导致解构的歧义，就不得使用圆括号。
### 7.用途
###### （1）交换变量的值
###### （2）从函数返回多个值
###### （3）函数参数的定义
###### （4）提取 JSON 数据
###### （5）函数参数的默认值
###### （6）遍历 Map 结构
###### （7）输入模块的指定方法
# 4.字符串的扩展
### 1.字符的 Unicode 表示法

### 2.codePointAt()

### 3.String.fromCodePoint()

### 4.字符串的遍历器接口
字符串可以被for...of循环遍历
### 5.at()

### 6.normalize()

### 7.includes(), startsWith(), endsWith()
includes()：返回布尔值，表示是否找到了参数字符串。

startsWith()：返回布尔值，表示参数字符串是否在原字符串的头部。

endsWith()：返回布尔值，表示参数字符串是否在原字符串的尾部。
### 8.repeat() 
repeat方法返回一个新字符串，表示将原字符串重复n次。
### 9.padStart()，padEnd()
padStart()用于头部补全，padEnd()用于尾部补全。
### 10.matchAll()
matchAll方法返回一个正则表达式在当前字符串的所有匹配
### 11.模板字符串
模板字符串（templatestring）是增强版的字符串，用反引号（`）标识。

可以用来定义多行字符串，或者在字符串中嵌入变量。
### 12.实例：模板编译

```
let template = `
<ul>
  <% for(let i=0; i < data.supplies.length; i++) { %>
    <li><%= data.supplies[i] %></li>
  <% } %>
</ul>
`;
```
使用<%= ... %>输出 JavaScript 表达式
### 13.标签模板
标签模板其实不是模板，而是函数调用的一种特殊形式。“标签”指的就是函数，紧跟在后面的模板字符串就是它的参数。
### 14.String.raw()
String.raw方法，往往用来充当模板字符串的处理函数，返回一个斜杠都被转义（即斜杠前面再加一个斜杠）的字符串，对应于替换变量后的模板字符串
### 15.模板字符串的限制
# 4.正则的扩展
### 1.RegExp 构造函数

### 2.字符串的正则方法
String.prototype.match 调用 RegExp.prototype[Symbol.match]

String.prototype.replace 调用 RegExp.prototype[Symbol.replace]

String.prototype.search 调用 RegExp.prototype[Symbol.search]

String.prototype.split 调用 RegExp.prototype[Symbol.split]
### 3.u 修饰符
正则表达式添加了u修饰符，含义为“Unicode 模式”，用来正确处理大于\uFFFF的 Unicode 字符。
### 4.y 修饰符
加了y修饰符，叫做“粘连”（sticky）修饰符。
### 5.sticky 属性
与y修饰符相匹配，ES6 的正则对象多了sticky属性，表示是否设置了y修饰符。
### 6.flags 属性
ES6 为正则表达式新增了flags属性，会返回正则表达式的修饰符。
### 7.s 修饰符：dotAll 模式
正则表达式中，点（.）是一个特殊字符，代表任意的单个字符，但是有两个例外。
### 8.后行断言
avaScript 语言的正则表达式，只支持先行断言（lookahead）和先行否定断言（negative lookahead），不支持后行断言（lookbehind）和后行否定断言（negative lookbehind）。ES2018 引入后行断言，V8 引擎 4.9 版（Chrome 62）已经支持。
### 9.Unicode 属性类
ES2018 引入了一种新的类的写法\p{...}和\P{...}，允许正则表达式匹配符合 Unicode 某种属性的所有字符。
### 10.具名组匹配

### 11.String.prototype.matchAll
如果一个正则表达式在字符串里面有多个匹配，现在一般使用g修饰符或y修饰符，在循环里面逐一取出。
# 6.数值的扩展
### 二进制和八进制表示法
二进制和八进制数值的新的写法，分别用前缀0b（或0B）和0o（或0O）表示。
### Number.isFinite(), Number.isNaN()

### Number.parseInt(), Number.parseFloat()

### Number.isInteger()
Number.isInteger()用来判断一个数值是否为整数。
### Number.EPSILON
ES6 在Number对象上面，新增一个极小的常量Number.EPSILON。根据规格，它表示 1 与大于 1 的最小浮点数之间的差。
### 安全整数和 Number.isSafeInteger()
JavaScript 能够准确表示的整数范围在-2^53到2^53之间（不含两个端点）

ES6 引入了Number.MAX_SAFE_INTEGER和Number.MIN_SAFE_INTEGER这两个常量，用来表示这个范围的上下限。
### Math 对象的扩展
Math.trunc方法用于去除一个数的小数部分，返回整数部分。

Math.sign方法用来判断一个数到底是正数、负数、还是零。对于非数值，会先将其转换为数值。

Math.cbrt方法用于计算一个数的立方根。

Math.clz32方法返回一个数的 32 位无符号整数形式有多少个前导 0。

Math.imul方法返回两个数以 32 位带符号整数形式相乘的结果，返回的也是一个 32 位的带符号整数。

Math.fround方法返回一个数的32位单精度浮点数形式。

Math.hypot方法返回所有参数的平方和的平方根。

Math.expm1(x)返回 ex - 1，即Math.exp(x) - 1。

Math.log1p(x)方法返回1 + x的自然对数，即Math.log(1 + x)。如果x小于-1，返回NaN。

Math.log10(x)返回以 10 为底的x的对数。如果x小于 0，则返回 NaN。

Math.log2(x)返回以 2 为底的x的对数。如果x小于 0，则返回 NaN。

###### ES6 新增了 6 个双曲函数方法。
### 指数运算符
ES2016 新增了一个指数运算符（**）。
# 7.函数的扩展
### 1.函数参数的默认值
ES6 允许为函数的参数设置默认值，即直接写在参数定义的后面。

参数默认值不是传值的，而是每次都重新计算默认值表达式的值。惰性求值

通常情况下，定义了默认值的参数，应该是函数的尾参数。

指定了默认值以后，函数的length属性，将返回没有指定默认值的参数个数。

一旦设置了参数的默认值，函数进行声明初始化时，参数会形成一个单独的作用域（context）。等到初始化结束，这个作用域就会消失。
### 2.rest 参数
 rest 参数（形式为...变量名），用于获取函数的多余参数，这样就不需要使用arguments对象了。rest 参数搭配的变量是一个数组，该变量将多余的参数放入数组中。
### 3.严格模式
只要函数参数使用了默认值、解构赋值、或者扩展运算符，那么函数内部就不能显式设定为严格模式，否则会报错。
### 4.name 属性
函数的name属性，返回该函数的函数名
### 5.箭头函数
箭头函数的代码块部分多于一条语句，就要使用大括号将它们括起来，并且使用return语句返回。

###### 箭头函数有几个使用注意点。
（1）函数体内的this对象，就是定义时所在的对象，而不是使用时所在的对象。

（2）不可以当作构造函数，也就是说，不可以使用new命令，否则会抛出一个错误。

（3）不可以使用arguments对象，该对象在函数体内不存在。如果要用，可以用 rest 参数代替。

（4）不可以使用yield命令，因此箭头函数不能用作 Generator 函数。
### 6.双冒号运算符
箭头函数可以绑定this对象，大大减少了显式绑定this对象的写法（call、apply、bind）。但是，箭头函数并不适用于所有场合，所以现在有一个提案，提出了“函数绑定”（function bind）运算符，用来取代call、apply、bind调用。

函数绑定运算符是并排的两个冒号（::），双冒号左边是一个对象，右边是一个函数。该运算符会自动将左边的对象，作为上下文环境（即this对象），绑定到右边的函数上面。
### 7.尾调用优化
指某个函数的最后一步是调用另一个函数。
### 8.函数参数的尾逗号
ES2017 允许函数的最后一个参数有尾逗号（trailing comma）。
# 8.数组的扩展
### 1.扩展运算符
扩展运算符（spread）是三个点（...）。它好比 rest 参数的逆运算，将一个数组转为用逗号分隔的参数序列。

由于扩展运算符可以展开数组，所以不再需要apply方法，将数组转为函数的参数了。

###### 扩展运算符的应用
（1）复制数组

（2）合并数组

（3）与解构赋值结合

（4）字符串

（5）实现了 Iterator 接口的对象

（6）Map 和 Set 结构，Generator 函数

### 2.Array.from()
Array.from方法用于将两类对象转为真正的数组：类似数组的对象和可遍历的对象（包括 ES6 新增的数据结构 Set 和 Map）
### 3.Array.of()
Array.of方法用于将一组值，转换为数组。
### 4.数组实例的 copyWithin()
数组实例的copyWithin方法，在当前数组内部，将指定位置的成员复制到其他位置（会覆盖原有成员），然后返回当前数组。

### 5.数组实例的 find() 和 findIndex()
数组实例的find方法，用于找出第一个符合条件的数组成员。它的参数是一个回调函数，所有数组成员依次执行该回调函数，直到找出第一个返回值为true的成员，然后返回该成员。

数组实例的findIndex方法的用法与find方法非常类似，返回第一个符合条件的数组成员的位置，如果所有成员都不符合条件，则返回-1。
### 6.数组实例的 fill()
fill方法使用给定值，填充一个数组。
### 7.数组实例的 entries()，keys() 和 values()
ES6 提供三个新的方法——entries()，keys()和values()——用于遍历数组。它们都返回一个遍历器对象，可以用for...of循环进行遍历，唯一的区别是keys()是对键名的遍历、values()是对键值的遍历，entries()是对键值对的遍历。

如果不使用for...of循环，可以手动调用遍历器对象的next方法，进行遍历。
### 8.数组实例的 includes()
Array.prototype.includes方法返回一个布尔值，表示某个数组是否包含给定的值，与字符串的includes方法类似。
### 9.数组的空位
forEach(), filter(), reduce(), every() 和some()都会跳过空位。
map()会跳过空位，但会保留这个值
join()和toString()会将空位视为undefined，而undefined和null会被处理成空字符串。

ES6 则是明确将空位转为undefined。
# 9.对象的扩展
### 1.属性的简洁表示法
ES6 允许直接写入变量和函数，作为对象的属性和方法。

属性的赋值器（setter）和取值器（getter），事实上也是采用这种写法。
### 2.属性名表达式
JavaScript 定义对象的属性:方法一是直接用标识符作为属性名，方法二是用表达式作为属性名，这时要将表达式放在方括号之内。

ES6 允许字面量定义对象时，用方法二（表达式）作为对象的属性名，即把表达式放在方括号内。
### 3.方法的 name 属性
函数的name属性，返回函数名。对象方法也是函数，因此也有name属性。
### 4.Object.is()
用来比较两个值是否严格相等，与严格比较运算符（===）的行为基本一致。
### 5.Object.assign()
Object.assign方法用于对象的合并，将源对象（source）的所有可枚举属性，复制到目标对象（target）。

###### 用途
（1）为对象添加属性

（2）为对象添加方法

（3）克隆对象

（4）合并多个对象

（5）为属性指定默认值
### 6.属性的可枚举性和遍历
对象的每个属性都有一个描述对象（Descriptor），用来控制该属性的行为。Object.getOwnPropertyDescriptor方法可以获取该属性的描述对象。

描述对象的enumerable属性，称为”可枚举性“，如果该属性为false，就表示某些操作会忽略当前属性。

###### 属性的遍历
（1）for...in

for...in循环遍历对象自身的和继承的可枚举属性

2）Object.keys(obj)

Object.keys返回一个数组，包括对象自身的（不含继承的）所有可枚举属性（不含 Symbol 属性）的键名

（3）Object.getOwnPropertyNames(obj)

Object.getOwnPropertyNames返回一个数组，包含对象自身的所有属性（不含 Symbol 属性，但是包括不可枚举属性）的键名。

（4）Object.getOwnPropertySymbols(obj)

Object.getOwnPropertySymbols返回一个数组，包含对象自身的所有 Symbol 属性的键名。

（5）Reflect.ownKeys(obj)

Reflect.ownKeys返回一个数组，包含对象自身的所有键名，不管键名是 Symbol 或字符串，也不管是否可枚举。


### 7.Object.getOwnPropertyDescriptors()
ES2017 引入了Object.getOwnPropertyDescriptors方法，返回指定对象所有自身属性（非继承属性）的描述对象。
### 8.__proto__属性，Object.setPrototypeOf()，Object.getPrototypeOf()
__proto__属性（前后各两个下划线），用来读取或设置当前对象的prototype对象。目前，所有浏览器（包括 IE11）都部署了这个属性。

Object.setPrototypeOf方法的作用与__proto__相同，用来设置一个对象的prototype对象，返回参数对象本身。它是 ES6 正式推荐的设置原型对象的方法。

该方法与Object.setPrototypeOf方法配套，用于读取一个对象的原型对象。
### 9.super 关键字
this关键字总是指向函数所在的当前对象，ES6 又新增了另一个类似的关键字super，指向当前对象的原型对象。

super关键字表示原型对象时，只能用在对象的方法之中，用在其他地方都会报错。
### 10.Object.keys()，Object.values()，Object.entries()

### 11.对象的扩展运算符
扩展运算符（...）。

对象的解构赋值用于从一个对象取值，相当于将目标对象自身的所有可遍历的（enumerable）、但尚未被读取的属性，分配到指定的对象上面。所有的键和它们的值，都会拷贝到新对象上面。

对象的扩展运算符（...）用于取出参数对象的所有可遍历属性，拷贝到当前对象之中。
# 10.Symbol
### 1.概述
ES5 的对象属性名都是字符串，这容易造成属性名的冲突。

ES6 引入了一种新的原始数据类型Symbol，表示独一无二的值。它是 JavaScript 语言的第七种数据类型，前六种是：undefined、null、布尔值（Boolean）、字符串（String）、数值（Number）、对象（Object）。

Symbol 值通过Symbol函数生成

Symbol函数前不能使用new命令，否则会报错。这是因为生成的 Symbol 是一个原始类型的值，不是对象。
### 2.作为属性名的 Symbol
每一个 Symbol 值都是不相等的，这意味着 Symbol 值可以作为标识符，用于对象的属性名，就能保证不会出现同名的属性。

### 3.实例：消除魔术字符串

### 4.属性名的遍历
Symbol 作为属性名，该属性不会出现在for...in、for...of循环中，也不会被Object.keys()、Object.getOwnPropertyNames()、JSON.stringify()返回。但是，它也不是私有属性，有一个Object.getOwnPropertySymbols方法，可以获取指定对象的所有 Symbol 属性名。

Object.getOwnPropertySymbols方法返回一个数组，成员是当前对象的所有用作属性名的 Symbol 值。
### 5.Symbol.for()，Symbol.keyFor()
重新使用同一个 Symbol 值，Symbol.for方法可以做到这一点。

Symbol.keyFor方法返回一个已登记的 Symbol 类型值的key
### 6.实例：模块的 Singleton 模式
Singleton 模式指的是调用一个类，任何时候返回的都是同一个实例。

对于 Node 来说，模块文件可以看成是一个类。怎么保证每次执行这个模块文件，返回的都是同一个实例呢？

很容易想到，可以把实例放到顶层对象global。
### 7.内置的 Symbol 值
对象的Symbol.hasInstance属性，指向一个内部方法。

对象的Symbol.isConcatSpreadable属性等于一个布尔值，表示该对象用于Array.prototype.concat()时，是否可以展开。

对象的Symbol.species属性，指向一个构造函数。创建衍生对象时，会使用该属性。

对象的Symbol.match属性，指向一个函数。当执行str.match(myObject)时，如果该属性存在，会调用它，返回该方法的返回值。

对象的Symbol.replace属性，指向一个方法，当该对象被String.prototype.replace方法调用时，会返回该方法的返回值。

对象的Symbol.search属性，指向一个方法，当该对象被String.prototype.search方法调用时，会返回该方法的返回值。

对象的Symbol.split属性，指向一个方法，当该对象被String.prototype.split方法调用时，会返回该方法的返回值。

对象的Symbol.iterator属性，指向该对象的默认遍历器方法。

对象的Symbol.toPrimitive属性，指向一个方法。该对象被转为原始类型的值时，会调用这个方法，返回该对象对应的原始类型值。

对象的Symbol.toStringTag属性，指向一个方法。在该对象上面调用Object.prototype.toString方法时，如果这个属性存在，它的返回值会出现在toString方法返回的字符串之中，表示对象的类型。

对象的Symbol.unscopables属性，指向一个对象。该对象指定了使用with关键字时，哪些属性会被with环境排除。
# 11.Set 和 Map 数据结构
### 1.Set
ES6 提供了新的数据结构 Set。它类似于数组，但是成员的值都是唯一的，没有重复的值。

###### Set 结构的实例有以下属性。
Set.prototype.constructor：构造函数，默认就是Set函数。

Set.prototype.size：返回Set实例的成员总数。
###### Set 实例的方法分为两大类：操作方法（用于操作数据）和遍历方法（用于遍历成员）
add(value)：添加某个值，返回 Set 结构本身。

delete(value)：删除某个值，返回一个布尔值，表示删除是否成功。

has(value)：返回一个布尔值，表示该值是否为Set的成员。

clear()：清除所有成员，没有返回值。

###### Set 结构的实例有四个遍历方法，可以用于遍历成员。

keys()：返回键名的遍历器

values()：返回键值的遍历器

entries()：返回键值对的遍历器

forEach()：使用回调函数遍历每个成员

### 2.WeakSet 
WeakSet 的成员只能是对象，而不能是其他类型的值。
WeakSet 中的对象都是弱引用，即垃圾回收机制不考虑 WeakSet 对该对象的引用。

###### WeakSet 结构有以下三个方法。

WeakSet.prototype.add(value)：向 WeakSet 实例添加一个新成员。
WeakSet.prototype.delete(value)：清除 WeakSet 实例的指定成员。
WeakSet.prototype.has(value)：返回一个布尔值，表示某个值是否在 WeakSet 实例之中。
### 3.Map 
JavaScript 的对象（Object），本质上是键值对的集合（Hash 结构），但是传统上只能用字符串当作键。

Map 的键实际上是跟内存地址绑定的，只要内存地址不一样，就视为两个键。

###### 实例的属性和操作方法:
（1）size 属性

（2）set(key, value)

（3）get(key)

（4）has(key)

（5）delete(key)

（6）clear()

###### 遍历方法:
keys()：返回键名的遍历器。

values()：返回键值的遍历器。

entries()：返回所有成员的遍历器。

forEach()：遍历 Map 的所有成员。
### 4.WeakMap
WeakMap只接受对象作为键名（null除外），不接受其他类型的值作为键名。
WeakMap的键名所指向的对象，不计入垃圾回收机制。
# 12.Proxy
### 1.概述
Proxy 用于修改某些操作的默认行为，等同于在语言层面做出修改，所以属于一种“元编程”（meta programming），即对编程语言进行编程。

### 2.Proxy 实例的方法
get方法用于拦截某个属性的读取操作，可以接受三个参数，依次为目标对象、属性名和 proxy 实例本身（即this关键字指向的那个对象），其中最后一个参数可选。

set方法用来拦截某个属性的赋值操作，可以接受四个参数，依次为目标对象、属性名、属性值和 Proxy 实例本身，其中最后一个参数可选。

apply方法拦截函数的调用、call和apply操作。

has方法用来拦截HasProperty操作，即判断对象是否具有某个属性时，这个方法会生效。典型的操作就是in运算符。

construct方法用于拦截new命令，下面是拦截对象的写法。

deleteProperty方法用于拦截delete操作，如果这个方法抛出错误或者返回false，当前属性就无法被delete命令删除

defineProperty方法拦截了Object.defineProperty操作。

getOwnPropertyDescriptor方法拦截Object.getOwnPropertyDescriptor()，返回一个属性描述对象或者undefined。

getPrototypeOf方法主要用来拦截获取对象原型

isExtensible方法拦截Object.isExtensible操作。

ownKeys方法用来拦截对象自身属性的读取操作。

preventExtensions方法拦截Object.preventExtensions()

setPrototypeOf方法主要用来拦截Object.setPrototypeOf方法。
### 3.Proxy.revocable()
Proxy.revocable方法返回一个可取消的 Proxy 实例。
### 4.this 问题

### 5.实例：Web 服务的客户端
Proxy 对象可以拦截目标对象的任意属性，这使得它很合适用来写 Web 服务的客户端。
# 13.Reflect
### 1.概述
###### Reflect对象的设计目的有这样几个:
（1） 将Object对象的一些明显属于语言内部的方法（比如Object.defineProperty），放到Reflect对象上。

（2） 修改某些Object方法的返回结果，让其变得更合理。

（3） 让Object操作都变成函数行为。

（4）Reflect对象的方法与Proxy对象的方法一一对应，只要是Proxy对象的方法，就能在Reflect对象上找到对应的方法。
### 2.静态方法
###### Reflect对象一共有 13 个静态方法。
Reflect.apply(target, thisArg, args)

Reflect.construct(target, args)

Reflect.get(target, name, receiver)

Reflect.set(target, name, value, receiver)

Reflect.defineProperty(target, name, desc)

Reflect.deleteProperty(target, name)

Reflect.has(target, name)

Reflect.ownKeys(target)

Reflect.isExtensible(target)

Reflect.preventExtensions(target)

Reflect.getOwnPropertyDescriptor(target, name)

Reflect.getPrototypeOf(target)

Reflect.setPrototypeOf(target, prototype)
### 3.实例：使用 Proxy 实现观察者模式
观察者模式（Observer mode）指的是函数自动观察数据对象，一旦对象有变化，函数就会自动执行。
# 14.Promise 对象
### 1.Promise 的含义
Promise 是异步编程的一种解决方案

简单说就是一个容器，里面保存着某个未来才会结束的事件（通常是一个异步操作）的结果。从语法上说，Promise 是一个对象，从它可以获取异步操作的消息。

###### 两个特点。
（1）对象的状态不受外界影响。

（2）一旦状态改变，就不会再变，任何时候都可以得到这个结果。
### 2.基本用法
Promise构造函数接受一个函数作为参数，该函数的两个参数分别是resolve和reject。

### 3.Promise.prototype.then()
作用是为 Promise 实例添加状态改变时的回调函数。
### 4.Promise.prototype.catch() 
Promise.prototype.catch方法是.then(null, rejection)的别名，用于指定发生错误时的回调函数。
### 5.Promise.prototype.finally()
finally方法用于指定不管 Promise 对象最后状态如何，都会执行的操作。
### 6.Promise.all()
Promise.all方法用于将多个 Promise 实例，包装成一个新的 Promise 实例。
### 7.Promise.race() 
Promise.race方法同样是将多个 Promise 实例，包装成一个新的 Promise 实例。
### 8.Promise.resolve()
有时需要将现有对象转为 Promise 对象，Promise.resolve方法就起到这个作用。
### 9.Promise.reject()
Promise.reject(reason)方法也会返回一个新的 Promise 实例，该实例的状态为rejected。
### 10.应用
将图片的加载写成一个Promise，一旦加载完成，Promise的状态就发生变化。

Generator 函数管理流程，遇到异步操作的时候，通常返回一个Promise对象。

### 11.Promise.try()
Promise.try就是模拟try代码块，就像promise.catch模拟的是catch代码块。
# 15.Iterator 和 for...of 循环
### 1.Iterator（遍历器）的概念
一种接口，为各种不同的数据结构提供统一的访问机制。任何数据结构只要部署 Iterator 接口，就可以完成遍历操作.

Iterator 的作用有三个：一是为各种数据结构，提供一个统一的、简便的访问接口；二是使得数据结构的成员能够按某种次序排列；三是 ES6 创造了一种新的遍历命令for...of循环，Iterator 接口主要供for...of消费。

Iterator 的遍历过程是这样的。

（1）创建一个指针对象，指向当前数据结构的起始位置。也就是说，遍历器对象本质上，就是一个指针对象。

（2）第一次调用指针对象的next方法，可以将指针指向数据结构的第一个成员。

（3）第二次调用指针对象的next方法，指针就指向数据结构的第二个成员。

（4）不断调用指针对象的next方法，直到它指向数据结构的结束位置
### 2.默认 Iterator 接口
提供了一种统一的访问机制，即for...of循环。

默认的 Iterator 接口部署在数据结构的Symbol.iterator属性

###### 原生具备 Iterator 接口的数据结构如下。

Array
Map
Set
String
TypedArray
函数的arguments对象
NodeList对象
### 3.调用 Iterator 接口的场合
（1）解构赋值

（2）扩展运算符

（3）yield*
###### 任何接受数组作为参数的场合，其实都调用了遍历器接口。

for...of

Array.from()

Map(), Set(), WeakMap(), WeakSet()（比如new Map([['a',1],['b',2]])）

Promise.all()

Promise.race()
### 4.字符串的 Iterator 接口
字符串是一个类似数组的对象，也原生具有 Iterator 接口。
### 5.Iterator 接口与 Generator 函数

### 6.遍历器对象的 return()，throw() 
return方法的使用场合是，如果for...of循环提前退出（通常是因为出错，或者有break语句或continue语句），就会调用return方法。

throw方法主要是配合 Generator 函数使用，一般的遍历器对象用不到这个方法。
### 7.or...of 循环
for...of循环可以使用的范围包括数组、Set 和 Map 结构、某些类似数组的对象（比如arguments对象、DOM NodeList 对象）、后文的 Generator 对象，以及字符串。
# 16.Generator 函数的语法
### 1.简介
Generator 函数是 ES6 提供的一种异步编程解决方案，语法行为与传统函数完全不同。

执行 Generator 函数会返回一个遍历器对象，也就是说，Generator 函数除了状态机，还是一个遍历器对象生成函数。返回的遍历器对象，可以依次遍历 Generator 函数内部的每一个状态。

###### 两个特征。
一是，function关键字与函数名之间有一个星号；

二是，函数体内部使用yield表达式，定义不同的内部状态（yield在英语里的意思就是“产出”）。

遍历器对象的next方法的运行逻辑如下。

（1）遇到yield表达式，就暂停执行后面的操作，并将紧跟在yield后面的那个表达式的值，作为返回的对象的value属性值。

（2）下一次调用next方法时，再继续往下执行，直到遇到下一个yield表达式。

（3）如果没有再遇到新的yield表达式，就一直运行到函数结束，直到return语句为止，并将return语句后面的表达式的值，作为返回的对象的value属性值。

（4）如果该函数没有return语句，则返回的对象的value属性值为undefined。
### 2.next 方法的参数
yield表达式本身没有返回值，或者说总是返回undefined。next方法可以带一个参数，该参数就会被当作上一个yield表达式的返回值。
### 3.for...of 循环
for...of循环可以自动遍历 Generator 函数时生成的Iterator对象，且此时不再需要调用next方法。
### 4.Generator.prototype.throw() 
Generator 函数返回的遍历器对象，都有一个throw方法，可以在函数体外抛出错误，然后在 Generator 函数体内捕获。
### 5.Generator.prototype.return()
Generator 函数返回的遍历器对象，还有一个return方法，可以返回给定的值，并且终结遍历 Generator 函数。
### 6.next()、throw()、return() 的共同点
它们的作用都是让 Generator 函数恢复执行，并且使用不同的语句替换yield表达式。

next()是将yield表达式替换成一个值。

throw()是将yield表达式替换成一个throw语句。

return()是将yield表达式替换成一个return语句。
### 7.yield* 表达式
yield*表达式，用来在一个 Generator 函数里面执行另一个 Generator 函数。
### 8.作为对象属性的 Generator 函数

### 9.Generator 函数的this
Generator 函数总是返回一个遍历器，ES6 规定这个遍历器是 Generator 函数的实例，也继承了 Generator 函数的prototype对象上的方法。
### 10.含义
Generator 是实现状态机的最佳结构。

协程（coroutine）是一种程序运行的方式，可以理解成“协作的线程”或“协作的函数”。协程既可以用单线程实现，也可以用多线程实现。前者是一种特殊的子例程，后者是一种特殊的线程。
### 11.应用
（1）异步操作的同步化表达

（2）控制流管理

（3）部署 Iterator 接口

（4）作为数据结构
# 17.Generator 函数的异步应用
### 1.传统方法
###### ES6 诞生以前，异步编程的方法，大概有下面四种。

回调函数/
事件监听/
发布/订阅/
Promise 对象
### 2.基本概念
所谓"异步"，简单说就是一个任务不是连续完成的，可以理解成该任务被人为分成两段，先执行第一段，然后转而执行其他任务，等做好了准备，再回过头执行第二段。

Promise 的写法只是回调函数的改进，使用then方法以后，异步任务的两段执行看得更清楚了，除此以外，并无新意。
### 3.Generator 函数
协程的 Generator 函数实现

next返回值的 value 属性，是 Generator 函数向外输出数据；next方法还可以接受参数，向 Generator 函数体内输入数据。

异步任务的封装
### 4.Thunk 函数
Thunk 函数是自动执行 Generator 函数的一种方法。
### 5.co 模块
co 模块其实就是将两种自动执行器（Thunk 函数和 Promise 对象），包装成一个模块。使用 co 的前提条件是，Generator 函数的yield命令后面，只能是 Thunk 函数或 Promise 对象。
# 18.async 函数
### 1.含义
 async 函数，使得异步操作变得更加方便。就是 Generator 函数的语法糖。
 
### 2.基本用法
async函数返回一个 Promise 对象，可以使用then方法添加回调函数。当函数执行的时候，一旦遇到await就会先返回，等到异步操作完成，再接着执行函数体内后面的语句。
### 3.语法
async函数的语法规则总体上比较简单，难点是错误处理机制。
### 4.async 函数的实现原理
async 函数的实现原理，就是将 Generator 函数和自动执行器，包装在一个函数里。
### 5.与其他异步处理方法的比较
 Async 函数的实现最简洁，最符合语义，几乎没有语义不相关的代码。
### 6.实例：按顺序完成异步操作

### 7.异步遍历器
# 19.Class 的基本语法
### 1.简介
生成实例对象的传统方法是通过构造函数。

一个“类”，可以看到里面有一个constructor方法，这就是构造方法，而this关键字则代表实例对象。
### 2.严格模式
类和模块的内部，默认就是严格模式，所以不需要使用use strict指定运行模式。只要你的代码写在类或模块之中，就只有严格模式可用。
### 3.constructor 方法
constructor方法是类的默认方法，通过new命令生成对象实例时，自动调用该方法。一个类必须有constructor方法，如果没有显式定义，一个空的constructor方法会被默认添加。
### 4.类的实例对象
生成类的实例对象的写法，与 ES5 完全一样，也是使用new命令。

可以通过实例的__proto__属性为“类”添加方法。
### 5.Class 表达式
类也可以使用表达式的形式定义。
### 6.不存在变量提升
类不存在变量提升（hoist），这一点与 ES5 完全不同。
### 7.私有方法和私有属性

### 8.this 的指向
类的方法内部如果含有this，它默认指向类的实例
### 9.name 属性
name属性总是返回紧跟在class关键字后面的类名。
### 10.Class 的取值函数（getter）和存值函数（setter）
在“类”的内部可以使用get和set关键字，对某个属性设置存值函数和取值函数，拦截该属性的存取行为。
### 11.Class 的 Generator 方法
某个方法之前加上星号（*），就表示该方法是一个 Generator 函数。
### 12.Class 的静态方法
类相当于实例的原型，所有在类中定义的方法，都会被实例继承。如果在一个方法前，加上static关键字，就表示该方法不会被实例继承，而是直接通过类来调用，这就称为“静态方法”。
### 13.Class 的静态属性和实例属性
静态属性指的是 Class 本身的属性，即Class.propName，而不是定义在实例对象（this）上的属性。
### 14.new.target 属性
new是从构造函数生成实例对象的命令。ES6 为new命令引入了一个new.target属性，该属性一般用在构造函数之中，返回new命令作用于的那个构造函数。
# 20.Class 的继承
### 1.简介
Class 可以通过extends关键字实现继承，这比 ES5 的通过修改原型链实现继承，要清晰和方便很多。

super关键字，它在这里表示父类的构造函数，用来新建父类的this对象。
### 2.Object.getPrototypeOf()
Object.getPrototypeOf方法可以用来从子类上获取父类。
### 3.super 关键字
super这个关键字，既可以当作函数使用，也可以当作对象使用。在这两种情况下，它的用法完全不同。

第一种情况，super作为函数调用时，代表父类的构造函数。

第二种情况，super作为对象时，在普通方法中，指向父类的原型对象；在静态方法中，指向父类。
### 4.类的 prototype 属性和__proto__属性
每一个对象都有__proto__属性，指向对应的构造函数的prototype属性。Class 作为构造函数的语法糖，同时有prototype属性和__proto__属性，因此同时存在两条继承链。

（1）子类的__proto__属性，表示构造函数的继承，总是指向父类。

（2）子类prototype属性的__proto__属性，表示方法的继承，总是指向父类的prototype属性。
### 5.原生构造函数的继承
原生构造函数是指语言内置的构造函数，通常用来生成数据结构。ECMAScript 的原生构造函数大致有下面这些。

Boolean()
Number()
String()
Array()
Date()
Function()
RegExp()
Error()
Object()
### 6.Mixin 模式的实现
Mixin 指的是多个对象合成一个新的对象，新对象具有各个组成成员的接口。
# 21.修饰器
### 1.类的修饰
修饰器是一个对类进行处理的函数。修饰器函数的第一个参数，就是所要修饰的目标类。
### 2.方法的修饰
修饰器不仅可以修饰类，还可以修饰类的属性。
### 3.为什么修饰器不能用于函数？
修饰器只能用于类和类的方法，不能用于函数，因为存在函数提升。
### 4.core-decorators.js
一个第三方模块，提供了几个常见的修饰器
### 5.使用修饰器实现自动发布事件
可以使用修饰器，使得对象的方法被调用时，自动发出一个事件。
### 6.Mixin
Mixin模式，就是对象继承的一种替代方案，中文译为“混入”（mix in），意为在一个对象之中混入另外一个对象的方法。
### 7.Trait
Trait 也是一种修饰器，效果与 Mixin 类似，但是提供更多功能，比如防止同名方法的冲突、排除混入某些方法、为混入的方法起别名等等。
### 8.Babel 转码器的支持
# 22.Module 的语法
### 1.概述
模块加载方案，最主要的有 CommonJS 和 AMD 两种。前者用于服务器，后者用于浏览器。

### 2.严格模式
###### 严格模式主要有以下限制。

变量必须声明后再使用

函数的参数不能有同名属性，否则报错

不能使用with语句

不能对只读属性赋值，否则报错

不能使用前缀 0 表示八进制数，否则报错

不能删除不可删除的属性，否则报错

不能删除变量delete prop，会报错，只能删除属性delete global[prop]

eval不会在它的外层作用域引入变量

eval和arguments不能被重新赋值

arguments不会自动反映函数参数的变化

不能使用arguments.callee

不能使用arguments.caller

禁止this指向全局对象

不能使用fn.caller和fn.arguments获取函数调用的堆栈

增加了保留字（比如protected、static和interface）
### 3.export 命令
模块功能主要由两个命令构成：export和import。export命令用于规定模块的对外接口，import命令用于输入其他模块提供的功能。

export命令可以出现在模块的任何位置，只要处于模块顶层就可以。
### 4.import 命令
想为输入的变量重新取一个名字，import命令要使用as关键字，将输入的变量重命名。

import命令具有提升效果，会提升到整个模块的头部，首先执行。

import是静态执行，所以不能使用表达式和变量，这些只有在运行时才能得到结果的语法结构。
### 5.模块的整体加载
使用整体加载，即用星号（*）指定一个对象，所有输出值都加载在这个对象上面。
### 6.export default 命令
export default命令，为模块指定默认输出。

这时import命令后面，不使用大括号。
### 7.export 与 import 的复合写法
一个模块之中，先输入后输出同一个模块，import语句可以与export语句写在一起。
### 8.模块的继承
模块之间也可以继承。
### 9.跨模块常量

### 10.import()
import()函数，完成动态加载。
# 23.Module 的加载实现
### 1.浏览器加载
HTML 网页中，浏览器通过<script>标签加载 JavaScript 脚本。

</script>标签打开defer或async属性，脚本就会异步加载。

###### 外部的模块脚本（上例是foo.js），有几点需要注意。

代码是在模块作用域之中运行，而不是在全局作用域运行。模块内部的顶层变量，外部不可见。

模块脚本自动采用严格模式，不管有没有声明use strict。

模块之中，可以使用import命令加载其他模块（.js后缀不可省略，需要提供绝对 URL 或相对 URL），也可以使用export命令输出对外接口。

模块之中，顶层的this关键字返回undefined，而不是指向window。也就是说，在模块顶层使用this关键字，是无意义的。

同一个模块如果加载多次，将只执行一次。

### 2.ES6 模块与 CommonJS 模块的差异
###### 重大差异。

CommonJS 模块输出的是一个值的拷贝，ES6 模块输出的是值的引用。

CommonJS 模块是运行时加载，ES6 模块是编译时输出接口。
### 3.Node 加载

### 4.循环加载
“循环加载”（circular dependency）指的是，a脚本的执行依赖b脚本，而b脚本的执行又依赖a脚本。
### 5.ES6 模块的转码
ES6 module transpiler

SystemJS
# 24.编程风格
### 1.块级作用域
（1）let 取代 var

（2）全局常量和线程安全
在let和const之间，建议优先使用const，尤其是在全局环境，不应该设置变量，只应设置常量。
### 2.字符串
静态字符串一律使用单引号或反引号，不使用双引号。动态字符串使用反引号。
### 3.解构赋值
使用数组成员对变量赋值时，优先使用解构赋值。

函数的参数如果是对象的成员，优先使用解构赋值。

函数返回多个值，优先使用对象的解构赋值，而不是数组的解构赋值。
### 4.对象
单行定义的对象，最后一个成员不以逗号结尾。多行定义的对象，最后一个成员以逗号结尾。

对象尽量静态化，如果添加属性不可避免，要使用Object.assign方法。

在创造对象的时候，使用属性表达式定义。

对象的属性和方法，尽量采用简洁表达法，这样易于描述和书写。
### 5.数组
使用扩展运算符（...）拷贝数组。

Array.from 方法，将类似数组的对象转为数组。

### 6.函数
立即执行函数可以写成箭头函数的形式

那些需要使用函数表达式的场合，尽量用箭头函数代替。因为这样更简洁，而且绑定了 this。

箭头函数取代Function.prototype.bind，不应再用 self/_this/that 绑定 this。

所有配置项都应该集中在一个对象，放在最后一个参数，布尔值不可以直接作为参数。

不要在函数体内使用 arguments 变量，使用 rest 运算符（...）代替。

使用默认值语法设置函数参数的默认值。
### 7.Map 结构
区分 Object 和 Map，只有模拟现实世界的实体对象时，才使用 Object。如果只是需要key: value的数据结构，使用 Map 结构。因为 Map 有内建的遍历机制。
### 8.Class
总是用 Class，取代需要 prototype 的操作。因为 Class 的写法更简洁，更易于理解。

使用extends实现继承，因为这样更简单，不会有破坏instanceof运算的危险。
### 9.模块
Module 语法是 JavaScript 模块的标准写法，坚持使用这种写法。使用import取代require。

使用export取代module.exports。

如果模块只有一个输出值，就使用export default

不要在模块输入中使用通配符。因为这样可以确保你的模块之中，有一个默认输出

如果模块默认输出一个函数，函数名的首字母应该小写。

如果模块默认输出一个对象，对象名的首字母应该大写
### 10.ESLint 的使用
一个语法规则和代码风格的检查工具，可以用来保证写出语法正确、风格统一的代码。
# 25.读懂 ECMAScript 规格
### 1.概述
规格文件是计算机语言的官方标准，详细描述语法规则和实现方法。
### 2.术语
抽象操作

Record 和 field

[[Notation]] 

Completion Record
### 3.抽象操作的标准流程

### 4.相等运算符

### 5.数组的空位

### 6.数组的 map 方法
# 26.ArrayBuffer
二进制数组由三类对象组成。

（1）ArrayBuffer对象：代表内存之中的一段二进制数据，可以通过“视图”进行操作。“视图”部署了数组接口，这意味着，可以用数组的方法操作内存。

（2）TypedArray视图：共包括 9 种类型的视图，比如Uint8Array（无符号 8 位整数）数组视图, Int16Array（16 位整数）数组视图, Float32Array（32 位浮点数）数组视图等等。

（3）DataView视图：可以自定义复合格式的视图，比如第一个字节是 Uint8（无符号 8 位整数）、第二、三个字节是 Int16（16 位整数）、第四个字节开始是 Float32（32 位浮点数）等等，此外还可以自定义字节序。

ArrayBuffer对象代表原始的二进制数据，TypedArray 视图用来读写简单类型的二进制数据，DataView视图用来读写复杂类型的二进制数据。

###### 浏览器操作的 API，用到了二进制数组操作二进制数据。

File API

XMLHttpRequest

Fetch API

Canvas

WebSockets
### 1.ArrayBuffer 对象
ArrayBuffer对象代表储存二进制数据的一段内存，它不能直接读写，只能通过视图（TypedArray视图和DataView视图)来读写，视图的作用是以指定格式解读二进制数据。

ArrayBuffer也是一个构造函数，可以分配一段可以存放数据的连续内存区域。

ArrayBuffer.prototype.byteLength

ArrayBuffer.prototype.slice()

ArrayBuffer.isView()

### 2.TypedArray 视图
###### typedArray 视图一共包括 9 种类型，每一种视图都是一种构造函数。

Int8Array：8 位有符号整数，长度 1 个字节。

Uint8Array：8 位无符号整数，长度 1 个字节。

Uint8ClampedArray：8 位无符号整数，长度 1 个字节，溢出处理不同。

Int16Array：16 位有符号整数，长度 2 个字节。

Uint16Array：16 位无符号整数，长度 2 个字节。

Int32Array：32 位有符号整数，长度 4 个字节。

Uint32Array：32 位无符号整数，长度 4 个字节。

Float32Array：32 位浮点数，长度 4 个字节。

Float64Array：64 位浮点数，长度 8 个字节。

（1）TypedArray(buffer, byteOffset=0, length?)

（2）TypedArray(length)

（3）TypedArray(typedArray)

（4）TypedArray(arrayLikeObject)

普通数组的操作方法和属性，对 TypedArray 数组完全适用。

字节序指的是数值在内存中的表示方式。

每一种视图的构造函数，都有一个BYTES_PER_ELEMENT属性，表示这种数据类型占据的字节数。

ArrayBuffer 与字符串的互相转换。

溢出

TypedArray.prototype.buffer

TypedArray.prototype.byteLength，TypedArray.prototype.byteOffset

TypedArray.prototype.length

TypedArray.prototype.set()

TypedArray.prototype.subarray()

TypedArray.prototype.slice()

TypedArray.of() 

TypedArray.from() 
### 3.复合视图
视图的构造函数可以指定起始位置和长度，所以在同一段内存之中，可以依次存放不同类型的数据，这叫做“复合视图”。
### 4.DataView 视图
DataView视图本身也是构造函数，接受一个ArrayBuffer对象作为参数，生成视图。
### 5.二进制数组的应用
AJAX

Canvas

WebSocket

Fetch API

File API
### 6.SharedArrayBuffer
SharedArrayBuffer，允许 Worker 线程与主线程共享同一块内存。SharedArrayBuffer的 API 与ArrayBuffer一模一样，唯一的区别是后者无法共享。
### 7.Atomics 对象
（1）Atomics.store()，Atomics.load()

（2）Atomics.wait()，Atomics.wake()

（3）运算方法

（4）其他方法
# 27.最新提案
### 1.do 表达式
块级作用域之前加上do，使它变为do表达式，然后就会返回内部最后执行的表达式的值。
### 2.throw 表达式
throw表达式里面的throw不再是一个命令，而是一个运算符。
### 3.链判断运算符
如果读取对象内部的某个属性，往往需要判断一下该对象是否存在
。

链判断运算符”（optional chaining operator）?.，简化上面的写法。
### 4.直接输入 U+2028 和 U+2029

### 5.函数的部分执行
多参数的函数有时需要绑定其中的一个或多个参数，然后返回一个新函数。
### 6.管道运算符
JavaScript 的管道是一个运算符，写作|>。它的左边是一个表达式，右边是一个函数。管道运算符把左边表达式的值，传入右边的函数进行求值。
### 7.数值分隔符

### 8.BigInt 数据类型
BigInt 只用来表示整数，没有位数的限制，任何位数的整数都可以精确表示。
### 9.Math.signbit()
MBigInt 只用来表示整数，没有位数的限制，任何位数的整数都可以精确表示。ath.signbit()方法判断一个数的符号位是否设置了。
