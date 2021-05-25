1.安装`babel`

```bash
npm i @babel/core @babel/preset-env babel-loader core-js -D
```

 2.`webpack.config.js`

```js
const path = require('path')

const HTMLWebpackPlugin = require("html-webpack-plugin")
const { CleanWebpackPlugin } = require('clean-webpack-plugin')

module.exports = {
    entry: "./src/index.ts",
    output: {
        path: path.resolve(__dirname, "dist"),
        filename: "bundle.js",
        environment :{
            arrowFunction:false //是否使用箭头函数
        }
    },
    module: {
        rules: [
            {
                test: /\.ts$/,
                use: [
                    /**
                     * 配置babel
                     */
                    {
                        //指定加载器
                        loader: "babel-loader",
                        //设置预定义环境
                        options: {
                            presets: [
                                [
                                    "@babel/preset-env",
                                    {
                                        //要兼容的目标浏览器
                                        targets: {
                                            "chrome": "88",
                                            // "ie":'6'
                                        },
                                        "corejs": "3",
                                        //使用corejs的方式 "usage"表示按需加载
                                        "useBuiltIns": "usage"
                                    }
                                ]
                            ]
                        }
                    },
                    'ts-loader'
                ],
                exclude: /node_modules/
            }
        ]
    },
    plugins: [
        new CleanWebpackPlugin(),
        new HTMLWebpackPlugin({
            template: "./src/index.html"
        })
    ],

    resolve: {
        extensions: [".ts", '.js']
    }

}
```



 