---
name: FAQs
---

# FAQs

### How do I use reverse proxy with NGINX?

Here is an example of NGINX config section, but values can be different from your situation:

```nginx
server {
	listen 80;
	server_name peachdocs.org;
	
	location / {
		proxy_pass http://localhost:5556;
	}
}
```

### Does my custom directory have to be a Git repository?

No, your custom directory does not have to be a Git repository, it's just a best practice to sync and backup your custom things.

### How do I setup single language documentation?

By default, Peach requires you have two language versions of documentation (`en-US` and `zh-CN`); otherwise it will give an error about missing documentation. To use single language documentation, you need to make similar changes in your `custom/app.ini` as follows:

```
[i18n]
LANGS = en-US
NAMES = English
```
