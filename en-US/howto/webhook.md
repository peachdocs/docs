---
name: Sync with Webhook
---

# Sync with Webhook

Obviously, you don't want to login to your server and update documentation manully every time you make a change, especially when change is very small.

Peach provides ability to sync your documentation at real-time through webhook.

So the first thing you need to do is [setting up your documentation](documentation) as a [Git repository](documentation#git-repository).

You can then set the webhook secret in your `custom/app.ini`:

```ini
[docs]
SECRET = mysecret
```

The format and URL path for trigger a hook is `POST /hook?secret={secret}`, you can see `secret` is pass by URL query.

Note that the `secret` is only valid when URL query and `SECRET` are matched **exactly**, so if `SECRET` is empty, URL query of secret must be empty, vice versa.

## GitHub

Here is an example of how to setup Peach webhook on GitHub, but elsewhere is almost same.

1. Go to your documentation repository new webhook page (`/:username/:reponame/settings/hooks/new`)
2. Fill in **Payload URL** with hook URL path, for example, `http://peachdocs.org/hook?secret=mypeach`.
3. Click `Add webhook`, and you're all set. :tada:

![](/docs/images/github_webhook.png)

Now every time you push or merge Pull Request on GitHub, your Peach instance will automatically update documentation to the latest version.