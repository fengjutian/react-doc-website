---
sidebar_position: 13
---

# 不使用 ES6

通常我们会用 JavaScript 的 class 关键字来定义 React 组件：

```js
class Greeting extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
```
如果你还未使用过 ES6，你可以使用 create-react-class 模块：

```js
var createReactClass = require('create-react-class');
var Greeting = createReactClass({
  render: function() {
    return <h1>Hello, {this.props.name}</h1>;
  }
});
```

