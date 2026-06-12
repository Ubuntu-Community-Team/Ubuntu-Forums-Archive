---
title: "how do i make a fat 32 drive usable in ubuntu"
date: 2006-05-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by dead7iest-weap0n on 2006-05-06
ok how do imake a fat 32 drive usable in linux? It appears in windows, but not in linux

---

### Post by neouser99 on 2006-05-06
find out what partition it is eg /dev/sdb1, then mount it somewhere. and easier way might be to go to the disk management under the administration utility and setup where you want it to automagically setup said windows partition

-neo

---

### Post by glenn45 on 2006-05-06
do as neouser99 says. determine the partition name. using maybe gparted or fdisk. then try mounting it .  for example if the partition of your fat32 is located at /dev/sda5 then first create a directory in your /media folder (e.g i create window using
mkdir  window

then once you have the directory /media/window try mounting it with the command:

mount /dev/sda5 /media/window -t vfat -o umask=000

---

### Post by notepad on 2006-05-06
/etc/fstab is the file the system looks to for information about which file systems to mount on boot. i have 2 IDE drives in my box each with a fat32 partition on them. the partitions are known as hda5 and hdb1. in rough terms, the hda5 partition is the 5th partition on the master and hdb1 is the first partition on the slave. the fstab entries that i use for these partitions are these:

/dev/hda5   /media/hda5   vfat   users,rw,uid=1000,gid=100   0   0
/dev/hdb1   /media/hdb1   vfat   users,rw,uid=1000,gid=100   0   0

try man mount and man fstab for more info about the options ive used.

---

### Post by Lin-X on 2006-05-07
Before you try anything else, please look at the How To's on the forum start page.
You will find what you need there. If there is something more you need, do a search in the forum. (Look up and to the right for the Search box.) I don't mean to trash anybody's answer, but really the very best, and most accurate information you need is in the How To's. Best advice you'll ever get, go there first every time you want help doing something.

---

### Post by mdmykel on 2006-05-08
The only thing I found about this topic in the HOWTO section was mounting an NTFS drive and when doing a general search, this thread seemed like the most applicable and it worked for me.

---

### Post by dead7iest-weap0n on 2006-05-10
ok when i try the mount command it tells me that only root can do that. I triesd logging into root, but i dont know the default password.

---

### Post by alastair lewis on 2006-05-11
You need to ```
sudo mount /dev/sda5 /media/window -t vfat -o umask=000
``` and enter your password when prompted.
There is no root account with ubuntu.
```
sudo -s -H
```
followed by your password gives you root privledges so you don't have to type sudo with every command.

---

### Post by notepad on 2006-05-14
there is a root account in ubuntu and i think the default password is password but im not sure. you change the password as a normal user by going to

system > admin > users and groups

select" show all users and groups"

select root and click on properties. the rest is obvious.

why dont you modify your fstab so you dont have to mess around manually mounting your drive anyway?

try looking at these for more help
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)
[http://ubuntuforums.org/showthread.php?t=1886](http://ubuntuforums.org/showthread.php?t=1886)

---

