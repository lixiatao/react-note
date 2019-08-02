# react相关笔记

### 1.  react组件如何获取子组件的状态

一般情况是组件将某个状态值保存在父组件中，通过props传给子组件，子组件通过调用父组件的方法改变这个状态值

今天要介绍的方法是**回调渲染模式（Render Callback Pattern）**，这种模式中，父组件会接收一个函数作为其子组件，子组件中以props.children进行调用


```
//父组件
render (
    <Children>
        {data => { return <OtherChildren value = {data} />}}//可以将状态传给别的组件
    </Children>
)
```


```
//子组件
render (
    <div>
        {
            this.props.children(this.state.value)
        }
        <button onClick={e=>this.onChange()}>修改状态</button>
    </div>
)
```
此方法将父组件与子组件解耦和，父组件不再需要通过 Props的传递 就可以直接访问子组件的内部状态，这样父组件能够更为方便地控制子组件
