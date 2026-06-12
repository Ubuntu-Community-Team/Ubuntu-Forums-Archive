---
title: "Wine slow in 11.10"
date: 2011-10-18
forum: Wine
---

### Post by ramshot on 2011-10-18
Greetings,

I recently upgraded to Ubuntu 11.10. Apart from me having to switch to XFCE because I severely dislike Unity/Gnome 3 for productive work, all is well, except for one thing. I use a little known program called LAMP that allows me to chat on the site shacknews.com without using a browser. It's a windows only app, but has worked fine under Wine... until now. It still starts up and "works", but it's very, very slow. Scrolling is laggy and stutters, text I type shows up with a severe delay and the whole window freezes for a couple of seconds randomly.

I've reinstalled both wine and the app but it doesn't help. The problem remains across all 3 window managers, meaning Unity, Gnome 3 and XFCE.

Has the wine version been changed from 11.04? If so, is there a way I can revert to the older version without having to compile it myself? Or could there be another reason for the poor performance?

Thank you!

---

### Post by howefield on 2011-10-18
Thread moved to the "Wine" forum.

---

### Post by ergo-proxy on 2011-10-19
The wine dev version changes biweekly, so you can use the latests stable (1.2.3) or the latest dev version, try both. If it doesnt work for you can will have to compile a different version for yourself (very easy).

---

### Post by ramshot on 2011-10-20
Fixed by downgrading to 1.2.3. Thank you.

---

