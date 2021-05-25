# 1.发布一个npm包

### **第一步：进入要发布的项目根目录，初始化为npm包：**

```bash
mkdir fibfunc
```

```bash
cd fibfunc
```

```bash
npm init
```

### 第二步、注册npm用户，有两种方法

方法一、npm官网注册：[npm](https://www.npmjs.com/)

方法二、使用npm 命令注册：npm adduser

### 第三步、账号登录

```bash
npm login
```

### 第四步、发布包，上传到npm包服务器

```bash
npm publish
```

### 第五部、更新发布的包

```bash
sudo npm version patch
```

或者 `npm version minor`、`npm version major`

- **patch**: 小改动，比如修个bug什么的，版本号变动： v1.0.0->v1.0.1
- **minor**：增加新功能，不影响现有功能，版本号变动v1.0.0->v1.1.0
- **major**：破坏模块向后的兼容性，版本号变动：v1.0.0->v2.0.0

如果用**git**追踪了修改，更新前需要**git commit**



# 2.`npm link`的使用

在这里，我们有两个项目，一个是`npm-link-module`，是我们要开发的npm模块,另一个是`npm-link-example`,是我们要运行npm模块的项目

### 首先，进入我们的`npm-link-module`项目，执行npm link

```bash
cd npm-link-module
npm link
```

### 然后，进入`npm-link-example`项目，执行 npm link npm-link-module

```ruby
cd npm-link-example
npm link npm-link-module
```

`npm-link-module`会被链接到 `npm-link-example/node_modules`下面

OK，链接创建完成

### 解除link

项⽬⽬录下，`npm unlink 模块名 `

模块⽬录下，`npm unlink 模块名`

### tips：

link时需要在要link的目录和引用link的目录都操作一下（且操作有一点不一样）







