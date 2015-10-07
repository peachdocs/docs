---
name: 配置完全手册
---

# 配置文件完全手册

在阅读本文档之前，您必须确保您已经了解所有的改动都必须发生在 `custom/app.ini` 文件中，并且使用 [INI](https://en.wikipedia.org/wiki/INI_file) 语法。

另外，该文档将只描述其它页面没有提及到的配置选项。

## 站点配置

```ini
[site]
# Peach 实例的名称
NAME = Peach Server
# HTML 描述
DESC = Peach is a web server for multi-language, real-time update and searchable documentation.
# 使用 CDN 来加载静态资源，但 Google Font 将总是从 CDN 加载
USE_CDN = true
# 外部访问站点的 URL
URL = http://localhost:5555
```

## 页面配置

```ini
[page]
# 设为 false 表示站点没有首页，用户将总是被自动重定向到文档页面
HAS_LANDING_PAGE = true
```