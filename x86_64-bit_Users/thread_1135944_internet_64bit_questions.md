---
title: "internet 64bit questions"
date: 2009-04-24
forum: x86 64-bit Users
---

### Post by origr15 on 2009-04-24
im about to install ubuntu 64 bit and i know there is no real flash for 64 bit firefox so i ask , which is better - gnash how will run nativly on 64 or flash which was mad for 32 but with a wiered program that will let me use it? because i want my firefox to rus as fast as posibale which i dont think will happen with 32bit made softwere... please help

oh and is there a way to use google toolbar with the bookmarks in 64 bit?

---

### Post by jespdj on 2009-04-24
If you install Flash on 64-bit Ubuntu Jaunty (by installing the package **flashplugin-nonfree**), then you will get the 32-bit version of Flash 10 installed with nspluginwrapper (a wrapper to make the 32-bit plugin work on 64-bit Firefox). This works without any problems, and is the recommended way to get Flash working on 64-bit Ubuntu.

There is, however, also a 64-bit native version of Flash 10 available, but it's still an alpha or beta version. If you really want that, then search around in this forum, there are several installation guides.

gnash is really not that good, it does not support many of the features of Adobe Flash, so it will not work with a lot of Flash stuff on websites.

---

### Post by Arup on 2009-04-24
The alpha x64 Flash 10 plugin works very good, just download the tar, untar it and copy the libflashplayer.so to /usr/lib/mozila/plugins and everything works fine.

---

### Post by origr15 on 2009-04-25
tnx , i'll try the 64bit version of flash

---

### Post by ubuntu27 on 2009-04-25
The new Ubuntu 9.04 (64-bit) seems to install Flash 64bit by default it seems.

You do not need to follow any guide or run a script.

Just install Flash like always

```
sudo apt-get install flashplugin-installer
```

See:

[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/310031](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/310031)


EDIT: Ok, nevermind.
Looks like they reverted back to the way it was before...

---

