---
title: "coldfusion 8 on 7.10 a64 server ?"
date: 2007-10-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by jkzfixme on 2007-10-19
I tried the fix that worked w/ ubuntu 7.04 even though it was a different error. This however did not change anything , I am still not able to install . Any input would be greatly appreciated.

~$ cat Coldfusion-8-lin.bin | sed "s/export LD_ASSUME_KERNEL/#xport LD_ASSUME_KERNEL/" > /tmp/coldfusion.bin
~$ sudo sh /tmp/coldfusion.bin  

Launching installer...

exec: 2481: /tmp/install.dir.8037/Linux/resource/jre/bin/java: not found

I am running
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0_03-b05, mixed mode)

2.6.22-14-server #1 SMP Sun Oct 14 22:09:15 GMT 2007 x
86_64 GNU/Linux

---

