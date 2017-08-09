# 使用静态资源

如果你曾经使用过官方的 `vuejs-templates/webpack`, 你应该会熟悉 `static/` 目录. 该目录下放置的文件, 可以被 `main` 和 `renderer` 进程消费. 在你的 `Vue应用` 中来使用这些资源很简单, 但是 `fs` 和其他需要使用完全路径的模块则有些麻烦. 还好, `electron-vue` 提供了 `__static` 变量来输出到 `static/` 的路径, 可以在 `开发环境`及`生产环境` 中使用.

### 用例: Vue组件中使用 `src` 标签

假如我有一个加载图片的组件, 但是图片路径只有在某个任务完成后才能获得. 简便起见, 我们来使用 `data` 变量来绑定 `<img>`'s 源. 

**SomeComponent.vue**

```html
<template>
  <img v-bind:src="imageUrl">
</template>

<script>
  export default {
    data () {
      // notice the url starts with `static/`
      return { imageUrl: 'static/imgs/unsplash.png' }
    }
  }
</script>
```

这里 `webpack` 并不会把 `unsplash.png` 打包, 而 `应用程序` 会在 `static/imgs/unsplash.png` 下查找相关内容. 多亏了 `vue-loader`, 剩余工作都已经做好了.

### `JS`之`fs`,`path`,`__static` 用例

假如我们需要在我们的应用程序中使用 `fs` 来读取某个资源文件, 那么我们在`开发环境`及`生产环境`中如何访问到 `static` 的真实目录呢? electron-vue 提供了一个全局变量 `__static` 来映射到 `static/` 的正确目录. 接下来我们展示如何 在`开发环境`及`生产环境`中使用它来读取一个文件. 

**static/someFile.txt**

```txt
foobar
```

**SomeFile.js \(**`main`** or **`renderer`** process\)**

```js
import fs from 'fs'
import path from 'path'

let fileContents = fs.readFileSync(path.join(__static, '/someFile.txt'), 'utf8')

console.log(fileContents)
// => "foobar"
```

请谨记在`生产环境`中,所有文件默认会使用高度推荐的 [`asar`](https://github.com/electron/asar) 来打包. 鉴于此, `static/` 下的所有资源都只能在 `electron` 中访问. 所以如果你计划要发布可以被 `其他程序` 读取的资源时, 你应该首先从你的 `应用程序` 复制这些资源到用户空间或者桌面, 然后你就可以使用 [`shell.openItem()`](https://electron.atom.io/docs/api/shell/#shellopenitemfullpath) 来打开这些资源. 

另一个解决方法可以在`生产环境`中通过配置 `electron-packager`/`electron-builder` 来指定可以从 `asar`包中解压的资源. electron-vue 并不计划支持这种方法; 所有涉及到此或者如何设置的问题都会被关闭的. 
