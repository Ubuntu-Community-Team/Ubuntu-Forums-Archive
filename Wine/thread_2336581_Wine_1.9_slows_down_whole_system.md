---
title: "Wine 1.9 slows down whole system"
date: 2016-09-09
forum: Wine
---

### Post by izznogooood on 2016-09-09
My ISP is providing an app kind of like Dropbox serving as free backup. I does not support linux so i run the client in Wine. The problem is when its in "active" state it seems to slow down my whole system. When I look at the CPU usage its not a whole lot, maybe 5-15%. But the problem i see is that wine is using all CPU's.... Or at least I think that is the problem, as i cant find any other hints....

This should be a low resource app.

Any ideas? Maybe there's a way to limit the number of CPU's for wine. Or another way to find out whats slowing down everything because i cant see anything in glances...
(1.9 is a wine development version, and it might be worth downgrading but i want to know if there's a fix)

I have an I7 with 16GB of ram so hardware should not be an issue (All HW are on proprietary drivers.)

EDIT: It also has trouble with large files... (Ressulting in handsake errors...).

Could the win 7 option be buggy?

---

### Post by deadflowr on 2016-09-09
> @moderator, wine is not technically virtualization 
You're right, it's not.
*Thread moved to **Wine**.*

---

### Post by tadrazen on 2016-09-14
hi i also experience it with my first download and some of my friend told me to uninstall and install it again then reboot my computer and now it is working properly

---

### Post by izznogooood on 2016-09-17
I've tried to reinstall, i've tried defferent distros and different versions of wine. I've had better luck with wine 1,8 when it comes to slowing down the system.

BUT: It still has problems transfering large files.

---

