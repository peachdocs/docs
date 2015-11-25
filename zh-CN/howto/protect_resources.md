---
name: 资源保护
---

# 保护内部资源

:white_flower: 要求 Peach 版本不得低于 **0.9.0**

当有些内部资源需要限制访问时，可以对此类资源启用保护模式。

那么，保护模式有什么用？

1. 基于 HTTP 基本授权进行认证
2. 用户定义一组授权用户和他们的密码
3. 用户定义一组受保护的资源以及允许访问的用户

您可以通过在和 `TOC.ini` 文件的相同目录下创建 `protect.ini` 文件来启用保护模式。

下面是一个示例文件：

```ini
[user]
user1 = 5F4DCC3B5AA765D61D8327DEB882CF99
user2 = xxx
user3 = xxx

[auth]
howto/documentation = user1,user2,user3
howto/webhook = user1,user2
howto/templates = user1
```

用户的密码必须经过 MD5 编码，多个用户之间需要使用逗号（`,`）分隔。

同时，文档的 URL 不需要添加 `/docs/` 前缀。

基于上面的文件，我们定义了 3 个授权用户和 3 个受保护的资源：

- `user1` 可以访问所有资源。
- `user2` 只能访问 `howto/documentation` 和 `howto/webhook`，尝试访问 `howto/templates` 将返回 **403** 错误。
- `user3` 只能访问 `howto/documentation`，尝试访问 `howto/webhook` 和 `howto/templates` 将返回 **403** 错误。
- 认证失败将返回 **401** 错误。