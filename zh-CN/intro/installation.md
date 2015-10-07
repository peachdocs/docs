---
name: 下载安装
---

# 下载安装

由于目前我们没有提供编译好的二进制进行分发，因此您必须知道如何搭建 [Go](https://golang.org/) 语言的开发环境。

## 从源码安装

从源码安装要求您已经搭建好 [Go](https://golang.org/) 语言的开发环境并正确设置 `$GOPATH` 环境变量。

您可以通过以下命令进行检查：

```sh
$ go version
go version go1.5.1 darwin/amd64
$ echo $GOPATH
~unknwon/go
```

最低要求的 Go 语言版本为 **1.2**。

然后，您就可以通过以下命令安装 Peach：

```sh
go get github.com/peachdocs/peach
```

搞定，如果没有错误出现，那么 Peach 已经安装成功了。