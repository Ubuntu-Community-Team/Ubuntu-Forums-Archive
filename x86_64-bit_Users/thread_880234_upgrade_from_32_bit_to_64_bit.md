---
title: "upgrade from 32 bit to 64 bit?"
date: 2008-08-04
forum: x86 64-bit Users
---

### Post by bulwynkl on 2008-08-04
Hi all,

why can't you upgrade directly from 32 bit to 64 bit ubuntu?

Surely it's just a matter of selecting the right install target in dpkg/atp-get/synaptic, etc.

---

### Post by tamoneya on 2008-08-04
its not that simple.  First you would have to replace the kernel with the 64 bit kernel.  Then you would need to replace drivers and then you would have to replace everything that you have installed through synaptic.  When you add something through synaptic you tell the repos what architecture you have.Then it sends the correct deb.  So this means you would need to replace everything.  So while it is technically possibly to do this it is by no means realistic.  It is MUCH easier to reinstall from scratch.

---

### Post by bulwynkl on 2008-08-04
> **tamoneya said:**
> its not that simple.  First you would have to replace the kernel with the 64 bit kernel.  Then you would need to replace drivers and then you would have to replace everything that you have installed through synaptic.  When you add something through synaptic you tell the repos what architecture you have.Then it sends the correct deb.  So this means you would need to replace everything.  So while it is technically possibly to do this it is by no means realistic.  It is MUCH easier to reinstall from scratch.

thanks... that is very helpful

the reason I would consider doing it this way is that I don't want to have to overwrite my existing system - it would mean reinstalling and configuring all the apps I have installed since loading the base system. As well as backing up a whole bunch of data - (yes I should probably do that anyway)

so, I guess the question is - how do I install 64 over the top of 32 and also update all the software installed on top of the base system?

if there is an easy way to do this as a new install, great, let me know.

if there is not then how do I install the 64 bit system as an upgrade (is there an install target)?

---

### Post by tamoneya on 2008-08-04
well all your configurations are in /home/<username> so to start with just backup those files and replace them in your new install.  Then if you install the apps they will detect their settings.  I dont know of a good way to transfer the apps though.  Typically I would recommend remastersys which makes you a custom iso so that you can recover your install but it would still have 32 bit so you wouldnt have made any progress.

---

