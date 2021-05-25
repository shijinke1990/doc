```
yarn add dotenv
```



# Dotenv

[![键盘侠五条](https://pic4.zhimg.com/v2-a772cd5800ef28fe1ea3c3fca6c8ec59_xs.jpg?source=172ae18b)](https://www.zhihu.com/people/wuli-north)

[键盘侠五条](https://www.zhihu.com/people/wuli-north)

一个爱鼓捣机械键盘的不知名博主

1 人赞同了该文章

**介绍**

`npm` 官方文档的这样介绍 [dotenv](https://link.zhihu.com/?target=https%3A//www.npmjs.com/package/dotenv): `Dotenv` 是一个零依赖的模块，它能将环境变量中的变量从 `.env` 文件加载到 `process.env` 中。将环境相关的配置独立于代码之外亦是 [The Twelve-Factor App](https://link.zhihu.com/?target=https%3A//12factor.net/config) 的要素之一。

## **使用**

1. 在项目中安装 dotenv

```text
npm install dotenv -S
```

1. 根目录下创建 .env 文件

```text
HOST=localhost
PORT=3000
MONGOOSE_URL=mongodb://localhost:27017/test
```

1. 根目录下 app.js 下引入 dotenv 并使用

```text
require('dotenv').config({ path: '.env' })

// 使用
console.log(process.env.HOST) // localhost
console.log(process.env.PORT) // 3000
console.log(process.env.MONGOOSE_URL) // mongodb://localhost:27017/test
```

使用 `dotenv` 可以让我们免于在各个文件中引入配置文件，也可以很好的解决敏感信息的泄漏，利于后期代码维护，快用起来吧！