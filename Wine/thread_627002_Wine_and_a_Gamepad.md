---
title: "Wine and a Gamepad"
date: 2007-11-29
forum: Wine
---

### Post by arigram on 2007-11-29
Can someone assist me in editing the registry in Wine to get my very basic Logitech Precision gamepad working?

---

### Post by ijason on 2007-11-29
i think you may need to edit your xorg.conf to set up the controller and then it will work across all applications. have you tried using it in linux native programs? so that you know it's configured in native but not through wine? if it isn't configured in native programs then the xorg.conf may be your answer :) if it is working in native apps but not in wine, then i'm afraid i can't help.

---

### Post by arigram on 2007-11-29
I have two gamepads.
The Logitech Precision works fine with all Linux games without needing a set up.
A Logitech Chillstream needs setting up to work.

I have only tried one game in Wine (and one I am interested in), Future Pinball and although it recognizes the presence of a gamepad, none of the buttons work.

From some thread I picked up the advice in editing the Wine registry to add the gamepad, but I have no idea how to do it.

---

### Post by MickLionheart on 2007-11-29
Don't quote me on this but I think wine just reads the linux gamepad configuration.
I know that I set up a gamepad in linux and it just worked in wine automatically.

---

### Post by cogadh on 2007-11-29
Not always, sometimes you need to explain to Wine exactly what your game controller device is. Go to the Wine [Useful Registry Keys](http://wiki.winehq.org/UsefulRegistryKeys) page and scroll down to the section about DirectInput, it basically explains what you need to do.

---

### Post by arigram on 2007-11-30
Apparently I won't be able to get the joypad working as the Wine Registry doesn't seem to help the problem.
Thank you for your answers anyway.

---

### Post by regeya on 2008-11-06
> **arigram said:**
> Apparently I won't be able to get the joypad working as the Wine Registry doesn't seem to help the problem.
Thank you for your answers anyway.

I know it's been a year, but you may need to set the dinput and dinput8 dlls to be builtin rather than native.  iirc if you use winetricks to install DirectX, it sets these to be native.

---

