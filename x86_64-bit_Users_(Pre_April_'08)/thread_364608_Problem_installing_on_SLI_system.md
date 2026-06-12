---
title: "Problem installing on SLI system"
date: 2007-02-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by Phil_McCrackin on 2007-02-18
I have previously installed Dapper 32 bit on my system with no problems. 
I recently completely wiped my system to straighten things and want to install 6.10 64bit. I get the install selection screen and have tried selecting install and install in safe graphics mode both with the same result. 

The system loads and I can hear the audio, but I lose the video. I end up with a still cursor in the upper-left corner and cannot see the install screen. 

NOTE: on previous installations (after install) I would run into the same problem in which case I logged into restore and manually added my second GPU that was not seen...problem solved.
Also, this system was installed in text mode which I do not see as an option in 6.10


However, pre-installation, there is no xorg.conf file to edit. Any ideas. am missing my ubuntu

System specs: AMD 64FX-55, 2x 7900GT, Biostar T-Force4 SLI, yada, yada

---

### Post by AscendedDaniel on 2007-04-23
I am running 7.04 Feisty on my system with SLI and it works fine. I am using an ASUS A8N-SLI Deluxe motherboard with two BFG Tech 6600GT cards. I have had trouble with previous versions of ubuntu, but Feisty worked without any X-server problems. 

So if you don't have to use 6.10, try 7.04.

---

### Post by coltrane on 2007-05-08
> **AscendedDaniel said:**
> I am running 7.04 Feisty on my system with SLI and it works fine. I am using an ASUS A8N-SLI Deluxe motherboard with two BFG Tech 6600GT cards. I have had trouble with previous versions of ubuntu, but Feisty worked without any X-server problems. 

So if you don't have to use 6.10, try 7.04.

God knows why it worked on yours then! I have almost exactly the same system as yours, the same motherboard but with Leadtek 6600GT's cards. Feisty just does the same as all the others did.
The live CD gets to the graphical screen and then freezes everything including mouse.
I have'nt tried the alternate CD but I suspect that will also do the same as previous editions.
i.e will only let me have a graphical gui as root user.
This also happens with 64bit and 32bit editions.
Strange because Debian 64bit works fine.

---

### Post by AscendedDaniel on 2007-05-08
Does Knoppix work for you? All I get is two blue dots in the upper middle part of the monitor when I try to boot from the live cd. I'm busy this week, but I could post my xorg.conf for your viewing if you want. 

Also, while it did just work off the live cd, I installed the nvidia drivers and got dual monitors working nicely. Good luck getting it work.

---

### Post by coltrane on 2007-05-12
I tried knoppix, and yes it does work on my pc, It uses XFree86(vesa) Server.
Please post your Xorg.conf file, I think I am getting closer to the answer, this would help.
Thanks

---

### Post by coltrane on 2007-07-12
I can now install ubuntu on my SLI system, it seems the cause was in bios.
The ASUS A8N SLI board has something called 'Cool & Quiet Technology' I simply disabled this in the Bios and then Ubuntu installed with no trouble.:)

---

