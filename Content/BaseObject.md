##2.4 	BaseObject类
用于对场景内已存在物体进行具体操作

|函数|函数说明|返回值|参数
|-------|--------------|-------|----|                                     
|addGravity|为指定对象添加重力（质量）|none|BaseObject.addGravity(mass)
|addScript|为指定对象添加脚本|ScriptObject类型的已添加脚本|BaseObject.addScript(script, name)
|addTail|为指定对象添加光尾，通常与movePath方法协同使用，可用来增强物体视觉效果|none|BaseObject.addTail({json})
|clone|复制一个已存在的对象|BaseObject类型的已复制对象|BaseObject.clone()
|destroy|删除一个已存在的对象|BaseObject类型的已复制对象|BaseObject.destroy()
|getPosition|获取指定对象的位置|Vector3类型的空间向量|BaseObject.getPosition()
|getScale|获取指定对象的尺寸|Vector3类型的空间向量|BaseObject.getScale()
|movePath|使指定对象按参数给定的方式移动|none|BaseObject.movePath({json})
|moveTo|使指定对象以给定时间移动至给定空间位置|none|BaseObject.(pos,time)
|pitch|使指定对象按X轴正向旋转给定角度|none|BaseObject.pitch(degree)
|playAnim|使指定对象执行物体动画|none|BaseObject.playAnim(animName)
|removeScript|移除指定对象上的脚本|none|BaseObject.removeScript(name)
|roll|使指定对象按Z轴正向旋转给定角度|none|BaseObject.roll(degree)
|setAnimSpeed|设置指定对象的物体动画速度|none|BaseObject.setAnimSpeed(speed)
|setColor|设置指定对象的颜色|none|BaseObject.setColor(color)
|setColorFlash|设置指定对象闪烁状态和方式|none|BaseObject.setColorFlash(enable, color,time)
|setPickEnabled|设置指定对象的选取可用状态，通常配合鼠标的拖拽事件使用|none|BaseObject.setPickEnabled(enable)
|setPosition|设置指定对象的空间位置(x,y,z坐标)|none|BaseObject.setPosition(x,y,z)
|setPositionXZ|设置指定对象的水平位置(x,z坐标)|none|BaseObject.setPositionXZ(x,z)
|setPositionY|设置指定对象的垂直位置(y坐标)|none|BaseObject.setPositionY(y)
|setScale|设置指定对象的尺寸|none|BaseObject.setScale(x,y,z)
|setTransparent|设置指定对象的透明度|none|BaseObject.setTransparent(trans)
|stopAnim|停止指定对象的物体动画|none|BaseObject.stopAnim()
|stopMoving|停止指定对象的移动状态|none|BaseObject.stopMoving()
|transformPoint|转换指定对象的相对坐标为绝对坐标|Vector3类型的绝对坐标点|BaseObject.transformPoint(pos)
|translate|使指定对象移动相对位移|Vector3类型|BaseObject.translate(pos)
|yaw|使指定对象按Y轴正向旋转给定角度|none|BaseObject.yaw(degree)

###BaseObject.addGravity(mass)
为指定对象添加重力（质量）
**参数说明**
mass：float类型；对象重力（质量）大小，单位kg
**示例**


```
var obj = object.create("AB052B5B646E4A48B9C045096FF9B088");
obj.addGravity(3.5) //定义了一个箱子对象，并为箱子添加了3.5千克的重力
```


###BaseObject.addScript(script, name)
为指定对象添加脚本
**参数说明**
script：Script类型；脚本对象内容
name：string类型；脚本对象的名字
**示例**


```
AutoRtate = {
speed : 0,
objOption : null,
function Start() {this.speed = util.randomFloat(1, 8);}
function Update() {this.objOption.yaw(this.speed); }}
// 创建脚本类，定义脚本类的speed属性、objOption属性，脚本可以包含Start和Update等内部方法，这些方法会被系统自动调用，Start方法将被执行1次，Update方法将被循环调用
var obj = object.create("AB052B5B646E4A48B9C045096FF9B088", Vector3(2.5, 0, 0));//添加箱子
var script = obj.addScript(AutoRtate,"rotation"); //为箱子添加脚本，脚本命名为"rotation"，便于removeScript方法调用，返回脚本对象
script.objOption = obj;//为脚本对象的属性objOption赋值，用于将脚本与箱子进行关联，此时脚本对象可以通过Update方法，让箱子以speed的速度以y轴为轴心进行旋转
```


###BaseObject.addTail({json})
为指定对象添加光尾，通常与movePath方法协同使用，可用来增强物体视觉效果
**参数说明**
{json}：json类型；包含光尾的开始宽度、结尾宽度、光尾颜色、持续时间
**示例**


