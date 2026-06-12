---
title: "Can't decrease resolution"
date: 2006-12-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by saisrujan on 2006-12-23
i'm on an AMD64 with on-board-GPU-Mobo NVIDIA® GeForce™ 6100 and NVIDIA nForce™ 430 chipset.

The current resolution is 1280x1024 (native resolution for the monitor (a Viewsonic VA712), and i would like to decrease the resolution to 1024x768 or 1152x864. But when I change the resolution using System -> Preferences -> Screen Resolution, then the screen flickers and gets back to the original resolution I have, ie., 1280x1024. 

I feel X might be crashing when using the new resolution, and so is returning me to the original resolution (but I might not be correct).
  
Here are the relevant sections from my xorg.conf file.
```

Section "Monitor"
        Identifier      "VA712"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "VA712"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection
```

What am I missing? Please help.

---

### Post by saisrujan on 2006-12-24
I realized I was using vesa drivers. I downloaded nvidia-glx drivers and the problem is solved. 

I should have done my home-work before posting ;)

---

