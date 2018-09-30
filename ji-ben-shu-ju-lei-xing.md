# undefined

* undefined类型只有一个值，一般表示一个变量定义但是没有初始化，那么这个变量的值就是undefined

* typeof的使用

  * 对未初始化的变量使用typeof会返回undefined
  * 对于未定义的变量使用typeof也会返回undefined

# Null类型

* null类型也是只有一个值，一般表示一个空对象指针，所以使用typeof操作时会返回“object”

  * 如果定义的变量用于保存对象，那么最好在初始化是设为null，这样就可以知道该变量以后是用于存放对象的

* undefined和null使用 “ ==”对比是，总是返回true

  * 虽然这里相等，但是他们的用途是有很大的差别的

# Boolean类型

* 只有两个字面值：true和false
  * true和false是区分大小写的
* 其他类型的String Object Number Undefined都是可以转换成对应的boolean值
  * 使用Boolean\(\)将其他类型的数据转换成boolean值
* * | 数据类型 | 转换成true的值 | 转换成false的值 |
    | :--- | :--- | :--- |
    | Boolean | true | false |
    | String | 非空字符串 | 空字符串'' |
    | Number | 任何非零数字值 | 0和NaN |
    | Object | 任何对象 | undefined |

    ```
          所以在if中可以直接用于判断
    ```

# Number类型

* number大致分为十进制，八进制和十六进制
  * 十进制直接表示，八进制以0开头，十六进制以0x开头
  * 在严格模式下，使用八进制和十六进制都会报错
* 浮点数：小数点表示法
* 数值范围
  * 最小值保存在Numer.MIN_VALUE中,最大值保存在Number.MAX\_VALUE中_
  * 如果超过最大纸盒最小值，那么就会转成特殊的infinity和 -infinity
    * infinity是不能参加计算的，确定一个数字是不是有穷的，可以使用isFinite\(\)来判断
* NaN :Not a Number 是一个特殊的数值
  * 任何数除以0都会返回NaN
  * 特点：
    1. 任何涉及NaN的操作返回鬧NaN
    2. NaN和任何值都不相等，包括NaN本身
  * 使用isNaN\(\)函数判断参数是否不为数值
    * 比如使用isNaN\('abs'\)，参数为字符串，转换后也不是数值（‘123’转换后为数值）,那么就会返回true
* 有三个函数可以把非数值转换成数值
  * Number\(\)
  * parseInt\(\)
    * 添加第二个参数为2 8 10 16 可以分别解析2进制 8进制 10进制 16进制的字符串
  * parseFloat\(\)
    * 智能解析十进制

# String类型

* 使用零个或者多个16为unicode组成
* 字符字面量
  * 转义字符串 使用+符号，比如表示\使用  
* 字符串一旦被创建就不可改变，所以只能使用一个新的字符串填充变量
* 转化为字符串
  * toString（）方法，基本数据类型都有一个toString方法
    * 在输出数值是，可以携带参数来表示输出的基数 2 8 10 16进制

# Object类型

* 是一个数据和功能的集合，可以通过new操作符跟上要创建的对象类型来创建。

  * ```
    //以下两种方式等价
    var o = new Object();
    var 0 = new Object;
    ```

* Object是所有对象的基类，每个Object的实例都有以下相同的属性和方法

  * constructor  指向实例的构造函数
  * hasOwnProperty\(propertyName\) 判断给定的属性是否在当前实例中
  * isPrototyeIf\(object\) 用于检查传入的对象是否是传入对象的原型
  * propertyIsEnumerable\(propertyName\) 用于检车给定的属性是否可以使用for-in枚举
  * toLocalString（） 返回对象的字符串表示
  * valueOf\(\) 返回对象的字符串数值或者布尔值表示，通常与toString\(\)方法返回值相同



