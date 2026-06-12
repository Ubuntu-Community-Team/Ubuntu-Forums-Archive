---
title: "[SOLVED] installing compiz-fusion"
date: 2008-01-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by ghettosamson on 2008-01-19
can somebody point me in the right direction for getting those wicked 3d effects like the cube and such. i am somewhat new and i just installed the mac4lin and got everything except awn to work. yeah, i have the 64bit version. but i want someone to point me to a how to or whatever cuz i would like to have the 3d effects. every time i go to system>appearance>visual effects and try to change it from none to anything else it tells me desktop effects could not be enabled.

---

### Post by Yellow Pasque on 2008-01-19
Use Method 2 Here: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

Then, there's a section further down the page about 3d effects.

---

### Post by dayanandasaraswati on 2008-01-19
First of all to make desktop effects work in your system you need to download the driver for your grahpix card and install it. Had you done this already you go to Synaptic and download compizconfig-settings-manager. That is the manager which will activate desktop effects and enable you to customize them too. Then go to Appearance and in the visual effects tab you'll find a new  fourth option called "custom" there. Enable that option to enjoy these new desktop effects. You can go to System->Preferences->Advanced Desktop Effects Settings to customize your desktop settings.

For further assistance contact this forum
[http://forum.compiz-fusion.org/showthread.php?t=6582]("http://forum.compiz-fusion.org/showthread.php?t=6582")

---

### Post by ghettosamson on 2008-01-19
the composite extension is not available is the message i get when i go to appearance>visual effects and try change to anything but none

---

### Post by dayanandasaraswati on 2008-01-19
I too had a similar kind of error like you. I searched in the net and found the following. I dont have the exact link but this is what i did. I went to xorg.conf and found these lines there in that file
> Section "Extensions"
        Option          "Composite"     "0"
EndSection



I initially had 1 in the place of zero there in the code. The tutorial asked me to change it to zero and everything is working fine now. I'm using a ATI gfx card. Try if this works

---

