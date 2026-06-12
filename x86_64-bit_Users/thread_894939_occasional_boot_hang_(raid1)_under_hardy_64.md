---
title: "occasional boot hang (raid1) under hardy 64"
date: 2008-08-19
forum: x86 64-bit Users
---

### Post by ruiruas on 2008-08-19
Hi,
I have my system installed intirely on software raid 1. I never had a problem with dapper, but since the upgrade to hardy, the system occasionally hangs during boot. It seems it can't find the boot raid array (its after the grub menu, when it tries to use the kernel boot image).

I end up in a console (initramfs) and after entering the "reboot" command, everything works fine. Then, two or three week later this happens again, and again after a reboot it works fine (after boot, when checking mdadm, the raid is working flawlessly). 

Can anyone help? Thanks

---

### Post by scu-ba-de-buntu on 2008-08-20
I know there is a forced check on harddrives every so many - 25? - times. Is a similar thing happening? Also, do you have any scheduled tasks, such as CRON? When I was making my own bootable SLAX / DSL branch I did some stuff in (if I remember correctly) the rc.X directories. Check to see what boot/shutdown scripts are operating on your box. Hopefully that helped.

---

### Post by ruiruas on 2008-08-20
Hi,
no. the problem isn't with jobs being performed on boot. It seems that grub can't mount the raid arrays... I don't know if it can't find them or if they are unavailable by some reason.

Thanks anyway. Does anyone else have an idea?

---

### Post by -MoonDoggie- on 2008-08-22
whoa, actually i think i have the same problem only with the live CD. i get to some black screen with the command line "initramfs:" i cant boot at all and for some reason, now windows vista is all like, "oh hey, that cd key you got there is invalid buddy. must not be running genuine vista." any help with this problem i'm having?

Edit: i dont currently have ubuntu on this system. i'm trying to install but i cant even get to the live cd environment.

---

