---
title: "Linux Restriced Driver: Video and Wi-Fi"
date: 2007-08-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by Maria_Firewire on 2007-08-11
Hello,

I just recently installed Feisty Fawn 64 bit. I had to use the vesa driver instead of the nv (my video card is Ge-Force 6800 GS) to get the GUI. But then I found this great thread to install the latest nvidia driver for my card: 

[http://ubuntuforums.org/showthread.php?t=496103&highlight=native+nvidia+driver+for+feisty+64-bit](http://ubuntuforums.org/showthread.php?t=496103&highlight=native+nvidia+driver+for+feisty+64-bit)

That worked great! HOWEVER, I had to uninstall the linux restricted drivers package(s) which consequently stopped my wireless from working, :)

I thought maybe installing the packages again, AFTER I had the new nvidia driver working would be alright but to my dismay, it killed the video driver again.

So here's my question, how (or is it possible?) can I get my wireless working AND keep the nvidia video driver I have installed? I have an Orinoco 11a/b/g Gold PCI card...atheros chipset?

I'm still pretty noob.

Any help is much appreciated!

-Maria-

---

### Post by John.Michael.Kane on 2007-08-11
> **Maria_Firewire said:**
> Hello,

I just recently installed Feisty Fawn 64 bit. I had to use the vesa driver instead of the nv (my video card is Ge-Force 6800 GS) to get the GUI. But then I found this great thread to install the latest nvidia driver for my card: 

[http://ubuntuforums.org/showthread.php?t=496103&highlight=native+nvidia+driver+for+feisty+64-bit](http://ubuntuforums.org/showthread.php?t=496103&highlight=native+nvidia+driver+for+feisty+64-bit)

That worked great! HOWEVER, I had to uninstall the linux restricted drivers package(s) which consequently stopped my wireless from working, :)

I thought maybe installing the packages again, AFTER I had the new nvidia driver working would be alright but to my dismay, it killed the video driver again.

So here's my question, how (or is it possible?) can I get my wireless working AND keep the nvidia video driver I have installed? I have an Orinoco 11a/b/g Gold PCI card...atheros chipset?

I'm still pretty noob.

Any help is much appreciated!

-Maria-

First the 6800 series GeForce cards should work using the restricted driver manager, and the driver that currently ships with feisty.

With that said you have three options.

1) Find out how the writer of that guide managed to installed the drivers with out loosing his wi-fi capabilities,

2) Reinstall feisty, and use the restricted driver manager to install the 9XXX series drivers.

3) Retry installing the driver using the [URL="http://www.albertomilone.com/nvidia_scripts1.html"]envy script  
[/URL]

IMHO I would have used that guide only if there were issues with the driver that ubuntu shipped.

---

