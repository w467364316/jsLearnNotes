为了方便操作表格，HTML DOM提供了一些table元素的属性和方法用来创建表格：![](/assets/import12.png)如下代码创建一个列表：

```
var table = document.createElement('table')
table.border = 1;
table.width = '100%'

tbody = document.createElement('tbody')
table.appendChild(tbody)

table.inserRow(0)
table.rows[0].insertCell(0)
table.rows[0].cells[0].appendChild(document.createTextNode('cell 1,1'))
table.rows[0].insertCell(0)
table.rows[0].cells[1].appendChild(document.createTextNode('cell 2,1'))
```