### Post by _Rosco_ on 2008-09-03
Have you run a CHKDSK on the Vista drive?  Ubuntu has issues with the NTFS filesystem if there are any problems.  Check out this article, there are a couple of related things [http://www.proposedsolution.com/solutions/ps0017.php](http://www.proposedsolution.com/solutions/ps0017.php)

Hope this helps

~Rosco~

---

### Post by ptn107 on 2008-09-03
I confirm; the same problem exists with my raid 1 setup (also x86_64).  I have also been able to reproduce this problem in a VM, so it must be a bug.

---

### Post by ruiruas on 2008-09-07
> **_Rosco_ said:**
> Have you run a CHKDSK on the Vista drive?  Ubuntu has issues with the NTFS filesystem if there are any problems.  Check out this article, there are a couple of related things [http://www.proposedsolution.com/solutions/ps0017.php](http://www.proposedsolution.com/solutions/ps0017.php)

Hope this helps

~Rosco~

"Nop". It has nothing to do with Vista either... I don't have it in my PC (and I don't think I'll ever have it! :-) )
Its a problem with the software raid itself. 
Thanks anyway!

---

### Post by hopper333 on 2008-10-28
similar problem here with 2.6.24 update

on hardy server-amd64, dual quad-core opterons on Tyan Thunder mobo, software RAID 1 with mdadm

upgraded to -21 and now it hangs for a long time then drops into busybox saying it "can't find /dev/md2"  i.e. my /  strangely though, it *can* find /dev/md1 -> /boot and /dev/md3 -> home with no problem

dropping back to -19 & everything is OK again

without wanting to be unappreciative of the excellent Ubuntu setup in general I have to ask - for a LTS server OS shouldn't testing have picked this up?

M

---

### Post by matiasow on 2008-11-05
Same problem here, but running 32-bit Ubuntu 8.04 Server on AMD64.
Looks like Grub can't find root partition on the RAID volume.

---

### Post by unclepedro on 2008-11-10
I'm having what looks like the same issue on an ASUS K8N-DL (dual dual-core Opteron 265s with an nvidia northbridge). I'm trying to install 2.6.24-19 now to see if this resolves the issue...

---

### Post by unclepedro on 2008-11-10
[waiting for a fsck...] Has anyone filed a bug about this?

---

### Post by unclepedro on 2008-11-10
Heh, ok, the bug is here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/290231/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/290231/)

As usual, I should look before I leap. For the record, 2.6.24-19 did not help me. I'm trying some older kernels.

---

### Post by unclepedro on 2008-11-11
So, I've been updating the bug report, but I haven't heard anything yet. Basically, the deal for me (which may or may not be the same thing that you are experiencing) is that when I boot with the new kernels 2.6.24-x, it is not finding my lvm partitions on my RAID1 device; that is, it finds /dev/md1, but it does not find the lvm groups -- specifically, /dev/mapper/group0-linux which is specified as the root= option in grub.

Unlike you guys, I do not have any luck with "reboot" on the busybox console, and it did not work when I tried to go back to 2.6.24-19 or any other 2.6.24 kernel. I'm still using a 2.6.15 kernel from Dapper.

Any ideas?

---

### Post by caljohnsmith on 2008-11-11
Maybe you could try adding "rootdelay=X" where X is some number, to the end of your kernel line, like so:
```
title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=77677cb5-6e56-4936-a373-80c15de06bca ro quiet splash [COLOR="Red"]rootdelay=130[/COLOR]
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```
Since your problem is intermittent, it might help to add a slight delay to the booting process so that your RAID array has a chance to be properly detected. Maybe it's a long shot, but it couldn't hurt to try.

---

### Post by unclepedro on 2008-11-12
Well, I'm not sure if I am having exactly the same problem as the others. For one thing, my problem does not seem to be intermittent; reboot doesn't help, so I don't think that a boot delay would help. Thanks though!

When I boot and fail into initramfs, it appears to see /dev/md1 (my root device) but does not see (or activate) /dev/mapper/group0-linux -- the lvm partition *on* /dev/md1 that I use for /. My menu.lst has the argument root=/dev/mapper/group0-linux which has worked in the past.

I thought that lvm on RAID1 worked "out of the box" on Ubuntu kernels... does anyone know if I need to do anything different or should be specifying my root partition in a different way? (For example, I see that your root= specifies a UUID... I will try that when I get home.)

---

### Post by ruiruas on 2008-11-12
Hi,
I also think that's a good idea. I just noticed that my webserver also lists the root in grub as "/dev/mdX".
Please let me know how it worked out with the UUID.

---

### Post by caljohnsmith on 2008-11-12
Unclepedro, do you mind posting your /boot/grub/device.map? That would help me understand better how Grub is trying to boot your RAID setup.

---

### Post by unclepedro on 2008-11-12
[flynn(/boot/grub)] cat device.map 
(hd0)   /dev/sda
(hd1)   /dev/sdb

sda and sdb are spanned by two RAID1 md devices, md0 (which is RAID1 boot) and md1, which is / and /mythtv, both defined as logical volumes on top of md1.

... i'm going to try booting with the UUID of the lvm partition instead of the /dev/mapper/ name.

---

### Post by unclepedro on 2008-11-12
Using the UUID did not help, nor did the root delay parameter.

Here's my output of /etc/mdadm/mdadm.conf (which should be used in the initramfs):

> [flynn(/etc/mdadm)] cat mdadm.conf 
DEVICE partitions
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=2dc57d11:e85b7d22:aa13769b:96f87ac4
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=56b78d14:b58d881e:5fc49bea:24c7fc50
MAILADDR root

... as you can see the md devices are there, and they appear during boot... but for some reason the lvm devices are not found on md1.

Now that I think about all this, my issue could be related to a failure during the upgrade from Dapper to Hardy (which was several weeks ago but I had not since rebooted). Specifically, when it was installing a new kernel, /boot ran out of space. I fixed the space issue on /boot and reinstalled the failed packages, and everything seemed to be fine. I have since uninstalled and reinstalled 2.6.24-21, etc., and regenerated initramfs, so the only thing I'm wondering is if whether I missed some conversion magic needed for lvm to work in a Hardy initramfs (which was not properly bestowed up my prior Dapper setup). 

From the looks of it though, the initramfs disk boots, finds the md devices, but utterly fails to see the lvm devices *on* md1.

---

### Post by unclepedro on 2008-11-12
Yeah, the more I look at this the more I think I'm just dealing with a half-baked initrd.

---

### Post by unclepedro on 2008-11-12
Well, wait a second. When I boot 2.6.24-21, the initramfs *has* the lvm tools... it's just that vgscan and vgchange do not find anything on /dev/md1... so maybe my initramfs is being built properly. Ideas?

---

