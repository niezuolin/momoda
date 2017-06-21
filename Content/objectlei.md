## 2.2 	object类
用于管理场景内的物体对象

|函数|函数说明|返回值|参数
|-------|--------------|-------|----|
|create|创建一个物体|object类型的已创建物体|object.create(bundleId,parentObj, callback,pos,scale)
|createArrowLine|创建一条箭头曲线|object类型的已创建曲线|object.createArrowLine(vertices,{json})
|createCurveLine|创建复杂曲线|object类型的已创建曲线|object.createCurveLine(vertices, bundleOrColorOrMat, parentObj, width, textiling, texOffSet)
|destroyAll|删除由脚本创建的所有对象|none|object.destroyAll()
|find|按uid查找物体|object类型的已存在物体|object.find(uid);

### object.create(bundleId,parentObj, callback,pos,scale)
创建一个物体
**参数说明**
bundleId：string类型；创建物体的ID
parentObj：BaseObject类型；创建物体的父对象
callback：function类型；回调函数，物体被加载后执行
pos：Vector3类型；创建物体的起始位置
scale：Vector3类型；创建物体的初始尺寸
**示例**
```
var obj1 = object.create("AB052B5B646E4A48B9C045096FF9B088",Vector3(1,0,1));
var obj2 = object.create("AB052B5B646E4A48B9C045096FF9B088",obj1,function(){obj1.yaw(45)},Vector3(2,0,1),Vector3(1,2,3)); //创建一个箱子obj1，初始位置为(1,0,1)；创建另一个箱子obj2，父对象为obj1，起始位置位于(2,0,1)，起始尺寸为(1,2,3)，物体被加载后执行回调函数，obj1按y轴正向旋转45度（此时obj2因为父对象是obj1，所以obj1、obj2作为整体在旋转）
```
object.createArrowLine(vertices,{json})
创建一条箭头曲线
参数说明
vertices：array类型或Vector3List类型；创建曲线的点集合（即所有点按次序连接后形成曲线）
{json}：json类型；表形式的参数，包含曲线颜色、箭头颜色
示例
var vecArray2 = [Vector3(0, 1, 20), Vector3(10, 1, 20)];//定义一个空间向量的数组
object.createArrowLine(vecArray2, {
 "color": Color.red,
 "arrowColor": Color.green}); //创建一条带箭头的曲线，起始位置为(0, 1, 20)，终点的位置为(10, 1, 20)，曲线的颜色为红色，曲线的箭头为绿色
object.createCurveLine(vertices, bundleOrColorOrMat, parentObj, width, textiling, texOffSet)
创建一条复杂曲线
参数说明
vertices：array类型或Vector3List类型；创建曲线的点集合（即所有点按次序连接后形成曲线）
bundleOrColorOrMat：string类型或颜色类型；指定材质或指定颜色或
parentObj：BaseObject类型；创建曲线的父对象
width：float类型；创建曲线的宽度
textiling：材质的重复度
texOffSet：材质的偏移度
示例
var vecList = Vector3List();
vecList.Add(Vector3(0,1,0));
vecList.Add(Vector3(10,1,0));
vecList.Add(Vector3(10,1,5));
var curveLine1=object.createCurveLine(vecList, Color.green);// 创建一条曲线curveLine1

var vecArray = [Vector3(0,1,5), Vector3(0,2,15), Vector3(10,4,15), Vector3(10,6,5)];
var curveLine2 = object.createCurveLine(vecArray, "1D2702801708453680664DCABE70890B",curveLine1,2,Vector2(1,2),Vector2(0,0)) //创建一条指定材质的、父对象为curveLine1的、宽度为2、材质重复度为的(1,2)、材质偏移度为(0,0)的曲线
object.destroyAll()
删除由脚本创建的所有对象
参数说明
none
示例
var obj = object.create("AB052B5B646E4A48B9C045096FF9B088"); //创建一个箱子
var vecArray = [Vector3(0,1,5), Vector3(0,2,15), Vector3(10,4,15), Vector3(10,6,5)];
var curveLine1=object.createCurveLine(vecArray, Color.green); //创建一条曲线
gui.createButton("删除", Rect(100, 100, 100, 30), function() {object.destroyAll()}) //创建一个按钮，点击按钮后执行删除对象操作
object.find(uid)
按uid查找物体
参数说明
uid：string类型；物体的uid
示例
var obj = object.find("Object01");
obj.yaw(-45); //查找到uid为"Object01"的物体，并赋值给对象变量obj，obj沿y轴负向旋转45度
