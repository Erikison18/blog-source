---
title: 从零开始学react
date: 2018-03-04 21:04:43
tags: react
categories: 
  - react
---

## react(1)---HelloWorld
### 安装
npm install -g create-react-app

create-react-app my-app

cd my-app

npm start

### 初识react

```
1.JSX
const h1 = <h1>Hello world</h1>;

2.JSX元素
const h1 = <h1>Hello world</h1>;
//将一个JSX元素储存到了一个变量中
const temp = {
  teacher: <li>张三</li>,
  monitor: <li>李四</li>,
  student: <li>王五</li>,
};
///把几个JSX元素储存到了一个object中

const temp=(
<a id="aid" href="https://buppt.github.io">
    <h1>
         我的博客
    </h1>
</a>
);

//这样是不可以的：
const temp = (
  <p>我在最外层.</p> 
  <p>我也在最外层.</p>
);
//这样才可以：
const temp = (
    <div>
      <p>我不在最外层.</p> 
      <p>我不在最外层.</p>
    </div>
);

3.让JSX元素显示在浏览器中
//ReactDOM.render(JSX元素，id)可以将JSX元素显示在浏览器上
const testList=(<ul>
    <li>test1</li>
    <li>test2</li>
    <li>test3</li>
  </ul>);
ReactDOM.render(testList,document.getElementById('test'));
```
## react(2)---JSX语法进阶

```
//1.JSX元素需闭合
<img ..   /> 
<br/>

//JSX中的JS,
//JSX中使用JS需要将JS放在{大括号内}，如：
ReactDOM.render(<h1>{2 + 3}</h1>,document.getElementById('test'));

const test = 'Hello World';
ReactDOM.render(<h1>{test}</h1>,document.getElementById('test'));

function function1() {
        alert("hello");
}
const button =<button onClick={function1}>button</button>;
ReactDOM.render(button,document.getElementById('test'));

//3.条件语句
//JSX中不能使用if else语句，但是可以使用三元运算表达式来代替
ReactDOM.render(<h1>{1!=2?"sure":"impossible"}</h1>,document.getElementById('test'));

//4.数组的使用
//直接定义：
 var arr = [
        <h1>test1</h1>,
        <h2>test2</h2>,
    ];
    ReactDOM.render(
            <div>{arr}</div>,
        document.getElementById('test')
    );
//用.map()，这个其实更加方便
 var arr = ['test1','test2','test3'];
 var arrList = arr.map((arr,index) => <li key={index}>{arr}</li>);
 ReactDOM.render(<ul>{arrList}</ul>,document.getElementById('test'));

//5.样式的使用
   var myStyle = {
        fontSize: 20,
        color: '#FF0000'
    };
    ReactDOM.render(
        <h1 style = {myStyle}>hello world</h1>,
        document.getElementById('test')
    );

//6.注释
ReactDOM.render(
    <div>
    <h1>hello</h1>
    {/*注释...*/}
     </div>,
    document.getElementById('test')
);

//独立文件
//可以将JSX代码放在一个独立文件中，例如创建helloworld.js文件
//然后在HTML中引入该JS文件

//不用JSX
const h1 = <h1>Hello world</h1>;
//不用JSX写就像这样：
const h1 = React.createElement(
  "h1",
  null,
  "Hello, world"
);
```
## react(3)---组件的创建

