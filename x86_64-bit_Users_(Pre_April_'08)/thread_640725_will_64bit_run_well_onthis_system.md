---
title: "will 64bit run well onthis system?"
date: 2007-12-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by tuproxy on 2007-12-14
I'm considering running the 64 bit version. will it run on my new pc?

It is a new Intel E6750, Dual Core,(4) 1gb pc6400 ram, ABit IP35 Pro 775. It is the newest stuff I could buy, except I could have bought the quad core. 

Anyway, I know the CPU supports 64 bit, so would I benefit greatly using 4 GB RAM?

I would like to run 6.06 server and then run VMware server on top of this to run my OS's.

Where can I find an Intel 64 bit OS.  All I see is the AMD version.

---

### Post by dandandan on 2007-12-14
The "amd 64bit" Version is the one you will want to run, even on Intel Hardware.
For example this link:
[http://mirrors.kernel.org/ubuntu-releases/dapper/ubuntu-6.06.1-desktop-amd64.iso](http://mirrors.kernel.org/ubuntu-releases/dapper/ubuntu-6.06.1-desktop-amd64.iso).

The more Applications you are running simultaneously, the more you will benefit from 4gigs of Ram.
If you are only running Fluxbox and 3 Terminals, you wont notice any difference between 32bit or 64bit or 512mb Ram or 4gigs ram.
If you are running multiple VMs you will notice the difference. If your are Using dm-crypt and the new aes cipher for 64bit you will notice an almost 2x speed increase compared to the 32bit Version.

So basically its a question of what you want to do with it and to what you compare it to.

---

### Post by tuproxy on 2007-12-14
Thanks for the insight. I am going to install a 64 bit, but am now torn between which version.  Are there great advantages to running 7.10?  I like the idea of LTS of 6.06. 

I would like to have a GUI installed. Is this possible with server? I know you can probably use apt-get install kde or gnome or something.  

Is there a diff between the 32bit and 64 bit GUI?

Finally, since I'm just getting back into Linux, I'm a moderate-newbie.  I'm looking for a good guide on what to learn and the order. Is there a good guide for this?  I'd love to find a guide to learn Linux and walk me through it.  

Thanks

---

### Post by Kilz on 2007-12-14
> **tuproxy said:**
> Thanks for the insight. I am going to install a 64 bit, but am now torn between which version.  Are there great advantages to running 7.10?  I like the idea of LTS of 6.06. 

I would like to have a GUI installed. Is this possible with server? I know you can probably use apt-get install kde or gnome or something.  

Is there a diff between the 32bit and 64 bit GUI?

Finally, since I'm just getting back into Linux, I'm a moderate-newbie.  I'm looking for a good guide on what to learn and the order. Is there a good guide for this?  I'd love to find a guide to learn Linux and walk me through it.  

Thanks

6.06 is 4 versions old. The next version 8.04 will be a lts. If you install 6.06 the upgrade path to 8.04 will be to upgrade to each version , one at a time. The odds on problems developing over 5 upgrades will be great.
I would suggest installing the 7.10 server and then upgrade to 8.04 when it is released.
There is no difference in the 32bit vs 64bit server gui. There is none. Servers do not have a gui installed by default in either 32 or 64bit.

---

### Post by John.Michael.Kane on 2007-12-14
The ABit IP35 Pro "might not be fully supported by the 6.06.1 kernel". Thus you will have to do a bit of research on that board if you decide to use that version of Ubuntu. 

The kernel included with Ubuntu 7.10 "should support the p35 chip set".

This may also be of some help.
[Ubuntu Server Guide]("http://doc.ubuntu.com/ubuntu/serverguide/C/index.html")

[Ubuntu 7.10 (Gutsy Gibbon) Server Setup]("http://www.ubuntugeek.com/ubuntu-710-gutsy-gibbon-lamp-server-setup.html")

[VMware Server]("https://help.ubuntu.com/community/VMware/Server")

[How to Install Vmware Server in Ubuntu 7.10]("http://www.ubuntugeek.com/how-to-install-vmware-server-in-ubuntu-710-gutsy-gibbon.html")

[The Perfect Server - Ubuntu Gutsy Gibbon (Ubuntu 7.10)]("http://www.howtoforge.com/perfect_server_ubuntu7.10")

[Ubuntu LAMP Server - Setup Guide with Desktop GUI]("http://www.zaphu.com/2007/08/07/ubuntu-lamp-server-setup-guide-with-desktop-gui/")

---

### Post by tuproxy on 2007-12-14
Thank you for the posts.  This is exactly what I was looking for!  I think I'll go with the 7.10 64 bit.

---

