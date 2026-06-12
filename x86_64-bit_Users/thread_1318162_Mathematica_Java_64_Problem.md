---
title: "Mathematica Java 64 Problem"
date: 2009-11-07
forum: x86 64-bit Users
---

### Post by fobos3 on 2009-11-07
Hi

I am running Karmic 64 bit and I've installed Mathematica. When I try to start it i.e. I type Mathematica in terminal, I get the following error message:

```
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x0633cba1, pid=6411, tid=3755686768
#
# Java VM: Java HotSpot(TM) Server VM (11.0-b15 mixed mode linux-x86)
# Problematic frame:
# V  [libjvm.so+0x33cba1]
#
# An error report file with more information is saved as:
# /home/dimitar/Downloads/hs_err_pid6411.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#
```

I installed a 32 bit version of Ubuntu in VBox and there is no problem at all.

I have sun-java6 installed from the repositories.

My question is can I fix this by installing 32 bit version of the java runtime and how do I do that.

---

