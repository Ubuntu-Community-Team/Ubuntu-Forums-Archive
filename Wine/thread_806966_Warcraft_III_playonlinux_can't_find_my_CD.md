---
title: "Warcraft III playonlinux can't find my CD"
date: 2008-05-25
forum: Wine
---

### Post by kob0724 on 2008-05-25
I installed Warcraft III using playonlinux. But whenever I try to play, I always get this error message:
> 
Please verify that your frozen throne disc is in your CD-ROM drive, then click on 'Retry'


Does anyone know how to fix this?

---

### Post by Toffeeapple on 2008-05-25
Install the latest patch it removes the cd check. You can get it [here]("http://us.blizzard.com/support/article.xml?articleId=20673")

---

### Post by kob0724 on 2008-05-25
That didn't work. I applied the patch and I'm still getting the same error.

---

### Post by tatrefthekiller on 2008-05-26
You don't have to use play on linux... Warcraft works very well using only wine.
Install Warcraft with : wine /mnt/cdrom0/setup.exe
Install Frozen Throne with : wine /mnt/cdrom0/setup.exe
Patch with : wine patch1.21.exe

And play with wine ~/.wine/drive_c/Program\ Files/Warcraft\ III/Frozen\ Throne.exe -opengl

---

### Post by Swarms on 2008-05-26
Otherwise go to Blizzard.com store, there you can register your cdkey and download a digital version of your Blizzard games. (WC3 and SC atm.)
The downloader downloads an .exe file which installs VERY quick and applies newest patch automatically.
Nn for playonlinux, just wine file.exe

---

### Post by kob0724 on 2008-05-27
Both of those are great solutions which I am eager to try. However, whenever I run either of them I get this error message.

> 
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:spoolsv:serv_main (0 (nil))


---

### Post by smd0665 on 2008-09-30
> **Toffeeapple said:**
> Install the latest patch it removes the cd check. You can get it [here]("http://us.blizzard.com/support/article.xml?articleId=20673")

How do you install the patch with PlayOnLinux?

---

### Post by mr.niceguy&lt; on 2009-05-08
do you have da cdrom? then just copy the 24kb icon in the disk into your warcraft III folder and it will work<<<<<<<<<<<Answer is correct.

---

### Post by darkest-nyte on 2009-12-11
Am I the only person who is having issues getting WC3 to run flawlessly using wine and the -opengl switch? The game runs fine at first, but then weird things start happening with the graphics tiling. The colors of the interface abruptly begin changing to weird colors. For instance, while playing DotA, the ground and trees (which are supposed to be green 3D objects), turned a flat gray color and almost appeared as if they were rough 3D objects. Anyone else notice this with their WC3 gameplay?

*- Darkest-Nyte -*

---

