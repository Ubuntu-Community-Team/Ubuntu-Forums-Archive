---
title: "Installed program on Playonlinux?"
date: 2015-06-02
forum: Wine
---

### Post by Samir_Ahuja on 2015-06-02
Hello all.
I have installed playonlinux on my laptop. I want to play FIFA 12 on it.
I have the files but not the setup. You see, I lost the setup files and all I have is the installed game on another PC.
I have copied the installed game but how do I install it now?

---

### Post by alex393 on 2015-06-03
Hi,

**1.** Go into PlayOnLinux. Choose install, and in the lower left corner press "install unsupported application". Choose a name for the wine prefix and leave everything else default. When it prompts to browse for an install file just press cancel.
**2.** You now have a wineprefix created in "PlayOnLinux's virtual drives" (its name is the one you chose in the beginning), Copy your Fifa 12 into PlayOnLinux's virtual drives/nameofwineprefix/drive_c/program files/
**3.** Go into PlayOnLinux press configure. On the left side choose your wineprefix, and press in the middle "Make a shortcut from this virtual drive" choose the fifa12.exe or whatever, and then your game will be displayed in playonlinux.
**4.** Try to launch it, and see if the game works in Linux.

---

### Post by Samir_Ahuja on 2015-06-04
Thanks a lot! It worked!

---

