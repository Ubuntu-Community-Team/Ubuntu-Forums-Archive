---
title: "Major XGL issues"
date: 2006-08-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by modestmelody on 2006-08-12
I tried following the guide posted on here for XGL/Compiz without any success and now have broken packages I can't fix in my install.

I had been trying to install cdwg since I thought that was part of the problem I was having, but ran into an issue involving libcairo-2, which I was able to install but hten had problems with libglitz-1 and libglitz-1-dev taht were needed.  When attempting to install libglitz-1-dev (libglitz-1 is listed as installed) this is the error I get:
(Reading database ... 102871 files and directories currently installed.)
Unpacking libglitz1-dev (from .../libglitz1-dev_0.5.3-0ubuntu2_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libglitz1-dev_0.5.3-0ubuntu2_amd64.deb (--unpack):
 trying to overwrite `/usr/include/glitz.h', which is also in package glitz-cvs
Errors were encountered while processing:
 /var/cache/apt/archives/libglitz1-dev_0.5.3-0ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
jason@jason-desktop:~$ sudo synaptic
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)

Also, trying to install XGL/Compiz has broken Twinview in favor of a single widescreen stretch.  I am just looking to rmove everything that I did and stp back and try again but with this broken package I'm running into some trouble.

---

### Post by modestmelody on 2006-08-12
Basically, at the point, when I type:
compiz --replace
I get a white screen and nothing else.

---

