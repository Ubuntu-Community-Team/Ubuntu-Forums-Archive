---
title: "Help to find reason for system hangs"
date: 2008-09-22
forum: x86 64-bit Users
---

### Post by erland on 2008-09-22
I get total system hangs on one of my ubuntu machines one or two times per month. I've got these hangs earlier when I was running 7.10 and I now also get them when running 8.04.

The installation is a bare minimum installation of a headless server running the AMD64 bit kernel on a Intel Core 2 Duo E6750 processor with 8GB ram. The machine runs a number of virtual machines in virtualbox. Earlier when the machine used Ubuntu 7.10 I used VM-Ware for the virtual machines.

Is there some way I can do something to find the cause of this ?

I can't find anything in the logs after the machine has hung, but I tried to write down some of the stuff that was shown on the screen in case this gives someone any idea of what's going on. There was a lot more information on the screen, but I tried to write down what felt relevant.

================
shrink_active_list+0xfb/0590
shrink_zone+0x100/0x120
kswapd+0x508/0x560
autoremove_wake_function+0x0/0x30
kswapd+0x0/0x5060
kthread+0x4b/0x80
child_rip+0xa/0x12
kthread+0x0/0x80
child_rip+0x0/0x12

Code: 0f 0b eb fe 48 8b 03 48 89 df 49 89 c7 e8 15 92 ff ff 48 89
RIP [<ffffffff8028f789>] isolate_lru_pages+0x109/0x210
	RSP <ffff8102251d1c30>
--- [end trace f73089facbce2c64 ]
================

uname -a gives:
Linux e6750 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux

Does any of this give anyone an idea of what could have caused this ?

Let me know if I can do something to provide some more information that might help someone to find the problem.

I'm not sure if this is a Ubuntu 64-bit problem, but I've only seen this on the machine that runs the 64-bit version. I have another machine that runs the 32-bit version of Ubuntu and that works perfectly without hangs. Of course the 32-bit machine also has totally different hardware.

---

### Post by soxs on 2008-09-22
Did you do a ramtest? If not do so and let it run for 24h (or more).

If this won't show any errors.. then we'll investigate further..

---

### Post by erland on 2008-09-22
Is there some way to do a ramtest while the machine is running, or do I need to do it directly from the boot menu ?

The reason I'm asking is that this is a 24/7 web server, so if I can't do it while the machine is running I need to plan it a bit to avoid unnecessary disturbances.

Is there something I can do to make sure it stores the crash log to disk ? Or do I need to write it down manually by reading the screen when it has crashed ?

---

### Post by soxs on 2008-09-23
If you can guess, or see a certain pattern right before it crashes, you could store the output from "ps ax", but if it happens that sudden without any hint in the pending logs (or in the logs at all) you hardly have a chance of getting anything useable.

Btw. I don't know wether it is posssible to do a ramtest while running, but I doubt that...

---

### Post by Creap on 2009-08-09
Hi erland. Did you solve this problem? I have the same thing, on a 64bit machine running Ubuntu Server 9.04.

---

### Post by erland on 2009-08-09
> **Creap said:**
> Hi erland. Did you solve this problem? I have the same thing, on a 64bit machine running Ubuntu Server 9.04.

I'm not sure yet, I suspect it's a memory issue. I decided to take down the server last week and run memtest on it, the result is that it actually showed some errors after a few minutes. So there are definitely memory problems with the machine, I suspect these might have caused my problems. 

After switching from DDR800 to DDR667 in BIOS I was able to run memtest for several hours without any problems. So now it's just a matter of waiting and see if switching to DDR667 also solves the hang problems.

I know there probably is some problem with my memory but since it seems to run reliable at DDR667 speed I decided to reconfigure the speed in BIOS instead of purchasing new memory chips.

---

