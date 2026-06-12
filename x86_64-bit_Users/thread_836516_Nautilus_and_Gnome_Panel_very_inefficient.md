---
title: "Nautilus and Gnome Panel very inefficient"
date: 2008-06-21
forum: x86 64-bit Users
---

### Post by Amurko on 2008-06-21
I first started running Ubuntu 64-bit when I got my Core 2 2.4Ghz system over a year ago running Edgy.  It was quite fast even after I finished installing much of the software I needed in my first month.  I haven't significantly added new software since then but have always upgraded to the latest distributions and gotten the latest patches from the update manager.

After every new upgrade, my comp seems to be running slower and slower (and I'm not even using Kubuntu.)  It's gotten to the point where nautilus is even slower running on that system compared to my Celeron 2.8Ghz from over 3 years ago (running Hardy 32-bit.)  I checked the system monitor and it seems that Nautilus and Gnome-panel always seem to be hogging a huge amount of memory (100MB - 300MB each!.)

I tried killing and restarting Nautilus and Gnome Panel but they resort to their memory hogging behavior again after 1-2 hours again.  I've even tried compiling both from source using apt-build to no avail.  Are there any separate libraries that these two programs depend on which I can try compiling from source using apt-build to hopefully alleviate the abnormal memory hogging behavior?  What else should I try next short of reinstalling?

---

### Post by cariboo on 2008-06-22
I checked the system nonitor for nautilus and gnome panel. Nautilus is using 115MB and Gnome-panel is using 26.3MB. If you're using compiz with lots of effects things will run slower. If gnome-panel is using 100-300MB you seem to have a problem. See attached picture.

---

### Post by Major_Kong on 2008-06-22
Are you using any special theme ? 

PS: You could change to thunar. [http://thunar.xfce.org/index.html](http://thunar.xfce.org/index.html)
There are guides on this in the forum.

---

