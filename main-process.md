# 主进程

> 在 `Electron` 中, 运行 `package.json's main script` 的进程被称为 `main process: 主进程`. 运行于主进程的脚本, 可以通过创建 web 页面来展示 GUI

**参考**[**Electron Documentation**](http://electron.atom.io/docs/tutorial/quick-start/#main-process)

---

由于 `main` process 本质是全node 环境, 除了两个文件以外, 不能有其他项目结构

#### `src/main/index.js`

该文件是程序的主文件, `electron` 的启动文件. 也是 `webpack` 构建时的入口文件. 所有的 `main process` 都应该从这里启动.

#### `src/main/index.dev.js`

由于安装了 `electron-debug` 和 `vue-devtools`, 该文件是专门用于开发环境的. 你不应该修改这个文件, 不过可以用来扩展你的开发需求.

## 关于 `__dirname/__filename` 的使用

由于 `main process` 会被 `webpack` 打包, 所有在产品环境中使用 `__dirname/__filename` 并不能达到预期的目标. 参考: [**File Tree**](/file-tree.md), 你会发现在产品环境中 `main.js` 是放置于 `dist/electron` 目录中. 基于此, 正确的使用 `__dirname/__filename`.
**如果你需要使用你的 `static/` 目录, 请详细阅读 **[**Using Static Assets**](/using-static-assets.md)** 来获取关于 `超级方便的 __static` 变量.**


```sh
app.asar
├─ dist
│  └─ electron
│     ├─ static/
│     ├─ index.html
│     ├─ main.js
│     └─ renderer.js
├─ node_modules/
└─ package.json
```
