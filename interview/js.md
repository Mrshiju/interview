编程： https://mp.weixin.qq.com/s/xVCvg-610j6x8Eh2WzRiIQ

    ： https://mp.weixin.qq.com/s/WFMxayFCpuMC8wpOslmIIA

# js的基本数据类型

undefined null string number boolean

# js的原型

每个对象内部都会有一个protoType，如果我们要查找一个对象的属性的话，首先会在该对象内部寻找，如果没有就去该对象的protoType里面找，这个protoType也会有自己的protoType，如果还是找不到，他就会沿着这个方式一直找下去

# js实现继承的几种方式

构造函数继承： 通过call或者apply改变函数this指向来继承
原型链继承
组合继承：将构造函数继承和原型链继承组合在一起

# js的作用域链

js的作用域就是获取变量值的范围，分为局部变量和全局变量

全局变量：指的是window

局部变量：指的是函数内部的变量【不可以被函数外部访问到】

# 什么是闭包

一个函数内部包裹另一个函数，内部函数可以访问内部函数的变量，变量不会被销毁【容易兆成内存泄漏，使用变量后，销毁即可】【模块化，避免全局污染】

# 如何判断一个对象是否属于某一个类

instanceof

a instanceof person

# bind call apply 的同异

同：都是用来改变函数执行的上下文

  ：第一个参数都需要传this

  ：都可以利用后续参数传参

异：call 返回u一个立即执行的函数，
    apply 返回一个立即执行的函数，只有两个参数，第二个参数为数组
    bind 返回一个被改变上下文的函数，不会立即执行

# 事件代理

通过给父节点绑定事件，向上查找，找到匹配节点从而触发事件，如果找不到则到绑定事件的元素上为止，以达到减少事件注册，减少内存占用

# js的垃圾回收机制

垃圾回收器会在初始的时候给每个变量加上标记，然后去掉环境中的变量以及被环境中变量所应用的变量）—闭包—（ 然后完成之后还存在标记的就是需要回收的变量

# 如何阻止冒泡和浏览器默认事件

冒泡：stopPropagation  IE: cancelBubble【kan shai ba bao】

默认：preventDefault   IE: returnValue

# 函数的节流和防抖

节流：阻止事件重复多次调用，在调用的时候会有一个时间间隔，如果调用事件在这个时间间隔内则不会调用【应用-----scroll】

防抖：阻止事件多次调用，只执行最后一次事件调用的结果【应用---输入查询事件】

# new操作符具体干了什么

创建实例对象，引入this，继承构造函数原型

属性和方法被加入到this的引用对象中

# 图片懒加载和预加载

懒加载：初始时不设置图片的url路径，将图片的url放置父节点上，通过data-src来记录图片的地址，当执行某些事件的时候，将父节点上的url放置在image上的src里

预加载：实现图片预先加载，将图片放置在css背景图里面，不显示在视图中 或者 新建一个image实例，设置src属性实现预加载

# 浅拷贝和深拷贝

浅拷贝: 就对象来说，他只是拷贝的对象的指针，而指针还是指向堆内存的地址

深拷贝：他开辟了一块新的空间，重新增加了一个指针，将指针指向这个新开辟的空间

# 区分数组和对象的方法

isArray

Array.protoType.isPrototypeOf([])

Object.prototype.toString.call([])

# 如何理解promise

Promise是一种异步解决方案，Promise有三种状态，pending（进行中），fulfiled（已完成），rejected（已失败）

Promise接受两个内置参数，resolve，reject，成功和失败两个参数

实例生成以后，可以通过.then来回去成功的回调，通过.catch来获取失败的回调

.all: 将多个Promise实例包裹成一个Promise实例 ， 通过数组的形式传入，当所有的Promise都成功执行以后才会返回resolve结果，否则返回reject结果，如果在单个Prmise里有自己独有的catch方法，则会执行自己的，否则会执行Prmise.all的catch

.race: 和all一样，也是包裹多个实例，但是race是根据返回的时间来执行回调的，如果某个参数执行的快就返回哪个结果

# axios和fetch的区别

