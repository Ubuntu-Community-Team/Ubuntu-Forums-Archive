---
title: "Startup Problem"
date: 2008-05-04
forum: x86 64-bit Users
---

### Post by Joe of loath on 2008-05-04
hi;

i decided to rebuild my pc, since XP was playing its usual 18 month old registry tricks (the performance always seems to drop after that long doesn't it?).

anyway, i installed 8.04 first. installation went fine. i went to start it up, and the progress bar froze 3/4 of the way along. so i restarted in the failsafe mode, and it got to the 'hardware extraction layer HALD' section, and; froze. the cursor was flashing, but an hour later it was stll flashing.

any idea on whats wrong? my only thought is that i'm running a 32 bit version on an AMD 64, but many other people are doing that too.

thanks for your help
Joe

p.s. sorry for any bad spelling or poor grammar, i'm typing cross legged on the living room floor with my ( working ubuntu) media centre. its not the most ergonomic position...

---

### Post by Joe of loath on 2008-05-04
ok, now its stuck on 'Gnome display manager'

still clueless...

---

### Post by Kilz on 2008-05-04
The 32bit version is not specificly designed for 64bit hardware. While it works a lot of the time there are instances when it doesnt. Why not try the 64bit version to see if it works for you?

---

### Post by Joe of loath on 2008-05-04
i wish i could. with windows went my CD burning capabilities. although, i have got a 64 bit version of 6.06. i guess i can upgrade once i get everything sorted, if it works?

---

### Post by Joe of loath on 2008-05-04
ok, this is the situation:

clean install on minimum hardware, i'm completing the boot process, but as the GUI starts the pc freezes. the light on the floppy is on for some reason. theres nothing on the screen, i thought it was something to do with my graphics card, so i stuck in my old radeon 7000, and still nothing. i think its my motherboard. in which case, i'm stuffed. i might try some different distributions of linux though.

---

### Post by Joe of loath on 2008-05-04
fixed :) i just added ACPI=OFF to the boot command in grub, and it works now :D

---

