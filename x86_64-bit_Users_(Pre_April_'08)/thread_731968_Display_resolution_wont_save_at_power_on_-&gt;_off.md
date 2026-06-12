---
title: "Display resolution wont save at power on -&gt; off"
date: 2008-03-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by chootarlaal on 2008-03-22
once i set the display settings to 1280x1024 and restart, it works fine, but on power off and then on, the display settings reset to 1600x1200.  i do have my drivers set for my card, nvidia 8600gts.

i did check the 
/etc/X11/xorg.conf
```

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation G80 [GeForce 8600 GTS]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Virtual 1600    1200
                Modes           "1280x1024@60"  "1280x960@75"   "1280x960@60"   "1400x1050@60"  "1280x1024@75"  "1600x1200@65"  "1152x864@75"   "1600x1200@60"
        "1024x768@60"   "1024x768@70"   "1024x768@75"   "832x624@75"    "800x600@60"    "800x600@75"    "800x600@72"    "800x600@56"    "640x480@75"    "640x4
80@72"  "640x480@60"
        EndSubSection
EndSection

```

---

### Post by EnkiduinNZ on 2008-03-23
You could try copying xorg.conf.failsafe to a safe place, copying the xorg.conf to xorg.conf.failsafe and restarting Xorg (by rebooting or Ctrl-Alt-Backspace).

If this fails, and X doesn't come up, remove xorg.conf and copy the xorg.conf.failsafe to xorg.conf and copy the xorg.conf.failsafe from where ever you saved it.

I think that for some reason Xorg, when starting, decides to to use the 'failsafe' version no matter what you do. :(

The above procedure worked for me. :)

Cheers,

Cliff

---

### Post by chootarlaal on 2008-03-24
but i dont have any xorg.conf.failsafe in my /etc/X11 directory....

---

### Post by chootarlaal on 2008-03-30
it was the virtual setting, it was set to 1600 1200.

---

