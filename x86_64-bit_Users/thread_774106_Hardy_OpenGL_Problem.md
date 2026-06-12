---
title: "Hardy OpenGL Problem"
date: 2008-04-29
forum: x86 64-bit Users
---

### Post by kogos on 2008-04-29
I am using Ubuntu for over a year now with no problems at all, and i recently installed 8.04 LTS. I installed all appropriate drivers, added medibuntu repos, enabled restricted drivers, installed wine to play world of warcraft, and started to play with my new distro... then BOOM...

When i tried to enable world of warcraft in 4x multisampling 24bit mode (playing it with -opengl), the system locks when i left click or move the mouse wheel. The keyboard and the mouse is not responding, although the game is not crashing (i see other ppl moving around me). The only way to reboot is SysRq+Alt+B... 

I thought that this was a wine bug (0.9.60) and decided to use 1x multisampling until a new wine release will be available. 

Then i installed googleearth from medibuntu repos (uses openGl as well) and opened instant messenger. There was an image loaded in the background within googleearth, and when i tried to click on the messenger, the system was locked again... no mouse movement, no keyboard/mouse response... only SysRq+Alt+B could work again :( So it had nothing to do with wine, but only with hardy and/or my video card. 

I guess it has something to do with openGL... i tried the above with 3d effects enabled and disabled... but the problem remains. Everything was working great in 7.10. I got restricted drivers enabled and i did not use any additional driver/softare from nvidia. 

I am using the following system: 

CPU: amd3800+ (not dual core)
VGA CARD: nvidia 7900 (GeForce7 chipset)
2GB ram

Any help would be appreciated... is this a known bug, is this only my problem? This is kinda urgent since those lock-ups are not good for my hard drives... Thanks in advance for your time!

---

### Post by sedition on 2008-04-29
Funny, it seems we both posted similar problem at the same time, but I in the wine forum (no response yet): [http://ubuntuforums.org/showthread.php?t=774087](http://ubuntuforums.org/showthread.php?t=774087)
I can get WoW to run with resolution @ 1680x1050 with all the settings minimized and no antialiasing override enabled in nvidia-settings. Unfortunately, I only get about 10 fps with these spartan settings. The strange thing I noticed, is that after a fresh Ubuntu login, glxgears runs at about expected speed. After starting and quitting WoW, then rerunning glxgears, the fps drops by over 50% until you relog into Ubuntu again.

---

### Post by kogos on 2008-04-29
i'm affraid your problem is not the same as mine... I never said i had fps or performance problems... I have complete mouse and keyboard lock up... Everythings works gr8, performance wise... 

Also, my problem has nothing to do with wine in my opinion... cause the "lock up" occures even when not playing wow... It occures with certain programs that are trying to use OpenGL, not through wine necesseraly....

thanks for postin though

---

### Post by sedition on 2008-04-29
I was trying to iterate that there is OpenGL prob's, but no worries. I've been doing some research while at work and came across a few things I intend on trying when I get home tonight. Namely, verify that the restricted driver installed the correct software (i.e. the amd64 libraries rather than the standard 32 bit ones as well as the amd64 driver).  Have you tried another version of the nvidia driver?
Also, when trying to get an older nvidia card to work in another box, I remember having a problem with lockups. If I recall correctly, it was the xorg.conf and had to do with the disabling the dri option and enabling glx. Hope it helps!

---

### Post by kogos on 2008-04-30
i solved it... by installing older drivers in Hardy... 

What i did was: 

1) installing build-essential (with synaptic if u want:) for compiling the driver) 
2) downloaded nvidia's driver version 100.14.19 from nvidia's archive ([http://www.nvidia.com/object/linux_amd64_display_archive.html](http://www.nvidia.com/object/linux_amd64_display_archive.html))
3) Uninstall nvidia-glx-new with synaptic (this is the default Ubuntu restricted driver) 
4) log off and then press Ctrl+Alt+F1 for command mode and log on with command prompt
5) type "sudo killall gdm" (kills desktop manager processes) 
6) go to the folder you downloaded the driver, and type "sudo sh NVIDIA-Linux-....." (this is the filename). You will be asked one or two questions, and BOOM.... reset and you are ready. 

