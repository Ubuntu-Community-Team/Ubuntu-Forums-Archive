---
title: "Help configuring an AGP x800xt AIW in Dapper Drake"
date: 2006-09-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by Over1ord on 2006-09-30
Alright, first off let me preface my first post by saying I am a total n00b to linux but I was a huge fan of DOS back in the day so I figured I would try .  So after a few failed attempts at installing Fedore Core I installed Ubuntu 6.06 with no problems and all the useful threads on this site have helped dearly aswell, but I cant figure out how to set up my 256MB AGP x800xt All in Wonder in Dapper Drake, I have decent graphics and 1600x1200 resolution but some of the screensavers seem really slow and some arent even displaying properly.  Any suggestions where to start out in fixing it?  And a side question, how can I back up my xorg.conf file so that if I mess it up and ubuntu wont start I dont have to reinstall it to fix it?

---

### Post by Kilz on 2006-09-30
> **Over1ord said:**
> Alright, first off let me preface my first post by saying I am a total n00b to linux but I was a huge fan of DOS back in the day so I figured I would try .  So after a few failed attempts at installing Fedore Core I installed Ubuntu 6.06 with no problems and all the useful threads on this site have helped dearly aswell, but I cant figure out how to set up my 256MB AGP x800xt All in Wonder in Dapper Drake, I have decent graphics and 1600x1200 resolution but some of the screensavers seem really slow and some arent even displaying properly.  Any suggestions where to start out in fixing it?  And a side question, how can I back up my xorg.conf file so that if I mess it up and ubuntu wont start I dont have to reinstall it to fix it?

What version of the drivers are you using? The ones in the repos or the ones in from ATI. If you want to back it up. Just click on Places > Filesystem. Then navigate to /etc/X11 right click copy on xorg.conf, then right click paste on the desktop. You then have a backup. You could also open a terminal and enter ```
cp /etc/X11/xorg.conf xorg.conf
``` and it will copy into your home folder.

---

### Post by Over1ord on 2006-09-30
I dont know what drivers I am using, the default ones after running the configuratino script where you walk through it step by step.  It sets it up as "ati" in my xorg.conf file but alot of the threads I have read say to change it from "ati" to "vesa" should I try that?  Or do I just need to go download some drivers for it, I dunno?

---

