---
name: 简介
---

# Peach 

Peach 是一款支持多语言、实时同步以及全文搜索功能的 Web 文档服务器。

## 项目初衷

目前网络上已经有多款非常棒的 Web 文档工具，但是观察了很久也没有一款完全符合自己的需求。最主要的是，我本身有许多项目的文档需要公布在 Web 上，这才决定着手开发一款新的 Web 文档服务器，希望能够成为一个 **通用但可自定义的解决方案**。

下面的表格对比了 Peach 与几款主流文档工具之间主要特性的区别（实际区别可能与我所理解的有偏差）：

|名称|自助托管|多语言文档|实时同步|静态 HTML|多版本|
|:--:|:---------:|:------------:|:------------:|:---------:|:---------:|
|Peach|✅|✅|✅|✅（可缓存）|[计划中](/docs/intro/roadmap)|
|Mkdocs|✅|❌|❌|✅|❌|
|Read The Docs|❌|✅|✅|✅|✅|

除此之外，Peach 还支持以下功能：

- 从任意 Git 托管源实时同步文档
- 根据首选语言全文搜索文档
- 使用 Markdown 作为文档书写语法
- 高度可自定义，包括模板、配置和 CSS 等
- 内置 Disqus 集成支持

## 开发状态

Peach 目前仍处于开发阶段，但已可被用于生产环境。

下面是一些注意事项：

- 文档和功能表现会根据需要进行变动，
- ... 但如果您不打算升级，则可以一直运行到世界末日。:100:
- 如果您突（shou）然（jian）希望升级，没事，认真阅读文档就好了。:joy:

## 案例学习

- [Peach 文档](http://peachdocs.org/)：[peach.peach](https://github.com/peachdocs/peach.peach)
- [Gogs 文档](http://gogs.io/)：[gogsweb.peach](https://github.com/gogits/gogsweb.peach)
- [Macaron 文档](http://go-macaron.com/)：[macaron.peach](https://github.com/macaron-contrib/macaron.peach)
- [INI 文档](https://ini.unknwon.io/): [ini.peach](https://github.com/go-ini/ini.peach)
