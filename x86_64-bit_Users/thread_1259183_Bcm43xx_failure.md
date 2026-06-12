---
title: "Bcm43xx failure"
date: 2009-09-06
forum: x86 64-bit Users
---

### Post by Darkz_Soul on 2009-09-06
Alright... i have the broadcom 4328 a/b/g/n wireless card.. the drivers from ubuntu doesn't work. i have followed the instructions to the tee from boadcom and ubuntu fourms. and i get an error along the line

~/driv$ sudo make -C /lib/modules/2.6.28-11-generic/build M='pwd'
make: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
scripts/Makefile.build:41: /usr/src/linux-headers-2.6.28-11-generic/pwd/Makefile: No such file or directory
make[1]: *** No rule to make target `/usr/src/linux-headers-2.6.28-11-generic/pwd/Makefile'.  Stop.
make: *** [_module_pwd] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'

no matter what i do i cannot get it to make the wl.ko file.

I am running 64bit 9.04 Ubuntu on a HP dv6663us laptop with a dual core 2.2ghz processor, toshiba 160 sata hdd, nvidia 7 GP7150 series graphics card

---

### Post by Bucky Ball on 2009-09-06
You shouldn't have to do anything like compile or download drivers from a seperate site for that card. They are pretty much covered as of 8.04 (I have one myself). Plug an ethernet cable in and get your updates; it will be picked up and you will be offered restricted drivers for it. Follow your nose from there.

Go to System->Administration->Hardware Drivers

Is there one in the containing B43? If it is unchecked, check it.

---

### Post by Darkz_Soul on 2009-09-06
The restricted drivers from ubuntu doesn't work.. on my computer they work on 32bit version of 9.04 but not my 64bit ver. I'm aware that there is a driver there and I have tried it several times with no success or difference

---

### Post by Bucky Ball on 2009-09-06
Strange because I am running 64bit on my laptop also and the restricted drivers work fine. Hmmm.

But then, I am running 8.04. This could be an anomaly in the current 9.04 which might be fixed in the next update. One never knows.

---

