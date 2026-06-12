---
title: "sun java and firefox plugin"
date: 2005-10-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by rush_ad on 2005-10-15
i downloaded the sun java jre and installed it.

rushad@patel-dorm:~$ java -version
java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_05-b05, mixed mode)

the above code shows java installed properly.

but the problem is that there is no 'plugin' directory in the java installation folder. so how do i setup firefox plugin???

---

### Post by DancingSun on 2005-10-15
[QUOTE=rush_ad]i downloaded the sun java jre and installed it.

rushad@patel-dorm:~$ java -version
java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_05-b05, mixed mode)

the above code shows java installed properly.

but the problem is that there is no 'plugin' directory in the java installation folder. so how do i setup firefox plugin???[/QUOTE]
There's no Sun Java plugin for the AMD64 platform yet.  You'll need to get Blackdown Java for that.

---

### Post by rush_ad on 2005-10-15
that sucks.

---

### Post by freakzilla on 2005-10-16
Will programs such as Azureus run for amd64 in breezy?

---

### Post by DancingSun on 2005-10-16
Yes, in fact, I have Azureus running right now. :D
You just need to install Java.

---

### Post by Aphorism on 2005-10-16
Just to clear things up:

Blackdown's java is an alternative to Sun's java.  Sun recently released an amd64 port of their java implementation ([https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)) but, as of this writing, there is no Mozilla plugin for it.  Time will tell...

If you wish to run Java apps in the amd64 version, both Sun's and Blackdown's will work.  If you wish to run embedded Java apps in Mozilla or its kin, you have only Blackdown's to support.

Personally, considering how Sun is -- and their horrible proprietary goals behind Java -- I would suggest supporting Blackdown's and work out the bugs.

---

