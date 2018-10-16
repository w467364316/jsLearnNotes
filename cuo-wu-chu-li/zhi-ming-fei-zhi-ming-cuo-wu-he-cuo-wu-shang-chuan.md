区分致命和非致命错误的方式大致是看会不会对用户的主要操作产生影响。



在我们预测会发生错误的地方，使用try-cathc语句，在捕获到错误的时候，可以将错误直接上传到服务器，可以通过img的src形式上传错误。

```js
 function logError(sev, msg){
        var img = new Image();
        img.src = "log.php?sev=" + encodeURIComponent(sev) + "&msg=" +
                  encodeURIComponent(msg);
}
```



