# 精读React官方教程

> React 是一个用于构建用户界面的 JavaScript 库

`React`官方教程还是挺多的，现在我们来把学习到的东西总结一下，把重要的内容罗列出来以便于记忆

这里我把所有内容分为一下几个部分：

1. `React`基础
2. `React`高级指引
3. `React`的API
4. `React`测试

> 注意：除了特别的说明，此篇博客以及以后的博客文章中都将使用`TypeScript`，如果你还是不熟悉它，请先阅读官方文档： <a href="https://www.tslang.cn/" target="_blank" rel="noopener noreferrer">TypeScript</a>

## React基础

### 向应用中添加`React`

`React`并不强制你重新创建你的应用，你可以通过引入标签的方式使用它（但一般我们不会这么做 ^_^)

```html
<!-- ... 其它 HTML ... -->

  <!-- 加载 React。-->
  <!-- 注意: 部署时，将 "development.js" 替换为 "production.min.js"。-->
  <script src="https://unpkg.com/react@16/umd/react.development.js" crossorigin></script>
  <script src="https://unpkg.com/react-dom@16/umd/react-dom.development.js" crossorigin></script>

  <!-- 加载我们的 React 组件。-->
  <script src="like_button.js"></script>

</body>
```

So,一般来说我们直接创建一个`React`应用即可。

### 创建新的`React`应用

要创建一个新的`React`应用，推荐直接使用`crate-react-app`，它是官方维护的一个脚手架工具，其他方式可以参考官方文档。

我们可以直接通过下面的命令，来创建一个单页面的`React`应用

```bash
npx create-react-app my-app
cd my-app
npm start
```

> `npx`是`npm` 5.2+版本中自带的工具，它可以让你无需全局安装工具的情况下来使用这些工具，比如如果你的环境中并没有全局安装`create-react-app`，你也可以不用安装它，直接使用`npx`即可

<image src="https://cdn.rawgit.com/facebook/create-react-app/27b42ac/screencast.svg" width="500px" />

安装完成之后直接：

```bash
npm start
# or
yarn start
```

我们再来说一下如果创建一个`Typescript`应用，在使用`create-react-app`时，它是支持带参数的，像下面这样：

```bash
npx create-react-app my-app --typescript
# or
yarn create reatc-app my-app --typescript
```

安装完成后，我们还需要安装一些其他的包：

```bash
npm install --save typescript @types/node @types/react @types/react-dom @types/jest
# or
yarn add typescript @types/node @types/react @types/react-dom @types/jest
```

接下来，将`js`结尾的文件改成`tsx`，重启应用即可。

### JSX

`JSX`是一个`JavaScript`语法扩展，看上去就像是一个包含着HTML标签的字符串，但其实它不是，因为它具有`JavaScript`的所有功能

```javascript
const element = <h1>Hello, World!</h1>;
```

`React`认为渲染逻辑和UI逻辑存在耦合关系，所以，它并没有分离标记与逻辑，它们都存在于组件（`Component`）之中，从而实现关注点分离。

`React`并不强制开发者使用`JSX`，但也强烈推荐（这不是废话吗?）

#### 在JSX中嵌入表达式

在`JSX`中，你可以在一对大括号中放入任何有效的`JavaScript`表达式，甚至是函数

```javascript
// 放入一个定义好的变量
const name = 'Kaindy Liu';
const element = <h1>Hello {name}</h1>;

ReactDOM.render(
  element,
  document.getElementById('root')
)
```

```javascript
// 放入定义的函数
function formatName(user) {
	return user.firstName + ' ' + user.lastName;
}

const user = {
	firstName: 'Kaindy',
	lastName: 'Liu'
}

cosnt element = (
	<h1>hello, {formatName(user)}</h1>
);

ReactDOM.render(
	element,
	document.getElementById('root')
)
```

#### JSX本身也是一个表达式

`JSX`在编译后会被转为普通的`JavaScript`函数调用，所以你可以：

- 在`if`和`for`循环的代码中使用`JSX`
- 将`JSX`赋值给变量
- 把`JSX`当做参数传入
- 从函数中返回`JSX`

```javascript
function getGreeting(user) {
	if (user) {
		return <h1>Hello, {formatName(user)}</h1>
	}
	return <h1>Hello, Stranger.</h1>
}
```

#### 特定属性

在`JSX`中我们可以通过引号来为属性指定字符串字面量，或者使用大括号包含一段`JavaScript`表达式

```javascript
const element = <div tabIndex="0"></div>;
const element2 = <img src={user.avatarUrl} />
```

#### 包含子元素

`JSX`中只能包含一个根元素，可以在其中包含多个子元素

```javascript
const element = (
	<div>
		<h1>Hello!</h1>
		<h2>Good to see you!</h2>
	</div>
)
```

**注意**,在`JSX`中使用小驼峰（`cameCase`）命名属性，`class`应该写成`className`，`tabindex`写成`tabIndex`

#### 防止注入攻击

