---
title: "vmware broken in 64 bit gutsy"
date: 2007-10-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by go_beep_yourself on 2007-10-19
VMware Server quit working after upgrading to 7.10. I have vmware installed through the Canonical repo. A package for the vmware server modules for kernel 2.6.22-14 does not exist. How can VMware Server work in 64 bit Gusty Gibbon?

---

### Post by jeromio on 2007-10-21
Same boat here. My previous installation of vmware player (installed while the system was 7.0.4) complains about not being able to find the monitor driver. Synaptics shows vmware as not being installed. When I try to install it, it complains about the entry being bogus.

---

### Post by go_beep_yourself on 2007-10-21
Download from vmware's website instead of using ubuntu packages.

---

### Post by ctw on 2007-10-21
I've downloaded the las vmware version VMware-workstation-6.0.2-59824.x86_64 and work it perfect with ubuntu 7.10.

---

### Post by tmcmulli on 2007-10-21
I downloaded vmplayer from vmware's website, walked through the install (recompile) now getting the attached error.

Trying to play a 32-bit VM, but that shouldn't matter, right??

---

### Post by parsim on 2007-10-23
> **ctw said:**
> I've downloaded the las vmware version VMware-workstation-6.0.2-59824.x86_64 and work it perfect with ubuntu 7.10.

Just a "me too." Was a bit annoying to have to reinstall, but no problems.

---

### Post by go_beep_yourself on 2007-10-24
> **tmcmulli said:**
> I downloaded vmplayer from vmware's website, walked through the install (recompile) now getting the attached error.

Trying to play a 32-bit VM, but that shouldn't matter, right??

I had a similar problem. Try starting the vmware service.

```
sudo /etc/init.d/vmware start
```

---

### Post by tmcmulli on 2007-10-26
> **go_beep_yourself said:**
> I had a similar problem. Try starting the vmware service.

```
sudo /etc/init.d/vmware start
```

After reinstalling Gutsy, this is what ultimately fixed it:

sudo apt-get install ia32-libs

Rock on!

---

