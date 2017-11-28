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

```js
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

### vue-cli的.eslintrc.js配置文件的解释

```js
module.exports = {
    //此项是用来告诉eslint找当前配置文件不能往父级查找
    root: true, 
    //此项是用来指定eslint解析器的，解析器必须符合规则，babel-eslint解析器是对babel解析器的包装使其与ESLint解析
    parser: 'babel-eslint',
    //此项是用来指定javaScript语言类型和风格，sourceType用来指定js导入的方式，默认是script，此处设置为module，指某块导入方式
    parserOptions: {
        sourceType: 'module'
    },
    //此项指定环境的全局变量，下面的配置指定为浏览器环境
    env: {
        browser: true,
    },
    // https://github.com/feross/standard/blob/master/RULES.md#javascript-standard-style
    // 此项是用来配置标准的js风格，就是说写代码的时候要规范的写，如果你使用vs-code我觉得应该可以避免出错
    extends: 'standard',
    // required to lint *.vue files
    // 此项是用来提供插件的，插件名称省略了eslint-plugin-，下面这个配置是用来规范html的
    plugins: [
        'html'
    ],
    // add your custom rules here
    // 下面这些rules是用来设置从插件来的规范代码的规则，使用必须去掉前缀eslint-plugin-
    // 主要有如下的设置规则，可以设置字符串也可以设置数字，两者效果一致
    // "off" -> 0 关闭规则
    // "warn" -> 1 开启警告规则
    //"error" -> 2 开启错误规则
    // 了解了上面这些，下面这些代码相信也看的明白了
    'rules': {
        // allow paren-less arrow functions
        'arrow-parens': 0,
        // allow async-await
        'generator-star-spacing': 0,
        // allow debugger during development
        'no-debugger': process.env.NODE_ENV === 'production' ? 2 : 0
    }
}
```
