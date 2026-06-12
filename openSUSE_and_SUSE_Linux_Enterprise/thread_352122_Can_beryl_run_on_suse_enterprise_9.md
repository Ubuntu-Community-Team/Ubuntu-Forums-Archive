---
title: "Can beryl run on suse enterprise 9?"
date: 2007-02-02
forum: openSUSE and SUSE Linux Enterprise
---

### Post by Roasted on 2007-02-02
But the suse forums aren't as populated, and I just have a simple question.

At school on my hard drive with suse enterprise server 9 on it, I was wondering if beryl is compatible with it. That way I could tinker around with my skills on other distros and get a broader view on this.

But as of now I can't even find it for server 9 enterprise. Is it even available?

---

### Post by RAV TUX on 2007-02-05
> **Roasted said:**
> But the suse forums aren't as populated, and I just have a simple question.

At school on my hard drive with suse enterprise server 9 on it, I was wondering if beryl is compatible with it. That way I could tinker around with my skills on other distros and get a broader view on this.

But as of now I can't even find it for server 9 enterprise. Is it even available?> 

**Install Beryl on SuSE with AIGLX and Intel GMA**

                      **From Beryl Wiki**

                                                  Jump to: [navigation]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_SuSE_with_AIGLX_and_Intel_GMA#column-one"), [search]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_SuSE_with_AIGLX_and_Intel_GMA#searchInput")
                         This guide is intended for SUSE 10.2. It will not work on any other SUSE release (including 10.1, 10.0, or even 9.3) because they do not include X.org 7.2. 
AIGLX is a bit different to XGL and is a bit trickier to set up. But it is a lot faster on Intel GMA chips(ie 855, 915, 950). Because SUSE 10.2 includes X.org 7.2 by default- It also therefore includes AIGLX. AIGLX is a little trickier to set up on OpenSUSE because Novell wants you using XGL. 
 **Contents**

[LIST]
[*][1 Part 1: Prerequisites.]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_SuSE_with_AIGLX_and_Intel_GMA#Part_1:_Prerequisites.")
[*][2 Part 2: Build Beryl from source]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_SuSE_with_AIGLX_and_Intel_GMA#Part_2:_Build_Beryl_from_source")
[*][3 Part 3: Configuring AIGLX]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_SuSE_with_AIGLX_and_Intel_GMA#Part_3:_Configuring_AIGLX")
[*][4 Part 4: The moment of Truth]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_SuSE_with_AIGLX_and_Intel_GMA#Part_4:_The_moment_of_Truth")
[*][5 Part 5: Run Beryl at Startup]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_SuSE_with_AIGLX_and_Intel_GMA#Part_5:_Run_Beryl_at_Startup")[LIST]
[*][5.1 Gnome]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_SuSE_with_AIGLX_and_Intel_GMA#Gnome")
[*][5.2 KDE]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_SuSE_with_AIGLX_and_Intel_GMA#KDE")[/LIST] 
[*][6 Blue Video fix]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_SuSE_with_AIGLX_and_Intel_GMA#Blue_Video_fix")[LIST]
[*][6.1 Mplayer]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_SuSE_with_AIGLX_and_Intel_GMA#Mplayer")
[*][6.2 KMPlayer]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_SuSE_with_AIGLX_and_Intel_GMA#KMPlayer")
[*][6.3 Xine]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_SuSE_with_AIGLX_and_Intel_GMA#Xine")
[*][6.4 Totem]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_SuSE_with_AIGLX_and_Intel_GMA#Totem")[/LIST] [/LIST]if (window.showTocToggle) { var tocShowText = &quot;show&quot;; var tocHideText = &quot;hide&quot;; showTocToggle(); }  

**Part 1: Prerequisites.**

 ***(Cyberorg (The maintainer of the SUSE packages) has told me that you CAN use packages from our repository to run AIGLX. If they do not run for some reason, I recommend compiling from source. I have not tested using his packages though with AIGLX and if it does work please tell me)*** 
Go to YaST2. Hit software and then "Software Management." On the pull down menu on the right, hit "Patterns." Make sure "Basis Development, GNOME Development and KDE Development" are checked and install "control-center2-devel". This may install a lot of stuff but its the stuff that I checked and AIGLX works fine for me right now. 
If you are already using Beryl with XGL: 
Get the "Beryl-core-Devel" packages from cyberorg's repo (check the "SUSE Packages" thread on the "Beryl Packages forum on how to get that) 
Once it's installed, run 
 gnome-xgl-switch --disable-xgl
 as root(DO NOT USE SUDO). You may have to do this several times or do it from "Gnome-xgl-settings" to make it work (I had to do it more that 5 times and restart twice before XGL was finally disabled). If you can't get it to disable, uninstall XGL and Compiz packages from YaST. 
Then uninstall beryl because we are going to build it from source 
***If you are completely new to desktop effects:*** 
You still need beryl-core-devel. Again check the SUSE packages thread for more info. 
 

