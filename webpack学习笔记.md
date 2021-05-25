1.自动生成html文件

```bash
npm i -D html-webpack-plugin
```

2.修改webpack.config.js

```js
const path = require("path")

const htmlWebpackPlugin = require('html-webpack-plugin') //新增

module.exports = {
    entry: "./src/index.ts",
    output: {
        path: path.resolve(__dirname, 'dist'),
        filename: "bundle.js"
    },
    module: {
        rules: [
            {
                test: /\.ts$/,
                use: "ts-loader",
                exclude: /node_modules/
            }
        ]
    },

    plugins:  //新增
        new htmlWebpackPlugin(),//新增
    ]//新增


}
```



