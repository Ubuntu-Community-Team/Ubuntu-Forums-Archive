---
title: "No boot from Hardisk"
date: 2007-01-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by tooCanad on 2007-01-23
Noob here. 

Building a pc on the  cheap with a combination of new and recycled parts.

New motherboard       - Biostar GEFORCE 6100-M9
New CPU                    - AMD 64 Athlon 3700
New RAM                    - 1 GIG Corsair DDR 400
Recycled Hard Drive    -  Western Digital 80 Gig
Recycled CD               - Creative 48X

I can't get ubuntu 64 to boot from the hard disc after install.

I am able to run the live cd no problem.  I have gone through the install several times using 6.10, 6.06, and 6.10 alternate CD burned at 4X.

Still no luck. The HD ticks away during the install. CD ejects when the install is complete. However, when it comes to to load from the HD, it fails and ask for a system disk.

Any assistance is appreciated. This is day 4 with no luck.

Should I try the 32 bit version?

TC

---

### Post by Lil_Eagle on 2007-01-23
It sounds to me like grub isn't installing in the Master Boot Record (MBR).  It is possible that the HD would better serve as a paperweight than a functioning part of a computer system.  They don't last forever you know.

---

### Post by tooCanad on 2007-01-23
With respect to the aging hard drive, it's still going strong.

Found a post on Google groups, my Western Digital hard drive doesn't like to be alone on an IDE cable if it's set to master.

This was my problem. I put the CD on the same cable and all is good, though the last install attempt was Fedora.

TC

---

### Post by Lil_Eagle on 2007-01-26
I didn't say your HD was toast, I only said it could be.

I'm glad you found the answer to your problem.  Funny how things can be so simple sometimes.

---

### Post by tooCanad on 2007-01-26
It's the little things that make you crazy. Whenever you do something new it inevitably takes some time and effort before you get where you need to be. Newly built PC, new operating system and an issue. Where do you start?

Thanks for the post.

---

