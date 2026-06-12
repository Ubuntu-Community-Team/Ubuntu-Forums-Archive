---
title: "QuodLibet Plugins Problem?"
date: 2006-05-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by TDave on 2006-05-31
So, here's the problem

I ran QuodLibet on my PowerBookG4 on 5.10 quite comfortably for a long time with a whole bunch of plugins installed. No problem.

For whatever reason (mainly boredom) I wanted to try out using the selections.txt backup idea and did a complete reinstall of my hard drive, sticking with 5.10 for now (eagerly awaiting dapper...) and dist-upgrade went fine. Everythings still there and nearly everything works.

Before the reinstall I backed up all my main additional pieces (wallpapers, gdm themes, icons etc - read: shiny stuff) and popped them back in. Unsurprisingly no problems.

However, when it came to QuodLibet I puyt the plugins folder back in the same place, exactly as before and per the instructions on the site (in /home/~/.quodlibet/plugins ) and started it back up. I opened up the plugins window to turn my regularly used ones back on and... nothing.

Ok, no worries, maybe I missed something... nope all is good. Maybe the install is buggy. I ran a full remove and reinstall and repeated the process - still a no go.

Is this a PPC specific problem? Is it a version issue? Anyone else experiencing the same thing?

I'm sure I must be missing something really obvious, or maybe something that'll be fixed in 6.06 but it just struck me as odd.

Equally, the mysql problem I've seen mentioned a few times still persists. x86 mysql install works no problem, seems like the PPC version now needs a workaround.
( [http://ubuntuforums.org/showthread.php?t=140036&goto=newpost](http://ubuntuforums.org/showthread.php?t=140036&goto=newpost) )

Any reccommendations appreciated

---

### Post by dimebar on 2006-05-31
hi - just wondering if you had tried the quodlibet-plugins package via apt - most of the useful ones are in there.

---

### Post by TDave on 2006-05-31
Now that you mention it it rings a bell. I have installed it before, don't honestly know whether it included in selections though. It should have done. Certainly on the reinstall I didn't do it.

Will try now and edit if it works...

EDIT: No joy...

---

### Post by hugmenot on 2006-06-01
Let&#8217;s guess: You dropped the plugins into your ~/.quodlibet/plugins folder earlier (while using 5.10). Now on Dapper you have a new QL version which is not backwards compatible to the old plugins.
Your only choice is to either remove them from your personal dir and install the plugins package /or/ remove them and redownload them one by one from the QL page (they were all(?) updated).

Be aware that they are subcategorized and have to go into respective sub-dirs.

Right? Right.

---

