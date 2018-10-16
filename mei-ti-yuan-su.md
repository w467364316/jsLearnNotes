HTML5主要新增加了vido和audio这两个媒体元素。

* 必须制定src属性。
* 因为浏览器不一定支持全部的格式，所以可以使用source元素指定不同格式的文件。
  * ```js
    <!-- 嵌入视频 -->
     <video id="myVideo">
    <source src="conference.webm" type="video/webm; codecs='vp8, vorbis'">
     <source src="conference.ogv" type="video/ogg; codecs='theora, vorbis'">
      <source src="conference.mpg">
      Video player not available.
    </video>
    ```

通过audio和video的属性方法和事件，我们可以通过操作他们的属性方法和监听事件来创建自定义的播放器。



## audio类型

audio元素还有一个原生的Audio构造函数，可以在任何时候播放音频。从同为DOM元素的角度来看，Audio与Image相似，但是Audio只要创建一个新实例，传入音频文件就可以播放。

下载完之后调用play（）播放音频。





