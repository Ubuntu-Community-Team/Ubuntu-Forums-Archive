---
title: "kde4 sources.list"
date: 2008-09-10
forum: x86 64-bit Users
---

### Post by silfosgnm on 2008-09-10
Hi everybody

I'm with this problem since yesterday.

I format my Dell D630, before yesterday i have ubuntu hardy server for 64bits with kde4 desktop, it was working fine except for my wireless card, i have some friends with hardy server 32bits + gnome and they don't have that problem, even I have a friend with hardy 64bits + gnome with no problems.

So today i want to install kde4.1 and add to my sources.list:

deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main

It's the same address that i use the last time, BUT this time when using aptitude i select kde4 (i don't want to install kubuntu-kde4-desktop, just kde4) and i got 6 errors and the confict library es indi-kde4, WHY?????, I;m not an expert and this is driving me crazy, no wireless, and now i can't install the package that i want.

I'm downloading gutsy server to see if it's version problem, but if any of you has a possible answer, please let me know.

---

### Post by Yellow Pasque on 2008-09-10
What kind of wireless card is it? If you don't know:
```
sudo lshw -C network
```

---

