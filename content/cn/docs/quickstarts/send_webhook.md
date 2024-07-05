---
title: "发送 webhook"
date: 2024-07-02T16:50:00+08:00
weight: 20
---

在这里，学习如何使用 `nanhook` 将 webhook 事件发送到用户的终点。

终点可以是第三方服务商，例如企业微信群机器人、飞书自定义机器人、钉钉自定义机器人，也可以是触发其他服务的 webhook 事件。

![](/docs/quickstarts/send_webhook.png)

#### 准备工作

* `nanhook cloud` 帐户。如果您没有帐户，请登录 `控制台` ，[创建一个帐户](https://dashboard.nanhook.com/login)。
* 用于接收 webhook 事件的后端终点。

#### 步骤：

1. 新增入口，入口是 webhook 监听事件，配置 webhook 事件如何进入系统。
    * 用 `nanhook` 生成的入口网址，提供给您的提供商，接收 webhook 事件。
1. 新增终点，填写终点网址：用来传递 webhook 事件内容的最终目的地。
    * 终点网址接收 HTTP 请求并响应 200 表示成功收件。
1. 新增路由，连接“入口”和“终点”。
    * 路由是入口、终点和可选规则组成的，它定义了 webhook 的数据流程，从收件到派送到终点。

就这样，发往入口网址的所有 webhook 事件现在都将传递到路由对应的终点，详细日志可以在[控制台查看](https://dashboard.nanhook.com/observability/requests)。