`React`在渲染所有输入内容之前，默认会进行转义，确保不会有非法的攻击脚本存在。

#### 表示为对象

`Babel`会把`JSX`转译成名为`React.createElement()`的函数调用，下面两段代码完全等效：

```javascript
// JSX
const element = (
	<h1 className="greeting">Hello, World!</h1>
)

// 转译之后
const element = React.createElement(
'h1',
{className: 'greeting'},
'Hello, World!'
)
```

### 元素渲染

元素是构成`React`应用的最小单元，而它也组成了组件，元素与组件是不同的概念。`React`中的元素与`DOM`不同，它就是普通的`JavaScript`对象

#### 将元素渲染为DOM

我们使用`ReactDOM.render()`方法将`React`元素渲染为`DOM`

```javascript
const element = <h1>Hello, world</h1>;
ReactDOM.render(element, document.getElementById('root'));
```

#### 更新元素

在`React`中，元素本质上是一个**不可变对象**，想要更新它的唯一方式，就是创建一个新的元素，并传入`ReactDOM.render()`

```javascript
function tick() {
	const element = (
		<div>
			<h1>Hello, world!</h1>
			<h2>It is {new Date().toLocaleTimeString()}.</h2>
		</div>
	);
	ReactDOM.render(element, document.getElementById('root'));
}

// 每一秒调用一次函数tick,相当于每一秒调用一次ReactDOM.render()
setInterval(tick, 1000);
```

#### 只更新需要更新的部分

在`ReactDOM`进行渲染的时候，`React`会比较`DOM`的状态，并只会更新变动的部分

### 组件 & Props

将UI拆分出来成为独立的可复用的代码片段，并且它有自己的逻辑，这就是组件，也可以把它理解为一个`JavaScript`函数，它接受任意的入参（`Props`）

#### 函数组件和`Class`组件

我们可以使用普通的`JavaScript`函数编写组件

```javascript
function Welcome(props) {
	return <h1>Helli, {props.name}</h1>;
}
```

上面的函数组件接受一个`props`参数对象并返回一个`React`元素，这类组件被称为**函数组件**，本质上它就是一个`JavaScript`函数

同时我们也可以使用`Class`来定义组件

```javascript
class Welcome extends React.Component {
	render() {
		return (
			<h1>Hello, {this.props.name}</h1>;
		)
	}
}
```

上面的`Class`组件和函数组件在`React`中是等效的。

#### 渲染组件

在`React`中，组件是可以自定义的，比如下面这个：

```javascript
function Welcome(props) {
	return <h1>Hello, {props.name}</h1>
}
```

`JSX`中接受了一个`props.name`的属性，`React`会将这些属性转换为单个对象传递给组件，这些对象我们称之为`props`

```javascript
<Welcome name="Kaindy" />
```

**注意**：默认的，我们都会将所有类型的组件定义都使用大写字母开头（大驼峰）

#### 组合

组件可以在其中引入其他组件，比如我们可以在`App`组件中多次引用`Welcome`组件

```javascript
function Welcome(props) {
	return <h1>Hello, {props.name}</h1>
}

function App() {
	return (
		<div>
			<Welcome name="Kaindy1" />
			<Welcome name="Kaindy2" />
			<Welcome name="Kaindy3" />
		</div>
	)
}

ReactDOM.render(
	<App />,
	document.getElementById('root')
)
```

#### Props只读性

无论是函数组件或`Class`组件，都不能修改传入的`Props`。

在函数式编程中，有一种函数叫"纯函数"，它不会修改入参，且多次输入相同的参数返回的结果都是相同的。

```javascript
// 纯函数
function sum(a, b) {
	return a + b;
}
```

在`React`中严格规定：**所有的`React`组件都应像纯函数一样保护它们的`Props`不被修改**

### State & 生命周期

`State`存在于组件内部，与`Props`类似，但它是私有的，并且完全受控于当前组件。

函数组件不存在`State`，所以必须将函数组件转换成`Class`组件

```javascript
class Clock extends React.Component {
	render() {
		return (
			<div>
				<h1>Hello, world!</h1>
				<h2>It is {this.props.date.toLocaleTimeString()}</h2>
			</div>
		)
	}
}
```

#### 添加局部State

现在，我们需要添加`State`到上面定义的`Class`组件中，这里，需要使用`Constructor`生命周期钩子，来初始化`State`

```javascript
class Clock extends React.Component {
	constructor(props) {
		super(props);
		this.state = {data: new Date()};
	}
	render() {
		return (
			<div>
				<h1>Hello, world!</h1>
				<h2>It is {this.state.data.toLocaleTimeString()}</h2>
			</div>
		)
	}
}
```

#### 添加生命周期方法

我们可以为`Class`组件声明一些特殊的方法，当组件挂载、更新或销毁时，这些方法会被自动调用，我们称之为**声明周期方法**

