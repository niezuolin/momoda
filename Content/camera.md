##2.1 	camera类
用于管理场景内的摄像机对象

|函数	|函数说明	|返回值	|参数|
|-------|--------------|-------|----|
|changeTo2D|场景模式改变至2维（顶视）|none|camera.changeTo2D()|
|changeTo3D|场景模式改变至3维|none|camera.changeTo3D()|
|getEyePos|获取当前摄影机位置|none|camera.getEyePos()|
|getTargetPos|获取摄影机的注视点|none|camera.getTargetPos()|
|fit|摄影机聚焦在给定物体上|none|camera.fit(obj)|
|flyTo|摄影机以给定的时间飞向给定的位置和注视点，完成后执行给定函数|none|camera.flyTo({json})|
|lookAt|设置摄影机的注视点|none|camera.lookAt(pos)|
|setPosition|设置摄影机位置|none|camera.setPosition(pos)|
|stopFlying|摄影机停止在触发该函数时所在位置、注视点，通常与camera.flyTo结合使用|none|camera.stopFlying()|

### camera.changeTo2D()
场景模式改变至2维（顶视）
**参数说明**
none
**示例**
camera.changeTo2D()  //场景模式改变至二维（顶视），如当前为二维则无变化
###camera.changeTo3D()
场景模式改变至3维
**参数说明**
none
**示例**
camera.changeTo3D()  //场景模式改变至三维，如当前为三维则无变化
###camera.getEyePos()
获取当前摄影机位置
**参数说明**
none
**示例**
print(camera.getEyePos());  //打印摄影机位置信息
###camera.getTargetPos()
获取摄影机的注视点
**参数说明**
none
**示例**
print(getTargetPos());  //打印摄影机的注视点信息
###camera.fit(obj)
摄影机聚焦在给定物体上
**参数说明**
obj：object类型；待聚焦的物体
**示例**
var obj = object.create("AB052B5B646E4A48B9C045096FF9B088"); 
camera.fit(obj);  //创建一个箱子obj，摄影机聚焦在obj（物体）上，聚焦后摄影机注视点为物体中心点，摄影机位置基于物体大小计算得来，且位于X轴负向、Y轴正向、Z轴正向位置上
###camera.flyTo({json})
摄影机以给定的时间飞向给定的位置和注视点，完成后执行给定函数
**参数说明**
{json}：json类型；包含位置、注视点、飞行时间、执行函数
**示例**
camera.flyTo({
"eye":Vector3(2,3,4),
"target":Vector3(3,4,5),
"time":2.0,
"complete":function(){print("OK!")}})  //经历2s时间摄影机由原位置飞向(2,3,4)、注视点变更为(3,4,5)，完成后打印信息“OK!”
###camera.lookAt(pos)
设置摄影机的注视点
**参数说明**
pos：Vector3类型；摄影机的注视点
**示例**
camera.lookAt(obj.center);  //将摄影机的注视点设置为obj（物体）的中心点
###camera.setPosition(pos)
设置摄影机位置
**参数说明**
pos：Vector3类型；摄影机位置
**示例**
camera.setPosition(Vector3(0,1,2));  //将摄影机位置设置为(0,1,2)
###camera.stopFlying()
摄影机停止在触发该函数时所在位置、注视点，通常与camera.flyTo结合使用
**参数说明**
none
**示例**
camera.flyTo({
"eye":Vector3(2,3,4),
"target":Vector3(3,4,5),
"time":2.0,
"complete":function(){print("OK!")}}) //经历2s时间摄影机由原位置飞向(2,3,4)、注视点变更为(3,4,5)，完成后打印信息“OK!”
gui.createButton("执行", Rect(10, 50, 200, 50), function() {camera.stopFlying();}) //在屏幕中创建一个按钮，点击按钮后摄影机停止在按钮点击时刻所在位置、注视点
