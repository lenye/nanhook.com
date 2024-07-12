---
title: "使用手册"
description: 使用 `nanhook` 发送和接收 webhook 事件所需的指南、示例和参考资料。
weight: 3
---

`nanhook` 是一个 webhook 异步网关，轻松管理、监控和测试你的 webhook 事件，助力你掌控事件全流程。

* 订阅事件，注册 webhook：创建端点，托管入口，注册路由，支持发送和接收多个 webhook 事件。
* 安全连接：使用 HTTPS 以确保数据加密且被安全传输，保护你的 webhook。
* 验证 webhook：实施验证方法，以确认传入的数据来自受信任的来源。
* 错误处理：将系统设计为优雅地处理故障，包括重试和不成功的 webhook 交付的警报。
* 监控和记录 webhook：维护 webhook 活动的详细日志，以便于调试并为数据流提供审计跟踪。

#### 准备工作

* `nanhook cloud` 帐户。如果您没有帐户，请登录 `控制台` ，[创建一个帐户](https://dashboard.nanhook.com/login)。
* 用于接收 webhook 事件的终点 api。