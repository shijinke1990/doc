作为一个*Weekly Downloads*下载数逆天的模块，`glob`质量有保障。整理一下`glob`的用法以输出促进学习并备作复习。

# 1.安装

```bash
npm i glob
```

或

```bash
yarn add glob
```

# 2.当前目录下所有**js**

```js
const glob = require('glob')

glob("*.js", function (err, files) {
    console.log(files)
})
```

# 3.匹配当前目录子目录下所有文件

```js
const glob = require('glob')

glob("*/*.*", function (err, files) {
    console.log(files)
})
```

# 4.递归匹配当前目录及其子目录下所有文件

体现的是 ** 与 * 的区别

```js
const glob = require('glob')

glob("**/*.*", function (err, files) {
    console.log(files)
})
```

# 5.glob 支持的通配符模式

glob 支持强大的匹配规则，但是要注意glob的匹配规则并不是正则表达式，详细支持如下：

- `*` 匹配0到多个字符
- `?` 匹配一个字符
- `[...]` 匹配一个字符列表，类似正则表达式的字符列表
- `!(pattern|pattern|pattern)` 反向匹配括号内的模式
- `?(pattern|pattern|pattern)` 匹配0或1个括号内的模式
- `+(pattern|pattern|pattern)` 匹配至少1个括号内的模式
- `*(pattern|pattern|pattern)` 匹配0到多个括号内的模式
- `@(pattern|pat*|pat?erN)` 精确匹配括号内的模式
- `**` 匹配0到多个子目录，递归匹配子目录

# 6.匹配app目录中所有文件名长度（不包括后缀）为1的js文件

```jsx
//?:匹配路径中某部分:1个字符
glob("app/?.js",function (er, files) {
    console.log(files)
})
```

# 7.将app目录a0.js,a1.js,a2.js,a3.js中存在的加入到返回的数组中

```js
glob("js/a[0-3].js",function (er, files) {
    console.log(files)
})
```

# 8.`*(pattern1|pattern2|pattern3)` : 匹配括号中多个模型的0个或多个或任意个的组合
 `|`前后不能有空格

```jsx
//*(pattern|pattern|pattern): 匹配路径中的某部分: 多个模型中的0个或多个. //除了三个模型本身,如果是组合也可以,比如ab.js,但是仅仅包含某个模型是不行的,比如a4.js.
    glob("js/*(a|a1|b).js",function (er, files) {
        console.log(files)
    })
```

获取`js`目录下`a.js`,`a1.js`,`b.js`,或者`a`,`a1`,`b`这几个字符的组合的`js`,比如`ab.js`



## 参考

https://www.jianshu.com/p/5274cb9d1fc6

https://www.cnblogs.com/xinxingyu/p/5736244.html

