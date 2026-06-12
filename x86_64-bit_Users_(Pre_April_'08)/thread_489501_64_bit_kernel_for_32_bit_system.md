---
title: "64 bit kernel for 32 bit system?"
date: 2007-07-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by HankB on 2007-07-01
Hi all,
I have a couple of opportunities to use a 64 bit kernel on a 32 bit system.

On one, I'll be upgrading from a 32 bit MOBO to a 64 bit (AMD) MOBO. I'm running 6.06 LTS and use it mostly as a server. Eventually I may upgrade the install to 64 bit, but in the mean time is there any benefit to installing a 64 bit kernel while everything else is still 32 bit?

On another system, I degraded some time ago from 64 bit to 32 bit. At that time the best way to run 32 bit apps on 64 bit system was a chroot and that's not transparent to the user. The primary user was my wife (who is a user, not a geek like me ;) ) and I just got tired of having to explain to her how to make stuff work or having her get less functionality out of the system. (Thanks to folks like Kilz stuff like that is a lot less necessary these days.) Nevertheless, the system is still 32 bit and I just installed an X2 dual core processor. :D I was a bit disappointed when only one processor was reported in /proc/cpuinfo. I also noticed that 'uname -a' does not identify an SMP kernel. I thought that all Ubuntu kernels were SMP. The first thing I decided to do was upgrade from edgy to feisty.  Maybe that will solve the SMP issue. But maybe I should also upgrade to a 64 bit kernel too.

What would be the easiest way to install a 64 bit kernel on a 32 bit system? Is there a way that will automatically get me upgrades?

thanks,
hank

---

### Post by Kilz on 2007-07-01
> **HankB said:**
> Hi all,
I have a couple of opportunities to use a 64 bit kernel on a 32 bit system.

On one, I'll be upgrading from a 32 bit MOBO to a 64 bit (AMD) MOBO. I'm running 6.06 LTS and use it mostly as a server. Eventually I may upgrade the install to 64 bit, but in the mean time is there any benefit to installing a 64 bit kernel while everything else is still 32 bit?

On another system, I degraded some time ago from 64 bit to 32 bit. At that time the best way to run 32 bit apps on 64 bit system was a chroot and that's not transparent to the user. The primary user was my wife (who is a user, not a geek like me ;) ) and I just got tired of having to explain to her how to make stuff work or having her get less functionality out of the system. (Thanks to folks like Kilz stuff like that is a lot less necessary these days.) Nevertheless, the system is still 32 bit and I just installed an X2 dual core processor. :D I was a bit disappointed when only one processor was reported in /proc/cpuinfo. I also noticed that 'uname -a' does not identify an SMP kernel. I thought that all Ubuntu kernels were SMP. The first thing I decided to do was upgrade from edgy to feisty.  Maybe that will solve the SMP issue. But maybe I should also upgrade to a 64 bit kernel too.

What would be the easiest way to install a 64 bit kernel on a 32 bit system? Is there a way that will automatically get me upgrades?

thanks,
hank

You cant do it. It wont work. My best suggestion is to install the 64bit version to a separate partition , keeping the 32bit one intact. that way you can do the setup at your own pace, get everything working. Without the need to have a working setup for your wife , who can boot into the 32bit install.

---

