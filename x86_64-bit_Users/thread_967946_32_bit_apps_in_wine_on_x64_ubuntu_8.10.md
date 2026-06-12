---
title: "32 bit apps in wine on x64 ubuntu 8.10????"
date: 2008-11-02
forum: x86 64-bit Users
---

### Post by nutpants on 2008-11-02
ok this might seem a silly question..

but some of the 32 apps i ran with wine before will not even install now. (games)
the installer errors out with a runtime error
(at 71:13299)
access violation at address 00000000 write address 00000000
(stalker SOC)

i am dead sure i this worked before.
i tried all the previous versions of wine that i KNOW worked..

 is this normal and do i have to go back to a 32bit ubuntu?

nutz

---

### Post by Kilz on 2008-11-02
> **nutpants said:**
> ok this might seem a silly question..

but some of the 32 apps i ran with wine before will not even install now. (games)
the installer errors out with a runtime error
(at 71:13299)
access violation at address 00000000 write address 00000000
(stalker SOC)

i am dead sure i this worked before.
i tried all the previous versions of wine that i KNOW worked..

 is this normal and do i have to go back to a 32bit ubuntu?

nutz

The wine package in amd64 Ubuntu is the exact same application that is in the 32bit version, its only packaged for 64bit. Wine is 32bit in both versions of Ubuntu, moving to 32bit Ubuntu will not solve the issues, it will only waste a lot of time.
Have you tried looking up the applications in the [Wine application database]("http://appdb.winehq.org/") to see if there is some setup that is needed? Have you tried playonlinux to install and manage wine and windows games?

---

### Post by nutpants on 2008-11-02
the game ( in this case stalker shadow of chernobal) installs fine and plays quite well in wine on 32 bit (and im 90% sure 64 bit) ubuntu hardy 8.04

but i get this error (see above) right after i pick language with my fresh install of x64 8.10 intrepid.

maybe ill download 32 bit intrepid and see if its is intrepid's error or if it is  just the x64 build of wine...

( i still have a computer with hardy x86  that installs the game and i am sure it worked and played on hardy x64 but i just went x64
a month ago so i could be wrong.)

nutz

---

### Post by Artemis3 on 2008-11-02
If it works in 32 bits it works in 64 bits because wine does the same, the problem lies elsewhere...

Update wine using the repository @ winehq
Check the restricted drivers manager, try nvidia's 177 instead of 173.

Check wine configuration. Start with a fresh .wine (eg delete/rename) if needed.

---

### Post by nutpants on 2008-11-02
> **Artemis3 said:**
> 
Update wine using the repository @ winehq
Check the restricted drivers manager, try nvidia's 177 instead of 173.

Check wine configuration. Start with a fresh .wine (eg delete/rename) if needed.

did all that
tried every wine from 1.0 up to the latest
deleted .wine every time

ill install intrepid x86 tomorrow and see if it works
i KNOW it works in hardy x86 
i might even try hardy x64 tonight.

nutz

---

