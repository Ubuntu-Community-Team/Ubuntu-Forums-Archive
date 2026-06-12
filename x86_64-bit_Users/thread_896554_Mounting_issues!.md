---
title: "Mounting issues!"
date: 2008-08-21
forum: x86 64-bit Users
---

### Post by IamNehalem on 2008-08-21
Hello dear friends, hello community!

**First of all let me go a lil off topic **since i'm a very enthusiast about using such a great distro. Let me just say that before i jumped to Ubuntu Hardy i tried all the other major distros out there (Fedora 9, openSuSE 11.0, Mandriva 2008 PP) and i found Ubuntu to be the best especially from the ease of use perspective and for the best community. It may very well not be the absolute best but for me it is since all my questions related to linux ended up best answered on Ubuntu forums. :)

So i am now sold to Ubuntu for ever :) Just a few days ago i started to read Ubuntu related books especially to familiarize myself with the command line. I'm not 100% linux newbie but still consider myself a newbie. I only had experience for half a year with Mandriva and now and then with Fedora. However i really want to dig deep into Ubuntu linux since it's so fun to get rid of Windows clutches. Honestly speaking i still have Windows Vista (yeah i know the worst one) installed as a dual boot but i also like to play DX10 games. So when wine/Cedega wll come up with some DX10 emulation i will happily remove Windows once and for all.

**Back to the topic** i'd like to ask your help for the following issue. I have 4 hdds installed in my computer with NTFS on them. One hdd has mixed NTFS and ReiserFS partitioning. I still keep NTFS since all my data is still on NTFS and well Windows can't read from something else. The thing is when i boot up Ubuntu the hdds are not properly mounted...i think. For example i set the desktop background from a picture located on a NTFS hdd. When i boot Ubuntu it shows me a orange desktop and after a while or after i click on Places->Butcher 2 (the hdd where the pic is located) the desktop is back again with the proper wallpaper. The same happens to Azureus when i run it after a fresh restart it cannot find the torrents saying "missing data". As soon as i literally access those hard drives all comes back to normal. So the question is: How can i make Ubuntu forcely mount those hdds and get them ready as soon as i login?

Here is my fstab configuration:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=8df29643-4599-4286-953e-6f8d5971eaa6 /               reiserfs notail,relatime 0       1
# /dev/sdb3
UUID=f75a633b-d157-4a2b-b22c-5d2fc0113c4a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
//192.168.0.200/Public  /media/Network  cifs  guest 0  0
```


Thank you very much! 
PS: The mapped network drive behaves the same.

PSS: Should i really worry about viruses? I mean can you point me to some linux virus literature/documentation especially compared to windows viruses. I'm like to install an antivirus, proabably Avira at least for the sake of not spreading windows viruses unknowingly. What do you recommend? Thank you again, and sorry for the OFF TOPIC! VERY VERY HAPPY! Cheers.

---

### Post by puppywhacker on 2008-08-21
Hi,

If you paste your fstab, you are not a newbie. you don't fools us :) First identify your partitions. Alternatively find their UUID.

dmesg | egrep "[s|h]da[1-9]"

gparted will give you the same but in a graphical application. Then add your NTFS partitions to your fstab

HDA is an PATA harddisk
SDA is an SCSI or SATA harddisk

 /dev/sda1 /mnt/windows ntfs-3g defaults 0 0

And as a bonus some commands you might want to try.
 mount /mnt/windows
 umount /mnt/windows
 mount -t ntfs-3g /dev/sda1 /mnt/windows

PS The mapped drive sounds like it tries to mount before your network is fully up and running. With _netdev as option you can postpone the mounting until the network is there.

//wherever/blah /somewhere/blah cifs guest,_netdev,uid=1000,iocharset=utf8,codepage=unicode,unicode 0 0

PPS [http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)

---

### Post by IamNehalem on 2008-08-21
> **puppywhacker said:**
> Hi,

If you paste your fstab, you are not a newbie. you don't fools us :) First identify your partitions. Alternatively find their UUID.

dmesg | egrep "[s|h]da[1-9]"

gparted will give you the same but in a graphical application. Then add your NTFS partitions to your fstab

HDA is an PATA harddisk
SDA is an SCSI or SATA harddisk

 /dev/sda1 /mnt/windows ntfs-3g defaults 0 0

And as a bonus some commands you might want to try.
 mount /mnt/windows
 umount /mnt/windows
 mount -t ntfs-3g /dev/sda1 /mnt/windows

PS The mapped drive sounds like it tries to mount before your network is fully up and running. With _netdev as option you can postpone the mounting until the network is there.

//wherever/blah /somewhere/blah cifs guest,_netdev,uid=1000,iocharset=utf8,codepage=unicode,unicode 0 0

PPS [http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)

I understand what you are saying, and sorry i made a mistake writing hda when it was sda since i have SATA hard drives. Anyway what really troubles me is the poor population of fstab. When i used to operate an openSuSE 10.3 on my server i used to see fstab populated with all my hard drives and partitions but now in Ubuntu i don't see that. Can you explain? I mean the only thing that come to my mind is that Ubuntu mounts the partitions only on demand. Also i saw that after i access the partitions Ubuntu places the shortcut on my desktop.

And yes thank you, the network drive needs that command added there but i forgot what it was to make it mount after the network was established.

PPS: Thank you for the wiki info but i'd like more pls :cool:

---

### Post by IamNehalem on 2008-08-22
dmesg | egrep "[s|h]da[1-9]" returned this:

```
andrei@Andrei:~$ dmesg | egrep "[s|h]da[1-9]"
[   44.268900]  sda1
andrei@Andrei:~$ 

