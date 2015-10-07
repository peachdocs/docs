---
name: FAQs
---

# FAQs

### How to I use reverse proxy with NGINX?

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