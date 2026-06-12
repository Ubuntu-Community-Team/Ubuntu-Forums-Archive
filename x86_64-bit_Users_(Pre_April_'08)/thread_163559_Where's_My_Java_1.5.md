---
title: "Where's My Java 1.5?"
date: 2006-04-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by AlphaMack on 2006-04-21
I followed the instructions for installing IBM's JRE as per the JavaPPC Wiki page.  When I get to the step where I need to sudo update-alternatives --config java, it's not even listed.  (Yes, the deb package was installed and set up).

Here's the output:

```
$ sudo update-alternatives --config java

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
*+    2        /usr/lib/jvm/java-gcj/bin/java

Press enter to keep the default[*], or type selection number:

```

I've added the path to my .bashrc and everything else according to the Wiki.  So what am I doing wrong?

Edit:  I noticed that /usr/lib/j2re1.5-ibm/ is missing.

---

### Post by bugme on 2006-04-28
same prob, dont know whats going on but you should find ibm java in /opt/ibm/

how do we make it an option in update-alternatives ?

---

