---
title: "Windows Office 2007 Installed, All works except Powerpoint"
date: 2008-11-16
forum: Wine
---

### Post by MTGap on 2008-11-16
I was able to install Microsoft Office 2007 after many attempts, but I can't open Powerpoint up, it always fails and never comes up when using windows xp. When I tried windows vista it gave me an error report. See the attached screenshot.

---

### Post by Kinst on 2008-11-16
```
wget http://www.kegel.com/wine/winetricks
sh winetricks riched20 riched30
```

Try that.

---

### Post by MTGap on 2008-11-16
I got this in the terminal after Powerpoint failed again:

```

mtgap@MTGap-Ubuntu:~$ sh winetricks riched20 riched30
Cannot find cabextract.  Please install it (e.g. 'sudo apt-get install cabextract' or 'sudo yum install cabextract').
Executing cabextract --directory=/home/mtgap/.wine/drive_c/winetrickstmp /home/mtgap/.winetrickscache/Q249973i.EXE
winetricks: 1510: cabextract: not found
Note: command 'cabextract --directory=/home/mtgap/.wine/drive_c/winetrickstmp /home/mtgap/.winetrickscache/Q249973i.EXE' returned status 127.  Aborting.
mtgap@MTGap-Ubuntu:~$ 

```

---

### Post by Kinst on 2008-11-16
Okay, install cabextract then try again.

---

### Post by Blue Wolf on 2009-05-05
Nice Job, that works great. Should this get marked as a solved or something?

---

### Post by NightMKoder on 2009-05-05
1) Don't dig up old threads, and 2) You don't need the winetricks. Just go inside winecfg and set riched20 to native.

---

### Post by jhoeijao on 2009-05-30
> **MTGap said:**
> I was able to install Microsoft Office 2007 after many attempts, but I can't open Powerpoint up, it always fails and never comes up when using windows xp. When I tried windows vista it gave me an error report. See the attached screenshot.

My Powerpoint works well with this guide. Give this a try [http://ubuntuforums.org/showthread.php?t=1173365&highlight=microsoft](http://ubuntuforums.org/showthread.php?t=1173365&highlight=microsoft)

---

