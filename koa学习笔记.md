1.koa2洋葱模型



2.koa-router的使用

prefix

allowMethods

3.restful状态码最佳实践

4.koa-body

koa-bodyparser

解析post data携带的数据

5.错误处理

ctx.throw(412,"先决条件错误")

​    koa-json-error

6.koa-parameter

数据校验

ctx.vertifyParams()

7.mongoose

schema 

 用selecte:false隐藏password等数据的返回



put，完整修改，提供完整对象

patch，部分修改，提供一个字段及新的值



8.报错

ctx.throw(404)

ctx.throw(409)



9.登陆逻辑

先校验用户名是否提供及格式是否正确

```js
ctx.vertifyParams({
name:{
type:"string",
  requireed:true
},
Password:{
type:"string",
  requireed:true
}
})
```

校验成功返回则token



10.中间件本质是一个携带ctx，next的函数



11.、验证token

Try{

jsonwebtoken.vertify(token, secret)

Ctx.state.user = 

}catch(err){



})



12.postman 中test

postman中token自动设置

 {{token}}



13.koa-jwt

```
yarn add koa-jwt
```

14.上传图片



15.koa-body优于koa-parser，koa-body支持form和json，文件

```





```

`ctx.upload.files.file`



16.koa-static



17.koa错误处理 `koa-json-error`

```javascript
const error = require('koa-json-error')

app.use(error({
    postFormat: (err, obj) => {
        if (process.env.NODE_ENV === 'production') {
            const {stack, ...rest} = obj
            return rest
        }
        return obj
    }
}))
```

18.monoose schemma

```js
const userSchema = new Schema({

  locations:{
  type:[{type:String}]
  },
  employments:{
    type:[{
      company:{type:String},
      title:{type:String}
    }]
  },
  educations:{
    type:[{
      school:{type:String},
      d:{
        type:enmu
      }
    }]
  }
})

```



19ctx.verifyParams参数为数组

```js
ctx.verifyParams:({
  location:{
    type:'array',
    itemType:"string"
    required:true
  }
})
```

20.mongoose 字段过滤

根据query里的fields决定显示的字段



21.设计restful接口时，务必复数名词后带id隔着再带名词

如

```js
/**====================================
 * GET /users/:userId/spares 喜欢我的（备选）
 * ------------------------------------*/
router.get('/:userId/spares', auth, checkOwner, listSpares);//喜欢我的（备选）
```

不要是

```js
/**====================================
 * GET /users/spares 喜欢我的（备选）
 * ------------------------------------*/
router.get('/spares', auth, checkOwner, listSpares);//喜欢我的（备选）
```

虽然此处userId可以也应该冲state中获取，但router是不知道`:userId`与任意一个别的如`following`,`userInfo`的区别的，可能导致路由失败，且中间间隔一个userId语义上也更合理







