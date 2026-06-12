---
title: "VirtualBox 2.0 performance on 64-bit host"
date: 2008-10-12
forum: x86 64-bit Users
---

### Post by ilchymis on 2008-10-12
I just upgraded my computer from 32-bit to 64-bit Hardy, and my 32-bit Windows XP VirtualBox 2.0 VM seems to have taken a large performance hit in the process.  More precisely, VirtualBox eats up about 33% of the clock cycles on one of my computer's CPU cores, even when the guest OS is doing very little; this happens both with and without VT-x support enabled.

In contrast, when hosted in 32-bit Ubuntu 8.04, VirtualBox 2.0 exhibited negligible CPU overhead running a 32-bit guest OS with VT-x.

Is this a known behavior, or is this something peculiar to my installation?  A free trial of VMware Workstation 6.5 is lightning fast on 64-bit Hardy by comparison...  I'm not particularly enthusiastic about paying for a VMware license, but that's what I'll have to do if I can't get VirtualBox performing more acceptably.  So any advice is welcome :)

For what it's worth, the system in question is running on an Intel Core 2 Duo T7500 @ 2.20 GHz, and has 4 GB of memory.

---

### Post by abcuser on 2008-10-12
Hi,
did you install the latest version of VirtualBox 2.0.2? [http://virtualbox.org/wiki/Linux_Downloads](http://virtualbox.org/wiki/Linux_Downloads)
As I have read on VirtualBox forum 2.0.0 has a lot of bugs.

How did you measure CPU occupation? I use top command on Ubuntu 8.04 32-bit host and see there is no more then 5% of CPU taken by VirtualBox when guest is started and doing not thing.
Regards,
Abcuser

---

### Post by ilchymis on 2008-10-12
Yep, I should have been more specific; this is with non-Free VirtualBox 2.0.2.  And I was using top to measure CPU utilization.

---

### Post by Thormick on 2008-10-27
I ran into a problem with very similar symptoms, except that VirtualBox ate 100% of my E6600 2.2 Ghz CPU and the virtual machine ran like a dog. This was due to VirualBox struggling with a multicore Windows kernel, when I switched to using a single core kernel as mentioned somewhere [_in this piece here_]("http://forums.virtualbox.org/viewtopic.php?t=8669&sid=81764b5ffd9f7a172ab387af67a5831d") everything was snappy and VirtualBox ate 4% cpu when idling.

---

