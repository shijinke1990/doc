## [使用node-config+dotenv 方便的管理配置](https://www.cnblogs.com/rongfengliang/p/12993767.html)

dotenv 是遵循12 factor 的一个环境变量管理npm 包,node-config 是一个强大的配置管理npm 包，我们集成起来
可以进行方便的配置管理，以下是一个简单使用说明

## 环境准备

- node 环境

 

```
yarn init -y
yarn add dotenv config
```

- npm script

```
{
  "dependencies": {
    "config": "^3.3.1",
    "dotenv": "^8.2.0"
  },
  "scripts": {
    "app":"node app.js"
  }
}
```

- 项目结构

```
├── app.js
├── .env
├── config
│   ├── custom-environment-variables.json
│   ├── default.json
│   └── stage.json
├── package.json
└── yarn.lock
```

- 简单说明
  default.json 为默认的配置，stage.json 为stage 的配置，custom-environment-variables.json为环境变量替换的模版
  .env 为基于dotenv 管理的一个env 配置,按照node-config 的约定，环境变量包含了NODE_ENV=stage 会走stage 的配置
  同时如果.env 包含了内容会自动替换，没有的为空，同时custom-environment-variables.json 的对象会有激活的配置合并
  （当然对于重复的，custom-environment-variables会覆盖）
  default.json

 

```
{
    "apps":{
        "users":{
            "name":"dalong",
            "age":333
        }
    }
}
```

stage.json

```
{
    "apps":{
        "users":{
            "name":"stage",
            "age":333
        }
    }
}
```

custom-environment-variables.json

```
{
    "username": "USERNAME",
    "userpassword":"USERPASSWORD"
}
```

.env

```
USERNAME=dalong
USERPASSWORD=dalong
NODE_ENV=stage
```

- app.js 代码

```
require("dotenv").config()
const config = require("config")
console.log(config)
console.log('NODE_APP_INSTANCE: ' + config.util.getEnv('NODE_ENV'));
```

## 运行&&效果

- 运行

```
yarn app
```

- 效果

![img](https://img2020.cnblogs.com/blog/562987/202005/562987-20200530171915289-1519562271.png)

 

 

## 说明

集成node-config 以及dotenv 我们可以实现灵活的系统配置管理，同时方便配置的引用，还是比较方便的



## 参考

https://www.cnblogs.com/rongfengliang/p/12993767.html

