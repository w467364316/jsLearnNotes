HTML5新增的一些功能，即便js被禁用或者由于种种原因未能加载，也可以确保基本的验证。



## 1 必填字段

使用required特性表示该表单字段是必填字段

```
<input type='text' required>
```



## 2 其他输入类型

H5为input的type类型添加了几个值，比如emial url等来定义文本输入框应该输入的类型。



## 3 数值范围

H5定义了其他的基于数字的类型，number,range,datetime,datetime-local date month week time等



## 4 输入模式

通过pattern属性定义一个正则规则来验证文本输入的是否匹配。



## 5 检测有效性

使用checkValidity\(\)方法检测表单中的某个字段是否有效。根据之前设定的约束，比如必填属性或者是跟pattern是否匹配，如果有效则返回true，无效则返回false。

```js
        if (!target.checkValidity()) {
          alert('请输入正确的数值')
          target.select()
          return;
        }
```

与checkValidity（）方法简单的相比字段是否有效，validity属性会告诉你为什么字段有效或者无效。



## 6 禁用验证

通过设置novalidate属性，告诉表单不进行验证。



