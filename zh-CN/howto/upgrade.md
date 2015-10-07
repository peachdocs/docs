---
name: 更新版本
---

# 更新版本

如果您之前是通过源码安装的 Peach，则可以直接通过执行以下命令来完成 Peach 的二进制升级操作：

```sh
$ go get -u github.com/peachdocs/peach
```

然后在每个项目的目录下，都要按照以下步骤完成升级操作：

1. 移除现有的默认 `conf`、`public` 和 `templates` 目录
2. 重新拷贝这些目录到当前项目中
3. 检查变更日志，确保没有兼容性问题
4. 在自定义目录下的 `templates` 和 `public` 目录做出任何需要的修改以修复可能的兼容性问题