---
title: "Help! Display fails to initialize after installing Nvidia Drivers"
date: 2007-07-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by fragility14 on 2007-07-12
I have a PCI Express 6600, and I installed the drivers for it on Kubuntu 7.04 through the adept package manager, then put in the command listed on the package manager to enable it. (thinking something would for once be just that easy)

Nowm when Kubuntu loads it shows the bar fill up once, flashes text, then goes back to the bar which doesnt fill up then a cursor just blinks and I cant put in commands.

I can get to the command line through recovery mode, but simply dont know what to do once there...


help please....I would have read an install tutorial closely, but I really thought using the package manager was the best solution.


edit: apt-get xorg-xserver and reset the driver to VESA

will use a guide for installing the right driver ;)

---

### Post by dabl on 2007-07-12
> **fragility14 said:**
>  then a cursor just blinks and I cant put in commands.

Actually, at this point you can do Alt-F1 or Ctrl-Alt-F1 and get a text prompt.
> edit: apt-get xorg-xserver and reset the driver to VESA

I think the configuration script that you want is ```
sudo dpkg-reconfigure xserver-xorg
```

On the first screen, choose "NO" to auto-detect, and on the next screen choose "VESA" and then at the end of the script it will dump you back to the text prompt.  At that point you can type ```
startx
``` and you should get a functional GUI, in which to proceed with your project.  :)

---

### Post by fragility14 on 2007-07-12
thanks a lot for responding, I did figure it out. One has to remember following a list of commands isnt actually that hard you have to just not be intimidated by it...up and working like a champ :)

---

