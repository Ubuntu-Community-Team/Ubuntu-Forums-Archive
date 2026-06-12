---
title: "update to Kernel 2.6.24 64bit and NVIDIA driver"
date: 2008-05-31
forum: x86 64-bit Users
---

### Post by Boexli on 2008-05-31
Hi Guys

I have updated my system to Kernel 2.6.24 and have now an issue with the NVIDIA drive. It seems that the NVIDA driver package has not yet been updated to the new kernel and is therefore not working. Has anybody successfully fixed this issue? Thanks Nick

---

### Post by chewearn on 2008-05-31
How is your nvidia driver installed?  I.e. via nvidia-glx-new, or custom compile package from nvidia website?

If nvidia-glx-new, run:
```
sudo apt-get update
```

Does it show nvidia-glx-new package then?  If yes:

```
sudo apt-get upgrade
```

or, maybe:
```
sudo apt-get dist-upgrade
```


If custom compile package, recompile it using the same steps you did the first time.

---

### Post by Boexli on 2008-05-31
thanks for the feedback- I have this package installed but the problem is that is does not work with the new kernel 2.6.24 as far as I can say. Does that mean I have to uninstall the nvidia new package and download the driver from nvidia? that does not sound like a really good plan .....Cheers Nick

---

### Post by chewearn on 2008-05-31
> **Boexli said:**
> thanks for the feedback- I have this package installed but the problem is that is does not work with the new kernel 2.6.24 as far as I can say. Does that mean I have to uninstall the nvidia new package and download the driver from nvidia? that does not sound like a really good plan .....Cheers Nick

That's strange.  I have same kernel 2.6.24.  I use nvidia-glx-new.  There was a kernel update two days ago, which has a corresponding nvidia-glx-new update.  The update proceed without error and reboot is OK.

You might be having a different problem, rather than nvidia-glx-new not working with 2.6.24.


My uname -r give: 2.6.24-17-generic

Here is my update log:

```

Commit Log for Thu May 29 21:10:30 2008


Upgraded the following packages:
apport (0.108.1) to 0.108.2
apport-gtk (0.108.1) to 0.108.2
f-spot (0.4.2-1ubuntu3) to 0.4.3.1-0ubuntu1
gdm (2.20.6-0ubuntu1) to 2.20.6-0ubuntu2
gnome-about (1:2.22.1-0ubuntu6.2) to 1:2.22.2-0ubuntu1
gnome-desktop-data (1:2.22.1-0ubuntu6.2) to 1:2.22.2-0ubuntu1
gnome-keyring (2.22.1-1) to 2.22.1-1ubuntu1
libgnome-desktop-2 (1:2.22.1-0ubuntu6.2) to 1:2.22.2-0ubuntu1
libgnome-keyring0 (2.22.1-1) to 2.22.1-1ubuntu1
libpam-gnome-keyring (2.22.1-1) to 2.22.1-1ubuntu1
linux-generic (2.6.24.16.18) to 2.6.24.17.19
linux-headers-generic (2.6.24.16.18) to 2.6.24.17.19
linux-image-generic (2.6.24.16.18) to 2.6.24.17.19
linux-libc-dev (2.6.24-16.30) to 2.6.24-17.31
linux-restricted-modules-common (2.6.24.12-16.34) to 2.6.24.12-17.36
linux-restricted-modules-generic (2.6.24.16.18) to 2.6.24.17.19
linux-source-2.6.24 (2.6.24-16.30) to 2.6.24-17.31
nvidia-glx-new (169.12+2.6.24.12-16.34) to 169.12+2.6.24.12-17.36
python-apport (0.108.1) to 0.108.2
python-problem-report (0.108.1) to 0.108.2

Installed the following packages:
libmono-cairo2.0-cil (1.2.6+dfsg-6ubuntu3)
linux-headers-2.6.24-17 (2.6.24-17.31)
linux-headers-2.6.24-17-generic (2.6.24-17.31)
linux-image-2.6.24-17-generic (2.6.24-17.31)
linux-restricted-modules-2.6.24-17-generic (2.6.24.12-17.36)
linux-ubuntu-modules-2.6.24-17-generic (2.6.24-17.25)

```

---

### Post by bford16 on 2008-05-31
How did you generate the update log?  I've been looking for that.

---

### Post by bford16 on 2008-05-31
> **bford16 said:**
> How did you generate the update log?  I've been looking for that.

Never mind.  Found it in Synaptic.

---

### Post by Youresorock on 2008-06-05
I'm having the same problem.

I'm running 2.6.24-18-server now, although I've booted to tons of available kernels and it's still hosed.

I've reinstalled via envy, nvidia.com, restricted drivers manager.  won't load the nvidia driver.

[PHP]sudo modprobe nvidia
sh: /sbin/lrm-video: not found
FATAL: Error running install command for nvidia
[/PHP]

I get the the FATAL:---- part when I do startx with my old xorg.conf

---

### Post by Boexli on 2008-06-21
works now with the latest updates - cheers nick

---

