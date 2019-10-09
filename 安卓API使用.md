[TOC]

**启动页添加脚本**

该脚本为app基础api

```html
<script type="text/javascript" src="cordova.js"></script>
```

> 一下所有脚本都需要在 `deviceready` 事件完成后进行安全调用

*eg:*

```js
document.addEventListener('deviceready', onDeviceReady, false);
```



## 微信API

* 微信分享示例

  https://jasonz1987.github.io/cordova-wechat-docs/docs/usages/share.html



## 支付宝API

```js
// 请求后台获取的带签名支付信息  eg: 
const payInfo = "charset=utf-8&biz_content=%7B%22timeout_express%22%3A%2230m%22%2C%22product_code%22%3A%22QUICK_MSECURITY_PAY%22%2C%22total_amount%22%3A%22100%22%2C%22subject%22%3A%221%22%2C%22body%22%3A%22%E6%88%91%E6%98%AF%E6%B5%8B%E8%AF%95%E6%95%B0%E6%8D%AE%22%2C%22out_trade_no%22%3A%220920175957-1871%22%7D&method=alipay.trade.app.pay&app_id=2016101300676096&sign_type=RSA2&version=1.0&timestamp=2016-07-29+16%3A55%3A53&sign=PYvn23%2FmpyB5Si%2BzaZvvfvQTVWudYO7phn8Lg2Nex36O1BeEbT1AsfR8zTgOPk47aZze%2FH%2BPCxRNPbKVBIs3Obd3WGohP8jOehqlvz1zjLMjdbgwBHZJIGmoAHUc7imrqgcxHGe5m%2B3fF8UCkWeM3qh4jf5FzV4aZOyBccJ1d3yrF4kRzdF4KlYojhTyUVzYh7dQdnUXa6SX5RtG5LlpBdUZfkl5gazm2yqGHf0AKLhvsgTqHziwZsjj8NXszbXy1oXDAnAFDpIPcrccIcn8uSTtG6yBzS3xFEIFKN5z%2BIp3QXs7DEF%2BMLZh5iz66C8AUnzj%2FlL5eVU1TlBeV5XBSA%3D%3D";
cordova.plugins.alipay.payment(payInfo, function success(e){
    dialog.alert("支付成功");
    console.log(e);
},function error(e){
    //TODO 支付失败
    console.log("支付失败" + e.resultStatus);
});
```



## 消息推送

* 示例

https://github.com/katzer/cordova-plugin-local-notifications

* 简单使用

```js
cordova.plugins.notification.local.schedule({
    title: 'My first notification',
    text: 'Thats pretty easy...',
    foreground: true
});
```



## 按键事件

http://cordova.axuer.com/docs/zh-cn/latest/cordova/events/events.html



## 手机定位

http://cordova.axuer.com/docs/zh-cn/latest/reference/cordova-plugin-geolocation/index.html

```js
navigator.geolocation.getCurrentPosition((position) => {
        alert('Latitude: '          + position.coords.latitude          + '\n' +
            'Longitude: '         + position.coords.longitude         + '\n' +
            'Altitude: '          + position.coords.altitude          + '\n' +
            'Accuracy: '          + position.coords.accuracy          + '\n' +
            'Altitude Accuracy: ' + position.coords.altitudeAccuracy  + '\n' +
            'Heading: '           + position.coords.heading           + '\n' +
            'Speed: '             + position.coords.speed             + '\n' +
            'Timestamp: '         + position.timestamp                + '\n');
    },
    (error) => {
        alert('code: '    + error.code    + '\n' +
            'message: ' + error.message + '\n');
    },
    { maximumAge: 3000, timeout: 5000, enableHighAccuracy: true });
```



## 拨打电话

入参：

* arg1：拨打成功回调    function

* arg2:   调用失败   function 

* arg3:   电话号码   string

* arg4:   是否绕过应用选择器  boolean

```js
window.plugins.CallNumber.callNumber(function onSuccess(result){
        $.alert("Success:call number" + result);
    },
    function onError(result) {
        $.alert("Error:call number" + result);
    },
    '13642284429' ,true);
```



检查是否支持拨号

```
window.plugins.CallNumber.isCallSupported((result) => {
    $.alert(`类型：${typeof result}, 值：${result}`);
}, (result) => {
    $.alert(`类型：${typeof result}, 值：${result}`);
});
```



## 状态栏操作

<https://github.com/apache/cordova-plugin-statusbar>

