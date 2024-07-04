---
title: '接收 webhook'
date: 2024-06-28T17:17:00+08:00
weight: 10
---

在这里，学习如何使用 `nanhook` 接收第一个 webhook 事件。

入口可以是第三方服务商，例如支付宝、企业微信、github，也可以是其他服务触发的 webhook 事件。

![](/docs/quickstarts/receive_webhook.png)

#### 准备工作

* `nanhook cloud` 帐户。如果您没有帐户，可以在[此处创建一个帐户](https://dashboard.nanhook.com/login)。
* 用于接收 webhook 事件的终点 api。

#### 步骤：

1. 新增入口，入口是 webhook 监听事件，配置 webhook 事件如何进入系统。
    * 用 `nanhook` 生成的入口网址，提供给您的提供商，接收 webhook 事件。
1. 新增终点，填写终点网址：用来传递 webhook 事件内容的最终目的地。
    * 终点网址接收 HTTP 请求并响应 200 表示成功收件。
1. 新增路由，连接“入口”和“终点”。
    * 路由是入口、终点和可选规则组成的，它定义了 webhook 的数据流程，从收件到派送到终点。

就这样，发往入口网址的所有 webhook
事件现在都将传递到路由对应的终点，并可从 `nanhook` [后台查看](https://dashboard.nanhook.com/observability/requests)。