```

I was expecting to see all my sata hard drives along with my partitions. Also the command was ran after a clean boot.

---

### Post by kinetek on 2008-08-22
Run the command 'df -h' after a fresh reboot. This should output all of your currently mounted filesystems.

 $ df -h

Any drive that does not show up is not being mounted upon boot, and will have to be entered in the /etc/fstab file as puppywhacker advised in the above post.

Once these entries have been added, then the partitions will mount on boot.

---

### Post by Ehtetur on 2008-08-23
Hi IamNehalem - Ubuntu doesn't need a physical drive's filesystem mount point in /etc/fstab to be able to mount it... HAL initializes filesystems as needed... The only time they need to be in fstab is when you want them initialized at boot...
As you know, to verify the different drives/partitions that ubuntu sees, you can run this:
> sudo fdisk -l

If you don't need the NTFS filesystems initialized at boot but only as you need to access them, I would just add the disk mounter applet to your panel.. You can use it to mount and unmount the filesystems...

---

### Post by IamNehalem on 2008-08-24
Hey guys! Thanks i will give it a try and see how well the drives are mounted. As i assume the only way to mount NTFS partitions with full w/r access is via ntfs-3g.

---

### Post by wrprlp on 2008-09-01
hi. I have a different issue I have 1 Sata Hd and 1  hda Hd. I want to increase my disk storage by adding another Hda hd, but when I do Grub wont boot. I am sure it must be the boot order but I am not sure how to fix this so I can add the hd. I tried changing the boot order in my cmos but that doesn't do it.
help needed thanks,

---

### Post by IamNehalem on 2008-09-02
> **wrprlp said:**
> hi. I have a different issue I have 1 Sata Hd and 1  hda Hd. I want to increase my disk storage by adding another Hda hd, but when I do Grub wont boot. I am sure it must be the boot order but I am not sure how to fix this so I can add the hd. I tried changing the boot order in my cmos but that doesn't do it.
help needed thanks,

I dunno if i'm qualified to give advice but have you saw the jumper settings on the ATA hard drives? Also on bios boot what's the order you see at the detection of the hard drives? Also if you have in bios a boot order for the hard drives you might wana check that out also.

---

### Post by soxs on 2008-09-02
> **wrprlp said:**
> hi. I have a different issue I have 1 Sata Hd and 1  hda Hd. I want to increase my disk storage by adding another Hda hd, but when I do Grub wont boot. I am sure it must be the boot order but I am not sure how to fix this so I can add the hd. I tried changing the boot order in my cmos but that doesn't do it.
help needed thanks,

Edit the boot options while being in grub (with "e" I think, but I am not quite sure)
there will be something like hd(0,1) try to change the first number to one higher and/or lower. One should work. If you're done, and ubuntu booted up successfully, do:
```
sudo nano /boot/grub/menu.lst
```
replaced any hd(p,y) related to ubuntu kernels with hd(x,y) (x being the one tried to boot with and worked; p being the number which was the prior value)
Sry for my bad english, you may have to read it multiple times to get every point... sry *g*

---

