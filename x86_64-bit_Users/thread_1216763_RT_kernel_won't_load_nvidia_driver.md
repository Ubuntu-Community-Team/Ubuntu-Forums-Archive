---
title: "RT kernel won't load nvidia driver"
date: 2009-07-18
forum: x86 64-bit Users
---

### Post by acidblue on 2009-07-18
When i try to boot the RT kernel i get an error:
"Failed to load NVIDIA kernel module. screens not found"
it'll load in low graphics mode, but thats all.

Also i'll get "display 0 busy"
Is there a way to get the rt kernel to load the driver?
or am i SOL?
I need the rt kernel for midi support for sound recording.
Any advice would be appreciated.

Using Ubuntu 9

---

### Post by Arup on 2009-07-18
Have you installed nvidia driver via .sh downloaded from nvidia site? If so it doesn't have the rt patch so rt kernel won't work with it. Suggest you install the driver from the repository via the hardware drivers applet, in case you need the latest driver add this ppa [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by acidblue on 2009-07-18
No i didn't use the .sh driver.
I used the System>>Admin>>Hardware Drivers.
I'll try that link, but i'm pretty sure i'm using the current driver.

---

### Post by Arup on 2009-07-18
Hardware drivers should work fine, its not the latest thoug unless you add the ppa.

---

### Post by acidblue on 2009-07-18
Yes they should !
but in my case there're not

---

### Post by Arup on 2009-07-18
Try removing the drivers and then reinstall, also this time use the PPA.

---

### Post by acidblue on 2009-07-18
ok i'll give it a go.

---

### Post by acidblue on 2009-07-18
No, that didn't work.
I'm getting the same error messages

---

### Post by Arup on 2009-07-19
Go to Synpatic and mark complete remove linux restricted modules and linux restricted modules common and reboot and see.

---

### Post by acidblue on 2009-07-19
Ok, i'll do that first thing in the morning,getting late in my neck
of the woods.
ZZZZZZZZZZZZZZZZ

---

### Post by acidblue on 2009-07-20
Unfortunately that didn't work either.
I get this when i run 'nvidia-config' in the RT kernal:
Using X configuration file: "/etc/X11/xorg.conf".

WARNING: No Layout specified, constructing implicit layout section using screen
         "Default Screen".


WARNING: Unable to find CorePointer in X configuration; attempting to add new
         CorePointer section.


WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first mouse device.


WARNING: Unable to find CoreKeyboard in X configuration; attempting to add new
         CoreKeyboard section.


WARNING: The CoreKeyboard device was not specified explicitly in the layout;
         using the first keyboard device.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'


Also here is a copy of my xconfig:
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

---

### Post by Arup on 2009-07-20
Are you using any different kernel, also I would suggest you re-install linux restricted modules.

---

### Post by acidblue on 2009-07-20
> **Arup said:**
> Are you using any different kernel, also I would suggest you re-install linux restricted modules.

Why re-install ?
Just the generic 2.6.28.13. and 2.6.28.11,(don't use this one, it's for backup in case the 2.6.28.13 gives me problems).

---

### Post by Arup on 2009-07-21
They are needed for using Ubuntu specific drivers you may use in future.

---

