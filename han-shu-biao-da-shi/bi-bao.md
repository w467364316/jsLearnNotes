# 闭包

## 函数中作用域链的理解

1. 当函数被创建时，会创建一个预先包含全局变量对象和包含自身函数（如果有的话）的活动对象的作用域链，并保存在函数的\[\[scope\]\]属性中。
2. 当调用函数时，会为函数创建一个执行环境，然后通过复制函数的\[\[scope\]\]属性中的对象构建执行环境的作用域链。
3. 然后一个活动对象，包含函数内定义的变量和方法等，被创建并推入执行环境作用域链的前端。
4. 由此可见，作用域链本质上是一个指向变量对象的指针列表，他只是引用但不实际包含变量对象。无论什么时候在函数中访问一个属性，都会从作用域链中搜索具有相应名字的变量。

代码图示分析如下：

```js
function compare (value1,value2) {

}

var result = compare()
```

![](/assets/import8.png)

一般来说当局部函数执行完毕之后呢，局部活动对象就会销毁，相应的作用域链销毁，内存中就只会存在全局作用域，但是闭包的情况不同。

### 常见闭包：

```js
 function createComparisonFunction(propertyName) {
        return function(object1, object2){
                var value1 = object1[propertyName];
                var value2 = object2[propertyName];
                if (value1 < value2){
                    return -1;
                } else if (value1 > value2){
                    return 1;
                } else {
                    return 0;
            } };
}

var func = createComparisonFunction(name)
func({name:'1'},{name:'2'})
```

分析：

1. createCompaision 函数被调用时会生成一个**执行环境**，其作用域链中包含了**全局变量对象**和**自身的活动对象**。
2. 当匿名函数被返回时，等于是创建匿名函数，那么会预先生成一个包含**全局变量对象**和其外部包含函数**createComprison函数的活动对象**的作**用域链**存在内部属性\[\[scope\]\]中。
3. 匿名函数返回后，createComparison函数执行完毕，执行环境销毁，作用域链销毁，但是自身的**活动对象**不会销毁，因为返回的**匿名函数的作用域链**中有对该活动对象的引用。
4. 当匿名函数被返回赋值给新的变量func调用时，会创建一个**执行环境**，从\[\[scope\]\]属性中的对象复制出来，形成**执行环境的作用域链条**，同时将**自身的活动对象**加入作用域链条顶端。
5. 那么在func函数中访问**propertyName**时，就会从作用域链条中搜寻，最终在**createComparison活动对象**中找到了propertyName变量。
6. 当func执行完毕，return之后，它的执行环境销毁，作用域链条销毁，内存中就只存在**全局变量对象**了。

![](/assets/import9.png)