```
var obj = object.create("AB052B5B646E4A48B9C045096FF9B088");// 创建箱子
var path = Vector3List();
for (var degree = 0; degree < 360; degree += 10)
path.Add(Vec3(Math.Cos(degree*Math.Deg2Rad)*10,0.5,Math.Sin(degree*Math.Deg2Rad)*10));
//生成了36个空间向量点组成的向量表，该表可以近似看成一个半径10米的圆
obj.movePath({
"path": path,
"time": 10,
"lookPos": Vector3.zero,
"loopType": "loop"
}); // 沿以上路径移动箱子，总时间为10秒，移动过程中物体始终指向（0,0,0），完成后循环移动
obj.addTail({
"startWidth": 0.6,
"endWidth":0,
"color":Color.red,
"time": 5
}); // 添加一个光尾，开始宽度为0.6米，结尾宽度为0米，颜色为红色，持续时间为5秒。
```


###BaseObject.clone()
复制一个已存在的对象
**参数说明**
none
**示例**
var obj = object.create("AB052B5B646E4A48B9C045096FF9B088");
var obj2=obj.clone();
obj2.yaw(45) //创建一个箱子，赋值给obj对象变量，使用clone方法复制一个箱子赋值给obj2对象变量，复制的箱子以y轴正向旋转45度
BaseObject.destroy()
删除一个已存在的对象
**参数说明**
none
**示例**


```
var obj = object.create("AB052B5B646E4A48B9C045096FF9B088");
gui.createButton("删除",Rect(10,100,100,20),function(){obj.destroy()}) //创建一个箱子，创建一个删除按钮，点击按钮后，箱子被从场景中删除
```


###BaseObject.getPosition()
获取指定对象的位置
**参数说明**
none
**示例**


```
var obj = object.create("AB052B5B646E4A48B9C045096FF9B088");
print(obj.getPosition()) //创建一个箱子，打印箱子的位置信息
```


###BaseObject.getScale()
获取指定对象的尺寸
**参数说明**
none
**示例**

```
var obj = object.create("AB052B5B646E4A48B9C045096FF9B088");
print(obj.getScale()) //创建一个箱子，打印箱子的尺寸信息
```


###BaseObject.movePath({json})
使指定对象按参数给定的方式移动
**参数说明**
{json}：json类型；包含移动的路径、移动总时间、指向点、是否循环
**示例**


```
var obj = object.create("AB052B5B646E4A48B9C045096FF9B088");// 创建箱子
var path = Vector3List();
for (var degree = 0; degree < 360; degree += 10)
path.Add(Vec3(Math.Cos(degree*Math.Deg2Rad)*10,0.5,Math.Sin(degree*Math.Deg2Rad)*10));
//生成了36个空间向量点组成的向量表，该表可以近似看成一个半径10米的圆
obj.movePath({
"path": path,
"time": 10,
"lookPos": Vector3.zero,
"loopType": "loop"
}); // 沿以上路径移动箱子，总时间为10秒，移动过程中物体始终指向（0,0,0），完成后循环移动
```


###BaseObject.moveTo(pos,time)
使指定对象以给定时间移动至给定空间位置
**参数说明**
pos：Vector3类型，移动的目标位置
time：float类型；移动过程所消耗的时间
**示例**


```
var obj = object.create("AB052B5B646E4A48B9C045096FF9B088");
obj.moveTo(Vector3(10, 0, 0), 5.0) //创建一个箱子，使箱子用5秒时间运动至空间(10, 0, 0)位置
```


###BaseObject.pitch(degree)
使指定对象按X轴正向旋转给定角度
**参数说明**
degree：float类型；旋转的角度
**示例**


```
var obj = object.create("AB052B5B646E4A48B9C045096FF9B088");
obj.pitch(45) //创建一个箱子，使箱子以X轴为轴心，正向旋转45度（符合左手定理，即拇指方向沿X轴正向，则四指弯曲方向为旋转方向）
```


###BaseObject.playAnim(animName)
使指定对象执行物体动画
**参数说明**
animName：string类型；物体动画的名称
**示例**


```
var obj = object.create("0bcba8ca78734b64a3dae3eb699a913c");
gui.createButton("奔跑", Rect(100, 100, 100, 30), function() {obj.playAnim("奔跑");}); //创建一个卡通人物，创建一个按钮，点击按钮后卡通人物执行物体动画"奔跑"
```


###BaseObject.removeScript(name)
移除指定对象上的脚本
**参数说明**
name：string类型；脚本对象的名字
**示例**


