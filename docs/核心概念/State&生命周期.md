---
sidebar_position: 4
---

# State & 生命周期
State 与 props 类似，但是 state 是私有的，并且完全受控于当前组件。

## 向 class 组件中添加局部的 state

1. 

```js
class Clock extends React.Component {
  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
        <h2>It is {this.state.date.toLocaleTimeString()}.</h2>
      </div>
    );
  }
}
```
2. 添加一个 class 构造函数，然后在该函数中为 this.state 赋初值：
```js
class Clock extends React.Component {
  constructor(props) {
    super(props);
    this.state = {date: new Date()};
  }

  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
        <h2>It is {this.state.date.toLocaleTimeString()}.</h2>
      </div>
    );
  }
}
```
通过以下方式将 props 传递到父类的构造函数中：
```js
constructor(props) {
    super(props);
    this.state = {date: new Date()};
  }
```
Class 组件应该始终使用 props 参数来调用父类的构造函数。

代码如下：
```js
class Clock extends React.Component {
  constructor(props) {
    super(props);
    this.state = {date: new Date()};
  }

  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
        <h2>It is {this.state.date.toLocaleTimeString()}.</h2>
      </div>
    );
  }
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<Clock />);
```
[在CodePen上尝试](https://codepen.io/gaearon/pen/KgQpJd?editors=0010)

## 将生命周期方法添加到 Class 中
```js
class Clock extends React.Component {
  constructor(props) {
    super(props);
    this.state = {date: new Date()};
  }

  componentDidMount() {
    this.timerID = setInterval(
      () => this.tick(),
      1000
    );
  }

  componentWillUnmount() {
    clearInterval(this.timerID);
  }

  tick() {
    this.setState({
      date: new Date()
    });
  }

  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
        <h2>It is {this.state.date.toLocaleTimeString()}.</h2>
      </div>
    );
  }
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<Clock />);
```
[codepen](https://codepen.io/gaearon/pen/amqdNr?editors=0010)

## 正确地使用 State
不要直接修改 State
使用 setState():
```js
this.setState({comment: 'Hello'});
```

## State 的更新可能是异步的
出于性能考虑，React 可能会把多个 setState() 调用合并成一个调用。
因为 this.props 和 this.state 可能会异步更新，所以你不要依赖他们的值来更新下一个状态。
这个函数用上一个 state 作为第一个参数，将此次更新被应用时的 props 做为第二个参数：
```js
this.setState((state, props) => ({
  counter: state.counter + props.increment
}));
```

