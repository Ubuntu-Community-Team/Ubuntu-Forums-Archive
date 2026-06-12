---
title: "World of Warcraft crashes when entering the world"
date: 2011-10-22
forum: Wine
---

### Post by MIssigno on 2011-10-22
Hi there!

So... im having this problem... After I select a character and enter the world, WoW suddenly crashes!

Looked for all solutions all over the Internet, none were useful.

I tried --opengl the command, "SET gxApi "OpenGL"" config.wtf. One solution i read was to modifiy xorg.conf and set some variables... (i cant fin xorg.conf anymore, but i dont think that is).

Soooo, any ideas? I also tried using 1.2 version of wine, and lastests 1.3 too; same results.

I have a Samsung RV510 laptop.

Thanks!

---

### Post by ubupirate on 2011-10-22
Are you using an Intel GPU?

---

### Post by MIssigno on 2011-10-22
> **ubupirate said:**
> Are you using an Intel GPU?


Yes, i am. Intel graphics media is the "videocard" my laptops has.

---

### Post by cwwilson721 on 2011-10-23
Search this forum for "Intel+wow"...Good luck.

The answers are there

---

### Post by MIssigno on 2011-10-23
Belive me PLEASE... I googled for this solution for like a week! 

Thanks this forums for its efficiency!

Solution:
```
sudo apt-get install driconf 
Open driconf, go to  the tab "image quality" and activate the S3TC texture compression, even  if the software support is not available. (Default is "no" change to  "yes") 
```

:)

---