```
AutoRtate = {
speed : 0,
objOption : null,
function Start() {this.speed = util.randomFloat(1, 8);}
function Update() {this.objOption.yaw(this.speed); }}
// 创建脚本类，定义脚本类的speed属性、objOption属性，脚本可以包含Start和Update等内部方法，这些方法会被系统自动调用，Start方法将被执行1次，Update方法将被循环调用
var obj = object.create("AB052B5B646E4A48B9C045096FF9B088", Vector3(2.5, 0, 0));//添加箱子
var script = obj.addScript(AutoRtate,"rotation"); //为箱子添加脚本，脚本命名为"rotation"，便于removeScript方法调用，返回脚本对象
script.objOption = obj;//为脚本对象的属性objOption赋值，用于将脚本与箱子进行关联，此时脚本对象可以通过Update方法，让箱子以speed的速度以y轴为轴心进行旋转
gui.createButton("移除脚本", Rect(100, 100, 100, 30),function(){obj.removeScript("rotation")}) //创建一个按钮，点击按钮后箱子的脚本被移除
```


###BaseObject.roll(degree)
使指定对象按Z轴正向旋转给定角度
**参数说明**
degree：float类型；旋转的角度
**示例**


```
var obj = object.create("AB052B5B646E4A48B9C045096FF9B088");
obj.roll(45) //创建一个箱子，使箱子以Z轴为轴心，正向旋转45度（符合左手定理，即拇指方向沿Z轴正向，则四指弯曲方向为旋转方向）
```


###BaseObject.setAnimSpeed(speed)
设置指定对象的物体动画速度
**参数说明**
speed：float类型；物体动画的速度
**示例**


```
var obj = object.create("0bcba8ca78734b64a3dae3eb699a913c");
gui.createButton("奔跑", Rect(100, 100, 100, 30), function() {obj.playAnim("奔跑");}); //创建一个卡通人物，创建一个按钮，点击按钮后卡通人物执行物体动画"奔跑"
gui.createButton("加速", Rect(100, 150, 100, 30), function() {obj.setAnimSpeed(4.5)}) //创建一个按钮，点击按钮后卡通人物的物体动画速度被设置为4.5
```


###BaseObject.setColor(color)
设置指定对象的颜色
**参数说明**
color：Color类型；颜色值
**示例**


```
var obj = object.create("FF2A3E364B1E4B928891E05A9279C7A7", Vector3(0, 0, 0));
obj.setColor(Color.blue); //创建一个箱子，设置箱子的颜色为蓝色
```


###BaseObject.setColorFlash(enable, color,time)
设置指定对象闪烁状态和方式
**参数说明**
enable：boolen类型；闪烁是否开启
color：color类型；闪烁的颜色值
time：float类型；闪烁一次所花时间
**示例**


```
obj = object.create("FF2A3E364B1E4B928891E05A9279C7A7", Vector3(4, 0, 0));
obj.setColorFlash(true, Color.green,2.5); //创建一个箱子，设置闪烁状态为可用，每2.5秒箱子闪烁为绿色，周而复始
```


###BaseObject.setPickEnabled(enable)
设置指定对象的选取可用状态，通常配合鼠标的拖拽事件使用
**参数说明**
enable：boolen类型；选取可用状态
**示例**


```
var obj = object.create("AB052B5B646E4A48B9C045096FF9B088");//创建一个箱子
var dragObj = null; // 记录拖拽对象

util.addEventListener("dragstart", function(event) {
if (event.obj && event.button == 0) {
dragObj = event.obj;
dragObj.setPickEnabled(false)
camera.enableRot = false; }});// 添加一个"开始拖拽"事件，箱子被鼠标左键"开始拖拽"时，设置箱子的"选取可用状态"为false(以此避免箱子被循环拖拽）
util.addEventListener("drag", function(event) {
if (dragObj && event.button == 0)
dragObj.pos = event.pos;}); // 添加一个"拖拽过程中"事件
util.addEventListener("dragend", function(event) {
if (dragObj && event.button == 0) {
dragObj.setPickEnabled(true);
dragObj = null;
camera.enableRot = true;}}); //添加一个"拖拽结束"事件，设置箱子的"选取可用状态"为true(以此使得箱子可以被再次选取）
```


###BaseObject.setPosition(x,y,z)
设置指定对象的空间位置(x,y,z坐标)
**参数说明**
x：float类型；空间中x轴坐标
y：float类型；空间中y轴坐标
z：float类型；空间中z轴坐标
**示例**


```
var obj = object.create("AB052B5B646E4A48B9C045096FF9B088");
obj.setPosition(0, 5, 0); //创建一个箱子，将箱子空间位置设置为(0,5,0)
```


###BaseObject.setPositionXZ(x,z)
设置指定对象的水平位置(x,z坐标)
**参数说明**
x：float类型；空间中x轴坐标
z：float类型；空间中z轴坐标
**示例**


