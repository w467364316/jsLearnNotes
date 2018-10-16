因为javascript是松散类型的，不像OC等那样对于函数的参数进行类型验证，所以在使用函数时一般会发生几种类型的错误：

* 类型转换错误
* 数据类型错误
* 通信错误

## 类型转换错误

发生在使用某个操作符或者使用其他可能会自动转换值的语言结构上。

```
function concat (str1,str2,str3) {
    var result = str1 + str2;
    if ( str3) {
        result +=str3
    }
    return result;
}
```

在上述中使用if判断str3是否有值，本意应该是判断是否是字符串，但是并不是只有字符串会被自动转换成true。比如数值0，会被转换成false，而数值1则会转换成true。

**对于基本类型，应该使用typeof来确定其类型。**

```
if (typeof str3 == 'string') {
    进行下一步
}
```



## 数据类型错误

```
function getQueryString (url) {
    var pos = url.indexOf('?');  //错误的做法
    if (pos >-1) {
        return pos.substring(pos+1);
    }
    return '';
}
```

如上述代码中所述，应该先判断url是否是字符串。

```
if (typeof url == 'string') {
    //进行其他处理
}
```

直接使用if\(value\)，不仅仅会引发类型转换错误，同样也会引发数据类型错误。

```
function reverseSort (values) {
    if (values) { //错误的判断
        values.sort();
        values.reverse();
    }
}
```

直接if（values）并不能确保values就是数组类型的对象。

另外一个常见的错误就是使用值和null进行对比。同样的也不推荐使用undefine和值进行比较。

另外一种常见错误就是使用某一个特性执行特性检测：

```
if (typeof values.sort == 'function') {}
```

通过判断对象的某个特性是否是函数，是否存在。但是传入的是一个定了sort方法的对象，那么在执行到values.reverse的时候，也会报错。



对于对象的类型应该使用instanceof来判断。

```
if (values instanceof Array) {
    //确保了values是一个数组类型的对象
}
```





## 通信错误

对于传递给服务器的URL中查询字符串，必须要使用encodeURLComponent（）方法进行编码，然后在传递给服务器。







