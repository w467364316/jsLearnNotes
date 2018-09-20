# 基本类型和引用类型

* 基本类型 一般指的是简单的数据段
* 引用类型 一般指的是可能有多个值构成的对象
  * 引用类型是保存在内存中的对象，与其他语言不同，js不允许直接访问内存中的位置，所以应用类型是按引用访问，指向的对象存储在堆内存中
    * js中字符串不属于引用类型，属于基本类型
* 引用类型可以动态的添加删除属性
* 复制变量值
  * 基本类型复制可以理解为是值的赋值，复制之后两个变量相互不影响
  * 引用类型复制其实是引用的复制（指针的复制），复制之后两个对象还是指向同一个对象的内存地址，所以是相互影响的
* 两种类型传递参数
  * 函数的参数传递都是值传递
    * 基本类型的参数会将值传递给函数中一个局部变量，函数结束则销毁
    * 引用类型的参数 也会将值传递给函数中的一个局部变量，但是传递的内存中对象的应用，所以如果在函数内部通过局部变量访问修改内存中的对象，那么也会影响函数的外部（总结： 参数传递是指针作为值进行传递）
* 检测类型： 使用typeof检测基本数据类型是最佳工具，但是检测引用类型时，往往我们需要知道的是是什么类型的对象，因此可以使用instanceof来进行判断
* ```
  var result = person instanceof Object
  ```

  由此来判断person是否是Object的实例

  * 使用instanceof检测基本数据类型的话，会返回false，因为基本数据类型不是对象


