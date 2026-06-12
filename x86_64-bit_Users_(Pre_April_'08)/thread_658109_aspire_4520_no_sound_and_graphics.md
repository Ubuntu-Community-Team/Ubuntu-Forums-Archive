---
title: "aspire 4520 no sound and graphics"
date: 2008-01-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by s.jesudasan on 2008-01-04
hi

im running aspire 4520

AMD Athlon 64 X2 Processor - TK-55 (1.8GHz, 512kB L2 Cache combined) 
Nvidia nForce 610M chipset 
Nvidia GeForce 7000M onboard graphics capable of up to 256MB VRAM (shared) 
1GB DDR2 667MHz RAM (512MBx2) 
160GB 5400RPM 2.5-inch SATA HDD 
8x DVD Burner with Dual Layer Support 
14.1-inch WideScreen Acer CrystalBrite LCD (glossy display) capable of 1280×800 resolution 

i installed ubuntu 6.06 64bit in safe mode 
and after i boot into desktop 
there is no sound
and my nvidia onboard graphics is not working
there is no 3d effects
so can anyone please help me
im a die hard fan of ubuntu
so i dont want to use any other distro 
please help me

---

### Post by Yellow Pasque on 2008-01-04
Have you installed the nvidia proprietary drivers by going to System -> Administration -> Restricted Driver Manager? If so, what does your /etc/X11/xorg.conf file look like?

For the sound, I would recommend trying the OSSv4 link in my signature.

---

### Post by s.jesudasan on 2008-01-04
im not sure which restricted driver i should use can you guide me with that. thank you for ur reply

---

### Post by Yellow Pasque on 2008-01-04
A lot of people seem to like the automated Envy install: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by s.jesudasan on 2008-01-04
when i try to use envy 
i get the message:
no specific driver found

---

