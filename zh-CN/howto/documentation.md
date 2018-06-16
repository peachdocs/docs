---
name: 创建文档仓库
---

# 创建文档仓库

每一个 Peach 文档仓库都包含两部分内容：

- TOC.ini
- 针对每个语言的文档
 
仓库结构大致如下：

```sh
$ tree
.
├── TOC.ini
├── en-US
│   ├── advanced
│   │   ├── README.md
│   │   └── ...
│   ├── faqs
│   │   └── README.md
│   ├── howto
│   │   ├── README.md
│   │   ├── ...
│   └── intro
│       ├── README.md
│       ├── ...
└── zh-CN
│   ├── ...
```

让我娓娓道来它们都是做什么的。:trollface:

## TOC.ini

在仓库的根目录，您必须创建一个名为 `TOC.ini` 的文件，也就是所谓的 **Table Of Content**。

在这个文件中，您需要使用 [INI](https://en.wikipedia.org/wiki/INI_file) 语法来定义显示哪些目录和文件，以及它们的显示顺序。

下面为 [Peach 文档](http://peachdocs.org) 的 `TOC.ini` 文件：

```ini
-: intro
-: howto
-: advanced
-: faqs

[intro]
-: README
-: installation
-: getting_started
-: roadmap

[howto]
-: README
-: documentation
-: webhook
-: templates
-: static_resources
-: disqus
-: ga

[advanced]
-: README
-: config_cheat_sheet

[faqs]
-: README
```

:speech_balloon: 您可能已经注意到，Peach 只支持一层目录结构。

在默认分区中，您可以定义显示哪些目录以及它们的显示顺序：

```ini
-: intro
-: howto
-: advanced
-: faqs
```

这些名称必须和目录名称一致。

然后再为每一个目录创建一个分区，顺序在这里是无所谓的：

```ini
[intro]
...
[howto]
...
[advanced]
...
[faqs]
...
```

在每个分区中，您可以定义显示哪些文件以及它们的显示顺序：

```ini
[intro]
-: README
-: installation
-: getting_started
-: roadmap
```

因为文件已经默认使用 Markdown 语法，并且必须以 `.md` 作为扩展名，所以您完全不需要在 `TOC.ini` 文件中说明。

:exclamation: :exclamation: :exclamation:

- 每个分区必须至少包含一个键
- 每个分区的第一个键用于指示该目录的信息
- 这个文件本身不会作为文档单独显示，但是会以目录的形式显示。例如：[简介](../intro)
- 该键的名称是随意的，但一般约定使用 `README`，即使用 `README.md` 作为文件名

## 本地化

在仓库的根目录，您需要为每个支持的语言创建一个名称符合 [Language Culture Name](https://msdn.microsoft.com/en-us/library/ee825488\(v=cs.20\).aspx) 的相应目录。

Peach 已经默认支持英语（`en-US`）和简体中文（`zh-CN`），所以 Peach 文档的目录结构为：

```sh
$ tree
.
├── en-US
│   ├── ...
└── zh-CN
│   ├── ...
```

当然，这两个目录拥有完全相同的目录结构和文件名称。

## 文档内容

每个文件都必须在最开头的部分定义自身的信息，然后才是文档的内容：

```
---
name: 简介
---

# Peach

Peach 是一款支持多语言、实时同步以及全文搜索功能的 Web 文档服务器。
...
```

如果您的目录不包含任何文档内容，只是代表分类，则可以省略文档部分：

```
---
name: 高级用法
---
```

## 链接跳转

Peach 中渲染链接的方式和其它地方大体相同：

- 链接到相同目录的其它页面：`[Webhook](webhook)`.
- 链接到某个目录：`[Introduction](../intro)`.
- 链接到其它目录下的页面：`[Getting Started](../intro/getting_started)`.

## 链接图片

默认情况下，所有的文档页面都会使用 `/docs` 作为 URL 前缀。并且您所有的图片都必须存放于仓库根目录下名为 `images` 的子目录。

然后通过这种语法来链接图片：`![](/docs/images/github_webhook.png)`

## 文档配置

所有的配置改动都必须发生在 `custom/app.ini` 文件。

### 本地化

Peach 已经默认支持英语和简体中文，所以如果您的文档正好只支持这两种语言，则不需要进行任何修改。

但是，如果您只书写英语文档，则必须对配置进行重写：

```ini
[i18n]
LANGS = en-US
NAMES = English
```

或者您支持两种以上语言：

```ini
[i18n]
LANGS = en-US,zh-CN,fr-FR
NAMES = English,简体中文,Français
```

在以上两个例子中，它们的第一个语言都是 `en-US`，第一个语言又被称之为 **默认语言**，如果某个页面在首选语言中不存在，则会自动显示默认语言的版本。

### Git 仓库

在部署环境下，一般建议使用远程 Git 源来作为您的文档仓库：

```ini
RUN_MODE = prod

[docs]
TYPE = remote
TARGET = https://github.com/Unknwon/peach-docs.git
TARGET_DIR = # 如果文档不是在仓库的根目录，可以在此处添加子目录名称
```

:white_flower: `TARGET_DIR` 选项要求 Peach 版本不得低于 **0.9.6**

如此一来，Peach 就知道去哪里拉取和更新文档，并对文档进行缓存。

## 本地开发

很显然，您会有本地书写开发文档的需求，因此 Peach 也支持将文档同步类型设置为本地：

```ini
RUN_MODE = dev

[docs]
TYPE = local
TARGET = ~unknwon/mydocs
```

在 `dev` 模式下，Peach 会在每次访问文档页面时重新加载并渲染相应的文档，从而也就达到实时预览效果的需求。