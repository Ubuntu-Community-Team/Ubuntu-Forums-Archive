---
title: "Freezes + Flashing Caps Lock"
date: 2008-12-02
forum: x86 64-bit Users
---

### Post by koolcracker on 2008-12-02
Okay, so I've looked around a bit, but had some trouble. I've been using Ubunutu for probably 4 months on this computer and then suddenly yesterday Ubuntu started these random freezes where nothing would unlock it, the only thing I could do was a hard computer restart. The only thing that happens is my laptop caps lock LED flashes at a constant rate.

In case it was something I changed by accident, I did a fresh install of Ubuntu, and its still doing it! I haven't tested my windows yet, but do you think this could be a new hardware problem? Or does anyone know of a solution to this problem or a way to better diagnose it? I am struggling here haha, and any and all help would be greatly appreciated.

---

### Post by iponeverything on 2008-12-02
> **koolcracker said:**
> Okay, so I've looked around a bit, but had some trouble. I've been using Ubunutu for probably 4 months on this computer and then suddenly yesterday Ubuntu started these random freezes where nothing would unlock it, the only thing I could do was a hard computer restart. The only thing that happens is my laptop caps lock LED flashes at a constant rate.

In case it was something I changed by accident, I did a fresh install of Ubuntu, and its still doing it! I haven't tested my windows yet, but do you think this could be a new hardware problem? Or does anyone know of a solution to this problem or a way to better diagnose it? I am struggling here haha, and any and all help would be greatly appreciated.

The flashing caps lock is a kernel panic. When you did the fresh install, did you do the updates right away. The reason that I am asking is that problem may have been introduced in the latest update.

---

### Post by kep1616 on 2008-12-02
My laptop (Toshiba Satellite u405) is also suffering from identical symptoms. I have been trying to debug it, but I am still new to Linux. The best I can figure is that there seems to be a correlation between the lockups and Openoffice, though it only started today so I cannot be sure.

Koolcracker, what hardware are you running Ubuntu on, and what programs are you running when it freezes?

Hopefully we can get someone to help us out here.

Edit:

I updated the kernel a few days ago. The problem started today. Also, booting the other kernels did not help the problem.

---

### Post by koolcracker on 2008-12-02
I did some extra hunting around after I posted and I think I found the solution to my problem anyways, I'll share it, see if you have the same.

I run an Intel 4965 wireless card, and apparently in the new kernal update 2.6.27 there is a bug. I found this in the release notes for Intrepid:

> 
System lock-ups with Intel 4965 wireless

The version of the iwlagn wireless driver for Intel 4965 wireless chipsets included in Linux kernel version 2.6.27 causes kernel panics when used with 802.11n or 802.11g networks. Users affected by this issue can install the linux-backports-modules-intrepid package, to install a newer version of this driver that corrects the bug. (Because the known fix requires a new version of the driver, it is not expected to be possible to include this fix in the main kernel package.) 

So for now I have just disabled my wireless Internet, and after I completely update my system with all of the new packages I lost in my reinstall, I am going to install the backports. I guess that I had never picked up an n or g signal since installing intrepid a month ago, and I'm assuming that just yesterday someone installed one within range of my computer.

So this is what I found for my solution, I hope it can help you too.

---

