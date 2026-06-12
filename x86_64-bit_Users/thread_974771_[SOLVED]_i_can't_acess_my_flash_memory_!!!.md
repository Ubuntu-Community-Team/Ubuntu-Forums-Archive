---
title: "[SOLVED] i can't acess my flash memory !!!"
date: 2008-11-07
forum: x86 64-bit Users
---

### Post by eng.reem on 2008-11-07
hi all,this is my first time to install ubuntu on my laptop,
i've ubuntu 8.10 and i can't access neither flash memory contents nor cd ROM
contents when i open them i find "Lost+found" folder then i get this error message when i try accessing it:

You do not have the permissions necessary to view the contents of "lost+found".

Thanks in advance :)

---

### Post by cariboo on 2008-11-07
You're looking in the wrong place, if you are looking in Lost + Found. That directory is for recovered files when Linux finds a problem with your hard drive. You need root access to look in the directory

Your external devices get mounted in /media.

Look in Places-->Computer to see which devices sre mounted.

Jim

---

### Post by eng.reem on 2008-11-08
thanks for UR reply ,but may be u didn't got what i meant 
i'm not looking in "lost+found" directory what happens is :
when i put my flash memory and open the media from  computer i don't find the flash memory contents inside it ,i find folder called :"lost+found"
when i try to open it i get that error message :
You do not have the permissions necessary to view the contents of "lost+found".
i tried to figure out authorizations by enabling any user to access removable devices but no use !!
any help plz ? :(

---

### Post by Raouf on 2008-11-08
> **eng.reem said:**
> i find folder called :"lost+found"
when i try to open it i get that error message :
You do not have the permissions necessary to view the contents of "lost+found".
i tried to figure out authorizations by enabling any user to access removable devices but no use !!
any help plz ? :(

hey Reem, 
This how to navigate without any problems
```
gksudo nautilus
``` 

check **[[COLOR="DarkRed"]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=549703")** :D
take care

- Raouf

---

### Post by eng.reem on 2008-11-08
yes it worked 
thanks alot

---

### Post by ssam on 2008-11-08
if you just see a folder called lost and found you are probably looking at an empty ext2 or ext3 formated disk.

if you want the usb disk to be readable on windows (and mac) as well as linux then you probably want to be formated as FAT32.

---

### Post by eng.reem on 2008-11-08
that's exactly what i did i formated it on vista then   
used  :


```
gksudo nautilus
```
now it worked 

but unfortunately i had to lose data on my flash memory 

thanx

---

