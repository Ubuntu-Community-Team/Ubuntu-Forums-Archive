---
title: "Screen resolution problem"
date: 2006-02-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by phantasmagoriana on 2006-02-16
I'm new to Linux and have recently installed Ubuntu 5.10 on a dual-boot system with Windows XP. However, I can't seem to get my screen resolution to work properly.

I have an Acer 17" TFT monitor which should run at 1280x1024@60Hz (as it does in Windows), and an ATI Radeon X300SE graphics card. The screen resolution options setting only gave me the options of 640x480, 800x600 or 1024x758 by default. I've tried editing /etc/X11/xorg.conf to add 1280x1024 to the list (and have even removed all other options), but now the highest resolution I can get is 1280x800@55Hz.

If it helps, this is what the relevant bits of /etc/X11/xorg.conf look like at the moment:

Section "Monitor"
              Identifier              "Acer AL1715"
              Option                 "DPMS"
              HorizSync            28-51
              VertRefresh          43-60
EndSection

Section "Screen"
              Identifier              "Default Screen"
              Device                 "ATI Technologies, Inc. Radeon X300 SE (RV370)"
              Monitor                "Acer AL1715"
              DefaultDepth       24
              SubSection  "Display"
                            Depth                         1
                            Modes                         "1280x1024"
              EndSubSection
              SubSection  "Display"
                            Depth                         4
                            Modes                         "1280x1024"
              EndSubSection
              SubSection  "Display"
                            Depth                         8
                            Modes                         "1280x1024"
              EndSubSection
              SubSection  "Display"
                            Depth                         16
                            Modes                         "1280x1024"
              EndSubSection
              SubSection  "Display"
                            Depth                         24
                            Modes                         "1280x1024"
              EndSubSection
EndSection

I also tried adding a modeline to the monitor section, but this made no difference.

Any help would be greatly appreciated!

---

### Post by heimo on 2006-02-16
Try:
```

HorizSync            24-80
VertRefresh          49-75

```

---

### Post by phantasmagoriana on 2006-02-16
That solved it!

Thanks for your help.

---

