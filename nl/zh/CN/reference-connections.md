---
copyright:
  years: 2016,2018
lastupdated: "2018-06-12"
---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# 连接配置
{: #connection-configuration}

{{site.data.keyword.composeForPostgreSQL_full}} 数据库连接通过 2 个 HAProxy 门户网站进行管理。每个门户网站有 64 MB 内存。有两个门户网站将支持应用程序在其中一个门户网站变为不可访问时保持连接。

客户机端故障转移由应用程序设计人员负责。某些 PostgreSQL 驱动程序会自动处理多个连接字符串和正常故障转移。除非使用可完全处理故障转移错误的驱动程序，否则您应该：

* 使用在其连接配置中接受多个端点的驱动程序。
* 确保应用程序的数据库读写调用针对错误做出正确反应。选项包括：
  + 记录错误并重新连接。
  + 重新连接并重试导致错误的操作。
  + 将失败操作排队并安排重新连接。

## 传输中加密

所有 {{site.data.keyword.composeForPostgreSQL}} HAProxy 门户网站都已启用 TLS/SSL，并且支持 TLS V1.2。用于服务的证书是自签名证书。您可能必须保存用于服务的证书的本地副本，并为应用程序驱动程序提供该副本的位置，以建立安全连接。

## 连接限制

服务的数据库连接的初始连接限制为 100 个连接。根据通过自动或手动扩展分配给服务的资源，连接限制最大为 1000 个连接。超过连接限制将使服务无响应。

可以通过驱动程序的连接池功能来管理应用程序的连接。
{: .tip}

## 代理超时

HAProxy 门户网站可管理服务器与客户机之间连接的生命周期。我们在此详细描述的信息供驱动程序作者以及对 {{site.data.keyword.composeForPostgreSQL}} 数据库连接低级别活动有兴趣的其他人员作为参考。

设置|值|适用情况
----------|-----------|-----------
client|1 天|客户机应该确认或发送数据的时间。
connect|4 秒|在代理与服务器之间建立连接的时间。
server|30 分钟|服务器应该确认或发送数据的时间。
tunnel|1 天|客户机与服务器之间建立双向连接，并且连接在两个方向均保持不活动状态的时间。
client-fin|5 分钟|服务器应该确认或发送数据，但一个方向的连接已关闭的时间。
check|5 秒|作为辅助超时，是指检查代理与服务器之间是否建立连接的时间。

{: caption="表 1. PostgreSQL HAProxy 超时" caption-side="top"}
