---
title: "Keyboard settings, 3rd level set no hash key?"
date: 2005-10-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by Diaboblop on 2005-10-31
I'm trying to get access to the Hash key but all of what I've read doesn't seem to be working.

I've set up 3rd level access with the alt keys (also tried just the left one, and just the right one)
All that happens is when i press the left alt key and 3, no characters are produced.  If I press the right one, a to the power of 3 number appears (a small number situated slightly above the normal character set).  I tried all the other keys and there was no hash key to be found.

here is my xorg.conf file for the keyboard section, I've tried the XKbSymbols for gb, but that's also a no go.  anyone spot what's wrong?

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
        Option          "XkbKeycodes"   "macintosh"
        Option          "XKbSymbols"    "macintosh/us"
        Option          "XKbGeometry"   "macintosh"
        Option          "XkbOptions"    "ctrl:no caps, lv3: lwin_switch"
        Option          "XkbRules"      "XKb"
        Option          "XkbModel"      "macintosh"
        Option          "XkbLayout"     "gb"
        Option          "XkbOptions"    "lv3:lwin_switch"
EndSection

Cheers

---

