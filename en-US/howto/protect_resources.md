---
name: Protect Resources
---

# Protect Internal Resources

:white_flower: Requires Peach version **0.9.0**

When some documents are internal use only, you can enable protect mode for them.

What does protect mode do?

1. Authentication based on HTTP Basic Authorization.
2. User defines a list of authorized users along with their password.
3. User defines a list of resources to be protected and individuals who can access.

To enable protect mode, you would need to create a file named `protect.ini` and put it in same directory as your `TOC.ini` does.

Here is an example:

```ini
[user]
user1 = 5F4DCC3B5AA765D61D8327DEB882CF99
user2 = xxx
user3 = xxx

[auth]
howto/documentation = user1,user2,user3
howto/webhook = user1,user2
howto/templates = user1
```

User password must be MD5-encoded, and use comma (`,`) to seperate multiple users.

Document URLs do not need `/docs/` prefix as you can tell.

Based on example file, there are three users are authorized, and three resources are protected:

- `user1` has all access to three resources.
- `user2` can only access `howto/documentation` and `howto/webhook`, and gets **403** when tries to access `howto/templates`.
- `user3` can only access `howto/documentation`, and gets **403** when tries to access `howto/webhook` and `howto/templates`.
- Fail to authenticate will result in **401**.