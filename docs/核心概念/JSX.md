---
sidebar_position: 1
---

# JSX 简介
设想如下变量声明：
```js
const element = <h1>Hello, world!</h1>;
```
这个有趣的标签语法既不是字符串也不是 HTML。它被称为 `JSX`，是一个 JavaScript 的语法扩展。

## 为什么使用 JSX？
React 认为渲染逻辑本质上与其他 UI 逻辑内在耦合，比如，在 UI 中需要绑定处理事件、在某些时刻状态发生变化时需要通知到 UI，以及需要在 UI 中展示准备好的数据。
React 并没有采用将标记与逻辑分离到不同文件这种人为的分离方式，而是通过将二者共同存放在称之为“组件”的松散耦合单元之中，来实现**[关注点分离](https://en.wikipedia.org/wiki/Separation_of_concerns)**。

## 在 JSX 中嵌入表达式

在下面的例子中，我们声明了一个名为 name 的变量，然后在 JSX 中使用它，并将它包裹在大括号中：

```js
const name = 'Josh Perez';
const element = <h1>Hello, {name}</h1>;
```

在下面的示例中，我们将调用 JavaScript 函数 `formatName(user)` 的结果，并将结果嵌入到 `<h1>` 元素中。
```js
function formatName(user) {
  return user.firstName + ' ' + user.lastName;
}

const user = {
  firstName: 'Harper',
  lastName: 'Perez'
};

const element = (
  <h1>
    Hello, {formatName(user)}!
  </h1>
);
```
## JSX 中指定属性

你可以通过使用引号，来将属性值指定为字符串字面量：

```js
const element = <a href="https://www.reactjs.org"> link </a>;
```
也可以使用大括号，来在属性值中插入一个 JavaScript 表达式：
```js
const element = <img src={user.avatarUrl}></img>;
```
:::tip
警告：

因为 JSX 语法上更接近 JavaScript 而不是 HTML，所以 React DOM 使用 `camelCase`（小驼峰命名）来定义属性的名称，而不使用 HTML 属性名称的命名约定。

例如，JSX 里的 `class` 变成了 className，而 tabindex 则变为 tabIndex。
:::

## JSX 防止注入攻击
你可以安全地在 JSX 当中插入用户输入内容：
```js
const title = response.potentiallyMaliciousInput;
// 直接使用是安全的：
const element = <h1>{title}</h1>;
```
React DOM 在渲染所有输入内容之前，默认会进行转义。它可以确保在你的应用中，永远不会注入那些并非自己明确编写的内容。所有的内容在渲染之前都被转换成了字符串。

## JSX 表示对象
Babel 会把 JSX 转译成一个名为 `React.createElement()` 函数调用。
以下两种示例代码完全等效：
```js
const element = (
  <h1 className="greeting">
    Hello, world!
  </h1>
);
```
```js
const element = React.createElement(
  'h1',
  {className: 'greeting'},
  'Hello, world!'
);
```




