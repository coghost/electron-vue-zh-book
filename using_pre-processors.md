# 使用预处理器

在 [`webpack`](https://github.com/webpack/webpack) 中使用 [`vue-loader`](https://github.com/vuejs/vue-loader) 的一个最大好处就是可以轻松的在 `Vue 组件` 中直接预处理 `HTML/CSS/JS`, 而这些只需要简单配置即可实现. 详情可参考 [**单文件组件**](https://vuejs.org/v2/guide/single-file-components.html).

## 使用场景

假定我们需要使用 `Sass/SCSS` 来处理我们的 CSS, 我们需要首先安装合适的 `webpack loader` 来处理相应语法.

#### 安装 `sass-loader`

```bash
npm install --save-dev sass-loader node-sass
```

安装完相应的加载器, 基本上步骤已经完成了. `vue-loader` 会接下来处理余下的所有工作. 现在我们需要做的仅仅是在 `Vue 组件`中添加 `lang="sass"` 或者 `lang="scss"`. 注意我们同样安装了 `sass-loader` 的依赖包 `node-sass`.

#### 应用 `lang` 属性

所以...

```html
<style>
  body {
    /* CSS */
  }
</style>
```

...现在变成了...

```html
<style lang="scss">
  body {
    /* SCSS */
  }
</style>

<!-- 译: 也可以使用 sass -->
<style scoped lang="sass">
  body {
    /* SASS */
  }
</style>
```

这个准则对于其他任何 `pre-processor` 都通用. 
假如你需要使用 `coffeescript`? 那么只需要安装 [coffeescript-loader](https://github.com/webpack/coffee-loader), 并且应用 `lang="coffeescript"` 到你的 `<script>` 标签上. 

如果需要了解更多高级用法, 参考 [vue-loader documentation](http://vue-loader.vuejs.org/en/configurations/pre-processors.html). 

## 启用 `Sass/SCSS` 全局变量

当使用 `Sass/SCSS` 来编写 CSS 时, 在所有的`Vue 组件`中使用全局 `variables/mixins` 是很有益处的, 下面来介绍下如何实现.

### 用例

下面的例子展示了如果应用 `globals.scss` 到所有组件中. 本文档假定你已经按照上面的说明安装设置好了 `sass-loader`.

#### 定义你的变量

**src/renderer/globals.scss**

```scss
$brand-primary: blue;
$brand-accent: turquoise;
```

#### 注入 `globals.scss` 到 `node-sass`

编辑 **.electron-vue/webpack.renderer.config.js** 配置中的 `vue-loader` 部分

```js
loaders: {
  sass: 'vue-style-loader!css-loader!sass-loader?indentedSyntax=1&data=@import "./src/renderer/globals"',
  scss: 'vue-style-loader!css-loader!sass-loader?data=@import "./src/renderer/globals";'
}
```

#### 使用

**SomeComponent.vue**

```html
<style lang="scss">
  body { color: $brand-primary; }
</style>
```

