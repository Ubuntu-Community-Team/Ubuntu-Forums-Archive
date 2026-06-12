---
title: "Orange Box and Twinview"
date: 2007-11-27
forum: Wine
---

### Post by Macros42 on 2007-11-27
I've installed the Orange Box and it is working. However I've two monitors in Twinview and I want to game on one screen only. (particularly as the monitors are different sizes and resolutions). When I go into the video settings for Portal it only allows me to select the total screen size which is 2880*1200. 

Is there any way to get it to run either windowed or just on one screen? I tried using the "Eumulate a virtual desktop" option but Portal ignored the desktop size setting and widened to both screens anyway. Preferably I'd like to play it at 1400*1050 windowed. This is the setting I play WoW in and I like it but even maximised to one screen would be fine. 

Mac

---

### Post by boast on 2007-11-28
in xorg, do you have something as such under devices
```
Option         "MetaModes" "DFP-0: 1920x1200, CRT-0: NULL; DFP-0: NULL, CRT-0: 1280x1024"
``` but with your settings of course..

---

### Post by Macros42 on 2007-11-28
Nope. Don't think I have any Metamodes option set. So this should list the resolutions of the two screens? And the other info in there - DFP-0, CRT-0 - does it make a difference they're LCDs? I have no idea what DFP is :)

Thanks for the help.

[edit]Meant to say - I'm in work ATM so I'll try this out when I get home.

---

### Post by Macros42 on 2007-11-28
Here's the relevant section from xorg.conf

```
Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G80 [GeForce 8800 GTS]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "RenderAccel" "true"
##This turns on NVidia&#8217;s TwinView
    Option         "TwinView"
##Here I&#8217;m setting the resolution to the individual monitors.
    Option         "MetaModes" "DFP-0: 1600x1200, CRT-0: NULL; DFP-0: NULL, CRT-0: 1280x1024"
    SubSection     "Display"
        Depth       1
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

Before I changed it the metamodes line read:
    Option         "MetaModes" "1600×1200 1280×1024"

Either way Portal still stretches across both screens.  What am I doing wrong?

---

### Post by Macros42 on 2007-11-28
I just realised something. That's not the option used. The below is:

```
Section "Screen"

# Removed Option "metamodes" "DFP-0: nvidia-auto-select +0+296, DFP-1: nvidia-auto-select +1280+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "DFP-0: nvidia-auto-select +1280+0, DFP-1: nvidia-auto-select +0+176"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection
```

When I changed the metamodes line to the one suggested only one screen would come on - the 1600*1200 one.

---

