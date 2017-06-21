# 2	API类参考
##2.1 	camera类
用于管理场景内的摄像机对象

|函数	|函数说明	|返回值	|参数|
|-------|--------------|-------|----|
|changeTo2D|场景模式改变至2维（顶视）|none|camera.changeTo2D()
|changeTo3D|场景模式改变至3维|none|camera.changeTo3D()
|getEyePos|获取当前摄影机位置|none|camera.getEyePos()
|getTargetPos|获取摄影机的注视点|none|camera.getTargetPos()
|fit|摄影机聚焦在给定物体上|none|camera.fit(obj)
|flyTo|摄影机以给定的时间飞向给定的位置和注视点，完成后执行给定函数|none|camera.flyTo({json})
|lookAt|设置摄影机的注视点|none|camera.lookAt(pos)
|setPosition|设置摄影机位置|none|camera.setPosition(pos)
|stopFlying|摄影机停止在触发该函数时所在位置、注视点，通常与camera.flyTo结合使用|none|camera.stopFlying()|
### camera.changeTo2D()
场景模式改变至2维（顶视）
**参数说明**
none
**示例**


```
camera.changeTo2D()  //场景模式改变至二维（顶视），如当前为二维则无变化
```


###camera.changeTo3D()
场景模式改变至3维
参数说明
none
示例


```
camera.changeTo3D()  //场景模式改变至三维，如当前为三维则无变化
```


