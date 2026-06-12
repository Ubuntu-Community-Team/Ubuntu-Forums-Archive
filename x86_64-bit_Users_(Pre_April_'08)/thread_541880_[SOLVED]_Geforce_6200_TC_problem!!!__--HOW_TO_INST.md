---
title: "[SOLVED] Geforce 6200 TC problem!!!  --HOW TO INSTALL NVIDIA DRIVERS ON FEISTY64"
date: 2007-09-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by gdaman on 2007-09-03
Hi,
I'm using Winfast Geforce 6200 TC (up to 128 mb ram supported), on ubuntu 7.04 amd64. I downloaded nvidia drivers for linux x64 for geforce 6x (from nvidia.com), booted my system into root with no gui, typed
/sh NVIDIA-Linux-x86_64-100.14.11-pkg2.run
and the installation went something like this:
1. You are in phase 3 (or something like that) the driver might not install correctly in this phase, you need to be in phase 1... Continue? Yes / No. YES
2. Would you like to install opengl32 drivers? YES
3. Would you like to connect to nvidia ftp to look for appropriate kernel? YES
  --- no appropriate kernel found
4. Would you like nvidia driver to set xorg.conf? YES

Then I rebooted, and system crashed (something about xorg.conf, you know). Then I tried to set xorg.conf manually with some dpkg command I found in forums, I set vendor to nvidia... didn't worked.. I set to nvidia with unknown device (Or default was)... didn't worked either... tried to set vendor to nv with  both default (or unknown device) and Geforce 6200 TC... also didn't worked.
What should I do? Was the installation correct, or the driver didn't worked for my card?
Maybe I should buy new card?

I'm using nvidia-glx driver now but it's not good for me--it's slow, tried also nvidia-glx-new... they were very very slow... so I stick with nvidia-glx for now.

Can you tell me how to install it correctly, or what should I do, to do it correctly??
I tried several times and had to start by reinstalling ubuntu all over, so I don't want to miss again

---

### Post by RavanH on 2007-09-03
Have you tried Envy yet? See [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) for more info and download...

---

### Post by auzboo on 2007-09-04
I'm having the same problem as you.  I just bought a HP DV2419US (notebook).  It has a geforce go 6150.  

I tried everything.  I finally got it working with the 100.14.11 drivers direct from nvidia.  Just followed their steps to install.  Then i downloaded the latest patch.  Ever since then i have been getting the same error msg you get.

I did some searching on here to reconfigure the system to use the NV drivers instead of the nvidia drivers.  That kinda worked but the screen was all jumpy and well just horrible.  Decided i would try to install the 100.14.11 driver again. However, still had the same problem.  

Unfortuntally, I have to go back to vista until I see that there is support for my card... maybe you will have better luck since yours isnt a geforce go card.

---

### Post by jocko on 2007-09-04
@gdaman:
I'm not sure about this, but as the installer asked if it should download an appropriate kernel, it looks like you may be missing some important packages that are needed in order to build the nvidia drivers.
My guess is that you need at least "build-essential" and "linux-headers-generic".
Another problem is that even if you have uninstalled nvidia-glx or nvidia-glx-new, the kernel modules for those drivers will still be left and conflict with your newer driver.
But I think envy will take care of both of these problems for you (see RavanH's post above).


@auzboo:
What "patch" did you install? A new kernel perhaps?
If you install a driver manually you need to rebuild it every time the kernel gets updated.
This is why it's so good to have the repos and the apt system, it will make sure the driver gets updated alongside the kernel, provided you installed the driver from the repos.
If you use envy (see the link in RavanH's post above), the "manual" install is automated, so instead of removing and reinstalling the drivers using nvidias installer, you just start envy and let it do it for you.

Both of you: nvidia-glx-new should be a pretty good driver for your cards. Unless the version in nvidia-glx-new (1.0-9755) have some issue with your cards, or if you happen to know/think the newer driver (100.14.11) will perform better, the easy fix is to stay with nvidia-glx-new.

---

### Post by gtdaqua on 2007-09-04
I am having NVIDIA Quadro NVS 210S and everything was fine until this morning. I installed nvidia-glx-new to get Google Earth working and it worked. After restart, i.e today morning I was only left with a white cursor on a white background! 

Tried all steps in this forum (HOWTOs, 100.14.11 guide etc) and other forums but nothing worked! I just reconfigured X-server using dpkg-reconfigure to get the GUI running.

Now I am having problems with flash on browsers!!! KInfo Centre says could not initialize OpenGL device!! 

Can any Ubuntu roast masters jump here please?

---

### Post by gtdaqua on 2007-09-04
I tried these - but no go!

[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html]("http://www.albertomilone.com/latest_nvidia_udsf_feisty.html")

[ How I got the latest NVIDIA 100.14.11 drivers installed ]("http://ubuntuforums.org/showthread.php?t=514161")

---

### Post by gtdaqua on 2007-09-04
Ok. No replies so far!

I have found a solution myself. NVIDIA is trying to setup its own kernel for the running linux version - in order for NVIDIA to achieve this restricted libraries for your running kernel version must be enabled. In my case it is 2.6.20-generic. Once that is installed NVIDIA will compile it correctly. 

Here goes:

1. Enable the 2.6.20-generic restricted libraries from apt-manager
2. Remove exisitng nvidia-glx-new (which was not working anyway)

(You might be asked if 2.6.20-generic libraries must be removed - dont remove it. you are going to need it.)

3. Stop the KDM and exit to command prompt.
4. run the Nvidia installation file. Choose defaults.
5. Start the kdm.
6. You should see the NVIDIA logo and login screen.
7. Login and run "sudo nvidia-settings"
8. Configure the settings you want - resolution, refresh rate etc and click "save to x configuration file". Saving is important. Dont select the merge option while saving. Just save and let a new file be created.
9. Reboot to see if this working.

For me, sadly, when I rebooted the first time, i was shown the command prompt and not GUI! I had to do the installation again (because i did not do step 8 the first time).

I have done all steps now and will now restart to see if everything is ok.

Ubuntu masters! We need simple solutions for a lot of problems. I mean, if this was Windows, I would have fixed this already...

---

### Post by gtdaqua on 2007-09-04
No good. Rebooting the system and KDM doesnt load. I can only see the cursor blinking on top left.

I have to redo the NVIDIA setup again from step 3 and then it works! I dont know why. Can anybody help here please?

---

### Post by jocko on 2007-09-04
@gtdaqua:
Do you mean you are trying to install the nvidia drivers downloaded from nvidia.com, or are you trying the drivers from the repos?

If you want to use drivers from nvidia, you need to make sure the version in restricted-modules is not used.
Either remove the restricted-modules (if you don't have any other hardware that needs them), or prevent them from loading the nvidia driver.
The latter can be done like this:


```
sudo kate /etc/default/linux-restricted-modules-common
```And change the last line to:
```
DISABLED_MODULES="nvidia nvidia_legacy"
```If you don't do this, the nvidia module from restricted-modules will replace your new kernel module after reboot, causing X to fail.

---

### Post by gdaman on 2007-09-04
I'll try Envy and post the result... currently I'm having a internet connection problem. Envy should remove restricted-drivers right? Because I won't need them anyway

---

### Post by jocko on 2007-09-04
> **gdaman said:**
> Envy should remove restricted-drivers right? Because I won't need them anyway

I'm pretty sure they will be inactivated similar to my post above.
I've never tried envy myself, I'm happy with the drivers from the repo...

---

### Post by auzboo on 2007-09-04
ok sorry, Im very new to ubuntu.  What is this repo you talk of?  Im gonna try to install ubuntu again and see if i cant get it working.

/edit heh just figured out what repos means. :)

---

### Post by auzboo on 2007-09-04
ok so i installed the driver you recommended from the repos.  I wasnt able to enable the desktop effects.  I then decided, what the heck, and installed envy and followed their instructions. Well good news is that im getting into the gui. Bad news is that when i try to start the desktop effects it says...."The Composite extension is not available"  anyone know how to fix this? or must i reinstall?

---

### Post by gtdaqua on 2007-09-04
> **jocko said:**
> @gtdaqua:
Do you mean you are trying to install the nvidia drivers downloaded from nvidia.com, or are you trying the drivers from the repos?

If you want to use drivers from nvidia, you need to make sure the version in restricted-modules is not used.
Either remove the restricted-modules (if you don't have any other hardware that needs them), or prevent them from loading the nvidia driver.
The latter can be done like this:


```
sudo kate /etc/default/linux-restricted-modules-common
```And change the last line to:
```
DISABLED_MODULES="nvidia nvidia_legacy"
```If you don't do this, the nvidia module from restricted-modules will replace your new kernel module after reboot, causing X to fail.

Ok. I will do that. Previously I had disabled "nv" and removed that setting too (coz it didnt work) and reverted to default. Let me restart the post u the results.

(I have the latest 64-bit version of 100.14.11 driver from NVIDIA website. Not from repos.)

---

### Post by gtdaqua on 2007-09-05
No luck! I did:
```

DISABLED_MODULES="nvidia nvidia_legacy"

```

and restarted. GUI did not show - only the cursor on top left. Had to hit ctrl+alt+f1 and run the NVIDIA installation again and restarted KDM. 

Then i added "nv" also like this:
```

DISABLED_MODULES="nv nvidia nvidia_legacy"

```

Same result. Should I completely remove restricted modules using apt-get? This morning Adept updater asked me to upgrade 7 packages including restricted modules and headers. They were all in "upgradeable" status before installing them.

Here are the last lines of my Xorg.0.log file until the white cursor point. 

```

(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "1280x1024_75 +0+0; 1280x1024 +0+0; 1024x768 +0+0; 800x600 +0+0; 640x480 +0+0"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

After installing NVIDIA manually (like everytime I have to after reboot) the Xorg.0.log will look:

```

(II) NVIDIA(0): Setting mode "1280x1024_75+0+0"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Keyboard0: Core Keyboard
(**) Option "Protocol" "standard"
(**) Keyboard0: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Keyboard0: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Keyboard0: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Keyboard0: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Keyboard0: CustomKeycodes disabled
(**) Option "Protocol" "auto"
(**) Mouse0: Device: "/dev/psaux"
(**) Mouse0: Protocol: "auto"
(**) Option "CorePointer"
(**) Mouse0: Core Pointer
(**) Option "Device" "/dev/psaux"
(**) Option "Emulate3Buttons" "no"
(**) Option "ZAxisMapping" "4 5"
(**) Mouse0: ZAxisMapping: buttons 4 and 5
(**) Mouse0: Buttons: 9
(II) XINPUT: Adding extended input device "Mouse0" (type: MOUSE)
(II) XINPUT: Adding extended input device "Keyboard0" (type: KEYBOARD)
(--) Mouse0: PnP-detected protocol: "ExplorerPS/2"
(II) Mouse0: ps2EnableDataReporting: succeeded

```

What is the next step here? I have feeling we are narrowing down on the problem now :)

---

### Post by gtdaqua on 2007-09-05
SUCCESS! SUCCESS! SUCCESS!

I got it! The problem was I was applying parts of multiple soultions found in multiple threads. I thought I would remove the modules completely and try and it worked!

Gdaman, 
follow these steps and see if you it works for you. Here is the actual link:

[How I got the latest NVIDIA 100.14.11 drivers installed]("http://ubuntuforums.org/showthread.php?t=514161")
Anyway the solution is as follows:


1. Download the latest NVIDIA driver (currently 100.14.11) from NVIDIA website and save it.
2. Backup your current config
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

```
3. Remove existing nvidia modules and restricted modules.
```

sudo apt-get remove nvidia* linux-restricted-modules*

```
4. Install the following modules: latest linux headers, build-essential, pkg-config and xorg-dev
```

sudo apt-get install linux-headers-$(uname -r) 
sudo apt-get install build-essential 
sudo apt-get install pkg-config 
sudo apt-get install xorg-dev

```
Note: ALL of them must get installed. I had problems with the xorg-dev yesterday and so this solution did not work out at that time. But today I had xorg-dev installed and so NVIDIA simply works now.

5. Stop the desktop manager so that u can run the nvidia installer from terminal.
```

sudo /etc/init.d/kdm stop

```

for gnome use "gdm" instead of kdm. 

6. cd to the directory where you downloaded the 100.14.11 nvidia driver and type
```

sudo sh NVIDIA-Linux-x86_64-100.14.11-pkg2.run

```

Select defaults (like remove existing driver, no precompiled kernel found etc). The installer might some files were not found or cannot be located - simply ignore it. 
(there are some details in the link above - I am not typing those here coz it simply worked for me)

7. simply start the desktop manager.

```

sudo /etc/init.d/kdm start

```

of course use "gdm" for gnome.

You should now see the NVIDIA splash logo and that's it! 

Just to be sure, restart the machine and see if GUI appears automtically. Mine did now and the flash problem also has vanished! 

I will keep a watch on this post (coz i hijacked urs and got mine working and so i will remain here until we sort you out. ok? cheers)

---

### Post by gdaman on 2007-09-05
I tried ENVY, worked fine for me.

---

### Post by gtdaqua on 2007-09-05
so - you have got everything right now? 

If so, you can mark this thread TITLE as SOLVED please.

---

### Post by gdaman on 2007-09-05
So how can I get Desktop Effects working?? when I try enable, windows go black....

---

### Post by gtdaqua on 2007-09-05
what is the resolution u r using? monitor refresh rate? do u think the values there are correct?

---

### Post by gdaman on 2007-09-05
They are good.... when I try to enable desktop effects, start AWN, or compiz-- windows look black, only close, minimize;file,edit;etc are displayed right..........on awn- the down part of the screen is black, only icons are right

---

### Post by gtdaqua on 2007-09-05
oh! so you are using compiz? 

I am not a compiz/beryl expert so far. I dont want to try that out because I am fairly new to Linux and I have been warned too! 

See [this]("http://ubuntuforums.org/showthread.php?t=349732") and [this]("http://ubuntuforums.org/showthread.php?t=363478")

---

