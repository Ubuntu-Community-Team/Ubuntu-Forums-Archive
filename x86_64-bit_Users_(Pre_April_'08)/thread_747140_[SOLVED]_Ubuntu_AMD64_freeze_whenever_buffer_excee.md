---
title: "[SOLVED] Ubuntu AMD64 freeze whenever buffer exceed 4GB"
date: 2008-04-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by wangrui on 2008-04-06
Hi,

I just spent a whole night trying to copy a 15GB file to my machine.

My machine did a lot of freeze when I run it 7x24. But after I move applications to a lower end computer. Everything seems works for a while. But today my machine freeze  a lot of times because I want to copy a file.

First, I have to say, there is no problem of the memory. I bought four KingMax DDR2-800 2GB memory. I have done a lot of test on them. And it works fine if I run programs which need 7GB memory.

But when the disk buffer use more than 4GB or address more than 4GB. The system will freeze:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/212817](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/212817)

I want to copy a file from another machine. Whenever the buffer goes beyond 4GB, the system will freeze. It also freeze when I occupied the upper 4GB by a program. And I found there is no way to clear the buffer. When I copy file, the buffer will increase. If I stop the copying, the buffer will not be cleared at all. The buffer will increase whenever the copy start. I use gFtp to do the copying. Each time I can mostly copy 4GB data. Then the system will freeze.

I spent a whole night trying to solve the problem. At last, I found a way to clear the buffer without rebooting the machine. Whenever I copied 3.5GB data. I stopped the transfering, and umount the disk. Then the buffer will be cleared. 

But this is so annoying. Whenever the disk buffer exceed 4GB, or if the buffer allocate when 4GB memory is used, the system will freeze. I hope there is a tool or something can set the buffer to a fix size or clear the buffer periodically. Otherwise I have to reboot the machine or unmount disks very frequently to avoid lock up.

---

### Post by wangrui on 2008-04-06
And another thing is:

During a lot of freezes, there is one time the onboard 1GB network card refuse to work after reboot. And there is another time the ASUS BIOS was cleared after reboot.

---

### Post by wangrui on 2008-04-06
Please forget about this thread. I just did a test on Hardy AMD64 live cd. The disk buffer goes to 7470MB without any problem. This bug is fixed in Hardy. I will move my system to Hardy instead. 

Life is good.:)

Thanks

---

