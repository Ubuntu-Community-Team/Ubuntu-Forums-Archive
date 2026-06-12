---
title: "cpu freq change"
date: 2005-11-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by dragon_mac on 2005-11-20
i there, how can i change the cpu freq, i have a powerbook g4 @ 500MHz but using system information it shows PowerPc 7410 altivec supported at  300Mhz .  i would like to toggle from 300mhz to 500mhz and vice versa i'm running breezy 5.10, every seems to be working fine, fan, airport, graphics, keyboard, HD spins down ok,  sleep and resume fine. any halp would be appreciated .

---

### Post by ssam on 2005-11-21
if it works like mine (1ghz titianium g4 powerbook) then it will automatically step up to full speed when needed.

there is a gnome applet (right click (f12) on the gnome panel, -> add to panel -> cpu frequency scalling monitor) that shows you the current speed. or
```
cat /proc/cpuinfo | grep clock
```
in a terminal.

now do some heavy work, like an image filter in gimp, playing a video etc, and see if it steps up.

---

