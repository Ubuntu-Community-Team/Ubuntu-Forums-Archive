---
title: "&quot;Aperature beyong 4gb.  Ignoring&quot;?"
date: 2008-11-12
forum: x86 64-bit Users
---

### Post by Torqumada286 on 2008-11-12
I had the 64bit version of Hardy and then upgraded to Intrepid when it was released.  Since then, I have been getting an error message that pops up so fast on boot up I can only get the first line, which is above.  Since 32bit systems are limited to 4gb systems, does this mean when I let the system automatically upgrade itself that it upgraded to the 32bit version instead of the 64bit version?  My system resource monitor shows a maximim of 3.9gb of memory, when it showed 4.1 in the past.  Anyone know how I can slow things down enough during the boot process to see the entire error/warning message?

Torqumada

---

### Post by phlembob on 2008-11-12
It is a factor of 10 programming error.  I will be fixed --- when is the question.  There are several other operating problems going on.  ATT the load error shouldn't bother you too much.  Work with the rest of the program and see if you wish to continue with it.  You may find some answers for the next generation.
:popcorn:

---

### Post by Torqumada286 on 2008-11-12
> **phlembob said:**
> It is a factor of 10 programming error.  I will be fixed --- when is the question.  There are several other operating problems going on.  ATT the load error shouldn't bother you too much.  Work with the rest of the program and see if you wish to continue with it.  You may find some answers for the next generation.
:popcorn:

I understand that this is an international forum and that there are people here who have english as their second laguage, so please forgive me for saying that your reply to my question doesn't make much sense to me.  Are you saying that the 64bit version of Intrepid isn't acting like a 64bit system, but it hoped that it will be in the future?

Torqumada

---

### Post by insane_alien on 2008-11-12
it will not have 'upgraded' to a 32 bit system. going from 64-bit to 32-bit that way isn't even possible unless you do a LOT of work (same goes for transitioning the other way)

i'm guessing its now just taking account of the memory used up by hardware(graphics cards and the like)

---

### Post by Yellow Pasque on 2008-11-12
> that it upgraded to the 32bit version instead of the 64bit version?
No. It does not work that way.

Look for an option in your BIOS about memory remapping or IOMMU. My motherboard (Biostar 780G) required a BIOS upgrade before this option was present.

---

### Post by Torqumada286 on 2008-11-12
> **Temüjin said:**
> No. It does not work that way.

Look for an option in your BIOS about memory remapping or IOMMU. My motherboard (Biostar 780G) required a BIOS upgrade before this option was present.

It wasn't a problem under Gutsy or Hardy.  It's not a problem under WinPro 64 or Vista 64.  The only thing that has changed was getting Intrepid, so I doubt it's some sort of BIOS problem.

Torqumada

---

### Post by Akita on 2008-11-12
There's a bug filed: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271070]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271070")

Please add your information there since the odds of anybody who can permanently fix the problem seeing a post in the forums is about slim to none :-)

---

### Post by Yellow Pasque on 2008-11-12
For more advanced users: Experiment with some different *iommu=* in the boot parameters to control the aperture.
[http://www.mjmwired.net/kernel/Documentation/x86_64/boot-options.txt](http://www.mjmwired.net/kernel/Documentation/x86_64/boot-options.txt)

---

