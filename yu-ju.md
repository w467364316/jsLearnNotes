# if语句

# while语句

# do-while语句

# for语句

# for-in语句

# label语句

* label语句可以z哎代码中中添加标签，结合for等循环语句来使用
  * 比如在多层for嵌套中，想要在内部for循环中判断然后中断外层的循环，那么就可以将外层使用label定义，这样就可以在内部for中断开
  * ```
    outMost: 
    for (var i = 0;i<10;i++) {
        for (var j = 0;j<10;j++) {
            if (j*i>20) {
                //直接断开外部for的循环
                break outMost;
            }
        }
    }
    ```

# switch语句

* 相比其他语言的不同，switch中case可以使用任何的数据类型（OC中只能使用数值）
  * case跟着的不一定是常量，也可以是表达式或者变量



