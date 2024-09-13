---
title: "路由"
date: 2024-07-05T16:07:00+08:00
weight: 30
---

路由连接 `入口` 和 `终点`，是 `nanhook` 中 webhook 事件从入口传递到终点的管道。
除了定义如何传递事件之外，路由还可指定要使用的延迟、自动重试策略。

### 新增路由

##### 准备工作

* [新增入口](/docs/manual/source)，生成一个唯一的 `入口网址`，允许 `nanhook` 开始接收 webhook 事件。
* [新增终点](/docs/manual/endpoint)，填写有效的 `终点网址`，`nanhook` 将收到 webhook 事件传递到终点。

选择 `入口` 和 `终点` 连接成路由。

![](/docs/manual/new_route.png)

### 状态

当 `状态` 没有选择 `可用` 时，路由状况是“停用”，路由的入口收到 webhook 事件不会传递到路由的终点。

### 状况

路由状况是一个计算字段，只有路由状况是 `启用`，才执行事件传递。

`路由状态`、`入口状态`、`终点状态` 决定路由状况是否为 `启用`：

* 路由、入口、终点的状态都是 `可用`，路由状况是 `启用`
* 路由、入口、终点的任意一个状态不是 `可用`，路由状况都是 `停用`

### 延迟

* 当设置为零时，取消延迟策略；
* 当设置大于零时，开启延迟策略，设置在入口成功收到 webhook 事件后延迟多久开始派送到终点；最多延迟 6 小时（60 * 60 * 6 =
  21600 秒）。

### 重试

配置派送到终点失败的自动重试策略；最多间隔 6 小时，最多自动重试 20 次；手动重试不限次数。

时间算法：

* `线性` 重试将以固定的时间间隔发生；
* `指数` 每次重试的延迟时间将是上一次的两倍（1 秒、2 秒、4 秒……）。

当次数设置为零时，取消自动重试策略。

### 请求标头

在 HTTP 请求发送到终点服务器之前需要添加和删除的标头。
[HTTP 标头参考文档](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers)

![](/docs/manual/route_request_headers.png)

#### 添加标头

将在终端服务器 HTTP 请求添加一个标头。

例如：

> 配置添加标头

```
foo: value
```

> 入口 HTTP 请求

```
GET / HTTP/1.1
host: q.nanhook.com
```

> 终点服务器的请求

```
GET / HTTP/1.1
host: q.nanhook.com
foo: value
```

#### 删除标头

如果删除具有多个值的标题，则所有值都将被删除。

例如：

> 配置删除标头

```
foo
```

> 入口 HTTP 请求

```
GET / HTTP/1.1
host: q.nanhook.com
foo: value1
foo: value2
```

> 终点服务器的请求

```
GET / HTTP/1.1
host: q.nanhook.com
```

#### 替换已存在的标头

例如：

> 配置删除标头

```
foo
```

> 配置添加标头

```
foo: new-value
```

> 入口 HTTP 请求

```
GET / HTTP/1.1
host: q.nanhook.com
foo: original-value
```

> 终点服务器的请求

```
GET / HTTP/1.1
host: q.nanhook.com
foo: new-value
```

#### 添加已存在的标头，它将再添加一个标头

例如：

> 配置添加标头

```
foo: new-value
```

> 入口 HTTP 请求

```
GET / HTTP/1.1
host: q.nanhook.com
foo: original-value
```

> 终点服务器的请求

```
GET / HTTP/1.1
host: q.nanhook.com
foo: original-value
foo: new-value
```

#### 区分大小写

添加和删除的标头时，`nanhook` 将不区分大小写的匹配任何标头。

#### 特殊情况

* 不能添加或删除用户代理标头 `User-Agent`。
* 不能添加或删除主机标头 `Host`。

### 删除

路由删除将不再传递 webhook 事件。
