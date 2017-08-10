# FAQs

* [Why is my electron app blank after running `npm run dev`?](#why-is-my-electron-app-blank-after-running-npm-run-dev)
* [Why does my electron app show a file explorer?](#why-does-my-electron-app-show-a-file-explorer)
* [Why is `vue-devtools`/`devtron` missing?](#why-is-vue-devtoolsdevtron-missing)
* [Where do I put Static Assets?](#where-do-i-put-static-assets)
* [Why did `npm run lint` end with an error?](#why-did-npm-run-lint-end-with-an-error)
* [Why can't I load my app in a web browser?](#why-cant-i-load-my-app-in-a-web-browser)
* [How do I import `jquery`?](#how-do-import-jquery)
* [How can I debug the `main` process?](#how-can-i-debug-the-main-process)

---

## Why is my electron app blank after running `npm run dev`?

#### 为什么我运行 `npm run dev` 后程序是 `blank => 空白的/或者是不能启动`?

确保你没有使用个人 **代理**, 这个有可能会篡改 `webpack-dev-server` 

## Why does my electron app show a file explorer?

#### 为什么我的应用显示了文件管理器?

你的 `src/renderer` 有错误, 仔细检查输出终端, 搞定错误, 然后使用 `CommandOrControl+R` 刷新 `electron`. 
如果启动时错误出现在 `src/renderer` 会导致与 ESLint 出现冲突. 相应的, 一个 `INVALID` 的 webpack `renderer.js` 会打断 `HtmlWebpackPlugin` 创建 `index.html`. 由于 `webpack-dev-server` 并没有 `index.html` 来服务, 服务就会回滚到 `文件管理器`. 

## Why is `vue-devtools`/`devtron` missing?

如果缺少了某些模块, 请在安装相应模块后, 关闭并重新启动应用. 检查终端看看是否在安装过程中有其他错误信息. 


## Where do I put Static Assets?

[**Using Static Assets**](/using-static-assets.md)

## Why did `npm run lint` end with an error?

这是一个正常现象, ESLint 的本质就是在终端中显示 `检查错误`, 如果有错误, 则程序就会异常退出. 

## Why can't I load my app in a web browser?

[\#195](https://github.com/SimulatedGREG/electron-vue/issues/195)

## How do import `jquery`?

如果你打算使用 `bootstrap`, 我在这会阻止你的. 在同一个环境下同时使用 `vue` 和 `jquery` 是一个错误的实践, 这会导致两个框架之间相互冲突. 此处高度推荐使用了 `vue` 作为 JavaScript 功能的开发者使用 `bootstrap替代品`. 
推荐使用的有 [`bootstrap-vue`](https://github.com/bootstrap-vue/bootstrap-vue) 和 [`vue-strap`](https://github.com/yuche/vue-strap). 不管为何你必须非要使用 `jquery`, 查看 `webpack`'s 的文档中关于`ProvidePlugin`的向导或者查看 [\#192](https://github.com/SimulatedGREG/electron-vue/issues/192).

## How can I debug the `main` process?

当使用 `electron@^1.7.2` 时, 你可以打开 `Google Chrome`, 输入 `chrome://inspect`, 然后选择运行于开发环境的你的应用. 详情参考 [文档](https://github.com/electron/electron/blob/master/docs/tutorial/debugging-main-process.md)