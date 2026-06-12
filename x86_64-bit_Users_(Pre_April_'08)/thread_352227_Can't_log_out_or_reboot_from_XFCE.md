---
title: "Can't log out or reboot from XFCE"
date: 2007-02-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by mikesf on 2007-02-03
Just installed 64 bit xubuntu 6.1.0 on a toshiba u205 laptop. everything works pretty good EXCEPT i can't
1)kill x server
2)log out
3)reboot 
whether i use the gui or command line. the screen just goes black and then nothing happens (but the computer is still on and the fan revs up). 
my guess is this is an X issue? otherwise i should be able to restart X with ctrl-alt-bkspce
any luck out there?

---

### Post by TheCaptain2000 on 2007-02-03
does your laptop come with an ATI video card? I had the same problem on a desktop, I have updated the video drivers and that solved it. Moreover there was also a problem of at video drivers having a bug in handling DVI plugs, I believe it does not apply to your case tho
Ren

---

### Post by mikesf on 2007-02-03
No on the ATI, it's the Intel 950 graphics. X works great otherwise (e.g. screen resolution was auto-magical).

---

### Post by mikesf on 2007-02-05
well.... i fixed the problem my installing 32 bit ubuntu (not xubuntu). so i don't know if the issue is xfce or 64 bit.

---

### Post by BuffyLinux on 2007-02-16
I seem to be having the same problem with Ubuntu x86-64 (no x) so I don't think its xfce. I've only had a few minutes to play with it, but might try some different xorg.conf settings before I try x86-32.

---

