---
title: "Ubnutu Live CD 5.10 on AMD64"
date: 2006-05-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by skali on 2006-05-03
Hai

I have just recieve my Ubuntu CDs.
I first tried the Live CD to check the how does it work.
Everything went fine till the GUI step. Screen goes white with the mouse cursor hanged at the middle of the screen.
My system configration is:

AMD Athlon 64 2800+ 
ASUS KV8-X Motherboard
256 MB DDR 400 RAM
ATI Radeon 9200SE 128MB AGP
Segate SATA 80GB 
Phillips 107S5 Monitor

I also tried the 32-bit verison of the LIVE-CDs with all in vain.
[http://ubuntuforums.org/images/liteblue/icons/icon8.gif](http://ubuntuforums.org/images/liteblue/icons/icon8.gif)
Angry

---

### Post by Rippa on 2006-05-04
I don't know if I can help you but I had similar problems with ubuntu on my machines. I expect it is the ATI graphics card. I had to install ubuntu on my system then I had to edit the "/etc/X11/xorg.conf" file (I booted into the shell) and tell it (the file) to use 'vesa' (the basic vga hardware with no acceleraion) once I got into ubuntu I had to follow the procedures of the 'How to ATI drivers' (this info exists somewhere in this wiki stuff try doing a search) . Now My system is dandy! Acceleration works on my graphics card.

If you require more information then let me know, I don't have it all handy currently.

Good luck.

---

### Post by skali on 2006-05-04
Thanks for your advice!
However I am new to Linux and I dint know as much as you know.
It would be very knid of you if you jot down the step need to do this or provide link address.

Thanks

---

### Post by Errol on 2006-05-04
I also just received my 64 bit cd's and tried to run live. I don't intend installing the 64 bit version until I see it running on live. Unfortunately it doesn't get past the "disk loading" stage so I'm stuck. As I am running a very good 386 version of Ubuntu AND Kubuntu I'm thinking of giving up of the conversion to 64bit and asking to be sent the K7 set of disks. 
Sorry that my experience didn't help you but I feel as frustrated and wanted to sympathise. Maybe you should also go for K7? Any comments?
Errol

[QUOTE=skali]Hai

I have just recieve my Ubuntu CDs.
I first tried the Live CD to check the how does it work.
Everything went fine till the GUI step. Screen goes white with the mouse cursor hanged at the middle of the screen.
My system configration is:

AMD Athlon 64 2800+ 
ASUS KV8-X Motherboard
256 MB DDR 400 RAM
ATI Radeon 9200SE 128MB AGP
Segate SATA 80GB 
Phillips 107S5 Monitor

I also tried the 32-bit verison of the LIVE-CDs with all in vain.
[http://ubuntuforums.org/images/liteblue/icons/icon8.gif](http://ubuntuforums.org/images/liteblue/icons/icon8.gif)
Angry[/QUOTE]

---

