---
name: Config Cheat Sheet
---

# Configuration Cheat Sheet

Before we get started, make sure you know that any change of configuration should be made in `custom/app.ini` file, and uses [INI](https://en.wikipedia.org/wiki/INI_file) syntax.

Also, this document only covers config options that are not mentioned anywhere else in the documentation.

## Site

```ini
# Site level configuration
[site]
# Name for your Peach instance
NAME = Peach Server
# HTML description meta
DESC = Peach is a web server for multi-language, real-time update and searchable documentation.
# Use CDN to load static resources, but Google Font will always be fetched from CDN
USE_CDN = true
# Your site URL to be accessed by other people
URL = http://localhost:5555
```

## Page

```ini
[page]
# Set to false means no home page for the site, and always redirect users to documentation page
HAS_LANDING_PAGE = true
```