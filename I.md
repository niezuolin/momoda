## 3.3 	初始化数据接口（I接口）
模模搭服务器部署成功后，场景数据默认为空，需要通过本接口传入初始化数据，传入成功后场景数据将被保存在服务器数据库中。客户端/浏览器每次载入场景时将自动加载这些数据。目前数据传入粒度为单一场景&单一物体。
接口地址
接口访问地址如下，本地部署IP地址为127.0.0.1，网络部署需替换成部署服务器IP。


```
http://127.0.0.1:8080/goods/save
```


**数据规范**
g.sid:场景ID
g.oid:物体ID
g.props:物体初始化数据
支持两种方式的传入：GET方法和POST方法，GET方法仅适合数据量比较少的情况。
**GET方法**
使用GET方法的数据格式如下：


```
http://127.0.0.1:8080/goods/save?g.sid=20170320095733039126770&g.oid=cabinet1&g.props={"Initialized Data":"Initialized Data"}
```


本示例使用GET方法向20170320095733039126770场景内cabinet1物体传入初始化数据{"Initialized Data":"Initialized Data"}
以第三方插件POSTMAN和JavaScript为例调用方法如下：
**POSTMAN示例**
![](/image/image003.png) 
**JavaScript示例**


```
<!DOCTYPE html>
<html>
<head>
<script src="jquery-1.11.1.min.js">
</script>
<script>
$(document).ready(function(){
  $("button").click(function(){
$.get('http://127.0.0.1:8080/goods/save?g.sid=20170320095733039126770&g.oid=cabinet1&g.props={"Initialized Data":"Initialized Data"}',
    function(data) { alert("Data:" + data);}
	);
  });
});
</script>
</head>
<body>

<button>提交数据</button>
</body>
</html>
```


POST方法
使用POST方法的数据格式如下：


```
http://127.0.0.1:8080/goods/save
POSTDATA{
g.sid:20170320095733039126770
g.oid:cabinet1
g.props:{"Initialized Data":"Initialized Data"}
}
```


本示例使用POST方法向20170320095733039126770场景内cabinet1物体传入初始化数据{"Initialized Data":"Initialized Data"}
以第三方插件POSTMAN和JavaScript为例调用方法如下：
POSTMAN示例
![](/image/image005.png) 
JavaScript示例


```
<!DOCTYPE html>
<html>
<head>
<script src="jquery-1.11.1.min.js">
</script>
<script>
$(document).ready(function(){
  $("button").click(function(){
    $.post("http://127.0.0.1:8080/goods/save",
    {
    "g.sid":"20170320095733039126770",
    "g.oid":"cabinet1",
    "g.props":'{"Initialized Data":"Initialized Data"}'    },
    function(data) { alert("Data:" + data);}
	);
  });
});
</script>
</head>
<body>
<button>提交数据</button>
</body>
</html>

```

