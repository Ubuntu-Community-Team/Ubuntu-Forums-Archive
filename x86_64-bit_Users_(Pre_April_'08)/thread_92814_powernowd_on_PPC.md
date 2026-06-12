---
title: "powernowd on PPC"
date: 2005-11-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by erez1012 on 2005-11-20
I have an old G3 clamshell ibook (366 MHz). I have it setup with hoary
and it works very nicely, sleeps when I close the lid, and the hard disk
shuts off periodically because I installed laptop-mode. Unfortunately
powernowd does not work so the cpu is always at maximum speed. I found a
bug report on bugzilla that said this was a problem with a kernel option
on PPC.

Has anyone solved this problem with recompiling the kernel, or possibly
is there a backports ppc kernel that fixes it?

Than

---

### Post by Rxke on 2005-11-21
Fellow Clamshell user here, would be interested in a solution to this one too (didn't know it was a bug, thought it was simply not supported)

BTW erez1012, between the lines i seem to read you're looking for power-saving 'tricks'? Here's two, for the HD...

```

sudo hdparm -S 1 /dev/hda
```
(spins down HD, 1= after 5 secs idle, 2=10, 3=15 etc...)

And:

```
sudo hdparm -B 1 /dev/hda
```
(agressive powermanagement, 1,2,3,... 1 being the most agressive..)

I suggest doing a ```

man hdparm
``` if you want more info about hdparm

---