```
//组件的创建既可以用createClass(ES5语法)也可以用class(ES6语法)
//使用ES5语法
var MyComponentES5 = React.createClass({
    render: function(){
        return (<h1>Hello world</h1>);
    }
});
//使用ES6语法
class MyComponentES6 extends React.Component {
  render() {
    return <h1>Hello world</h1>;
  }
}

//1.组件的创建
<body>
<div id="test"></div>
<script src="./react/react.development.js"></script>
<script src="./react/react-dom.development.js"></script>
<script src="https://cdn.bootcss.com/babel-core/5.8.38/browser.js"></script>
<script type="text/babel">
class Hello extends React.Component {
  render() {
    return (<h1>Hello world</h1>);
  }
}

ReactDOM.render(
  <Hello />,
  document.getElementById('test')
);
</script>
</body>
//创建了一个名叫Hello的组件。(注意：组件的名称首字母要大写！这是规定。) 
//在组件中，我们创建了一个render方法，这个方法返回了一个JSX表达式。 
//在ReactDOM.render()中使用组件的方法就是<组件名 />。

//2.组件中使用变量属性
const blog={
    src: 'https://buppt.github.io',
    name: 'buppt'
}
class Myblog extends React.Component{
    render(){
        return (
            <a href={blog.src}>这是我的博客{blog.name}</a>
        );
    }
}
ReactDOM.render(
  <Myblog />,
  document.getElementById('test')
);

//3.render方法
const test = Math.random() < 0.5;
class Hello extends React.Component{
  render(){
    let task;
    if(test){
      task = "I'm true";
    }else{
      task = "I'm false";
    }
    return (<h1>{task}</h1>);
  }
}
ReactDOM.render(
    <Hello />,
    document.getElementById('test')
);

//4.在组件中使用this
class Hello extends React.Component{
  get name() {
        return 'buppt';
  }
  render() {
    return (<h1>My name is {this.name}.</h1>);
  }
}
ReactDOM.render(
    <Hello />,
    document.getElementById('test')
);
//this即该组件

//5.组件中事件监听
class Hello extends React.Component{
  name() {
        alert('My name is buppt');
  }
  render() {
    return <button onClick={this.name}>点我！</button>;
  }
}
ReactDOM.render(
    <Hello />,
    document.getElementById('test')
);
//onClick事件要大写第一个C

//6.组件中使用另一个组件
class Hello extends React.Component {
  render() {
    return (<h1>Hello</h1>);
  }
}
class World extends React.Component {
  render() {
    return (
    <div>
        <Hello />
        <h1> World</h1>
    </div>);
  }
}
ReactDOM.render(
  <World />,
  document.getElementById('test')
);

//7.无状态组件
class Hello extends React.Component{
  render() {
    return (<h1>Hello</h1>);
  }
}
//可以写成下面的形式
const Hello = () =>{
    return <h1>Hello</h1>;
}

//这种形式的组件可以传递props属性
const Hello = (props) =>{
    return <h1>{props.message}</h1>;
}
ReactDOM.render(
  <Hello message="Hello World" />,
  document.getElementById('test')
);
```
## react(4)---组件的props和state
react组件具有props成员和state成员，这两个成员都是object类型，而props和state的主要区别是：props不可变，而state可以根据和用户的互交来改变。 

##### props
1.获取props

```
class Hello extends React.Component {
  render() {
    return (<h1>Hello {this.props.mes}</h1>);
  }
}
ReactDOM.render(
  <Hello mes="world" />,
  document.getElementById('test')
);
```
在ReactDOM.render()中给了组件Hello一个属性 mes=”Hello world” ,然后在创建组件的代码中使用{this.props.mes}来获取该属性的值，this.props.mes就是这个组件的props成员的mes属性。这样浏览器中显示出Hello world，说明获取到了mes属性的值。

2.默认props

```
class Hello extends React.Component {
  render() {
    return <h1>Hello {this.props.name}</h1>;
  }
}
Hello.defaultProps = { name: 'buppt'};
ReactDOM.render(
  <Hello />,
  document.getElementById('test')
);

//组件内部定义的写法
class Hello extends React.Component {
  static defaultProps = {
    name: 'buppt'
  }
  render() {
    return <h1>Hello {this.props.name}</h1>;
  }
}
```
用 Hello.defaultProps 给props属性设置一个默认值，这样我们在使用组件但没有给出属性值时，会显示默认值

3.props属性验证

```
//可以用 propTypes 给props属性设置一个类型限定
class Hello extends React.Component {
  //组件内设置如下
  //static propTypes = { name: React.PropTypes.string.isRequired,}
  render() {
    return <h1>Hello {this.props.name}</h1>;
  }
}
//组件外设置如下
//Hello.propTypes = { name: React.PropTypes.string.isRequired};
//var myName=123;
var myName="buppt";
ReactDOM.render(
  <Hello name={myName} />,
  document.getElementById('test')
);
// React.PropTypes 自 React v15.5 起已弃用。请使用 prop-types 库代替。
```
4.this.props.children

