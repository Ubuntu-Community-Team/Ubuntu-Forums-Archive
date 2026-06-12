---
title: "Kernel Panic after reboot... getting insane with it!"
date: 2007-09-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by sm!rnas on 2007-09-21
Hi everyone...

Last night i was using my ubuntu desktop (just chatting around in pidgin) when my pc suddenly rebooted due to a thunderstorm nearby.

When i booted it again it hanged on ubuntu loading and keyboard leds started flashing. Tried recovery mode on both kernels and got this kernel panic message:

HARDWARE ERROR
CPU 0: Machine Check Exception: 4 bank 4: b200000000007FOF
TSC 102a60eccd
This is not a software problem.. bla bla bla...mcelog -ascii etc etc
Kernel Panic - not syncing: Machine check

My system is a athlon64 3500+, asus nf4 a8n mobo, kingston ram 4x512, samsung SATA II hard drive.

Ah and btw anytime i try to mount my linux drive on the ubuntu 7 64bit Live/CD (partition in fact...) it hangs and it starts that keyboard LED flashing again. 
Windows starts with no problems.

Any thoughts? I have absolutely no idea about what happened...

Thanks

---

### Post by Jouke74 on 2007-09-21
If you still have the Ubuntu CD, try to boot from that and run the memory test. Maybe the lighting (power surge) has killed a part of your hardware. Normally the memtest will run until you stop it with escape. If it fails to start with a similar error you likely will have a CPU, Mobo problem. If it does run, it should not produce any errors. If it finds errors your memory is damaged, and this is something windows more easily goes by than linux. Furthermore it is possible that your filesystem / disk partition needs a fix, if the rest does seem to run fine.

---

### Post by sm!rnas on 2007-09-21
Ok. Did all of that and there were no erros, memtest+ did all the tests successfully. Anyway, and i forgot to mention, i use a UPS with power surge protection and obviously battery backup also.

So, u think theres a chance i can recover my ubuntu? that would be nice cuz i wont have much time to configure it all over again and i cant seem to mount my linux partition even on a live-cd...:S
Thx

---

