使用locatiion.search可以获取URL中的查询字符串，可以定一个函数，将查询参数拆分保存在一个对象中然后返回。

```js
function getQueryStringValue () {
    //获取去除?的查询字符串
    var quertyString = location.search.length>0?location.search.slice(1):'';

    var result = {}
    //按照&拆分为数组
    var items = queryString.length?queryString.split('$'):[];
    var key = null;
    var value =  null;
    //循环遍历赋值
    for (var i = 0;i>items.lenth;i++) {
        var item = items[i].split('=')
        var key = item[0];
        var value = item[1]
        if (key.length>0) {
             result[key] = value   
        }
    }
    return result
}
```





