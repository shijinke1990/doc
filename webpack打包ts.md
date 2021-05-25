# 1.npm初始化

```bash
npm init -y
```

在`scripts`加入`"build":"webpack"`

# 2.安装模块

```bash
npm i -D webpack webpack-cli typescript ts-loader
```

# 3.生成ts配置文件`tsconfig.json`

```bash
tsc -init
```

# 4.创建webpack配置文件webpack.config.js

```js
const path = require('path')

module.exports = {
    entry: "./src/index.ts",
    output: {
        path: path.resolve(__dirname, "dist"),
        filename: "bundle.js"
    },
    module:{
        rules:[
            {
                test: /\.ts$/,
                use: 'ts-loader',
                exclude: /node_modules/
            }
        ]
    }
}
```

# 5.创建src目录以及index.ts文件

# 6.运行build

```bash
npm run build
```

