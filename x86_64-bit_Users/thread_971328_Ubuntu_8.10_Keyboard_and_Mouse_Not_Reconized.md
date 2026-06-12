---
title: "Ubuntu 8.10 Keyboard and Mouse Not Reconized"
date: 2008-11-04
forum: x86 64-bit Users
---

### Post by fattymatty on 2008-11-04
I wiped my hdd and installed 8.10 and went thru and works good except i cant get to reconize keyboard. I've tried editing xorg.conf file but that came back as error so deleted that. did the console reconfigure of keyboard but to no avail and also today tried sudo apt-get install xserver-xorg-input-all but it said it was all ready upto date. any ideas

Matt

PS Also have tried ms curve keyboard and ms usb mouse as well. currently using compaq ps/2 keyboard and usb ms laser 6000

---

### Post by Yellow Pasque on 2008-11-04
How did you edit your xorg.conf without a keyboard? :P

Is it a USB keyboard? (If so, does this list your keyboard?)
```
lsusb
```

---

### Post by fattymatty on 2008-11-04
I launched Live cd and used that to connect to my linux partition and edited it thru the terminal with nano function but when i added

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "keyboard"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
EndSection 

but this cameup with an error and wouldnt load so i removed it
also the keyboard works if i go into recovery

the keyboard is ps/2 

mouse and keyboard work in live cd

---

