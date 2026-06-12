---
title: "Ubuntu 8.1 Nvidia Blank Screen"
date: 2008-12-31
forum: x86 64-bit Users
---

### Post by Agitpropist on 2008-12-31
I installed Ubuntu 8.1 (Ibex) on my PC, the install went through fine, internet and audio works. I tried to install the video drivers (Nvidia 7600 GS) through the restricted driver dialog, and after the system reboots I get a blank screen (No Input Signal).

I can get a command line with CTRL + ALT + F1. I've tried to download the driver from Nvidia's website, it builds it's own kernel module (I'm not sure what that is), and it still gives me a blank screen. I've tried to edit xorg.conf and add "UseDisplayDevice" "DFP", but that doesn't help. I've reinstalled Ubuntu five times and tried different techniques each time to get the video driver to work.

It worked once, but I let the System Update utility run and after the reboot I got a blank screen once again. The only time the video card worked properly was under the 2.6.26-7 Kernel, and after I installed the driver from Nvidia's website (177). Unforntuatly I don't recall exactly what I did to make the video card work for that one brief instance. After I updated (through automatic system updates) to 2.6.26-9 I got a blank screen.

I would like to install Ubuntu to my system, but I need to have the Nvidia driver to work properly in order to get a resolution higher than 800x600, and at 60hz refresh rate. I don't understand why it's so difficult to get a video card to work with this system. I'm coming from Windows and I'd like to switch to Linux but this video card situation is very discouraging.

I'd appreciate some help, thanks.

---

### Post by Hydrid on 2008-12-31
I had the same problem and the solution was to install 8.10 from the cd with no graphics support in the beging of the installation.When u boot from the cd it has an option (i think its f4)to choose to install with generic graphics driver.Hope this helps you.

---

### Post by Agitpropist on 2008-12-31
The only option I see that pertains to the video driver is 'Safe Graphics Mode'. Ubuntu always installs a generic video driver, I've had the generic video driver working and it only gives me a max resolution of 800x600, it's really terrible.

---

### Post by Agitpropist on 2008-12-31
I just tried reinstalling with safe graphics mode, then installed the Nvidia driver and I get the same result, blank screen (No Signal Input). Does Linux really  suck this bad?

---

### Post by Agitpropist on 2009-01-01
Tried running EnvyNG, tried compiling the driver kernel module from  Nvidia...

I understand why Linux users are so skilled, running Linux is like keeping a sinking ship afloat. Maybe that's too harsh, but it shouldn't be this hard to get a video card to work.

Is this a problem with the new kernel? Is it because theres a conflict with Xen Server (which is installed by default, prohibiting the building of the nvidia kernel)?

It's an Nvidia 7600 GS (AGP), pretty standard, why is Linux rejecting it like a kidney transplant gone wrong?

Maybe Ubuntu puts bugs in the distros, after all they make a living by providing tech support.

---

### Post by abn91c on 2009-01-01
remove compiz

---

### Post by DeMus on 2009-01-01
> **Agitpropist said:**
> Tried running EnvyNG, tried compiling the driver kernel module from  Nvidia...

I understand why Linux users are so skilled, running Linux is like keeping a sinking ship afloat. Maybe that's too harsh, but it shouldn't be this hard to get a video card to work.

Is this a problem with the new kernel? Is it because theres a conflict with Xen Server (which is installed by default, prohibiting the building of the nvidia kernel)?

It's an Nvidia 7600 GS (AGP), pretty standard, why is Linux rejecting it like a kidney transplant gone wrong?

Maybe Ubuntu puts bugs in the distros, after all they make a living by providing tech support.


I had the same problems with Hardy Heron 8.04. Installation went fine with the build in driver. When I tried to update that problems started. Finally in one of the threads here somebody told me to use EnvyNG. I re-installed Hardy, installed EnvyNG and now I do have the latest nVidia driver working with no problem at all.
I see you also tried EnvyNG, but without any luck. Was that done after a fresh install? I mean without trying this or that first? If not, try it. Do a fresh re-install, install EnvyNG from using Synaptic and use it.
Hope it works for you. Good luck.

DeMus

---

### Post by abn91c on 2009-01-01
> **DeMus said:**
> I had the same problems with Hardy Heron 8.04. Installation went fine with the build in driver. When I tried to update that problems started. Finally in one of the threads here somebody told me to use EnvyNG. I re-installed Hardy, installed EnvyNG and now I do have the latest nVidia driver working with no problem at all.
I see you also tried EnvyNG, but without any luck. Was that done after a fresh install? I mean without trying this or that first? If not, try it. Do a fresh re-install, install EnvyNG from using Synaptic and use it.
Hope it works for you. Good luck.

DeMus

**[COLOR="Blue"]reinstalling is totally unneccessary[/COLOR]**[B][COLOR="Red"]  read this: [http://ubuntuforums.org/showthread.php?t=1010875](http://ubuntuforums.org/showthread.php?t=1010875)
[/COLOR][/B]

---

### Post by Agitpropist on 2009-01-01
Thanks for the advice everyone. I solved the problem by uninstalling Ubuntu and installing openSUSE instead. So I'm running KDE instead of Gnome. I don't know what it is about the Ubuntu distro, but I had no problems getting my video card to work with openSUSE.

---

