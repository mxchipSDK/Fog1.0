##Description: MQTT连接

* [startMqtt](#1)

* [recvMqttMsg](#2)

* [stopRecvMqttMsg](#3)

* [publish](#4)

* [stopMqtt](#5)

* [subscribe](#6)


##**概述**

	easyMqtt模块封装了标准的mqtt方法，可实现订阅，publish和停止订阅

#**startMqtt**<div id="1"></div>

	打开MQTT，如果未连接成功，则自动重连直到连接上为止。

	startMqtt({params}, callback(ret, err))

##params

host：

- 类型：字符串
- 默认值：无
- 描述：服务器地址，不可为空

username：

- 类型：字符串
- 默认值：无
- 描述：用户名，可为空

password：

- 类型：字符串
- 默认值：无
- 描述：用户密码，可为空


clientID：

- 类型：字符串
- 默认值：无
- 描述：客户端连接mqtt所用到的唯一ID，不可为空


topics：

- 类型：字符串
- 默认值：无
- 描述：订阅的主题，不可为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:true		//是否成功，布尔类型
}
```

err：

- 类型：JSON对象

- 内部字段：
	
```js
{
	msg:""    //错误描述
}
```

##示例代码

```js
var topic = "b574d4b8/c89346918175/out/#";
var host = "api.easylink.io";
var username = "";
var password = "";
var clientID = "clientId-abcdedf";
EasyMqtt.startMqtt({
	host : host,
	username : username,
	password : password,
	clientID : clientID,
	topics : topic
}, function(ret, err) {
	console.log(JSON.stringify(ret));
});
```

##补充说明

	打开MQTT连接

##可用性

	iOS系统，Android系统

	可提供的1.0.0及更高版本


#**recvMqttMsg**<div id="2"></div>

	接收消息

	recvMqttMsg(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

- 内部字段：

```js
{
	subs:		 //消息内容，JSON对象
}
```

err：

- 类型：JSON对象

- 内部字段：

```js
{
	msg:""    //错误描述
}
```

##示例代码

```js
EasyMqtt.recvMqttMsg(function(ret, err) {
	console.log(ret.subs);
});
```

##补充说明

	无

##可用性

	iOS系统，Android系统

	可提供的1.0.0及更高版本


#**stopRecvMqttMsg**<div id="3"></div>

	停止接收消息。

	stopRecvMqttMsg()

##示例代码

```js
EasyMqtt.stopRecvMqttMsg(function(ret, err) {
});
```

##补充说明

	无

##可用性

	iOS系统，Android系统
	
	可提供的1.0.0及更高版本


#**publish**<div id="4"></div>

	向服务发送消息并获取回执

	publish({params}, callback(ret, err))

##params

topic：

- 类型：字符串
- 默认值：无
- 描述：发布消息的主题，不可为空

command：

- 类型：字符串
- 默认值：无
- 描述：发布消息的指令，不能为空

##callback(ret, err)
ret：

- 类型：JSON对象

内部字段：

```js
{
	status:false		//是否成功，布尔类型
}
```

err：

- 类型：JSON对象

- 内部字段：

```js
{
	msg:""    //错误描述
}
```
##示例代码

```js
EasyMqtt.publish({
	topic : "b574d4b8/c89346918175/in/read/",
	command : "{}"
}, function(ret) {
});
```

##补充说明

	发送消息

##可用性

	iOS系统，Android系统

	可提供的1.0.0及更高版本


#**stopMqtt**<div id="5"></div>

	关闭MQTT连接

	stopMqtt(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

- 内部字段：

```js
{
	status:false		//是否成功，布尔类型
}
```

err：

- 类型：JSON对象

- 内部字段：

```js
{
	msg:""    //错误描述
}
```
##示例代码

```js
EasyMqtt.stopMqtt(function(ret, err) {
});
```

##补充说明

	关闭MQTT连接

##可用性

	iOS系统，Android系统

	可提供的1.0.0及更高版本


#**subscribe**<div id="6"></div>

	关闭MQTT连接

	subscribe(topics, callback(ret, err))

##params

topics：

- 类型：字符串
- 默认值：无
- 描述：发布消息的主题，不可为空


##callback(ret, err)

ret：

- 类型：JSON对象

- 内部字段：

```js
{
	status:false		//是否成功，布尔类型
}
```

err：

- 类型：JSON对象

- 内部字段：

```js
{
	msg:""    //错误描述
}
```
##示例代码

```js
EasyMqtt.subscribe("b574d4b8/c89346918175/out/#", function(ret, err) {
});
```

##补充说明

	关闭MQTT连接

##可用性

	iOS系统，Android系统

	可提供的1.0.0及更高版本