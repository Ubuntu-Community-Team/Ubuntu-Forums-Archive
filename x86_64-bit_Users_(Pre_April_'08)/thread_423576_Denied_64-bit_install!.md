---
title: "Denied 64-bit install!"
date: 2007-04-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by lnebrown on 2007-04-26
I'm new to Ubuntu, trying to install Feisty 64-bit on my Toshiba A135 laptop (hoping to dual-boot with Vista), but as I start to boot of the CD, I get the "your cpu does not support long version.  please choose a 32 bit version."

I have the Intel Centrino Duo processor, and in the vista device manager it shows two processors, each a T2250 1.73GHz.

Why would I be getting denied here?  I looked at my BIOS settings and it appears that the only option related to the two cores (do you want the second core enabled, or something like that) is enabled.

Appreciate the advice in advance...

---

### Post by ronocdh on 2007-04-26
> **lnebrown said:**
> I'm new to Ubuntu, trying to install Feisty 64-bit on my Toshiba A135 laptop (hoping to dual-boot with Vista), but as I start to boot of the CD, I get the "your cpu does not support long version.  please choose a 32 bit version."

I have the Intel Centrino Duo processor, and in the vista device manager it shows two processors, each a T2250 1.73GHz.

Why would I be getting denied here?  I looked at my BIOS settings and it appears that the only option related to the two cores (do you want the second core enabled, or something like that) is enabled.

Appreciate the advice in advance...
I believe the issue is that while your processor does have two cores, it's still only 32-bit. The most common case of this is the Intel Core Duo versus the Core2 Duo; 32-bit and 62-bit, respectively. Fortunately, the generic kernel from the i386 CD supports SMP, and so you'll still get to work both cores.

You'll lose SMP functionality if you upgrade to a strictly i386 kernel, though.

So just install the typical i386 build and you'll be A-OK. =)

---

### Post by lnebrown on 2007-04-26
> **ronocdh said:**
> You'll lose SMP functionality if you upgrade to a strictly i386 kernel, though.

So just install the typical i386 build and you'll be A-OK. =)

Thanks for the info.  So is there any difference in performance between a 32-bit OS using SMP and a 64-bit OS?

And the quote above sounds like a contradiction... "lose SMP" with a "strictly i386 kernel", but a "typical i386 build" is OK??  What's the difference?

Thanks!

---

### Post by ronocdh on 2007-04-26
> **lnebrown said:**
> Thanks for the info.  So is there any difference in performance between a 32-bit OS using SMP and a 64-bit OS?

And the quote above sounds like a contradiction... "lose SMP" with a "strictly i386 kernel", but a "typical i386 build" is OK??  What's the difference?

Thanks!
Well most i386 processors are not dual cores... only at the end of 2005 and beginning of 2006 did Intel pump out those 32-bit dual core processors such as the Core Duo; AMD had long since been fully 64-bit, and Intel was trying to play catch-up. The generic Linux kernel, which Ubuntu installs by default, will afford you SMP capability; just be careful if you ever go to update your kernel-headers, because some not-so-careful people might order you to grab the i386 ones, which mean that Ubuntu will treat your proc as only having one core.

Not too big of a deal, actually, because your other kernels will still exist and be visible on the GRUB screen. If you ever "mess up" and switch to i386, you can also edit your GRUB conf file and comment out the i386 kernel, so the generic boots by default.

Sorry if that's unclear; post a question again and I'll do my best.

---

