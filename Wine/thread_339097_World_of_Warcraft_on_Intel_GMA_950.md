---
title: "World of Warcraft on Intel GMA 950?"
date: 2007-01-15
forum: Wine
---

### Post by Spif on 2007-01-15
I was wondering if anyone has tried running WoW with on a laptop with an Intel GMA 950 graphics card. It should work well on XP, but I am not sure the Linux drivers are as good for the GMA 950.

Anyone have any experiences with this?

---

### Post by iMav on 2007-02-25
> **Spif said:**
> I was wondering if anyone has tried running WoW with on a laptop with an Intel GMA 950 graphics card. It should work well on XP, but I am not sure the Linux drivers are as good for the GMA 950.

Anyone have any experiences with this?
I am wondering this as well.  WoW runs respectably on my MacBook with the same video.

---

### Post by R4D10Active on 2007-12-04
I am on a Toshiba Satellite A135-S4527 which uses the Intel GMA 950 I just recently was able to install WoW successfully under Ubuntu 7.10 with the latest release of wine.  I am pretty sure that I messed something up during the install because the graphics are crap.  I am a complete linux noob even though I have used it for school.  If anyone could help me out I would greatly appreciate it.  I have been through the [WoW: How To]("https://help.ubuntu.com/community/WorldofWarcraft") and the Troubleshooting section at the same.

Cheers

R4D10Active

---

### Post by R4D10Active on 2007-12-04
Bump for the night.

---

### Post by Espionage724 on 2008-02-13
I would use Cedega if possible to install WoW....right now I am in the process of even trying to get it to work though....

---

### Post by pedro_orange on 2008-02-13
Try running:

```
glxinfo | grep rendering
```

If you get an output similar to: "direct rendering: Yes" you should be ok in the graphics department. This does not take into account CPU/Memory etc.

I have problems running WoW with an Intel Extreme, with jerky graphics etc. (This is after all the reg/conf tweaks) Works much better on my desktop with an 8800GTS and 4GB Ram :D

If you haven't checked out: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)
You should now.

GL

---

