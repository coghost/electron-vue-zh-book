# 项目结构

当需要开发 `electron apps` 时, 项目结构会有一点变动. 如果你之前有使用过官方的 [`vuejs-templates/webpack`](https://github.com/vuejs-templates/webpack) 的设置, 那么这个架构, 你会看起来相当熟悉. 这部分文档会对于框架如何工作及在编译过程的不同之处给出一个大概的描述.

### 单 `package.json` 配置

不久之前, 两个独立的 `package.json` 文件仍然是必需的, 但是多亏了 [@electron-userland](https://github.com/electron-userland), 现在 [`electron-packager`](https://github.com/electron-userland/electron-packager) 和 [`electron-builder`](https://github.com/electron-userland/electron-builder) 全部都支持了使用单 `package.json` 来配置

#### `dependencies: 运行依赖`

这些依赖`会`出现在最终的产品之内. 因此,如果你的程序需要某个特定的模块来运行, 安装在这里

```bash
npm i <module> --save
```

#### `devDependencies: 开发依赖`

这些依赖`不会`出现在你最终发布的产品之中. 在这里, 你可以安装开发过程中所有需要的包比如 `webpack` 等.`(打包时,不会增加打包大小)`


```bash
npm i <module> --save-dev
```

#### 安装 `Native NPM Modules:原生npm模块`

我们需要确保我们的`原生npm模块`可以被electron支持.要实现这个, 我们可以使用 [`electron-rebuild`](https://github.com/electron/electron-rebuild), 不过为了简化操作, 高度推荐使用 [`electron-builder`](https://github.com/electron-userland/electron-builder) 来作为编译工具, 因为 `electron-builder` 会帮你做大量的处理工作.

### 关于 `main` 进程

在开发过程中, 你也许已经注意到了 `src/main/index.dev.js`. 这个文件是专门用来在开发过程中使用, 通常用来安装 `dev-tools:开发工具`. 这个文件不应该被修改, 而是用来扩展你的开发需求. 
在构建项目时, `webpack` 会被调用并且使用 `src/main/index.js` 来作为入口文件来创建一系列文件.
