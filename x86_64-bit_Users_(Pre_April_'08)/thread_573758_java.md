---
title: "java"
date: 2007-10-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by Silent_Hunter on 2007-10-11
Does java work as 64 bit in a 64 bit browser yet? I read that java would not be in 64 bit until java 7 was released. When is the release date? Then I found a 64 bit java version 1.5.

[http://www.java.com/en/download/help/5000011400.xml](http://www.java.com/en/download/help/5000011400.xml)

Does that work as a 64 bit java plugin in Linux? I tried 64 bit blackdown java once in IceWeasle browser, and it didn't work for yahoo games.

---

### Post by Kilz on 2007-10-12
> **Silent_Hunter said:**
> Does java work as 64 bit in a 64 bit browser yet? I read that java would not be in 64 bit until java 7 was released. When is the release date? Then I found a 64 bit java version 1.5.

[http://www.java.com/en/download/help/5000011400.xml](http://www.java.com/en/download/help/5000011400.xml)

Does that work as a 64 bit java plugin in Linux? I tried 64 bit blackdown java once in IceWeasle browser, and it didn't work for yahoo games.

Eventually Java 7 will be released and one more piece of the 64bit puzzel will be done, I cant wait for it.

If you follow that link to the download page, under the 64bit downloads is this note.

* Please use the 32-bit version for Java applet and Java Web Start support.

If you need java support there are 3 choices.

1. [install a 32bit browser and plugins.]("http://ubuntuforums.org/showthread.php?p=1174435") (this is what I would recommend)

2. Run the jgc-compat plugin that runs without a security manager that poses a security threat in that any and all applets will run. Even if they do malicious things like reformat your hard drive.

3. [Run Swiftweasel and the 64bit Blackdown 1.4.2 plugin]("http://tghc.org/forum/viewtopic.php?id=4"). Swiftweasel will crash less than Firefox. But this is not perfect as some newer sites will crash the browser.

---

### Post by Silent_Hunter on 2007-10-13
> **Kilz said:**
> 
1. [install a 32bit browser and plugins.]("http://ubuntuforums.org/showthread.php?p=1174435") (this is what I would recommend)

I did install swiftweasel32-2.0.0.7_athlon64-32bit_ubuntu-AMD64.deb. There is a problem with it. These are its dependencies.

Depends: ia32-libs, ia32-libs-gtk, linux32, gsfonts, gsfonts-x11, [COLOR="Red"]ia32-lib-firefox[/COLOR]

That package does not exist, so my package manager is broken. Swiftweasle32 is working, so how can I get the package manager to ignore the missing package that doesn't exist?

---

