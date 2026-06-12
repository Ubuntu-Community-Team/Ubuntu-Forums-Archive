---
title: "Ubuntu Freezing on install disk"
date: 2009-02-02
forum: x86 64-bit Users
---

### Post by wizardspade on 2009-02-02
I just bought a quad gateway DX4710-07 it came with Vista Pista ugg
The ubuntu cd starts the bar goes back and fourth then it starts to load and freezes on the 3 block.
Any help would be great, There is no way in living hell I am going to run Vista.

---

### Post by shadowhacker on 2009-02-03
Ubuntu is loading a driver that's not getting along with some piece of hardware you have. On the Boot Menu, there should be an options setting for something about additional parameters or boot options (number 5 I think.) Go in there and choose the parameter that disables quiet boot. Post back here with the last line of code when your computer crashes. (When Caps lock starts blinking)

---

### Post by shadowhacker on 2009-02-03
Sorry, It's been a while since I had to use the Live CD. At the boot menu you want to press F6 (Other Options.) In the command line it gives you at the bottom of the screen, delete quiet splash from the end. Then let it boot and report back with the last line of code you get. This will tell me the driver that needs to be blacklisted.

---

### Post by wizardspade on 2009-02-03
Thanks,

It was my wireless card. Turns out it was causeing vista to crash like crazy also. Guess the Mobo dont like it  just got the computer tonight man I need some sleep. hehehe
And a new wireless card.

Thanks for the tips

---

