## 移除初始化数据接口（R接口）

如需修改特定初始化数据，需首先调用本接口移除指定场景&指定物体数据，再重新添加。目前数据移除粒度为单一场景&单一物体。如需移除数据，直接调用本接口。

接口地址

接口访问地址如下，本地部署IP地址为127.0.0.1，网络部署需替换成部署服务器IP。



```
http://127.0.0.1:8080/goods/remove
```



数据规范

sid:场景ID

oid:物体ID

目前本接口仅支持GET方法提交，如下：

GET方法

使用GET方法的数据格式如下:


```

http://127.0.0.1:8080/goods/remove?sid=20170320095733039126770&oid=cabinet1
```



本示例使用GET方法移除20170320095733039126770场景内cabinet1物体的初始化数据。

以第三方插件POSTMAN和JavaScript为例调用方法如下：

POSTMAN示例

![](/image/image008.png)

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

    $.get('http://127.0.0.1:8080/goods/remove?sid=20170320095733039126770&oid=cabinet1',

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


