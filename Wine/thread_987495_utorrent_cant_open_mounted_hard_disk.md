---
title: "utorrent cant open mounted hard disk"
date: 2008-11-19
forum: Wine
---

### Post by da.tiger on 2008-11-19
I am running utorrent on wine and trying to save on a mounted hard disk(windows partition), but I cant see it. Is this a problem related to wine/utorrent? or something else. Please advise on solutions

thanks

---

### Post by magpa on 2008-11-20
> **da.tiger said:**
> I am running utorrent on wine and trying to save on a mounted hard disk(windows partition), but I cant see it. Is this a problem related to wine/utorrent? or something else. Please advise on solutions

thanks

What devices do you have listed in winecfg? Try adding your hdd (browse-> /media/device_name) if you haven't already. 
Might be labeled differently as I'm running Ubuntu in Swedish..

/Magnus

---

### Post by YokoZar on 2008-11-20
It's a little awkward, but you'll find it at Z:\media\disk-3 (or similar)

Z:\ is by default mapped to / on your system, so anything that gets mounted somewhere will be accessible through that.

---

