---
name: 自定义模板
---

# 自定义模板文件

默认的模板文件看起来已经十分完（er）美（bi），但很多情况下您依旧会希望对它们进行自定义，尤其是主页（当然，我不介意您给 Peach 做免费的推广 :beers:）。

首先，您需要复制默认的模板文件到您项目目录下的 `custom` 目录：

```sh
$ cp -r templates custom
$ tree custom/templates
custom/templates
├── 404.html
├── base.html
├── disqus.html
├── docs.html
├── footer.html
├── home.html
├── navbar.html
└── search.html

0 directories, 8 files
```

接下来，就可以随意编辑这些文件啦！不过一般来说，您只需要修改 `home.html` 和 `footer.html` 这两个文件。

## 模板语法

Peach 使用 Go 语言 [Pongo2 v3 版本](https://github.com/flosch/pongo2/tree/v3) 作为模板引擎，它使用的是 Django HTML 格式，并与 [Django 1.7](https://docs.djangoproject.com/en/1.7/ref/templates/builtins/) 的语法基本兼容。   

## UI 框架

Peach 默认使用 [Semantic UI](http://semantic-ui.com/) 作为它的 UI 框架。

如果您已经对这款框架非常熟悉，那么最好不过了。但这并 **不是一个硬性要求**。 

因为 Peach 提供了对模板的完全自定义能力，您可以根据喜好将 UI 框架修改为 [Bootstrap](http://getbootstrap.com/)。当然，这就要求您首先 [导入所有相关的静态资源](static_resources) 到 `custom` 目录中。

可以参考 [go-ini/ini 的案例](https://ini.unknwon.io/)，该网站使用了 [Material Design for Bootstrap](https://mdbootstrap.com/) 作为 UI 框架。

## 模板本地化

Peach 使用 [Macaron](http://go-macaron.com/) 框架的 [i18n](http://go-macaron.com/docs/middlewares/i18n) 中间件来实现模板的本地化需求。

下面是一个在模板中翻译某个字符串的例子：

```django
<h2>{{Tr(Lang,"hello %s","world")}}!</h2>
```

下面是一个如何组织自定义本地化文件的例子（例子中支持 3 种语言）：

```ini
$ tree custom/locale
custom/locale
├── locale_en-US.ini
├── locale_fr-FR.ini
└── locale_zh-CN.ini

0 directories, 3 files
```

## 案例学习

如果您对其它项目如何自定义模板感兴趣，可以参考以下案例：

- [gogsweb.peach](https://github.com/gogits/gogsweb.peach)
- [ini.peach](https://github.com/go-ini/ini.peach)
