---
title: "Fglrx overclocking videocard?"
date: 2007-02-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by rogeriovinhal on 2007-02-04
Hi, I am having some crash problems at some games, especially with wine, even with games that are known to work perfectly. It crashes always after about 1 to 5 minutes of gameplay.

I noticed also that in Wine, the 3D games are a LOT smoother and anti-aliased than in Windows, it seems like another videocard is playing the game, and at the same resolution as in Windows.

Firstly I thought the crashes had to do with sound, because the sound driver keeps on giving errors and warnings all the time in the console, but today I tried without any sound at all, and it still crashed.

So, I thought that because of the smoothness the game is playing, maybe the videocard is something of overclocked by default, or with some options that shouldn't be enabled, as the "aticonfig --initial" never worked with me, I always had to edit the xorg.conf to change the driver to fglrx.

This is the important part of my xorg.conf, is there something I should change or add?

```

Section "Monitor"
        Identifier   "F700P"
        Option      "DPMS"
EndSection

Section "Device"
        Identifier  "ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        Option      "OverlayOnCRTC2" "0"
        VideoRam    131072
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
        Monitor    "F700P"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "0"
EndSection

```

---

