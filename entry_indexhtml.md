# 入口 `index.html`

electron-vue 在构建产品时通过使用 [**`html-webpack-plugin`**](https://github.com/ampedandwired/html-webpack-plugin) 来创建 `index.html`. 在开发过程中, 你会发现 `src/` 目录下的 `index.ejs`, 而这个就是你用来改变你最终生成的 `HTML` 文件的模板.

如果你不了解这个插件是怎么工作的, 那么推荐你看一下 [html-webpack-plugin]((https://www.npmjs.com/package/html-webpack-plugin). 但是如果你不关心, 那么简单来说, 这个插件会自动包含 `renderer.js/styles.css` 等资源到并 `注入/压缩` 到 `index.html` 中.

### 开发使用的 `index.ejs`

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title><%= htmlWebpackPlugin.options.title %></title>
    <%= ... %>
  </head>
  <body>
    <div id="app"></div>
    <!-- webpack builds are automatically injected -->
  </body>
</html>
```

### 产品中使用的`index.html` 

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>app</title>
    <link href="styles.css" rel="stylesheet">
  </head>
  <body>
    <div id="app"></div>
    <script type="text/javascript" src="renderer.js"></script>
  </body>
</html>
```

### 关于使用 `CDNs`

尽管使用 `CDN` 可以减少你最终生成  `app` 的大小, 但是仍然不推荐使用. 主要原因就是如果使用 `CDN`, 则我们需要保证 `app` 应用需要一直保持到 `Internet` 的连接, 而这个却并不是 `Electron apps` 所具备的. 如果你使用了像 `bootstrap` 这样的 `CSS框架`, 这就是一个导致你的 `app` 样式看起来一团糟的相当重要的原因. 

> "我不管, 我就是要用 CDN"

如果你依然打算使用 CDN, 那么你可以在 `src/index.ejs` 中添加相应 tags . 不过你需要确保设置合适的 `UI/UX` 来应对 `app` 离线的情形.