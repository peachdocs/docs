---
name: Customize Templates
---

# Customize Templates

Default templates are cool and fine, but in many cases you will want to customize them, especially the home page (though it would be awesome if you advertise for Peach :beers:).

To do that, you need first copy over default template files to `custom` directory in your project directory:

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

You now can edit those files to fit your needs. Generally, you only need to edit `home.html` and `footer.html` these two files.

## Syntax

Peach uses Go [Pongo2 v3](https://github.com/flosch/pongo2/tree/v3) as its templating engine, which uses using Django HTML, and syntax is most compatible with [Django 1.7](https://docs.djangoproject.com/en/1.7/ref/templates/builtins/).   

## UI Framework

By default, Peach is using [Semantic UI](http://semantic-ui.com/) as its UI framework.

If you're familiar with it, awesome! But it is **not a requirement**. 

You can change it and use [Bootstrap](http://getbootstrap.com/) as your UI framework because you have full control of how templates are defined. Of course, you need first [import all the static resources](static_resources) you need to the `custom` directory.

See [example of go-ini/ini package](https://ini.unknwon.io/) which uses [Material Design for Bootstrap](https://mdbootstrap.com/) as its UI Framework.

## Localization

Peach uses [Macaron](http://go-macaron.com/)'s [i18n](http://go-macaron.com/docs/middlewares/i18n) middleware for localization, here is an example how to translate a string in the template:

```django
<h2>{{Tr(Lang,"hello %s","world")}}!</h2>
```

And a quick example for how to organize your custom locale files (there three supported languages in the example below):

```ini
$ tree custom/locale
custom/locale
├── locale_en-US.ini
├── locale_fr-FR.ini
└── locale_zh-CN.ini

0 directories, 3 files
```

## Case Studies

In case you are interested in how other projects customize their templates and locale files:

- [gogsweb.peach](https://github.com/gogits/gogsweb.peach)
- [ini.peach](https://github.com/go-ini/ini.peach)
