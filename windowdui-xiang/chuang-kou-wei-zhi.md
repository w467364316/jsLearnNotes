# 窗口位置

IE safari opera chrome都提供了screenLeft和screenTop属性，分别表示窗口相对于屏幕左边和上边的位置。Firfox则是提供了screenX和screenY表示窗口的位置。基于特殊性，可以如下方式获取这两个属性：

```
var Left = (typeof window.screenLeft == 'number')?window.screenLeft:window.screenX;
var top = (typeof window.screenTop == 'number')?window.screenTop:window.screenY;
```

* moveTo\(\)和moveBy\(\)
  * 将窗口移动到相应的位置，前者是移动到指定的x,y，后者是往左往下移动x,y的距离。
  * 这两个方法一般都被浏览器禁用。而且这两个方法不适用与框架，只能对最外层的window对象使用。



