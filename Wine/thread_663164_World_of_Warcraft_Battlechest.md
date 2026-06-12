---
title: "World of Warcraft Battlechest"
date: 2008-01-09
forum: Wine
---

### Post by mrwestfall on 2008-01-09
I own the battlechest version of WoW and I was wondering how to access the installer.exe on the disk. From what i was able to find out on my own, i can't find it because the disk has different parts that only show when in windows or in a mac. Any help finding it would be great. By the way, It would be a hassle to find a windows computer and get it from there. Thanks for the help.

---

### Post by Ferrat on 2008-01-10
I have the same problem with the DVD version but if you got a deacent connection, try downloading the installer from wow homepage

---

### Post by RabidWeezle on 2008-05-09
According to the guys in #winehq on freenode irc server:

> <odietsch> RabidWeezle, AFAIR it's possible to use the webinstaller of WoW for installing the data from DVD

I'm about to try it

They also said:

> odietsch> RabidWeezle, [http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine](http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine)

---

### Post by alaQ on 2008-07-05
It mounts the Mac only side because of the hybrid dvd nature.  In order to mount it fully, unmount the drive (open nautilus, right click -> unmount), then in a terminal, enter this:
```

sudo mount -t iso9660 /dev/x /media/y

```
where x is the device file for your cdrom drive (something like scd0) and y is the mount point you want (probably use cdrom or cdrom0).  Then, you'll be able to get to it.

---

