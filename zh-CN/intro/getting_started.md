---
name: 开始使用
---

# 开始使用

同志们好！------ 你不是首长！

同志们辛苦了！------ 我忙着创建 Peach 项目呢，别嚷嚷！

根据约定，每个 Peach 项目都以 `*.peach` 的格式命名，在本例中，我们将使用 `my.peach`，并将项目放置在默认的下载目录：

```sh
$ cd ~/Downloads
```

接下来，我们需要做一些基本设定（假设路径 `$GOPATH/bin` 已经被添加到环境变量 `$PATH`）。

如果您是通过源码安装 Peach 的，应该执行与以下类似的命令：

```sh
$ peach new -target=my.peach
➜  Creating 'my.peach'...
➜  Creating 'templates'...
➜  Creating 'public'...
Do you want to use custom templates?[Y/n] n
✓  Done!
```

好了，来看看目前我们的项目是个什么情况吧：

```sh
$ cd my.peach
$ tree -L 2
.
├── conf
│   ├── app.ini
│   └── locale
├── public
│   ├── css
│   ├── fonts
│   ├── img
│   └── js
└── templates
    ├── 404.html
    ├── base.html
    ├── disqus.html
    ├── docs.html
    ├── duoshuo.html
    ├── footer.html
    ├── home.html
    ├── navbar.html
    └── search.html
```

不错不错，差不多都搞定了，不过还差一样，是什么呢？当然是自定义配置啦。

为了方便起见，我们直接使用 Peach 自己的配置，因为它已经 [开源在 GitHub](https://github.com/peachdocs/peach.peach) 上了。 :heart_eyes:

卧槽，这都（shen）可（me）以（gui）？

当然没问题，我们直接克隆到本地系统并命名为 `custom` 即可，因为该名称就是 Peach 用来加载所有自定义设置的目录。

```sh
git clone https://github.com/peachdocs/peach.peach.git custom
```

简单粗暴！请给自己的机智点 32 个赞。:clap:

好了，快点在我们的项目目录下（`~/Downloads/my.peach`）运行 Peach 吧：

```sh
$ peach web
```

现在，我们就可以从控制台看到一些日志啦：

```
[Peach] 15-10-06 19:58:44 [ INFO] Peach 0.8.0.1025
[Peach] 15-10-06 19:58:44 [ INFO] Peach Server Listen on 0.0.0.0:5556
```

从日志说明来看，Peach 将监听的端口自定义为了 `5556`（默认为`5555`）。

此时打开浏览器，访问 http://localhost:5556/ ，哈哈哈，我真是太佩服自己了。

如果您对 Peach 的自定义配置感兴趣，让我通过 `custom/app.ini` 文件简单地解释一下：

```ini
# 修改监听端口
HTTP_PORT = 5556

[docs]
# 设置文档类型为远程 Git 源
TYPE = remote
# 远程 Git 源的 URL
TARGET = https://github.com/Unknwon/peach-docs.git
```

现在您应该明白为什么我们之前什么都没做就可以直接浏览文档了吧？

好了，让我们继续学习下一个部分：[创建文档仓库](../howto/documentation)。
