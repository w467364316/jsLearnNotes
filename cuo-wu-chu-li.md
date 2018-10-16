## try-catch代码块

```
try {
    执行可能发生错误的代码
}catch(error) {
    捕获错误
}
```



finally语句

只要写了finally语句之后，不管try catch中是什么代码，finally中的代码一定会执行。但是在IE7中，没有提供catch语句，则finally的语句不会执行。

```
try {
    执行可能发生错误的代码
}catch(error) {
    捕获错误
}finally {

}
```



