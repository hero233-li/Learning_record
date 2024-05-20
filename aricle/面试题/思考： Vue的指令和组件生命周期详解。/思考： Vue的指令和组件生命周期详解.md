#  Vue的指令和组件生命周期详解。

参考：

[Vue系列之—Vue生命周期详解](https://www.cnblogs.com/jinkai123/p/15889088.html)

[VUE 自定义指令详解](https://zhuanlan.zhihu.com/p/686349064)

vue为了满足相关的开发需要，有许多的指令可以让用户使用，像v-on 和v-bind,，同时为了更好的可扩展性和满足更多的开发需求。vue能够让用户自定义指令。实现图片懒加载、文本复制等功能

自定义指令可使用是vue.directive注册全局指令和directives注册内部指令在自定义指令中，提供五个钩子函数

```JavaScript
Vue.directive('directive-name', {
  bind(el, binding, vnode) {
    // 在元素绑定到 DOM 时执行的代码
  },
  inserted(el, binding, vnode) {
    // 在元素插入到 DOM 中时执行的代码
  },
  update(el, binding, vnode, oldVnode) {
    // 当 VNode 更新时执行的代码
  },
  componentUpdated(el, binding, vnode, oldVnode) {
    // 在组件 VNode 及其子 VNode 全部更新后执行的代码
  },
  unbind(el, binding, vnode) {
    // 在指令与元素解绑时执行的代码
  }
});
```

同时vue自定义指令可以让用户直接接触Dom，进行操作。

在vue中，有8种生命周期，同时在vue中，有keep-alive组件，对组件进行缓存，也有两个生命周期，actived和deactivated

![img](https://saeczhfvuci.feishu.cn/space/api/box/stream/download/asynccode/?code=OWZmZjJiN2MxZWVhMDEwNWFjMjFiMDcxMTlkOTAwYjRfQVc3TmZ4NjA1cGFYWGVqVEtlNUd0SnVTYnJ0dHRoV0FfVG9rZW46RHBlUWJ2ZFpyb08yeUh4NGpuOGNOcUh6bjZkXzE3MTYxOTA4ODU6MTcxNjE5NDQ4NV9WNA)
