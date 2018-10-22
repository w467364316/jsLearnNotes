### 迭代器 \(待定\)

迭代器也是一个对象，他能迭代一系列值并每次返回其中一个值。

调用Iterator构造函数，配合next\(\)方法，返回一个数组：

* 如果迭代的是数组，那么每次返回的数组，第一项为值的索引，第二项为值
* 如果迭代的是对象，那么返回的数组第一项是key，第二项为值。



### 数组领悟（待定）



### 解构赋值

从一组值中挑出一或多个值，然后把他们分别赋值给独立的变量。

```js
    var colors = ['red','blue','yellow'];
    var [,color2] = colors;
    console.log(color2); // blue

    var person = {
      name:'123',
      age:20
    }
    var {age,name} = person;
    console.log(name+''+age);  //123 20
```









