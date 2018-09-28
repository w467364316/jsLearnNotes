# 私有变量

严格的说js中并没有私有成员的概念，所有的对象属性都是公有的。但是有一个私有变量的概念。

在函数内部定义的变量和方法都可以理解为私有变量，因为不能再外部访问这些变量。

在函数中使用闭包可以访问包含函数中的私有变量，所以把有权访问私有变量和函数的公有方法称为**特权方法**。

在对象上创建特权方法的方式：

1. 在构造函数内部创建访问私有成员的特权方法
2. ```
   function MyObjecct (){
       var number=10;
       function privateFunction () {
            return false   
       }
       this.publicMethod = function () {
           number ++;
           return privateFunction();
       }
   }
   ```



