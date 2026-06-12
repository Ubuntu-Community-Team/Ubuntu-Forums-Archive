---
title: "windows in fstab"
date: 2005-09-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by shomi on 2005-09-18
hello everyone, 

ive searched the how-to but i couldn't find what i was looking for, 

what is the line that i need to add to fstab in order to add the windows partition to my linux???
with read/write ....

thanks

shomi

---

### Post by acariquara on 2005-09-18
[QUOTE=shomi]hello everyone, 

ive searched the how-to but i couldn't find what i was looking for, 

what is the line that i need to add to fstab in order to add the windows partition to my linux???
with read/write ....

thanks

shomi[/QUOTE]
 > sudo gedit /etc/fstab

look for the lines that have "vfat" in there

where it reads "defaults", substitute it for 

iocharset=utf8,umask=000

---

### Post by Mano[FA] on 2005-11-27
for more newbies like me:

```

sudo mkdir /media/win_hd
sudo gedit /etc/fstab

```
add this line
```

/dev/hdb3  /media/win_hd  vfat  iocharset=utf8,umask=000  0  0

```

where **hdb3** is the partition you want to mount in read/write. hda1 in case you want to mount windows C:

:confused:  I'd like to know what iocharset=utf8,umask=000 does, but it works :cool:

---

