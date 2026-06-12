---
title: "some gutsy 64 &quot;problems&quot;"
date: 2007-11-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by svtfmook on 2007-11-14
a couple of things i have run into, wondering if anyone else has run into these problems.

i installed gutsy amd64 last night, i didn't get a whole lot of time to tinker, but here is what i ran into:
k9copy
seems to be slower on gutsy than feisty

i cannot get avant window manager installed, not through the deb, not through svn.

i cannot add the tuxfamily.org repo

under hard info, none of the detailed specifications are in the fields.  am i supposed to install drivers for the processor, etc?

---

### Post by kuja on 2007-11-14
With regards to k9copy, one thing you could do is run "time k9copy" (in a shell) and see if it indeed does take longer (it'll give you a solid number)

---

### Post by svtfmook on 2007-11-15
well, i was able to get awn working.  i was also able to configure lm-sensors and nvclock.  got conky going, emerald, pretty much everything in the effects department.

now the only issues i have are:
gparted doesn't open
sometimes when i click the "quit" button, the system hangs
sometimes when i boot, i get the black screen, ctr-alt-backspace then relogging in fixes this.

---

### Post by Inxsible on 2007-11-15
you need to build AWN from source since a 64 bit version is not available. I see that you have already sorted that out.

Have you installed GParted? It is not installed by default. Where are you trying to open it ?

---

### Post by svtfmook on 2007-11-15
i actually got awn working from a deb package from cvs.

nvclock took a lot of configuring to get it to work right.  but fortunately, nvclock isn't a necessary tool that the average user would need.

i installed gparted using synpatic.  it worked before, but now it's not working.  i'm trying to run it from the admin menu.  i have 2 other drives that i'd like to adjust the partition on.  but when i open gparted, the window comes up, and it just runs (status bar going back and forth) like it's searching for the devices.  maybe i'll remove it and reinstall it.

tomorrow/this weekend i'm going to venture into vmware and trying to get that running.

---

### Post by Inxsible on 2007-11-15
> **svtfmook said:**
> i actually got awn working from a deb package from cvs.

nvclock took a lot of configuring to get it to work right.  but fortunately, nvclock isn't a necessary tool that the average user would need.

i installed gparted using synpatic.  it worked before, but now it's not working.  i'm trying to run it from the admin menu.  i have 2 other drives that i'd like to adjust the partition on.  but when i open gparted, the window comes up, and it just runs (status bar going back and forth) like it's searching for the devices.  maybe i'll remove it and reinstall it.

tomorrow/this weekend i'm going to venture into vmware and trying to get that running.Best bet would be to use GParted from the Live CD. the drives are not mounted that way, and you can easily modify the partition tables.

---

