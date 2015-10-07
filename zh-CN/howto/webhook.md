---
name: 使用 Web 钩子同步
---

# 使用 Web 钩子同步文档

正常人都不希望自己每次更新文档的时候都要远程登录服务器去进行手动更新操作，特别是进行一些小修改的时候。

为此，Peach 提供了通过 Web 钩子来实时同步文档的功能。

那么我们要做的第一件事情就是确保通过 [Git 仓库](documentation#git-%E4%BB%93%E5%BA%93) 来 [创建文档仓库](documentation)。

然后就可以在 `custom/app.ini` 文件中填写密钥值：

```ini
[docs]
SECRET = mysecret
```

触发钩子的格式和 URL 路径为 `POST /hook?secret={secret}`，其中密钥值 `secret` 是通过 URL 查询的方式传递的。

必须注意的是密钥值 `secret` 只有在和 `SECRET` 的值 **完全匹配** 的情况下才视为有效。因此，如果您的 `SECRET` 值为空，则 URL 查询传递的密钥值 `secret` 也必须为空，反之亦然。

## GitHub

我们在这里阐述一下如何在 GitHub 上设置 Peach 的 Web 钩子，但在其它地方也是基本一样的。

1. 访问文档仓库的新增 Web 钩子页面（`/:username/:reponame/settings/hooks/new`）
2. 填写 **Payload URL** 值为触发钩子的 URL 路径，例如：`http://peachdocs.org/hook?secret=mypeach`
3. 单击 `Add webhook` 搞定。 :tada:

![](/docs/images/github_webhook.png)

从此以后，凡是在 GitHub 推送或合并请求，您的文档都会自动更新到最新版本。