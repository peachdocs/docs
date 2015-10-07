---
name: 添加静态资源
---

# 添加静态资源

自定义静态资源的目录同样需要被放置在 `custom` 目录中，并且与默认的静态资源目录具有相同的目录结构：

```sh
$ tree custom/public
custom/public
├── css
├── fonts
├── img
└── js
```

## Logo

自定义站点的第一步就是将默认的 Logo 替换为您项目的 Logo。

因此，您需要将 Logo 文件重命名为 `favicon.ico` 然后放置到 `custom/public/img` 目录中：

```sh
$ tree custom/public/img
custom/public/img
└── favicon.ico
```

无论 Logo 文件的格式是什么（PNG、JPEG 或其它），都必须遵守该名称约定，浏览器会自动识别并展示图片。

:speech_balloon: 您需要强制刷新浏览器以查看最终效果。 

## 自定义 CSS

根据约定，您可以在 `custom/public/css` 目录中创建一个名为 `my.css` 的 CSS 文件：

```sh
$ tree custom/public/css
custom/public/css
└── my.css
```

然后在 `custom/app.ini` 文件中修改相关配置：

```ini
[asset]
CUSTOM_CSS = /css/my.css
```

## 自定义 UI 框架

如果您需要完全自定义一个其它的 UI 框架，则可以将所有需要的静态资源都放置到 `custom/public` 目录中，然后对 `base.html` 模板文件中的旧链接进行替换：

```html
...
	<!--<link href="/css/semantic.min.css?v={{AppVer}}" rel="stylesheet" />-->
	<!--<link href="/css/peach.css?v={{AppVer}}" rel="stylesheet" />-->
	<link href="/css/bootstrap.min.css" rel="stylesheet" />
	
	<!--<script type="text/javascript" src="/js/semantic.min.js?v={{AppVer}}"></script>-->
	<!--<script type="text/javascript" src="/js/peach.js?v={{AppVer}}"></script>-->
	<script type="text/javascript" src="/js/my.js"></script>
...
```