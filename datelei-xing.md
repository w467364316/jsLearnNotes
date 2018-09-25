# Date类型

* 创建一个日期对象
  * ```
    var date = new Date() //默认是获取当前时间点
    ```
* 根据给定的时间创建一个日期对象

  * Date.parse\(\) 接受一个字符串作为参数，然后会尝试着转换成对应日期的的毫秒数

    * 然后在使用new Date\(毫秒数\)来创建Date实例

    * 在new Date\(\) 参数直接传递事件字符串，解析器会默认调用Date.parse\(\)方法

      * eg: new Date\("6/12/2018"\)

  * Date.UTC\(\)

    * 同样是返回表示日期的毫秒数，但是参数格式为，年份，基于0的月份，月中的那一天，小时数，分钟，秒以及毫秒数

      * 前两个参数是必须得，没有提供天数则默认为1，如果省略其他参数，则通通假设为0
      * eg: new Date\(2018,6,13\)

    * 同样的，new Date\(\)参数中如果传入的shi跟UTC\(\)方法一样的参数，那么也会默认调用Date.UTC（）方法，只不过是基于本地时间

  * Date.now\(\) 获取当前时间和日期的毫秒数

* 继承自Object的方法

  * 重写了toString toLocalString valueOf 等方法

  * toString\(\) 方法就会返回带有时区信息的日期和时间

  * toLocalString\(\)方法会返回本地带有AM PM给的日期和时间

  * valueOf方法会返回日期的毫秒表示，因此可以方便使用比较操作符进行两个日期的比较

    * ```
      var time = new Date(2007,0,1)
      var time2 = new Date(2007,1,1)
      console.log(time>time2) false
      console.log(time<time2) true
      ```

* 日期格式化方法

  * toDateString\(\)

  * toTimeString\(\)

  * toLocalDateString\(\)

  * toLocalTimeString\(\)

  * toUTCString\(\)

* 其他的一些方法



