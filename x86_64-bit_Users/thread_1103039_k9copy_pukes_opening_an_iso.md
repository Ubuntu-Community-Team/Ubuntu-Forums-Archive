---
title: "k9copy pukes opening an iso"
date: 2009-03-22
forum: x86 64-bit Users
---

### Post by lingenfr on 2009-03-22
I just did a fresh install of k9copy. When I try to open an iso of a DVD it crashes with the following information:

Application: k9copy (k9copy), signal SIGABRT
0x00007f5b38ec16e1 in nanosleep () from /lib/libc.so.6
[Current thread is 0 (LWP 9639)]

Thread 2 (Thread 0x42045950 (LWP 9644)):
#0  0x00007f5b38ef84b2 in select () from /lib/libc.so.6
#1  0x00007f5b3b030006 in ?? () from /usr/lib/libQtCore.so.4
#2  0x00007f5b3af67362 in ?? () from /usr/lib/libQtCore.so.4
#3  0x00007f5b376243ea in start_thread () from /lib/libpthread.so.0
#4  0x00007f5b38effcbd in clone () from /lib/libc.so.6
#5  0x0000000000000000 in ?? ()

Thread 1 (Thread 0x7f5b3ccb5730 (LWP 9639)):
[KCrash Handler]
#5  0x00007f5b38e4c015 in raise () from /lib/libc.so.6
#6  0x00007f5b38e4db83 in abort () from /lib/libc.so.6
#7  0x00007f5b3af5f6b5 in qt_message_output () from /usr/lib/libQtCore.so.4
#8  0x00007f5b3af5f7fd in qFatal () from /usr/lib/libQtCore.so.4
#9  0x00000000004a0c89 in ?? ()
#10 0x000000000046de0c in _start ()

If I try to just rip the DVD to avi, it comes back immediately and says it is finished, but nothing happens. Thanks.

---

