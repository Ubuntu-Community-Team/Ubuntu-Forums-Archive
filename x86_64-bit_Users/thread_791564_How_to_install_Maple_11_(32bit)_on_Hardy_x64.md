---
title: "How to install Maple 11 (32bit) on Hardy x64"
date: 2008-05-12
forum: x86 64-bit Users
---

### Post by ginbuntu on 2008-05-12
Here is how to install Maple 11 (32bit) on Hardy x64.

Before you install Maple 11 (32bit), you need to install the package ia32-libs

```
 sudo apt-get install ia32-libs
```

Now just install Maple 11 the usual way, after install go to your installation directory and do the following

```
cp -rf bin.IBM_INTEL_LINUX bin.X86_64_LINUX
```
```
cp -rf  jre.IBM_INTEL_LINUX jre.X86_64_LINUX
```

Then run the file xmaple in the bin directory. If you have compiz enabled (you'll see a blank window if you have it enabled), then refer to this thread
[http://ubuntuforums.org/showthread.php?t=450064&highlight=maple+11](http://ubuntuforums.org/showthread.php?t=450064&highlight=maple+11)

ps. don't forget to put the license file in place.

g'luck

---

### Post by freemath on 2009-06-19
Works for me. I'm using Maple 10 (32-bit) on Jaunty (64-bit). Thanks!

---

### Post by calsaverini on 2009-07-16
The solution presented in the link doesn't work for me with Maple12 on Ubuntu Jaunty (both 64 bits version).

When I use: 
```

export AWT_TOOLKIT=MToolkit;

``` 
o my *.bashrc* and try to run xmaple I get the followin error message:

```

[pcmec43] ~ > xmaple
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007fbb33e9b58f, pid=18555, tid=140441289427280
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (1.6.0-b105 mixed mode)
# Problematic frame:
# C  [libc.so.6+0x3158f]  catgets+0x1f
#
# An error report file with more information is saved as hs_err_pid18555.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted


```

---

