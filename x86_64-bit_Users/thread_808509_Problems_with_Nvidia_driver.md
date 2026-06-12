---
title: "Problems with Nvidia driver"
date: 2008-05-26
forum: x86 64-bit Users
---

### Post by x86-64-Scotland on 2008-05-26
Hi,

I have installed the Nvidia driver, (NVIDIA-Linux-x86_64-169.12-pkg2) which seemed to go fine. When I reboot everything seems to work until I get an Nvidia logo for a second, then just as I get to the login screen the monitor goes black. At this point I need to Ctrl+Alt+F1 to get back to the shell, then 'repair the x configuration' from the grub bootloader. 

What config files can I post to help diagnose this issue? Does anyone have any advice?

TIA.

---

### Post by kingtaurus on 2008-05-26
You'll need to post a few configuration and log files. The following would be useful:
/etc/X11/xorg.conf
/var/log/dmesg (or dmesg.0 - which ever corresponds to the failed X session)
/var/log/Xorg.0.log (or Xorg.0.log.old)
/var/log/nvidia-installer.log

Further, why are you using the binary installer rather than the packages stored in the ubuntu repositories?

---

### Post by x86-64-Scotland on 2008-05-27
I will post these logs when I get home (currently working). I tried to use the driver that came with ubuntu but this also did not work, and seemed to leave my system in a bit of a state. Attemping to uninstall it produced an error as the uninstall script references a path which does not exist on an x86-64bit build, at which point it becomes impossible to remove. I created the path and was able to uninstall the driver.

> **kingtaurus said:**
> You'll need to post a few configuration and log files. The following would be useful:
/etc/X11/xorg.conf
/var/log/dmesg (or dmesg.0 - which ever corresponds to the failed X session)
/var/log/Xorg.0.log (or Xorg.0.log.old)
/var/log/nvidia-installer.log

Further, why are you using the binary installer rather than the packages stored in the ubuntu repositories?

---

### Post by Zoja on 2008-05-27
also try envy 

```
sudo apt-get install envyng-gtk
```

---

### Post by x86-64-Scotland on 2008-05-27
Yeah, I had a look at this (I have seen this advice given on various forums) and tried to use it. Actually by downloading the driver myself I seem to have got further than I did when I made a previous attempt using envy. When I used envy I did not get the nvidia logo/flash of login screen (before going blank, as I described), just a blank screen where I would have expected to see the lgoin screen. 

> **Zoja said:**
> also try envy 

```
sudo apt-get install envyng-gtk
```

---

### Post by x86-64-Scotland on 2008-05-27
Hi,

find attached to this post the files requested. I had to compress them as the forum would not allow me to upload the files uncompressed.

> **kingtaurus said:**
> You'll need to post a few configuration and log files. The following would be useful:
/etc/X11/xorg.conf
/var/log/dmesg (or dmesg.0 - which ever corresponds to the failed X session)
/var/log/Xorg.0.log (or Xorg.0.log.old)
/var/log/nvidia-installer.log

Further, why are you using the binary installer rather than the packages stored in the ubuntu repositories?

---

### Post by kingtaurus on 2008-05-27
> **x86-64-Scotland said:**
> Hi,

find attached to this post the files requested. I had to compress them as the forum would not allow me to upload the files uncompressed.

It looks like this might be causing a problem:
```

(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
```

