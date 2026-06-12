---
title: "Should I use the repo's to get Flash and Java?"
date: 2009-01-29
forum: x86 64-bit Users
---

### Post by novafluxx on 2009-01-29
Just wiped my entire drive, and installed AMD64 Ubuntu last night (Is there a difference between AMD64 and Intel 64 cause my laptop has an Intel CPU) and I was wondering if its as easy as it looks. Can I just install flash and Java from the repo's or do I need to do something special?

I plan on using Firefox that came with the installation if that changes anything.

---

### Post by jerome1232 on 2009-01-29
Yes you can install flash and java from the repos BUT

The flash you install will be the 32 bit Adobes flash, along with a plugin wrapper that makes it work on 64 bit.

The Java you download will be OpenJDK, and icedtea not sun's java. They work fine for me but some people will need sun's version. I think suns java is actually in the repos as well I just never had problems with openJDK and have never felt the need to switch.

---

### Post by novafluxx on 2009-01-29
is Sun's Java not available in the repo's for 64bit ubuntu?

This is my first 64bit OS, so I'm brand new...and im sorta new to Linux too

---

### Post by sanderj on 2009-01-29
> **novafluxx said:**
> Can I just install flash and Java from the repo's?


Yes, you can. Be careful to select the Java you want; there's also some kind of open source Java, which I don't like to have.

---

### Post by jespdj on 2009-01-29
> **novafluxx said:**
> is Sun's Java not available in the repo's for 64bit ubuntu?
Yes it is:
```
sudo apt-get install sun-java6-jre
```
Look on [http://packages.ubuntu.com/](http://packages.ubuntu.com/) to search for packages.

But: There is no browser plug-in for 64-bit Sun Java yet (Sun has promised that it's coming in the next update of their Java - Java 6 update 12).

If you need to run Java in Firefox, try OpenJDK Java with the IcedTea plugin first:
```
sudo apt-get install icedtea6-plugin
```
Unfortunately not all Java applets work with it, because OpenJDK is not yet 100% compatible with Sun Java.

There is a beta version of Sun Java 6 update 12 available, if  OpenJDK/IcedTea don't work you can install that (there are a number of threads in the forum about how to download and install it).

> **sanderj said:**
> ... there's also some kind of open source Java, which I don't like to have.
Why not? Do you know what OpenJDK Java is? It's Sun's project to make their own Java open source. OpenJDK Java is 95% the same as Sun Java 6, with proprietary parts (stuff from third parties that Sun used in their Java 6) replaced by open source software. OpenJDK Java is almost as good as Sun Java 6, and it's fully open source.

---

### Post by novafluxx on 2009-01-29
So icedtea is the Java plugin for the browser, and OpenJDK is the open Java runtime that I can install?

What is nswrapper and what are its advantages/disadvantages?

When I got to add/remove programs, I search for flash, and the Adobe flash come up, so if I check that, it will install what I need to get flash in firefox, right?

If I install OpenJDK, it will only install the runtime, not the plugin, correct?

---

### Post by Kilz on 2009-01-29
> **novafluxx said:**
> So icedtea is the Java plugin for the browser, and OpenJDK is the open Java runtime that I can install?

What is nswrapper and what are its advantages/disadvantages?



nspluginwrapper = the only way for 64bit browsers to use flash until recently.
If you are a new user and just want flash to work without messing around with it, install flashplugin-nonfree from the repos.
If you are the kind of person that loves to tweak things and dosent mind things not working while you fix it, or likes to track when the next version of the beta is out to manually replace it. go with the flash 64bit flash ALPHA.

But 

**THIS IS ALL IN THE STICKY POSTS!**

---

### Post by novafluxx on 2009-01-29
The sticky, as informative as it is, only tells me what to do, not explaining what exactly I'm doing. I don't know what nswrapper is, I sort of understand what it does but I'd like some more details.

I can't learn anything just by copying and pasting terminal commands from a forum! Thats why I asked for more detail.

---

### Post by jespdj on 2009-01-30
> **novafluxx said:**
> So icedtea is the Java plugin for the browser, and OpenJDK is the open Java runtime that I can install?
Yes.

> When I got to add/remove programs, I search for flash, and the Adobe flash come up, so if I check that, it will install what I need to get flash in firefox, right?
Yes.

> If I install OpenJDK, it will only install the runtime, not the plugin, correct?
Yes.

---

### Post by Kilz on 2009-01-30
> **novafluxx said:**
> The sticky, as informative as it is, only tells me what to do, not explaining what exactly I'm doing. I don't know what nswrapper is, I sort of understand what it does but I'd like some more details.

I can't learn anything just by copying and pasting terminal commands from a forum! Thats why I asked for more detail.

Yes you can learn from the stickies, They have a lot of information. They do not contain only copy and paste info. [you can also use google.]("http://www.letmegooglethatforyou.com/?q=what+is+nspluginwrapper")

---

