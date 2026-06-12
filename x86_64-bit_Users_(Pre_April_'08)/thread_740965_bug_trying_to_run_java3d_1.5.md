---
title: "bug trying to run java3d 1.5"
date: 2008-03-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by tickletik on 2008-03-31
Have no problems installing java3d 1.5, compiles examples fine, but when I try to run it, I get the following error:

#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002aba8abe4df0, pid=14678, tid=1093912912
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (1.6.0_03-b05 mixed mode)
# Problematic frame:
# C  [libc.so.6+0x79df0]  memset+0x60
#
# An error report file with more information is saved as hs_err_pid14678.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#


This happens even when I try to run the most basic java3d example:

[http://www.java3d.org/starting.html](http://www.java3d.org/starting.html)

While I'm not going to be using java3d for a long while yet, it would be nice if I can get the damn thing to work.  I checked google before this, and the only posts I've seen were very discouraging.  Maybe there's a supergenius running around the forums who can solve this problem?  

:(

-ron

---

### Post by xlinuks on 2008-03-31
Try the latest JDK realease, it's 1.6.0_05-b13 (jdk-6u5-linux-x64.bin from java.sun.com), perhaps it helps. If not, try Java version 5.

---

