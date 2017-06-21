2.4 	BaseObject类
用于对场景内已存在物体进行具体操作

|函数|函数说明|返回值|参数
|-------|--------------|-------|----|                                     
|addGravity|为指定对象添加重力（质量）|none|BaseObject.addGravi
|addScript|为指定对象添加脚本|ScriptObject类型的已添加脚本|Base
|addTail|为指定对象添加光尾，通常与movePath方法协同使用，可用来
|clone|复制一个已存在的对象|BaseObject类型的已复制对象|BaseObje
|destroy|删除一个已存在的对象|BaseObject类型的已复制对象|BaseOb
|getPosition|获取指定对象的位置|Vector3类型的空间向量|BaseObjec
|getScale|获取指定对象的尺寸|Vector3类型的空间向量|BaseObject.g
|movePath|使指定对象按参数给定的方式移动|none|BaseObject.movePa
|moveTo|使指定对象以给定时间移动至给定空间位置|none|BaseObject.
|pitch|使指定对象按X轴正向旋转给定角度|none|BaseObject.pitch(de
|playAnim|使指定对象执行物体动画|none|BaseObject.playAnim(animN
|removeScript|移除指定对象上的脚本|none|BaseObject.removeScript
|roll|使指定对象按Z轴正向旋转给定角度|none|BaseObject.roll(degr
|setAnimSpeed|设置指定对象的物体动画速度|none|BaseObject.setAni
|setColor|设置指定对象的颜色|none|BaseObject.setColor(color)   
|setColorFlash|设置指定对象闪烁状态和方式|none|BaseObject.setCo
|setPickEnabled|设置指定对象的选取可用状态，通常配合鼠标的拖拽?
|setPosition|设置指定对象的空间位置(x,y,z坐标)|none|BaseObject.
|setPositionXZ|设置指定对象的水平位置(x,z坐标)|none|BaseObject.
|setPositionY|设置指定对象的垂直位置(y坐标)|none|BaseObject.set
|setScale|设置指定对象的尺寸|none|BaseObject.setScale(x,y,z)   
|setTransparent|设置指定对象的透明度|none|BaseObject.setTranspa
|stopAnim|停止指定对象的物体动画|none|BaseObject.stopAnim()    
stopMoving|停止指定对象的移动状态|none|BaseObject.stopMoving() 
transformPoint|转换指定对象的相对坐标为绝对坐标|Vector3类型的绝
translate|使指定对象移动相对位移|Vector3类型|BaseObject.transla
yaw|使指定对象按Y轴正向旋转给定角度|none|BaseObject.yaw(degree)

