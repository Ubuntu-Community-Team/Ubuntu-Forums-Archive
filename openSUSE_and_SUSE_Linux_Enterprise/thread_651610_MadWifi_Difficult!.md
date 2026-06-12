---
title: "MadWifi Difficult!"
date: 2007-12-27
forum: openSUSE and SUSE Linux Enterprise
---

### Post by pteri498 on 2007-12-27
I decided to make a switch to OpenSuse because I'm having no end of problems with Gutsy and my pchdtv 5500, and OpenSuse appears to have a good guide out.

That'd be great, if only I could get my wifi driver working. I'm working form xp, as this is my only internet access at the moment, so I'll try to remember what's going on.

So I manage to successfully install MadWifi, do a modprobe on it and the driver appears to be working in Yast's network devices.

Except, in configuration, the card's zone is something along the lines of "no access". I switch it to "external", but as soon as I hit next and go back to see if it took, it goes back to no access.

Any ideas on how to solve this? I can't get online like this.

---

### Post by the_darkside_986 on 2008-01-01
Wow... I can't even get to the part where I successfully install madwifi RPM packages. I downloaded both madwifi and madwifi-kmp-default-... something but the second package won't install due to dependencies on the kernel package. I have no way of accessing internet from openSUSE so is there a list of individual packages I should download to satisfy the dependencies? and how do I add a local folder to my software repository list?

I might try to see if ndiswrapper will work. But I'm pretty sure madwifi is the correct driver, as I used to use it openSUSE 10.1 for the same card. But when I was using Ubuntu, it was easy and I forgot how to do all this stuff...

(I'm just using openSUSE 10.3 for fun until Hardy Heron is released.)

---

### Post by the_darkside_986 on 2008-01-01
I got ndiswrapper installed but it isn't loading the module automatically. In Ubuntu, I would add "ndiswrapper" to /etc/modules, but openSUSE 10.3 has no such file. How do I add modules such as ndiswrapper to be loaded during startup? I looked at /etc/modprobe.conf but I'm not sure what that does and I'm afraid to mess with files that do not look obvious.

Anyway, my plan is to install ndiswrapper for my card for internet access until I can get madwifi dependencies resolved. Anyway, madwifi drivers can unlock certain features of my wireless card that the Windows drivers will not allow. 

I am so sick of these guides and tutorials saying "add this source to repositories" in order to get a network card working. I don't have internet access without a functional wireless card DUH so that is stupid advice. How about just giving me a big long list of each RPM to download to satisfy dependencies. :(

---

### Post by RedDwarf on 2008-01-02
> **the_darkside_986 said:**
> is there a list of individual packages I should download to satisfy the dependencies?
No because you just need bash and kernel-default... and for sure you have both.

But the kernel from the DVD doesn't provide "kernel(vmlinux) = 12f6088d1c360912", so just must update it (any of the three available updates is enough, but you should download the last one...).

---

### Post by the_darkside_986 on 2008-01-04
Yeah I finally figured out what to do to get ndiswrapper to work, I was supposed to right-click on KNetworkManager after configuring the card to use ndiswrapper. But I got my kernel updated so I think I can successfully install madwifi at some point in time.

---

