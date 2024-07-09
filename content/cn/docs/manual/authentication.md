---
title: "验证"
date: 2024-07-04T16:22:00+08:00
weight: 40
---

在两个领域会使用身份验证：

* 入口
* 终点

### 入口身份验证

来自 `入口网址` 的入站请求可以通过以下方式进行身份验证：

* [基本身份验证](https://developer.mozilla.org/en-US/docs/Web/HTTP/Authentication#basic_authentication_scheme) `Basic Auth`：用户名和密码；
* API 密钥 `API Key`：可配置在 HTTP Header 或 Query 参数中提供；
* 第三方服务商的身份验证；

支持的第三方服务商列表：

* [微信测试号](https://developers.weixin.qq.com/doc/offiaccount/Basic_Information/Access_Overview.html)
* [企业微信](https://developer.work.weixin.qq.com/document/10514)
* [码云 gitee](https://gitee.com/help/articles/4290)
* [Github](https://docs.github.com/zh/webhooks/using-webhooks/validating-webhook-deliveries)

### 终点身份验证

对 `终点网址` 的出站请求可以通过以下方式进行身份验证：

* [基本身份验证](https://developer.mozilla.org/en-US/docs/Web/HTTP/Authentication#basic_authentication_scheme) `Basic Auth`：用户名和密码；
* API 密钥 `API Key`：可配置在 HTTP Header 或 Query 参数中提供；
* Bearer 令牌：配置在 Bearer 为前缀的 HTTP Header；
* 第三方服务商的身份验证；

支持的第三方服务商列表：

* [企业微信群机器人](https://developer.work.weixin.qq.com/document/path/91770)
* [飞书自定义机器人](https://open.feishu.cn/document/client-docs/bot-v3/add-custom-bot)
* [钉钉自定义机器人](https://open.dingtalk.com/document/robots/custom-robot-access)