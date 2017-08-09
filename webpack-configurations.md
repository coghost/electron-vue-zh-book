# Webpack 配置

`electron-vue` 使用了存储在 `.electron-vue/` 目录中的三个独立的 `webpack config文件`. 除了可选的 `web` 输出, `main` 和 `renderer` 拥有相似的设置. 都使用了 `babel-preset-env` 来指向 `node@7` 特性, 使用 `babili`, 视所有的模块为 `externals`.

### `.electron-vue/webpack.main.config.js`

指向 electron's `main` 进程. 该配置除了一些常用的 `webpack` 业务配置, 基本没有其他内容.

### `.electron-vue/webpack.renderer.config.js`

指向 electron's `renderer` 进程. 该配置会处理你的 `Vue应用`, 它包含了 `vue-loader` 以及很多其他在官方 `vuejs-templates/webpack` 框架中的可用配置.

##### 外部白名单

一件重要的事情是关于这个配置文件, 你可以指定不被 webpack 认为是 `externals` 的白名单. 通常情况下该功能并不需要, 但是对于需要提供 `原生的 *.vue` 的 `Vue UI库`, 需要放置于白名单之中, 这样 `vue-loader` 就可以来编译它们了. 另一个使用情形是使用了 `webpack aliases` 功能, 比如设置 `vue` 来导入完整的 `Compiler + Runtime` 编译. 因此, `vue` 已经被加入了白名单. 

### `.electron-vue/webpack.web.config.js`

定位于编译你的 `renderer进程` 代码为可在浏览器中运行. 这个配置文件基于你确实需要发布 web 应用. ** electron-vue 并不支持超出其提供支持范围的 web 输出.** 而`web输出`的相关问题很有可能会被推迟或者关闭.
