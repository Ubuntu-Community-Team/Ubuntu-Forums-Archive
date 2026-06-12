---
title: "Problem with ATI drivers"
date: 2005-11-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by Disablez on 2005-11-21
Hi!
I recently tried to add 3D Acc. to my comp (Acer Aspire 1501 with a Radeon 9600 (Mobility M10). So I installed the ATI drivers with the installer from their website. 8.19.10-x86-64, to be precise. 

Everything went ok, configured the xorg.conf file and rebooted with no problem (but for the mouse having a strange white stripe under it during the initial screen of KDE (I installed the kubuntu-desktop), or everytime I click on the Gnome menu bar).

Anyway, I tried to run supertux, just for trying, and it doesnt work. so I tried to run it from konsole, and I get a message saying that it couldnt find the shared library libGL.so.1 .

I found the library, /usr/X11R6/lib/libGL.so.1.2 ,and started making ln -s in all possible /lib  , /lib32, /usr/lib, /usr/lib32, (lib64 are links to lib, so...) even I have tried with creating linked folders /usr/lib/fglrx , /usr/lib/ati-fglrx ... with no luck.

Can anyone tell me where is my system looking for them ? I tried for hours in Google but had no luck finding a solution... :(

---

