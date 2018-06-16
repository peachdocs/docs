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

Let me explain them one at a time.

## TOC.ini

In the repository root directory, you must have a file named `TOC.ini`, which stands for **Table Of Contents**.

In this file, you will use [INI](https://en.wikipedia.org/wiki/INI_file) syntax to define the directories and files, and their organization.

Here is the `TOC.ini` from [Peach Docs](http://peachdocs.org):

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

:speech_balloon: Note that Peach only supports single-level directories.

In the default section, define the directories and their order:

```ini
-: intro
-: howto
-: advanced
-: faqs
```

These names are the same as the directory's name.

Then create a section for each name. The section order doesn't matter:

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

In each section, define the files and their order:

```ini
[intro]
-: README
-: installation
-: getting_started
-: roadmap
```

Because files use Markdown syntax, their names must end with an `.md` extension. However, since we know that, no extension needs to be added in the `TOC.ini` file at all.

:exclamation: :exclamation: :exclamation:

- Every section must have at least one key.
- The first key in every section corresponds to the directory's information.
- This file itself will not be shown as a document page, but for the directory. For example, [Introduction](../intro).
- The name of the first key can be anything, but conventionnally, `README` and `README.md` are used as file names.

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

And of course, both of these directories have exactly the same structure and file name.

## Document

Every file must define itself in the very beginning; real content follows afterwards:

```
---
name: Introduction
---

# Peach

Peach is a web server for multi-language, real-time synchronization and searchable documentation.
...
```

If you only need to define information in a directory but it has no content, skip the content:

```
---
name: Advanced
---
```

## Links

Rendering links in Peach basically works the same way as anywhere else:

- Link to page in the same level: `[Webhook](webhook)`.
- Link to directory page: `[Introduction](../intro)`.
- Link to page in another directory: `[Getting Started](../intro/getting_started)`.

## Images

By default, documentaion pages have a URL prefix `/docs`, and all your images must be put in a subdirectory of repository root directory named `images`.

This is how to link a image: `![](/docs/images/github_webhook.png)`.

## Configuration

All configuration changes must be made in file `custom/app.ini`.

### Locales

By default, Peach supports English and Simplified Chinese, so if you're writing documentation for these two languages, you don't need to change settings in this part.

If you're just writing documentation in English, you would need to rewrite corresponding values:

```ini
[i18n]
LANGS = en-US
NAMES = English
```

If you're supporting more than two languages:

```ini
[i18n]
LANGS = en-US,zh-CN,fr-FR
NAMES = English,简体中文,Français
```

Note that the first language, `en-US` in both of the examples above, will also be known as **default language**. Any page that is not available in other languages will present content in this language.

### Git Repository

In production, use remote Git source as your documentation repository:

```ini
RUN_MODE = prod

[docs]
TYPE = remote
TARGET = https://github.com/Unknwon/peach-docs.git
TARGET_DIR = # Add subdirectory here if docs are not located in the root directory of your repository
```

:white_flower: `TARGET_DIR` option requires Peach version **0.9.6**

This means Peach knows where to fetch and update your documentation, and cache all documents.

## Developing Locally

To make your life easier while you're developing your documentation locally, Peach also supports specification of a local target path of your documentation repository:

```ini
RUN_MODE = dev

[docs]
TYPE = local
TARGET = ~unknwon/mydocs
```

In `dev` mode, Peach reloads your documents every time you refresh a page, so you can preview results instantly.