```
var obj = object.create("AB052B5B646E4A48B9C045096FF9B088");
obj.setPositionXZ(1,1); //创建一个箱子，将箱子水平位置（x轴坐标,z轴坐标）设置为(1,1)
```


###BaseObject.setPositionY(y)
设置指定对象的垂直位置(y坐标)
**参数说明**
y：float类型；空间中y轴坐标
**示例**


```
var obj = object.create("AB052B5B646E4A48B9C045096FF9B088");
obj.setPositionY(5); //创建一个箱子，将箱子垂直位置(y轴坐标)设置为(5)
```


###BaseObject.setScale(x,y,z)
设置指定对象的尺寸
**参数说明**
x：float类型；对象在x轴方向长度
y：float类型；对象在y轴方向长度
z：float类型；对象在z轴方向长度
**示例**


```
var obj = object.create("AB052B5B646E4A48B9C045096FF9B088");
obj.setScale(1,2,3); //创建一个箱子，设置箱子在x轴、y轴、z轴方向的长度分别为1,2,3
```


###BaseObject.setTransparent(trans)
设置指定对象的透明度
**参数说明**
trans：float类型；对象的透明度（范围：0~1）
**示例**


```
var obj = object.create("AB052B5B646E4A48B9C045096FF9B088");
obj.setTransparent(0.5); //创建一个箱子，设置箱子的透明度为0.5
```


###BaseObject.stopAnim()
停止指定对象的物体动画
**参数说明**
none
**示例**


```
var obj = object.create("0bcba8ca78734b64a3dae3eb699a913c");
gui.createButton("奔跑", Rect(100, 100, 100, 30), function() {obj.playAnim("奔跑");}); //创建一个卡通人物，创建一个按钮，点击按钮后卡通人物执行物体动画"奔跑"
gui.createButton("停止", Rect(100, 150, 100, 30), function() {obj.stopAnim()}); //创建一个按钮，点击按钮后卡通人物停止物体动画奔跑
```


###BaseObject.stopMoving()
停止指定对象的移动状态
**参数说明**
none
**示例**


```
var obj = object.create("AB052B5B646E4A48B9C045096FF9B088");
obj.moveTo(Vector3(10, 0, 0), 5.0) //创建一个箱子，使箱子用5秒时间运动至空间(10, 0, 0)位置
gui.createButton("停止", Rect(100, 150, 100, 30), function() {obj.stopMoving()}); //创建一个按钮，点击按钮后箱子停止移动
```


###BaseObject.transformPoint(pos)
转换指定对象的相对坐标为绝对坐标
**参数说明**
pos：Vector3类型；待转换的空间坐标
**示例**


```
var obj1 = object.create("AB052B5B646E4A48B9C045096FF9B088",Vector3(1,2,3));
var obj2 = object.create("AB052B5B646E4A48B9C045096FF9B088",obj1,Vector3(4,5,6));
print(obj2.transformPoint(Vector3(7,8,9))); //创建一个箱子obj1,坐标为(1,2,3)；创建另一个箱子obj2，父对象为obj1，坐标为(4,5,6)；此时obj1由于没有设置父对象，则绝对坐标为(1,2,3)，由于obj2设置父对象为obj1，则绝对坐标为父对象坐标与相对坐标相加(1,2,3)+(4,5,6)=(5,7,9)，transformPoint(7,8,9)后，转换相对坐标为绝对坐标(5,7,9)+(7,8,9)=(12,15,18),打印信息结果应为(12,15,18)
```


###BaseObject.translate(pos)
使指定对象移动相对位移
**参数说明**
pos：Vector3类型；相对位移值
**示例**


```
var obj = object.create("81807868C78141BFB2E93275AC3ABB39");
var Button1= gui.createButton("translate", Rect(100, 200, 80, 50), function() {
obj.translate(Vector3(1, 0, 1))});
var Button2= gui.createButton("setPosition", Rect(100, 300, 80, 50), function() {
obj.setPosition(Vector3(1, 0, 1))}); //创建了一个推土机；创建2个按钮，点击按钮分别执行translate、setPosition方法,可见translate会使推土机移动相对位置(1, 0, 1)，而setPosition会使推土机移动至绝对位置(1, 0, 1)
```


###BaseObject.yaw(degree)
使指定对象按Y轴正向旋转给定角度
**参数说明**
degree：float类型；旋转的角度
**示例**


```
var obj = object.create("AB052B5B646E4A48B9C045096FF9B088");
obj.yaw(45) //创建一个箱子，使箱子以Y轴为轴心，正向旋转45度（符合左手定理，即拇指方向沿Y轴正向，则四指弯曲方向为旋转方向）
```





