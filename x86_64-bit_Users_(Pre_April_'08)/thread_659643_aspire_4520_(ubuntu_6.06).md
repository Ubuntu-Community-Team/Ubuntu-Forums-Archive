---
title: "aspire 4520 (ubuntu 6.06)"
date: 2008-01-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by s.jesudasan on 2008-01-05
hi
im having aspire 4520 (ubuntu 6.06)
and im trying to install drivers for nvidia 7000m graphics card
i tried to install nvidia restricted driver for k8
and configured then when i restarted my computer i 
didnt get a gui
so i went and changedthe driver from nv to vesa
and then i was able to boot int gui but with same 1024x800
resolution

my /etc/X11/xorg.config file is

Section "Device"
        Identifier      "NVIDIA Corporation NVIDIA Default Card"
        Driver          "vesa"
        BusID           "PCI:0:18:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NVIDIA Default Card"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
 EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection

kindly help me

---

### Post by rajeev1204 on 2008-01-06
u need the latest nvidia drivers for the nvidia 7000 graphics chip version 100.14. which is not avalable in 6.06.

Install gutsy and u can download from the repository .

---

