# 一个懒人自己用的 Angular 种子项目

自己一直用的一个 Angular 项目脚手架。这个项目的特点就是用了好多年但是主体思想基本没变，就是 `cat **/*.js > all.js`（嗯哼我就是不喜欢各种 AMD/CMD/TMD 什么的）。

## 项目初始化

```
git clone git://github.com/perfectworks/angular-sample.git
```

然后用你自己喜欢的编辑器或者 `sed` 把 `angular-common` 替换成你喜欢的项目名字，就这样。我自己是有个 sed 脚本来做这个事情的，但是写的太烂了不想开源。

目录下比较重要的文件是 `index.html`, `main.js` 和 `main.less` 三个文件，这三个文件不能改名。作用如下:

### `index.html`

落地页，要加第三库的就直接在这里面增加 `<script>` 和 `<link>` 标签。这里要注意的是我建议第三方库不合并直接引入，因为静态资源有缓存并且其实浏览器加载并没你想的那么慢。

### `main.js`

第一个被执行的 js，要做什么随你啦。不过我建议这里面除了初始化一个 angular 项目然后管理模块依赖以外什么都不要做，留着它就行了。要写别的 js 文件的话，随便找个地方写就好了，js 合并方式基本上就是 `cat **/*.js > all.js`，所以你只要写在这个项目下面，不管写在哪都能找到的。

### `main.less`

顾名思义，写样式的地方。随便写，你开心就好。最终会被编译成 `app.css`。

## 使用这个项目

记得先 `npm install` 之后才能好好玩。这个项目主要有两套脚本，一套是支持开发环境下的无编译调试，另一套支持线上环境的打包压缩部署。

### 开发使用

```
node node_modules/gulp-angular-project/devServer.js
```

然后访问本地 3000 端口就好了。

### 线上部署

```
gulp --gulpfile node_modules/gulp-angular-project/gulpfile.js --cwd . [--cdn CDN_PATH]
```

之后所有文件会打到 `dist` 目录下。如果通过 `--cdn` 指定了 `CDN_PATH`，那么所有静态文件前面都会多一个 `CDN_PATH` 作为前缀。

打包完之后把整个 `dist` 目录通过你喜欢的工具传到服务器上，就行了，这个项目在线上环境是纯静态的，不需要 node 也不需要 java 什么的，有 nginx 就够了。

## 其他

鉴于前端构建是一座一点都不好玩的屎山，所以这个项目基本上不会增加新 feature。

## License

MIT.
