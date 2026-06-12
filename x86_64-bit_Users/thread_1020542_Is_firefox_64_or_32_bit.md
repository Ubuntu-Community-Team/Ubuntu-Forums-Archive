---
title: "Is firefox 64 or 32 bit?"
date: 2008-12-24
forum: x86 64-bit Users
---

### Post by stormtrooprdave on 2008-12-24
I'm using Intrepid with the default Firefox installed.  Is it 64 bit or 32?  How can I tell?

---

### Post by SuperSonic4 on 2008-12-24
In firefox; Help -> About

```
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.5) Gecko/2008121621 Ubuntu/8.04 (hardy) Firefox/3.0.
```

if it says x86_64 where mine says i686 then you are running 64 bit firefox

---

### Post by roelpeeters on 2008-12-24
In general when you are searching to understand if a program is 32 bit or 64-bit, you can use the **file** program from the commandline. In a terminal window do the following:

```
roel@stardust64:/usr/lib/firefox-3.0.5$ file firefox
firefox: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), for GNU/Linux 2.6.8, dynamically linked (uses shared libs), stripped

```

It shows it is a 64-bit executable. Sometimes you have to try to find the real executable instead of the shell script that starts it. In this case you will find the firefox executable in /usr/lib/firefox-3.0.5

---

