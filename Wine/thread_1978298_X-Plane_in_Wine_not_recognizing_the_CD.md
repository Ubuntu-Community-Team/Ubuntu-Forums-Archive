---
title: "X-Plane in Wine not recognizing the CD"
date: 2012-05-11
forum: Wine
---

### Post by djpemberton on 2012-05-11
I have installed a Windows version of X-Plane 7 in Wine in Ubuntu 12.04 (I had the CD from before I began using Linux). It works beautifully, except for one thing. It doesn't recognize that I have the CD in the drive, so it will only start in demo mode. Are there any ways to make it recognize a CD?

---

### Post by jwbrase on 2012-05-11
Search for an application called "Configure Wine" or "winecfg" (I'm not sure exactly what search term will get you to it in Unity because I'm using 10.04 with Gnome 2. You can start it from a terminal with "winecfg". If you're using Gnome fallback mode in 12.04 instead of Unity, you should be able to start it with Applications -> Wine -> Configure Wine).

Anyways, once you've started winecfg, go to the "Drives" tab. There will be a section marked drive mappings, which should look something like this:

```
Letter     Drive Mapping
C:         ../harddiskvolume0
D:         /media/cdrom
Z:         /
```

What drive letters and mappings do you have listed?

Also, more recent versions of X-Plane have native Linux versions. You might want to try the demo for X-Plane 10, and, if it works well on your machine, buy it. (I have the Linux version of X-Plane 9).

---

### Post by djpemberton on 2012-06-01
Sorry for the delayed response. I would like to get X-Plane for Linus. Eventually I will, but my cash is otherwise occupied right now.

Concerning the Drives, here is what it reports:

C:  ../drive_c
Z:  /

seems like there could be something missing there.

---

### Post by nothingspecial on 2012-06-01
*Thread moved to **Wine**.*

---

