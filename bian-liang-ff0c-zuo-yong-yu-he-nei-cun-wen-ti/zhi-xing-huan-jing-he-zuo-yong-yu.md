# 执行环境和作用域

* 每一个执行环境都有一个对应的变量对象（局部函数中将活动对象作为变量对象），保存着执行环境中定义的所有变量和函数
  * 虽然代码无法访问到，但是解析器会使用这个变量对象进行解析
* 全局执行环境是最外围的一个环境，关联的对象一般是window
* 每一个函数都有自己的执行环境，当执行流进入一个函数时，函数的环境就会被推入一个环境栈中，当函数执行之后，栈再讲环境弹出，把控制权返回给之前的执行环境。
  * 那么可以理解为一段js代码是有一层一层的执行环境，解析器通过对执行环境对应的变量操作，来查询读取对应的变量和函数
* 因此当代码在一个环境中执行时，会创建变量对象的一个作用域链条，保证对执行环境有权访问的变量和函数进行有序的访问。  
  ![](/assets/import.png)如上图中的代码，一共有三个执行环境，一个全局环境，一个changeColor的局部环境，一个swapColors的局部环境。那么对应的作用域链条可以表示为下图所示：  
      ![](/assets/import1.png)

  ```
        window为最低端，swapColors为最前端，那么在代码中要访问变量时，就会先从最近的环境开始查找，如果没有继续往上层查找，知道找到为止，如果全局环境中还是没有，证明该变量未被定义。
  ```

* js中没有块级作用域，而且只有函数才能生成局部执行环境。

  * 没有类似OC中的块级作用域
  * 声明变量
    * 使用var声明的变量会自动被添加到最接近的环境中
    * 如果在函数中定义变量没有使用var定义，那么该变量默认为全局变量。
  * 查询标识符
    * 当在使用变量时，会在作用域链条中不断的往上查询，知道查询到对应的值为止。**但是只能按照作用域链往上查询，不能往下查询**。



