---
title: "need help with diagnosing slow start up gdm"
date: 2007-06-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by bugler on 2007-06-07
I'm getting a slow start up after login.  Everything works after gnome-panel and desktop comes up.  The slow startup is about 1 minute.  This just started and i can't figure out what program is causing this.

How can I diagnose this problem?  Is there a msconfig program?  What logs do I look in?  What can I copy here to give you the information to help you help me?

First time Ubuntu user for the last 6 months or so... exclusively linux and windows free for 6 months.

Thanks so much in advance for this awesome community.

Bugler

Edited:  ISSUE RESOLVED.  I was running by some threads on ifconfig and was trying some different things and screwed my /etc/network/interfaces file.  I commented out everything except auto eth0 and auto lo.  All worked well after that.  I Love Ubuntu and Linux\\:D/

---

### Post by incubus on 2007-06-08
bugler,

Good job and nice touch on updating with your solution.  Few people do that.

Best,

incubus

---

