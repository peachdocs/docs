---
name: Upgrade
---

# Upgrade Peach

If you installed Peach from source code, you can then simply execute following command to upgrade Peach binary:

```sh
$ go get -u github.com/peachdocs/peach
```

Then in all of your project directories, you should do following steps for each of them:

1. Remove current default `conf`, `public` and `templates` directories.
2. Copy over latest version of those directories.
3. Check with change log, make sure there is no compatibility issues.
4. Make necessary changes in your custom `templates` and `public` directories to fix any possible compatibility issues.