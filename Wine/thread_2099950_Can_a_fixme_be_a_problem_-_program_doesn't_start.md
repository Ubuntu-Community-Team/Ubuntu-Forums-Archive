---
title: "Can a fixme be a problem? - program doesn't start"
date: 2012-12-31
forum: Wine
---

### Post by Weisskrautbrautkleid on 2012-12-31
Hi,

I'm trying to get a little program run  with wine. I need it to get access to a tipping bucket (measures  rainfall) via USB. The porgramm is called Tinytag Explorer. I got it  installed but it just doesn't want to start. I managed to eradicate all  error and fixme manages so far and now I'm left with only one:

(terminal output)
```
fixme:imm:ImmReleaseContext (0x20034, 0x1f6118): stub
```
Does  anyone have an idea about this or, to be more precise, does anyone can  give me an answer whether this message can be the reason for the program  not to start? Because when I google this in the forum, I always read  posts which say: Don't care for the fixmes, they are just for  developers. Can anyone confirm this in my case? Or is there indeed a  solution for that problem?

Thanks a lot, Weisskrautbrautkleid

Running:
Ubuntu 12.04
Wine 1.4.1 from the Wine-PPA
no other Windows-Software installed
fresh Wine - no changes in config or the registry

---

### Post by dino99 on 2012-12-31
the fixme are warnings, like a todo list for devs, but not errors.

Actually with 1.5.19/20 there is some issue loading apps (meanly games right now, but maybe more)

[https://bugs.launchpad.net/ubuntu/+source/wine/+bug/1094870](https://bugs.launchpad.net/ubuntu/+source/wine/+bug/1094870)

you can vote (affect me too) to get dev attention.

---

