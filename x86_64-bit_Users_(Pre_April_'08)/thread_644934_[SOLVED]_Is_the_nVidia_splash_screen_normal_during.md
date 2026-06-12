---
title: "[SOLVED] Is the nVidia splash screen normal during login/logoff?  Can it be disabled?"
date: 2007-12-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by crjackson on 2007-12-19
Well, I finally got my splash screen / logins screen / video playback corruption problems all sorted out and now I have an nVidia splash screen when loading and logging off.  I'm guessing this is normal.  Can I turn it off?

Thanks.

---

### Post by dlpfmVfH on 2007-12-19
you can turn the nvidia logo off, by doing the following:

edit you're xorg.conf by typing the following in a terminal:

```
sudo gedit /etc/X11/xorg.conf 
```

and add this line to the section "device" :

```
Option        "NoLogo"    "True"
```

and for further reference this is my "device" section:
```

Section "Device"
    Identifier    "nVidia Corporation G80 [GeForce 8500 GT]"
    Boardname    "nvidia 8500GT Silent"
    Busid        "PCI:1:0:0"
    Driver        "nvidia"
    Option        "RenderAccel"    "true"
    Option        "TripleBuffer"    "true"
    Option        "XvmcUsesTextures"    "true"
    Option        "InitialPixmapPlacement" "2"
    Option        "BackingStore"    "true"
    Option        "DamageEvents"    "true"
    Option        "UseEvents"    "true"
    Option        "DPMS"    "True"
    Option        "AllowGLXWithComposite"    "true"
    Option        "UseEdidDpi"    "false"
    Option        "AddARGBVisuals"    "True"
    Option        "AddARGBGLXVisuals"    "True"
    Option        "NoLogo"    "True"
    Screen    0
EndSection
```

---

### Post by crjackson on 2007-12-19
Great.  I was actually looking in the nvidia-settings app. without any luck.

Thanks a bunch...

---

### Post by crjackson on 2007-12-20
Thanks, worked perfectly.

---

