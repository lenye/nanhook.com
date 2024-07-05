---
title: "终点"
date: 2024-07-05T21:32:00+08:00
weight: 20
---

终点是可以接收 webhook 事件的有效 HTTP URL。

##### 请求标头 http headers

当将入口的请求路由到终点目标时，终点收到 http 请求方法和入口的一样，`nanhook` 会保留原始请求的标头、正文、查询字符串和路径。
下面列出了此规则的更详细详细信息：

`终点网址` 不是第三方服务商时，除了请求的原始标头之外，`nanhook` 还添加了以下标头：

```
X-Nanhook-Trace-Id               追踪 id，用于调试和故障排除
X-Nanhook-Attempt-Count          派送尝试计数
X-Nanhook-Connecting-Ip          发送到入口请求的客户端的 IP
X-Nanhook-Source-Id              入口 id
X-Nanhook-Source-Http-Method     入口的 http 请求方法
X-Nanhook-Source-Url-Path        入口的 url path
X-Nanhook-Source-Url-Query       入口的 url query 参数
X-Nanhook-Source-Verify          入口是否身份验证
```

##### 响应请求 http response

终点响应从 `nanhook` 收到的事件时，请牢记终点要使用反映系统实际状态的 http 状态码响应每个请求。
处理操作时，响应 HTTP 200 表示成功，或响应 HTTP 4XX - 5XX 表示失败。

终点必须在 10 秒内响应请求，否则将得到超时状态码 -1，并在 `nanhook` 中标记为失败。然后重试。

#### 新增终点

创建终点，填写有效的 `终点网址`，`nanhook` 可以将收到 webhook 事件传递到终点。

![](/docs/manual/new_endpoint.png)

#### 状态

当 `状态` 没有选择 `可用` 时，终点状态是“禁用”，连接终点的路由状况是停用的，相应入口收到 webhook 事件不会传递到终点。

#### 验证

可以选择性地对请求进行身份验证。

`nanhook` 支持的通用身份验证选项：基本身份验证 `Basic Auth`、`API Key` 和 `Bearer Token`，涵盖了大多数身份验证需求。
此外，`nanhook` 还内置支持许多第三方服务商的身份验证。
有关第三方服务商的完整列表，请参阅[终点第三方身份验证提供商](/docs/manual/authentication#endpoint)。

配置终点请求的身份验证:

1. 选择验证请求的真实性；
2. 从下拉框中选择一个验证方法；
3. 填写身份验证方法所需的信息。

#### 删除

终点删除将永久停止 `终点网址`。

终点关联的请求和事件数据将在有效时段内保留。

一旦终点被删除，它关联的路由也被删除。