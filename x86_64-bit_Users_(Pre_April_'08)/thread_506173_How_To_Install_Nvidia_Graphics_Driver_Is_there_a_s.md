---
title: "How To Install Nvidia Graphics Driver? Is there a short version?"
date: 2007-07-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by chrisfisehr on 2007-07-21
I am a Ubuntu newbie.....I installed Kubutu Feisty 64 on a AMD Dual Core 64 Bit with 3 GB RAM. I am trying to install the driver for the Nvidia GeForce 6150LE. I have spent hours reading endless chapters from Nvidia on the install, as well as Ubuntu forum posts and general Google articles.  I am worn out. Can anyone provide me with the "short" version of how to install my graphics driver? 

What I have done: I have located and downloaded the 64 Bit version of the driver from Nvidia.  I downloaded it to my desktop. I actually got the installer going in a root console shell following nvidia provided command line instructions, but got an error about X server needing to be disabled. 

Can anyone help?

---

### Post by John.Michael.Kane on 2007-07-21
There is no quick way to manually install the drivers, and with every kernel update you have to redo some of the steps you did to manually install the drivers.

To manually install nvidia have a read..
[NvidiaManual]("https://help.ubuntu.com/community/NvidiaManual")
[Installing the NVIDIA Driver]("http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/README/chapter-04-section-02.html")

Your other other options try installing them via system &#8594; Administration &#8594; Restricted Devices Manager. 

Or 

method-one listed in this guide.
[HOWTO: Latest NVIDIA drivers#METHOD_1]("http://www.albertomilone.com/latest_nvidia_udsf_feisty.html#METHOD_1")

Another tool to install them is the envy script.
[Envy]("http://www.albertomilone.com/nvidia_scripts1.html")

---

### Post by chrisfisehr on 2007-07-21
Thanks for the quick reply.  The Envy method appears least painful.  Also, I noticed that I will have to re-install my graphics driver each time Kubuntu is updated to a newer version. Is there a way around this? Can my Adept updater handle this automatically?

---

### Post by John.Michael.Kane on 2007-07-21
No Adept will not handle the nivida driver if you use the manual method or the envy method. In these cases you will have to install the driver the way those guides explain it. 

The only way to have Adept handle the nividia driver is to install driver that is in ubuntu repos using Adept, and #METHOD_1 to install the driver.

---

### Post by chrisfisehr on 2007-07-21
I appreciate the help! Method#1 states that it doesn't matter what install method you use, you will have to manually update your Nvidia drivers every time Ubuntu is updated.  That is the weirdest concept for me to grasp as a new Ubuntu (actually Kubuntu) user. I cannot understand why a "simple" video driver is such a big deal. I know Ubuntu is making a push to go mainstream. Apparently, video driver installs is one area that will have to be improved to accomplish this goal.  Thanks again for your help!!!! I greatly appreciate it!!! Chris

---

### Post by John.Michael.Kane on 2007-07-21
Method#1 does not require the end user to manually update your Nvidia drivers. 

To install using method one
First
```
sudo apt-get install linux-generic
```

Second
```
sudo apt-get install nvidia-glx-new
```

Third
```
sudo nvidia-xconfig
```

Fourth```
kdesu kate /usr/share/applications/NVIDIA-Settings.desktop
```

**Copy paste the following lines into the new file that opens:**
```
[Desktop Entry] Name=NVIDIA Settings Comment=NVIDIA X Server Settings Exec=nvidia-settings Icon= StartupNotify=true Terminal=false Type=Application Categories=Application;System;
```

Save the edited file.

Reboot the machine

Thats is it.

Note: If you have any issues, and wish to revert back to a clean xorg config.
Run:
```
dpkg-reconfigure -phigh xserver-xorg
```

Using the method described above which came from Method one, If theres security updates for the nvidia driver your package manger will notify you if so. 

When you upgrade to the next ubuntu release that driver should be automatically updated the same as the other packages.

The only time you have to update the nividia drive manually is if you install it using a manual method that does not rely on ubuntu repos.

---

### Post by chrisfisehr on 2007-07-21
I got up to the install of the nvidia driver. Unfortuantly, I think it didn't install correctly. I don't know if this helps but here is the message I got:

The following NEW packages will be installed:
  nvidia-glx-new
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/8682kB of archives.
After unpacking 26.0MB of additional disk space will be used.
(Reading database ... 91487 files and directories currently installed.)
Unpacking nvidia-glx-new (from .../nvidia-glx-new_1.0.9755+2.6.20.5-16.29_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/nvidia-glx-new_1.0.9755+2.6.20.5-16.29_amd64.deb (--unpack):
 trying to overwrite `/usr/bin/nvidia-settings', which is also in package nvidia-settings
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-new_1.0.9755+2.6.20.5-16.29_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by rickggreen on 2007-07-21
The video driver problems encountered by those of us that have ATI/Nvidia cards (which is 80% of the installed equipment BTW) can drive you right around the bend. My own experience with trying to set up a muilti monitor system almost led me to take up drinking as a hobby. 
I came to Linux with a lot of  Windows/DOS experience,  so I thought I knew what I was doing. The biggest advantage of linux (choice) is also it's Archilles heel (too much choice).
With Nvidia 6150 you should run the restricted 9755 driver unless you are trying to run a multi monitor configuration, then the 100.14 driver is needed. especially if you are trying to drive a TV as a monitor.
If you want to use the 100.14 use ENVY and be sure that you get back to a VESA config and remove all Nvidia software (with ENVY before you install 100.14, and remeber that if there are any kernal updates that you will have to run envy -t from the terminal from a safe boot before you will be able to use Ubuntu again.

---

### Post by misfitpierce on 2007-07-21
ENVY is a tool to easilly setup latest nvidia or ATI graphics driver they have built into program. Very useful.

---

### Post by chrisfisehr on 2007-07-21
I followed the instructions again, and for some reason it installed this time. I did install the 9755 driver.  New problems though. I can launch the Nvidia control panel and it accurately recognizes the monitor (including model #). The highest resolution Nvidia offers is 640x480. Obviously something isn't right. Any suggestions??

---

### Post by rickggreen on 2007-07-21
You only have to turn on the resricted driber from the System>Administration>resricted Drivers, you don't have to install anything, the applet will do it for you.

---

### Post by chrisfisehr on 2007-07-21
> **rickggreen said:**
> You only have to turn on the resricted driber from the System>Administration>resricted Drivers, you don't have to install anything, the applet will do it for you.
Not sure exactly what you're talking about here....I use KDE, perhaps that is why I can't find this??

also, any ideas about this:  I followed the instructions again, and for some reason it installed this time. I did install the 9755 driver. New problems though. I can launch the Nvidia control panel and it accurately recognizes the monitor (including model #). The highest resolution Nvidia offers is 640x480. Obviously something isn't right. Any suggestions??
Thanks!
Chris

---

### Post by rickggreen on 2007-07-21
Acguire EDID to get your horizontal and verticle refresh rates then edit your xorg.conf

---

### Post by chrisfisehr on 2007-07-21
> **rickggreen said:**
> Acguire EDID to get your horizontal and verticle refresh rates then edit your xorg.conf
i have no idea what your are talking about...EDID?? edit xorg.conf ????

---

### Post by John.Michael.Kane on 2007-07-21
You  can try one of these methods to adjust your resolution?

[screen refresh rates....]("http://ubuntuforums.org/showthread.php?p=2605716#post2605716") 

[HOWTO: change resolution/refresh rate in Xorg]("http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution")

Heres how my xorg is setup for the monitor I'm using, and I'm using a gforce 6100.
```
Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       31.0 - 107.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
# 1600x1200 @ 85.00 Hz (GTF) hsync: 107.10 kHz; pclk: 234.76 MHz
  Modeline "1600x1200_85.00"  234.76  1600 1720 1896 2192  1200 1201 1204 1260  -HSync +Vsync
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1600x1200_85.00"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1600x1200_85.00"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1600x1200_85.00"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1600x1200_85.00"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1600x1200_85.00"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200_85.00"
    EndSubSection
EndSection
```

---

### Post by rickggreen on 2007-07-21
EDID  is data thet your monitor supplies to your system to tell about it.s capablities. There are a couple of ways of getting that data, (choices again). You can go into your nvidia control panel, select your monitor then select acguire EDID. 

Your /etc/X11/xorg.conf should lokk something like this

Section "Monitor"
    Identifier "monitor1"
    VendorName "Plug'n Play"
    ModelName "SCEPTRE P73V"
    HorizSync 30-70
    VertRefresh 50-120
    
    # Monitor preferred modeline (60.0 Hz vsync, 64.0 kHz hsync, ratio 5/4)
    ModeLine "1280x1024" 108 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    
    # TV fullscreen mode or DVD fullscreen output.
    # 768x576 @ 79 Hz, 50 kHz hsync
    ModeLine "768x576"     50.00  768  832  846 1000   576  590  595  630
    
    # 768x576 @ 100 Hz, 61.6 kHz hsync
    ModeLine "768x576"     63.07  768  800  960 1024   576  578  590  616
EndSection

Section "Device"
    Identifier "device1"
    VendorName "nVidia Corp."
    BoardName "NVIDIA GeForce 6 Series"
    Driver "nvidia"
    Option "AddARGBGLXVisuals" "True"
    Option "DPMS"
EndSection

Section "Screen"
    Identifier "screen1"
    Device "device1"
    Monitor "monitor1"
    DefaultColorDepth 24
    
    Subsection "Display"
        Depth 8
        Modes "1024x768" "832x624" "800x600" "640x480" "480x360" "320x240"
    EndSubsection
    
    Subsection "Display"
        Depth 15
        Modes "1024x768" "832x624" "800x600" "640x480" "480x360" "320x240"
    EndSubsection
    
    Subsection "Display"
        Depth 16
        Modes "1024x768" "832x624" "800x600" "640x480" "480x360" "320x240"
    EndSubsection
    
    Subsection "Display"
        Depth 24
        Modes "1024x768" "832x624" "800x600" "640x480" "480x360" "320x240"
    EndSubsection
EndSection


Remember this is my config. yours will be different, The important part is the 

Section "Monitor"
    Identifier "monitor1"
    VendorName "Plug'n Play"
    ModelName "SCEPTRE P73V"
    HorizSync 30-70
    VertRefresh 50-120


It is the horizSync and VertRefresh that sets your screen size. BTW I use gnome so my access to system utils is differnet (choices again)

---

### Post by chrisfisehr on 2007-07-21
Well, I've been working on this for 5 hours now. No success. I never thought that a graphics driver install could be so complicated. My monitor manual doesn't even include all the settings that I need to enter. Then again, why would they? Nobody sets up monitors with manual settings in config files any more.

I reeeeeeeeeeeeeeeeally appreciate everyone's help and willingness to help me find a solution. I love this part of the Ubuntu experience.  However, I just don't think I am ready for Kubutu on my desktop.  I'll try again later this year with the new Kubutu release. Maybe they will have this driver install process more streamlined/mainstreamed.

---

### Post by Ocxic on 2007-07-21
try downloading a program called envy, it'll install the drivers for you,  i use it, and it's pain free.

---

