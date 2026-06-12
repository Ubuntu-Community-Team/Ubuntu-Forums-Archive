---
title: "[SOLVED] sound gone"
date: 2008-07-23
forum: x86 64-bit Users
---

### Post by LoneWolfJack on 2008-07-23
Ok, I "finally" have this issue, too... this seems to be quite a weak spot in linux/ubuntu.

bottom line, for reasons that I think are not important, I just had to reboot my machine three times. all clean reboots, no hitting the reset button or something like that. now finally my sound is gone.

I didn't install or delete anything.

there are like a zillion threads about the sound suddenly not working, but none of the fixes worked for me.

where would I go to check whats going on?

/edit
oh, and I'm using gutsy

---

### Post by mamut0o1 on 2008-07-23
Have you tried this command:
chmod 666 /dev/snd/*
that took care of my sound problem.

---

### Post by LoneWolfJack on 2008-07-23
thanks, but all files are 666

any other ideas?

---

### Post by Thelasko on 2008-07-23
Open up the system monitor.  Do you see anything strange?

When I had this problem the only thing that fixed it was an upgrade to Hardy.  Hardy is much better than Gusty, but I kinda wish I didn't have to resort to that.  Hope you have better luck.

---

### Post by LoneWolfJack on 2008-07-23
short of nautilus and gnome using 17 billion GB of RAM, there's nothing I would consider fishy...

I tried hardy on a new machine I bought but it turned out to be quite unstable. I guess it could work on this machine but currently I'm not taking chances.

so, basically, I'm still looking for help...

---

### Post by LoneWolfJack on 2008-07-23
um, ok, it just started working again... no idea what I did to fix it... my best guess is that clicking one of the "test" buttons under preferences->sound somehow fixed the issue...

---

### Post by Thelasko on 2008-07-24
I'm glad your sound started working again.  It's too bad you couldn't figure out why.

I just recently found out that people on new machines are having trouble with Gusty.  My machine is a year old and I found everything to "just work."  Sounds like more cooperation with hardware vendors is needed.

---

