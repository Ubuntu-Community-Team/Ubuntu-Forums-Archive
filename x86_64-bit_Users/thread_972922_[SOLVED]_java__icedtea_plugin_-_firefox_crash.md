---
title: "[SOLVED] java / icedtea plugin - firefox crash"
date: 2008-11-06
forum: x86 64-bit Users
---

### Post by SnakeHips on 2008-11-06
Intrepid Ibex 8.10

Well..... I had the java thing working and run a couple of updates and well ....... errr ......now when I got java.com and check version it kills Firefox.....any ideas?

I removed Java through Synaptic ,re-booted ,re-installed ,re-booted and terminal gives this..

pete@desk:~$ java -version
java version "1.6.0_0"
IcedTea6 1.3.1 (6b12-0ubuntu6) Runtime Environment (build 1.6.0_0-b12)
OpenJDK 64-Bit Server VM (build 1.6.0_0-b12, mixed mode)


Cant find any clues in var/log/messages.

Any ideas ,maybe which of the updates has caused the problem?

---

### Post by Thelasko on 2008-11-06
If you search for "java" in synaptic, what packages are installed?

---

### Post by SnakeHips on 2008-11-06
> **Thelasko said:**
> If you search for "java" in synaptic, what packages are installed?

ca-certificates-java
dbus
gcj-4.2-base
gcj-4.3-base
gdb
icedtea6-plugin
java-common
libaccess-bridge-java
libdbus-1-3
libgcj8-1
libgcj8-jar
libgcj9-0
libgcj9-jar
libgcj-common
libgtksourceview-common
libgtksourceview2.0-common
libtext-java
libswt3.2-gtk-gcj
libswt3.2-gtk-java
libswt3.2-gtk-jni
libxml-sax-perl
openjdk-6-jre
openjdk-6-jre-headless
openjdk-6-jre-liphp-cli
php-common
php-gd
rhino
tzdata-java

That's the lot ,thanks for any help you can give...

---

### Post by Thelasko on 2008-11-06
I'm still on Hardy, so I'm a little behind the times.  Try getting rid of "gcj-4.2-base" and "gcj-4.3-base" but make sure you leave the openjdk packages installed when you do so.  On Hardy gcj and openjdk don't play nice with each other, they probably don't in Intrepid either.

---

### Post by SnakeHips on 2008-11-06
> **Thelasko said:**
> I'm still on Hardy, so I'm a little behind the times.  Try getting rid of "gcj-4.2-base" and "gcj-4.3-base" but make sure you leave the openjdk packages installed when you do so.  On Hardy gcj and openjdk don't play nice with each other, they probably don't in Intrepid either.

I removed the "gcj-4.2-base" package and it works now ,cheers!

---

### Post by jru on 2008-11-11
Thanks Thelasko! 

I was having (read struggling) with the same problem with firefox 3.0.3 on Ubuntu Intrepid Ibex 8.10 64bits: Java Applets would often hang the browser.
Removing Java gcj-4.x.base using synaptic fixed it: Gcj and Icedtea are incompatible... that's a hellish bug to figure out without help like yours.

Your help plus this link:
[http://www.howtoforge.com/installing-adobe-flash-10-on-a-64bit-ubuntu-8.04](http://www.howtoforge.com/installing-adobe-flash-10-on-a-64bit-ubuntu-8.04)
and removing all add-ons (with firefox -safe-mode)  ... and now it looks like I have a browser again...

---

### Post by Thelasko on 2008-11-12
I've filed a [bug report.]("https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/297246")

---

### Post by fsando on 2008-12-30
I don't think gcj-4.x.base is a problem, at least not directly. It may rather be that some of its dependencies are at fault. So when gcj-4 is removed the offending package is removed too.


I'm a bit surprised how I got my setup working. I had all the problems above, hanging browser, cpu at 100%.
Then I *thought* i uninstalled gcj-4.x.base but that action doesn't appear in synaptic history and it is still installed so I guess I didn't.
What i did though was uninstalling all java plugins sun5,sun6 openjava icedtea - everything
After that I deleted (renamed) ~/.java
Then reinstalled sun-java6 plugin (still didn't work) and then icedtea and then it worked.

Perhaps some corruption or perhaps firefox mix several things together?

Here are some entries from my synaptic history (some duplicate installs/uninstalls left out)
```

**Commit Log for Tue Dec 30 12:39:32 2008**
Removed the following packages:
sun-java5-bin
sun-java5-demo
sun-java5-jdk
sun-java5-jre
sun-java5-plugin

**Commit Log for Tue Dec 30 12:51:49 2008**
Removed the following packages:
icedtea6-plugin

**Commit Log for Tue Dec 30 12:57:46 2008**
Removed the following packages:
cacao-oj6-plugin
default-jre-headless
openjdk-6-jre
openjdk-6-jre-headless
openjdk-6-jre-lib

**Commit Log for Tue Dec 30 12:58:38 2008**
Removed the following packages:
ca-certificates-java
cacao-oj6-jre
cacao-oj6-jre-headless
cacao-oj6-jre-lib

**Commit Log for Tue Dec 30 13:12:21 2008**
Removed the following packages:
sun-java6-bin
sun-java6-jre
sun-java6-plugin

**Remark: removed ~/.java**

**Commit Log for Tue Dec 30 13:14:11 2008**
Installed the following packages:
sun-java6-bin (6-10-0ubuntu2)
sun-java6-jre (6-10-0ubuntu2)
sun-java6-plugin (6-10-0ubuntu2)

**Commit Log for Tue Dec 30 13:31:06 2008**
Installed the following packages:
ca-certificates-java (20080712ubuntu3)
icedtea6-plugin (6b12-0ubuntu6)
openjdk-6-jre (6b12-0ubuntu6)
openjdk-6-jre-headless (6b12-0ubuntu6)
openjdk-6-jre-lib (6b12-0ubuntu6)


```

---

