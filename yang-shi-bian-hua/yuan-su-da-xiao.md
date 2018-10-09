## 1 偏移量

元素的可见大小由其高度，宽度，滚动条和边框大小（不包括外边距）。

* offsetHeight   像素为单位，为元素的高度，可见水平滚动条的高度，上线边框的高度。
* offsetWidth 像素为单位，为元素的宽度，可见垂直滚动条的宽度，左右边框的高度
* offsetLeft  元素的左外边框至包含元素的左内边框之间的像素距离
* offsetTop 元素的上外边框至包含元素的上内边框之间的像素距离。
* offsetParent  offsetLeft和offsetTop的取值跟包含元素offsetParen有关

**offsetParent不一定等于parentNode，offsetParent理解为元素外部包含元素中最近的一个有定位（postion）的元素。**

那么求元素对于页面的偏移量就可以使用遍历的方法，自身的offsetLeft不断去加offsetParent的offsetLeft，知道offsetParent为null。

所有的偏移量都是可读的，每次访问都需要重新进行计算，所以应该避免重复的访问。

![](/assets/import17.png)

## 2 客户区的大小

客户区大小（client dimension） 元素内容以及其内边距占用的空间大小

* clientHeight 元素的高度加上上下内边距的高度
*  clientWidth 元素的宽度加上左右内边距的宽度

常用的方式，获取浏览器视口的大小

```
var height = document.documentElement.clientHeight || document.body.clientHeight
var width = document.documentElment.clientWidth || document.bod.clientWidth
```



![](/assets/import16.png)



## 3 滚动大小

包含滚动内容元素的大小。有些元素自带滚动条（html等），其他的一些元素需要通过css的overflow属性进行设置\(overflow : scroll\)。

* scrollHeight 滚动内容的高度
* scrollWidth 滚动内容的宽度
* scrollLeft  被隐藏在内容区域左边的像素。 可以设置来调整滚动的位置
* scrollTop 被隐藏在内容区上方的像素。 可以设置来调整滚动的位置

![](/assets/import15.png)



## 4 确定元素的大小

getBoundingClientRect\(\) 方法，返回一个矩形对象，包含4个属性：left, right,top.bottom,给出了元素在页面中相对于视口的位置。

其中top.bottom都是距离视口顶部的距离，left和right都是距离视口左边距的距离，所以有bottom-top = offsetHeight, right-left = offsetWidth