```javascript
class Clock extends React.Component {
	constructor(props) {
		super(props);
		this.state = {date: new Date()}
	}

	// 组件挂载完成后执行的生命周期方法
	componentDidMount() {

	}

	// 组件被卸载前执行的生命周期方法
	componentWillUnMount() {

	}

	render() {
		return (
			<div>
				<h1>Hello, world!</h1>
				<h2>It is {this.state.data.toLocaleTimeString()}</h2>
			</div>
		)
	}
}
```

我们可以编写一个修改当前`State`中的`date`值的方法，然后在生命周期方法中循环调用，并在组件即将被卸载之前清除掉它

```javascript
class Clock extends React.Component {
	constructor(props) {
		super(props);
		this.state = {date: new Date()}
	}

	componentDidMount() {
		this.timeID = setInterval(
			() => this.tick(),
			1000
		)
	}

	componentWillUnMount() {
		clearInterval(this.timeID);
	}

	tick() {
		this.setState({
			date: new Date()
		})
	}

	render() {
		return (
			<div>
				<h1>Hello, world!</h1>
				<h2>It is {this.state.data.toLocaleTimeString()}</h2>
			</div>
		)
	}
}
```

#### 正确使用State

- 不要直接修改`State`

  ```javascript
  // 错误的
  this.state.someState = 'Hello';

  // 正确使用
  this.setState({someState: 'Hello'})
  ```

  构造函数(`constructor`)是唯一一个可以给`this.state`赋值的地方

- `State`的更新可能是异步的

  `React`为了性能会将多个`this.setState()`调用合并成一个，为了实现它，`this.props`和`this.state`就可能会是异步更新，所以我们不能依赖它们的值来更新下一个状态，为此我们需要给`this.setState()`传入一个函数方法，而不是一个对象

  ```javascript
  // 传入的方法接收两个参数，prevState是更新前的state，nextProps是新传入的Props
  this.setState((prevState, nextProps) => {
	  return {
		  counter: prevState.counter + nextProps.increment
	  }
  });
  ```

- `State`的更新会被合并

  当我们的`State`中包含多个状态变量定义，我们更新了其中一个，其他的定义会被合并下来，也就是这个过程是一个**浅合并**

  ```javascript
  constructor(props) {
      super(props);
	  this.state = {
	      posts: [],
		  comments: []
	  }
  }

  componentDidMount() {
      fetchPosts().then(response => {
	      this.setState({
		      posts: response.posts
		  })
	  })
  }
  ```

#### 数据是向下单向流动的

在`React`中，数据总是自顶向下流动，一个组件，无论它是父组件还是子组件，都无法得知其他组件的内部状态，内部状态（`State`）只会存在于组件内部，并为组件内部逻辑服务，但组件可以将它的`State`作为`Props`传递给它的子组件

### 事件处理

`React`中事件处理与`DOM`中的很相似，但在语法上有一些区别：

- `React`事件的命名采用小驼峰(`camelCase`)
- `JSX`中需要传入一个函数，而不是一个字符串

  ```javascript
  <button onClick={activeLasers}></button>
  ```

- 需要显式的调用`e.preventDefault()`来处理浏览器的默认事件
- 函数方法需要绑定当前作用域上下文（`this`）

  ```javascript
  class Toggle extends React.Component {
	  constructor(props) {
		  super(props);
		  this.state = {}
		  // 绑定this
		  this.handleClick = this.handleClick.bind(this)
	  }
	  
	  handleClick() {
		  this.setState(prevState => {
			  // ...
		  })
	  }
	  
	  render() {
		  return (
			<button onClick={this.handleClick}></button>
		  )
	  }
  }
  ```

- 同样的我们也可以使用实验性语法：`public class fields`，来避免使用`bind`

  ```javascript
  class LogginButton extends React.Component {
	  // 下面的语法是实验性的
	  handleClick = () => {
		  console.log('this', this)
	  }

	  render() {
		  return (
		      <button onClick={this.handleClick}>ClickMe</button>
		  )
	  }
  }
  ```

  当然我们也可以直接在`JSX`的回调中使用箭头函数，但这种做法不被提倡，因为可能会造成额外的渲染开销，推荐上面的方式

  ```javascript
  class LogginButton extends React.Component {
	  handleClick() {
		  // ...
	  }
	  render() {
		  return (
			  {/* 传入匿名函数，每次render会都会创建函数，造成额外的性能开销 */}
		      <button onClick={() => this.handleClick(e)}>ClickMe</button>
		  )
	  }
  }
  ```

#### 传递参数

通常为事件处理函数传递额外的参数可以参照下面的写法：

```javascript
<button onClick={(e} => this.delete(id, e)}>Delete Row</button>
<button onClick={this.delete(this, id)}>Delete Row</button>
```

需要注意的是，如果使用箭头函数，事件对象`e`必须显式的进行传递，而如果使用`bind`,它会被隐式传递

### 条件渲染

`React`中的条件渲染与`JavaScript`中的一样，我们可以使用`if`或条件运算符去创建元素来表现当前的状态，然后`React`会根据这个状态来更新UI

