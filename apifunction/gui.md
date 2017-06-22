## 2.3 	gui类
用于管理场景内的图形界面对象

|函数|函数说明|返回值|参数
|-------|--------------|-------|----|
|createBox|创建一个矩形GUI对象|object类型的已创建矩形|gui.createbox(text,rect)
|createButton|创建一个按钮GUI对象|object类型的已创建按钮|gui.createButton(text,rect,callback)
|createLabel|创建一个标签GUI对象|object类型的已创建标签|gui.createLabel(text, rect)
|createToggle|创建一个复选框GUI对象|object类型的已创建复选框|gui.createToggle(checked,text,rect,callback)
|load|载入外部的GUI资源|none|gui.load(url,callback)

###gui.createbox(text,rect)
创建一个矩形GUI对象
**参数说明**
text：string类型；创建的矩形GUI对象的显示文本
rect：rect类型；创建的矩形GUI对象的位置和大小
**示例**


```
var obj=gui.createBox("矩形1", Rect(100, 200, 80, 50),function(){print("ok!")}); //创建一个矩形GUI对象，位置位于窗口左侧100像素，窗口上侧200像素，大小为左右80像素，上下50像素；
```


### gui.createButton(text,rect,callback)
创建一个按钮GUI对象
**参数说明**
text：string类型；创建的按钮GUI对象的显示文本
rect：rect类型；创建的按钮GUI对象的位置和大小
callback：function类型；回调函数，创建的按钮GUI对象被点击后执行该函数
**示例**


```
var Button1= gui.createButton("按钮1", Rect(100, 200, 80, 50), function() {
print("您点击了按钮1");}); //创建一个按钮GUI对象，位置位于窗口左侧100像素，窗口上侧200像素，大小为左右80像素，上下50像素；按钮被点击会打印调试信息“您点击了按钮1”
```


### gui.createLabel(text, rect)
创建一个标签GUI对象
**参数说明**
text：string类型；创建的标签GUI对象的显示文本
rect：rect类型；创建的标签GUI对象的位置和大小
**示例**


```
gui.createLabel("标签1", Rect(100, 200, 80, 50)); //创建一个标签GUI对象，位置位于窗口左侧100像素，窗口上侧200像素，大小为左右80像素，上下50像素
```


###gui.createToggle(checked, text, rect, callback)
创建一个复选框GUI对象
**参数说明**
checked：boolean类型；创建的复选框GUI对象的选中状态
text：string类型；创建的复选框GUI对象的显示文本
rect：rect类型；创建的复选框GUI对象的位置和大小
callback：function类型；回调函数，创建的复选框GUI对象状态改变时执行该函数
**示例**


```
gui. createToggle ("复选框1", Rect(100, 200, 80, 50), function() {
print("您改变了复选框状态");}); //创建一个复选框GUI对象，位置位于窗口左侧100像素，窗口上侧200像素，大小为左右80像素，上下50像素；复选框状态改变时执行回调函数，打印调试信息“您改变了复选框状态”
```


### gui.load(url,callback)
载入外部的GUI资源
**参数说明**
url：string类型；载入外部资源的路径
callback：function类型；回调函数，资源载入后执行该函数
**示例**


```
var url = "http://www.3dmomoda.com/mmdclient/script/examples/demos/scifi_ui.bundle"
gui.load(url, function(){print("外部资源载入成功！")}); //载入指定url的外部GUI资源，载入后执行回调函数，打印调试信息“外部资源载入成功”（此GUI界面由模模搭技术人员制作，自定义GUI界面的制作和使用方法请咨询官网技术人员）
```

