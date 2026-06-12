---
title: "Calling tseliot!!! I need help with Nvidia please"
date: 2006-03-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by ford460 on 2006-03-24
I am using the Nvidia 6600 GT, so its not too old. And no tseliots link and method 2 did not work (or any other method for that matter) it gave me the same output I've been having.  It did give some good information on kernels though, and when I go to /usr/src and ls the directory, I find this output interesting:
total 28
drwxr-xr-x 18 root root 4096 2006-03-24 09:03 linux-headers-2.6.12-10
drwxr-xr-x 4 root root 4096 2006-03-24 09:03 linux-headers-2.6.12-10-amd64-generic
drwxr-xr-x 18 root root 4096 2006-03-23 21:06 linux-headers-2.6.12-9
drwxr-xr-x 4 root root 4096 2006-03-23 21:06 linux-headers-2.6.12-9-amd64-generic
drwxr-xr-x 4 root root 4096 2006-03-23 22:36 linux-headers-2.6.12-9-amd64-k8
drwxr-xr-x 4 root root 4096 2006-03-23 22:36 linux-headers-2.6.12-9-amd64-k8-smp
drwxr-xr-x 4 root root 4096 2006-03-23 22:36 linux-headers-2.6.12-9-amd64-xeon
why do I have so many kernels installed? I may be wring but it would seem that I need only 1, the one for my machine, which I think is *-amd64-generic. I have an Athlon 64 3000+ proc, and am running Ubuntu 5.1 x64 edition. Furthermore, it doesn't seem to be the latest kernel available considering what I've come up with google. For some reason apt-get upgrade, doesn't find any newer kernel versions, nor does synaptic. I can find at least 2.6.16 on the web.  
Thanks guys,
A very confused
Steve
Dallas, TX
I am having an error to the extent : nvidia installer couldn't compile a kernel, or something like that.
Unable to find kernel source tree seems to be another error.

---

### Post by FluffyElmo on 2006-03-25
Ubuntu releases a new version every six months and then issues only security fixes until the next release. So it's normal for the kernel to be a bit behind the latest Debian at this stage. When Dapper comes out it will be fully up to date and the cycle will begin again.

It's also normal to have multiple kernels available. When a new kernel is installed/upgraded the old one remains and is selectable via the grub menu (hit Esc when you see the message). If you have problems with an update this lets you go back to a working configuration. You can easily remove any extra kernels using Synaptic to save space or confusion.

The only odd one in the list is the Xeon one, can't imagine that being any use. ;) You might also have better luck using the latest k8 kernel instead of generic, it's compiled specifically for amd64.

While this doesn't help your core Nvidia problem hope it at least removes some confusion. Good Luck!

---

