---
title: "Mac Mini"
date: 2005-10-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by kingc8 on 2005-10-19
A week ago my Mac Mini was silent again. But now, like weeks before, I hear the sound of the hard drive running constantly, and when it spins down after a minute, it immediatly spins up again!

Its beginning to get annoying. Is there deamon running thats spinning up the drive forever?

How do I check?

Thanks,

Cameron

---

### Post by dbott67 on 2005-10-19
You can list running processes by typing 'top' at the command prompt to get a real-time listing of running processes that gets updated every few seconds:
> dbott@breezy:~$ top

top - 21:38:34 up  4:36,  3 users,  load average: 0.74, 0.54, 0.39
Tasks:  85 total,   2 running,  78 sleeping,   5 stopped,   0 zombie
Cpu(s): 21.4% us,  1.3% sy,  0.6% ni, 73.2% id,  3.3% wa,  0.1% hi,  0.0% si
Mem:    256796k total,   251348k used,     5448k free,    12828k buffers
Swap:   208772k total,    12476k used,   196296k free,    67312k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 6777 root      15   0 54068  35m 7648 S 11.1 14.1  48:55.36 Xorg
10937 dbott     15   0  2124  984  752 R  5.5  0.4   0:00.06 top
 7372 dbott     15   0 21432  11m 8636 S  1.8  4.7   0:08.91 mixer_applet2
    1 root      16   0  1564  532  460 S  0.0  0.2   0:04.00 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      10  -5     0    0    0 S  0.0  0.0   0:00.22 events/0
    4 root      11  -5     0    0    0 S  0.0  0.0   0:00.07 khelper
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.88 kacpid
   84 root      10  -5     0    0    0 S  0.0  0.0   0:00.07 kblockd/0
  110 root      15   0     0    0    0 S  0.0  0.0   0:00.09 pdflush
  111 root      15   0     0    0    0 S  0.0  0.0   0:00.14 pdflush
  113 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  112 root      15   0     0    0    0 S  0.0  0.0   0:00.25 kswapd0
  698 root      15   0     0    0    0 S  0.0  0.0   0:00.00 kseriod
 1873 root      17   0     0    0    0 S  0.0  0.0   0:00.00 khubd
 2966 root      15   0     0    0    0 S  0.0  0.0   0:01.45 kjournald


Basically, you'll have to watch & listen... when the hard disk starts spinning, take a look at 'top' and see which processes are using CPU & Memory.

A few nights ago, someone else posted a similar question and some of the thoughts were: journaling/indexing of the hard drive (the 'locate' command was working) and possibly the OS running some sort of update.

-Dave

---

