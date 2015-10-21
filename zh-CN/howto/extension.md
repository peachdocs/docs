---
name: 使用扩展功能
---

# 使用扩展功能

## 搜索

搜索扩展处于默认开启状态，修改以下配置可以禁用该扩展：

```ini
[extension]
ENABLE_SEARCH = false
```

## Highlight JS

Highlight JS 默认启用且不可关闭，但可以自定义它的渲染主题。

例如，您希望将默认主题替换为 `zenburn`，则需要先将 `zenburn.css` 文件拷贝至 `custom/public/css` 目录下，然后在 `custom/app.ini` 文件中做出如下修改：

```ini
[extension]
HIGHLIGHTJS_CUSTOM_CSS = /css/zenburn.css
```

## 编辑页面

您可以在文档页面添加一个编辑页面的链接以方便用户一同协助改进文档。

您需要对配置文件做出相应的修改才能使用该扩展：

```ini
[extension]
ENABLE_EDIT_PAGE = true
EDIT_PAGE_LINK_FORMAT = https://github.com/peachdocs/docs/blob/master/{lang}/{blob}
```

请不要忘记将链接修改为您的仓库链接！

:white_flower: 如果您正在使用低于 **0.7.0** 版本的 Peach，并且使用了自定义模板，则需要在 `docs.html` 模板文件的 `{{Content|safe}}` 这一行之前加入以下内容：

```django
{% if Extension.EnableEditPage %}
	<a class="ui blue button" id="edit_page" href="{{EditPageLink}}">{{Tr(Lang, "docs.edit_page")}}</a>
{% endif %}
```

## Disqus

您需要在 [Disqus](https://disqus.com/) 上添加一个站点后才能使用 Disqus 扩展，然后做出相应的配置修改：

```ini
[extension]
ENABLE_DISQUS = true
DISQUS_SHORT_NAME = mypeach
```

## 多说

:white_flower: 要求 Peach 版本不得低于 **0.7.1**

您需要在 [DuoShuo](http://duoshuo.com/) 上添加一个站点后才能使用多说扩展，然后做出相应的配置修改：

```ini
[extension]
ENABLE_DUOSHUO = true
DUOSHUO_SHORT_NAME = mypeach
```

## Google Analytics

您需要在 [Google Analytics](http://www.google.com/analytics/) 上创建一份档案后才能使用 Google Analytics 扩展，然后做出相应的配置修改：

```ini
GA_BLOCK = """<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','//www.google-analytics.com/analytics.js','ga');
  ga('create', 'UA-xxxxxxxx-y', 'auto');
  ga('send', 'pageview');
</script>"""
```

---

由于您对模板文件拥有完全的自定义能力，因此总是可以通过修改相应的 `.html` 模板文件来达到使用或添加更多扩展的需求。