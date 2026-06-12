---
title: "Screen Resolution"
date: 2006-01-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by Dath on 2006-01-02
I just installed ubuntu, and on the page where resolutions are chosen, I couldn't figure out how to select more than the three(1024, 800, and 640). Now i'm stuck at 1024*768, when my screen supports 1280*1024 as it is an LCD. How can I fix this?
Thanks for your help!

---

### Post by mazelado on 2006-01-02
You need to edit your /etc/X11/xorg.conf file. Look for a section that looks similar to this:

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon 9800 Pro (R350 NH)"
        Monitor         "DELL M992"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection
```

Where it says "Modes" in each SubSection, add "1280x1024" (with quotes) and after a reboot it should show up as a selection.

---

### Post by Dath on 2006-01-02
Ok, it won't let me edit it because i'm not the 'owner.' How can I do this?

---

### Post by FluffyElmo on 2006-01-02
You have to run the editor as root. *sudo* lets you run a program as root while logged in as a regular user. So to edit xorg.conf using gedit:
```
sudo gedit /etc/X11/xorg.conf
```
You should also make a back-up copy before editing:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.org
```

Good Luck!

---

