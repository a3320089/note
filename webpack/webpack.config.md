# webpack

webpack.cnofig.js的配置文件写法

```javascript

const path = require("path");

const HtmlWebpack = require("html-webpack-plugin");
const CleanWebpack = require("clean-webpack-plugin");

const rv = (name) =>{
    return path.resolve(__dirname,name);
}

module.exports = {
    entry:"./src/app.js",
    output:{
        filename:"[hash]_app.js",
        path:rv("dist")
    },
    module:{
        rules:[{
            test:/\.js$/,
            use:["babel-loader"],
            exclude:[rv("node_modules")]
        }]
    },
    plugins:[
        new HtmlWebpack({
            filename:"index.html",
            template:"./src/index.html"
        }),
        new CleanWebpack(["dist"])
    ]
}
```



插件需要:

​	babel-core     babel的核心

​	babel-loader		webpack处理代码的核心

​	babel-preset-react    处理react代码

​	babel-preset-env		处理es6代码

​	