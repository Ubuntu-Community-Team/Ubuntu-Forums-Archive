---
title: "Problem Upgrading to 8.04"
date: 2008-04-28
forum: x86 64-bit Users
---

### Post by iamroot on 2008-04-28
I have a Dell Vostro 1000 AMD64 laptop running Ubuntu 7.10. I am trying to upgrade to Hardy Heron but am unsuccessful. Here's what happens:

I try to run the Update Manager to get all my updates before upgrading.

I get an error message: **'Not all updates can be installed'**

I try to run a Partial upgrade (as recommended) and another error comes up that reads: **'Unable to get exclusive lock: This usually means that another package management application (like apt-get or aptitude) already running. Please close that application first.'**

There's no other package management application running, so I hit OK and update manager closes.

I open update manager again and this time hit "close" instead of "partial upgrade" and return to my main update manager window. There are 3 updates shown, but when I check for more, there are 64 updates, but they won't download and I get this error message: 

[B]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/B]

So I run 'sudo dpkg --configure -a' and get this:

Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-image-2.6.22-14-generic (2.6.22-14.52) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.22-14-generic (--configure):
 subprocess post-installation script returned error exit status 2
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: subprocess post-installation script returned error exit status 1

I try running apt-get install update and apt-get install upgrade, but they both produce the same 'E: dpkg was interrupted' error. 

**Now I'm at a dead end. Can anyone help?**

---

### Post by esdaniel on 2008-04-28
Try to run:

 	Code:
 	sudo apt-get -f install 
If that does not help:

 	Code:
 	sudo apt-get update && sudo apt-get -u dist-upgrade

---

### Post by villindesign on 2008-04-30
also, you could open synaptic, reload the repositories, and then select 'mark all for upgrade'.

---

### Post by Sef on 2008-05-04
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

Applications > Accessories > Terminal

then type

```
sudo dpkg --configure -a
```

After that, all should be ok.

---

