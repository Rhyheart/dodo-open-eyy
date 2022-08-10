<p align="center">
  <a href="https://open.imdodo.com">
    <img src="https://open.imdodo.com/hero.png" width="200" height="200" alt="dodo-open">
  </a>
</p>

<div align="center">

  # dodo-open-eyy

  _✨ 基于最新 易语言 开发，中文编程极大的降低了开发门槛。 ✨_

  <a href="https://github.com/dodo-open/dodo-open-eyy/blob/main/LICENSE">
    <img src="https://img.shields.io/github/license/dodo-open/dodo-open-eyy" alt="license">
  </a>
  <a href="https://github.com/dodo-open/dodo-open-eyy/releases">
    <img src="https://img.shields.io/github/v/release/dodo-open/dodo-open-eyy?color=blueviolet&include_prereleases"
      alt="release">
  </a>

</div>

## 项目介绍

- 项目内包含完整的SDK源码以及SDK调用实例，请放心使用！

- 您既可以下载SDK源码，自行编译生成模块，然后项目内引用，亦可以直接引用官方编译好的模块进行引用，请参考下方 [示例项目](#示例项目)

## 开发工具

[易语言](https://www.eyuyan.la/cate/25.html)

- 请下载最新版版本进行开发

## 示例项目

[dodo.open.client](https://github.com/dodo-open/dodo-open-eyy/blob/main/src/dodo.open.client.e)

- 创建一个控制台程序
- 引用易语言模块 [dodo.open.sdk](https://github.com/dodo-open/dodo-open-eyy/blob/main/src/dodo.open.sdk.ec)
- 入口方法使用以下代码
- 启动控制台程序
- 机器人所在群内发送"菜单"即可查看示例功能

```

.版本 2

.程序集 Main

.子程序 _启动子程序, 整数型, , 本子程序在程序启动后最先执行
.局部变量 openApiOptions, OpenApiOptions
.局部变量 openApiService, OpenApiService
.局部变量 openEventOptions, OpenEventOptions
.局部变量 openEventService, OpenEventService
.局部变量 eventProcessService, DemoEventProcessService


' 接口配置
openApiOptions.BaseApi ＝ “接口地址”
openApiOptions.ClientId ＝ “机器人唯一标识”
openApiOptions.Token ＝ “机器人鉴权Token”

' 接口服务
openApiService.Init (openApiOptions)

' 事件处理服务，可自定义，只要继承EventProcessService基类即可
eventProcessService.Init (openApiService)

' 事件服务
openEventOptions.IsReconnect ＝ 真
openEventOptions.IsAsync ＝ 真
openEventService.Init (openApiService, eventProcessService, openEventOptions)

' 开始接收事件消息
openEventService.ReceiveAsync ()

标准输入 ()

返回 (0)

```

## 核心代码

#### [OpenApiService](https://github.com/dodo-open/dodo-open-eyy/blob/main/src/dodo.open.sdk.e)

此类封装了接口相关调用逻辑

#### [OpenEventService](https://github.com/dodo-open/dodo-open-eyy/blob/main/src/dodo.open.sdk.e)

此类封装了事件相关接收逻辑

#### [EventProcessService](https://github.com/dodo-open/dodo-open-eyy/blob/main/src/dodo.open.sdk.e)

此基类封装了事件相关处理逻辑，用户只需要创建自己的处理类（例如：[DemoEventProcessService](https://github.com/dodo-open/dodo-open-eyy/blob/main/src/dodo.open.sdk.e)）并继承此基类，即可自定义处理逻辑

继承后，需要重写Connected、Disconnected、Reconnected、Exception核心方法，其他事件方法可以选择性重写！

**注意：ReceivedInternal请勿重写，否则其他事件方法将全部失效！**
