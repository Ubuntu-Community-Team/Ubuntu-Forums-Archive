---
title: "trouble installing GPU drivers..."
date: 2007-05-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by the2ndtrombone on 2007-05-31
GPU: NVIDIA 7300 GS

ok, so i think i tried everything i could find on here, and it didnt work. didnt work - it said it couldnt find the fileClicking "Enable Driver" in desktop effects and restricted drivers did nothing no matter how many times i clicked it - i think the card isnt supported even though its on the list of known & supported cards here:
 [http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html) 

so i went onto [www.nvidia.com](www.nvidia.com) andf download the linux driver for that card, put it on my desktop and hit "run in terminal". It starts to install happily enough, but then it comes up with an error - "nvidia installer must be run as root". Im a complete newbie with ubuntu and have no idea whats going on. can anybody help me?

---

### Post by RAOF on 2007-06-01
[This howto](https://help.ubuntu.com/community/BinaryDriverHowto) should give you all the info you need.

Failing that, ```
sudo aptitude install linux-generic nvidia-glx-new
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```
should work, but try the howto first.

---