fetch： 优： fetch是浏览器底层API方便调用，基于Promise来封装
        缺： 只对网络请求进行报错，对一些错误处理都需要去做封装处理
            fetch默认不会携带cookie，需要添加配置项
            fetch不支持请求暂停怕【不会监听请求进度】

axios： 优：客户端支持放置CSRF攻击【跨站请求伪造】
            有请求拦截
            i可以暂停数据请求，自动转换json数据
        缺： i在IE或者一些老版浏览器不支持

# http的状态码

100： 代表发送的请求时 

200： 正确返回信息

301： 请求网页移动到新的地址

302： 临时重定向

303： 同上，使用GET请求的方式

304： 读取缓存【无更改内容】

400： 服务器无法理解的请求方式

401： 请求未授权

403： 禁止访问

404： 资源不存在

500： 服务找不到

503： 服务端暂时无法处理请求

# 一个页面从出入URL到页面加载完成，这个过程发生了什么

首先通过DNS查找对应IP地址

进行Tcp连接（三次握手）：
    客户端向服务器端发送连接的请求
    服务接收到请求后发送同意连接的请求
    客户端收到服务器的同意连接请求后，在次向服务端发送确认信号

发送http请求
    服务器端接受到http请求后，返回相应的html资源
    浏览器在接受html的过程中开始解析渲染，将html文件构建DOM树，解析css文件构建css规则树，根据Dom树和css规则树构造渲染树，构建完成后开始将其绘制到屏幕上

断开连接（4次挥手）
    客户端向服务端发送一个断开请求
    服务端接受到请求后发送确认请求
    服务端向客户端发送断开通知
    客户端接受到断开通知后发送确认信息，服务端接受到以后断开连接

# 跨域是什么？如何解决

跨域：受同源策略影响，产生的安全模式angruizi

同源策略：协议，域名，端口一样，如果有一项不一样即为跨域

解决方法：

    jsonp：通过动态的创建script标签，设置src为接口地址，拼接动态生成的callback传递到后端，后端接受到callback后将需要的参数放到callback中
    
    cors：需要服务端设置请求头Access【an'kan'sai s】-Control【kang'cuo】-Allow【e'lai】-Origin【ang'rui'zi】
    
    代理：客户端发送请求，本地服务器进行拦截，本地服务器发送请求，跨域服务器返回数据，本地服务器接受到数据，将数据返回到客户端

# http和https的区别

https需要ca证书

http是超文本传输协议，是明文传输，https是ssl加密传输，安全性比较高

http和https的连接状态不一样，端口号也不一样http是80 https是443

# 浏览器的本地存储

sessionStorage 关闭浏览器以后就会销毁

localStorage 持久化的本地缓存，除非主动删除，否则永远不会消失

cookie 持有化存储，可以设置过期时间，但是有限制，存储量太小，每条只有4kb，每次http请求都会将其发送到后端，需要自己封装设置，获取，删除cookie的方法

# 对前端缓存的理解

强缓存：强缓存主要是通过cache-Control【kan s kang cui ao】来控制，一般会设置cache-Control的值为“publci， max-age = xxx”，表示在xxx每秒内访问资源的时候，使用本地资源，不在向服务器发起请求

协商缓存：需要每次向服务器验证缓存的有效性

实践：通过webpack打包，给打包后的文件带上Hash值

webpack ： Hash ： hash： 和整个项目有关系，如何项目中有一个文件发生了改变，则所有文件的hash值都会发生改变，因为打包出来的hash值都是一样的

                ：chunkhash： 根据不同的入口依赖文件进行改变，构建对应的chunk，生成hash
    
                ：contenthash：有文件内容产生的hash值，不同的内容产生的hash都不一样

总结：在做前端缓存的时候，我们尽可能的设置强缓存，通过改变文件的hash值来做版本更新

# 常见的http请求头有哪些

Cache-Control：缓存策略

Content-Type：返回内容的类型

Content-Length：返回内容的字节长度

Host：请求的主机

Data：返回的时间

# cookie的所有属性

name: cookie的名字

value：cookie的属性值

maxAge：cookie的失效时间

path：cookie的路径

# 数组的方法

push：向后添加  ----------- 返回新的长度

pop：向后删除   ------------ 返回删除的值【第一个】

shift：向前删除

unshift：向前添加




