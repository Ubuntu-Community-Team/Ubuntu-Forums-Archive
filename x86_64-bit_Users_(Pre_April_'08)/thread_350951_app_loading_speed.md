---
title: "app loading speed"
date: 2007-02-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by cgons on 2007-02-01
not sure if this is the right place to post this but i am sporting an amd64x2 so i thought here would be a good place to start.

when i try to run a program whether from the menu or the CL it literally takes a good 10 seconds before anything happens....i say "anything" because sometimes after all that it doesn't even open... this happens with all installed apps 32 bit, 64 bit, kde apps, i have tried to spped up this process or atleast determine why this is, but i haven't had any luck.....any ideas????

i understand some of the kde apps will be buggy in gnome, ktorrent, amarok, although the latter is pretty stable. this is beyond buggy.  this is like having 128 mem trying to run vista...

ohyeah 
amd64 x2-tl56
ati radeon express
edgy x86 desktop install
1G ram / 2G swap
80G hdd

---

### Post by kuja on 2007-02-01
You've got plenty of memory, so that certainly isn't the problem. That's unusually slow though, perhaps you'll find a clue as to what's going wrong in your /var/log/messages file.

---

### Post by cgons on 2007-02-01
ok,, i'll check that and post back......i was thinking it might  be the ndiswrapper plugin??does it fully support 64bit framework????i don't know let me see what i can find..

---

### Post by cgons on 2007-02-01
this is what some other members did and helped them but i tried this already

[http://www.ubuntuforums.org/showthread.php?t=297092&page=6](http://www.ubuntuforums.org/showthread.php?t=297092&page=6)

on my original Desktop install i had to add "acpi=force irqpoll" to reconize my HDD.. i then altered it to "noapic nolapic irqpoll" both give me among other errors

```
unexpected IRQ trap at vector 30 
```

---

