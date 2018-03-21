---
name: Introduction
---

# Peach

Peach is a web server for multi-language, real-time synchronization and searchable documentation.

## Motivation

There are some awesome web documentation tools, but for a long time, none of them satisfied my need to post multi-project documentation on the web, so I have been searching for **a common and customizable solution**. This is initally why Peach was created.

The following table illustrates the main feature differences between Peach and other existing tools (concepts may be different from what I understand):

|Name|Self-hosted|Multi-language|Real-time Sync|Static HTML|Versionable|
|:--:|:---------:|:------------:|:------------:|:---------:|:---------:|
|Peach|✅|✅|✅|✅(cachable)|[Roadmap](/docs/intro/roadmap)|
|Mkdocs|✅|❌|❌|✅|❌|
|Read The Docs|❌|✅|✅|✅|✅|

Other than those, Peach also supports following features:

- Real-time sync from any Git hosting sources.
- Full-text search based on preferred language.
- Use Markdown to write like a writer.
- Highly configurable without touching a single bit of Git history.
- Built-in Disqus integration support.

## Development Status

Peach is currently still in development, but can be used in production with some notes:

- Things are subject to change,
- ... but if you don't upgrade, it will keep working until the end of the world. :100:
- If you do want to upgrade, just read the documentation. :joy:

## Case Studies

- [Peach Docs](http://peachdocs.org/): [peach.peach](https://github.com/peachdocs/peach.peach)
- [Gogs Docs](http://gogs.io/): [gogsweb.peach](https://github.com/gogits/gogsweb.peach)
- [Macaron Docs](http://go-macaron.com/): [macaron.peach](https://github.com/macaron-contrib/macaron.peach)
- [INI Docs](https://ini.unknwon.io/): [ini.peach](https://github.com/go-ini/ini.peach)
