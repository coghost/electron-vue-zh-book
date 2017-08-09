# 使用 CSS 框架

尽管听起来像是废话, 我还是建议你使用 [`style-loader`](https://github.com/webpack/style-loader) 来导入你的 `third-party CSS 库` 到 `webpack`中, 而这个已经帮你设置好了. 

## 用例

假如你打算在你的产品中使用 [bootstrap](http://getbootstrap.com/), [bulma](http://bulma.io/), 或者 [materialize](http://materializecss.com/). 像通常那样来使用 `npm` 来安装你的框架, 但是我们会通过在 `src/renderer/main.js` 来 `import 相应的 css`, 而不是直接添加到 `index.ejs` 文件.

#### Example

- 安装 `bulma`

```bash
npm install bulma --save
```

- 接下来 `src/renderer/main.js` 添加如下

```bash
import 'bulma/css/bulma.css'
```

- 同样, 你也可以只在某个组件中引入 `bulma`

**App.vue**

```html
<style>
  @import "~bulma/css/bulma.css";
</style>
```

现在 `webpack` 就知道要在我们的应用中使用 `bulma`, 并且保证可以在发布的产品中可用.
