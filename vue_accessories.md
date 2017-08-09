# Vue 插件

在使用 `vue-cli` 脚手架安装的过程中, `electron-vue` 提供了如下关于 `vue` 的插件可供选择...

* [axios ](https://github.com/mzabriskie/axios)\(web requests\)
* [vue-electron](https://github.com/SimulatedGREG/vue-electron) \(attach electron APIs to Vue object\)
* [vue-router](https://github.com/vuejs/vue-router) \(single page application routes\)
* [vuex](https://github.com/vuejs/vuex) \(flux-inspired application architecture\)

---

### [`axios`](https://github.com/mzabriskie/axios)

> 可用于 `browser` 和 `node.js` 的基于 `Promise` 的 `HTTP Client`

如果你熟悉 `vue-resource`, 那么 `axios` 也一样, 它拥有和 `vue-resource` 基本类似的 `API`. 你可以在 `主进程` 中简单的引入 `axios`, 或者在`渲染进程`中使用 `this.$http / Vue.http`.

### [`vue-electron`](https://github.com/SimulatedGREG/vue-electron)

> 可以在 Vue object 中附着 `electron APIs`, 这样 Vue components 就可以轻松使用 `electron` 了

一个让访问 `electron APIs` 变得简单的 `vue` 插件, 可以直接使用 `this.$electron` 来直接访问, 而不需要 `import electron` 到每一个组件中.

### [`vue-router`](https://github.com/vuejs/vue-router)
> `vue-router` 是 [Vue.js](http://vuejs.org/) 使用的官方路由

### [`vuex`](https://github.com/vuejs/vuex)
> Vuex 是一个 Vue.js 应用 **状态管理模板 + 库**. 它作为应用的所有组件的 `中心存储`, 制定规则来保证 `状态` 只以可预测的方式来改变.
