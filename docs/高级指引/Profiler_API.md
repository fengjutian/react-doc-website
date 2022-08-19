---
sidebar_position: 12
---

# Profiler API
Profiler 测量渲染一个 React 应用多久渲染一次以及渲染一次的“代价”。 它的目的是识别出应用中渲染较慢的部分，或是可以使用类似 memoization 优化的部分，并从相关优化中获益。

:::tip
Profiling 增加了额外的开支，所以它在生产构建中会被禁用。

为了将 profiling 功能加入生产环境中，React 提供了使 profiling 可用的特殊的生产构建环境。 从 fb.me/react-profiling了解更多关于如何使用这个构建环境的信息。
:::