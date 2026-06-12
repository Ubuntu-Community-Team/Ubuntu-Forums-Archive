---
title: "Ubuntu 6.06/6.10 + 6600GT = Barf"
date: 2007-04-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Thraxarious on 2007-04-03
I'm not sure what the heck is going on here.

I've got a workstation and installing with a 6600GT video card itself is a chore. At times I've managed to choose a resolution and have it actually readable, but often enough it goes into some wierd video mode with green lines down the screen, or all the pixels scrunched up top like its using the pixels in a long stream, but only the resolution for a smaller screen inside a larger one, so its all striped funny.

When its completely bonko, its green lines, funny video mode, and when I try to Ctrl-Alt-F1 to get to a terminal, the mode is messed up and I can't read any text. Its normal grey, but all the screen has lines down and text is blocks.

 I know this card worked fine before. and I've mucked about with it, gone into vesa mode, etc and its worked okay...  but soon as I get into X and the nv driver... it barfs. I had trouble with a FX5500 as well, but not so much. I think its also given me trouble with the Nvidia driver and once strangely, the vesa driver.

I'm kind of going crazy here. I had to stuff a Matrox M2 in there earlier to see if I could fake it to install LinuxMCE... but trying to switch things back to the Nvidia driver after installing most everything with the other card was no easy chore for me.

Is there some really bad incompatibility with some 6600GT cards that it decides to dump them into some crazy text only mode instead of a graphical one?

I'm finding LinuxMCE to be very hard to install, since when I get the card to work, linuxMCE decides to redo the video setup for itself and I get the same trouble, only worse since I haven't been able to fix it. It basically wants config during its driver hissy fit.

---

### Post by warp99 on 2007-04-10
I had the same problem with my 6200 card (same graphics engine). Go in your BIOS and switch to 4x mode instead of 8x. The problem should be fixed and the nvidia drivers should run, but first place this option switch in your xorg.conf file:

**sudo gedit /usr/X11/xorg.conf**

```

Section "Device"
        Identifier   "nVidia Corporation NV43 [GeForce 6200]"
        Driver       "nvidia"
        BusID        "PCI:1:0:0"
        **Option       "NvAGP"                    "2"**
```

To enable fast writes and side bus addressing do the following:

**sudo gedit /usr/modprobe.d/options**

Then add this code to the bottom:

```
# Enable AGPGART fast writes and side bus addressing for nvidia
options nvidia NVreg_EnableAGPFW=1
options nvidia NVreg_EnableAGPSBA=1

```  

After that just restart X and you should be fine. I believe the problem has something to do with using AGPGART which is compiled into the kernel for x86_64 instead of using NVagp.  :)

---

