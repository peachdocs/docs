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

## Disqus

您需要在 [Disqus](https://disqus.com/) 上添加一个站点后才能使用 Disqus 扩展，然后做出相应的配置修改：

```ini
[extension]
ENABLE_DISQUS = true
DISQUS_SHORT_NAME = mypeach
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