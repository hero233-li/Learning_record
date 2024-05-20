> 我是小桂子，欢迎来到我的个人博客，在这里你可以看到我的所思所想，以及和我进行互动。

🎯 **我的** **OKR**

日更一文

🧑🏻💻 **我的项目**

✅ **我的待办**

🏞 **我的作品**

❓ **FAQ**

#### 📝八股

1. ##### 浏览器如何跨域

1. ##### 协商存储：no-cache 和 no-store 的区别

No-store 是不将数据存储在客户端

No-catch 是将数据存储在客户端，但是每次都需要前往服务端请求资源新鲜度

1. ##### 协商存储里面还有哪些字段

1. ##### 什么是代理服务器

代理服务器就是通过一台代理服务器将，客户端发出的向服务器请求资源的请求代理，由代理服务器进行处理

代理分为正向代理和 反向代理

![img](https://saeczhfvuci.feishu.cn/space/api/box/stream/download/asynccode/?code=ZGFjZDBkNDc2MjkwYWI5ZTZiMDYzM2E3YmJjYmE1M2JfVmFFSkF0c25LSHNXa0lJblhSOVpSNTRNNjJnQzVqQnNfVG9rZW46UHF6N2JrdzQyb1c4M0Z4YU5BVGNWWGtsblBkXzE3MTYxNzE0Mzc6MTcxNjE3NTAzN19WNA)

正向代理是代理客户端向服务器发出的请求，都由代理服务器进行拦截转发处理和缓存，可以让请求方不知道服务器的真实地址，防止恶意攻击，以及可以对部分资源和请求进行缓存，当相同请求时，快速返回。提高性能

反向代理是代理多个客户端和多个服务器之间的交互。

可以实现负载均衡的效果，达到提升性能的目的，以及对客户端隐藏真实地址。

1. ##### webpack打包的时，携带的hash值有利于缓存，不带有hash值，如何缓存

1. ##### 跨域的cookie会被携带上吗

1. ##### redux中间件的原理

1. ##### 轮播图的实现的原理

1. ##### H5 C3新特性

1. ##### CSS3 不兼容的情况有了解吗

1. ##### ES6的我东西知道哪些

1. ##### 排序算法，sort的用法解释一下

1. ##### 前端怎么限制用户截图

1. #####  深拷贝爆栈

1. ##### Object.defineProperty 为什么不能监听到数组下标的变化

1. ##### vue初始化页面有了解它底层的渲染.

1. ##### 面向对象和面向过程的区别

1. ##### keep-live 和 websocket 的区别

1. ##### 说说React中onClick绑定后的工作原理

1. ##### 父组件更新，如何避免子组件更新

1. ##### css 模块化的作用和实现

1. ##### 前端能否实现多线程

1. ##### 如果对null和undefined结果解构会怎么样

1. ##### GPU合成层是什么

即使用opacity或 translate 等3D属性的 设置项时，会将相关图形的绘制从 CPU 转移至 GPU，在 GPU 将图形渲染完成之后，将结果返回给 CPU，能够提升相关的性能

- GPU 可以并行计算，比 CPU 绘图更快，且不消耗 CPU 性能，
- 分层合成，GPU 将图形分成多个图层分开渲染，提高渲染速度，最后将图层合并也是在 GPU 中进行，避免 CPU 操作
- GPU 合成层的图形，当需要重绘时，只会重绘自身，不会影响到其他图形
- 对于 transform 和 opacity 效果，不会触发 重绘和回流

1. ##### 原生JS如何实现数据双向绑定

1. ##### vue2和vue3的区别

[Vue3 是如何通过编译优化提升框架性能的？](https://cloud.tencent.com/developer/article/2224683)

[详解Vue3.0对虚拟Dom的优化](https://juejin.cn/post/7062917822334107656#heading-7)

[面试官：vue3有了解过吗？能说说跟vue2的区别吗？](https://vue3js.cn/interview/vue/vue3_vue2.html#哪些变化)

vue2和vue3有许多的改进，

1. ######  速度更快

   1.   编译优化
      1.    **记录动态元素**

     **Block 更新**

     动态节点的 VNode，会被**按顺序存储 Block 的** **`dynamicChildren`** **中**

   - 存储在 `dynamicChildren`，是为了可以**只对这些元素进行比对**，跳过其他静态元素

   - `dynamicChildren` 只存储在 Block，不需要所有 VNode 都有 `dynamicChildren`，因为**仅仅通过 Block** **`dynamicChildren`** **就能找到其内部中所有的动态元素**

   - 按顺序，即旧 VNode 的 `dynamicChildren` 和 新 VNode 的 `dynamicChildren` 的**元素是一一对应的**，这样的设计就**不需要使用 Diff 算法**，从新旧 VNode 这两个 children 数组中，找到对应（key 相同）的元素

     - 1.    **静态提升**

     -    指在编译器编译的过程中，将一些静态的节点或属性将静态元素的 `createVNode` 提升到渲染函数之外，这样每次更新组件的时候，**就不会重新创建 VNode**，因此每次拿到的 VNode 的引用相同，Vue 渲染器就会直接跳过其渲染

1.  diff算法优化

   1.   **patchFlag，**

     实现静态标记

     静态节点不比较，动态节点做标记， Vue3 在 Vdom 的更新时，**只会关注它有变化的部分**

     在diff算法中，会对比每一个新旧dom树的每一个层级的Dom节点，当发生变化时，会进行标记更新，但是遍历整个Dom树，比较耗费性能，使用pathFlag，根据pathFlag的值，来执行对应的更新操作

     **会根据****`vnode`****的****`patchFlag`****上具有的属性来执行不同的****`patch`****方法**，如果没有`patchFlag`那么就执行`full dif`

   ```JavaScript
   export const enum PatchFlags {
     // 动态文字内容
     TEXT = 1,
     
     // 动态 class
     CLASS = 1 << 1,
   
     // 动态样式
     STYLE = 1 << 2,
   
     // 动态 props
     PROPS = 1 << 3,
   
     // 有动态的key，也就是说props对象的key不是确定的
     FULL_PROPS = 1 << 4,
   
     // 合并事件
     HYDRATE_EVENTS = 1 << 5,
   
     // children 顺序确定的 fragment
     STABLE_FRAGMENT = 1 << 6,
   
     // children中有带有key的节点的fragment
     KEYED_FRAGMENT = 1 << 7,
   
     // 没有key的children的fragment
     UNKEYED_FRAGMENT = 1 << 8,
   
     // 只有非props需要patch的，比如`ref`
     NEED_PATCH = 1 << 9,
   
     // 动态的插槽
     DYNAMIC_SLOTS = 1 << 10,
   
     // SPECIAL FLAGS -------------------------------------------------------------
   
     // 以下是特殊的flag，不会在优化中被用到，是内置的特殊flag
   
     // 表示他是静态节点，他的内容永远不会改变，对于hydrate的过程中，不会需要再对其子节点进行diff
     HOISTED = -1,
   
     // 用来表示一个节点的diff应该结束
     BAIL = -2,
   }
   ```

1.  **记录动态元素**

 动态节点的 VNode，会被**按顺序存储 Block 的** **`dynamicChildren`** **中**

  存储在 `dynamicChildren`，是为了可以**只对这些元素进行比对**，跳过其他静态元素

- 体积减少
  - 使用tree-shirking将无用模块剔除，精简代码
- 更易维护
- 更接近原生
- 更易使用

1. ##### A、B及其正常连接后，B机器突然重启，问此时A处于TCP的什么状态

1. ##### 解释什么是事件代理，以及它在DOM操作中的优势

1. ##### Vue组件间的通信方式有哪些

1. ##### 详细描述从输入URL到页面完全渲染的过程，包括网络请求、HTML解析、DOM树构建、CSSOM树构建、JS执行和渲染树构建。

1. ##### 如何配置Webpack以允许更小的bundle大小?

1. ##### 全局作用域中，用 const 和 let 声明的变量不在 window 上，那到底在哪

在JS代码将要进行执行时，会创建一个执行上下文，在执行上下文中进行执行，而执行上下文的创建分为创建阶段和执行阶段，在创建阶段会进行this绑定，创建词法环境，创建变量环境，在执行阶段是将对应的变量赋值，完成分配

创建阶段中，在创建词法环境时会创建一个环境记录和一个外部环境的引用，外部环境的引用是作用域链的机制生效原因，而在环境记录中又分为三部分，

- 声明式环境记录
  - 声明式环境记录是是存储let、const、class、module、function等等声明的位置。声明式环境记录有两个特殊类型，
    - 函数式环境记录：记录函数
    - 模块式环境记录：记录导出的export模块
- 对象式环境记录
  - 记录with和global的环境记录。每个对象式环境记录都会与一个对象绑定，对象被称为binding object，
- 全局环境记录
  - 是对象式环境记录和声明式环境记录的封装，在全局环境记录中记录的对象式绑定的对象就是全局object binding，在浏览器内，全局的this及window绑定都指向全局对象。全局环境记录的对象式环境记录组件，绑定了所有内置全局属性、全局的函数声明以及全局的var声明。因此对象式环境记录都是在window上，var也是在window上，而声明式环境记录不是简单的对象绑定，因此不可以访问到。
  -  参考：[词法环境](https://github.com/logan70/Blog/issues/1)

1. ##### 前端更新部署后，如何通知用户刷新

[前端更新部署后，如何通知用户刷新](https://saeczhfvuci.feishu.cn/docx/A7qhdIbzFooJijx79Etc7uMynKc)

1. ##### const res=obj[1][2][3]+4，实现一个对象，让结果为 10

[请你实现一下这个 obj 对象,使得最后的输出结果为 10 const res = obj[1\][2][3] + 4](https://saeczhfvuci.feishu.cn/docx/FPMtd93dOoeZdexyjQnc2XQwnXc)
