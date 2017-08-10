# [`electron-packager`](https://github.com/electron-userland/electron-packager)

由 `electron-packager` 构建的所有可执行文件都放置在 `build` 目录

#### 编译为全系统平台通用

并不是所有平台都可以编译支持所有其他平台. 

```bash
npm run build
```

#### 编译指定系统平台

当前已支持 `darwin`, `mas`, `linux` 和 `win32`. 

```bash
# build for darwin (macOS)
npm run build:darwin
```

#### 清空

删除 `build` 目录所有已编译内容

```bash
npm run build:clean
```

### 非 `Windows` 用户

如果打算在 `非Windows` 平台编译支持 `Windows` 执行程序, 你必须安装 [wine](https://www.winehq.org/). [查看更多信息](https://github.com/electron-userland/electron-packager#building-windows-apps-from-non-windows-platforms).

### 默认配置

可以参考[文档](https://github.com/electron-userland/electron-packager/blob/master/docs/api.md#options)来获取关于如何修改 `.electron-vue/build.config.js` 来进行自定义/更详细的配置. 最终生成的 可执行文件名是在你的 `package.json` 中 `productName` 设置好的.

```js
{
    // Target 'x64' architecture
    arch: 'x64',

    // Compress app using 'electron/asar'
    asar: true,

    // Directory of the app
    dir: path.join(__dirname, '../'),

    // Set electron app icon
    // File extensions are added based on platform
    //
    // If building for Linux, please read
    // https://github.com/electron-userland/electron-packager/blob/master/docs/api.md#icon
    icon: path.join(__dirname, '../build/icons/icon'),

    // Ignore files that would bloat final build size
    ignore: /(^\/(src|test|\.[a-z]+|README|yarn|static|dist\/web))|\.gitkeep/,

    // Save builds to `builds`
    out: path.join(__dirname, '../build'),

    // Overwrite existing builds
    overwrite: true,

    // Environment variable that sets platform
    platform: process.env.BUILD_TARGET || 'all'
}
```