```
class Hello extends React.Component {
  render() {
    return <h1>Hello {this.props.children}</h1>;
  }
}

ReactDOM.render(
  <Hello>
    <span>I am buppt.</span>
    <br/>
    <span>Nice to meet you!</span>
  </Hello>,
  document.getElementById('test')
);
```
可以写成<组件名><组件名/>。 
每一个组件的props都有一个children属性，这个属性将返回所有在<组件名><组件名/>之间的内容。state

##### state
1.获取state

```
class Hello extends React.Component {
  constructor(props){
    super(props);
    this.state = { mood: 'happy' };
  }
  render() {
    return <h1>I am {this.state.mood}</h1>;
  }
}

ReactDOM.render(
  <Hello/>,
  document.getElementById('test')
);
```
和props不同，state不是从<组件名/>中传进来的，而是组件自己的状态


将会显示’I am happy’，至于为什么要先调用super(props)：ES6中，在子类的constructor中必须先调用super才能引用this。 
super(props)的目的：在constructor中可以使用this.props。 
根本原因是constructor会覆盖父类的constructor，导致你父类构造函数没执行，所以手动执行下。

##### 2.使用setState更新state

```
class Hello extends React.Component {
  constructor(props){
    super(props);
    this.state = { color: 'green' };
    this.changeColor = this.changeColor.bind(this);
  } 
  changeColor() {
    this.setState({ color: 'yellow' });
  } 
  render() {
    return (
      <div style={{background: this.state.color}}>
        <h1>
          Change my color
        </h1>
        <button onClick={this.changeColor}>Change color</button>
      </div>
    );
  }
}
```
使用this.setState()可以更新(改变)this.state中的属性值

其中用到了.bind(this)，使changeColor()无论怎样调用都有相同的this。
## react(5)---组件的生命周期
一个组件的生命周期可分为三个状态： 
1. Mounting: 已插入真实DOM 
2. updating:正在被重新渲染 
3. unmounting: 已移出真实DOM 


```
class Hello extends React.Component{
  constructor(props){
      super(props);
      console.log('1.构造函数');
      //初始化state
      this.state={ count:1 };
      this.handleClick=this.handleClick.bind(this);
  }
  //2.组件将要被渲染到真实的dom节点中
  componentWillMount(){
      console.log('2.componentWillMount');
  }
  //3.组件已经插入到真实的dom节点中
  componentDidMount(){
      console.log('3.componentDidMount');
  }
  //4.组件是否要被重新渲染
  shouldComponentUpdate(){
      console.log('4.shouldComponentUpdate');
      return true;
  }
  //5.组件将要被重新渲染
  componentWillUpdate(){
      console.log('5.componentWillUpdate');
  }
  //6.组件已经被重新渲染
  componentDidUpdate(){
       console.log('6.componentDidUpdate');
  }
  handleClick(){
      console.log('点击了按钮');
      this.setState({count:this.state.count+1})
      console.log('点击事件结束'); 
  }
  render(){
      console.log('render');
      return(
          <div>
              <h1>{this.state.count}</h1>
              <button onClick={this.handleClick}>Add</button>
          </div>
          )
  } 
}
ReactDOM.render(
  <Hello />,
  document.getElementById('test')
);
```
生命周期的方法有： 
1. componentWillMount : 在渲染前调用,在客户端也在服务端。 
2. componentDidMount : 在第一次渲染后调用，只在客户端。之后组件已经生成了对应的DOM结构，可以通过this.getDOMNode()来进行访问。 如果你想和其他JavaScript框架一起使用，可以在这个方法中调用setTimeout, setInterval或者发送AJAX请求等操作(防止异部操作阻塞UI)。 
3. componentWillReceiveProps : 在组件接收到一个新的prop时被调用。这个方法在初始化render时不会被调用。 
4. shouldComponentUpdate : 返回一个布尔值。在组件接收到新的props或者state时被调用。在初始化时或者使用forceUpdate时不被调用。可以在你确认不需要更新组件时使用。 
5. componentWillUpdate : 在组件接收到新的props或者state但还没有render时被调用。在初始化时不会被调用。 
6. componentDidUpdate : 在组件完成更新后立即调用。在初始化时不会被调用。 
7. componentWillUnmount : 在组件从 DOM 中移除的时候立刻被调用。】

