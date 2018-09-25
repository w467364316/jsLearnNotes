# Math对象

Math对象的属性

## Math对象的方法

* min\(\) 和max\(\)
  * 分别是算一组数值中最小和最大的数，都可以接受无限个数值参数
  * 怎么对数组进行最值计算？
    * ```
      使用apply方法，改变this的值进行计算
      Math.min.apply(Math,[1,2,3,4,5])
      ```
* 舍入规则

  * Math.ceil\(\)

    * 向上舍，返回比参数大的最小的整数

  * Math.floor\(\)

    * 向下舍，返回比参数小的最大的整数

  * Math.round\(\)

    * 按照四舍五入规则对参数进行处理

* random（）

  * 选取0-1之间的一个随机数

  * 通常使用方法为 Math.random\(\)\*可能值的总数+第一个可能的值

    * ```
      Math.floor(Math.random()*10+1) 表示从1-10随机选取一个整数
      Math.floor(Math.random()*9+2) 表示从2-10随机算去一个整数
      ```





