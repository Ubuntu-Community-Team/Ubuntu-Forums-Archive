---
title: "permissions could not be determined"
date: 2008-08-30
forum: x86 64-bit Users
---

### Post by nixter on 2008-08-30
Got a weird problem after a clean install of 8.04. My setup consists of 3 IDE HDD's (160 GB, 200 GB, 500 GB) and 1 IDE DVD+-RW. The system is up and running, even quite stable; but two of my disks report (when right clicking the desktop icon in Gnome and navigating to properties...) "that permissions for <drive name> could not be determined." The funny thing is that ls -l outputs the correct information. I have already changed ownership using chown; and as well have changed permissions to 755 using chmod. Am I missing something? 


There is another issue effecting the system as well - since it is disk related I'm going to mention it just in case it may be pertinent. My Pioneer DVD multi recorder drive no longer will burn dvd's nor will it allow the system to boot using DVD media. I think it may be on its last leg but - like I said - since it is disk related I figured I'd include the info.

Any help would be greatly appreciated.

---

### Post by Kilz on 2008-08-30
> **nixter said:**
> Got a weird problem after a clean install of 8.04. My setup consists of 3 IDE HDD's (160 GB, 200 GB, 500 GB) and 1 IDE DVD+-RW. The system is up and running, even quite stable; but two of my disks report (when right clicking the desktop icon in Gnome and navigating to properties...) "that permissions for <drive name> could not be determined." The funny thing is that ls -l outputs the correct information. I have already changed ownership using chown; and as well have changed permissions to 755 using chmod. Am I missing something? 


There is another issue effecting the system as well - since it is disk related I'm going to mention it just in case it may be pertinent. My Pioneer DVD multi recorder drive no longer will burn dvd's nor will it allow the system to boot using DVD media. I think it may be on its last leg but - like I said - since it is disk related I figured I'd include the info.

Any help would be greatly appreciated.

The contents of your fstab file will probably help diagnose whats going on. Open a terminal and type
```
gksudo gedit /etc/fstab
```
Then copy and paste the contents of the file that opens to a post.

---

### Post by nixter on 2008-08-30
File system table says:


proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=ecccb38e-d2d6-4e1f-936f-f708358c2d86 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda2 :
UUID=f58645fe-8143-4833-b9a6-541886545b2b none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

UUID="7c8fe1ce-657f-494a-bff6-0f8ec57462a7" /media/gMovies ext3 defaults 0 2

UUID="2da4affe-8ab9-4fdd-a449-c37f6de49866" /media/pMovies ext3 defaults 0 3

the last two entries are the ones concerning.
BTW - I placed these entries here to make these drives mount automatically; but they problem preceded me doing so.

---

