# 渲染进程

> 鉴于 `Electron` 使用了 `Chromium` 来展示 web 页面,所以 `Chromium's` 的多进程架构也同样引入了. Electron 的每一个页面都有一个属于自己的独立进程, 称为 `renderer process: 渲染进程`

> 在标准的浏览器中, web 页面通常都运行于 `沙箱环境` 并且不允许直接访问原生资源. 然后 `Electron 用户` 可以通过在 web 页面中使用 `Node.js APIs` 来实现与底层操作系统进行交互.

** 参考 ** [**Electron Documentation**](http://electron.atom.io/docs/tutorial/quick-start/#renderer-process)

---

## 关于 `vue` 和 `vuex`

### vue 组件

如果你并不熟悉 `Vue组件`, 可以先阅读 [这个文档]((http://vuejs.org/v2/guide/single-file-components.html)). 使用组件, 可以更好的组织我们的大型复杂软件结构. 而每一个组件都可以拥有独立的 `CSS/template/javascript功能` 封装.

组件都存储在 `src/renderer/components`. 当创建一个新的子组件时, 一个常用的组织技巧是放置在以他们的父组件命名的文件夹之中. 这在协调不同的路由时, 会相当有用. `(译注: 当然你完全可以自己命名, 效果一样)`

```
src/renderer/components
├─ ParentComponentA
│  ├─ ChildComponentA.vue
│  └─ ChildComponentB.vue
└─ ParentComponentA.vue
```

### vue 路由

可以查看 [vue-router文档](https://github.com/vuejs/vue-router) 来获取更多关于 `vue-router` 的信息. 简言之, 在开发 `Electron App` 时, 我们鼓励使用 `vue-router` 来创建单页面应用. 难道你真的愿意管理一大堆 `BrowserWindows` 并且在其间来实现通信交换数据信息吗? 显然不是.

在 `src/renderer/router/index.js` 定义的路由如下...

```js
{
    path: '<routePath>',
    name: '<routeName>',
    component: require('@/components/<routeName>View')
}
```

...这里的 `<routePath>`和`<routerName>` 都是变量. 这些路由最终都会附加在 `src/renderer/App.vue` 中使用 `<router-view>`指令定义的组件树上.

##### 注意

当使用 `vue-router` 时, 不要使用 [**HTML5 History Mode**](http://router.vuejs.org/en/essentials/history-mode.html). 这个模式是严格限制在使用 `http` 协议来提供文件服务的, 而 `electron` 的产品只能使用 `file` 协议来提供文件服务. 故默认的 `hash` 模式正好是我们所需要的.

### vuex modules

描述 `vuex` 不是一个轻松的事情, 所以请阅读 [这个文档](http://vuex.vuejs.org/en/intro.html) 来获取更多信息吧. 这里描述了 `vuex` 是解决什么问题, 并且是如何做到的.

electron-vue 利用了 `vuex` 的 `module架构`, 提供了多个 `data stores`, 并存储于 `src/renderer/store/modules` 中.

拥有多个 `data stores` 可以给组织功能带来便利, 但如果需要导入每一个文件却是一件让人烦恼的事情. 不过别害怕, `src/renderer/store/modules/index.js` 会帮我们做这些让人烦的事情! 这个脚本会让 `src/renderer/store/index.js` 可以实现一次导入我们的所有模块. 如果这些不好理解的话, 那么你只需要记住, 你只要简单的复制已有的 `Counter.js` 模块, 修改为新的模块 `NewMdl.js`, 则`NewMdl.js` 模块已经神奇的加载好, 可以使用了.
