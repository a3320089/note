# webpack

webpack.cnofig.js的配置文件写法

```javascript
var path = require("path");
var htmlWebpack = require("html-webpack-plugin");
var cleanWebpack = require("clean-webpack-plugin");
var rv = (...a) => path.resolve(__dirname,...a);

var webpack = require("webpack");

module.exports ={
    entry:"./src/app.js",
    output:{
        filename:"app.js",
        path:rv("dist")
    },
    module:{
        rules:[{
            test:/\.js$/,
            use:["babel-loader"],
            exclude:[rv("node_modules")]
        },{
            test:/\.css$/,
            use:["style-loader","css-loader"] // loader: 'style!css-loader?modules&importLoaders=1&localIdentName=[name]__[local]___[hash:base64:5]'
        },
        {
            test:/\.(jpg|png|jpeg|gif)/,
            use:["file-loader"]
        }
        ]
    },
    devtool:"eval-source-map"
    ,
    plugins:[
        new htmlWebpack({
            filename:"index.html",
            template:"./src/index.html"
        }),
        new cleanWebpack(["dist"]),
        new webpack.ProvidePlugin({
            React:"react",
            Component:["react","Component"],
            ReactDOM:"react-dom"
        })
    ],
    devServer:{
        open:true,
      historyApiFallback:true
    }

}
```



插件需要:

​	babel-core     babel的核心

​	babel-loader		webpack处理代码的核心

​	babel-preset-react    处理react代码

​	babel-preset-env		处理es6代码

### ​package.json:

"dev": "webpack",

"start": "webpack-dev-server"

```javascript
{
  "name": "React-router",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "dev":"webpack",
    "start":"webpack-dev-server"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {
    "react": "^16.0.0",
    "react-dom": "^16.0.0"
  },
  "devDependencies": {
    "babel-core": "^6.26.0",
    "babel-loader": "^7.1.2",
    "babel-plugin-transform-object-rest-spread": "^6.26.0",
    "babel-preset-env": "^1.6.1",
    "babel-preset-react": "^6.24.1",
    "clean-webpack-plugin": "^0.1.17",
    "css-loader": "^0.28.7",
    "file-loader": "^1.1.5",
    "html-webpack-plugin": "^2.30.1",
    "style-loader": "^0.19.0",
    "webpack": "^3.8.1",
    "webpack-dev-server": "^2.9.4"
  }
}

```

