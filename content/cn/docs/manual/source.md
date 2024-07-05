---
title: "入口"
date: 2024-07-04T14:52:00+08:00
weight: 10
---


入口是一个接收任何发送到 `nanhook` 平台 HTTP 请求的服务。
例如，发送 Webhook 的第三方服务（如企业微信、github），或其他内部服务发出 HTTP 请求，入口接收请求，将事件分发给外部或内部的其他服务。

每个入口都有一个唯一的 `nanhook` 入口网址，该 `入口网址` 可以填写到发送方平台的 HTTP 或 webhook URL 字段中，或者在发出 HTTP 请求时在代码中使用。

一旦 `nanhook` 通过 `入口网址` 收到 HTTP 请求，就会根据您的路由规则传递事件。

#### 新增入口

创建入口允许 `nanhook` 开始接收 webhook 事件。

![](/docs/manual/new_source.png)

#### 状态

当 `状态` 是禁用时，入口收到的任何请求，仍将返回 HTTP 200 状态码和相应的响应内容，但是路由的状况是停用的，不会将请求传递到终点。

#### 失效时间

可以在 `失效时间` 填写入口到期的时间（北京时间）。当入口到期失效，入口收到的任何请求，仍将返回 HTTP 200 状态码和相应的响应内容，但是路由的状况是停用的，不会将请求传递到终点。

#### HTTP 请求方法

默认情况下接受 `POST` 请求。在创建和修改时可以启用 `GET, POST, PUT, PATCH, DELETE` 请求。

#### 验证

可以选择性地对请求进行身份验证。 `nanhook` 支持的通用身份验证选项：基本身份验证和 API 密钥，涵盖了大多数身份验证需求。
此外， `nanhook` 还内置支持许多第三方服务商的身份验证。
有关第三方服务商的完整列表，请参阅[入口第三方身份验证提供商](/docs/manual/authentication#source)。

配置入口请求的身份验证:
1. 选择验证请求的真实性；
2. 从下拉框中选择一个验证方法；
3. 填写身份验证方法所需的信息。

#### 删除

入口删除将永久停止 `入口网址` 上的入站请求。`nanhook` 在 `入口网址` 上收到的任何请求返回 HTTP 410 状态码。

入口关联的请求和事件数据将在有效时段内保留。

一旦入口被删除，它关联的路由也被删除。