This is easier than it looks in this post... i just went through all the steps so even new users of Ubuntu can solve this... I hope this helps

I hope to see better support with some new nvidia driver in the future... for now i am staying with the old ones

---

### Post by olmari on 2008-04-30
Also read this I just discovered when I had an massive problems with nvidia GPUs and 64-bit Hardy: [http://ubuntuforums.org/showthread.php?t=776362](http://ubuntuforums.org/showthread.php?t=776362)

---

### Post by kogos on 2008-05-02
I saw in forum that there are some nvidia users that had a problem with the xorg file not saved, or the resolution is crappy after restarting the system with the old nvidia drivers... I managed to reproduce this problem on a fresh Hardy installation... without enabling restricted drivers, and without installing the buggy 169.12 default ubuntu driver, i decided to install an older nvidia driver, but after restarting the system, i couldn't get the driver to load, ending up with crappy resolution...

The solution to this is simple... you need to enable restricted drivers, install the buggy 169.12 driver, then uninstall nvidia-glx-new. Then follow the steps above...

I also found that in some computers, step 5 might screw up things... so it's better to use "sudo /etc/init.d/gdm stop" command to stop gnome. Then, after installing the driver use "sudo /etc/init.d/gdm start" to restart it. No need to restart the system, and it's better not to restart it. 

When gnome gets back on, run "nvidia-settings" and make a new xorg.conf file (there is an option there to do it for u). That's it.

So, to sum up and make it easier: 

1) enable restricted drivers (restart if needed)
2) install build-essential
3) uninstall nvidia-glx-new and restart (don't disable restricted drivers, just uninstall nvidia-glx-new and restart)
4) log in to your system with crappy resolution, and press Ctrl+Alt+F1
5) type "sudo /etc/init.d/gdm stop" (stops gnome processes)
6) install the driver u downloaded with "sudo sh NVIDIA-Linux-....."
7) type "sudo /etc/init.d/gdm start" (to start gnome)
8 ) run "nvidia-settings" in terminal and save a new xorg.conf file (maybe "sudo nautilus" could be used to replace the old xorg file in /etc/x11/xorg.conf)

that's it....

---

### Post by chrisccoulson on 2008-05-02
I had the same issues with OpenGL apps in Hardy with the 169.12 drivers, and I reported it as [bug 209354]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/209354") 

I found a solution for me though, which was to add:
```
Option "UseCompositeWrapper" "True"
```
..to the Screen or Device section of my xorg.conf.

kogos: Are you using FSAA in Compiz? If so, could you please try again with 169.12 drivers and see if this option fixes it? If it does, then maybe this option should be added by default by the restricted drivers manager.

---

### Post by kogos on 2008-05-02
i tried that with all the driver version newer than 100.14.19, and in all cases it didn't work... I load warcraft, i then left click on anything, and mouse/keyboard are locked. So, i'm back to 100.14.19 now... i think it has to do with the way opengl works with the new driver.

---

### Post by sonicb00m on 2008-06-21
Opengl does not work for me either in Hardy 64. Latest Nvidia driver being used too.

---

### Post by kogos on 2008-06-23
the only thing that worked for me is roll back to older drivers as i described above:( too sad:(

---

### Post by rickyrockrat on 2008-11-25
I thank God that I stopped buying Nvidia hardware. When my last box locked with a Nvida GPU, I started buying Intel based GPUs. It's funny, there are Xorg driver issues before Intrepid with OpenGL and the intel drivers, but they are rock solid now. Blender runs great on both my Intel boxes.

I realize this doesn't help those of you still with Nvidia's chips, but perhaps it will influence future purchases!  I try to say it with my money!

---

