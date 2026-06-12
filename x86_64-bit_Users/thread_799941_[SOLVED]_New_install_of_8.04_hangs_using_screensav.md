---
title: "[SOLVED] New install of 8.04 hangs using screensaver"
date: 2008-05-19
forum: x86 64-bit Users
---

### Post by Fozzie69 on 2008-05-19
This is my first ubuntu install on a new build PC

Motherboard: MSI K9MM-V, VIA Chipset
Athlon 64 3200+
1 Gb RAM
Using onboard VGA graphics
160 Gb Hard Drive

Install went without error.  All appears to work well, except when trying to use certain screensavers - most of which cause a hang/freeze/crash (not too sure of the correct term)

What I typically see is the screen is suddenly covered with apparently random vertical lines, the mouse does not respond, the keyboard capslock key no longer lights the led, computer doesn't respond to <cntl><alt><del>

Only way out is the reset button on the front of the PC.

I have since discovered that some games hang the computer in the same manner - the common link appears to be all involve 3d graphics (games and screensaver options).

This afternoon, I also tried a clean install of Gutsy Gibbon and I get the same crash.

Any ideas?

---

### Post by Sef on 2008-05-20
Do you have a video card around that you could install and see if the problem still exists?

---

### Post by Fozzie69 on 2008-05-20
I have ordered one which I'll try when it arrives.  Is it quite straight forward to put in a graphics card?  Does ubunto automatically recognise it?

When I turn off the PC, put in the card and then turn it on - do I plug the monitor into the on-board port - or the new card right away?

Is there a 'installing a graphics card' HowTo somewhere that you could point me to?

Thanks

---

### Post by Fozzie69 on 2008-05-20
OK - a graphics card solved it.  I've just installed an NVIDIA GF6200.  I was impressed - I simply powered down the PC, put in the card and powered back on.  The OS noticed the card, recommended a new driver, I clicked yes to a couple of things, the PC rebooted and everything worked.

:)

It's a shame it crashed rather than gracefully handling the absence of a card - but it's good that it all works OK now.

---

