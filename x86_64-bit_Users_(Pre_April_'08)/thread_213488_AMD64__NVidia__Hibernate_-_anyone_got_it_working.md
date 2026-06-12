---
title: "AMD64 / NVidia / Hibernate - anyone got it working"
date: 2006-07-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by bms20 on 2006-07-11
Has anyone got hibernate working on 6.06 x86_64 with NVidia's driver?

Cheers,

  -bms20

---

### Post by fabertawe on 2006-07-11
> **bms20 said:**
> Has anyone got hibernate working on 6.06 x86_64 with NVidia's driver?

Cheers,

  -bms20

Not here... I'm actually more interested in 'suspend'. When I try it I'm unable to wake the machine.

Paul

---

### Post by mkw87 on 2006-07-14
Hibernate works fine with my rig (it goes into and comes out of it fine, and even maintains its overclock which doesnt happen in windows when I put it in standby - dont use hibernate in windows).

It just worked by default, I didn't do anything special =/

---

### Post by toykilla on 2006-07-17
Its not working for me. I cant get the system to turn back one. Have to resort to hard reset.

How can i disable it?

---

### Post by toykilla on 2006-07-19
anyone?

---

### Post by alvenegas on 2006-07-19
This is certanly a problem of a graphics card.  When I had 
Breezy, the suspend button used to work.  I ignore which 
drivers it was using, I suspect "nv" for default nvidia.
However, when I upgraded to Dapper, the graphics card was
using "nv".  After installing Google Earth, i started 
fiddling around with the graphics driver.  I downloaded
the drivers from the nVidia website and also played for 
a while with nvidia-glx and nvidia-glx-legacy.  Google Earth
still ran pretty slow.  Anyway, when I finished installing
the latest nvidia drivers, i put the computer to suspend and 
guess what....it never came back to life. 

I have an Inspiron 8100 with nVidia GeForce 2 Go.

---

### Post by ferox_2 on 2006-07-25
I have the same problem. I report freeze too when using OpenGL applications.
I have installed Ubuntu 64 bit and running nvidia-glx drivers

I´m using an ASUS laptop with Turion 64x2 TL50
RAM 2GB
Video nvidia GeForce 7600


Any suggestions?
Thanks,
   

  Ferox

---

### Post by el_ave on 2007-01-31
Same problem here.
Kubuntu 6.10
Turion 64 X2
GeForce Go 7600 with nvidia driver

It seems to me switching to "nv" should solve the problem, I'll try that later and post my results.

---

### Post by juaka on 2008-01-14
I fixed this in my machine (Ubuntu 7.10 32, nvidia geforce fx5200)

I followed this steps [https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend)
Then restarted x.

Btw, before doing that I installed the package hibernate.
Dontknow if that modified any file or something.

Hibernate works ok.
My Suspend act the same way as Lock screen. dont know if thats correct.

---