```javascript
function Greeting(props) {
	const isLoginedIn = props.isLoginedIn;
	if (isLoginedIn) {
		return <UserGreeting />;
	} else {
		return <GuestGreeting />;
	}
}
```

#### 元素变量

我们也可以将元素存储在变量中，在`render`中使用`if`条件来输出

```javascript
render() {
	let button;
	if (isLoggedIn) {
		button = <LogoutButton onClick={this.handleLogoutClick} />
	} else {
		button = <LoginButton onClick={this.handleLoginClick} />
	}

	return (
		<div>{button}</div>
	)
}
```

#### 与运算符 &&

有时候我们需要更加简洁的方式来进行判断，比如使用与运算符`&&`

```javascript
function MailBox(props) {
	const unreadMessages = props.unreadMessages;
	return (
		<div>
			{unreadMessages.length > 0 &&
				<h2>You have {unreadMessages.length} unread messages</h2>
			}
		</div>
	)
}
```

#### 三目运算符

我们也可以使用三目运算符来实现条件渲染

```javascript
render() {
	const isLoggedIn = this.state.isLoggedIn;
	return (
		<div>
			The user is <b>{isLoggedIn ? 'currently' : 'not'} logged in.</b>
		</div>
	)
}
```

#### 阻止组件渲染

有时候我们需要隐藏组件，这时候我们只需要让`render`方法直接返回`null`即可。

### 列表 & Key

在`React`中，我们使用`map`函数生成多个相同的列表元素

```javascript
const numbers = [1, 2, 3, 4, 5];
const listItems = numbers.map(number =>
	<li>{number}</li>
)

ReactDOM.render(
	<ul>{listItems}</ul>,
	document.getElementById('root')
)
```

#### 基础列表组件

我们可以把上面的例子重构成一个渲染了多个元素的列表组件

```javascript
function NumberList(props) {
	cosnt numbers = props.numbers;
	const listItems = numbers.map(number =>
		<li>{number}</li>
	);
	return (
		<ul>{listItems}</ul>
	)
}

const numbers = [1, 2, 3, 4, 5];
ReactDOM.render(
	<NumberList numbers={numbers} />,
	document.getElementById('root')
)
```

#### Key

上面的代码，如果运行的话会在控制台打印出一段警告，意思就是当我们创建一个元素时，应该为它设置一个特殊的`key`

```javascript
const numbers = [1, 2, 3, 4, 5];
const listItems = numbers.map(number =>
	<li key={number.toString()}>{number}</li>
)
```

`key`是用来标识当前元素的，相当于给元素一个唯一的可辨识的字符串，这样当修改或删除元素时，有利于`React`进行性能上的优化。一般地，我们会将数据中的`id`值作为`key`，如果确实没有，也可以使用索引值`index`

```javascript
const todoImtes = todos.map((todo, index) => {
	<li key={index}>{todo.text}</li>
})
```

但这种使用索引`index`作为`key`的做法并不推荐，因为列表顺序可能会被改变，导致性能受损。所以，这里建议一定要为数据添加一列`id`字段用于辨识列表元素

#### 设置Key的正确方式

`key`属性应该设置在`map`方法中的元素中

```javascript
function ListItem(props) {
	// 这里不能设置key
	return <li>{props.value}</li>
}

function NumberList(props) {
	const numbers = props.numbers;
	const listItems = numbers.map(number =>
		// 这里才是指定key的地方
		<ListItem key={number.toString()} value={number} />
	)
	return (
		<ul>{listItems}</ul>
	)
}
```

#### key在兄弟节点之间必须是唯一的

数组元素中使用的`key`在其兄弟节点之间应该是独一无二的，而不需要在全局也是唯一的。

#### 在JSX中使用map

在`JSX`中，我们也可以使用`map`

```javascript
function NumberList(props) {
	const numbers = props.numbers;
	return (
		<ul>
			{
				numbers.map(number =>
					<ListItems key = {number.toString()} value={number} />
				)
			}
		</ul>
	)
}
```

### 表单

#### 受控组件

表单元素，如：`<input>`、`<textarea>`和`<select>`，通常自己维护`state`，并根据用户输入进行更新，在`React`中，可变状态（`mutable state`）通常保存在组件的`state`属性中，且只能使用`setState()`进行更新。

这种被`React`控制的表单输入元素，就叫做**受控组件**

```javascript
class NameForm extends React.Component{
	constructor(props) {
		super(props);
		this.state = {
			value: ''
		}
	}

	handleChange(event) {
		this.setState({
			value: event.targe.value
		})
	}

	render() {
		return (
			<form>
				<label>名字：
					<input value={this.state.value} onChange={this.handleChange.bind(this)} />
				</label>
			</form>
		)
	}
}
```

#### textarea标签

在`React`中，`textarea`使用`value`来绑定值，这与`input`很相似

