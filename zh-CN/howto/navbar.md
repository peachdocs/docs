---
name: 自定义导航栏
---

# 自定义导航栏

Peach 的导航栏默认包含 3 个链接：

- 首页
- 文档首页
- GitHub 链接

您可以通过修改配置文件 `custom/app.ini` 来自定义导航栏中已有的链接：

```ini
[navbar]
-: home
-: documentation
-: github

[navbar.home]
LOCALE = navbar.home
LINK = /

[navbar.documentation]
LOCALE = navbar.documentation
LINK = /docs

[navbar.github]
ICON = github
LOCALE = GitHub
LINK = https://github.com/peachdocs/peach
BLANK = true
```

或者添加新的链接：

```ini
[navbar]
-: home
-: download
-: documentation
-: github

[navbar.home]
...
[navbar.download]
...
[navbar.documentation]
...
[navbar.github]
...
```

其中，`[navbar]` 分区指定了链接的显示顺序，然后在每个下属分区中，最多可以指定五个属性：

1. **ICON**：Semantic UI 中图标的样式名称，留空表示没有图标
2. **LOCALE**：等待被翻译的本地化字符串，但当遇到如 “GitHub” 这样的特有名词，您不需要指定翻译结果，则该字符串就不会被翻译
3. **LINK**：链接的具体地址，可以是内部链接 `/docs` 或外部链接 `https://github.com/peachdocs/peach`
4. **BLANK**：值为 `true` 表示使用新窗口打开链接，默认为 `false`
5. **Enabled**：值为 `false` 表示不渲染该元素，默认为 `true`（ :white_flower: 该选项要求 Peach 版本不得低于 **0.9.8**）

:bell: 如果您的实际配置和默认的一样，则不需要书写或修改任何内容！这样一来，才能够最大程度保证 Peach 更新后与现有配置的兼容性。

当然，如果您觉得 Peach 显示导航栏的方式太搓了，完全可以通过修改模板文件 `navbar.html` 来实现更加高程度的自定义。