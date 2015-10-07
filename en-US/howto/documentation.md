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

In the default section, you define what are the directories and the order of them:

```ini
-: intro
-: howto
-: advanced
-: faqs
```

These name are the same as the directores' name.

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

## Configuration

TODO