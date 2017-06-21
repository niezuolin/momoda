## 2.8 	console类
用于管理控制台

|函数	|函数说明	|返回值	|参数
|-------|--------------|-------|----|
|clear	|清除控制台文本内容	|none	|console.clear()
|log	|在控制台打印指定对象的信息	|none	|console.log(obj)
|show	|控制台显示或隐藏	|none	|console.show(show)
## console.clear()
清除控制台文本内容
**参数说明**
none
**示例**


```
var obj = object.create("AB052B5B646E4A48B9C045096FF9B088");
console.log(obj)
console.clear() //清除控制台文本内容
```


## console.log(obj)
在控制台打印指定对象的信息
**参数说明**
obj：object类型；待打印信息的对象
**示例**


```
var obj = object.create("AB052B5B646E4A48B9C045096FF9B088");
console.log(obj.getScale()) // 创建箱子，打印箱子的尺寸信息
```


## console.show(show)
控制台显示或隐藏
**参数说明**
show：boolean类型；是否显示控制台
**示例**


```
print("这里是控制台")
gui.createButton("显示控制台", Rect(100, 100, 200, 50), function() {console.show(true)});
gui.createButton("关闭控制台", Rect(100, 200, 200, 50), function() {console.show(false)});
```


