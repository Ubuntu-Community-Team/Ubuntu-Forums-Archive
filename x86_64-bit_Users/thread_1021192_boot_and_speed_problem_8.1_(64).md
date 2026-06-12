---
title: "boot and speed problem 8.1 (64)"
date: 2008-12-25
forum: x86 64-bit Users
---

### Post by nagaraj on 2008-12-25
did an online upgrade from 8.04. system got slow and especially boot took a lot of time. even after booting the programmes would take a lot of time to start. now the system has become pathetically slow and getting a boot error "*failed to start x server (your graphical interface). it is likely that it is not set up correctly. would you like to view the x server outputto diagnose the problem?"*. could not make out anything there.starts in low graphics mode. but still the programmes dont start quickly. so far have tried - 'sudo apt-get remove tracker' ; 'sudo apt-get clean' ; 'sudo apt-get autoclean' . what more to do? should i roll back to 8.04?
help will be appreciated. thanks in advance.

---

### Post by namdung on 2008-12-25
I recommend Hardy Heron 8.04.1 because it's LTS. Intrepid has more features than Hardy but more likely to have bugs. Hardy 8.04.2 is coming out in Jan 09. 

However, reboot and Press *Esc Key* to enter Recovery mode. Here fix XOrg server.

---

### Post by Sef on 2008-12-25
What are your system specs?

---

### Post by kristian_k on 2008-12-25
I seem to have the same problem with Ubuntu 8.10 (amd64). The performance is so low it's criminal.
My config:

AMD Athlon64 X2 TK-57
4GB of RAM
ATI X1250

try typing 'top' in terminal to see which process is using up all the CPU. In my case it's Xorg.
Tried updating graphic card driver but I'm either doing it wrong or something else is going bad.
Hope this gets fixed!
Marry X-mas to all !! :)

---

### Post by obsrv on 2008-12-25
This is caused by ATI driver I think. But I might be wrong. Also check if DMA is on like this:

```
hdparm -d /dev/<DRIVE>
```

<DRIVE> should be like sda or sdb or hda or hdb

---

### Post by nagaraj on 2008-12-25
checked top - wineserver is using >85% of cpu. how do i fix it? have some programmes which run on wine. moreover this may not be related to boot problem- i guess. how do i go about? dont really want to roll back because of the better features of 8.1.
my system specs are - amd 64 (3200+), 1gb RAM, swap 1.6gb, (need help to find out other devices and specs)

---

### Post by nagaraj on 2008-12-25
stopped wineserver through 'system monitor' and the system speed improved. still need help to tackle the xorg problem. will try to reboot and try to tackle it in recovery mode as suggested by namdung. thanks
merry x-mas to all.

---

### Post by nagaraj on 2008-12-25
stopped wineserver through 'system monitor' and the system speed improved. still need help to tackle the xorg problem. will try to reboot and try to tackle it in recovery mode as suggested by namdung. thanks
merry x-mas to all.

---

