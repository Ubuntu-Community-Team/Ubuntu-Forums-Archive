---
title: "Ubuntu 14.04 English + Playonlinux 4.2.2 + MS Office 2007 ... characters problem"
date: 2014-04-30
forum: Wine
---

### Post by michal-urban on 2014-04-30
Hi,

Im on english Ubuntu 14.04 x86_64 with Playonlinux 4.2.2. Im trying to run MS Office 2007 (hybrid, legal license). MS Office 2007 installs and activates fine. Then I add SP3 update, FileFormats update and PDF support with no problems. I also add MS Fonts (using the Playonlinux menu). Everything works as good as on english 12.04, except for one thing.

My problem is with writing diacritics. Im Czech, but with english system language but Ive got no problems with writing diacritical characters like "&#283;š&#269;&#345;žýáíé" nowhere in the system. Those characters can be written in two ways - either I use one of the respective keys (those which on english layout write "234567890") or I can write first the sign and then the letter (like &#711; + s = š). The problem Im dealing with is that when I use the second way nothing gets written - the cursor even dont move. Its like the keyboard letters are not transferred correctly to the MS Office programs.

Im using latest Wine 1.7.17 (installed through Playonlinux just to this MS Office installation in Playonlinux). 

Also, I need to start either the Office program or Playonlinux itself with LANG=cs_CZ.utf8, the czech encoding ... if I dont do this, MS Office options tell me that my czech language support is limited (whatever that means) ...

Only change here is when I use the default Wine in Playonlinux which is 1.2.3 ... in that case writing š&#269;&#357; in the second way (like &#711; + s = š) leads in "box, box, e" ...

I really dont know what to do. I dont want to reinstall my freshly configured system and Im also not sure if it would help ...

---

### Post by michal-urban on 2014-04-30
[http://forum.winehq.org/viewtopic.php?f=8&t=20133](http://forum.winehq.org/viewtopic.php?f=8&t=20133)
"I changed an option of the "Language Support" dialog of Ubuntu: In "Keyboard input method system" I selected "none" instead of "IBus" and restarted the system. "

---

