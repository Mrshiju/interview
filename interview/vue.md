# 如何理解MVVM模式

MVVM模式主要分为三部分 Model View ViewModle 

Modle： 主要是用来进行数据操作，获取接口请求的数据

View：主要是用来展示视图模板，绑定数据，事件的操作

ViewModle： 主要是用来关联Modle和view层，用来响应View的绑定操作，对这些绑定操作进行监听，当Modle数据发生改变时，视图也会跟着改变

# vue的组件通讯

父子： 通过props来进行传递

子父： 通过$emit自定义事件和v-on来进行传递

跨级：通过EventBus来进行传递：重新实例化vue，在vue上挂载$emit和$on进行信息的发布和订阅

    ：2.4中加入的$attrs和$liteners
    
    : vuex

# computed和watch有啥区别

computed: 是计算属性，他会将计算好的值进行缓存，如何他所依赖的这个值不发生改变的时候，他是不会改变的，如果发生了改变，则他就会从新计算

watch: 主要是进行观察，当观察的这个值发生改变以后，我们可以去做一些事情，没有缓存

# vue是如何进行双向绑定

主要是利用object.defineproperty的数据劫持，为每个属性分配一个订阅者的管理数组dep，然后在编译的时候在该属性的数组中添加订阅者，修改值就则会触发该属性set的方法，在set方法内通知订阅数组dep，订阅者数组循环调用订阅者的Update方法更新视图

3.0 以后主要是通过proxy来实现，【解决了3.0以前修改数组，视图不发生改变的情况【如果使用了数组会被遍历两次，影响性能】】，而proxy可以直接监听的数组的变化

# 如何理解vue的响应式系统

每一个组件都有一个他们自己的watch实例

vue的data上的属性都会被添加set和get属性

当vue初始化的时候，data上的get属性就会被触发，从而获取到data对象上的状态

当data上的属性被改变时会触发set属性，此时vue就会通知所有依赖该值的组件进行更新

# 虚拟DON优略势

优：当状态发生改变时，通过diff找出最小差异，进行批量修改，提高性能
    无需手动操作DOM

缺：无法极致优化


# 虚拟Dom实现原理

虚拟dom是对真实dom的抽象，状态更新时记录更新差异，最后通过对比差异来更新dom

# 既然Vue通过数据劫持可以精准探测数据变化,为什么还需要虚拟DOM进行diff检测差异?

vue 是通过数据劫持来收集修改的依赖，检测到发生改变的组件，然后在组件内部通过虚拟DOm获取到具体差异进行更新】两者想结合【

# vue路由的实现原理

hash：通过在浏览器url中添加‘#’符号，可以通过localtion.hash读取

    ：不会被包含在http请求中，他是用来指导浏览器动作的
    
    ：通过loaction.hash跳转路由-------通过location.href修改地址-----通过hashchange监听状态

history：采用了H5的新特性，h5提供了两个新的方法：pushState，replaceState来控制路由，使用popState事件可以监听到状态的变更

# 如何让vue的css只在当前组件适用

在style 上添加scoped

# 关于vue页面闪速

使用v-cloak设置为dispaly：none

# 关于vue自定义指令【如何定义】

vue.directive 【全局】

directives 【局部】

第一个参数是指令名称，另一个参数是函数-----函数内部有三个钩子函数 bind绑定事件触发， inserted节点插入时报错，update组件内相关更新时调用，unbind指令与元素解绑时调用

# vue的路由导航守卫

全局路由导航：beforeEach --- 前置   afterEach --- 后置

路由独享守卫：beforeEnter

组件内的守卫：beforeRouteEnter

           ：beforeRouteUpdate
    
           ：beforeRouteLeave 

# vue如何创建组件

全局组件：使用Vue.components('组件名'， 组件)

局部组件：引入组件，在components中在注册，然后直接调用

# vue和react的不同

vue是双向数据流，react是单项数据流

vue有指令，计算属性等

创建组件的方式不一样:

        react通过class和函数创建组件
    
        vue通过components实例创建

###	 **面试**

1. 在vue中使用了element ui 如果想自己改变样式，没有生效该如何解决
2. 请求到后台数据，并且改变但是页面没有生效该如何解决。
3. vue运行环境。