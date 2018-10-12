三种方法：

1. 使用removeChild方法，移除节点
2. 使用select的remove\(index\)方法移除节点
3. 将对应的option设置为null

```js
第一种：
select.removeChild(select.options[0])

第二种：
select.remove(0);

第三种：
select.options[0] = null;
```