## react(6)---props属性验证
React.PropTypes 自 React v15.5 起已弃用。请使用 prop-types 库代替。

```
import PropTypes from 'prop-types'; //ES6
//
//我们之前一直使用的是<script>标签引入，可引入如下标签
<script src="https://unpkg.com/prop-types/prop-types.js"></script>
//或者
<script src="https://unpkg.com/prop-types/prop-types.min.js"></script>

//一个例子
class Hello extends React.Component {
  render() {
    return <h1>{this.props.message}</h1>;
  }
}
Hello.propTypes = {
  message: PropTypes.string
};
var data="hello";
// var data = 11;
ReactDOM.render(
  <Hello message={data}/>,
  document.getElementById('test')
);
```
message为string类型时，没有问题，当message为其他类型（如number）时，控制台会产生如下warning


```
Hello.propTypes = {
  message: PropTypes.string.isRequired
}
```
如果该组件没有提供message属性，会打印警告信息。而前面的例子中，没有message属性并不会打印警告

#### 所有验证器

```
MyComponent.propTypes = {
  // 你可以将属性声明为以下 JS 原生类型
  optionalArray: PropTypes.array,
  optionalBool: PropTypes.bool,
  optionalFunc: PropTypes.func,
  optionalNumber: PropTypes.number,
  optionalObject: PropTypes.object,
  optionalString: PropTypes.string,
  optionalSymbol: PropTypes.symbol,
  //
  // 任何可被渲染的元素（包括数字、字符串、子元素或数组）。
  optionalNode: PropTypes.node,
  //
  // 一个 React 元素
  optionalElement: PropTypes.element,
  //
  // 你也可以声明属性为某个类的实例，这里使用 JS 的
  // instanceof 操作符实现。
  optionalMessage: PropTypes.instanceOf(Message),
  //
  // 你也可以限制你的属性值是某个特定值之一
  optionalEnum: PropTypes.oneOf(['News', 'Photos']),
  //
  // 限制它为列举类型之一的对象
  optionalUnion: PropTypes.oneOfType([
    PropTypes.string,
    PropTypes.number,
    PropTypes.instanceOf(Message)
  ]),
  //
  // 一个指定元素类型的数组
  optionalArrayOf: PropTypes.arrayOf(PropTypes.number),
  //
  // 一个指定类型的对象
  optionalObjectOf: PropTypes.objectOf(PropTypes.number),
  //
  // 一个指定属性及其类型的对象
  optionalObjectWithShape: PropTypes.shape({
    color: PropTypes.string,
    fontSize: PropTypes.number
  }),
  //
  // 你也可以在任何 PropTypes 属性后面加上 `isRequired` 
  // 后缀，这样如果这个属性父组件没有提供时，会打印警告信息
  requiredFunc: PropTypes.func.isRequired,
  //
  // 任意类型的数据
  requiredAny: PropTypes.any.isRequired,
  //
  // 你也可以指定一个自定义验证器。它应该在验证失败时返回
  // 一个 Error 对象而不是 `console.warn` 或抛出异常。
  // 不过在 `oneOfType` 中它不起作用。
  customProp: function(props, propName, componentName) {
    if (!/matchme/.test(props[propName])) {
      return new Error(
        'Invalid prop `' + propName + '` supplied to' +
        ' `' + componentName + '`. Validation failed.'
      );
    }
  },
  //
  // 不过你可以提供一个自定义的 `arrayOf` 或 `objectOf` 
  // 验证器，它应该在验证失败时返回一个 Error 对象。 它被用
  // 于验证数组或对象的每个值。验证器前两个参数的第一个是数组
  // 或对象本身，第二个是它们对应的键。
  customArrayProp: PropTypes.arrayOf(function(propValue, key, componentName, location, propFullName) {
    if (!/matchme/.test(propValue[key])) {
      return new Error(
        'Invalid prop `' + propFullName + '` supplied to' +
        ' `' + componentName + '`. Validation failed.'
      );
    }
  })
};
```
## react(7)---Create React App简介
安装的Create React App

