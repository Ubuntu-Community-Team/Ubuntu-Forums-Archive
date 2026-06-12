---
title: "32-bit Java Firefox plugin for all users"
date: 2006-11-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by gwi on 2006-11-14
I am using the AMD64 version of Ubuntu 6.06. I have installed 32-bit Firefox, and installed the Java runtime (as described in [Howto Install 32 bit Firefox with Flash w/sound and Java for AMD64](http://www.ubuntuforums.org/showthread.php?t=202537)).

The plugin only shows up when the user that installed the JRE goes to about : plugins in Firefox. When another user does this, the JRE does not show up (and sites using Java don't function). World has read access to /usr/local/java32. All users have a .java directory in their home directory.

How can I enable the Firefox plugin for all users (of which only one can act as su to install the JRE)?

---

### Post by Kilz on 2006-11-14
> **gwi said:**
> I am using the AMD64 version of Ubuntu 6.06. I have installed 32-bit Firefox, and installed the Java runtime (as described in [Howto Install 32 bit Firefox with Flash w/sound and Java for AMD64](http://www.ubuntuforums.org/showthread.php?t=202537)).

The plugin only shows up when the user that installed the JRE goes to about : plugins in Firefox. When another user does this, the JRE does not show up (and sites using Java don't function). World has read access to /usr/local/java32. All users have a .java directory in their home directory.

How can I enable the Firefox plugin for all users (of which only one can act as su to install the JRE)?

The following command should solve the problem. You will need to edit it, replace Yourlogin with the name you login with.

```
sudo chown -R Yourlogin:users /usr/local/firefox32/plugins
```

---

### Post by gwi on 2006-11-15
Suppose I have two users: john and mary. When I do a
```
sudo chown -R john:users /usr/local/firefox32/plugins
```
to solve the problem for user john, will this solve the problem for user mary?

---

### Post by Kilz on 2006-11-15
> **gwi said:**
> Suppose I have two users: john and mary. When I do a
```
sudo chown -R john:users /usr/local/firefox32/plugins
```
to solve the problem for user john, will this solve the problem for user mary?

It should, since both are members of the users group.

---

