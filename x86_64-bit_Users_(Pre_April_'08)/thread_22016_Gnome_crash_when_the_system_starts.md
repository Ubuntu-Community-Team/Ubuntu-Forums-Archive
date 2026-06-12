---
title: "Gnome crash when the system starts"
date: 2005-03-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Frafra on 2005-03-25
When I open gnome, it crash. It display only a brown screen and the cursor. The cursor works, but the keyboar doesn't work. I've try 5.04-preview and hoary-array5. What i must do? I use:

amd 64 3500
geforce 6200 (agp)
asus av8 deluxe
1 gb ddr 400
120 gb sata

Excuseme for the bad english.

---

### Post by arctic on 2005-03-25
it could be two things:
first, if you updated your system or use an old account with the new distro (e.g. you switched from suse to ubuntu) then there is most probably a conflict with your gnome config files in your /home account. try to remove the gtk and gnome related hidden folders on your /home partition.
second, have you properly set up your graphic card? it could be caused by false entries in your xorg.conf (or xfree86.conf, whichever you use) file.

---

### Post by Frafra on 2005-03-25
Ah, ok. Thanks. I use /home with suse 9.2. Now I install only ubuntu :D


Thanks.

---

### Post by Frafra on 2005-03-25
Now ÃI''m using lynx for write this post. The error is equal. I've formatted all. Now my hd is:
50 gb /
70 gb /home (only for Ubuntu)
1 gb swap

I've upgraded all the programs and the kenel. What I must do?

---

### Post by Frafra on 2005-03-25
Fantastic! Now it work. I've edit xorg.conf with xorgconfig. How I must to do for work the wheel of the mouse?

---

### Post by arctic on 2005-03-25
no idea... i don't have a mouse wheel. :D maybe someone else can help you with that.

---

### Post by wmcbrine on 2005-03-25
Scroll wheels should be supported automatically. What's your hardware?

For what it's worth, here's my mouse entry from xorg.conf. I'm using a PS/2 Microsoft Trackball:

```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

```

---

### Post by Frafra on 2005-03-26
Thanks! Now it work :D

---

