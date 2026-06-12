---
title: "Manually Adding LCD Monitor in Jaunty?"
date: 2009-05-03
forum: x86 64-bit Users
---

### Post by allandelmare on 2009-05-03
Hey,

I have an ACER AL1706 LCD. My NVIDIA X Server Settings application recognizes it as a CRT. The display looks like an OLD CRT with a refresh problem (diagonal lines wavering across screen)

I found the driver, which includes an .INF and a .ICM file...the problem is, I'm new to Linux and have no CLUE what to do now.

I'm running Jaunty 9.04

Thanks

---

### Post by allandelmare on 2009-05-04
forgot to mention Jaunty 64 bit...

---

### Post by Yellow Pasque on 2009-05-04
Report it as a bug to Nvidia

---

### Post by allandelmare on 2009-05-04
Okay, but in the meantime, I would still like to install the correct driver, which I have.  

Perhaps I'm not understanding? Are you saying that it's impossible to manually add a monitor driver in Ubuntu?

---

### Post by Erlander on 2009-05-04
Try System/Administration/Hardware Drivers.

It should offer you the correct drivers for your display card.  The monitor should be recognised correctly at boot.

Rob

---

### Post by garethclark on 2009-05-04
The screen is not always picked up correctly on boot. I had this problem with 8.10. Do the following.

Type the following in the terminal:

sudo displayconfig-gtk


Then under screen - model. Select Generic and the LCD screen resolution your screen offers. Then make sure the resolution is also checked to what you want. Then it should work.

---

### Post by allandelmare on 2009-05-06
Hmmm...

$ sudo displayconfig-gtk

sudo: displayconfig-gtk: command not found

---

### Post by SirAry on 2009-05-09
About same problem with an 42'' TFT screen ... it works as VGA detected as unknown ... On HDMI is detected as HEC and it tries to show the image, and after it falls to black, and so on ... anybody?

It seems that jaunty is very buggy if you need something over the basic functionality ... I had big problems to get sound on optical S/PDIF ... etc ...

If anybody knows how to ad generic panels in jaunty please share ...
Thanks

---

