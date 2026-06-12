---
title: "Whenever I press both mouse buttons, it middle clicks"
date: 2009-01-23
forum: x86 64-bit Users
---

### Post by Rushz0rz on 2009-01-23
Whenever I press both of my mouse buttons at the same time, it presses the middle button. This gets really annoying when I try to walljump in warsow, does any one know how to turn it off?

---

### Post by wd5gnr on 2009-01-23
I am pretty sure you have Emulate3Buttons turned on in your xorg.conf.

Edit /etc/xorg.conf and find your pointer entries. You should see:

Option  "Emulate3Buttons" "yes"

Change yes to no or make a new line. For reference, here's my mouse section (note Mouse0 is mentioned in ServerLayout and then below that is the Mouse0 definition):

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

. . . 

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

---

### Post by Rushz0rz on 2009-01-23
ive tried adding the emulate3buttons line to my xorg.conf, and even created a hal script and neither of them worked. by the way im using intrepid and ive got a logitech mx518 and its in a usb port

---

### Post by steveneddy on 2009-01-23
Make sure that you restart X after making any changes to xorg.conf.

Ctrl + Alt + Backspace

---

### Post by Rushz0rz on 2009-01-23
restarting x didn't help :(

---

### Post by emzo on 2009-05-08
Hi, I upgraded to Intrepid 3 days ago and I have EXACTLY the same problem. I will search for the solution somewhere.

Mouse: MX518

---

### Post by emzo on 2009-05-08
I got this DONE :)

What I've done:
```
egrep "Name|Handlers" /proc/bus/input/devices
```
You will see something like..
```

...
H: Handlers=event8 
N: Name="SynPS/2 Synaptics TouchPad"
H: Handlers=mouse1 event9 
N: Name="Logitech USB-PS/2 Optical Mouse"
H: Handlers=mouse2 event10 

```
I remembered the "event10" string connected with my mouse entry
Then changed mine xorg.conf "InputDevice" like this:
```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "evdev"
        Option          "Device" "/dev/input/event10"
        Option          "CorePointer"
        Option          "Emulate3Buttons" "False"
EndSection

```
..see the "event10" position?
I did not forget to change also this section, so the mouse is "CorePointer":
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen         "Default Screen" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard" 
    InputDevice    "Synaptics Touchpad" "SendCoreEvents"
    Inputdevice    "Configured Mouse" "CorePointer"
EndSection

```

I restarted X with Ctrl+Alt+BckSp et voilá! ..worked for me

---