see here: [http://www.nvnews.net/vbulletin/showthread.php?t=106535](http://www.nvnews.net/vbulletin/showthread.php?t=106535)

---

### Post by x86-64-Scotland on 2008-05-28
Thanks for the reply, I too am using an older monitor at the moment. I commented out the Load GLX line, rebooted and crossed my fingers. Sadly this made no difference to my situation and the screen still flicks off after the Nvidia logo disappears and the logon screen is visible for a second or so.

> **kingtaurus said:**
> It looks like this might be causing a problem:
```

(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
```

see here: [http://www.nvnews.net/vbulletin/showthread.php?t=106535](http://www.nvnews.net/vbulletin/showthread.php?t=106535)

---

### Post by kingtaurus on 2008-05-28
Hmmm ... have you tried running the nvidia uninstall script and then using nvidia-glx-new package in the repositories?

---

### Post by x86-64-Scotland on 2008-05-29
Hi,

thanks. I have done this, uninstalled the Nvidia driver, then installed the nvidia-glx-new package the rebooted. On reboot it boots, I get a login screen, but I don't seem to have 2d or 3d hardware acceleration, can't enable 'visual effects', so I don't think this has worked.

> **kingtaurus said:**
> Hmmm ... have you tried running the nvidia uninstall script and then using nvidia-glx-new package in the repositories?

---

### Post by kingtaurus on 2008-05-29
Can you run 
```
 glxinfo 
```
```
 glxinfo | grep direct 
```

and post the output.

---

### Post by x86-64-Scotland on 2008-05-31
Thanks:

glxinfo:

name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x5c 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

glxinfo | grep direct:


Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".



> **kingtaurus said:**
> Can you run 
```
 glxinfo 
```
```
 glxinfo | grep direct 
```

and post the output.

---

### Post by kingtaurus on 2008-06-01
Something really isn't setup correctly (my guess is either the driver module is not inserted into the kernel, X isn't configured properly, or something more mysterious is going on).

Can you post the output of the following commands:
```

lshw -C video

```
```

lsmod | grep nvidia

```

---

### Post by x86-64-Scotland on 2008-06-01
Thanks

lshw -C video:

  *-display UNCLAIMED     
       description: VGA compatible controller
       product: GeForce 8800 GT
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0

lsmod | grep nvidia returns nothing.


> **kingtaurus said:**
> Something really isn't setup correctly (my guess is either the driver module is not inserted into the kernel, X isn't configured properly, or something more mysterious is going on).

Can you post the output of the following commands:
```

lshw -C video

```
```

lsmod | grep nvidia

```

---

### Post by kingtaurus on 2008-06-01
Okay. So it looks like the kernel module is not being inserted ... which is puzzling. Can you please go to System->Administration->Hardware Drivers
and make sure that the Nvidia graphics driver is in use and enabled.

---

### Post by x86-64-Scotland on 2008-06-01
Thanks for this, it says 'No proprietary drivers are in use on this system'

> **kingtaurus said:**
> Okay. So it looks like the kernel module is not being inserted ... which is puzzling. Can you please go to System->Administration->Hardware Drivers
and make sure that the Nvidia graphics driver is in use and enabled.

---

### Post by kingtaurus on 2008-06-02
> **x86-64-Scotland said:**
> Thanks for this, it says 'No proprietary drivers are in use on this system'

I think this means that the nvidia driver is either not installed (or install failed) or not configured properly. Can you do the following (and return the output):
```

sudo aptitude search nvidia

```

Finally attach your current /etc/X11/xorg.conf

---

### Post by x86-64-Scotland on 2008-06-02
Thanks:
sudo aptitude search nvidia:

p   nvidia-cg-toolkit                       - NVIDIA Cg Toolkit Installer                       
p   nvidia-glx                              - NVIDIA binary XFree86 4.x/X.Org driver            
p   nvidia-glx-dev                          - NVIDIA binary XFree86 4.x/X.Org driver development
p   nvidia-glx-dev-envy                     - NVIDIA binary XFree86 4.x/X.Org driver development
p   nvidia-glx-envy                         - NVIDIA binary XFree86 4.x/X.Org driver            
p   nvidia-glx-legacy                       - NVIDIA binary XFree86 4.x/X.Org 'legacy' driver   
p   nvidia-glx-legacy-dev                   - NVIDIA binary XFree86 4.x/X.Org 'legacy' driver de
p   nvidia-glx-legacy-dev-envy              - NVIDIA binary XFree86 4.x/X.Org 'legacy' driver de
p   nvidia-glx-legacy-envy                  - NVIDIA binary XFree86 4.x/X.Org 'legacy' driver   
i   nvidia-glx-new                          - NVIDIA binary XFree86 4.x/X.Org 'new' driver      
p   nvidia-glx-new-dev                      - NVIDIA binary XFree86 4.x/X.Org 'new' driver devel
p   nvidia-glx-new-dev-envy                 - NVIDIA binary XFree86 4.x/X.Org 'new' driver devel
p   nvidia-glx-new-envy                     - NVIDIA binary XFree86 4.x/X.Org 'new' driver      
v   nvidia-kernel-1.0.7184                  -                                                   
v   nvidia-kernel-1.0.8774                  -                                                   
v   nvidia-kernel-169.12                    -                                                   
v   nvidia-kernel-71.86.04                  -                                                   
v   nvidia-kernel-96.43.05                  -                                                   
i A nvidia-kernel-common                    - NVIDIA binary kernel module common files          
p   nvidia-kernel-source                    - NVIDIA binary kernel module source                
p   nvidia-kernel-source-envy               - NVIDIA binary kernel module source                
p   nvidia-legacy-kernel-source             - NVIDIA binary 'legacy' kernel module source       
p   nvidia-legacy-kernel-source-envy        - NVIDIA binary 'legacy' kernel module source       
p   nvidia-new-kernel-source                - NVIDIA binary 'new' kernel module source          
p   nvidia-new-kernel-source-envy           - NVIDIA binary 'new' kernel module source          
p   nvidia-settings                         - Tool of configuring the NVIDIA graphics driver    
p   nvidia-xconfig                          - The NVIDIA X Configuration Tool   

