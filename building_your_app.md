# 编译 App 

electron-vue 支持使用 [electron-packager](https://github.com/electron-userland/electron-packager) 和 [electron-builder](https://github.com/electron-userland/electron-builder) 来编译和发布你的应用. 两个编译工具都是由神奇的 [@electron-userland](https://github.com/electron-userland) 社区支持并且都拥有详尽的文档. 在使用 `vue-cli` 脚手架时, 你可以来自由选择使用哪一个. 

## [`electron-packager`](using-electron-packager.md)

如果你只是刚刚开始学习 `electron` 或者只是仅仅需要创建执行文件, 那么 `electron-packager` 完全可以满足你的需求.

## [`electron-builder`](using-electron-builder.md)

如果你需要全平台安装包, 自动升级, CI(`Travis CI & AppVeyor`), 或者自动编译`原生node模块`, 则推荐使用 `electron-builder`. 
