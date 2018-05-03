## 中间层依赖库

### 核心依赖库
1.
`egg.js` 

阿里的node 框架，核心基于koa2，使用`egg init`初始化项目，包含`egg`的一系列库：`egg-scripts`,`egg-bin`,`egg-ci`,`egg-mock`

2.
`vue`, `vue-server-renderer`

实现vue服务端渲染的核心库

3.
`webpack系列库`: `webpack`,`webpack-cli`,`webpack-merge`,`webpack-node-externals`,`friendly-errors-webpack-plugin`

使用webpack 对vue项目打包，通过`vue-server-renderer`提供的方法，将打包成服务端需要的样子。

4.
`babel`系列库：`babel-core`,`babel-loader`,`babel-plugin-syntax-dynamic-import`,`babel-preset-env`

5.
loaders：`css-loader`,`url-loader`,`vue-loader`,`vue-template-compiler`

6.
其他库: 
`rimraf`：用于删除dist

## 项目说明

关于项目架构，详见`后台管理项目--前端架构.xmind`

### 项目目录
```
app
  | controller // 控制器 分发请求
  | extend // 扩展
  | middleware // 中间件
  | public 
  | service // controller分发请求数据到对应service，service具体处理请求
  | view // 模板
  | web // 前端项目所在目录
    | build
    | dist
    | starluxe-ms
      | router // 前端项目路由
      | store // vuex
      | app.js // 创建app的工厂函数
      | App.vue // 入口vue文件
      | entry-client.js // 客户端入口
      | entry-server.js // 服务端入口
      | index.template.html // 服务端渲染的模板
  | router.js // 路由请求致对应controller
config // 对不同环境下，进行配置
  | config.[env].js
  | plugin.js
logs
test // 单元测试
.babelrc
package.json



```

### egg与vue ssr的结合

[egg.js官方文档](https://eggjs.org/zh-cn/intro/quickstart.html)
[vue ssr 官方文档](https://ssr.vuejs.org/zh/)

1.
**webpack打包项目**
在`web/build`下，配置不同环境的`webpack.config`，在不同环境的配置文件中，调用对应环境的`vue-server-render/[env]-plugin`

在`package.json`中配置`webpack`打包命令（注意设置--mode），运行打包，在`web/dist`生成对应环境的`.json`文件。
- `vue-ssr-server-bundle.json`
- `vue-ssr-client-manifest.json`

2.
**配置 egg 路由-控制器-服务 的逻辑**
从`router.js`路由`http`请求根目录到`starluxe-ms`对应的`controller/starluxeMS.js`，此controller, 将请求分发到`service/ssrStarluxeMS.js`

ssrStarluxeMS.js 会调用`vue-server-renderer`的`createBundleRenderer`方法，生成一个renderer实例
向该方法传入：
- `web/starluxe-ms/index.template.html`模板，
- `web/dist/vue-ssr-server-bundle.json`打包配置文件

调用renderer实例的`renderToString`方法，将传入的appContext应用在初始化时候，配置的模板上，根据打包配置文件，将模板渲染出来，并传入回掉函数。

> 注意，在传入打包配置文件时候，必须传入一个绝对路径。在这里通过`require`进来，获得一个bundle绝对路径





