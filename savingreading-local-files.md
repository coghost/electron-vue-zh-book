# 读写本地文件

使用 `electron` 的一个最大获益就是可以访问用户文件系统, 这让你可以读写用户本地文件. 为了避免 `Chromium` 的限制并且读写你的应用程序的内部文件, 请确保使用了 `electron`'s APIs, 通过 [`app.getPath(name)`](https://electron.atom.io/docs/api/app/#appgetpathname) 功能, 来获取 `应用程序` 的目录. `app.getPath(name)` 方法可以帮助你获取你的文件在系统中的位置, 比如 `user`'s 桌面, 系统临时文件等.

### 用例

假定我们需要使用本地数据库来存储我们的应用程序. 这里我们使用 [`nedb`](https://github.com/louischatriot/nedb) 来描述. 

```bash
yarn add nedb # or npm install nedb --save
```

**src/renderer/datastore.js**

在这里我们设置 `NeDB` 并将其指向我们的 `userData` 目录. 这部分空间是专门为我们的程序使用的, 所以我们确信其他程序或者交互不会篡改我们的文件空间. 在此我们可以导入 `datastore.js` 到 `renderer`进程并且消费它. 

```js
import Datastore from 'nedb'
import path from 'path'
import { remote } from 'electron'

export default new Datastore({
  autoload: true,
  filename: path.join(remote.app.getPath('userData'), '/data.db')
})
```

**src/renderer/main.js**

To take this a step further, we can then import our datastore into `src/renderer/main.js` and attach it to the Vue prototype. Doing so, we are now able to access the datastore API through the usage of `this.$db` in all component files.

```js
import db from './datastore'

/* Other Code */

Vue.prototype.$db = db
```

