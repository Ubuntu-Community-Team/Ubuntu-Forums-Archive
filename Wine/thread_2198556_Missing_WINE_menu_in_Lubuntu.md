---
title: "Missing WINE menu in Lubuntu?"
date: 2014-01-09
forum: Wine
---

### Post by zer010 on 2014-01-09
I've had this issue several times after installing WINE in Lubuntu.  The latest issue was in 13.04.  I haven't upgraded to 13.10 yet so I don't know if the issue was resolved.  
Likewise, I haven't really used any of the other *buntu variants as of late so I can't comment on their status with the WINE menu.  Hopefully, this will help some trying to get the WINE category to show up in the LXDE panel menu (launcher). 

 It's quite simple really. You can find the WINE .desktop files in /usr/share/applications. Just copy those to ~/.local/share/applications and reboot.  If the directory doesn't exist, create it.  This should put the WINE category and it's components in the LXDE panel menu (launcher).

Hope this helps someone as it took me a while to figure it out.  It seems that the thread I posted my findings in has been closed, but that doesn't mean it's forgotten! ~_^d

---

