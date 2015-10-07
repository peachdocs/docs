---
name: Use Extensions
---

# Use Extensions

## Search

Search extension is enabled by default, to disable it:

```ini
[extension]
ENABLE_SEARCH = false
```

## Highlight JS

Highlight JS is enabled and can not be disabled, but you can customize the theme of it.

For example, you want to use `zenburn` theme instead of default one. 

You first copy `zenburn.css` and put it into `custom/public/css` directory, then change setings in `custom/app.ini`:

```ini
[extension]
HIGHLIGHTJS_CUSTOM_CSS = /css/zenburn.css
```

## Disqus

To use Disqus extension, you should add a site on [Disqus](https://disqus.com/) first, then make corresponding changes of settings:

```ini
[extension]
ENABLE_DISQUS = true
DISQUS_SHORT_NAME = mypeach
```

## Google Analytics

To use Google Analytics extension, you should add a profile on [Google Analytics](http://www.google.com/analytics/) first, then make corresponding changes of settings:

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

As always, you can hack on corresponding `.html` template files to use and add more extensions.