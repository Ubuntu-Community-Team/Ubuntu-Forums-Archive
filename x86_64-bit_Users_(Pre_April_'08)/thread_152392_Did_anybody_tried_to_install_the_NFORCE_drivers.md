---
title: "Did anybody tried to install the NFORCE drivers?"
date: 2006-03-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by ispmarin on 2006-03-29
Did anybody tried to install the Nvidia NFORCE drivers? I have tried several times on Breezy but it turned the situtation worse: my network card stopped working. Breezy automatically detected everything and got to work. Dapper detected my soundcard, but alsa cannot work with it (only oss) and I was considering to try the NFORCE drivers... but not sure. 

My specs:
AMD64 3000+
Asus A8N SLI (nForce 4 SLI)
2GB Samsung RAM
120 GB Seagate SATA 7400RPM
GeForce 6200 128MB PCIEx
Dapper Flight 5

---

### Post by johnnymac on 2006-03-30
I'm running Dapper on my AMD64 system but it's NForce3 and an XPC Shuttle....Similar but not quite the same eh.

You may just have to wait 'cause support may not be there yet.  Dapper is an always-improving project and what doesn't work one day may work the next.

---

### Post by ispmarin on 2006-03-30
Yeah, agreed, not so worried about the dapper support (that I think, like breezy, is amazing), but with the performance and stability of nforce drivers. Does anybody has an idea, or made some tests?

---

### Post by jhalmu on 2006-04-01
I have quite same specs than you (AMD64 +3500/1024Mb/Abit AN8-SLI/MSI GeForce 6600), they worked well (?) in breezy, now I'm using Dapper, only occationally (only when I reboot ;) ) my ethernet do not get ip, but thats not big problem.

---

### Post by johnnymac on 2006-04-01
ispmarin - you had me interested so I did it...and no problems.

---

### Post by johnnymac on 2006-04-01
[QUOTE=jhalmu]I have quite same specs than you (AMD64 +3500/1024Mb/Abit AN8-SLI/MSI GeForce 6600), they worked well (?) in breezy, now I'm using Dapper, only occationally (only when I reboot ;) ) my ethernet do not get ip, but thats not big problem.[/QUOTE]

Okay...same issue as you....most of the time I boot and I get an IP and my interface is up...sometimes it doesn't come up so a few reboots and POOF...working again.

---

### Post by Bokonon on 2006-04-02
I would like to give them a try as well (MSI nForce4), but I am bit leery of trying them because it would be a huge pain to loose my ubuntu system--even if just for a day or so.

I assume they would clean things up and bump performance a bit.

---

### Post by jhalmu on 2006-04-02
I put ip by hand, cos my router give me wrong ip, and no it's working. One more problem have occured; my machine freezes maeby 'cos of screensaver (so i have to reboot). I take it off.

---

### Post by gmclachl on 2006-04-02
I am having problems as well, although mine are sligtly different. Everytime I shut down or boot up my machine it kills the connection on my router. I have 5 machines on the network and it only does this on hthe nvidia board. 

 George

---

### Post by NewbieNik on 2006-04-03
I am using Breezy on a MSI K8N SLI Geforce4 board with Dual-Core AMD64 3800 Processor and all works fine from install.
How are you setting IP address? Is your router using DHCP or are you setting it manually?
If you cannot connect what does ifconfig say? Is it recognising the card, but not seeing network?

---

### Post by henriquemaia on 2006-04-03
I have installed NFORCE drivers for on my newly installed Dapper Flight6 and everything is ok. But, then, so it was when not installed. I do not see any advantage in having the drivers installed at least until now.

---

### Post by gmclachl on 2006-04-03
This may seem a sily question but where are the nforce drivers. I have nvidia graphics driver installed (are they the same) 

George

---

### Post by ispmarin on 2006-04-03
No, you can download the nforce drivers from the nvidia website. But there are not the same of the nvidia _video_ drivers. 
Yeah, same here, no problems but no advantages...

---

### Post by johnnymac on 2006-04-03
I can echo the poopie-ness - no increase in any performance.....and no genie jumped out of my shuttle :(

---

### Post by robert114 on 2006-04-06
It's maybe a silly question, but arn't the drivers in the restricted module package?

Non-free Linux 2.6.15 modules on AMD K7
This package provides restricted modules for Linux version 2.6.15 on
AMD Duron/Athlon.
Currently the following modules are included:
 - madwifi (Atheros)
 - fglrx (ATI)
 - nvidia
 - fcdsl, fcdsl2, fcdslsl, fcdslslusb, fcdslusb, fcdslusb2, fcdslusba,
   fcpci, fcpcmcia, fcpcmcia_cs, fcusb, fxusb (AVM ISDN)
 - ltmodem (Winmodem)

in synaptic i get the above information, but it's just saying nvidia. Are these the video drivers or nforce?

---

### Post by ispmarin on 2006-04-09
No, just the video drivers... but this is a good question. Why the restricted modules does not include the nforce drivers?

---

