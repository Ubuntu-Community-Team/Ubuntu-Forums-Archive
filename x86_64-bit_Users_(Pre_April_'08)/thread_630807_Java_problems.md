---
title: "Java problems"
date: 2007-12-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by tom the newb on 2007-12-03
The ice tea java plugin doesn't work with Sun java menu systems or website code.  I downloaded the latest java for AMD 64 platforms.  Since this is my first attempt at Linux, I can't get the binary file to install.  The iced tea that loads into Fedora does work but that distro isn't as user friendly (or so I thought).  If anyone can help I would appreciate it.

---

### Post by Kilz on 2007-12-03
> **tom the newb said:**
> The ice tea java plugin doesn't work with Sun java menu systems or website code.  I downloaded the latest java for AMD 64 platforms.  Since this is my first attempt at Linux, I can't get the binary file to install.  The iced tea that loads into Fedora does work but that distro isn't as user friendly (or so I thought).  If anyone can help I would appreciate it.

icedtea isnt from sun. Its an open source project. It isnt perfect as you are seeing. It will load some sites but not all. There is also no 64bit sun java plugin. That will come when java 7 is released, but that isnt ready yet. If you need the functionality of a sun java plugin you can install a 32bt browser and 32bit java. [I have a script that will install it ]("http://ubuntuforums.org/showthread.php?p=1174435")by answering a few yes/no questions.

---

### Post by Ehtetur on 2007-12-03
If you want to stay w/ 64 bit, Blackdown Java provides a 64-bit plugin.
You need to enable multiverse repos to install it - (**j2re1.4-mozilla-plugin**)..
The downside is that it's version 1.4.2 and it's actively maintained.
I'm using it with firefox and swift-weasel.

---

### Post by Kilz on 2007-12-03
> **Ehtetur said:**
> If you want to stay w/ 64 bit, Blackdown Java provides a 64-bit plugin.
You need to enable multiverse repos to install it - (**j2re1.4-mozilla-plugin**)..
The downside is that it's version 1.4.2 and it's actively maintained.
I'm using it with firefox and swift-weasel.

Blackdown is not maintained. Its not sun java, its an older open source plugin with even worse security and compatibility that the icedtea the original poster said would not work for them. If you are going to recommend it to people at least warn them of the lack of a security manager in Blackdown and the security risk it poses.

---

### Post by tszanon on 2007-12-04
If I recall correctly, I read some time ago that Sun was finally going to release a 64bit plugin for linux in the near future. Does anyone know how is it going?

---

### Post by tom the newb on 2007-12-04
Java.com  lists a browser plugin for Linux 64 platforms.  The file name is jre-1_5_0_02-linux-amd64-rpm.bin. That is the binary file that I need help installing.

---

### Post by jespdj on 2007-12-04
That is not a Java browser plug-in. It is the JRE (Java Runtime Environment), which is the software you need to run Java programs on your computer. The current  64-bit version of Sun's JRE does not include a Java browser plug-in.

---

### Post by smileone on 2007-12-05
I use gcjwebplugin with mozilla-firefox and it work perfectly.
Gcjwebplugin use gcj, it is open-source compiler.

---

