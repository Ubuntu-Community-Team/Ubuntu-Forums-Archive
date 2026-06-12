---
title: "Fan Stays on Full Speed"
date: 2009-05-11
forum: x86 64-bit Users
---

### Post by swatto on 2009-05-11
Hello all,

It has been quite a while since I last posted on here but I have a bit of a problem.  I have just installed the 64-bit version of the latest distro.  Everything seems to work fine however the fan stays on at full speed and doesn't turn off (once the computer has booted to an os it normally turns off) and it is quite loud.  Please does anyone have an idea as to what may be causing this?

Cheers for any advice/guidance :P

---

### Post by swatto on 2009-05-11
Hmm, after further research I think it is my graphics card fan that is staying on full speed.  Im trying to install some drivers for it but it is a .run file and i do the sudo sh blabla.run and nothing happens?  My graphics card is a Nvidia 9600GT.

Please can someone help me :(

---

### Post by ShadowTek on 2009-05-11
Yes, I also have a 9600 GT, and the fan *will *run at full speed unless the proper drivers are installed.

I did a clean install of Ubuntu 9.04 AMD64, and the open-source drivers successfully moderated the fan speed. I'm using the proprietary drivers now, and the fan's performance is also properly moderated.

I also noticed that this 9600 GT's fan was running at full speed when I booted Windows XP, which did not have any nVidia drivers at that point. Once I installed their drivers, the fan speed was properly moderated.

---

### Post by swatto on 2009-05-12
> **ShadowTek said:**
> Yes, I also have a 9600 GT, and the fan *will *run at full speed unless the proper drivers are installed.

I did a clean install of Ubuntu 9.04 AMD64, and the open-source drivers successfully moderated the fan speed. I'm using the proprietary drivers now, and the fan's performance is also properly moderated.

I also noticed that this 9600 GT's fan was running at full speed when I booted Windows XP, which did not have any nVidia drivers at that point. Once I installed their drivers, the fan speed was properly moderated.


Hello ShadowTek,

Thankyou for your reply :) I have managed to successfully install the nVIDIA drivers and it has moderated the fan speed.  I had to stop X running first (which I didn't realise)

---

### Post by mirak63 on 2009-05-13
I bought a 9600gt and the fan runs at fullspeed no matter what, on linux and windows

I returned it and they say it's working fine, I can't see how it's possible, I tried on two totally different computers.

---

### Post by swatto on 2009-05-13
Have you tried installing the latest proprietary drivers?

---

### Post by ShadowTek on 2009-05-13
> I bought a 9600gt and the fan runs at fullspeed no matter what, on linux and windows

I returned it and they say it's working fine, I can't see how it's possible, I tried on two totally different computers.     Did you plug the monitor into the video card and disable the onboard graphics in BIOS?

---

### Post by mirak63 on 2009-05-14
> **swatto said:**
> Have you tried installing the latest proprietary drivers?


yes, on linux and windows

> **ShadowTek said:**
> Did you plug the monitor into the video card and disable the onboard graphics in BIOS?

the bios was set so that onboard graphic card disable itself when a peg is plugued.
so yes. in dvi/hdmi
and I tried on another motherboard without onboard graphics with vga


now since I returned the card they said the card is working perfectly, however I don't believe them. I don't see what's wrong on my configuration to have such a result.

I tried on a 330 watts psu and a 380watts, both antec, that's the only thing that might be responsasible for this.
Also the fan plug have 4 pins, though only two are wired to the fan, a red and a white.

If there is still no regulation I will return it again.
My problem is that powermizer settings in xorg have no effect, and on windows it's the same.
I mean if they just flashed the bios just to have it on economic always I will notice it for sure.

---

