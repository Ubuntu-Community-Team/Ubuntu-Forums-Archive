---
title: "eclipse 3.2 error when starting"
date: 2006-09-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by toniocus on 2006-09-02
Hi everybody,

I was trying to upgrade to eclipse 3.2, I'm using
sun's jdk 1.5.0_08 and I have a strange problem
with eclipse 3.2 version.

When I try to create a new workspace, and every
now and then while I'm working with it, this error apears:

======================================================
LoadPlugin: **failed to initialize shared library libXt.so** [libXt.so: cannot open shared object file: No such file or directory]
LoadPlugin: **failed to initialize shared library libXext.so** [libXext.so: cannot open shared object file: No such file or directory]
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0x00002aaaef527f89, pid=22638, tid=46912501790416
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (1.5.0_08-b03 mixed mode)
# Problematic frame:
# C  [libgkplugin.so+0x27f89]
#
# An error report file with more information is saved as hs_err_pid22638.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#

======================================================
I asume the java error is just because it cannot
load the X libs.

It seems to me that some "module" is trying to fetch
the 32 bit version of libXt.so and libXext.so, because
both of them are installed in my system, and 3.1
is running correctly.

Any other ideas will be great,
thanks in advance
tonioc

---

### Post by toniocus on 2006-09-02
32 bit version of eclipse 3.2 seems
to work fine in my chroot environment.

---

