# 对setState的理解

在执行setState这个过程的时候他是根据dom流程走的，会将新的state值放入到一个更新队列中，事务transaction【chuan'ran'ke'sheng】会进行下一步的操作，在批量调用的情况下，会对多个setState进行合并

setTimeout中setState会自己触发一个事务，而生命周期的setState已经处于react生命周期的transaction事务i

# react的diff算法怎么完成的

把树形结构按层级分解，只比较同级元素

通过列表结构每一个单元的添加到额key值进行区分同级元素的比较

# react的虚拟DOM实现原理

使用js对象结构表示DOM树，然后用这个树构造一个真正 的dom树，插到文档中，当状态发生改变的时候，重新构造一棵新的对象树，新旧对象树进行对比，找出差异，渲染到视图中

优点：减少dom树的操作，提高性能

# React如何进行性能优化

利用shouldComponent函数，避免无所谓的render

在DOM遍历的时候加上key值

减少对真实DOM的操作

# redux实现流程

页面触发一个行为action，然后Store自动调用reducer，并传入两个参数当前的State和接受到的action，reducer返回新的state，每当state更新之后，就会重新渲染页面

使用`react-redux`进行页面和redux的来连接，通过Provider包裹根节点，页面中通过connect包裹组件并将state，和action通过props传入组件内部，监听仓库的变化，这样就可以响应state

# redux中间件

redux-thunk：是用来解决仓库的异步操作，他返回的是一个函数，函数内部接受一个dispath，我们就可以在函数内部调用异步操作，当异步操作呢完成后，再次触发action【使用applymiddle】

# react高阶组件

高阶组件就是一个函数，它接受一个组件作为参数，并返回一个新的组件

创建高阶组件的两种方法：

        属性代理：通过返回一个class组件，在组件内部进行props操作，或者布局操作等，

        反向继承：返回一个class组件，这个class组件将继承参数组件【】如果想要在组件内部使用生命周期或者一些参数组件拥有的方法时，可以通过super.方法名调用

# react的生命周期

挂载阶段

componentWillMount： 组件即将被装载，Dom渲染到页面之前

render

componentDidMount：组件渲染到页面中，这里可以拿到真正的DOM

更新阶段：

componentWillReceiveProps: 当props发生改变以后触发，接受一个新的props为参数

shouldComponentUpdate：可以控制是否执行render，返回true执行，返回false不执行

componentWillUpdate：当状态发生改变的时候

render

componentDidUpdate： 在组件发生改变以后调用

卸载阶段

componentWillUnmount：卸载阶段

------------------------------------------------

16.4更新的生命周期【更新原因：react推出了Fiber框架，开启了异步render，这就导致在render前的生命周期，可能会被执行多次】

废弃了 componentWillMount componentWillReceiveProps componentWillUpdate

getDerivedStateFromProps 接受两个参数，一个是新的props，一个是新的state，返回值是一个新的state，如果返回null则不更新state【是静态方法 需要在前面加static】

getSnapshotBeforeUpdate 在组件渲染之前，返回一个值，作为componentDidUpdate第三个参数

执行顺序

挂载阶段

getDerivedStateFromProps

render

componentDidMount

更新阶段

getDerivedStateFromProps

shouldComponentUpdate

render

getSnapshotBeforeUpdate

componentDidUpdate

# react16优化有哪些

1. 在html-webpack-plugin中插入loding，在模板中引入即可【htmlwebpackplugin.options.loding.css】

2. 动态使用polyfill【pang'lai'fan'o】，他会根据浏览器的UA头，判断是否支持某些特性，返回一个合适的polyfill

3. 使用splitChunkPlugin拆分模块

4. 使用lazyload进行路由懒加载

5. 使用骨架屏，提升加载体验