```javascript
class TextareaForm extends React.Component {
	constructor(props) {
		super(props);
		this.state = {
			value: '请撰写一篇关于你喜欢的 DOM 元素的文章'
		}
	}
	
	hanleChange(event) {
		this.setState({
			value: event.target.value
		})
	}
	
	render() {
		return (
			<form>
				<label>文章：
					<teaxtarea value={this.state.value} onChange={this.handleChange.bind(this)} />
				</label>
			</form>
		)
	}
}
```

#### select标签

在`React`中，我们在`select`根标签上使用`value`属性，来绑定当前选定的值

```javascript
class FlavorForm extends React.Component {
	constructor(props) {
		super(props);
		this.state = {
			value: 'coconut'
		}
	}
	
	handleChange(event) {
		this.setState({
			value: event.target.value
		})
	}
	
	render() {
		return (
			<form>
				<label>选择你喜欢的风味：
					<select value={this.state.value} onChange={this.handleChange.bind(this)}>
						<option value="grapefruit">葡萄柚</option>
						<option value="lime">酸橙</option>
						<option value="coconut">椰子</option>
						<option value="mango">芒果</option>
					</select>
				</label>
			</form>
		)
	}
}
```

如果上面的`select`需要选中多个值，可以给`value`值绑定一个数组

```javascript
<select multiple={true} value={['B', 'C']} />
```

#### 文件 input 标签

在`React`中，可以使用`<input type="file" />`实现文件上传，这跟在`HTML`中是相似的。

因为文件`input`的`value`是只读的，所以它是`React`中的一个**非受控组件**

#### 处理多个输入

如果需要处理多个`input`元素的输入时，我们可以给每个元素添加`name`属性，然后让处理函数根据`event.target.name`来执行操作

```javascript
class Reservation extends React.Component {
	constructor(props) {
		super(props);
		this.state = {
			isGoing: true,
			numberOfGuests: 2
		}
	}

	handleInputChange(event) {
		const target = event.target;
		const value = target.type === 'checkbox' ? target.checked : target.value;
		const name = target.name;

		this.setState({
			[name]: value
		})
	}

	render() {
		return (
			<form>
				<label>参与：
					<input
						name="isGoing"
						type="checkbox"
						checked={this.state.isGoing}
						onChange={this.handleInputChange.bind(this)} />
				</label>
				<label>来宾人数：
					<input
						name="numberOfGuests"
						type="number"
						value={this.state.numberOfGuests}
						onChange={this.handleChange.bind(this)} />
				</label>
			</form>
		)
	}
}
```

### 状态提升

在`React`中，将多个组件中需要共享的`state`向上移动到它们的最近的共同父组件中，就可以实现共享`state`，这就是`React`中的状态提升

在 React 应用中，任何可变数据应当只有一个相对应的唯一“数据源”。通常，state 都是首先添加到需要渲染数据的组件中去。然后，如果其他组件也需要这个 state，那么你可以将它提升至这些组件的最近共同父组件中。你应当依靠自上而下的数据流，而不是尝试在不同组件间同步 state。

### 组合 & 继承

在`React`中，推荐使用组合而非继承来实现组件间的代码复用。

#### 包含关系

有时候我们无法预知某个组件中它们的子组件的具体内容，这时我们可以使用一个特殊的`children props`来将子组件传递到渲染结果中

```javascript
function FancyBorder(props) {
	return (
		<div className={'FancyBorder FancyBorder-' + props.color}>
			{props.children}
		</div>
	)
}
```

## React高级指引

### 无障碍

网络无障碍辅助功能（Accessibility，也被称为 a11y，因为以 A 开头，以 Y 结尾，中间一共 11 个字母）是一种可以帮助所有人获得服务的设计和创造。

#### 语义化的HTML

语义化的`HTML`是无障碍辅助功能网络应用的基础，我们可以使用`React Fragments`来结合各种组件

```javascript
import React, { Fragment } from 'react';

function ListItem({ item }) {
	return (
		<Fragment>
			<dt>{item.term}</dt>
			<dd>{item.description}</dd>
		</Fragment>
	)
}

function Glossary(props) {
	return (
		<dl>
			{
				props.items.map(item => (
					<ListItem item={item} key={item.id} />
				))
			}
		</dl>
	)
}
```

我们也可以在不需要向`fragment`传入任何`props`时使用短语法

```javascript
function ListItem({ item }) {
	return (
		<>
			<dt>{item.term}</dt>
			<dd>{item.description}</dd>
		</>
	)
}
```

#### 无障碍表单

在`W3C`标准中所有的`HTML`表单控制都可以直接在`React`中使用，需要注意的是，`for`在`JSX`中应该被写作`htmlFor`

```html
<label htmlFor="namedInput">Name:</label>
<input id="namedInput" type="text" name="name" />
```

#### 控制焦点

在`React`中，我们需要以编程的方式让键盘聚焦到正确的地方，为此我们可以在组件的`JSX`中创建一个元素的`Ref`

