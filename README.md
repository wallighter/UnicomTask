<div align="center">
<h1 align="center">UnicomTask</h1>
<img src="https://img.shields.io/github/issues/srcrs/UnicomTask?color=green">
<img src="https://img.shields.io/github/stars/srcrs/UnicomTask?color=yellow">
<img src="https://img.shields.io/github/forks/srcrs/UnicomTask?color=orange">
<img src="https://img.shields.io/github/license/srcrs/UnicomTask?color=ff69b4">
<img src="https://img.shields.io/github/search/srcrs/UnicomTask/main?color=blue">
<img src="https://img.shields.io/github/v/release/srcrs/UnicomTask?color=blueviolet">
<img src="https://img.shields.io/github/languages/code-size/srcrs/UnicomTask?color=critical">
</div>

# 简介

👯✨😄📫

联通手机营业厅自动完成每日任务，领流量、签到获取积分等，月底流量不发愁。

开源不易，如果本项目对你有帮助，那么就请给个star吧。😄

# 目录

- [简介](#简介)
- [目录](#目录)
- [功能](#功能)
- [使用方式](#使用方式)
  - [Github Actions（推荐）](#github-actions推荐)
    - [1.fork本项目](#1fork本项目)
    - [2.准备需要的参数](#2准备需要的参数)
    - [3.将参数填到Secrets](#3将参数填到secrets)
    - [4.开启Actions](#4开启actions)
    - [5.进行一次push操作](#5进行一次push操作)
  - [腾讯云函数（推荐）](#腾讯云函数推荐)
    - [1.fork本项目](#1fork本项目-1)
    - [2.准备需要的参数](#2准备需要的参数-1)
    - [3.将参数填到Secrets](#3将参数填到secrets-1)
    - [4.部署](#4部署)
- [通知推送方式](#通知推送方式)
  - [1.邮箱](#1邮箱)
  - [2.钉钉机器人](#2钉钉机器人)
  - [3.TgBot机器人](#3tgbot机器人)
- [同步上游代码](#同步上游代码)
- [申明](#申明)
- [参考项目](#参考项目)

# 功能

* [x] 沃之树领流量、浇水(12M日流量)
* [x] 每日签到(1积分+翻倍4积分+第七天1G流量日包)
* [x] 天天抽奖，每天三次免费机会(随机奖励)
* [x] 游戏中心每日打卡(连续打卡，积分递增至最高7，第七天1G流量日包)
* [x] 游戏中心宝箱100M任务(100M日流量+随机奖励并翻倍)
* [x] 4G流量包看视频、下软件任务(90M+150M七日流量)
* [x] 每日领取100定向积分 
* [x] 积分抽奖，每天最多抽30次(中奖几率渺茫)
* [x] 冬奥积分活动(第1和7天，可领取600定向积分，其余领取300定向积分,有效期至下月底)
* [x] 获取每日1G流量日包(截止日期暂时不知道)
* [x] 邮件、钉钉、Tg推送运行结果

# 使用方式

## Github Actions（推荐）

### 1.fork本项目

项目地址：[srcrs/UnicomTask](https://github.com/srcrs/UnicomTask)

![](https://draw-static.vercel.app/UnicomTask/fork本项目.gif)

### 2.准备需要的参数

手机号、服务密码、`appId`。

其中`appId`的获取:

+ 安卓用户可在文件管理 --> `Unicom/appid` 文件中获取。

+ 苹果用户可抓取客户端登录接口获取。
> `https://m.client.10010.com/mobileService/login.htm`
 
### 3.将参数填到Secrets

在`Secrets`中的`Name`和`Value`格式如下：

Name | Value
-|-|-
USERS_COVER | config.json中内容

将`config.json`中内容复制下来，按照要求填写添加到`Secrets`中，如若选填内容不想配置，需将该行删除。如只想基本功能，无需通知和用积分抽奖，应填写如下内容：

```json
[
    {
        "username": "18566669999",
        "password": "123456",
        "appId": "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
    }
]
```

注意`json`格式，最后一个要删掉逗号。建议在填写之前，使用[json校验工具](https://www.bejson.com/)进行校验。

注意：不要将个人信息填写到仓库`config.json`文件中（不要动这个文件就没事），以免泄露。

多账号，参考[关于多账号的使用方式](https://github.com/srcrs/UnicomTask/discussions/16)

![](https://draw-static.vercel.app/UnicomTask/将参数填到Secrets中.gif)

### 4.开启Actions

默认`Actions`处于禁止状态，在`Actions`选项中开启`Actions`功能，把那个绿色的长按钮点一下。如果看到左侧工作流上有黄色`!`号，还需继续开启。

![](https://draw-static.vercel.app/UnicomTask/开启Actions.gif)

### 5.进行一次push操作

`push`操作会触发工作流运行。

删除掉`README.md`中的😄即可。完成后，每天早上`7:30`将自动完成每日任务。

![](https://draw-static.vercel.app/UnicomTask/进行一次push操作.gif)
