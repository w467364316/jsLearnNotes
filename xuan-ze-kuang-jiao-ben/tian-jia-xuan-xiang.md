添加option的两种方式：

1. 使用DOM的方式创建
   1. ```
      var option = document.createElement('option')
      option.inneerText = '123'
      select.appendChild(option)
      ```
2. 使用Option构造函数创建，接受两个参数，第一参数为text温恩，第二个参数为值value，虽然会创建一个实例对象，但是在兼容DOM的浏览器中会返回一个&lt;option&gt;元素。

   1. ```
      var option = new Option('text','value')
      select.appendChild(option)
      ```

3. 第三种添加的方式是先创建option元素，然后调用select的add方法

   1. ```
      var option = new Option('text','value')
      select.add(option,undefined) //最佳方案
      ```

如果想将option添加到其他位置，就应该使用标准DOM技术和insertBefore（）方法



