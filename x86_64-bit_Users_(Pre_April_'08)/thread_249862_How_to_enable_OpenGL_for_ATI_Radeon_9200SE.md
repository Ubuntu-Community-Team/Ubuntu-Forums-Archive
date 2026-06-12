---
title: "How to enable OpenGL for ATI Radeon 9200SE?"
date: 2006-09-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by kopilo on 2006-09-03
Hi, I'm wondering what is the best and easiest way to enable OpenGL  on my system.

_Specs_
Processor: AMD Athlon 64 3000+
Mother board: ASUS K8V SE Deluxe
Video card: ATI Radeon 9200SE
RAM: 512MB 400 DR

**xorg.conf**
```

Section "Device"
        Identifier      "ATI Technologies, Inc. RV280 [Radeon 9200 SE]"
        Driver          "vesa"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "DV1770FD3"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. RV280 [Radeon 9200 SE]"
        Monitor         "DV1770FD3"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

```

---

### Post by Kilz on 2006-09-03
> **kopilo said:**
> Hi, I'm wondering what is the best and easiest way to enable OpenGL  on my system.


[The Wiki is your friend.]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-26e8b0d4be861a6b7c545dc21c45232f909d8ca2")

---

### Post by kopilo on 2006-09-03
Ok thanks, wikipedia isn't always crediable but I trust your judgement. :cool: 

Thanks.

---

### Post by kroiz on 2006-09-03
> ** Problematic Hardware **

 Hardware with known glitches or incompatibilities: 
 [LIST]
[*] **ATI**[LIST]
[*] Mobility Radeon M6 LY (7000), Mobility Radeon M9 (9000) and Mobility Radeon M9+ (9200)
Drawing artifacts and occasional flickering.
[*] Radeon 9200
No hardware acceleration using fglrx 8.22.5 driver
[*] Radeon XPRESS 200M 5955 (PCIE), Driver: "fglrx_pci", XGL works but the 2D/3D files will not work propely(2D/3D games,full screen videos, etc.).[/LIST] [/LIST]

taken from [http://en.opensuse.org/Xgl#Hardware_Advisory](http://en.opensuse.org/Xgl#Hardware_Advisory)

so this video card of yours might be problematic.

---

### Post by kopilo on 2006-09-03
Yes, which is why I asked the question.. However I guess trial and error might be a better way to find out.

---

### Post by matiit on 2006-09-03
I have got a OpenGl on My Radeon 9200SE 
I used this tutorial:
```
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial --overlay-type=Xv
```
reboot
then:
```
wget -c http://files.covertprestige.info/important/libGL.so.1.2
sudo cp libGL.so.1.2 /usr/lib/
sudo ln -s /usr/lib/dri /usr/lib/xorg/modules/dri
```
reboot

---

### Post by kopilo on 2006-09-03
Hi, I tried the wiki/your suggestion and I got this error...

Terminal log
```
desktop:~$ sudo apt-get install linux-restricted-modules-$(uname -r)
Reading package lists... Done
Building dependency tree... Done
linux-restricted-modules-2.6.15-26-amd64-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up samba (3.0.22-1ubuntu3.1) ...
update-rc.d: warning: /etc/rc2.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
update-rc.d: warning: /etc/rc3.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 102
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by kopilo on 2006-09-04
Hi, I went ahead with the installation ignoring the errors and now this is the result of my xorg.conf
```

Section "Device"
        Identifier  "ATI Technologies, Inc. RV280 [Radeon 9200 SE]"
        Driver      "vesa"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
EndSection


```
I'm wondering if I should change the 'Driver' under 'ATI Technologies Inc, etc to 'fglrx'? I'm not sure how to test if I have opengl or not, I tried running glxgears and it returned;
> glxgears:error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

---

### Post by Kilz on 2006-09-04
> **kopilo said:**
> Hi, I went ahead with the installation ignoring the errors and now this is the result of my xorg.conf
```

Section "Device"
        Identifier  "ATI Technologies, Inc. RV280 [Radeon 9200 SE]"
        Driver      "vesa"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
EndSection


```
I'm wondering if I should change the 'Driver' under 'ATI Technologies Inc, etc to 'fglrx'? I'm not sure how to test if I have opengl or not, I tried running glxgears and it returned;

It looks like the drivers didnt even install. Here is another howto that is better laid out. They both do more or less the same thing. [Only use method 2.]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.28.8_drivers_in_Ubuntu_Dapper_Manually")

---

### Post by kuja on 2006-09-04
If you are seeing something about samba when you're setting up FGLRX, you probably ran into issues when setting up samba to begin with. Try running "sudo apt-get -f install" and see what it does.

---

### Post by kopilo on 2006-09-05
Hi Kuja, interesting avatar considering your name. ;)

Anyway this is what I got when I tried your suggestion.
```

Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up samba (3.0.22-1ubuntu3.1) ...
update-rc.d: warning: /etc/rc2.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
update-rc.d: warning: /etc/rc3.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 102
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
:( 

Just trying your suggestion Kilz.
update: Ran into the same error as stated above when running; "sudo apt-get install module-assistant build-essential"

Side note, when trying to (atp-get) update;  I was unable to connect to "security.ubuntu.com:80 (1.0.0.0)"... Is there something wrong with my repository settings? I have multiverse and universe enabled. :confused:

---

### Post by Kilz on 2006-09-05
> **kopilo said:**
> Hi Kuja, interesting avatar considering your name. ;)

Anyway this is what I got when I tried your suggestion.
```

Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up samba (3.0.22-1ubuntu3.1) ...
update-rc.d: warning: /etc/rc2.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
update-rc.d: warning: /etc/rc3.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 102
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
:( 

Just trying your suggestion Kilz.
update: Ran into the same error as stated above when running; "sudo apt-get install module-assistant build-essential"

Side note, when trying to (atp-get) update;  I was unable to connect to "security.ubuntu.com:80 (1.0.0.0)"... Is there something wrong with my repository settings? I have multiverse and universe enabled. :confused:

You have a package that wasnt installed. It may be stoping you from installing anyting else. I would say try to remove it, but the package is samba. Do you have a network of linux and windows machines?

---

### Post by kopilo on 2006-09-05
Well, no this is the only computer with windows on it, I have been trying to connect this computer to a mepis computer and I have connected to a server via SSH.. However, maybe a re-install of samba? Or just plain removal, then install opengl and then try installing samba after opengl is working?

:-k

---

### Post by kuja on 2006-09-05
Mmhmm, like I thought. Remove Samba. (Re-)Install Samba. Verify that it is installed properly. Proceed with installing your 3d graphics drivers.
Edit: Don't worry, you won't lose any configuration files or whatnot that you may need... you only lose those if you specify --purge when removing the package.

---

### Post by kopilo on 2006-09-05
Sorry, I'm almost a complete noob at this.
I searched in Synaptic Package Manager for 'samba', selected 'remove', told it to apply and got this error;
"E: samba: subprocess pre-removal script returned error exit status 102"

The terminal window.
```
(Reading database ... 87070 files and directories currently installed.)
Removing samba ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--remove):
 subprocess pre-removal script returned error exit status 102
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```

---

### Post by MaximB on 2006-09-05
maybe this thread might help you
I'm using ATI Radeon 9800 pro...but still try it.
[http://www.ubuntuforums.org/showthread.php?t=203105](http://www.ubuntuforums.org/showthread.php?t=203105)

---

### Post by kuja on 2006-09-05
> **kopilo said:**
> Sorry, I'm almost a complete noob at this.
I searched in Synaptic Package Manager for 'samba', selected 'remove', told it to apply and got this error;
"E: samba: subprocess pre-removal script returned error exit status 102"

The terminal window.
```
(Reading database ... 87070 files and directories currently installed.)
Removing samba ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--remove):
 subprocess pre-removal script returned error exit status 102
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```
one thing worth trying is 

sudo apt-get remove --purge samba

If this doesn't work, try manually removing the symlinks that are "dangling"

ie: sudo rm /etc/rc2.d/K09samba



edit: on second thought, if you've already gone through the trouble of configuring samba, it might be worth your while to try removing the "dangling files first". Take your pick.

---

### Post by kopilo on 2006-09-06
Thanks Kuja, I tried the complete removal of samba first, failing that I deleted the dangles (sudo rm /etc/rc2.d/K09samba). Which worked perfectly.

Now I'm trying the method2 that Kilz posted, it seems to be working very well, currently recompiling the kernal. I'll post my terminal log as a file, just in case it goes funny.

[http://bluedelta.smile.reaktor7.com/opengl_install.log](http://bluedelta.smile.reaktor7.com/opengl_install.log)

---

### Post by kopilo on 2006-09-06
Thank you all, open-gl is definatly installed and working, glxgears works fine. :D 

_output of fglrxinfo_
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9250/9200 Series DDR Generic
OpenGL version string: 1.3.1091 (X4.3.0-8.28.8)

*Ubuntu "I am what I am because of who we are".*

---

