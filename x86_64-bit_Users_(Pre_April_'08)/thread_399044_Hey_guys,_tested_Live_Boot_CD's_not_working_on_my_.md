---
title: "Hey guys, tested Live Boot CD's not working on my computer, help please"
date: 2007-04-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by ramb0w on 2007-04-01
First: my computer
DFI Lanparty 939
1 stick 1gb pc3200 @ 408
64 3000+ 1.8@2.4
7800gt

I burnt a copy of ubuntu 6.10 64bit to install, it booted fine until right before the desktop boots up (music plays, see mouse, can move mouse, get really distorted window on desktop, and nothing more loads up on the desktop)

test cd, reburn, same problem, test on friends core2duo, works fine no problems

so i figured I'd try ubuntu 32bit

it gets to the same spot and gives the same error, but runs fine on a PII 600mhz dell

any ideas as to what could be wrong?

---

### Post by John Jason Jordan on 2007-04-01
> **ramb0w said:**
> ... any ideas as to what could be wrong?
The live/install CDs have various boot options. Try some of them. In particular, try safe mode. Safe mode takes you to a command line instead of starting the GUI. If you can get to a command line, enter "dmesg | less." This will give you a list of everything that happened during the boot. Spacebar advances one page at a time; when you get to the end PgUp and PgDn move you up and down in the text. Read through it looking for suspicious stuff.

---

### Post by ramb0w on 2007-04-01
ok ill be back in a min

---

### Post by Jouke74 on 2007-04-02
I think your videocard and or monitor are not recognized correctly by Ubuntu. As a consequence your graphical interface goes haywire. To resolve this, try to boot using the safe-vga mode. If you are going to install Ubuntu this issue will also come up. In that case you can use the same option, or the text-based installer. Afterwards it is going to be a bit nasty to get your xorg.conf file in the right way. Some other people need to help with that.

---

### Post by ramb0w on 2007-04-02
I did not have time to do much last night, but i did try and boot in safe vga mode, the problem that i've been getting is the same for both 32 and 64bit at the same spot, safe vga or not.

---

