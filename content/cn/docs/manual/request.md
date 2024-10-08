---
title: "请求"
date: 2024-07-09T14:36:00+08:00
weight: 50
---


请求表示 `nanhook` 入口收到的 HTTP 请求日志。
`nanhook` 评估每个请求是否应创建事件。如果请求符合事件条件，请求状态标记为“采纳”，并且创建事件；
否则请求被视为“驳回请求”。


您可以浏览有效时段内所有请求的历史记录，或筛选请求。此日志对于调试和排除请求故障以及它们生成的事件非常有用。

对于每个请求，请求`详情`会显示请求和响应数据：header, path, query, body。

### 采纳

<table>
  <thead>
    <tr>
      <th>状态</th>
      <th>说明</th>
    </tr>
  </thead>
  <tbody>
    <tr>
        <td>成功</td>
        <td>请求成功，创建事件</td>
    </tr>
    <tr>
        <td>验证</td>
        <td>一次性验证请求，不创建事件</td>
    </tr>
  </tbody>
</table>

### 驳回

<table>
  <thead>
    <tr>
      <th>状态</th>
      <th>说明</th>
    </tr>
  </thead>
  <tbody>
    <tr>
        <td>重复</td>
        <td>重复请求</td>
    </tr>
    <tr>
        <td>禁用</td>
        <td>入口不可用</td>
    </tr>
    <tr>
        <td>已失效</td>
        <td>入口已到期</td>
    </tr>
    <tr>
        <td>已删除</td>
        <td>入口已经删除了</td>
    </tr>
    <tr>
        <td>签名验证失败</td>
        <td>请求的身份验证失败</td>
    </tr>
    <tr>
        <td>无路由</td>
        <td>入口未配置路由</td>
    </tr>
    <tr>
        <td>请求方式不正确</td>
        <td>请求方式不符合入口配置</td>
    </tr>
    <tr>
        <td>太多请求</td>
        <td>请求超过频率限制</td>
    </tr>
    <tr>
        <td>请求内容太大</td>
        <td>请求负载大于当前配额允许的负载</td>
    </tr>
    <tr>
        <td>余额不足</td>
        <td>虚拟币余额不足</td>
    </tr>
    <tr>
        <td>订阅已失效</td>
        <td>用户的订阅已到期</td>
    </tr>
    <tr>
        <td>内部错误</td>
        <td>发生未知错误</td>
    </tr>
  </tbody>
</table>