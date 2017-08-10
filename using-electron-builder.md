# [`electron-builder`](https://github.com/electron-userland/electron-builder)

由 `electron-builder` 构建的所有可执行文件都放置在 `build` 目录

#### 编译

```bash
npm run build
```

#### 只编译生成执行文件

只编译生成执行文件, 而不是完整安装包. 多用来了快速测试. 

```bash
npm run build:dir
```

### 默认配置

参考 [文档](https://github.com/electron-userland/electron-builder/wiki/Options) 获取关于如何定制 `package.json` 中的 `electron-builders` 的更多信息. 

```js
"build": {
  "productName": "ElectronVue",
  "appId": "org.simulatedgreg.electron-vue",
  "dmg": {
    "contents": [
      {
        "x": 410,
        "y": 150,
        "type": "link",
        "path": "/Applications"
      },
      {
        "x": 130,
        "y": 150,
        "type": "file"
      }
    ]
  },
  "directories": {
    "output": "build"
  },
  "files": [
    "dist/electron",
    "node_modules/",
    "package.json"
  ],
  "mac": {
    "icon": "build/icons/icon.icns"
  },
  "win": {
    "icon": "build/icons/icon.ico"
  },
  "linux": {
    "icon": "build/icons"
  }
}
```

## 使用 CI 自动部署

当你选择了使用 `electron-builder` 来作为编译选项时, 会自动生成 `appveyor.yml` 和 `.travis.yml` 来实现自动化部署工作. 两个配置文件都是用来设置编译你的应用并且推送你的代码到 `GitHub版本`, 二进制包等. `Travis CI` 是用于 `linux`和`darwin` \(macOS\) 平台, 而 `AppVeyor` 是用于 `win32`. 两者对于开源软件来讲都是免费的. 

#### 设置 `Travis CI/AppVeyor`

1. 在[Travis CI](https://travis-ci.org/getting_started) / [AppVeyor](https://www.appveyor.com/)创建账号
2. 链接你的 在 github 上的`electron-vue项目库`
3. 访问 [https://github.com/settings/tokens](https://github.com/settings/tokens), 点击 **Generate new token ** \(一个 token 可以同时被Travis CI & AppVeyor使用\)
	1. 设置 **Token description**
	2. 检查 **public\_repo** 区域
	3. 点击 **Generate token**
4. 复制保存你的 token 备用. 
5. 打开你的 `Travis CI/AppVeyor` 的仓库设置, 添加 **Environment Variable**
	1. 设置变量名为 `GH_TOKEN`
	2. 设置变量值为你刚才创建的 `GitHub access token` 
	3. 确保加密已经开启, 然后 **Save** 新添加的变量

现在, 每一件事都已经设置好了. `Travis CI/AppVeyor` 默认会监视你的向 `master` 推送的代码. 
当你发起新的推送时, `Travis CI/AppVeyor` 会从你的仓库中 clone 代码到其服务器并且开始编译过程. 在最后一步, `electron-builder` 会查看 `GH_TOKEN` 环境变量然后创建一个 `待发布版本` 并上传到你的公共 `Github 仓库`. 接下来, 你可以编辑这个 `待发布版本`, 发布到全世界. 在发布你的新版本之后, 请确保在 `package.json` 中更新你未来需要发布的版本号. 

#### 自动升级

让你的应用支持自动更新是一个相当酷的事情, 不过你首先需要 [**Code Signing**](https://github.com/electron-userland/electron-builder/wiki/Code-Signing). 你可以依照 [文档](https://github.com/electron-userland/electron-builder/wiki/Code-Signing) 说明来设置一下必须的环境变量. 等设置好了认证, 你就可以安装 `electron-updater`, 然后取消 `src/main/index.js` 文件底部的注释来启用自动升级功能了. 

不过就像大多数人一样, 如果你没有代码签名认证, 那么你可以使用 GitHub API 来检查新的版本. 当一个新的版本出现时, 会在你的内部产生一个通知, 指明在哪里用户可以下载安装最新版本. 多亏了神奇的 `electron-builder`, 用户并不需要先卸载当前版本才能安装新版本, 新版本会自动覆盖老版本, 并且保存原有的 `web storage`或者 `userData` 文件. 

