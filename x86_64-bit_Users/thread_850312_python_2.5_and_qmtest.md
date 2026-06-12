---
title: "python 2.5 and qmtest"
date: 2008-07-05
forum: x86 64-bit Users
---

### Post by lmdavid on 2008-07-05
Hi,

I have recently tried to run qmtest with python 2.5 (default on my ubuntu Hardy installation) and I had the following problem:
user@ubuntu:~/tdb$ qmtest gui
QMTest running at [http://127.0.0.1:39292/test/dir](http://127.0.0.1:39292/test/dir)
Segmentation fault

GDB is giving the following stack trace:
QMTest running at [http://127.0.0.1:59316/test/dir](http://127.0.0.1:59316/test/dir)
(no debugging symbols found)
(no debugging symbols found)

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0x7f86d6c5d6e0 (LWP 21321)]
0x0000000000443897 in PyDict_SetItem ()
(gdb) info stack
#0  0x0000000000443897 in PyDict_SetItem ()
#1  0x00000000004439bb in PyDict_SetItemString ()
#2  0x00007f86d258a3cc in initMissing () from /usr/lib/python2.5/site-packages/Missing.so
#3  0x00000000004a39c3 in _PyImport_LoadDynamicModule ()
#4  0x00000000004a1809 in ?? ()
#5  0x00000000004a1cdb in ?? ()
#6  0x00000000004a1f1a in ?? ()
#7  0x00000000004a23c5 in PyImport_ImportModuleLevel ()
#8  0x0000000000481a19 in ?? ()
#9  0x0000000000417e73 in PyObject_Call ()
#10 0x0000000000481fc2 in PyEval_CallObjectWithKeywords ()

I have python2.5 (2.5.2-2ubuntu4) and  python-extclass  (1.2.0zope-2.5.1-5build1). 
I suppose it is the later package that is at the origin of the problem because it contains the shared library "Missing.so" issuing the segmentation fault. I suppose that there is a module that has not been found and it is defaulting to "Missing.so" as it was mentioned at [http://www.codesourcery.com/archives/qmtest/msg01240.html](http://www.codesourcery.com/archives/qmtest/msg01240.html) .

I found a sort of workaround: removing (or renaming) the shared library Missing.so. It then seems to work at least for qmtest.


My config:
     *-cpu
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4800+
          vendor: Advanced Micro Devices [AMD]
          physical id: a
          bus info: cpu@0
          width: 64 bits

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"

Linux multimedia 2.6.24-19-generic #1 SMP Wed Jun 18 14:15:37 UTC 2008 x86_64 GNU/Linux

---

