# 原型式继承

借助原型基于已有的对象创建新对象

```
function object(o) {
    function F () {}
    F.prototype = o;
    return new F()
}

var person = {
    name: '123',
    age: 12
}

var p = object(person)
console.log(p.name) // '123'
```

将传入的对象作为原型

ECMAScript5 新增Objecct.create\(\) 方法规范了原型继承，接受两个参数

1. 第一个参数为将被作为原型的对象
2. 第二参数为要为新对象定义额外的属性的对象
   1. 格式与defineproperties的第二个参数一致
      1. ```js
         var person = {
             name:'123'
         }
         Object.create(person,{
             age: {
                 value: 12,
                 emuerable: true
                 ...
             }
         })
         ```



