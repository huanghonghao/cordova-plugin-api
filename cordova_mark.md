[TOC]

# Cordova常用命令

* 官网： https://cordova.apache.org
* 官方文档：https://cordova.apache.org/docs/en/latest/guide/overview/index.html
* 中文手册：http://www.dba.cn/book/cordova/CORDOVAJiaoCheng/CORDOVADiYiGeYingYongChengXu.html
* 查看帮助：cordova help
* 查看某个命令的帮助： cordova command help



# 如何进行Cordova项目开发

1. 创建项目
2. 添加平台支持和插件
3. 打包前检查是否满足要求
4. 打包
5. 预览

## 步骤1-创建项目

```bash
cordova create <文件夹名> <包名> <app名>
eg:
cordova create test com.suoju.test testApp
```

**test** 是创建应用程序的目录名称。

**com.suoju.test**是默认的反向域值。 如果可能，您应该使用您自己的域值。

**testApp** 是应用标题、包名

## 步骤2-添加平台支持

您需要在命令提示符下打开您的项目目录。在我们的示例中是 **test**。你应该只选择你需要的平台。为了能够使用指定的平台，您需要安装特定的平台SDK。由于我们在Windows上开发，我们可以使用以下平台。我们还安装了[android SDK](http://www.dba.cn/book/android/) ，因此我们只会为本教程安装Android平台。

添加平台支持：

```
cordova platform add android
```

删除平台支持：

```
cordova platform rm android
```

查看平台支持：

```
cordova platform ls
```



## 步骤3-检查

检查是否满足构建平台要求

```
cordova requirements
```



## 步骤4-构建打包并运行

* 构建并打包，例如要在安卓平台运行，就打包为安卓支持的包

```
cordova build android
```

`build`命令还支持多环境支持打包

```
cordova build android window --debug --device
```

* 运行

使用默认模拟器运行

```
cordova emulate android
```

使用外部模拟器或真实设备

```
cordova run android
```





# 项目热更新

#### 1. 在项目中安装插件

```bash
cordova plugin add cordova-hot-code-push-plugin
```

#### 2. 安装编译和初始化插件

```bash
npm install -g cordova-hot-code-push-cli
```

#### 3. cordova项目的config.xml配置

```xml
<chcp>
        <auto-download enabled="true" />   自动更新默认为true，建议不要关闭 关闭后需要自己手动调用插件的js方法来更新了
        <auto-install enabled="true" />
        <config-file url="https://www.zehuiwenhua.com/jiyifa/www/chcp.json" />   配置文件的目录
        <native-interface version="1" />   外壳的版本，
    </chcp>
```





# 常用插件

* 拨打电话

```powershell
cordova plugin add https://github.com/huanghonghao/CordovaCallNumberPlugin.git
```



* 状态栏工具
* <https://github.com/apache/cordova-plugin-statusbar>

```
cordova plugin add cordova-plugin-statusbar
```



# config.xml 配置

```xml
<!-- 禁止IOS上下拖动 -->
<preference name="DisallowOverscroll" value="true" />
```



## IOS11 webView适配

* https://www.jianshu.com/p/88403ff3b907