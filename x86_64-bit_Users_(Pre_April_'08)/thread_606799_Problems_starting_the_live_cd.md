---
title: "Problems starting the live cd"
date: 2007-11-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by m_nayob97 on 2007-11-08
Hi, bit of a noob here.
I installed ubuntu 7.10 32bit edition just fine, everythnig works apart from my xfi sound card. Since there are 64bit drivers available for it i wanted to install ubuntu 64.
I burned the cd and it boots from it fine, but then when i choose to "start or install ubuntu" option i get a message saying the kernel is alive and that its mapped to some table. Then the screen just goes blank. I also tried it with the safe graphics option but the same thing happens. I dont get the splash screen with the progress bar. There is continuous cd and hdd activity but nothing on screen. I left it running for 10 mins just in case, but nothing happens.
Im running;
Intel Quad Core 6600
NVidia 8800GTS
Asus Striker Extreme motherboard
2gig crosair performance ram

Ubuntu 32 works fine with this hardware.

Any ideas anyone?

---

### Post by dabl on 2007-11-08
Sounds like a bad CD burn. You need to hold the burn speed down to 4X, and don't put too much stock in the results of "check CD" -- others have gotten positive results, but it still won't read for installation. :)

---

### Post by ganja_guru on 2007-12-08
splash gave me issues too, Press 'F6' for advanced boot options (or was it F5?) and edit the end of the line:

/boot/vmlinuz-2.6.22-14-generic ***blah*** quiet splash--

remove this : 'splash--'  => you have to remove the word splash and the two '--' too, or it doesn't seem to work.

---

### Post by dlikhten on 2007-12-08
I had the exact same problem. Same specs just diff mobo.

32 bit works.
64 bit i can't do ANYTHING: Not even cd-check. 
removing 
quiet splash --
or
splash --

does not work. Computer hits a black screen then just resets in 1 sec.

---

### Post by Cappy on 2007-12-08
try adding
```
noapic nolapic nosplash
```
or
```
acpi=off noapic nosplash
```
to the end (without removing anything)

---

### Post by dlikhten on 2007-12-08
I will try this. Just FYI, i tried the alternative CD and nothing worked. Alternative text-based install did not boot, starting kernel, then blank and restart.

Can you please explain what the arguments are, It would be REALLY helpful to know for future reference.

---

### Post by dlikhten on 2007-12-08
I tried both suggestions. Same exact problem.
Q6600 processor
P35-DS3R gigabyte mobo
Geforce 8800gts

---

### Post by graphisong on 2007-12-08
Try the safe-graphics mode.

---

### Post by graphisong on 2007-12-08
Sorry- didn't see you'd tried safe-graphics mode.

---

### Post by dlikhten on 2007-12-09
I tried text-based installer with all recommendations above, nothign works.

---

### Post by kg1 on 2007-12-09
I had the same issue as the original poster which I got around by:

1) Press F4 to change video resolution when booting from the cd (I used 800x600x16).
2) Press F6 to edit line to remove "quiet splash --" and add "noapic"

I'm not sure step 1 was required, but I saw it in a different thread here (which I've now lost).
Removing "quiet splash --" alone did not work.  I also needed to add the "noapic".

Core2Duo
P35-DS3R
8800GTS

---

### Post by dlikhten on 2007-12-09
no, that did not solve it for me. I had similar issues when it was just a blank screen in 32 bit and removing nosplash and quiet did it.

---

### Post by picopir8 on 2007-12-10
If you tried all those options and they all fail then it sounds like you have a bad CD.

Do all fail at the same spot?

What about the live CD?  Where does it fail?

Did you check the ISO before burning?

Did you check the CD for errors after booting?

---

### Post by dlikhten on 2007-12-12
- I created 2 copies downloaded form 2 separate sources of the x64 cd
- I checked the burn after burning
- I tried text-based installer
- I cannot do cd-check because the crash happens before it can start up. The kernel won't even load.
- It fails when doing apic it can never detect. After doing noapic it fails a bit later. I forget the exact text.

---

