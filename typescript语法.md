# 1.ts面向对象

static 静态属性

readonly 只读属性



# 2.ts构造函数

```typescript
class Dog{
  name:string
  age:number
  constructor(name:string,age:number){
    //this表示当前对象的实例，可以通过this向新建的对象添加属性
    this.name = name
    this.age = age
  }
  bark(){
    //this表示调用方法的对象
    console.log(this.name)
  }
}

const dog1 = new Dog('小黑',4)
const dog2 = new Dog('小白',3)
```

# 3.ts继承

**OCP** ,对扩展开放，对修改封闭

```typescript
(function(){
  class Animal{
    name:string;
    age:number;
    constructor(name:string,age:number){
      this.name=name
      this.age =age
    }
  }
  class Dog extends Animal{
    
  }
  class Cat extends Animal{
    
  }
  
  const dog = new Dog('大黄',5)
  const cat = new Cat('小白',3)
  console.log(dog)
  dog.sayHello()
  console.log(cat)
  cat.sayHello()
  
})()
```

# 4.ts中的super

# 5.ts中的抽象类

抽象类需要被继承，其子类才能实例化。抽象类不能直接实例化

```typescript
abstract class Animal(){
  
  // 抽象方法只能定义在抽象类中，子类必须对抽象方法进行重写
  abstract sayHello()

}
```

# 6.ts中的接口

接口用来定义一个类结构,用来定义一个类中应该包含哪些属性和方法

接口可以在定义类的时候去限制类的结构

接口中的所有的属性都不能有实际的值

接口只定义对象的结构，而不考虑实际值

接口中的所有方法都是抽象方法（抽象类中则抽象方法普通方法都可以）

接口只在ts中，js中不存在

```typescript
interface myInterface{
  name:string
	age:number
}

//实现接口
class MyClass implements myInterface{
  
}
```

其作用类似于

```typescript
let InFa:{name:string,age:number}
```

```typescript
type infa:{name:string,age:number}
```

# 7.ts属性的封装

**public** 可在任意位置修改

**privite** 只能在类内部进行访问

**protected** 受保护属性，只能在当前类和当前类的子类中访问

**ts**中的**getter**、**setter**方法

```typescript
...
class Person{
  private _name:string
  ...
  get name(){
    return this._name
  }
  set name(value:string){
    this._name = value
  }
	...
}

const p = new Person()
console.log(p.name)
p.name='sjk'
...
```

# 8.ts泛型

在定义函数或者类时，如果遇到类型不明确就可以使用泛型

```typescript
functuion fn<T>(a:T):T{
	return T
}
```

可以直接调用具有泛型的函数

```typescript
fn(10); //不指定泛型，ts可以自动对类型进行推断
```

```typescript
fn<string>('hello'); //指定泛型
```

可以有多个泛型

```typescript
function fn<T,K>(a:T,b:K):T{
	return a
}
fn(123,'sjk');
fn('sjk',456);
```

结合接口(**interface**)

```typescript
interface Inter(){
	length:nmuber
}
function fn<T extends Inter>(a:T):number{
  return a.number
}
fn({length:12})
```

类中使用

```typescript
class MyClass<T>{
	name:T;
  constructor(name:T){
  	this.name = name
  }
}
const mc = new MyClass<string>('sxy')
```

