---
title: "pvcreate fails to create Physical Volume"
date: 2007-06-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Stilby on 2007-06-25
I've been working with LVM2 for some time under FC3, 4, Ubuntu 6.10. I recently installed Ubuntu 7.04 64bit Server on the same machine that I've been previously using LVM with [fresh install], however other than during install it is not possible to create Physical Volumes for LVM.

Example:
cfdisk /dev/sdc [create 1 partition on type 8e, Linux LVM and write changes]
pvcreate /dev/sdc1
Physical volume "/dev/sdc1" successfully created [that's what it says, but...]
pvdisplay
[..and I only see sdb1, which I created at install.]

I even dismantled a previous Volume Group:
lvremove vg0
vgremove vg0
cfdisk /dev/sdc [no changes made, just checking]
...
sdc1 Primary Linux LVM

pvdisplay
[..and I only see sdb1, which I created at install.]

I've run apt-get update
followed by apt-get upgrade

...but there was no LVM update installed.

Either pvdisplay doesn't work [but does display pv's created at install] or pvcreate doesn't work.

Am I missing something?

---

### Post by Stilby on 2007-06-25
It turns out that pvcreate does work. It's pvdisplay that's flaky. I ran vgextend vg0 /dev/sdc1 and then ran vgdisplay and would you believe it there was an extra pv there. I ran pvdisplay and now it shows up. So it doesn't show up when it is created but it does show up when it is added to a volume group.

---

