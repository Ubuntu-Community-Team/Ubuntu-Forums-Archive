---
title: "[SOLVED] Sun Java 6 runtime won't install"
date: 2008-09-03
forum: x86 64-bit Users
---

### Post by Oldhacker on 2008-09-03
Attempting to install Sun Java6 runtime from Add/Remove, I receive the following error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I am running Ubuntu on an AMD 64.

What should I do to get Java installed?

Thanks,

---

### Post by tuxxy on 2008-09-03
Run this command in terminal

```
sudo dpkg --configure -a
```

Then try again

---

### Post by Oldhacker on 2008-09-04
When I took your suggestion, add/remove showed that Java6 runtime was already installed ???

Then, when I attempted to add a java program (PLCash, that I have used for years on SUSE) with java -jar PLCash.jar, it gave the following errors:

The program 'java' can be found in the following packages:
 * java-gcj-compat-headless
 * openjdk-6-jre-headless
 * cacao
 * j2re1.4
 * kaffe
 * jamvm
 * gij-4.1
 * gij-4.2
 * sablevm
Try: sudo apt-get install <selected package>
bash: java: command not found

IS Ubuntu that much more difficult for some things than openSUSE?
Just when I was starting to think of switching, I run into a roadblock.

All pertinent suggestions are still welcome,

---

### Post by philinux on 2008-09-04
Basic stuff apologies if you've done this.
Did you cd to the directory where the jar file resides?

If you downloaded to your desktop then you need

cd Desktop

Note the capital.

---

### Post by Oldhacker on 2008-09-04
I just received two Sun Java updates, and now the Java installation of
PLCash worked!

Thanks to all for the pointers. :)

---

