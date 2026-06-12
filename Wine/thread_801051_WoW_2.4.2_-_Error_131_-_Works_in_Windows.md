---
title: "WoW 2.4.2 - Error 131 - Works in Windows"
date: 2008-05-20
forum: Wine
---

### Post by Knad on 2008-05-20
Hey Hey

I have WoW installed on a shared FAT32 partition between Windows XP SP3 and Ubuntu 8.04. WoW works fine in windows, but does not in ubuntu.

I used to be able to run it, but the graphics were so slow, so I used windows. After the 2.4.2 patch, and after installing Wine 1.0 RC I tried Ubuntu again, I am getting the error:

ERROR #131 (0x85100083) File Corrupt
Program:	E:\World of Warcraft\Wow.exe
File:	DBFilesClient\AnimationData.dbc

I am using the modifications from [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) (i.e. Changing the cfg file and adding reg tweak). I have ran with -opengl and with -d3d, with the same error. I have also used the WoW repair utility to delete the cache and check the files.

The file cannot be corrupt, as it works perfectly well in Windows (same files!!).

Any ideas? (info attached)

/Adam

Laptop : Dell Inspiron 6400, inbuilt graphics
Wine : 1.0~rc1~winehq0~ubuntu~8.04-1
WoW : 2.4.2.8278

---

