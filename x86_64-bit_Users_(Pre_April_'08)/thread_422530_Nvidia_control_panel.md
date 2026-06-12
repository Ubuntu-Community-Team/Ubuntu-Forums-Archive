---
title: "Nvidia control panel"
date: 2007-04-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by heracles on 2007-04-25
I can invoke the Nvidia control panel by cmd line nvidia-settings.How can I make it stay in my launcher? Plus when I change the settings to twin view I get the left on the the right and the right on the left so to speak. Is there a way in Control panel I can alter this? Plus 2 try as I might I cannot save the configuration is there a lib I am missing or something? Three questions sorry.

---

### Post by John.Michael.Kane on 2007-04-25
To Create a link to the &#8220;Nvidia-Settings&#8221; Panel in your application menu:

```
gksudo gedit /usr/share/applications/NVIDIA-Settings.desktop
```

Copy paste the following lines into the new file:
```
[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA X Server Settings
Exec=nvidia-settings
Icon=
StartupNotify=true
Terminal=false
Type=Application
Categories=Application;System;
```

Save the edited file.
Log out and press CTRL+ALT+BACKSPACE  Then re-login.

To set up twinview read here.
[**HowTo: Dual Monitors** ]("http://ubuntuforums.org/showthread.php?t=221174")

---

### Post by garlik42 on 2007-04-25
To flip the screens around, use the "TwinViewOirientation" device option.

```
Section "Device"
    Identifier     "Nvidia FX-540"
    Driver         "nvidia"
    BusID          "PCI:5:0:0"
    Option         "TwinView" "True"
**    Option         "TwinViewOrientation" "RightOf"**
    Option         "UseEdidFreqs" "True"
    Option         "Metamodes" "1280x1024,1680x1050; 1280x1024,1280x1024; 1024x768,1024x768"
    Option         "UseDisplayDevice" "DFP, CRT"
    Option         "ConnectedMonitor" "DFP, CRT"
EndSection
```

You might want "LeftOf", and there may be other options.

---

### Post by heracles on 2007-04-25
Very comprehensive answers many thanks. I will reply again to give result.

---

