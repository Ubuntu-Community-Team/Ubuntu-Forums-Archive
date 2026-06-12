---
title: "firewire help needed"
date: 2005-11-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by tr333 on 2005-11-06
what is the device name for the firewire port on apple powerbooks?

i accidentally formatted the ipod HDD as ext3 while using a DamnSmallLinux livecd and now ubuntu and OSX cannot find it, so i thought i might be able to reformat as msdos or similar but i cant find where is is located.

---

### Post by ssam on 2005-11-06
firewire should be sd[a,b,c...] if you run dmesg after plugging it it you should be able to see what device it was asigned.

sam

---

### Post by earobinson on 2005-11-06
I know that there is a SW bug with my firewire and my computer can not use it. This may be the same for you.

---

### Post by tr333 on 2005-11-06
thanks for your help.  i fixed the problem by reformatting the drive from OSX.

---

### Post by earobinson on 2005-11-07
can you expand on this maybe i can get my firewire working

---

### Post by tr333 on 2005-11-07
when i was using DSL to format the ipod, the firewire port was locate at /dev/sda3.  before formatting, i would normally start up ubuntu breezy and then just plug in the ipod into firewire on my powerbook.  the ipod appeared as an ipod icon on the gnome desktop.

---

### Post by earobinson on 2005-11-08
[QUOTE=tr333]thanks for your help.  i fixed the problem by reformatting the drive from OSX.[/QUOTE]
As to fixing the problem, what did you format that made your firewire work? maybe im being slow but im not catching on

---

