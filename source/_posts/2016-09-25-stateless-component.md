---
layout: post
title: "Stateless component"
permalink: stateless-component
date: 2016-09-24 21:17:22
comments: true
description: "stateless component"
keywords: ""
categories:

tags:
    "React"
---

在 React 中, 最初的 Component 定义方式为 createClass, 随着 ES6 规范的落地, 后又添加了 ES6 Class 定义方式(该种方法不支持 mixin 以及 autobind). React 组件本质上是一个 JS 方法, 输入数据, 输出UI, 所以 v0.14 引入了一种新的组件定义语法 [Stateless Functions](https://facebook.github.io/react/docs/reusable-components.html#stateless-functions):

```js
function HelloMessage(props) {
  return <div>Hello {props.name}</div>;
}
ReactDOM.render(<HelloMessage name="Sebastian" />, mountNode);
```

或者ES6箭头函数

```js
const HelloMessage = (props) => <div>Hello {props.name}</div>;
ReactDOM.render(<HelloMessage name="Sebastian" />, mountNode);
```

结合参数析构

```js
const HelloMessage = ({name}) => <div>Hello {name}</div>;
ReactDOM.render(<HelloMessage name="Sebastian" />, mountNode);
```

该种组件没有state, 没有 backing instances, 参数为 props, 没有生命周期方法, 是纯方法(pure functions of their props). 但可以定义 .propTypes 跟 .defaultProps

```js
const HelloMessage = (props) => <div>Hello, {props.name}</div>;
HelloMessage.propTypes = {
  name: React.PropTypes.string
}
HelloMessage.defaultProps = {
  name: 'John Doe'
}
ReactDOM.render(<HelloMessage name="Mădălina"/>, mountNode);
```

这种方式定义的组件因为没有 back instances, 所以没法使用 ref. 如果想要查找这种组件的 DOM node, 可以将他们包装进普通组件里(ES6 class component).

在理想情况下大部分组件应该是 stateless component, 官方推荐尽量使用这种方式定义组件.
