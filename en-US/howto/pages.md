---
name: Add Pages
---

# Add Single Pages

We understand the needs of showing pages as part of website other than the part of documentation, so Peach also supports to specify what files should be treated as single pages.

In your `TOC.ini` file, add a section named `[pages]`:

```ini
[pages]
-: donate
```

Then you should put file(s) is(are) named `donate.md` under root directory of every supported language.

For example, you support `en-US` and `zh-CN`, then you should have two following files:

- `/en-US/donate.md`
- `/zh-CN/donate.md`

However, the **rule of default language** will also apply that if you only have this file in default language version, the content of default language version will be presented when user's preferred language is not default language.

The URL path to access this page, will then be `/donate`, which is same as file name without `.md` extension.

Last but not the least, you can have as many as single pages you want, just define them in the `TOC.ini` file.