TIA 


> **kingtaurus said:**
> I think this means that the nvidia driver is either not installed (or install failed) or not configured properly. Can you do the following (and return the output):
```

sudo aptitude search nvidia

```

Finally attach your current /etc/X11/xorg.conf

---

### Post by kingtaurus on 2008-06-02
Okay. So it looks like the xorg.conf is configured properly (although the screen resolution is a little odd ... this can be dealt with by installing and using nvidia-settings or nvidia-xconfig ... or by hand). The aptitude response shows me that you have the proper things installed (although I don't know if its been correctly installed). First lets check the module you are using isn't currently being blacklisted:
```

grep nvidia_ /etc/modprobe.d/blacklist* 

```
If this returns nothing then the module is not blacklisted (which is good). Lets check that the module is installed properly next:
```

modprobe -l | grep nvidia

```
If this returns something like this: 
/lib/modules/2.6.24-17-generic/volatile/nvidia.ko
/lib/modules/2.6.24-17-generic/volatile/nvidia_legacy.ko
/lib/modules/2.6.24-17-generic/volatile/nvidia_new.ko
/lib/modules/2.6.24-17-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/2.6.24-17-generic/kernel/drivers/char/agp/nvidia-agp.ko

Then the drivers are probably installed properly (if unsure about the response from your machine, please post the response to the above command before proceeding).

Lets try and insert the module (warning this can cause the computer to lock up if something goes wrong, so save all your data):
```

sudo insmod nvidia

```
If this crashes the computer ... either the module is not configured properly or installed properly ... we will cross this bridge later.

---

### Post by x86-64-Scotland on 2008-06-02
Thank you for your prompt, detailed reply:
```

modprobe -l | grep nvidia
/lib/modules/2.6.24-16-generic/volatile/nvidia_legacy.ko
/lib/modules/2.6.24-16-generic/volatile/nvidia_new.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/video/nvidia.ko
/lib/modules/2.6.24-16-generic/kernel/drivers/video/nvidia/nvidiafb.ko

```
I don seem to have an nvidia.ko

```

sudo insmod nvidia
insmod: can't read 'nvidia': No such file or directory

```

> **kingtaurus said:**
> Okay. So it looks like the xorg.conf is configured properly (although the screen resolution is a little odd ... this can be dealt with by installing and using nvidia-settings or nvidia-xconfig ... or by hand). The aptitude response shows me that you have the proper things installed (although I don't know if its been correctly installed). First lets check the module you are using isn't currently being blacklisted:
```

grep nvidia_ /etc/modprobe.d/blacklist* 

```
If this returns nothing then the module is not blacklisted (which is good). Lets check that the module is installed properly next:
```

modprobe -l | grep nvidia

```
If this returns something like this: 
/lib/modules/2.6.24-17-generic/volatile/nvidia.ko
/lib/modules/2.6.24-17-generic/volatile/nvidia_legacy.ko
/lib/modules/2.6.24-17-generic/volatile/nvidia_new.ko
/lib/modules/2.6.24-17-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/2.6.24-17-generic/kernel/drivers/char/agp/nvidia-agp.ko

Then the drivers are probably installed properly (if unsure about the response from your machine, please post the response to the above command before proceeding).

Lets try and insert the module (warning this can cause the computer to lock up if something goes wrong, so save all your data):
```

sudo insmod nvidia

```
If this crashes the computer ... either the module is not configured properly or installed properly ... we will cross this bridge later.

---

### Post by kingtaurus on 2008-06-02
Hmmm ... that is puzzling. Lets try something simple (reinstalling the drivers and making sure the restricted-modules get installed) and then proceed:

```

sudo aptitude reinstall linux-restricted-modules-generic nvidia-glx-new

```

---

### Post by x86-64-Scotland on 2008-06-02
```

sudo aptitude reinstall linux-restricted-modules-generic nvidia-glx-new

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
The following packages will be REINSTALLED:
  linux-restricted-modules-generic nvidia-glx-new 
0 packages upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded.
Need to get 26.4kB/9397kB of archives. After unpacking 0B will be used.
Writing extended state information... Done
Get:1 http://ubuntu.virginmedia.com hardy/restricted linux-restricted-modules-generic 2.6.24.16.18 [26.4kB]
Fetched 26.4kB in 0s (101kB/s)                        
(Reading database ... 101652 files and directories currently installed.)
Preparing to replace linux-restricted-modules-generic 2.6.24.16.18 (using .../linux-restricted-modules-generic_2.6.24.16.18_amd64.deb) ...
Unpacking replacement linux-restricted-modules-generic ...
Preparing to replace nvidia-glx-new 169.12+2.6.24.12-16.34 (using .../nvidia-glx-new_169.12+2.6.24.12-16.34_amd64.deb) ...
Unpacking replacement nvidia-glx-new ...
Setting up linux-restricted-modules-generic (2.6.24.16.18) ...
Setting up nvidia-glx-new (169.12+2.6.24.12-16.34) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done 

```

Do I need to reboot now?

---

### Post by kingtaurus on 2008-06-02
Yes. Hopefully this will clear up the issue. If it doesn't ... I'm starting to think a re-install of Hardy might clear this up (I hate recommending this and hopefully you setup the computer with a seperate home directory).

---

### Post by x86-64-Scotland on 2008-06-02
I rebooted and I got a message that said something like 'kinit could not find resume image' the screen flashed a few times and then I was presented with the 'low graphics mode'. I have been here a few times and whenever I select the nvidia driver gnome starts, at a reduced resolution, I dont think the Nvidia driver is in use.

> **kingtaurus said:**
> Yes. Hopefully this will clear up the issue. If it doesn't ... I'm starting to think a re-install of Hardy might clear this up (I hate recommending this and hopefully you setup the computer with a seperate home directory).

---

### Post by kingtaurus on 2008-06-02
> **x86-64-Scotland said:**
> 
```

sudo insmod nvidia
insmod: can't read 'nvidia': No such file or directory

```

Arg ... made a stupid mistake (sorry). This should have been 
```

sudo modprobe nvidia

```

Now I just feel dumb.

---

### Post by x86-64-Scotland on 2008-06-02
Thanks
```

sudo modprobe nvidia
FATAL: Could not open '/lib/modules/2.6.24-16-generic/kernel/drivers/video/nvidia.ko': No such file or directory

```

sorry about all this

> **kingtaurus said:**
> Arg ... made a stupid mistake (sorry). This should have been 
```

sudo modprobe nvidia

```

Now I just feel dumb.

---

### Post by kingtaurus on 2008-06-02
Okay ... you don't have an entry in modprobe relating to nvidia ... darn. I'm guessing that you might have to reinstall Hardy (I can't think of anything else - check [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") they might have some other suggestions that I haven't mentioned).

Further, this might be something related to the fact that the newest nvidia graphics cards are just beginning to be supported. I guess you might want to try envyng-gtk to install the driver (you might have to enable the proposed repositories to get access to the latest drivers).

---

### Post by x86-64-Scotland on 2008-06-03
Thanks,

I have reinstalled 8.04 and am back at the stage where I added the restricted driver when prompted to do so, however after a reboot i don't get a login screen, just a black screen.

> **kingtaurus said:**
> Okay ... you don't have an entry in modprobe relating to nvidia ... darn. I'm guessing that you might have to reinstall Hardy (I can't think of anything else - check [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") they might have some other suggestions that I haven't mentioned).

Further, this might be something related to the fact that the newest nvidia graphics cards are just beginning to be supported. I guess you might want to try envyng-gtk to install the driver (you might have to enable the proposed repositories to get access to the latest drivers).

---

### Post by Apfelmaennchen on 2008-06-03
Hi,

is there anyone who has solved this issue yet?
It is pretty annoying if you find yourself in front of a 19" tube getting a headache because of the meager 60 Hz it is flashing at you...

Cheers,
A

---

### Post by Victormd on 2008-06-03
Have you seen this [NVIDIA how to]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")?

If that doesn't work, you can also get some tips [here]("http://www.stchman.com/video_drivers.html").

---

### Post by x86-64-Scotland on 2008-06-03
this link does not mention hardy (8.04), is the advice still valid? > **Victormd said:**
> Have you seen this [NVIDIA how to]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")?

If that doesn't work, you can also get some tips [here]("http://www.stchman.com/video_drivers.html").

---

### Post by Spyplane on 2008-06-03
Any idea if today's nvidia-driver update fixes any of the current known problems?   I have installed ubuntu hardy on 4 machines now, and my latest machine cannot have the nvidia-driver enabled because all it does is flicker on login.   Mysteriously if I start nvidia-settings and change anything and hit apply it stops flickering (for the most part).   But getting that open is hard considering I have to find my mouse pointer with a constant flicker.  

Oh and by flicker I mean that my monitor goes to power save mode repeatedly.   Oh and I have a 7800 card with dual DVI so it is a known issue apparently.

---

### Post by kingtaurus on 2008-06-03
A lot of the advice is still valid ... but if you are unsure ask in theses forums and someone might be able to answer your questions.

---

### Post by x86-64-Scotland on 2008-06-03
Ok,

I have reinstalled 8.04 (64 bit) from CD, installed the 123 updates when I was prompted to do so, then enabled the nvidia driver via 'System'->'Administratoion'->'Hardware Drivers'. On reboot, where I should get a login screen I get a blank screen.

Please find attached my nvidia-bug-report.log which should contain all of the pertinent info.

> **kingtaurus said:**
> A lot of the advice is still valid ... but if you are unsure ask in theses forums and someone might be able to answer your questions.

---

### Post by kingtaurus on 2008-06-03
Just looking through the log report, this is interesting:
(WW) NVIDIA(0): The EDID for Smile (CRT-0) contradicts itself: mode
(WW) NVIDIA(0):     "1280x1024" is specified in the EDID; however, the EDID's
(WW) NVIDIA(0):     valid HorizSync range (28.000-69.000 kHz) would exclude
(WW) NVIDIA(0):     this mode's HorizSync (80.0 kHz); ignoring HorizSync check
(WW) NVIDIA(0):     for mode "1280x1024".

I would guess that your screen should be at 60 kHz for HorizSync. Sometimes when monitors are set to have a Sync rate that is too high it causes the monitor not to display anything. This could be the cause of your problem.

---

### Post by x86-64-Scotland on 2008-06-04
So is this something that I can fix in the xorg.conf or is this a hardware issue. It is an old monitor.

> **kingtaurus said:**
> Just looking through the log report, this is interesting:
(WW) NVIDIA(0): The EDID for Smile (CRT-0) contradicts itself: mode
(WW) NVIDIA(0):     "1280x1024" is specified in the EDID; however, the EDID's
(WW) NVIDIA(0):     valid HorizSync range (28.000-69.000 kHz) would exclude
(WW) NVIDIA(0):     this mode's HorizSync (80.0 kHz); ignoring HorizSync check
(WW) NVIDIA(0):     for mode "1280x1024".

I would guess that your screen should be at 60 kHz for HorizSync. Sometimes when monitors are set to have a Sync rate that is too high it causes the monitor not to display anything. This could be the cause of your problem.

---

### Post by dcstar on 2008-06-04
> **x86-64-Scotland said:**
> So is this something that I can fix in the xorg.conf or is this a hardware issue. It is an old monitor.

Try this:

```
sudo nvidia-xconfig --no-use-edid-freqs
```

---

### Post by Plasma_NZ on 2008-06-04
How are u installing the nvidia driver.. ? i'll list how i installed mine..

1. Download the new driver - 173 or something now..
2. ctrl + alt + f1
3. login
4. ```
sudo /etc/init.d/gdm stop
```
5. change to folder that the drivers located in
6. ```
sudo sh NVIDIA-driver-package-name
```
7. let it do its thing, follow its options.. dont let it download a kernel module, make it compile one for you.
8. ```
startx
```
9. ```
sudo nvidia-xconfig
```
10. once logged in in low gfx mode do ```
sudo nvidia-settings
```
11. change settings etc.. 


Hope's this helps...

I used to have your problem, and this is how i solved it.. hope it helps..

---

### Post by Spyplane on 2008-06-04
> **Spyplane said:**
> Any idea if today's nvidia-driver update fixes any of the current known problems?   I have installed ubuntu hardy on 4 machines now, and my latest machine cannot have the nvidia-driver enabled because all it does is flicker on login.   Mysteriously if I start nvidia-settings and change anything and hit apply it stops flickering (for the most part).   But getting that open is hard considering I have to find my mouse pointer with a constant flicker.  

Oh and by flicker I mean that my monitor goes to power save mode repeatedly.   Oh and I have a 7800 card with dual DVI so it is a known issue apparently.

BTW, the newest updates fixed my problem with the flickering.

---

### Post by x86-64-Scotland on 2008-06-04
Thanks for this, and all of the other posts today giving advice. I shall try when I get home.
> **Spyplane said:**
> BTW, the newest updates fixed my problem with the flickering.

---

### Post by x86-64-Scotland on 2008-06-08
Ok,

I have tried all of the above, including various reinstalls, and I have no joy, the monitor flickers, the login screen is presented for a second (well, less than a second) and the screen goes black.

I think I am going crazy :P

> **x86-64-Scotland said:**
> Thanks for this, and all of the other posts today giving advice. I shall try when I get home.

---

### Post by tenmoi on 2008-06-08
Scotland,

So your monitor is old. How about another monitor? If after you install another one and the problem exists, then you should continue asking for help. If it solves your problem, the old monitor is to blame.

I once had a monitor which refused to work with the Nvidia driver. I just changed it and had no more headache!

---

### Post by x86-64-Scotland on 2008-06-09
Hi, thanks for the advice, 

I only have access to one more monitor to try, its newer than the one I am currently trying to use, though it is still a 17" CRT with VGA connector, rather than DVI.

I will let you know how I get on.

> **tenmoi said:**
> Scotland,

So your monitor is old. How about another monitor? If after you install another one and the problem exists, then you should continue asking for help. If it solves your problem, the old monitor is to blame.

I once had a monitor which refused to work with the Nvidia driver. I just changed it and had no more headache!

---

### Post by zipppz on 2008-06-09
> the monitor flickers, the login screen is presented for a second (well, less than a second) and the screen goes black.

The same is happening to me, and I even can't see Grub's screen, neither the disk menu when I boot from CD. All i get is a black sreen with the backlight on, and the system running behind. The curious thing is that when rebooting I don't have any problem (except for the grub's screen): I log in in a graphical environment and the X run fine because my monitor doesn't loose signal. But if i turn off my computer for a while, I get the same black screen when booting.No need to say this is most annoying!

I'm not sure if this issue is directly related to the nvidia driver, or perharps it is an ACPI or a kernel issue, since it happens too in Debian Lenny with kernel 2.6.25...? I've been messing around with the nvidia drivers and grub's mnu.lst for two months and now i realize that I don't even know the nature of the problem. Anyway, i think a temporary solution might be going back to Ubuntu 7.10

AMD Athlon x64, Ubuntu Hardy x64, GeForce 8600 GT, LCD ViewSonic VX922

---

### Post by x86-64-Scotland on 2008-06-09
Well, I changed the monitors over, and it works fine. Thanks for your help everyone

> **tenmoi said:**
> Scotland,

So your monitor is old. How about another monitor? If after you install another one and the problem exists, then you should continue asking for help. If it solves your problem, the old monitor is to blame.

I once had a monitor which refused to work with the Nvidia driver. I just changed it and had no more headache!

---

### Post by kingtaurus on 2008-06-09
Congrats on solving the problem :).

---

### Post by Spyplane on 2008-06-11
Maybe I missed this earlier, but does your video card have two dvi outs?   If so, try hooking your original monitor to the other DVI port and see if that works.   I had forgotten that when I got the update that fixed my issue, at the same time I switched which DVI port I was using.   Thinking about it today, i don't really know if the update fixed my problem or if switching ports did.   I'm at work now, so I can't really test it, but if you don't want to be forced to use an old CRT, you might want to try switching ports.

---

