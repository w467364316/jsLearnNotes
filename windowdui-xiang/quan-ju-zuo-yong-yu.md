# 全局作用域

* 因为window扮演者ECMAScript中Global对象的角色，因此所有全局作用域中声明的变量函数都会变成window对象的属性和方法。

```
var age = 29;
console.log(window.age) //29
console.log(this.age)  // 29
```

* 定义的全局变量不能通过delete删除，但是直接在window对象定义的变量属性能够使用delete删除

  * ```
    var age = 29;
    window.color = 'red'

    delete window.age  //返回false 表示不能删除
    delete window.color //返回true 表示正常删除
    ```

    因为直接定义的全局变量属性，它的\[\[configurable\]\]特性为false，所以不能使用delete删除

* 尝试访问未声明的变量会抛出错误，但是如果直接使用window对象查询，可以知道某个可能未声明的变量是否存在

  * ```
    var newValue = oldValue  //报错
    var newValue = window.oldValue  //newValue的值为undefined
    ```



