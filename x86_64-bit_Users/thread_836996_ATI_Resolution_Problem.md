---
title: "ATI Resolution Problem"
date: 2008-06-22
forum: x86 64-bit Users
---

### Post by psayeed on 2008-06-22
Found a solution here: [http://ubuntuforums.org/showthread.php?t=834824&highlight=Sreen+Resolution]("http://ubuntuforums.org/showthread.php?t=834824&highlight=Sreen+Resolution") 

**The key, however, was changing the "defaultDepth" from 24 to 16 in /etc/X11/xorg.conf**


Original Post:
=====================================================================
I have just installed the OS. Initially I was getting all options for my Screen Resolution and up to 1600X1200.

Then I upgraded the Ubuntu Version 7.x to 8.x via "Update Manager". From that point on I only get resolution options up to 1280X1024.

The modes line in xorg.conf looks right:

Modes           "1920x1200" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"

Any ideas?

Thanks.

---

