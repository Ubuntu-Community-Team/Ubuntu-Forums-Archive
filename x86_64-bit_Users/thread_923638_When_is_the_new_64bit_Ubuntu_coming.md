---
title: "When is the new 64bit Ubuntu coming ?"
date: 2008-09-18
forum: x86 64-bit Users
---

### Post by Shadowmeph on 2008-09-18
I am wondering this because as it is hardy doesn't work for me with 4gb ram and the fglrx drivers it just won't start so I am hoping that the next version will work because I am stuck using opensuse which to me seems really buggy

---

### Post by Kilz on 2008-09-18
> **Shadowmeph said:**
> I am wondering this because as it is hardy doesn't work for me with 4gb ram and the fglrx drivers it just won't start so I am hoping that the next version will work because I am stuck using opensuse which to me seems really buggy

Intrepid Ibex is set for October. [You can look here]("http://ubuntuforums.org/forumdisplay.php?f=346") for release information. There will be a sticky. [But with just a quick look I would not be in a hurry]("http://ubuntuforums.org/showthread.php?t=923018").

---

### Post by stinger30au on 2008-09-18
ubuntu 8.10 gets released at the end of october. the 30th it was from memory

---

### Post by Shadowmeph on 2008-09-18
Cool I really Like Hardy it is just it doesn't work for me with 4gb ram and the fglrx drivers which is a total drag

---

### Post by phlembob on 2008-09-18
I'm using Foxconn mobo with AMD 4800 X2 w/ 2gb RAM w/o problems.  Have you tried loading up w/ 2gb RAM, then ad 2gb RAM later?  That might work, I have read other conversations here with 4gb RAM problems.
:guitar:
Keep Jammin':lolflag:

---

### Post by jack frost on 2008-09-18
> **Shadowmeph said:**
> I am wondering this because as it is hardy doesn't work for me with 4gb ram and the fglrx drivers it just won't start so I am hoping that the next version will work because I am stuck using opensuse which to me seems really buggy
I am using 4gb of ram on ecs elite group board -nforce6m-a amd64 x2. using 4 x1gb sticks of apacer and works fine for me.

---

### Post by Kilz on 2008-09-18
> **Shadowmeph said:**
> Cool I really Like Hardy it is just it doesn't work for me with 4gb ram and the fglrx drivers which is a total drag


Depending on your motherboard and video card, your 4gb may not show. I would strongly suggest you look at the links I placed to read about the ati driver on Intrepid.

---

### Post by jespdj on 2008-09-19
> **Shadowmeph said:**
> Cool I really Like Hardy it is just it doesn't work for me with 4gb ram and the fglrx drivers which is a total drag
If you want help with this, explain exactly what "doesn't work" means, what you have tried, etc. Without more information we cannot help you with the problem, and waiting until the next version might not be the right solution.

---

### Post by Shadowmeph on 2008-10-24
> **jespdj said:**
> If you want help with this, explain exactly what "doesn't work" means, what you have tried, etc. Without more information we cannot help you with the problem, and waiting until the next version might not be the right solution.

been a while I was a little busy.
ok what happened is that Ubuntu ran perfectly with 2GB ram but I installed another exact match of 2 GB ram and when I started Ubuntu it would load until Just before the desktop then freeze with the Black screen, so I tried as cou8ple of more time and the result was always the same , finnally I rebooted and went into the xor.conf file and change the fglrx to ati and it booted with out any problems at all
so It has something to do either with the driver or my MB/Ubuntu and driver combination I was hoping that Ubuntu will work with the newest version this is my Computer build
```

Gigabyte Motherboard: P35-DS3L

Basic I/O System(BIOS): Award Modular BIOS v6.00PG

Central Processing Unit(CPU): Intel(R) Core(TM)2 Duo CPU E8400 @ 3.00GHz

Physical Memory X 4

    1024MB

    1024MB

    1024MB

    1024MB

Hard Disk X 2

    ST3320620AS ATA Device (298GB)

    ST3320620A ATA Device (298GB)

Video Card: ATI Radeon HD 3800 Series

Monitor: Generic Non-PnP Monitor

Audio Device X 4

    High Definition Audio Device

    USB Audio Device

    Realtek High Definition Audio

    ASUS Xonar DX Audio Device

Network Adapter

    Local Area Connection - Intel(R) PRO/1000 GT Desktop Adapter (Connected)

Keyboard: USB Human Interface Device

Mouse: USB Human Interface Device
```
I was thinking to just update to the newest Kernel but I always seem to run into problems on other Linux Distro's when I have done this

---

### Post by jespdj on 2008-10-25
One thing to check is if the RAM works properly: reboot, and in the GRUB menu choose the memtest86 option, which starts a memory testing program. Let it run for a few hours to test the RAM in your computer. If it finds errors, then there's something wrong with the memory modules you installed in your computer.

---

### Post by Shadowmeph on 2008-10-25
> **jespdj said:**
> One thing to check is if the RAM works properly: reboot, and in the GRUB menu choose the memtest86 option, which starts a memory testing program. Let it run for a few hours to test the RAM in your computer. If it finds errors, then there's something wrong with the memory modules you installed in your computer.

the ram runs perfectly I posted this problem before months back and IntuitiveNipple said this is the problem I am not sure if it is but if it is I hope that they fix it

> When you use the LiveCD it probably uses different video drivers than you've got installed.

What most likely causes this is the video card needing to allocate a large range of PCI IOMEM but, because you've got 4GB of RAM installed, there is not enough free IOMEM address space below the 4GB boundary for the PCI IOMEM window - video devices usually need 256MB or 512MB.

When the PC only has 2GB of RAM, there's a window of 1.25GB available for PCI IOMEM. With 4GB of RAM, 1GB is mapped above the 4GB boundary, leaving just 256MB of PCI IOMEM space between the 3GB and 4GB boundaries.

As all PCI devices in the system have to share this space, and the video device isn't the first to request an IOMEM allocation, the system doesn't have enough IOMEM space and the video device doesn't get any.

That means it will only operate in text and low-resolution graphics modes. When a high-resolution mode is attempted it can't do it, and fails the way you describe.

There isn't a solution at present. I'm currently putting the finishing touches to new Linux kernel PCI IOMEM allocation system that works as well as, if not better than, Windows. That won't appear in mainline for a few months though, and I doubt it'll get backported to existing releases.

---

### Post by Yashiro on 2008-10-25
If this is a genuine kernel problem then it kinda renders 64bit builds pointless if they can't be used for high end graphics.

Unless of course it's an Ati proprietary driver only issue?

---

