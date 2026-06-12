---
title: "kernel-k8 dosent work with nvidia"
date: 2004-11-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by ubuser on 2004-11-09
Hi,

I have an athlon64/3000+ and asus k8v-x, nvidia FX 5700LE and ubuntu uptodate.
I installed nvidia drivers (and nvidia-config). I works well with the generic kernel.
I installed the kernel-k8 which is the optimized version for my proc.
After reboot it stops when launching gnome. It says it cant start X (blah blah) and then say it disable gdm.
In console mode I tried nvidia-config but it didnt change nothing.
I tried modprobe nvidia and say module not found.
In XFree.log it says module v4l not found. NVIDIA Failed to initialize the NVIDIA kernel module (XIO fatal IO error 104.

Thanks for your attention.

Sincerely,

Ubuser.

---

### Post by dmatrix on 2004-11-09
For the Nvidia driver you need to install a matching linux-restricted-modules for the kernel you are running.

ie. Install this for linux-amd64-k8: linux-restricted-modules-amd64-k8

---

### Post by HiddenWolf on 2004-11-13
dmatrix, isn't that a dependeny then?

---

### Post by cybrjackle on 2004-11-23
[QUOTE=HiddenWolf]dmatrix, isn't that a dependeny then?[/QUOTE]

For me,  after I install a new kernel, go and change nvidia back to nv, reboot then:

sudo apt-get install linux-headers-`uname -r`
sudo apt-get install linux-restricted-modules-`uname -r`
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable

sudo /etc/init.d/gdm stop

Log back in

sudo /etc/init.d/gdm start

---

### Post by jdong on 2004-11-24
[QUOTE=HiddenWolf]dmatrix, isn't that a dependeny then?[/QUOTE]

Depends on what was installed... linux-(arch) is a metapackage for linux-(arch)-image linux-(arch)-restricted-modules

If one installed linux-(arch)-image, then no, modules wouldn't be installed.

---

