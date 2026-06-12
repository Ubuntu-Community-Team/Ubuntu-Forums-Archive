---
title: "Help setting up my dual boot correctly (2 HD's)"
date: 2005-09-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by grimdeath on 2005-09-03
Hi, first post here!

just to let you know ive searched over MANY post trying to get an idea of what ive done wrong with my boot loaders. I think it has to do with the way i installed not the order:

my two drives are:
Master = 80gb w/kubuntu
Slave = 120gb w/WinXPpro(which i installed first)

when installing kubuntu i didnt see any options directly for grub to setup my boot choices or anything like that, but grub is installed and works, only catch is windows doesnt show up, i see the following:
linux amd64 default
linux amd64 recorvery
linux amd64
linux memtest+86

i tried editing my menu.lst file for grub to look like this:

> ...(deleted comments)...

## ## End Default Options ##

title  Ubuntu, kernel 2.6.10-5-amd64-generic Default 
root  (hd0,0)
kernel  /boot/vmlinuz root=/dev/hda1 ro console=tty0 quiet splash
initrd  /boot/initrd.img
savedefault
boot

title  Ubuntu, kernel 2.6.10-5-amd64-generic Default (recovery mode)
root  (hd0,0)
kernel  /boot/vmlinuz root=/dev/hda1 ro console=tty0 single
initrd  /boot/initrd.img
savedefault
boot

title  Ubuntu, kernel 2.6.10-5-amd64-generic 
root  (hd0,0)
kernel  /boot/vmlinuz-2.6.10-5-amd64-generic root=/dev/hda1 ro console=tty0 quiet splash
initrd  /boot/initrd.img-2.6.10-5-amd64-generic
savedefault
boot

title  Ubuntu, kernel 2.6.10-5-amd64-generic (recovery mode)
root  (hd0,0)
kernel  /boot/vmlinuz-2.6.10-5-amd64-generic root=/dev/hda1 ro console=tty0 single
initrd  /boot/initrd.img-2.6.10-5-amd64-generic
savedefault
boot

title  Ubuntu, kernel memtest86+ 
root  (hd0,0)
kernel  /boot/memtest86+.bin  
savedefault
boot

title windowsXP 
root (hd1,0) 
makeactive 
chainloader +1 
savedefault 

### END DEBIAN AUTOMAGIC KERNELS LIST 

did i set that correctly for windows xp(entered manually with gedit) because i know for sure that windows is hard drive 2, and the only partition on the drive...here what fdisk - l says:
> Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9356    75152038+  83  Linux
/dev/hda2            9357        9729     2996122+   5  Extended
/dev/hda5            9357        9729     2996091   82  Linux swap / Solaris

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14592   117210208+   7  HPFS/NTFS

please dont point me towards other topics just tell me if i did something overall wrong or if i just need to change a couple things!!

THANKS SOOOO MUCH if you can help me get this working!!

btw, just on the side, is there a 32bit version of kubunta that will work with my amd64 system? seeing as ive found that flash and java and a few things like that dont seem to work with the i86_64 version

again THANKS!

---

### Post by bjweeks on 2005-09-03
You boot config looks to me, but I'm not an expert. Yes, you can use the 32 bit version on an AMD 64.

---

### Post by grimdeath on 2005-09-03
ok thanks for the responce, i just noticed im getting this message when it "tries" to boot:

> title windowsXP 
root (hd1,0)
 Filesystem type unknown, partition type 0x7    <--this part!!
makeactive 
chainloader +1 
savedefault
boot (yes i just added this)

not sure why i got the amd64 version, guess it just seemed right at the time :P whats the best app to use to burn an iso(such as kubuntu or ubuntu 32bit) to a disc!! i just used nero on windows

---

### Post by bjweeks on 2005-09-04
Gnome Baker is my favorite.

---

### Post by grimdeath on 2005-09-04
hmm "gnome" baker will that work with my KDE kubuntu?

---

### Post by Kemotaha on 2005-09-05
To get windows to runn off a seperate hard drive you have to trick it to think that it is the "primary hard drive".  It is fairly easy to do,  I am doing it on my system.  I have ubuntu64 on one and winxp64 on the other.  I will deal with the problems that 64 causes (a lot less in linux then in windows).  Here is the section of windows in my menu.lst file: 

```

title		Windows XP
map	(hd0) (hd1)
map	(hd1) (hd0)
root		(hd1,0)
makeactive
chainloader	+1

``` 

If you need any other help.  Let me know.

---