```javascript
class CustomTextInput extends React.Component {
	constructor(props) {
		super(props);
		// 创建一个ref
		this.textInput = React.createRef();
	}

	render() {
		// 在元素上绑定这个ref
		return (
			<input type="text" ref={this.textInput} />
		)
	}
}
```

接着我们就可以在需要的时候把焦点设置到这个元素上

```javascript
focus() {
	this.textInput.current.focus();
}
```

有时候父组件需要把焦点设置在其子组件的一个元素上，我们可以通过`props`传递这个`ref`给子组件

```javascript
function ChildCompnent(props) {
	return (
		<div>
			<input ref={props.inputRef} />
		</div>
	)
}

class ParentComponent extends React.Component {
	constructor(props) {
		super(props);
		this.inputElement = React.createRef();
	}

	render() {
		return (
			<ChildComponent inputRef={this.inputElement} />
		)
	}
}

// 接下来就在需要的时候设置焦点
this.inputElement.current.focus();
```

当使用`HOC`来扩展组件时，我们建议使用`React`的`forwardRef`函数来向被包裹的组件转发`ref`

#### 鼠标和指针事件

### 代码分割

应用在发布之前需要将代码进行打包，为了避免出现过大体积的包，我们需要对过大的包进行单独处理，从而能够创建多个包并在运行时动态加载。

#### import

在代码中使用代码分割的最佳实践是通过使用动态的`import`语法

```javascript
// 使用之前
import { add } from './math';
console.log(add(1, 2));

// 编译之后
import('./math').then(math => {
	console.log(math.add(1, 2));
})
```

如果你是使用`create-react-app`脚手架创建的应用，这个功能可以立即使用而无需配置。

#### React.lazy

