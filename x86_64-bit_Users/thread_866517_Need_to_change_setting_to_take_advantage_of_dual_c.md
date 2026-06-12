---
title: "Need to change setting to take advantage of dual core?"
date: 2008-07-21
forum: x86 64-bit Users
---

### Post by risknothin on 2008-07-21
[http://ourtweaks.com/ubuntu-tweaks/enable-dual-core-processors/](http://ourtweaks.com/ubuntu-tweaks/enable-dual-core-processors/)

this site says you have to change a setting to get dual core processors to work, is this correct?

---

### Post by tamoneya on 2008-07-21
that is a tweak to increase boot speed.  It utilizes multiple cores.  The processor however is correctly used however by the kernel.  By default the ubuntu kernel supports up to 8 cores I believe.  As far as normal usage you wont notice a difference.  This just affects the startup.

Incase you want to know I do have this optimization on both my dual core and quad core comps and really it didnt seem to help all that much.

---

### Post by risknothin on 2008-07-21
what about their other tweaks on the site? swapping? and the ipv6? do those work?

---

### Post by xen-uno on 2008-07-21
Init.d's appear to be scripts for starting & stopping services, which would normally occur only at startup & shutdown. [x]Ubuntu's are SMP aware by default (check CPU History in System>Administration>System Monitor>Resources). I doubt there would be any gain with this mod.

---

### Post by tamoneya on 2008-07-21
assuming that you have a fairly recent computer i think the most useful one would be changing the swappiness.  This is primarily because harddrives are the bottle neck when it comes to linux on current computers.  The concurrency doesnt help much since one processor is more than enough for ubuntu to boot from and two or four is excessive so it doesnt speed it up much.  As for the IPv6 it could help but I havent played with it much.  As a general rule of thumb networks are slower than harddrives which are slower than RAM and Processors.  Therefore an optimization on something network based could lead to nice boot speeds.  I have disabled DHCP on my home network and have assigned IP statically.  This has helped my boot times since it doesnt have two wait for IPs to be dynamically assigned.  

If you want to get into the details of your boot sequence you should start by installing bootchart:[http://ubuntuforums.org/showthread.php?t=241604](http://ubuntuforums.org/showthread.php?t=241604).

NOTE: all of the above optimizations deal with boot speed not the speed of the computer while its running.

---

### Post by cariboo on 2008-07-21
Install htop it is available in the repositories and then do something cpu intensive. You will see both of your cores in action.

Jim

---

### Post by xen-uno on 2008-07-21
The Speed Up Menu's tweak works nice ... was wondering how to do that.

---

### Post by risknothin on 2008-07-21
doesn't system monitor show you what your core's are doing?


also are there any tweaks that can speed up ubuntu? im all about getting the most out of my system.

1,73 duo processor, 2gb ram

---

### Post by erkanea on 2008-07-22
> **risknothin said:**
> doesn't system monitor show you what your core's are doing?

Yes it does show how much % each core is being used.

---

