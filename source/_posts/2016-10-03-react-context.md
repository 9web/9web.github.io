---
layout: post
title: "React Context"
permalink: react-context
date: 2016-10-02 17:26:13
comments: true
description: "react context"
keywords: ""
categories:

tags:

---
通常情况数据在React组件中通过 props 层层传递. React 提供了 Context 特性, 可以实现类似全局变量的效果, 若某组件定义了 Context, 则其所有子组件可以从 context 获取数据. 该特性与 Server 开发中 context 概念类似, 可以理解为组件的上下文. React-redux 中的 Provider 即使用该特性将 store 传递给子组件的.


#### 如何使用

```js
class Button extends React.Component {
    render() {
        // 3. 通过 this.context 调用数据
        return (
            <button style={ {background: this.context.color} }>  
                {this.props.children}
            </button>
        );
    }
}

// 4. 需要定义 contextType 才能使用, 否则只能获取到空 context
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
    // 1. 子组件通过该方法获取context
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
// 2. 父组件需要定义 childContextTypes
MessageList.childContextTypes = {
    color: React.PropTypes.string
};
```

除了在render 方法中, 其他组件生命周期方法也可以引用 `componentWillReceiveProps`, `shouldComponentUpdate`, `componentWillUpdate`, `componentDidUpdate` context 是通过额外参数传递的.

无状态组件也可以使用 context 中的数据

```js
const Button = ({children}, context) =>
  <button style={ {background: context.color} }>
    {children}
  </button>;

Button.contextTypes = {color: React.PropTypes.string};
```

context 更新可以被 props, state 变化触发, 所以通过调用 setState 方法可以更新 context

#### 何时使用
context 类似于全局变量, 使用 context 让 data flow 更混乱, 代码难于理解. context 可以用于: 登录用户, 系统语言, 主题信息等. 使用 context 让组件耦合更深, 不易重用.

[文档地址](https://facebook.github.io/react/docs/context.html)
