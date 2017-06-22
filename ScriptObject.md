## 2.5 	ScriptObject类
用于对场景内已存在物体添加脚本

|函数|函数说明|返回值|参数
|-------|--------------|-------|----|
|Start	|目前使用范围局限在物体脚本中，脚本执行时仅执行一次该方法	|none	|function |Start({script}) 
|Update	|目前使用范围局限在物体脚本中，脚本执行时每帧执行一次该方法	|none	|function Update({script})
### function Start({script}) 
目前使用范围局限在物体脚本中，脚本执行时仅执行一次该方法
**参数说明**
{script}：函数体；待执行的函数体
**示例**


```
AutoRtate = {
 speed : 0,
 objOption : null,
 function Start() {this.speed = util.randomFloat(1, 8);}
 function Update() {this.objOption.yaw(this.speed); }}
// 创建脚本类，定义脚本类的speed属性、objOption属性，脚本可以包含Start和Update等内部方法，这些方法会被系统自动调用，Start方法将被执行1次，Update方法将每帧执行一次
 var obj = object.create("AB052B5B646E4A48B9C045096FF9B088", Vector3(2.5, 0, 0));//添加箱子
 var script = obj.addScript(AutoRtate,"rotation"); //为箱子添加脚本，脚本命名为"rotation"，便于removeScript方法调用，返回脚本对象
 script.objOption = obj;//为脚本对象的属性objOption赋值，用于将脚本与箱子进行关联，此时脚本对象可以通过Update方法，让箱子以speed的速度以y轴为轴心进行旋转
```


### function Update({script})
目前使用范围局限在物体脚本中，脚本执行时每帧执行一次该方法
**参数说明**
{script}：函数体；待执行的函数体
**示例**


```
同Start函数案例
```


