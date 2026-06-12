---
title: "pismo dual battery"
date: 2005-12-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by shawn12345 on 2005-12-31
Hello, I'm running gnome ubuntu on a powerbook pismo. I have two batteries. My questions are regarding the battery icon and activation of the 2nd battery. in general does the time displayed take into account the two batteries or only one? (i haven't ran it dead to test it...the battery last quite a long time.) I assume that the 2nd battery is OS independent  (in otherwords ubuntu wont short my runtime assuming i only have 1 battery correct?...i would imagine thats all hardware regardless of OS.

I'm showing upwards of 8 hours =) ...not sure if the 2nd battery is fully charged yet.

thanks for any help.

-shawn

---

### Post by shawn12345 on 2005-12-31
I answered my own question...

Both batteries do get recognized by linux. Guess i'll just have to run it and see how long they last. If you'll notice time rem is 0 for one battery  but maybe it kicks in when the other goes dead and no idea if the battery applets sum the two batteries for time in thier calculations.

pismo:~/Desktop/notes$ ls /proc/pmu/
battery_0  battery_1  info  interrupts  options
pismo:~/Desktop/notes$ cat /proc/pmu/*

flags      : 00000011
charge     : 4567
max_charge : 4568
current    : 0
voltage    : 12490
time rem.  : 0

flags      : 00000011
charge     : 4201
max_charge : 4210
current    : -676
voltage    : 12203
time rem.  : 22372
PMU driver version     : 2
PMU firmware version   : 0c
AC Power               : 0
Battery count          : 2

---

