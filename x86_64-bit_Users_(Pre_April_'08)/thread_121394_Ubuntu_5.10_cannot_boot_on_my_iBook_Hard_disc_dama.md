---
title: "Ubuntu 5.10 cannot boot on my iBook: Hard disc damaged after trying..."
date: 2006-01-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by s_groening on 2006-01-25
Yeterday evening I tried booting my official Ubuntu 5.10 PPC cd on my iBook G4 1 GHz, and it failed miserably!

Until  then the computer worked flawlessly, however, after trying to boot by hitting Alt on boot to select a different 'Statup Disc', the graphics got all weird and the computer would not boot.

My Mac OS X 10.4.4 installation reported I/= errors from the 'Startup Disc' and could not boot MAc OS X. On the other hand, Darwin 8.01, installed on another partition on the same physical drive, worked perfectly...

'Disc Utility' on my Mac OS X 10.4 Install DVD cannot correct the problem at all... Now I seem to have lost valuable data in my longing to stack my computer with free software.... Oy Gevalt!!

Can anyone help me??

---

### Post by stream303 on 2006-01-25
I had a similar problem when I lost the yaboot on my ibook when I was messing around with startup disks.

I'm not sure this will work for you since it sounds like you are just booting the live cd, but it worked for me with a dedicated install.  Proceed at your own risk.

The fix for me was to reset the Mac's pram by rebooting and holding down command-option-P-R  (cloverleaf/command key).

Awkward to manage 4 fingers during that...

---

### Post by s_groening on 2006-01-25
I have now been able to save all of my files by removing the hard disc and mounting it from a USB enclosure on an iMac ....

I did not lose anything of importance, though... -However, I no have countless hours of installing and tweaking Mac OS X in front of me :)

Thank you for your reply!

---

