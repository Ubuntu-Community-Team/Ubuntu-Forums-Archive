---
title: "Ubuntu Problems.."
date: 2005-12-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by ubunick on 2005-12-04
Despite the fact that I'm actually using Ubuntu at the moment, it keeps freezing within the first 10 minutes of use (espeically with launching an application) and I reall y have no idea what's wrong and any idea how to fix it.  Yeah, I'm a total noob with it, I'm really hanging on a limb (accidentally deleted Windows XP).  

Any help would be really appreciated!

And BTW, I know I havn't fixed it in the control panel and which ever, but my aim is "nickp229".  If you could use that it would also be appreciated!

---

### Post by towsonu2003 on 2005-12-04
maybe because of updatedb? try doing this: ```
sudo chmod -x /etc/cron.daily/slocate
```, which will disable autorun of updatedb (a search database which is very very nice for finding stuff in computer real fast, using 'locate filename'). After doing this, you will need to do ```
sudo nice -n 19 updatedb
``` before using slocate... nice -n 19 is to give it a low priority to avoid the freeze:)
If you find that this is not working, do ```
sudo chmod u+x /etc/cron.daily/slocate
``` to enable updatedb again. good luck

---