```
npm install -g create-react-app
create-react-app my-app
//create-react-app能够帮你自动创建基于Webpack+ES6的最简易的React项目模板
cd my-app
npm start
```
简单使用：安装完成后，输入命令npm start可以启动配置，这样自动会进入开发模式，此时热替换是处于自动激活状态，你也可以实时地在界面或者命令行中看到错误提示。

当你开发完成，可以输入npm run build来编译得到生产环境，此时代码会被编译到build目录下，此时会自动将整个应用打包发布，它会自动使用Webpack控件进行优化与压缩。

```
//如下的目录结构：
my-app/
  node_modules/           //依赖的包
  public/
    index.html              //页面模板
    favicon.ico
    manifest.json
  src/              //开发源码
    App.css
    App.js          //
    App.test.js
    index.css
    index.js        //js入口文件
    logo.svg
    registerServiceWorker.js
  package.json
  package-lock.json
  README.md
  build/            //如果运行了`npm run build`
```

用import引入其他文件， 
如引入库文件import React from 'react'; 
引入css文件import './index.css'; 
引入其他js文件中的组件import App from './App';

App.js文件中最后export是为了导出App组件。index.js中获取id为root，可以在public/index.html文件中找到或修改。
## react(8)---表单的使用
使用的是Create React App：

```
//App.js
import React from 'react';

export class App extends React.Component {
  render() {
    return (
      <div>
        <h1>My name is</h1>
        <select>
          <option value="BUPPT">BUPPT</option>
          <option value="Ben">Ben</option>
          <option value="Beijing">Beijing</option>
        </select>
      </div>
    );
  }
}
//index.js
import React from 'react';
import ReactDOM from 'react-dom';
import {App} from './App';

ReactDOM.render(
    <App />,
    document.getElementById('root')
);
```
然后给App组件添加一个state.name，给下拉框添加一个onChange事件，这个事件根据下拉框的内容改变state.name的内容。然后在h1标签中显示出来。

```
//App.js
import React from 'react';

export class App extends React.Component {
  constructor(props){
    super(props);
    this.state = { 
      name: 'BUPPT' 
    };
    this.handleChange = this.handleChange.bind(this);
  }
  handleChange(e){
    const name = e.target.value;
    this.setState({
      name: name
    });
  }
  render() {
    return (
      <div>
        <h1>My name is {this.state.name}!</h1>
        <select onChange={this.handleChange}>
          <option value="BUPPT">BUPPT</option>
          <option value="Ben">Ben</option>
          <option value="Beijing">Beijing</option>
        </select>
      </div>
    );
  }
}
```
类似的，新建一个Input.js文件，在index.js中引入。

```
//Input.js
import React from 'react';

export class Input extends React.Component {
  render() {
    return (
      <div>
        <input type="text" />
        <h1></h1>
      </div>
    );
  }
}
//index.js
import React from 'react';
import ReactDOM from 'react-dom';
import {App} from './App';
import {Input} from './Input';
ReactDOM.render(
    <div>
        <App /><br/>
        <Input />
    </div>,
    document.getElementById('root')
);
```
给组件添加一个state.userInput，给input标签添加一个onChange事件，监听用户输入，根据用户输入修改state.userInput内容，然后在h1中显示出来

```
//Input.js
export class Input extends React.Component {
  constructor(props){
    super(props);
    this.state={
      userInput: '请输入内容'
    };
    this.handleUserInput=this.handleUserInput.bind(this);
  }
  handleUserInput(e) {
   this.setState({
     userInput: e.target.value
   });
  }
  render() {
    return (
      <div>
        <input type="text" value={this.state.userInput} onChange={this.handleUserInput} />
        <h1>{this.state.userInput}</h1>
      </div>
    );
  }
}
```
