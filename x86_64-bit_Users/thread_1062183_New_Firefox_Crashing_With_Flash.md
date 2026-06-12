---
title: "New Firefox Crashing With Flash"
date: 2009-02-06
forum: x86 64-bit Users
---

### Post by mikelikespie on 2009-02-06
This just recently started to happen.

I have been running the 64 bit flash player extension just fine until now.  Now, when I load a flash app, I get a crash.  Ran in gdb mode, here's the stack trace.

```
Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0x7f1ba35e06f0 (LWP 26642)]
0x00007f1b868bb702 in ?? () from /home/mlewis/.mozilla/plugins/libflashplayer.so
(gdb) bt
#0  0x00007f1b868bb702 in ?? () from /home/mlewis/.mozilla/plugins/libflashplayer.so
#1  0x00007f1b868bb818 in ?? () from /home/mlewis/.mozilla/plugins/libflashplayer.so
#2  0x00007f1b868bbd3a in ?? () from /home/mlewis/.mozilla/plugins/libflashplayer.so
#3  0x00007f1b868bf2b2 in ?? () from /home/mlewis/.mozilla/plugins/libflashplayer.so
#4  0x00007f1b869ee605 in ?? () from /home/mlewis/.mozilla/plugins/libflashplayer.so
#5  0x00007f1b8690f99c in ?? () from /home/mlewis/.mozilla/plugins/libflashplayer.so
#6  0x00007f1b86a0b8a7 in ?? () from /home/mlewis/.mozilla/plugins/libflashplayer.so
#7  0x00007f1b866feb59 in ?? () from /home/mlewis/.mozilla/plugins/libflashplayer.so
#8  0x00007f1b866eebdf in ?? () from /home/mlewis/.mozilla/plugins/libflashplayer.so
#9  0x00007f1b9e31d4fb in ?? () from /usr/lib/libglib-2.0.so.0
#10 0x00007f1b9e31cd3b in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#11 0x00007f1b9e32050d in ?? () from /usr/lib/libglib-2.0.so.0
#12 0x00007f1b9e3206cb in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
#13 0x00007f1ba1350e5d in ?? () from /usr/lib/xulrunner-1.9.0.5/libxul.so
#14 0x00007f1ba1350fab in ?? () from /usr/lib/xulrunner-1.9.0.5/libxul.so
#15 0x00007f1ba13f75ad in ?? () from /usr/lib/xulrunner-1.9.0.5/libxul.so
#16 0x00007f1ba13cc8c2 in ?? () from /usr/lib/xulrunner-1.9.0.5/libxul.so
#17 0x00007f1ba13510c9 in ?? () from /usr/lib/xulrunner-1.9.0.5/libxul.so
#18 0x00007f1ba11f10a9 in ?? () from /usr/lib/xulrunner-1.9.0.5/libxul.so
#19 0x00007f1ba0c78e82 in XRE_main () from /usr/lib/xulrunner-1.9.0.5/libxul.so
#20 0x00000000004016b4 in ?? ()
#21 0x00007f1ba24c7466 in __libc_start_main () from /lib/libc.so.6
#22 0x00000000004011b9 in ?? ()
#23 0x00007fffab6032d8 in ?? ()
#24 0x000000000000001c in ?? ()
#25 0x0000000000000001 in ?? ()
#26 0x00007fffab603fdc in ?? ()
#27 0x0000000000000000 in ?? ()
(gdb) c
Continuing.

Program received signal SIGSEGV, Segmentation fault.
0x00007f1ba31d7fab in raise () from /lib/libpthread.so.0
(gdb) c
Continuing.

Program terminated with signal SIGSEGV, Segmentation fault.
The program no longer exists.
```


Tried disabling other plug-ins.

FF version is

```
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.5) Gecko/2008121623 Ubuntu/8.10 (intrepid) Firefox/3.0.5
```

---

### Post by marcelkoopman on 2009-02-06
Where did you get the flash plugin from? Did you install it manually or via the repositories?

---

### Post by mikelikespie on 2009-02-06
Installed it manually from
```
libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz
```

It was failing with 
```
libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz
```
as well though.

Tried running firefox 3.2a nightly just to see what happened, and the plugin actually behaves properly with the nightly

---

### Post by mikelikespie on 2009-02-06
Actually I lied. It breaks on the nightly.

The page I'm using to test the crashing is [http://news.bbc.co.uk/2/hi/americas/7875520.stm](http://news.bbc.co.uk/2/hi/americas/7875520.stm)


-Mike

---

### Post by Yashiro on 2009-02-06
libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz
Mozilla/5.0 (X11; U; Linux x86_64; en-gb; rv:1.9.0.5) Gecko/2008121622 Firefox/3.0.5

Does not crash for me at that site. 
Hardy x86_64, A8N SLi, Ati 8.10 Binary video driver.

---

