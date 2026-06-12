---
title: "Put ubuntu window around games"
date: 2008-07-24
forum: Wine
---

### Post by Falc7 on 2008-07-24
How do i put an ubuntu style window around my games (using wine)? So i can use them like any other application and prevent them from taking over the whole screen/changing the screen resolution?

Also, how can i edit xorg.conf?

---

### Post by ::: on 2008-07-25
Here's an example for your first question:
```
wine explorer /desktop=default,640x480 "C:\Program Files\Diablo II\Diablo II.exe"
```

For the second question:
```
sudo gedit /etc/X11/xorg.conf
```
don't forget to make a backub of that file first!

---

### Post by Falc7 on 2008-07-30
Thanks very much for your reply!
Continueing the first question, can i change any screen resolution a game play in by altering the template you've shown me?

And with the 2nd one, to turn off dynamic twin view (which i have been told is buggy, and not needed since this is a laptop anyway) should i change the file to
Section "Device"
   Identifier   "Configured Video Device"
   Driver      "nvidia"
   Option      "NoLogo"   "True"
  Option       "DynamicTwinView" "FALSE"
EndSection

---

