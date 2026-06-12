---
title: "amd64 socket am2"
date: 2006-07-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by kanenas on 2006-07-13
I tried to install the amd64 version both the desktop and alternative but both of them can not be installed

First I tried the desktop version but it seems to have a problem with apic

then i downloaded the alternative version as it was suggested by this forum. The text installation stops after it identifies the ps2 mouse

finally i tried the normal version the x86 but again
i could not installed it

All the previous cds have been downloaded and they have been used on other boxes successfully.

Moreover the box boots the slax livecd into a useful desktop therefore it is not a problem with hardware.

I have an asus m2n sli socket am2 with an amd3800 x2

thanks in advance

---

### Post by nicolam on 2007-02-26
hey :-)

I've bought the same MB, and I've been digging through the forums here, preparing for the installation. Anyhow, this seems to be a problem with the BIOS of the mother board. Refer to this thread for more information:

[http://www.ubuntuforums.org/showthread.php?t=280083&highlight=M2N-SLI+noapic](http://www.ubuntuforums.org/showthread.php?t=280083&highlight=M2N-SLI+noapic)
[the second post details a solution]

This problem has popped up a few times in the forums, just search for "M2N-SLI noapic".

I hope this helps :-)

--
Nicola

---

### Post by pseudonym on 2007-02-27
I had the same problem with my M/B, which is of the same recent vintage. It's because the default kernel in Edgy isn't new enough.

Booting with 'noapic' should help, but at the cost of some IRQs (23 versus 15). To be able to boot without this option you will need to recompile your kernel. 2.6.19 works nice. There is a howto [here]("http://www.ubuntuforums.org/showthread.php?t=311158&highlight=kernel+compile") if you're unsure how to go about it.

The issue should also disappear with the release of Feisty, btw, since that uses kernel 2.6.20.

---

