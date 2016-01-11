---
name: 下载安装
---

# 下载安装

由于目前我们没有提供编译好的二进制进行分发，因此您必须知道如何搭建 [Go](https://golang.org/) 语言的开发环境。

## 从二进制安装

您可以直接从 [GitHub](https://github.com/peachdocs/peach/releases) 上下载最新版本的二进制文件。

## 从源码安装

从源码安装要求您已经搭建好 [Go](https://golang.org/) 语言的开发环境并正确设置 `$GOPATH` 环境变量。

您可以通过以下命令进行检查：

```sh
$ go version
go version go1.5.1 darwin/amd64
$ echo $GOPATH
~unknwon/go
```

最低要求的 Go 语言版本为 **1.3**。

然后，您就可以通过以下命令安装 Peach：

```sh
go get github.com/peachdocs/peach
```

也可以通过使用 `-u` 标志来更新 Peach：

```sh
go get -u github.com/peachdocs/peach
```

然后使用以下命令来检查安装在您系统的 Peach 版本（假设路径 `$GOPATH/bin` 已经被添加到环境变量 `$PATH`）：

```sh
$ peach -v
Peach version 0.9.2.1214
```
