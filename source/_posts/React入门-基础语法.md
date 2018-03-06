
#### （1）JSX语法深入理解
简介：从根本上来说，JSX语法提供了一种创建React元素的语法糖，JSX语句可以编译成： React.createElement(component, props, …children)的形式。

```
<MyButton color="blue" shadowSize={2}>
  Click Me
</MyButton>

//编译结果：
React.createElement(
  MyButton,
  {color: 'blue', shadowSize: 2},
  'Click Me'
)

//使用自闭和的形式：
<div className="sidebar" />
```
**1.指定React元素的类型**

JSX标签的头部，决定了React元素的类型，大写的标签，意味着JSX的标签与React的组件一一对应

```
<Foo/>标签就对应了Foo组件

//（1）必须包裹在一定的范围内
import React from 'react';
import CustomButton from './CustomButton';

function WarningButton() {
  // return React.createElement(CustomButton, {color: 'red'}, null);
  return <CustomButton color="red" />;
}
引入了2个组件，构成了一个新的组件WarningButton，组件的返回值的元素，必须包含在一定范围内，这里通过函数的’{ ‘, ’ } ‘实现包裹的效果。

 //（2）用户定义的组件必须大写

function Hello(){
   return <h2>Hello,World</h2>
}
//定义过程
<Hello/>
//使用过程

//(3)不能在运行期间，动态的选择类型

import React from 'react';
import { PhotoStory, VideoStory } from './stories';

const components = {
  photo: PhotoStory,
  video: VideoStory
};

function Story(props) {
  return <components[props.storyType] story={props.story} />;
  //这样写是不对的，我们在返回的组件中，动态定义了组件，这种动态的定义是无效的
}

//应该改写为:
import React from 'react';
import { PhotoStory, VideoStory } from './stories';

const components = {
  photo: PhotoStory,
  video: VideoStory
};

function Story(props) {

  const SpecificStory = components[props.storyType];
  return < SpecificStory  story={props.story} />;
    //这样就是正确的，我们不要在JSX的标签中使用动态定义
}
```
**2.JSX中的Props属性**

```
//（1）JS表达式
//通过{}，包裹js的语法来使用
<MyComponent foo={1 + 2 + 3 + 4} />

//（2）Props属性的默认值
<MyTextBox autocomplete />

<MyTextBox autocomplete={true} />
//两个式子是等价的，但是不推荐使用默认值，因为在ES6的语法中{foo}代表的意思是：{foo:foo}的意思，并不是{foo:true}。

//（3）扩展属性 
function App1() {
  return <Greeting firstName="Ben" lastName="Hector" />;
}

function App2() {
  const props = {firstName: 'Ben', lastName: 'Hector'};
  return <Greeting {...props} />;
}
```
**3.JSX中的children**

```
//（1）children中的function
function ListOfTenThings() {
  return (
    <Repeat numTimes={10}>
      {(index) => <div key={index}>This is item {index} in the list</div>}
    </Repeat>
  );
}

function Repeat(props) {
  let items = [];
  for (let i = 0; i < props.numTimes; i++) {
    items.push(props.children(i));
  }
  return <div>{items}</div>;
}
//Repeat组件的定义中可以看出来，children中的方法按此定义会一直执行10次

//（2）忽略Boolean，Null以及Undefined
//false,null,undefined以及true是不能通过render()方法，呈现在页面上的，下面的这些div块的样式 相同，都是空白块：
<div />

<div></div>

<div>{false}</div>

<div>{null}</div>

<div>{true}</div>

<div>
  {showHeader && <Header />}
  <Content />
</div>
//逻辑是，只有showHeader==true，在会在页面呈现Header组件，否则为null，即为不显示任何东西，这相当于一个if的判断了。

<div>
  {props.messages.length &&
    <MessageList messages={props.messages} />
  }
</div>
//即使元素为0，0是能够呈现在页面中的。也就是说上述代码中，只要 
props.messages数组存在，不管长度是否为0都是存在的。

//（3）如何显示Null，Undefined和Boolean
<div>
  My JavaScript variable is {String(myVariable)}.
</div>
//其先转化为字符串之后再显示
```
## （2）对于Refs最新变动的理解
#### 1.什么是ReactJS中的refs
React中组件并不是真实的 DOM 节点，而是存在于内存之中的一种数据结构，叫做虚拟 DOM （virtual DOM）。只有当它插入文档以后，才会变成真实的 DOM 。根据 React 的设计，所有的 DOM 变动，都先在虚拟 DO上发生，然后再将实际发生变动的部分，反映在真实 DOM上，这种算法叫做 DOM diff ，它可以极大提高网页的性能表现。
如果我们想在虚拟DOM时（此时DOM还没有转化为真是DOM），取到某一个元素，此时不能通过JS的getElementByXXX这种形式。

