# 外卖商城

## 项目初始化

```
vue init webpack

npm install chromedriver --chromedriver_cdnurl=http://cdn.npm.taobao.org/dist/chromedriver

npm install 

npm run dev
```

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

### vue-cli脚手架的.babelrc文件

```json
{
    // 此项指明，转码的规则
    "presets": [
        // env项是借助插件babel-preset-env，下面这个配置说的是babel对es6,es7,es8进行转码，并且设置amd,commonjs这样的模块化文件，不进行转码
        ["env", { "modules": false }],
        // 下面这个是不同阶段出现的es语法，包含不同的转码插件
        "stage-2"
    ],
    // 下面这个选项是引用插件来处理代码的转换，transform-runtime用来处理全局函数和优化babel编译
    "plugins": ["transform-runtime"],
    // 下面指的是在生成的文件中，不产生注释
    "comments": false,
    // 下面这段是在特定的环境中所执行的转码规则，当环境变量是下面的test就会覆盖上面的设置
    "env": {
        // test 是提前设置的环境变量，如果没有设置BABEL_ENV则使用NODE_ENV，如果都没有设置默认就是development
        "test": {
            "presets": ["env", "stage-2"],
            // instanbul是一个用来测试转码后代码的工具
            "plugins": ["istanbul"]
        }
    }
}
```
