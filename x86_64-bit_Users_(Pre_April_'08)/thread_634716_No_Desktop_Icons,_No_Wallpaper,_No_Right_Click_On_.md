---
title: "No Desktop Icons, No Wallpaper, No Right Click On Desktop After Upgrade"
date: 2007-12-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by ugly_b on 2007-12-08
I've had this problem recently.  It happened after I did a 'apt-get upgrade' and rebooted.  The desktop then came up without my wallpaper, no desktop icons, and I was unable to right-click on the desktop.

I see some other people have this same problem, but their scenario is different than mine so I started this new thread.

After trying many suggestions from different posts, which didn't work, here's how I fixed mine.

First, I went to System | Preferences | Appearance.  When the dialog opened up, my wallpaper magically came back to my desktop.  Then I clicked on the Visual Effects tab and changed mine from Extra to None and closed the dialog box.

Then I went to System | Preferences | Sessions and clicked on the Session Options tab.  Uncheck the "Automatically remember..." checkbox and close the dialog box.

After a reboot, everything was back to normal.  My icons were back on my desktop, along with my wallpaper, and right-click ability.

Then I went back to Session Options and re-enabled "Automatically remember...".  Rebooted, and everything's still good.

So I guess the Session state was the real problem with whatever packages I updated which introduced the problem.

I hope this helps someone!

[www.WheresMyStar.com](www.WheresMyStar.com)

---

### Post by zidty on 2007-12-08
this stuff happnd to me too a few times .. but when i chkd by using system monitor then i saw that nautilus was hanging .. then i killed the nautilus using kill process and it became ok .. icons back wallpaper back and fav rt click too :D never happend after upgrade ..

---

