# 1.typeScript的优势

### 1）编译过程排除一些错误

### 2）更好的代码提示

### 3） 



# 2.

1).ts 指定函数返回类型

```typescript
function sum(a:number,b:number):number{
	return a+b
}
```

2)字面量类型

```typescript
let a:10 = 10
let b:10|20|30
```

3)联合类型

```typescript
let a:string|boolen
```

4)

`unknown `是类型安全的`any`

5) 类型断言

```typescript
let s = e as string
let s2 = <string>f
```

6)限定变量为对象，可指定对象中可包含的属性

```typescript
let b:{name:string,age?:number,[propNamae:string]:any}
b= {name:'sxy'}
```

```typescript
let f:(a:number,b:number)=>number
```

7)数组声明

```typescript
let arr = number[]
let g:Array<number>
```

8)元组

```typescript
let t:[string,number]
```

9)枚举

10）类型别名

type str = string



# 3.TS编译设置

1）自动编译单个文件

```bash
tsc XX.ts -w
```

加上 `-w`表示watch，文件修改时自动编译

2）自动编译所有文件

创建`tsconfig.json`

运行

```bash
tsc -w
```

tsconfig.json是ts编译器的配置文件，`tsc -w`的运行基于它，ts编译器可以根据他的信息对代码进行编译

a).`include`用来指定那些ts文件需要被编译

b.)`exclude`指定不需要被编译的文件目录,默认值，["node_modules","bower_components","jspm_packages"]

 `** `表示任意目录

`*`表示 任意文件

c)`compilerOptions`，编译器选项

d）`target`指定ts被编译为的ES的版本

e）`module` 指定ts被编译为的ES的模块化方案

f)`lib`指定要用到的库，一般情况下不要修改

h) `outDir` 指定编译后文件所在目录

i）`outFile` 如果指定，ts所有全局作用域会被编译并合并到此文件

j）`allowJs` 是否对js文件进行编译，默认为否

k）`checkJS`是否检查js语法是否符合TS语法规范 默认false

l）`removeComments` 是否移除注释

m）`noEmit`是否输出编译文件 

n)`noEmitOnError`当有错误时不输出编译文件

o) `alwaysStrict` 用来设置编译后的文件是否使用严格模式

p）`noImplicitAny` 不允许隐式的any类型，默认false

q)`noImplicitThis` 不允许不明确的类型，默认false

r）`strictNullChecks`  严格检查空值

避免控制报错的一种写法

```typescript
let box1 = document.getElementById('box1')
if(box1!==null){
  box1.addEventListener('click',function(){
    alert('box1 clicked')
  })
}
```

```typescript
let box1 = document.getElementById('box1')
box1?.addEventListener('click',function(){
  alert('box1 clicked')
})
```

s）`strict` 所有严格检查的总开关



# 4.webpack编译Ts

`npm init -y`,`-y`可以不用慢慢设置，直接使用默认设置

### 1）`npm i -D webpack webpack-cli typescript ts-loader`

### 2)   添加`webpack.config.js`

```js
const path = require('path')

module.exports = {
  //指定入口文件
  entry:"./src/index.ts",
  
  //指定打包文件目录
  output:{
    //指定打包文件的目录
    path:path.resolve(__dirname,'dist'),
    //打包后的文件名
    filename:"bundle.js"
  },
  
  //指定webpack打包时要使用的模块
  module:{
    //指定要加载的规则
    rules:[
      {
        //test指定的是规则生效的文件
        test:/\.ts$/,
        //要使用的loader
        use:'ts-loader',
        /排除文件
        exclude:/node_modules/
      }
    ] 
  }
}
```

### 3）`tsconfig.json`

```bash
tsc -init
```

或手动创建`tsconfig.json`

```json
{
  "compilerOptions":{
    "module":"commonjs",
    "target":"es5",
    "strict":true
  }
}
```





