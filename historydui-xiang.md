# history

该对象保存着用于上网的历史记录，从窗口被打开的那一刻算起，因为history是window对象的属性，所有每个浏览器窗口，每个标签乃至每个框架，都有自己的history对象与特地的window对象关联。

虽然无法得知用户浏览过得URL，但是可以听过go\(\)方法实现后退和前进

go\(\) 接受一个参数，

* 如果是正值数值则前进 go\(1\) 前进一页 go\(2\)前进两页
* 负值则后退 go\(-1\)
* 如果传递的是字符串，那么就会挑战到历史记录中包含该字符串最近的一个，可能后退，也可能前进。

另外可以使用back\(\)和forward\(\)方法来代替go\(\)的后退和前进操作。

history对象还有一个length属性，保存着历史记录的数量。这个数量包括所有的历史记录，即向前向后的记录。对于加载到窗口标签页或者框架中的第一个页面而言，history.length等于0，可以由此判断用户是否一开始就打开了你的页面。

```
if (history.length == 0) {
    //用户一开始就打开了你的界面
}
```



