---
sidebar_position: 9
---

# 深入 JSX
实际上，JSX 仅仅只是 `React.createElement(component, props, ...children)` 函数的语法糖。如下 JSX 代码：

```js
<MyButton color="blue" shadowSize={2}>
  Click Me
</MyButton>
```

会编译为：

```js
React.createElement(
  MyButton,
  {color: 'blue', shadowSize: 2},
  'Click Me'
)
```
