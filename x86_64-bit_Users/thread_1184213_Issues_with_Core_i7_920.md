---
title: "Issues with Core i7 920"
date: 2009-06-10
forum: x86 64-bit Users
---

### Post by aglc2005 on 2009-06-10
Just built a new computer with the following specs:

EVGA X58 Triple SLI
Intel Core i7 920
2 kits 3x2GB Corsair XMS 3
BFG Tech 9600GT 512mb

I am running Jaunty, and I have noticed that the CPU Scaling is not working with my i7 and is stuck at 1.56GHz (its a 2.66GHz CPU). Besides this, everything else so far has been great since my transition back to Ubuntu. I have tried searching every where to get this working, but can't seem to find anything that will help. Anyone have any suggestions?

---

### Post by Rody on 2009-06-11
what does your boot screen say your processor is running at?
It is possible that speedstep is enabled and when your computer is not under stress it down clocks your processor. Also you could try to reset bios defaults and then re setup any customizations.

---

### Post by aglc2005 on 2009-06-11
Hi, thaks for the quick response. Speedstep was not enabled in the bios, it is off by default and I have the default settings. My boot screen says the processor is running at 2.67GHz. I've run a couple commands in the prompt to see what it said what available frequencies there were (don't remember the commands now) and all that was listed was 1.56GHz. Also when I add the CPU Frequency Monitor to the bar, it tells me that frequency scaling is not supported and the processor is running at 1.56GHz.

---

### Post by Arup on 2009-06-12
Speedstep needs to be enabled in BIOS for frequency scaling, I setup a i7 for my friend on Intel board and the scaling works fine there.

---

### Post by aglc2005 on 2009-06-12
I also tried that, turning the Speedstep on and still no go on it

edit: Figured it out. Apparently the BIOS revision that came on my board wouldn't allow me to enable the turbo speed option on the i7. Well I decided to see if the older BIOS revision was at fault. Updated to the newest, could enable turbo speed, and now I have throttling, and Ubuntu is boosting it up to 2.79GHz when the need is there for it :-)

---

### Post by DesiBabu on 2009-07-07
[FONT=Arial][SIZE=3]I too have been struggling with new install of Ubuntu-64 on an Intel I-920 with 6gb ddr3 ram,  2x750 Gb Segate Baracuda and Invidia GeForce 9500GT with 1Gb DDR2 non shared Ram.
The mobo is Asus P6T.

The performance is so bad that when I unzip a 1.7Gb file it crashes my two VMWare guests with the message:

This virtual machine has been unresponsive for more than 20 seconds and has caused another virtual machine sharing a disk with it via SCSI reservations to believe it has died.

Can anyone please suggest some options. I really need to have this working else I'll be forced to go to  uncle Bill's OS

What tools can I get to test my i/o or stress test the disks/controllers etc...?

Thanks

[/SIZE][/FONT]

---

### Post by leomelo on 2009-07-07
DesiBabu,use a motherboard Intel and a Western Digital drive.And come back again with your feedback,after doing that.

---

### Post by Th3_uN1Qu3 on 2009-07-07
I know that Western Digital makes good hard drives (all my drives are WD), but an Intel mobo? Come on. I hope that was a joke. :p

---

### Post by Arup on 2009-07-07
Intel motherboards are pretty well made, they can't be overclocked except for some exceptions but overall, they are top notch in quality, their server boards are industry standard. I have the XS5400 board for my dual quads and I have around 13 DG31PR installed at my firm, not one has given us any headaches. Intel boards are made by Foxconn.

---

### Post by Th3_uN1Qu3 on 2009-07-07
Yeah but Asus (or any other manufacturer for that matter), is still going to use the same Intel chipset. I still don't get what the motherboard's got to do with it.

---

### Post by Arup on 2009-07-08
> **Th3_uN1Qu3 said:**
> Yeah but Asus (or any other manufacturer for that matter), is still going to use the same Intel chipset. I still don't get what the motherboard's got to do with it.

Some motherboards have been known to have lousy BIOS leading to all sorts of issues, in general higher cost motherboards like ASUS, Gigabyte, Foxconn etc. upgrade their BIOS frequently to weed out any issues.

---

### Post by Th3_uN1Qu3 on 2009-07-08
I have a feeling that it's got nothing to do with the mobo. The default CPU speed governor in 9.04 is ondemand, and it is set to only speed up the CPU when it's 95% used. Ubuntu 8 used to set it to 60%. Maybe it is failing to speed up the processor when needed? I do not have an i7 so i don't know how many frequency steps it has, but it could be an issue.

Regardless, this behaviour can be fixed by following this guide: [http://brainwreckedtech.wordpress.com/2009/05/29/ubuntu-9-04-bug-ondemand-doesnt-scale-cpu-speed/](http://brainwreckedtech.wordpress.com/2009/05/29/ubuntu-9-04-bug-ondemand-doesnt-scale-cpu-speed/)

---

### Post by Rizlaw on 2009-07-08
> **aglc2005 said:**
> Just built a new computer with the following specs:

EVGA X58 Triple SLI
Intel Core i7 920
2 kits 3x2GB Corsair XMS 3
BFG Tech 9600GT 512mb

I am running Jaunty, and I have noticed that the CPU Scaling is not working with my i7 and is stuck at 1.56GHz (its a 2.66GHz CPU). Besides this, everything else so far has been great since my transition back to Ubuntu. I have tried searching every where to get this working, but can't seem to find anything that will help. Anyone have any suggestions?

I have a similar system and Ubuntu 9.04 64bit OS allows my 920 D0 to scale between 1.60 - 2.87 with no problems and Conky shows all "8" cpus. At the moment, my BIOS settings for the cpu are all at defaults except for hardware virtualization which is enabled.

Based on recent experience I might also suggest looking at your power supply. I couldn't get Intel virtualization to work on my Classified MB with the Seasonic MD12-850 PS I had purchased for my new setup. My system would instantly crash each time I tried to enable the BIOS setting for virtualization. EVGA tech support recommended that I change the PS even though mine wasn't one of the listed problem PS's for the Classified MB. I changed the PS to a Corsair HX850W and the problem disappeared! I never would have believed a BIOS setting for cpu hardware virtualization would depended on a power supply.   

Also, since you have a new setup, I suggest that you check to see if  your motherboard's BIOS is the most current available. If not, you might consider an update; especially if you have a D0 stepping i7 920 cpu.

Good Luck with you new system.:):)

---

