# 开始

## 脚手架

该框架是可以定制你最终的APP`vue-cli`的脚手架, 需要使用 `node@^7` 或者更高版本. `electron-vue` 官方推荐使用 `yarn` 包管理器(`yarn`可以更好的管理模块依赖和通过`yarn clean`来减少最终生成的app大小).

```bash
# Install vue-cli and scaffold boilerplate
npm install -g vue-cli
vue init simulatedgreg/electron-vue my-project

# Install dependencies and run your app
cd my-project
yarn # or npm install
yarn run dev # or npm run dev
```

#### 主版本选择

尽管不是必须, 但是在创建完成项目后, 建议锁定你的 `electron 版本`. 这可以避免不同开发者在同一个项目中使用不同版本的 `electron`. 而且 `Electron` 经常会发布一些版本变更, [详情参考](http://electron.atom.io/docs/tutorial/electron-versioning/)

#### Windows用户说明

如果在 `npm install` 中出现了 `node-gyp` 报错, 则很有可能是由于你的系统安装了错误的编译工具. 这些编译工具包括 `Python` 和 `Vusual Studio`. 感谢 [@felixrieseberg](https://github.com/felixrieseberg) 提供的简化这些操作的包.

首先检查 `npm 版本`,并确保安装了最新版本, 可以通过 [`npm-windows-upgrade`](https://github.com/felixrieseberg/npm-windows-upgrade) 来检查实现. 如果你使用的是 `yarn`, 可以跳过该检查

确定最新版本后, 我们接下来使用 [windows-build-tools`](https://github.com/felixrieseberg/windows-build-tools) 来实现设置编译工具. 全局安装后会相应的安装 `Vusual C++ packages, Python` 和一些相关依赖.

到这里, 所有相关依赖应该已经安装成功, 但是如果还有问题, 则你需要全新安装 `Vusual Studio` 环境. 这里已经不是 `electron-vue` 本身的问题了 (Windows 总是有一些莫名其妙的问题).