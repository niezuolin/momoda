## 2.7 	input类
用于判定键盘鼠标的输入状态

|函数|函数说明|返回值|参数
|-------|--------------|-------|----|
|getKey|获取键盘给定键点击状态|boolen类型|getKey(keyCode)
|getKeyDown|获取键盘给定键按下状态|boolen类型|getKeyDown(keyCode)
|getKeyUp|获取键盘给定键弹起状态|boolen类型|getKeyUp(keyCode)
|getMouseButton|获取鼠标给定按钮点击状态|boolen类型|getMouseButton(MouseCode)
|getMouseButtonDown|获取鼠标给定按钮按下状态|boolen类型|getMouseButtonDown(MouseCode)
|getMouseButtonUp|获取鼠标给定按钮弹起状态|boolen类型|getMouseButtonUp(MouseCode)

### input.getKey(keyCode)
获取键盘给定键点击状态
**参数说明**
keyCode：键盘按键编码值，用于区分键盘不同按键
**示例**


```
Player = {  //创建一段脚本类
    obj : null,
    function Update() {
        if (input.getKey(KeyCode.A))  this.obj.yaw(-5); //当键盘点击A键时，人物按y轴负向旋转5度
        if (input.getKey(KeyCode.D))  this.obj.yaw(5); //当键盘点击D键时，人物按y轴正向旋转5度           
        if (input.getKeyDown(KeyCode.R))  this.obj.moveTo(Vector3(3,0,3),2); //当键盘R键被按下时（还未抬起），人物向点(3,0,3)移动 
        if (input.getKeyUp(KeyCode.R))  this.obj.moveTo(Vector3(-3,0,-3),2);  //当键盘R键被抬起时，人物向点(-3,0,-3)移动 
        if (input.getMouseButtonDown(0)) {print("鼠标左键按下");} //当鼠标左键按下时，打印调试信息“鼠标左键按下”
        if (input.getMouseButtonUp(0)) {print("鼠标左键抬起");}  //当鼠标左键抬起时，打印调试信息“鼠标左键抬起”
        if (input.getMouseButtonDown(1)) {print("鼠标右键点击");} }} //当鼠标右键被点击时，打印调试信息“鼠标右键点击”
var obj = object.create("0bcba8ca78734b64a3dae3eb699a913c"); //创建人物
var script = obj.addScript(Player);
script.obj = obj; //为人物添加脚本，并进行关联
camera.enableMove = false;// 关闭摄影机的ASDW
```


### input.getKeyDown(keyCode)
获取键盘给定键按下状态
**参数说明**
keyCode：键盘按键编码值，用于区分键盘不同按键
**示例**


```
同getKey函数案例
```


### input.getKeyUp(keyCode)
获取键盘给定键弹起状态
**参数说明**
keyCode：键盘按键编码值，用于区分键盘不同按键
**示例**


```
同getKey函数案例
```


### input.getMouseButton(MouseCode)
获取鼠标给定按钮点击状态
**参数说明**
MouseCode：鼠标按键编码值，用于区分鼠标不同按键；0为鼠标左键，1为鼠标右键
**示例**


```
同getKey函数案例
```


### input.getMouseButtonDown(MouseCode)
获取鼠标给定按钮按下状态
**参数说明**
MouseCode：鼠标按键编码值，用于区分鼠标不同按键，0为鼠标左键，1为鼠标右键
**示例**


```
同getKey函数案例
```


### input.getMouseButtonUp(MouseCode)
获取鼠标给定按钮弹起状态
**参数说明**
MouseCode：鼠标按键编码值，用于区分鼠标不同按键，0为鼠标左键，1为鼠标右键
**示例**


```
同getKey函数案例
```