#### 2.ReactJS前期的做法
在虚拟DOM阶段取元素，语法如下：

```
function Hello(){
    handleClick:function(){
       this.refs.myinput.fucus();
    }
    return <input ref="myinput" />
 }
```
可以通过refs.[refsName]来取得虚拟DOM中的元素
#### 3.ReactJS最新版本，对于refs的定义
组件中的refs是一个回调函数。这个函数，在组件生成期（mounted）会自动执行，这个回调函数的参数是元素本身：

```
function Hello(){
   handleClick:function(){

   }
   return <input ref={(input)=>{this.myinput=input;}}/>
}
```
ref的函数，传入了input元素本身，并且将this.myinput赋值为input元素本身。

在元素的销毁期（unmounted）也会执行，但是在销毁期，无论如何只会返回null。

ref 属性：React 支持一种非常特殊的属性，你可以用来绑定到 render() 输出的任何组件上去。这个特殊的属性允许你引用 render() 返回的相应的支撑实例（ backing instance ）。这样就可以确保在任何时间总是拿到正确的实例。

```
<input type="text" ref="username" />  
  
//下面4种方式都可以通过ref获取真实DOM节点  
var usernameDOM = this.refs.username.getDOMNode();  
var usernameDOM = React.findDOMNode(this.refs.username);  
var usernameDOM = this.refs['username'].getDOMNode();  
var usernameDOM = React.findDOMNode(this.refs['username']);  
```
## （3）React中的Context
简介：在React中，数据可以以流的形式自上而下的传递，每当你使用一个组件的时候，你可以看到组件的props属性会自上而下的传递。但是，在某些情况下，我们不想通过父组件的props属性一级一级的往下传递，我们希望在某一级子组件中，直接得到上N级父组件中props中的值。
##### 1.一般情况下通过props传值的情况

```
class Button extends React.Component {
  render() {
    return (
      <button style={{background: this.props.color}}>
        {this.props.children}
      </button>
    );
  }
}

class Message extends React.Component {
  render() {
    return (
      <div>
        {this.props.text} <Button color={this.props.color}>Delete</Button>
      </div>
    );
  }
}

class MessageList extends React.Component {
  render() {
    const color = "purple";
    const children = this.props.messages.map((message) =>
      <Message text={message.text} color={color} />
    );
    return <div>{children}</div>;
  }
}
```
分析一下这段代码，大致的组件分为3级:顶层MessageLists——>Message一级子类——>Button底层子类，我们来看从父组件到子组件的值的传递情况：

（1）text:我们可以看到，在顶层组件MessageLists中的值，传递到一级子组件Message中，并在此组件中被使用。

（2）color:再看props中的color的传递情况，在顶层组件MessageLists中的值，先传递到一级子组件Message中，在传递到二级子组件Button中，最后在二级子组件中被使用。

综上：这就是一般在React中，所使用的通过props属性，在父组件与子组件中进行值传递。

#### 2.如何利用React中的Context来进行值的越级传递。

```
class Button extends React.Component {
  render() {
    return (
      <button style={{background: this.context.color}}>
        {this.props.children}
      </button>
    );
  }
}

Button.contextTypes = {
  color: React.PropTypes.string
};

class Message extends React.Component {
  render() {
    return (
      <div>
        {this.props.text} <Button>Delete</Button>
      </div>
    );
  }
}

class MessageList extends React.Component {
  getChildContext() {
    return {color: "purple"};
  }

  render() {
    const children = this.props.messages.map((message) =>
      <Message text={message.text} />
    );
    return <div>{children}</div>;
  }
}

MessageList.childContextTypes = {
  color: React.PropTypes.string
};
```
上述代码，我们实现了通过React的Context实现了值——color的越级传递。我们来分析一下上述的方法。