**Part 2: Build Beryl from source**

 You need subversion for this. If you haven't got it, get it from YaST 
In a terminal, run 
 svn co svn://svn.beryl-project.org/beryl/trunk/ beryl
 Wait a while until it stops scrolling lines. Then run 
 ./makeall
 in that directory 
It should work fine. If it doesn't you can A: Get the software it says you need or B: Post the error message or bit "undefined" in this thread and we will try to help. 
If it built fine, then CONGRATS! You have mastered one of the hardest bits of this guide. 
 

**Part 3: Configuring AIGLX**

 First of all, you will need a "Default Xorg.conf" with 3D acceleration. To do that, run 
 Sax2
 as root and check 3d acceleration and then test that config. It should work. 
Now run 
 su
 in a command line and type your root password and run 
 gedit /etc/X11/xorg.conf
 (or you can use "nano") if you want 
NOW FOR THAT REALLY HARD BIT!!!!! 
(If it screws up and you cant get to a gui, then log on a "root" and type "sax2" to save your a** It usually ALWAYS works) 
(Thanks to Cyberorg for this bit) 
Add these changes in your Xorg.conf (Don't replace, just add in the respective sections, and don't add "Section" or EndSection") 
To Section "ServerLayout" 
 Option "AIGLX" "true"
 To Section "Extensions" 
 Option "Composite" "Enable"
 To Section "DRI" 
 Group 0
        Mode 0666
 
To section "Device" 
 Option      "XAANoOffscreenPixmaps" "true"
        Option      "DRI"     "true"
 
Here is what the respective sections on mine look like 
 Section "Extensions"
Option   "Composite"   "Enable"
EndSection

Section "DRI"
    Group      0
    Mode       0666
EndSection

Section "ServerLayout"
  Identifier   "Layout[all]"
  InputDevice  "Keyboard[0]" "CoreKeyboard"
  InputDevice  "Mouse[1]" "CorePointer"
  InputDevice  "Mouse[3]" "SendCoreEvents"
  Option       "Clone" "off"
  Option       "Xinerama" "off"
  Option       "AIGLX"   "true"
  Screen       "Screen[0]"
EndSection

Section "Device"
  BoardName    "915 GM"
  BusID        "0:2:0"
  Driver       "i810"
  Identifier   "Device[0]"
  Option       "NoDDC"
  VendorName   "Intel"
  Option       "XAANoOffscreenPixmaps" "true"
  Option       "DRI"   "true"
EndSection
 Your's might vary a little, but it should look something like that- especially the "DRI" section 
 

**Part 4: The moment of Truth**

 Save the Xorg.conf (As root) and log out. If the log in screen comes up then you have done it right (w00t!) 
If not then run "Sax2" (or something like that) as root to reset and try again 
Login- and open up a "Run command" box 
Execute 
 beryl --use-copy
 (You may also need to issue the "--replace" option if another WM is running) 
and see if it works. If it doesn't- run it in a terminal and post the output and if it does YAY!!!!!!. You're 9/10ths of the way there 
run 
 beryl-manager --no-force-window-manager
 to make sure it doesn't screw everything up. 
If that works then CONGRATULATIONS! You are one of the few who can run AIGLX on openSUSE. 
Now just add that to your startup in gnome or kde: 
 

**Part 5: Run Beryl at Startup**

 

**Gnome**

 Computer(SLAB menu) &#8594; Control-Center &#8594; Sessions &#8594; Startup Programs &#8594; Then add 
 beryl --use-copy
 and 
 beryl-manager --no-force-window-manager
 
To make it run on startup 
 

**KDE**

 Start those programs, end your session and they should start up automatically (By default) 
 

**Blue Video fix**

 

**Mplayer**

 Settings>Video> Then in the driver section make sure that X11 (Xshm) is highlighted 
 

**KMPlayer**

 Same thing 
 

**Xine**

 Something like that.. (I dont use Xine) 
 

**Totem**

 Fix should be applied from Xine. 
  There is a fix to make Java apps (ie. *cough*limewire*cough*) work, but I cant find it. Can someone tell me so I can put it here? 
  The fix for Java apps is to export an environment variable of AWT_TOOLKIT=MToolkit from your .bash_profile  Now go enjoy playing Xmoto at a decent framerate while wobbling another window! Smile
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_SuSE_with_AIGLX_and_Intel_GMA](http://wiki.beryl-project.org/wiki/Install_Beryl_on_SuSE_with_AIGLX_and_Intel_GMA)

---

### Post by Roasted on 2007-02-05
Thank you. :) If I have some free time in my linux class tomorrow I'll be sure to check it out.

---

### Post by Roasted on 2007-02-06
Uh, check out the top line of the wiki page. It's not for the distro I'm using, which is SuSE Server 9 Enterprise Edition. I guess it's not available for this one?

---

