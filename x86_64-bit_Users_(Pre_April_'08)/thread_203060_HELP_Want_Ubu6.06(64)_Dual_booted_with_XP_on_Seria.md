---
title: "HELP: Want Ubu6.06(64) Dual booted with XP on Serial-Stripped Raid"
date: 2006-06-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by Insanityman358 on 2006-06-24
Is that title enough to take in?

OK so I was over the last week sold on linux by a friend of mine.  I really want to try it out, but am still somewhat sceptical.  here is my problem.

Steps taken:

Made Ubu64 disk
Booted Disk and ran Ubu from disk fine
Clicked install option, runs fine

Problem:

When it asks where i want to install it I cant choose a location that doesnt require a wipe of my drives.  It give me option to install on either of my two drives, but not across both as in raid.

Thanks

---

### Post by JoWilly on 2006-06-25
[quote=Insanityman358]
When it asks where i want to install it I cant choose a location that doesnt require a wipe of my drives.  It give me option to install on either of my two drives, but not across both as in raid.[/quote] 
If you want to install in raid you need to use the alternate install cd.

Are you using  an ide fakeraid (software raid on your motherbord) ? If this is the case, and if the install cd didn't detect your fakeraid, there are many chances that there are no drivers for this on linux (complain to your manufacturer).

In any case, the best is always to install using linux software raid (put your controller in ide mode, not raid). Linux raid has better performance and more features than any fake raid and also more features than many real hardware raids.

You might have a problem if you have windows on the fakeraid. If this is the case you need to chose if you want to reinstall windows on a single partition (not raid), then you can make a linux raid using partitions on the same disks.

---

### Post by RAOF on 2006-06-25
What you want is entirely possible, although perhaps a little involved.  Check out the [FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) on the Ubuntu wiki.  It's **exactly** what you want.

---