> `Ract.lazy`和`Suspense`还不支持服务端渲染，如果需要，可以参考 [Loadable Components](https://github.com/smooth-code/loadable-components "Loadable Components")

`React.lazy`函数用来处理动态引入的组件

```javascript
const otherComponent = React.lazy(() => import('./OtherComponent'));
```

`React.lazy`接收一个函数，这个函数需要动态调用`import()`，它必须返回一个`Promise`，该`Promise`需要`resolve`一个`default export`的`React`组件

接着，我们需要在`Suspense`组件中渲染`lazy`组件，这样，在某些网络延迟的场景中，我们就可以让用户看到一些类似`Loading`加载器的效果，从而提升体验。

```javascript
const OtherComponent = React.lazy(() => import('./OtherComponent'));

function MyComponent() {
	return (
		<div>
			<Suspense fallback={<div>Loading...</div>}>
				<OtherComponent />
			</Suspense>
		</div>
	)
}
```

上面代码中的`fallback`属性接受一个任何在加载过程中你想要展示的`React`元素，`Suspense`也可以包含多个懒加载的组件

```javascript
const OtherComponent = React.lazy(() => import('./OtherComponent'));
const AnotherComponent = React.lazy(() => import('./AnotherComponent'));

function MyComponent {
	return (
		<div>
			<Suspense fallback={<div>Loading...</div>}>
				<section>
					<OtherComponent />
					<AnotherComponent />
				</section>
			</Suspense>
		</div>
	)
}
```

参考文章：[ 延迟加载 React Components](https://juejin.im/post/5c60e1d2f265da2dd16843f6 " 延迟加载 React Components")

#### 异常捕获边界(Error Boundaries)

如果模块加载失败，那么它会触发一个错误，我们可以通过异常捕获边界来处理这种情况。

```javascript
import ErrorBoundary from './ErrorBoundary';
const OtherComponent = React.lazy(() => import('./OtherComponent'));
const AnotherComponent = React.lazy(() => import('./AnotherComponent'));

const MyComponent = () => (
	<div>
		<ErrorBoundary>
			<Suspense fallback={<div>Loading...</div>}>
				<section>
					<OtherComponent />
					<AnotherComponent />
				</section>
			</Suspense>
		</ErrorBoundary>
	</div>
)
```

异常边界将在下面的章节中介绍

#### 基于路由的代码分割

一个好的代码分割的实践是通过路由进行

```javascript
import { BrowserRouter as Router, Route, Switch } from 'react-router-dom';
import React, { Suspense, lazy } from 'react';

const Home = lazy(() => import('./routes/Home'));
const About = lazy(() =>import('./routes/About'));

const App = () => (
	<Router>
		<Suspense fallback={<div>Loading...</div>}>
			<Switch>
				<Route exact path='/' component={Home} />
				<Route path='/about' component={About} />
			</Switch>
		</Suspense>
	</Router>
)
```

### Context

`Context`提供了一种能在组件间传递数据而无需依靠逐层添加`props`的方法

在一个典型的`React`应用中，通常数据是通过`props`自上而下进行传递的，但某些数据需要全局共享，也就是可能大部分的组件都会使用到它，`Context`提供一种在组件间共享此类数据的方式，而不必显式的通过组件数逐层传递`props`

**注意**，此方法在实际应用中很少使用，一般都会使用`Redux`或`Mobx`来共享这些数据，在`Hooks`中会介绍另外一种。

#### 使用Context

在使用`Context`之前，我们需要为需要共享的数据创建`Context`，然后使用`Provider`包含子组件，最后就可以在所有子组件中直接调用数据

```javascript
// 创建Context
const ThemeContext = React.createContext('light');

// 父组件
class App extends React.Component {
	render() {
		// 使用Provider
		return (
			<ThemeContext.Provider value="dark">
				<Toolbar />
			</ThemeContext.Provider>
		)
	}
}

// 直接子组件无需使用props传递数据
class Toolbar extends React.Component {
	constructor(props) {
		super(props);
		this.state = {}
	}

	render() {
		return (
			<div>
				<ThemedButton />
			</div>
		)
	}
}

// 在子孙组件中调用
class ThemedButton extends React.Component {
	static contextType = ThemeContext;
	render() {
		return <Button theme={this.context} />
	}
}
```

#### 使用Context之前的考虑

`Context`并不适合所有场景，如果只是想避免某些数据逐层传递，可以将使用这些数据的组件传递下去。

### 错误边界（Error Boundaries）

`React` 16版本引入了一个新的概念：错误边界，它是一种`React`组件，可以捕获并打印发生在其子组件树任何位置的`JavaScript`错误，并且会渲染出备用UI。

**注意**，它无法获取以下场景中的错误：

- 事件处理
- 异步代码
- 服务端渲染
- 自身抛出的错误

如果一个`class`组件中定义了`static getDerivedStateFromError()` 或 `componentDidCatch()`这两个生命周期方法中的一个或两个，那么它就变成了一个错误边界（组件），如果有错误被抛出，可以使用`static getDerivedStateFromError()`渲染备用UI，使用`componentDidCatch()`打印错误信息

```javascript
class ErrorBoundary extends React.Component {
	constructor(props) {
		super(props);
		this.state = { hasError: false }
	}

	static getDerivedStateFromError(error) {
		// 更新state使得下一次渲染可以展示降级后的UI
		return { hasError: true }
	}

	componentDidCatch(error, errorInfo) {
		// 这里可以将错误日志上报给服务器或直接打印到控制台
		logErrorToMyService(error, errorInfo);
		console.log(error, errorInfo);
	}

	render() {
		if (this.state.hasError) {
			// 展示降级后的UI
			return <h1>Something went wrong.</h1>
		}
		return this.props.chidlren;
	}
}
```

接下来，它就可以作为一个组件去使用了

```javascript
<ErrorBoundary>
	<MyOtherComponent />
</ErrorBoundary>
```

错误边界只能针对`React`组件，只有`class`组件才可以成为错误边界组件，我们只需要声明一次，就可以在全局去使用它

**注意**，错误边界只能捕获其子组件的错误。

#### 未捕获错误

从`React`16开始，任何未被错误边界捕获的错误将会导致整个`React`组件树被卸载

#### 组件栈追踪

在开发环境下，`React`16会把渲染期间的错误打印到控制台，除了错误信息和`JavaScript`栈外，它还提供了组件栈追踪，可以准确的查看发生在组件树内部的错误信息

![](https://zh-hans.reactjs.org/static/error-boundaries-stack-trace-f1276837b03821b43358d44c14072945-acf85.png)

我们可可以在组件栈追踪里查看文件名和行号，这个功能在`create-react-app`中默认开启

![](https://zh-hans.reactjs.org/static/error-boundaries-stack-trace-line-numbers-45611d4fdbd152829b28ae2348d6dcba-acf85.png)

#### 事件处理错误捕获

错误边界无法捕获事件处理器内部的错误，这时我们仍然使用`JavaScript`中的`try...catch`来处理

```javascript
class MyComponent extends React.Component {
	constructor(props) {
		super(props);
		this.state = { error: null };
	}

	handleClick() {
		try {
			// 执行某些操作
		} catch (err) {
			this.setState({ error: err })
		}
	}

	render() {
		if (this.state.error) {
			return <h1>Caught an error.</h1>
		}
		return <div onClick={this.handleClick.bind(this)}>ClickMe</div>
	}
}
```

### Refs转发

`Refs`转发是一种将`ref`通过组件传到其子组件的技巧，我们通常不需要它，但对于某些应用场景，比如高阶函数（`HOC`），就可以使用它

#### 转发Refs到DOM组件

`Ref`转发是一个可选特性，其允许某些组件接受`ref`，并将其向下传递给其子组件

```javascript
const FancyButton = React.forwardRef((props, ref) => (
	<button ref={ref} className="FancyButton">
		{props.children}
	</button>
));

const ref = React.createRef();
<FancyButton ref={ref}>Click Me</FancyButton>
```

#### 在高阶组件中转发Refs

一般的我们无需使用`ref`转发特性，但在一个特定的场景，高阶组件中，这个技巧就特别有用。我们可以使用`React.forwardRef`明确的将`refs`转发到内部组件中，`React.forwardRef`接受一个渲染函数，其接收`props`和`ref`两个参数并返回一个`React`节点

```javascript
function logProps(Component) {
	class LogProps extends React.Component {
		componentDidUpdate(prevProps) {
			console.log('prev props', prevProps);
			console.log('next props', this.props);
		}

		render() {
			const { forwardedRef, ...rest } = this.props;
			// 将自定义的prop属性"forwardefRef"定义为ref
			return <Component ref={forwardedRef} {..rest} />;
		}
	}

	return React.forwardRef((propos, ref) => {
		return <LogProps {...props} forwardedRef={ref} />
	})
}
```

### Fragments

在`React`中，一个组件如果想要返回多个子元素，可以使用`Fragments`，它可以将子列表进行分组，而无需向DOM添加额外的节点

```javascript
class Columns extends React.Component {
	render() {
		return (
			<React.Fragment>
				<td>Hello</td>
				<td>world</td>
			</React.Fragment>
		)
	}
}
```

还有一种短语法

```javascript
class Columns extends React.Component {
	render() {
		return (
			<>
				<td>Hello</td>
				<td>world</td>
			</>
		)
	}
}
```

#### 带key的Fragments

使用显式的`React.Fragment`语法声明时可能需要带有`key`，一个使用场景是将一个集合映射到一个`Fragments`数组

```javascript
function Glossary(props) {
	return (
		<dl>
			{props.items.map(item => (
			 	<React.Fragment key={item.id}>
					<dt>{item.term}</dt>
					<dt>{item.description}</dt>
				</React.Fragment>
			 ))}
		</dl>
	)
}
```

### 高阶组件

高阶组件（`HOC`）是`React`中用于复用组件逻辑的一种高级技巧。它接收一个组件为参数，返回一个新的组件

#### 横切关注点问题

什么是横切关注点？ 举个栗子，如果你有多个组件，需要在它们的`props`发生变化时，做进一步的处理，这个操作或行为可能是大多数组件都需要的，那么它就是我们所说的横切关注点。

我们可以写一个函数`withSubscription`，它接收两个参数，一个列表组件`CommentList`，还有一个`DataSource`数据集，然后返回一个接收了修改之后的数据的新组件，且这个函数中的组件参数可以是任意业务组件，从而达到多个组件复用监听数据修改的逻辑

```javascript
const CommentListWithSubscriptionComponent = withSubscription(
	CommentList,
	(DataSource) => DataSource.getComments()
)

const OtherWithSubscriptionComponent = withSubscription(
	OtherComponent,
	(DataSource) => DataSource.getComments()
)
```

函数实现如下：

```javascript
// 函数接收一个组件和数据
function withSubscription(WrapperdComponent, selectData) {
	// 返回另一个组件
	return class extends React.Component {
		constructor(props) {
			super(props);
			this.state = {
				data: selectData(DataSource, props)
			}
		}

		componentDidMount() {
			DataSource.addChangeListener(this.handleChange);
		}

		componentWillUnmount() {
			DataSource.removeChangeListener(this.handleChange);
		}

		handleChange() {
			this.setState({
				data: selectData(DataSource, this.props)
			})
		}

		render() {
			return <WrappedComponent data={this.state.data} {...this.props} />
		}
	}
}
```

**请注意，`HOC`不会修改传入的组件，也不会使用继承来复制其行为，它通过将组件包装在容器组件中来返回新组件，`HOC`是纯函数，没有副作用**

#### 不要修改原始组件，使用组合

`HOC`不应该修改传入的组件，而应该使用组合的方式，通过将组件包装在容器组件中实现功能

```javascript
function logProps(WrappedComponent) {
	return class extends React.Component {
		componentWillReceiveProps(nextProps) {
			console.log('Current props', this.props);
			console.log('Next props', nextProps);
		}

		render() {
			return <WrappedComponent {...this.props} />;
		}
	}
}
```

#### 将不相关的`props`传递给被包裹的组件

`HOC`为组件添加特性，自身不应该大幅改变约定，它应该透传与自身无关的`props`

```javascript
render() {
	// 过滤掉与HOC无关的props，且不要进行透传
	const { extraProp, ...passThroughProps } = this.props;

	// 需要传递的方法
	const injectedProp = someStateOrInstanceMethod;

	return (
		<WrappedComponent
			injectedProp={injectedProp}
			{...passThroughPorps}
		/>;
	)
}
```

#### 注意事项

- 不要在`render`中使用`HOC`
- 务必复制静态方法
- `refs`不会被传递

### 深入JSX

`JSX`其实就是`React.createElement(component, props, ...children)`函数的语法糖

```javascript
<MyButton color="blut" shadowSize={2}>
	Click Me
</MyButton>

// 编译后：
React.createElement(
	MyButton,
	{color: 'blue', shadowSize: 2},
	'Click Me'
)
```

#### React元素类型

大写字母开头的`JSX`标签意味着它们都是`React`组件，并且用户自定义的组件也必须以大写字母开头

## React API

## React 测试