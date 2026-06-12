---
title: "Cannot install [k]ubuntu 8.10"
date: 2008-11-09
forum: x86 64-bit Users
---

### Post by Cerium on 2008-11-09
I'm attempting to install Kubuntu 8.10, but every time I get passed the main progress bar (either install or the livecd demo), I get a black or white screen (random) and all keyboard input is ignored; in fact, I have to either reset or unplug the machine at this point.

I've checked my ram and verified the CDs and there are no errors. The only issue I've run into is this:

[0.004000]Aperture beyond 4GB. Ignoring
[0.004000]Your BIOS doesn't leave a aperture memory hole.
[0.004000]Please enable the IOMMU option in the BIOS setup.
[0.004000]This costs you 64MB of RAM

Google results tell me this is an AGP thing, but I have no AGP slot (nor any AGP bios options), so I'm not sure how to address this.

I've noticed a thread started by someone else with this issue, but it ends with what amounts to "lol, it's working now" without any hint of what was done or why it's suddenly working.

The relevant hardware I'm running is:
- MSI K9A2 Platinum Mainboard
- 8GB RAM
- ATI 4870 PCIe Graphics

There's no onboard video, nor do I own a PCI video card to test what the afore mentioned thread hinted at.

Any help would be appreciated.

-C

---

### Post by Mark69 on 2008-11-09
Sorry to hear your troubles Cerium....I had simular issues all i can advise is that if you havnt already done so is update your bios, disable any quiet n cool  and check your power saver settings the one i pin pointed to was HPET support try disabling it and try again.

Hope this helps :)

---

### Post by inter4ever on 2008-11-09
Hi

I also have the ATI 4870 and I suffer from the white screen issue. The solution that I have found is to press F4 on the live CD menu and then choose safe graphics mode. This will boot the live CD with VESA drivers. I have yet to install intrepid so I don't know what would happen after installation. I believe others could help you with that till i manage some time to get it installed this weekend.

---

### Post by Cerium on 2008-11-09
Disabling HPET didn't change anything, but using safe graphics mode fixed it enough to actually install.

Slightly off topic: Why would the installer and the live CD use non-safe graphics? Wouldn't it be detrimental to the potential user base if attempting to "try linux" caused problems?

Anyway, thanks for the help. I should be able to get everything working from this point.

-C

---

### Post by inter4ever on 2008-11-09
It's great that safe graphics mode worked. I am glad that I was of help to you. I belive the issue is with the driver choosing mechanism in ubuntu, it is choosing a driver that does not supprot the ATI 4870 or so I think. Anyway do you mind telling me what happenned after the install? Do you get to the desktop then install the fglrx driver or does ubuntu enable that driver again and you get locked up witha white screen?

---

### Post by Cerium on 2008-11-10
At the moment I'm still fighting with the installer, though I think my dvd drive is in need of an RMA as it gets to 42% of the installation process then starts blinking in a very error-message-like way.

Sadly, I've not had the fun of dealing with proper video (or audio, that should be fun too) drivers as of yet.

---

### Post by Cerium on 2008-11-10
So, after replacing the optical drive, I got this beast installed. However, I'm still running in safe graphics mode which I'd like to fix. First thing I did was went to "Hardware Drivers" and tried to activate the proprietary drivers. Problem is, though, no matter how many times I click the Activate button, nothing happens.

Any ideas? I've heard there are issues with the drivers straight from the ATI website, so I'm a bit skeptical to jump to those before figuring this out.

-C

---

### Post by Reiger on 2008-11-11
Thanks to the safe graphics guy. Was wondering about how on earth come the Live CD did work on PC X, but got locked up on Y. Tis the ATI 4870HD...

Question to the previous poster: do you actually *have* the ATI driver? It might just be Ubuntu 'knows' the ATI cards may use a propietary driver and hence show the option -- but if you don't have a driver any attempt to activate one would fail...

IIRC the package is called something with fglrx, try an aptitude search on that.

EDIT: And for the record, the safe graphics work-around/option works for the AMD 64 Intrepid Ibex.

---

### Post by stmiller on 2008-11-11
woops- sorry. ignore post!

---

### Post by Yellow Pasque on 2008-11-11
System -> Administration -> Software Sources
Make sure you have the restricted repo enabled, or trying to activate restricted  drivers won't work.

---

### Post by Cerium on 2008-11-13
> **Temüjin said:**
> System -> Administration -> Software Sources
Make sure you have the restricted repo enabled, or trying to activate restricted  drivers won't work.

I didn't have an Administration app/button/tab, so this didn't really lead anywhere. Interestingly enough, in Adept I already had enabled restricted sources but it didn't find any drivers.
What ended up happening is after updating the Hardware Drivers app, clicking the "Activate" button caused it to download and install the drivers -- and every thing's been working fine since.

Now I get to deal with finding a good browser. Firefox would be nice, but it looks ugly on Kubuntu; lots of graphical anomalies and what have you. Problem is, I've grown quite fond of my extensions (No-Script, DownThemAll, All-In-One Sidebar).

Suggestions?
-C

---

### Post by Yellow Pasque on 2008-11-14
I'm guessing a lot of KDE people use Konqueror.

BTW, the aperture thing is fairly common and occurs for AGP and PCI-e boards, because the BIOS doesn't support memory remapping (or it's not enabled). It will not stop the system from booting.

---

