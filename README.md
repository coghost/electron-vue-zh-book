
![](https://simulatedgreg.gitbooks.io/electron-vue/content/images/logo.png)

> 这是一个用来开发 electron+vue 的框架

[![Build Status](https://semaphoreci.com/api/v1/simulatedgreg/electron-vue/branches/master/badge.svg)](https://semaphoreci.com/simulatedgreg/electron-vue)

[![js-standard-style](https://cdn.rawgit.com/feross/standard/master/badge.svg)](https://github.com/feross/standard)

[![forthebadge](http://forthebadge.com/images/badges/built-with-love.svg)](http://forthebadge.com) [![forthebadge](http://forthebadge.com/images/badges/uses-js.svg)](http://forthebadge.com) [![forthebadge](http://forthebadge.com/images/badges/makes-people-smile.svg)](http://forthebadge.com)

## 概述

`electron-vue` 使用了脚手架 `vue-cli` 来避免手动设置 electron 来支持 vue 的繁琐步骤, 并添加了 [`vue-loader`](https://github.com/vuejs/vue-loader) 和 [`electron-packager`](https://github.com/electron-userland/electron-packager)/[`electron-builder`](https://github.com/electron-userland/electron-builder)等功能支持的`webpack`, 以及 `vue-router`和`vuex` 等一些常用的插件.

#### 查看文档[中文](https://coghost.gitbooks.io/electron-vue-zh/content/).

框架支持功能如下:

* 单个`package.json`即可的项目基础架构
* 详尽的[文档](https://coghost.gitbooks.io/electron-vue-zh/content/)支持
* 项目脚手架 [vue-cli](https://github.com/vuejs/vue-cli)
* 已安装可用的库 ([axios](https://github.com/mzabriskie/axios), [vue-electron](https://github.com/SimulatedGREG/vue-electron), [vue-router](https://github.com/vuejs/vue-router), [vuex](https://github.com/vuejs/vuex))*
* 开发工具 [vue-devtools](https://github.com/vuejs/vue-devtools) 和 [devtron](https://github.com/electron/devtron)
* 方便快捷的打包安装工具 [electron-packager](https://github.com/electron-userland/electron-packager) 或者 [electron-builder](https://github.com/electron-userland/electron-builder)\*
* 方便 [electron-builder](https://github.com/electron-userland/electron-builder)\*自动化部署的配置文件 `appveyor.yml` 和 `.travis.yml` 支持
* 可以生成供 `Webbrowser 浏览器` 使用的代码 `译注: 某些库可能不支持web使用, 故需要注意`
* 简单易用的 [NPM scripts](/npm_scripts.md)
* 使用 [webpack](https://github.com/webpack/webpack) 和 [vue-loader](https://github.com/vuejs/vue-loader)来实现代码热重载 `译注: 如果是 npm 新安装的 module则需要重新运行程序`
* Process restarting when working in electron's `main` process `译: 不是太明白`
* 使用 [vue-loader](https://github.com/vuejs/vue-loader/) 来实现 `HTML/CSS/JS` 预处理支持 
* ES6 默认启用 [`stage-0`](https://babeljs.io/docs/plugins/preset-stage-0/) 编译
* 使用 [`babili`](https://github.com/babel/babili) 来避免编译到 ES5
* ESLint 支持 [`standard`](https://github.com/feross/standard) 和 [`airbnb-base`](https://github.com/airbnb/javascript)
* 单元测试 `Karma + Mocha`
* 端到端测试 `Spectron + Mocha`

\* 可通过 `vue-cli` 来定制化上述插件

### 开始
该框架是可以定制你最终的APP的 `vue-cli` 脚手架, 需要使用 `node@^7` 或者更高版本. `electron-vue` 官方推荐使用 `yarn` 包管理器(`yarn` 可以更好的管理模块依赖, 通过 `yarn clean` 可以减少最终生成的app大小).

```bash
# Install vue-cli and scaffold boilerplate
npm install -g vue-cli
vue init simulatedgreg/electron-vue my-project

# Install dependencies and run your app
cd my-project
yarn # or npm install
yarn run dev # or npm run dev
```

##### 作为 Windows 用户?
请仔细检查 [**Windows用户须知**](https://simulatedgreg.gitbooks.io/electron-vue/content/en/getting_started.html#a-note-for-windows-users), 确保你已经安装所有必须依赖.

##### 使用 Vue 1?
`electron-vue` 官方不推荐使用, 不过你可以查看 [**1.0文档**](https://github.com/SimulatedGREG/electron-vue/tree/1.0/docs) 来获取信息. 

```bash
vue init simulatedgreg/electron-vue#1.0 my-project
```

### 下一步
请查看 [中文文档](https://coghost.gitbooks.io/electron-vue-zh/content/), 在这儿你可以找到关于 `配置/项目架构/编译APP` 的有用见意, 还有[常见问题](https://simulatedgreg.gitbooks.io/electron-vue/content/en/faqs.html)的汇总

### 使用 electron-vue 的项目

* [**Surfbird**](https://github.com/surfbirdapp/surfbird): A Twitter client built on Electron and Vue
* [**Lulumi-browser**](https://github.com/qazbnm456/lulumi-browser): Lulumi-browser is a light weight browser coded with Vue.js 2 and Electron
* [**Space-Snake**](https://github.com/ilyagru/Space-Snake): A Desktop game built with Electron and Vue.js.
* [**Forrest**](https://github.com/stefanjudis/forrest): An npm scripts desktop client
* [**miikun**](https://github.com/hiro0218/miikun): A Simple Markdown Editor
* [**Dakika**](https://github.com/Madawar/Dakika): A minute taking application that makes writing minutes a breeze
* [**Dynamoc**](https://github.com/ieiayaobb/dynamoc): Dynamoc is a GUI client for dynamodb-local, dynalite and AWS dynamodb
* [**Dockeron**](https://github.com/dockeron/dockeron): A dockeron project, built on Electron + Vue.js for Docker
* [**Easysubs**](https://github.com/matiastucci/easysubs): Download subtitles in a very fast and simple way