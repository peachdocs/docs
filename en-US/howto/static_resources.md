---
name: Add Static Resources
---

# Add Static Resources

The directory of custom static resources follows the same structure of default ones, and should be put under `custom` directory as well:

```sh
$ tree custom/public
custom/public
├── css
├── fonts
├── img
└── js
```

## Logo

The very first thing you want to customize is the Logo of your project.

To do that, rename your Logo file to `favicon.ico` and put it under `custom/public/img` directory:

```sh
$ tree custom/public/img
custom/public/img
└── favicon.ico
```

It does not matter what your Logo image format is (PNG, JPEG or whatever), it's just a name convention, and let browser figures it.

:speech_balloon: You need do a hard refresh on your browser to actually see the effect. 

## Custom CSS

By convention, you can create a CSS file named `my.css` under `custom/public/css` directory:

```sh
$ tree custom/public/css
custom/public/css
└── my.css
```

And then, change settings on your configuration file `custom/app.ini`:

```ini
[asset]
CUSTOM_CSS = /css/my.css
```

## Custom UI Framework

In the case you need to completely change a UI framework, you can put all needed static resources on `custom/public` directory and change template file `base.html` to replace old resource links with custom ones:

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