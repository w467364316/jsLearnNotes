JavaScript提供一个JSON对象，有两种方法，parse\(\)和stringify\(\)分别用于将字符串解析为js对象和将js对象序列化为JSON字符串。

## 序列化js对象

使用stringify\(\)方法将对象序列化为json字符串，可用参数为三个：

* 第一个参数为要序列化的对象，可以单独只传递第一个参数
* 第二参数可为数组或者函数，称为过滤数组或过滤函数
  * 数组中表示只选取数组中值对应的属性进行序列化
  * 过滤函数接受两个参数，分别为属性名和属性值，对象中的每个键值对都会依次调用，然后通过函数返回一个值，可以用于序列化中修改对象中的值。
* 第三个参数表示字符串缩进，设定了缩进后得到的字符串会自动换行
  * 如果是数值，那么会缩进多少个空格，最大值为10
  * 如果是字符串，那么会以字符串代替空格实现缩进。

```js
var jsonText = JSON.stringify(obj,function(key,value){
        if (key === 'intest') {
          return value.join('-');
        }
        return value;
    },4);
```

**toJSON方法**

可以在 对象中定义toJSON方法，那么在序列化时，就会返回toJSON方法的值。

序列化的顺序：

\(1\) 如果存在 toJSON\(\)方法而且能通过它取得有效的值，则调用该方法。否则，返回对象本身。

\(2\) 如果提供了第二个参数，应用这个函数过滤器。传入函数过滤器的值是第\(1\)步返回的值。

\(3\) 对第\(2\)步返回的每个值进行相应的序列化。

\(4\) 如果提供了第三个参数，执行相应的格式化。

## 解析JSON字符串为对象

使用parse\(\)方法将JSON字符串解析为js对象。可有两个参数：

* 第一个参数为JSON字符串
* 第二参数为还原函数，跟stringify的过滤函数一样，也是接受两个参数，可以对键值对中的值进行一些处理。
  * 比如JSON字符串中有时间格式的字符串，那么可以在还原函数中转变为相应的Date对象等。
  * ```js
        var obj1 = JSON.parse(jsonText,function(key,value){
          if (key === 'intest') {
            return value.split('-');
          }
          return value;
        });
    ```



