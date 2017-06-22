## 实时数据接口（M接口）

第三方行业应用如需驱动特定3D场景各类信息动态变化，实现实时状态可视化展示，需使用本接口向场景内推送数据，此数据不支持保存，客户端/浏览器重新载入场景后数据必须重新推送。

**接口地址**

接口访问地址如下，本地部署IP地址为127.0.0.1，网络部署需替换成部署服务器IP。


```

http://127.0.0.1:8080/data/putdata
```



**数据规范**



```
JSON数据：param:{" 场景ID ":{"物体ID ":”物体实时数据”}}
```



支持两种方式的传入：GET方法和POST方法，GET方法仅适合数据量比较少的情况。
**GET方法**
使用GET方法的数据格式如下：



```
http://127.0.0.1:8080/data/putdata?param={"20170320095733039126770":{"cabinet1": {"monitoring data":"monitoring data"}}}  
```



本示例使用GET方法向20170320095733039126770场景内cabinet1物体传入实时数据{"monitoring data":"monitoring data"}

以第三方插件POSTMAN和JavaScript为例调用方法如下：

**POSTMAN示例**
![](/image/image009.png)


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

    $.get('http://127.0.0.1:8080/data/putdata?param={"20170320095733039126770":{"cabinet1": {"monitoring data":"monitoring data"}}}',

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
http://127.0.0.1:8080/data/putdata

POSTDATA{

param:{"20170320095733039126770":{"cabinet1":{"monitoring data":"monitoring data"}}}

}
```



本示例使用POST方法向20170320095733039126770场景内cabinet1物体传入实时数据{"monitoring data":"monitoring data"}

以第三方插件POSTMAN和JavaScript为例调用方法如下：

**POSTMAN示例**

![](/image/image011.png)

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

    $.post("http://127.0.0.1:8080/data/putdata",

    {

param:'{"20170320095733039126770":{"cabinet1":{"monitoring data":"monitoring data"}}}'    },

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
