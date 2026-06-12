---
title: "64-32 bit dual boot doesn't work"
date: 2005-05-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by Terracotta on 2005-05-24
hy,
I installed both kubuntu 32bit and 64 bit, I installed 32 after 64 both on different partitions, both different home directory, only the same boot partition, but after I installed the 32bit version, the 64 wouldnt start, there was some file missing, and then it tries to start the 32 bit version for some reason???? but I end up in a console mode of the 32 bit version, starting the 32 bit version by selecting   it in grub works, only the  64 bit won't work???
Can someone help me since I am trying to do as much as I can on the 64 system, but occasionally I need some wmv files to open, or some flash-sites ....

---

### Post by FluffyElmo on 2005-05-24
First, have you considered running AMD64 with a 32bit chroot. That way you can run a single 64bit system but run 32bit apps (MPlayer, Flash, etc) as needed. A good primer on doing this is here: [http://ubuntuforums.org/showthread.php?t=24575&highlight=chroot](http://ubuntuforums.org/showthread.php?t=24575) 

But to try answering your question, it sounds to me that by using the same boot partition the 32bit install overwrote the settings for booting the 64bit version. You'll have to modify your grub settings and add an entry to boot the 64bit partition. You'll probably also have to generate an initrd.img for the 64bit install...though that is where my knowledge breaks down.

From your 32bit install as root edit */boot/grub/menu.lst* and add an entry for the 64bit install. The key entries for mine look like the following:

```

title		Ubuntu, kernel 2.6.10-5-amd64-k8 Default 
root		(hd0,0)
kernel		/vmlinuz root=/dev/hda2 ro console=tty0 quiet splash
initrd		/initrd.img
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-amd64-k8 Default (recovery mode)
root		(hd0,0)
kernel		/vmlinuz root=/dev/hda2 ro console=tty0 single
initrd		/initrd.img
savedefault
boot


title		Ubuntu, kernel 2.6.10-5-amd64-k8 
root		(hd0,0)
kernel		/vmlinuz-2.6.10-5-amd64-k8 root=/dev/hda2 ro console=tty0 quiet splash
initrd		/initrd.img-2.6.10-5-amd64-k8
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-amd64-k8 (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.10-5-amd64-k8 root=/dev/hda2 ro console=tty0 single
initrd		/initrd.img-2.6.10-5-amd64-k8
savedefault
boot

```

In the fragment above, *root (hd0,0)* refers to hda1, *root (hd1,0)* would be hdb1. If your installs are on the same disk you should be able to copy an existing entry and just point to a 64bit initrd.img.

If you don't have a 64bit initrd.img left on your boot partition then you will have to create one. You should be able to chroot into your 64bit install and generate one from the command line. I don't know how to do this myself, but you may be able to figure it out by searching the forums and the wiki.

Good Luck!

---

### Post by blinksilver on 2005-05-25
it may have to do with grub not liking that fact that your OS is 64bit, and it is 32bit

---

### Post by Terracotta on 2005-05-26
I have tried the chroot stuff once, but it didn't work that well, seemed a bit to difficult at the moment (exams coming up, so not that much time to figure a lot of things out) 
could indeed be that grub is 32 bit or so :s.

---

