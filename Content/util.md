## 2.6 	util类
一般的常用方法

|函数|函数说明|返回值|参数
|-------|--------------|-------|----|
|addEventListener|添加一个事件|none|util.addEventListener(eventType, callback)
|clearAllEvents|清除场景内的所有事件|none|util.clearAllEvents()
|clearAllTimers|清除所有的计时器，无需指定计时器ID|none|util.clearAllTimers()
|clearInterval|清除setInterval方法生成的计时器，需指定计时器ID|none|util.clearInterval(intervalID)
|clearScriptObjects|清除场景内由脚本创建的对象,包含物体,GUI等|none|util.clearScriptObjects()
|clearTimeout|清除setTimeout方法生成的计时器，需指定计时器ID|none|util.clearTimeout(timeoutID)
|downloadTexture|将一个外部url材质图片载入至场景内|none|util.downloadTexture({json}）
|downloadTextures|将多个外部url材质图片载入至场景内|none|util.downloadTextures({json}）
|randomColor|生成一个RGBA类型的随机颜色值|RGBA类型的颜色值|util.randomColor()
|randomFloat|生成给定范围内一随机浮点数|float类型随机结果|util.randomFloat(a,b)
|randomInt|生成给定范围内一随机整数|int类型随机结果|util.randomInt(a,b)
|randomVector3|生成一个Vector3类型的随机空间向量|Vector3类型的空间向量|util.randomVector3(randius)
|setInterval|计时器记满后执行回调函数，而后计时器清零再次计时，循环往复，返回number类型的计时器ID|int类型的计时器ID|util.setInterval(callback,tickTime)
|setRenderCallback|每帧执行一次回调函数|none|util.setRenderCallback(callback)
|setTimeout|计时器记满后执行回调函数，返回number类型的计时器ID|int类型的计时器ID|util.setTimeout(callback,delayTime)
### util.addEventListener(eventType,callback)
添加一个事件
**参数说明**
eventType:string类型；待添加的事件类型，支持类型有：click,dblclick,mouseup,mousedown,mousemove,drag,dragstart,dragend,keydown,keyup,resize
callback:function类型；回调函数，事件发生时执行该函数
**示例**
util.addEventListener("click", function(event) {object.create("FF2A3E364B1E4B928891E05A9279C7A7", event.pos);}); //添加一个鼠标点击事件，鼠标被点击后在点击位置处创建一个物体
util.clearAllEvents()
清除场景内的所有事件
**参数说明**
none
**示例**
util.clearAllEvents() //结合以上**示例**，执行后以上事件被清除
util.clearAllTimers()
清除所有的计时器，无需指定计时器ID
**参数说明**
none
**示例**
util.clearAllTimers() //清除所有的计时器
util.clearInterval(intervalID)
清除setInterval方法生成的计时器，需指定计时器ID
**参数说明**
intervalID number类型；需要清除的计时器ID
**示例**
util.clearInterval(2) //清除ID为2的计时器，此时对应的setInterval方法中的回调函数将不再被执行
util.clearScriptObjects()
清除场景内由脚本创建的对象,包含物体,GUI等
**参数说明**
none
**示例**
gui.createButton("按钮", Rect(100, 100, 200, 50), function() {});
object.create("AB052B5B646E4A48B9C045096FF9B088");
util.clearScriptObjects() //清除场景内由脚本创建的按钮和箱子
util.clearTimeout(timeoutID)
清除setTimeout方法生成的计时器，需指定计时器ID
**参数说明**
timeoutID：number类型；需要清除的计时器ID
**示例**
util.clearTimeout(1) //清除ID为1的计时器，此时对应的setTimeout方法中的回调函数将不再被执行
util.downloadTexture({json}）
将一个外部url材质图片载入至场景内
**参数说明**
{json}：json类型；包含url、success执行函数
**示例**
var earth = object.create("B723E9E1B279467EBC9433D30D35F683", Vec3(0, 5, 0));
util.downloadTexture({
"url": "http://img1.juimg.com/141102/330507-141102164G965.jpg",
"success": function(texture) {
var earthMat = util.createMaterial(texture);
earth.setMaterial(earthMat); }}); //创建一个正方体，载入单一外部贴图资源，成功后执行函数并将资源传入函数，函数将创建材质对象earthMat，并设置earth的材质为earthMat（此贴图资源由模模搭技术人员制作，自定义贴图的制作和使用方法请咨询官网技术人员）
util.downloadTextures({json}）
将多个外部url材质图片载入至场景内
**参数说明**
{json}：json类型；包含url、success执行函数
**示例**
var earth = object.create("9f5681fe55674ce9b617f9fa23d9729b", Vec3(0, 5, 0)); //创建地球
var moon = object.create("9f5681fe55674ce9b617f9fa23d9729b",Vec3(0, 7, 0),Vec3(0.2, 0.2, 0.2)); //创建月球
util.downloadTextures({
"url": "http://www.3dmomoda.com/mmdclient/script/examples/demos/earth_moon.zip",
"success": function(textures) {
var earthMat = util.createMaterial(textures["Earth.jpg"]);
earth.setMaterial(earthMat);
var moonMat = util.createMaterial(textures["Moon.jpg"]);
moon.setMaterial(moonMat);}}); //载入外部贴图资源包，成功后执行函数并将资源传入函数，函数将创建材质对象earthMat、moonMat，并分别设置地球、月球的材质为earthMat、moonMat（此贴图资源包由模模搭技术人员制作，自定义贴图的制作和使用方法请咨询官网技术人员）
util.randomColor()
生成一个RGBA类型的随机颜色值
**参数说明**
none
**示例**
obj.setColor(util.randomColor()) //将obj（物体）的颜色设置为一个RGBA类型的随机颜色值，比如：RGBA(0.443,0.345,0.456,1.000)
util.randomFloat(a,b)
生成给定范围内一随机浮点数
**参数说明**
a：float类型；随机范围最小值
b：float类型；随机范围最大值
**示例**
var d = util.randomFloat(1,3) //随机生成1（包含）至3（包含）范围内的一浮点数
util.randomInt(a,b)
生成给定范围内一随机整数
**参数说明**
a：int类型；随机范围最小值
b：int类型；随机范围最大值
**示例**
var c = util.randomInt(1,10) //随机生成1（包含）至10（包含）范围内的一整数
util.randomVector3(randius)
生成一个Vector3类型的随机空间向量
**参数说明**
randius：number类型；控制随机向量的半径范围
**示例**
util.randomVector3(1) //在空间（-1至1,-1至1,-1至1）的正方形空间内随机生成空间向量
util.setInterval(callback,tickTime)
计时器记满后执行回调函数，而后计时器清零再次计时，循环往复，返回number类型的计时器ID
**参数说明**
callback：function类型；计时器记满后执行该函数
tickTime：number类型；计时器时长，单位ms
**示例**
var b=util.setInterval(function() {print("time over again!")}, 3000) //每隔3s打印信息“time over again!”
util.setRenderCallback(callback)
每帧执行一次回调函数
**参数说明**
callback：function类型；每帧执行一次
**示例**
util.setRenderCallback(function(){
var obj = object.create("AB052B5B646E4A48B9C045096FF9B088");
obj.addGravity(3);
}) //每帧创建一个箱子，并添加3千克重力
util.setTimeout(callback,delayTime)
计时器记满后执行回调函数，返回number类型的计时器ID
**参数说明**
callback：function类型；计时器记满后执行该函数
delayTime：number类型；计时器时长，单位ms
**示例**
var a=util.setTimeout(function() {print("time over!")}, 3000) //计时3s，超时后打印信息“time over!”