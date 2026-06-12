---
title: "linux-ubuntu-modules: Fatal: Kernel /vmlinuz is too big"
date: 2008-02-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by mikecrowe on 2008-02-19
Hi folks

I'm trying to get Xen working in gusty.  When I install **linux-ubuntu-modules-2.6.22-14-xen**, I get the following.  Am I doing something stupid?  

```
Setting up linux-ubuntu-modules-2.6.22-14-xen (2.6.22-14.37) ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-xen
update-initramfs: lilo run failed for /boot/initrd.img-2.6.22-14-xen:

Warning: LBA32 addressing assumed
Warning: '/proc/partitions' does not match '/dev' directory structure.
    Name change: '/dev/dm-0' -> '/dev/VolGroup00/LogVol00'
Warning: Name change: '/dev/dm-1' -> '/dev/VolGroup00/LogVol02'
Warning: Name change: '/dev/dm-2' -> '/dev/VolGroup00/LogVol01'
Fatal: Kernel /vmlinuz is too big
dpkg: error processing linux-ubuntu-modules-2.6.22-14-xen (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-xen:
 linux-image-xen depends on linux-ubuntu-modules-2.6.22-14-xen; however:
  Package linux-ubuntu-modules-2.6.22-14-xen is not configured yet.
dpkg: error processing linux-image-xen (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-xen:
 linux-xen depends on linux-image-xen (= 2.6.22.14.21); however:
  Package linux-image-xen is not configured yet.
dpkg: error processing linux-xen (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-xen-desktop-amd64:
 ubuntu-xen-desktop-amd64 depends on linux-xen; however:
  Package linux-xen is not configured yet.
dpkg: error processing ubuntu-xen-desktop-amd64 (--configure):
 dependency problems - leaving unconfigured

```

TIA
Mike

---

### Post by CRCarl on 2008-02-20
Mike - Looks like you may have hit a bug. Is your /boot in a logical volume?

There are some suggestions, fixes in the bug thread. 

[https://bugs.launchpad.net/ubuntu/+source/lilo-installer/+bug/23835]("https://bugs.launchpad.net/ubuntu/+source/lilo-installer/+bug/23835")

Good luck!

Craig

---

### Post by mikecrowe on 2008-02-20
CRCarl,

Yes, I'm on a logical volume.  Thanks, I'll review that link.

---

