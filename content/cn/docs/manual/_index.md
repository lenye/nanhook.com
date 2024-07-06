---
title: "使用手册"
description: 使用 `nanhook` 发送和接收 webhook 事件所需的指南、示例和参考资料。
weight: 3
---

`nanhook` 是一个 webhook 异步网关，轻松管理、监控和测试你的 webhook 事件，助力你掌控事件全流程。

* 注册 webhook ，订阅的事件：创建端点，托管入口，注册路由，以支持发送和接收多个 webhook 事件。
* 保护你的 webhook ：为了确保 webhook 数据的完整性和保密性，实施安全措施是至关重要的，如 SSL/TLS 加密和认证令牌，这些措施将有助于保护你的 webhook，阻止未经授权的访问和篡改。
* 处理重试和失败：记录失败的 webhook，建立一个重试机制，以便在失败时重新发送请求。
* 监控和记录 webhook：追踪你的 webhook，记录传入的请求、有效载荷和处理结果。监测你的 webhook 将帮助你识别潜在的问题，跟踪性能，并确保你的系统的可靠性。

#### 准备工作

* `nanhook cloud` 帐户。如果您没有帐户，请登录 `控制台` ，[创建一个帐户](https://dashboard.nanhook.com/login)。
* 用于接收 webhook 事件的终点 api。