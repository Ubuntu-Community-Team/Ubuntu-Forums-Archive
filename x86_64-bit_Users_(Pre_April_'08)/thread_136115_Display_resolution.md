---
title: "Display resolution"
date: 2006-02-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by ibingaa on 2006-02-25
I'm a Linux newbie so this may sound like a simple question.

My monitor will not support the resolution that has been set up when I installed Ubuntu Breezy Badger,  I can do a ctrl-alt-f1 to get into a text mode.  

My question is which file to I need to modify and how do I do it so that I can reduce my screen resolution so I can see the GUI.

Thanks,

George

---

### Post by heimo on 2006-02-25
[quote=ibingaa]My question is which file to I need to modify and how do I do it so that I can reduce my screen resolution so I can see the GUI.
[/quote]

/etc/X11/xorg.conf

You can edit it directly or reconfigure using dpkg-reconfigure command. See some [instructions here]("http://www.ubuntuforums.org/showthread.php?t=83973").

---

