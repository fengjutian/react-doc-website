---
sidebar_position: 1
---

# Hook 简介
Hook 是 React 16.8 的新增特性。它可以让你在**不编写 class 的情况下使用 state 以及其他的 React 特性**。

```jsx
import React, { useState } from 'react';

function Example() {
  // 声明一个新的叫做 “count” 的 state 变量
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```

## 没有破坏性改动

- 完全可选的。 你无需重写任何已有代码就可以在一些组件中尝试 Hook。但是如果你不想，你不必现在就去学习或使用 Hook。
- 100% 向后兼容的。 Hook 不包含任何破坏性改动。
- 现在可用。 Hook 已发布于 v16.8.0。

**没有计划从 React 中移除 class。**

## 动机
### 在组件之间复用状态逻辑很难
React 没有提供将可复用性行为“附加”到组件的途径（例如，把组件连接到 store）。React 需要为共享状态逻辑提供更好的原生途径。  
你可以使用 Hook 从组件中提取状态逻辑，使得这些逻辑可以单独测试并复用。**Hook 使你在无需修改组件结构的情况下复用状态逻辑** 。 这使得在组件间或社区内共享 Hook 变得更便捷。

### 复杂组件变得难以理解
我们经常维护一些组件，组件起初很简单，但是逐渐会被状态逻辑和副作用充斥。每个生命周期常常包含一些不相关的逻辑。
在多数情况下，不可能将组件拆分为更小的粒度，因为状态逻辑无处不在。
为了解决这个问题，**Hook 将组件中相互关联的部分拆分成更小的函数（比如设置订阅或请求数据）**，而并非强制按照生命周期划分。你还可以使用 reducer 来管理组件的内部状态，使其更加可预测。

### 难以理解的 class
除了代码复用和代码管理会遇到困难外，我们还发现 class 是学习 React 的一大屏障。你必须去理解 JavaScript 中 this 的工作方式，这与其他语言存在巨大差异。还不能忘记绑定事件处理器。  
为了解决这些问题，**Hook 使你在非 class 的情况下可以使用更多的 React 特性**。 