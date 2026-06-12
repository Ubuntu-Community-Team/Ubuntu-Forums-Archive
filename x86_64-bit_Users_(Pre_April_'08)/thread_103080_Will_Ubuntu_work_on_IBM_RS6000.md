---
title: "Will Ubuntu work on IBM RS/6000?"
date: 2005-12-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by ed_d on 2005-12-13
Well, figured I would ask, as the PPC is also IBM RS/6000. If so, what models have you gotten Ubuntu to work on. I would really like to give this a go as I work with pseries / RS/6000 boxes. Would be cool to have one running, like a 7044-170.

---

### Post by anil_robo on 2005-12-14
You should download LIVE CD, burn the ISO image in a CD, and boot from it. If the LIVE CD works fine, you can safely install Ubuntu on the hard drive using the INSTALL CD.

---

### Post by joshuapurcell on 2005-12-21
I have access to a RS/6000 270 that I'm trying to install Ubuntu on, and I'm not getting very far at the moment. When I go in to the SMS mulitboot section and select the option to install from the CD drive, the system lists Ubuntu as an option to install (from reading the CD). When I select it however it freezes when it says "Loading Software", and never actually starts the boot process from the CD. The same thing happens if I change the boot order to boot from CD first. Could the problem be something to do with the fact that this system is SMP? I read something about a workaround for this when installing an older Debian version.

EDIT: I heard the 170s don't have the same problem the 270s do since they have different processors and require a different kernel... if I find the link then I'll post it (just did a google search on 'debian rs/6000').

---

### Post by ed_d on 2005-12-22
you are correct on the difference in procs on the 270s vs 170s. So, are you a dealer or end user to have access to a 270? I have the end of year push right now, so no time to play. I will be giving it a whirl next chance I have. Would be cool to have an  rs6k running ubuntu.....

---

### Post by joshuapurcell on 2005-12-22
[QUOTE=ed_d]you are correct on the difference in procs on the 270s vs 170s. So, are you a dealer or end user to have access to a 270? I have the end of year push right now, so no time to play. I will be giving it a whirl next chance I have. Would be cool to have an  rs6k running ubuntu.....[/QUOTE]
I'm an end-user more than a dealer, and we have a 270 assigned to our current project that isn't actually being used at the moment, so I thought it would be nice to try the install and see how it turns out. Our group isn't exactly in hardware sales (more along the lines of solutions... so both hardware and software in a way). I've installed Linux on these machines before (not Ubuntu though... yet).

---

### Post by hndrcks on 2005-12-22
[http://www.ifh.ee.ethz.ch/~rharbers/rs6000/rs6000.html](http://www.ifh.ee.ethz.ch/~rharbers/rs6000/rs6000.html)

Mayhaps this will help?

---

### Post by joshuapurcell on 2005-12-23
[QUOTE=hndrcks][http://www.ifh.ee.ethz.ch/~rharbers/rs6000/rs6000.html](http://www.ifh.ee.ethz.ch/~rharbers/rs6000/rs6000.html)

Mayhaps this will help?[/QUOTE]
Thanks for the link. That's the article I mentioned earlier but didn't look for a link to... I think it could possibly help but I haven't looked into it very much since it seems some of the available options you have with the Debian install (and mentioned in that article to perform) are not available in the Breezy install (choosing the expert-power3 option).

One thing I haven't tried yet that is mentioned is to boot by using a command at the OpenFirmware boot prompt instead of the built-in SMS boot selector. I'll try that later today and post how it goes.

EDIT: I've tried to boot off the CD using the command given in this article, and when I enter that command I get an 'OK' message followed by nothing. I thought that maybe this updated the firmware so I rebooted, but I'm still at the same point with it hanging while saying:```
RS/6000RS/6000RS/6000RS/6000RS/6000RS/6000RS/6000RS/6000RS/6000RS/6000
RS/6000RS/6000RS/6000     STARTING SOFTWARE      RS/6000RS/6000RS/6000
RS/6000RS/6000RS/6000       PLEASE WAIT          RS/6000RS/6000RS/6000
RS/6000RS/6000RS/6000RS/6000RS/6000RS/6000RS/6000RS/6000RS/6000RS/6000
```
Also, the article says to use a custom PPC64 kernel for the install process, and that the POWER3 kernel included in the Sarge installation would not boot. This may be the same situation with the standard PPC Breezy installation, and since I haven't tried to use a different kernel to boot I'm guessing that's where my problem is.

I've installed RHEL versions 3.5 and 4 using the base PPC CDs on this same hardware. I'm not 100% sure what kernel is used during the install process for that distribution, but the kernel that gets installed is the 2.4.21-32.EL ppc64 kernel.

The Ubuntu PPC manual is geared completely towards Apple systems (either old- or new-world), so it doesn't say alot that will help with getting the software installed on this system. Hopefully that will change within the coming year. Ubuntu is too popular to not be running on Power-based servers, and if Debian can do it then Ubuntu can as well.

---

