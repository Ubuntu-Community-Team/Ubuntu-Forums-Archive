---
title: "Dualhead (dual monitor) display not working :("
date: 2008-08-23
forum: x86 64-bit Users
---

### Post by zachhill91 on 2008-08-23
I have an nVidia GeForce 8600GT 512MB which has a DVI and a VGA output.

I have a 22" Acer monitor plugged into the DVI output and I have a Dell 19" display plugged into the VGA.

I can only use one or the other, not both.
I tested it in windows and works there by customizing the nVidia drivers.

Is there a way to customize them in Ubuntu, or a program I can use to get this set up?

Thanks in advance for any and all help.

---

### Post by xen-uno on 2008-08-24
The default NVidia drivers are lacking the "NVidia X Server Settings" applet, but it is available via Synaptic. It might help to install the latest drivers from the NVidia site, using [http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6) as a guide. If that doesn't work then you may have to do some xorg.conf editing. Do a google or forum search on dual monitors.

edit: here's a long one ...

[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

---

### Post by modestmelody on 2008-08-24
I've had Twinview setup several times so if you need any further help after reading those threads feel free to PM me your xorg.conf and I'll take a look.

Just don't forget to backup your xorg.conf so if things get fishy you can always go back to the old settings.  Graphically, things work pretty well with Nvidia right now but I've always done dual screens the old fashion way.

---

### Post by zachhill91 on 2008-08-24
Thanks guys, but I found a program called EnvyNG, I installed that and configured the nVidia X Server Settings and everything worked.

Now I am enjoying laying in bed typing this. LOL

---

