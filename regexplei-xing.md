# RegExp类型

* 用来支持正则表达式，使用字面量来创建实例
  * var expression = /pattern/flags  
    * pattern为正则表达式
    * flags为匹配模式，一般有三种
      * g 表示全局模式，并非是发现第一个匹配项就停止
      * i 表示不区分大小写
      * m 表示多行模式，即在到一行文本末尾时继续查找下一行中是否存在于模式匹配的项
* **与其他语言中的正则表达式类似，模式中使用的所有元字符都必须转义。**
* 使用new RegExp\(param1,param2\) 构造函数来定义，有两个参数

  * 第一个参数为正则表达式
  * 第二个参数为匹配模式
  * **注意**：

    * 使用字面量表达式创建的始终会共享一个EegExp实例，因为其实例属性（lastIndex等）不会改变，所以多次调用的话都是使用的同一个实例

      * \`\`\`  
        var re = null,i  
        for \(i =0 ;i&lt;10;i++\) {

        ```
        re = /cat/g;
        re.test('catagfda')
        ```

        }  
        for \(i =0 ;i&lt;10;i++\) {

        ```
        re = new RegExp('cat','g')
        re.test('catagfda')
        ```

        }

        \`\`\`

    * 如上图第一个循环所示，虽然每一次循环re都被赋值，但是他们是共享同一个RegExp实例，所以test\(\)调用第一次会返回true，第二次就为空了。 但是第二个循环因为每一次都是新创建的一个实例，所以每次调用test\(\)都会返回true

    * 而使用构造函数创建的会生成一个新的实例

* RegExp的实例属性

  * gloabal  是否设置了g标志
  * multiLine 是否设置了m标志
  * ignoreCase 是否设置了i标志
  * lastIndex 表示开始搜索下一个匹配项的字符位置，从0开始算起
  * source 将正则表达式按照字面量的形式变成字符串返回

* RegExp的实例方法
  * exec\(\)  接受一个参数作为应用模式的字符串
    * 返回一个数组，包含额外的属性 index和input，index表示匹配项在字符串中的位置，input表示正则表达式的字符串
    * Reg每一次都只会匹配一次，就算设置了全局模式g，也只会执行一次。
      * 如果RegExp没有设置g，只会匹配一次，多次调用始终会返回第一个匹配的内容
      * 如果RegExp设置了g，那么多次调用的时候就会不断的记录上一次匹配到的位置，然后继续进行匹配（也就是会修改RegExp的lastIndex属性，下一次调用时就会默认从lastIndex开始匹配）
  * text（） 方法，在模式与参数匹配的情况下返回true,否则返回false
  * toString\(\)和toLocalString\(\)方法都会以RegExp实例的字面量表达式作为字符串返回
* RegExp的构造函数属性
  * 根据RegExp的构造函数属性，可以获得更加详细的信息



