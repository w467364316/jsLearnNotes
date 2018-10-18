```js
function handleResponse(response){
          alert("You􏵑re at IP address " + response.ip + ", which is in " +
          response.city + ", " + response.region_name);
}
var script = document.createElement("script");
script.src = "http://freegeoip.net/json/?callback=handleResponse";   //指定回调函数名
document.body.insertBefore(script, document.body.firstChild);
```

缺点为：

* 从其他域中访问，不是很安全
* 判断jsonp是否失败不同意。



