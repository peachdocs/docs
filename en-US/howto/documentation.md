---
name: Setup Documentation
---

# Setup Documentation

Every Peach documentation repository should contain two parts of information:

- TOC.ini
- Documentation for every supported language
 
Repository structure should look like as follows:

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

Let me explain them each at a time.

## TOC.ini

In the repository root directory, you must have a file named `TOC.ini`, which stands for **Table Of Content**.

In this file, you will use [INI](https://en.wikipedia.org/wiki/INI_file) syntax to define what are the directories and files, and in which order to organize them.

Here is the `TOC.ini` took from [Peach Docs](http://peachdocs.org):

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

:speech_balloon: A quick answer to the question you may have, yes, Peach only supports one level for directory.

In the default section, you define what the directories are and their order:

```ini
-: intro
-: howto
-: advanced
-: faqs
```

These name are the same as the directory's name.

Then you create a section for each of these name, and the order of these sections does not matter:

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

In each of these sections, you define what are the files and the order of them:

```ini
[intro]
-: README
-: installation
-: getting_started
-: roadmap
```

Files are using Markdown syntax so their name must end with `.md` extension but since we know that, you do not need to put extension in the `TOC.ini` file at all.

:exclamation: :exclamation: :exclamation:

- Every section must at least have one key.
- Every first key in a section is corresponding to the information of the direcetory.
- This file itself will not be shown as a document page, but for the direcetory. For example, [Introduction](../intro).
- The name of first key can be anything, but the convention is using `README`, and `README.md` as file name.

## Localization

In the repository root directory, every supported language should have a directory with corresponding [Language Culture Name](https://msdn.microsoft.com/en-us/library/ee825488\(v=cs.20\).aspx).

By default, Peach supports English (`en-US`) and Simplified Chinese (`zh-CN`), so Peach has two directories as follows:

```sh
$ tree
.
├── en-US
│   ├── ...
└── zh-CN
│   ├── ...
```

And of course, both of these two directories have exactly the same structure and files' name.

## Document

Every file must have definition information of itself at the very beginning, real content follows afterwards:

```
---
name: Introduction
---

# Peach

Peach is a web server for multi-language, real-time synchronization and searchable documentation.
...
```

In case you only need to define information of a directory, but there is no content for it, you can skip the content:

```
---
name: Advanced
---
```

## Links

Rendering links in Peach is pretty much same as all the other places:

- Link to page in the same level: `[Webhook](webhook)`.
- Link to directory page: `[Introduction](../intro)`.
- Link to page in another directory: `[Getting Started](../intro/getting_started)`.

## Images

By default, documentaion pages have a URL prefix `/docs`, and all your images must be put in a subdirectory of repository root directory named `images`.

Then this is how you link a image: `![](/docs/images/github_webhook.png)`.

## Configuration

All configuration changes must be made in file `custom/app.ini`.

### Locales

By default, Peach supports English and Simplified Chinese, so if you're writing documentation for these two languages, you don't need to change settings in this part.

But if you're just writing documentation in English, you would have to rewrite corresponding values:

```ini
[i18n]
LANGS = en-US
NAMES = English
```

Or you're supporting more than two languages:

```ini
[i18n]
LANGS = en-US,zh-CN,fr-FR
NAMES = English,简体中文,Français
```

Note that the first language, in both examples above, `en-US` will also be known as **default language**, any page that is not available in other languages, will present content in this language.

### Git Repository

In production, you would use remote Git source as your documentation repository:

```ini
RUN_MODE = prod

[docs]
TYPE = remote
TARGET = https://github.com/Unknwon/peach-docs.git
```

So Peach knows where to fetch and update your documentation, and cache all documents.

## Developing Locally

To make your life easier while you're developing your documentation locally, Peach also supports specify a local target path of your documentation repository:

```ini
RUN_MODE = dev

[docs]
TYPE = local
TARGET = ~unknwon/mydocs
```

In `dev` mode, Peach reloads your documents every time you refresh a page, so you can preview results instantly.
