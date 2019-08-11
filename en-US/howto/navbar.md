---
name: Customize Navbar
---

# Customize Navbar

By default, Peach only shows three items on navbar:

- Home page
- Documentation page
- GitHub link

You can customize these items in your `custom/app.ini` file:

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

Or add more items:

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

You can see that the order of items are defined in the section `[navbar]`, and in each of those sections, you can define at most four attributes:

1. **ICON**: the name of icon in Semantic UI, no icon if it's empty.
2. **LOCALE**: the value to be translated based on your locale file, and for certain name like "GitHub", you don't define a translation result, so it will not be translated.
3. **LINK**: link of item, can be internal link like `/docs` or external link like `https://github.com/peachdocs/peach`.
4. **BLANK**: `true` for open link in a new windows, default is `false`.
5. **Enabled**: `false` for not rendering the element, default is `true` ( :white_flower: requires Peach version **0.9.8**)

:bell: You don't need to write or change anything, if your settings are exactly the same as default! This way, you can have most compatible way to work with Peach with possible future updates.

If you don't like the way Peach presents the navbar, you can always customize it by changing template file `navbar.html`.