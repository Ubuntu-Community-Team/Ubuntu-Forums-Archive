---
title: "Ubuntu 5.10 /64-bit Resource hungry ?"
date: 2005-10-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by jvictor on 2005-10-14
Just installed 64 bit 5.10 on a machine with 1 G ram , bit resource hungry ?


top - 00:21:53 up  3:58,  2 users,  load average: 0.33, 0.41, 0.47
Tasks:  71 total,   1 running,  70 sleeping,   0 stopped,   0 zombie
Cpu(s): 12.3% us,  1.0% sy,  0.0% ni, 86.4% id,  0.0% wa,  0.3% hi,  0.0% si
Mem:    959412k total,   906040k used,    53372k free,    37828k buffers
Swap:   714852k total,        0k used,   714852k free,   526004k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 7047 root      15   0  133m  51m 7692 S  7.3  5.5  14:36.34 Xorg
 9996 neo      16   0  106m  14m 9560 S  4.0  1.6   0:01.64 gnome-terminal
 7465 neo      15   0  267m  67m  23m S  0.7  7.2   5:43.93 firefox-bin
10009 neo      16   0 10508 1240  940 R  0.7  0.1   0:00.49 top
 7404 neo     15   0  157m  29m  14m S  0.3  3.1   0:33.52 nautilus
    1 root      16   0  2628  560  476 S  0.0  0.1   0:00.58 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      10  -5     0    0    0 S  0.0  0.0   0:00.09 events/0
    4 root      17  -5     0    0    0 S  0.0  0.0   0:00.01 khelper
    5 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    7 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
   93 root      10  -5     0    0    0 S  0.0  0.0   0:00.03 kblockd/0
   96 root      15   0     0    0    0 S  0.0  0.0   0:00.00 khubd
  127 root      15   0     0    0    0 S  0.0  0.0   0:00.01 pdflush
  128 root      15   0     0    0    0 S  0.0  0.0   0:00.20 pdflush

---

### Post by tbfr on 2005-10-14
As far as I understand this there is nothing to worry about. Linux is just trying to use all your memory. 

There is nice article about Linux memory managment here
[http://forums.gentoo.org/viewtopic.php?t=175419](http://forums.gentoo.org/viewtopic.php?t=175419)

and one on measuring memory usage here:
[http://www.kdedevelopers.org/node/1445](http://www.kdedevelopers.org/node/1445)

Cheers,

Tobi

---

### Post by d1337 on 2005-10-14
As I was informed a few weeks back, memory from top will be freed as needed.  Run a free and compare the -/+ buffers/cache.  This gives you a much better picture than top does.

d1337

---

### Post by zekolas on 2005-10-15
Your memory is very fast and should be always near 100% usuage. If you open up a file or a program, linux will keep it cached in memory incase you decide to open up the file/program again it will open very fast. Since it is in cache it can be overwriten or used if other programs need more memory.

This increases performance, because hard drive access is very slow, so every time you need to read from your disk it creats a bottle neck in performace, so linux tries to keep every thing it can in fast memory.

---

