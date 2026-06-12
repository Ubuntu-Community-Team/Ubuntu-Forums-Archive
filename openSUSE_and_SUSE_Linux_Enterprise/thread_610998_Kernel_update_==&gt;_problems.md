---
title: "Kernel update ==&gt; problems"
date: 2007-11-12
forum: openSUSE and SUSE Linux Enterprise
---

### Post by RebounD11 on 2007-11-12
Nothing major, though. The auto updater updated my kerne from 2.6.22.9-0.1-default (or sth like that) to 2.6.22.12-0.1-default.

I've solved the usual problems... uninstalled my previous nvidia drivers and compiled new ones (actually same old ones :D but on an nvidia driver-free system), reconfigurated my VMware, VirtualBox and Cedega apps for the new kernel, recompiled the wireless driver. Everything went smooth (a little to smooth for everything to be OK in the end -- Murphy never sleeps :P).

X Server started and Compiz worked well after reboot (correct resolution, correct refresh rate, correct monitor and GPU names and details and fully functional plugins on both Gnome and KDE), but the performance has gone down... glxgears shows 600+ FPS and it used to be 6500+ FPS with Compiz on, Cedega says I don't have 3D acceleration although I did have it on the old kernel (tried reinstalling fresh - with no file from Cedega left behind be it config file or game folder). Also Xine gives me the error that no sound drivers can be found, sound and video works, only I can't choose any driver, it says none in the driver selection box in Amarok (I used to have ALSA, OSS and some sort of proprietary Asus linux driver for my onboard 5.1 sound card). Cedega also reports that I have no ALSA or OSS installed (which I have installed and reinstalled over and over again) and that despite the fact that I can hear the ingame music and soundFX (the only difference is that I can't do so anymore if I'm listening to music at the same time which easn't a problem before).

Another issue that I left out, now I have to mount USB pendrives manually (terminal/konsole style) since they don't automount anymore, they're not even showed as unmounted drives, and I have the same settings for automounting removable devices (they still work for CD's and DVD's even empty ones, just not for USB pendrives).

So, if anyone has any ideas and would like to share them he/she is welcome to do so. I can provide any other details on request if needed.

PS: I wouldn't like to open a new topic about this but has anyone tried Fedora 8, is it better than OpenSuSE 10.3 for you?

---

### Post by RedDwarf on 2007-11-13
> **RebounD11 said:**
> I've solved the usual problems... uninstalled my previous nvidia drivers and compiled new ones (actually same old ones :D but on an nvidia driver-free system), reconfigurated my VMware, VirtualBox and Cedega apps for the new kernel, recompiled the wireless driver.
There is no need to do so if you use the KMP from the nVidia repository.
> **RebounD11 said:**
> X Server started and Compiz worked well after reboot (correct resolution, correct refresh rate, correct monitor and GPU names and details and fully functional plugins on both Gnome and KDE), but the performance has gone down... glxgears shows 600+ FPS and it used to be 6500+ FPS with Compiz on, Cedega says I don't have 3D acceleration although I did have it on the old kernel (tried reinstalling fresh - with no file from Cedega left behind be it config file or game folder).
if xorg.conf hasn't been modified looks like the kernel module isn't loaded.
> **RebounD11 said:**
> Also Xine gives me the error that no sound drivers can be found, sound and video works, only I can't choose any driver, it says none in the driver selection box in Amarok (I used to have ALSA, OSS and some sort of proprietary Asus linux driver for my onboard 5.1 sound card). Cedega also reports that I have no ALSA or OSS installed (which I have installed and reinstalled over and over again) and that despite the fact that I can hear the ingame music and soundFX
Strange problem, but even more strange your "ALSA, OSS and some sort of proprietary Asus linux driver".
How have you "reinstalled" OSS and ALSA?
> **RebounD11 said:**
> (the only difference is that I can't do so anymore if I'm listening to music at the same time which easn't a problem before).
Probably because you are using the OSS kernel emulation from ALSA.
> **RebounD11 said:**
> Another issue that I left out, now I have to mount USB pendrives manually (terminal/konsole style) since they don't automount anymore, they're not even showed as unmounted drives, and I have the same settings for automounting removable devices (they still work for CD's and DVD's even empty ones, just not for USB pendrives).
Uhm... stange, very strange. Whar "settings" are you talking about?


I don't have a USB pendrive to test. But everything else works correctly here. Well, I'm using ALSA from OBS, but that'e because my sound card isn't fully supported by ALSA 1.0.14.

---

### Post by RebounD11 on 2007-11-14
> **RedDwarf said:**
> There is no need to do so if you use the KMP from the nVidia repository.

Yes it is... X didn't start after reboot.

> **RedDwarf said:**
> if xorg.conf hasn't been modified looks like the kernel module isn't loaded.

The xorg.conf has been regenerated, but it looks the same as the old one (saved that as precaution), and it's still not loaded (kinfocenter isn't showing it loaded)

> **RedDwarf said:**
> Strange problem, but even more strange your "ALSA, OSS and some sort of proprietary Asus linux driver".
How have you "reinstalled" OSS and ALSA?

Yes

> **RedDwarf said:**
> Probably because you are using the OSS kernel emulation from ALSA.

I don't know. How do I find out?

> **RedDwarf said:**
> Uhm... stange, very strange. Whar "settings" are you talking about?

Gnome Control Center --> Removable Drives and Media, I know it's Gnome not KDE, but it's the only place I found options about automounting removable drives. Anyway, settings are set OK, but it doesn't work (KDE, Gnome or Xfce).

---

### Post by Jeff_From_VA on 2007-11-15
I am having the same usb issues - no luck finding anything so far...

---

### Post by RebounD11 on 2007-11-16
I've solved the sound problem... it needed a restart... :D but I'm still working on the video drivers issue, the USB isn't such a big deal, since I find it safer to mount and unmount manually.

RedDwarf said something about the KMP from the repos. It's installed, only it's the old one for 2.6.22.5-30-default, and I can't find another for the new kernel, nor will the nvidia installer compile a correct one, I tried several ways and several times for each way to install the drivers. every time I've completely removed the previous installation and it still shows my kernel module not loaded.

I'll keep trying... If I don't succeed I'll try Fedora 8, I've been meaning to try it for a while now, and if I don't like it it's back to openSuSE, nothing better than a clean install to clear the problems :D

---

### Post by RedDwarf on 2007-11-17
> **RebounD11 said:**
> RedDwarf said something about the KMP from the repos. It's installed, only it's the old one for 2.6.22.5-30-default, and I can't find another for the new kernel
There is no need for a new package.
```
~> rpm -qR nvidia-gfxG01-kmp-default-100.14.19_2.6.22.5_30-1.1
rpmlib(VersionedDependencies) <= 3.0.3-1
kernel-default
x11-video-nvidiaG01 = 100.14.19
/bin/sh
/bin/sh
/bin/sh
rpmlib(PayloadFilesHavePrefix) <= 4.0-1
rpmlib(CompressedFileNames) <= 3.0.4-1
[B]kernel(vmlinux) = 50010dfbe221cfe5
kernel(drivers_i2c) = 619065e2ef882d9c[/B]
rpmlib(PayloadIsBzip2) <= 3.0.5-1
```
This nVidia module works with any kernel version that provides the same "vmlinux" and "drivers_i2c". The last kernel update hasn't changed these parts, so works.
> **RebounD11 said:**
> and it still shows my kernel module not loaded.
So probably logs will say something. But... you have the kernel-source package that match your kernel-default one? ```
rpm -qf /boot/vmlinuz /usr/src/linux
```

---

### Post by RebounD11 on 2007-11-17
Thanx for the reply :D but I changed to Fedora 8 today. No problems so far, and more my wireless seems to have a wider range now, either that or 6 new networks appeared since yesterday in my area :P

I only had 1 problem with it so far, and it wasn't it's fault (nor was it mine, but I don't want to go into the stupidity of others).

I'll keep it to see how it works out... so far it's a little faster than openSuSE 10.3 and like it it recognized everything out of the box, what's more it took 35 minutes from turning on the computer with the live disc in it until I had everything I needed installed and running, which is a new record (even faster than Sabayon where it took me a whole hour to clean up the unnecessary crap it installed).

---

### Post by Incense on 2007-11-17
I'd be interested in hearing your thoughts on fedora vs openSUSE once you've been using it for a week or so. Reading the openSUSE forums, that update really hosed a lot of people, so at least you weren't alone FWIW.

---

### Post by RebounD11 on 2007-11-24
Ok, just switched back to OpenSuSE 10.3 from Fedora 8 (still didn't fix the video problem, but I got my Wireless to go into monitor mode and even if 3D acceleration isn't at its full I still can use it for 99% of the tasks I needed it for, and the remaining 1 % is on its way to me :D).

Here are my pros and cons on Fedora 8 vs OpenSuSE 10.3:
Pros:

OpenSuSE                                                       
- everything works out of the box                        
- Great new artwork for all the DE (Gnome, KDE and Xfce)                     
-More repositories + 1-click install                            
- if you want you can ditch the terminal (good for noobs --> Yast)                    

Fedora
- same here + wireless can do monitor mode
- probably the best artwork for the Gnome DE I've ever seen
- Better organized repos (my opinion)
- Yum is faster then Yast and if you liked Ubuntu it'll feel like home

Cons:

OpenSuSE                                                      
- Damn update, I thought, wow, no more update problems...  Wrong! but fixable (preety easy too)                   
- a little harder to find stuff in it's Wiki page (again maybe I'm dumb not the Wiki)                    
- OpenSuSE menu in both KDE & Gnome, I hate them but can't give them up cause they fit perfectly on the Desktop :D                                 

Fedora 
- ALSA, KDE and all its apps don't work (at least for me), big errors... gave up :(
- Stuck with Gnome and only Gnome
- Very hard to get codecs, and the whole fluendo commercial, I hope they got a big sponsorship 


Conclusion: OpenSuSE wins the fight but the war is not over yet (I hope)... 1% 3D acceleration (opensuse) vs all KDE and no sound in some applications  (fedora)... I choose OpenSuSE for now :D

PS: I hate this Forum (in certain text editing options :D)

---

### Post by RebounD11 on 2007-11-24
> **RedDwarf said:**
> There is no need for a new package.
So probably logs will say something. But... you have the kernel-source package that match your kernel-default one? ```
rpm -qf /boot/vmlinuz /usr/src/linux
```

I think there is a need for some packages... :|

```

rebound11@Tron:~> rpm -qf /boot/vmlinuz /usr/src/linux
kernel-default-2.6.22.12-0.1
kernel-source-2.6.22.12-0.1

```

Tried using the kmp package from the repos... performance went down... tried fresh install of NVidia drivers (clean one with no other drivers loaded at that moment) from the Nvidia website (in both ways, the SuSE way - SuSE tutorial on the site, and the "generic" way) and got the same performance as the old drivers from the repos.

Conclusion: I can't play NFS Carbon or Pro Street any more :| (otherwise no difference :D )

Any other idea is appreciated here or [here]("http://ubuntuforums.org/showthread.php?t=622133"), or anywhere just point me to it :D

---

### Post by Incense on 2007-11-25
> **RebounD11 said:**
> Ok, just switched back to OpenSuSE 10.3 from Fedora 8 (still didn't fix the video problem, but I got my Wireless to go into monitor mode and even if 3D acceleration isn't at its full I still can use it for 99% of the tasks I needed it for, and the remaining 1 % is on its way to me :D).

Here are my pros and cons on Fedora 8 vs OpenSuSE 10.3:
Pros:





Thanks for the list! Just what I was looking for!

---

### Post by RebounD11 on 2007-11-25
You're welcome! :D

---

### Post by RebounD11 on 2007-11-27
I got the framerate and peformance back, with the cost of losing CompizFusion by disabling Composite extension in the xorg.conf :| not sth I would have wanted to do but it's a solution for those who have had this problem and don't use desktop effects.

---

### Post by dca on 2007-11-29
The updates got me good, also.  I restarted my (play) laptop and the menu panels (I don't use slab menu w/ GNOME) on top/bottom only went 3/4 of the ways across the screen and the bottom one was up an inch indicating it's displaying in 1024x768.  However, the wallpaper was still displaying 128x800 and windows can still be dragged all over the screen.  On one of my PC(s) running KDE, all of a sudden a message popped up from the tray indicating problems w/ HAL and it will prevent things from functioning correctly.  I'm still doing a damage report.

---

### Post by RebounD11 on 2007-11-29
I gave up on SuSE for that... I want both CF and ProStreet ... sry SuSE, it will however remain so far the best distro I've had... up until the updates :D

I got Ubuntu 7.10 the 32-bit version to run and it does so flawlessly so far (no kernel update yet :D) ... the 64-bit version didn't bother to start up... some error I'm trying to figure out (I really want 64 bit) so it starts with a giant handicap... to SuSE, or Fedora (which I couldn't get KDE to run) and even Feisty (without wireless).

---

### Post by Incense on 2007-12-02
I'm really happy I didn't get hit by any of these problems. I have not upgrading my desktop to 10.3 yet though because of issues like this. It's not too big a deal if my notebook goes down, but I need my production machine to always be functional. It does blow me away however that the SUSE devs let an update go that broke so many installs.

---

