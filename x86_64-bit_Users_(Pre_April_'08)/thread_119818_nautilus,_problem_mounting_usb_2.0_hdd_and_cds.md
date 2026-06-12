---
title: "nautilus, problem mounting usb 2.0 hdd and cds"
date: 2006-01-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by T31 on 2006-01-20
As you can see on my signature I have a mac mini with 512mb ram, Im having several problems since I upgrade it with a usb 2.0 case for my old 80gb hdd this was the hard disk I had on my old k7 box. I liked to play with it installing everysingle flawor of GNU/Linux I could, that means it has 8 partitions :razz: 

Well my problem is that gnome when starts not always shows me all of them, and I have to start gparted and after a loooong looooong scanning (up to longer than 15 min) maybe Im lucky and detect the rest, but this is not the end of my nightmare I have to mount the cds from a terminal, and eject them as well from terminal, for me it is just annoying but for my wife it is just end road.

someone has have same issue?

please help :(

---

### Post by ssam on 2006-01-20
do you have gnome-volume-manager running?

whats in you /etc/fstab ?

---

### Post by dombleu on 2006-01-20
I'm sure this not the issue but who knows... an update of pmount ( what the heck is that packge - I cannot say... ) did get a similar problem solved for me.

```
sudo apt-get update

sudo apt-get upgrade
```

---

### Post by T31 on 2006-01-21
this is my fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda9       /media/141205   ext3    defaults        0       2
/dev/hda2       /media/breezy   stable  reiserfs        defaults 0 2
/dev/hda8       /media/kubuntu  ext3    defaults        0       2
/dev/hda10      none            swap    sw              0       0
# /dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

# /dev/cdrom        /media/cdrom   udf,iso9660 user,noauto     0       0

/dev/cdrom     /media/cdrom0     iso9660  noauto,user,noexec,ro	0	0




everytime I try to make mount -a says me error in the line 7 so as you can see I have been trying to make it work but everysingle case without success, the package pmount I cant reinstall it and if I remove it forces me to remove half system :P and yes the gnome-manager-volume is working but again today after start the computer I only have a few of the total number of partitions avaliable ](*,)

---

### Post by T31 on 2006-01-22
This weekend I have been installing I dont know how many times because of many unstabilities in my system and I think I have found out the origin of all my troubles, I thought was becouse of the last kernels but seems to be because I install ubuntu with the usb hdd plugged in, so it could be a fail in the installator, I will try out further and write here my experiences ;)

---