（1）首先在顶层组件中：

```
MessageList.childContextTypes = {
  color: React.PropTypes.string
};
```
定义了顶层组件所拥有的子类context对象——该顶层组件所拥有的的子类context对象为color，且必须为字符串。

然后通过getChildText方法，来给子context对象的属性赋值：

```
getChildContext() {

    return {color: "purple"};
  }
```
这样就完成了顶层组件中，context对象的赋值。

（2）越级传递，因为color属性只在最底层使用

我们来看color属性的越级传递，因为color属性，在一级子组件Message中并没有直接用到，因此我们可以直接传递到最底层（越级），在Button组件中使用。

首先Button组件中，再次声明了所接受到的context的子组件color的类型，声明必须为字符串：

```
Button.contextTypes = {
  color: React.PropTypes.string
};
```
然后可以通过this.context.color这种方式调用：

```
<button style={{background: this.context.color}}>
        {this.props.children}
 </button>
```
## （4）ShouldComponentUpdate的用法
简介：ShouldCompleteUpdate，指明什么时候component（组件）需要进行更新。
#### 1.常见的SCU的用法：

```
//（1）比如在下面的例子中，组件中只有2个值，props.color和state.count可以发生改变
class CounterButton extends React.Component {
  constructor(props) {
    super(props);
    this.state = {count: 1};
  }

  shouldComponentUpdate(nextProps, nextState) {
    if (this.props.color !== nextProps.color) {
      return true;
    }
    if (this.state.count !== nextState.count) {
      return true;
    }
    return false;
  }

  render() {
    <button
      color={this.props.color}
      onClick={() => this.setState(state => ({count: state.count + 1}))}>
      Count: {this.state.count}
    </button>
  }
}
//组件仅仅会校验prop.color和state.count,如果这些值都不会改变，那么组件就不会有更新。

//（2）如果组件更加复杂，拥有的状态变量更多
//当组件复杂化，拥有状态变多时，我们需要设计一种模式，对所有的props变量和state变量，做一个“shallow comparison(浅比较）”，这样会使得SCU函数冗杂化，为了解决该问题，React给了我们提供了另一个继承方法——React.PureComponent：
class CounterButton extends React.PureComponent {
  constructor(props) {
    super(props);
    this.state = {count: 1};
  }

  render() {
    <button
      color={this.props.color}
      onClick={() => this.setState(state => ({count: state.count + 1}))}>
      Count: {this.state.count}
    </button>
  }
}
//在大部门情况下我们可以用React.PureComponent来代替SCU，但是当props和state中的变量发生突变的情况下，
//“shallow comparison”会失效，因此在props和state的变量发生突变的情况下，
//不能通过React.PureComponent来更新组件。

var x=[1,2];
var y=x;
x.push(3);
console.log(x==y)//输出true

var x={a:1};
var y=x;
x.b=2;
console.log(x==y)//输出true
//shallow comparison不能进行深层比较的原因是，js中数组和对象的本质都是Object，
//一旦赋值y=x后，无论x如何变化，x,y都会只想的是同一个对象。

```
#### 3.如何解决shallow comparison失效的问题

```
//失效状态1：
handleClick() {
    // This section is bad style and causes a bug
    const words = this.state.words;
    words.push('marklar');
    this.setState({words: words});
  }

//解决方法：
handleClick() {
  this.setState(prevState => ({
    words: prevState.words.concat(['marklar'])
  }));
}

//失效状态2：
function updateColorMap(colormap) {
  colormap.right = 'blue';
}

//解决方法：
function updateColorMap(colormap) {
  return Object.assign({}, colormap, {right: 'blue'});
}

//本质:解决方法的本质是生成了一个新的对象，新对象与原对象比较一定返回的是false。
```