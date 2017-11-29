# 外卖商城

## 目录结构

```js
.
|-- build                       // 项目构建(webpack)相关代码
|   |-- build.js                  // 生产环境构建代码
|   |-- check-version.js          // 检查node、npm等版本
|   |-- dev-client.js             // 热重载相关
|   |-- dev-server.js             // 构建本地服务器
|   |-- utils.js                  // 构建工具相关
|   |-- webpack.base.conf.js      // webpack基础配置
|   |-- webpack.dev.conf.js       // webpack开发环境配置
|   |-- webpack.prod.conf.js      // webpack生产环境配置
|-- config                      // 项目开发环境配置
|   |-- dev.env.js                // 开发环境变量
|   |-- index.js                  // 项目一些配置变量
|   |-- prod.env.js               // 生产环境变量
|   |-- test.env.js               // 测试环境变量
|-- src                         // 源码目录
|   |-- api                       // 所有请求
|   |-- assets                    // 放静态内容的地方，但是支持预编译
|   |-- router/index.js           // router文件夹是放路由的地方，index.js是我们的根路由 
|   |-- components                // vue公共组件
|   |-- store                     // vuex的状态管理
|   |-- style                     // 放置样式
|   |-- App.vue                   // 页面入口文件
|   |-- main.js                   // 程序入口文件，加载各种公共组件
|-- static                      // 静态文件，比如一些图片，json数据等
|   |-- .gitkeep                  // 该文件的作用就是即使目录是空的也会提交到仓库
|-- .babelrc                    // ES6语法编译配置
|-- .editorconfig               // 定义代码格式
|-- .gitignore                  // git上传需要忽略的文件格式
|-- README.md                   // 项目说明
|-- favicon.ico                 // 图标
|-- index.html                  // 入口页面
|-- package.json                // 项目基本信息
```

![sell商城](https://camo.githubusercontent.com/a83e675d5dc0e7b828868d49cfc5afb4bacc7dd9/68747470733a2f2f7765626170702e646964697374617469632e636f6d2f7374617469632f7765626170702f736869656c642f7675652d73656c6c2e706e67)


