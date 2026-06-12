---
title: "Gutsy will just freeze / lock up / crash"
date: 2007-10-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by jonah1980 on 2007-10-23
hi i just installed gutsy amd64, i have nvidia graphics and i turned off desktop effects incase that was causing the crashes. The machine will lock up after randomly. you can use it for an hour then it will freeze or for 5 mins if that and it will. Desktop effects on or off makes no difference and it crashes whatever. And it's a real crash like can't move mouse or exit to prompt etc.

can anyone help me out thanks?

---

### Post by jerry.k.jerry on 2007-10-23
r u havin da same prob wit other operating systems as well...... if da prob persists in windows or some other distribution of Linux u prolly have some kind of hardware conflict....
dat prolly is da case..... i dont think its ubuntu!!! try da memory test at boot der maybe some issues with ure ram chip!!

---

### Post by jonah1980 on 2007-10-23
no i've been using elive for months and no problem with that at all, it never locked up. i don't use windows, i think it's worst thing i've ever seen. fedora and others seem ok also, although i can get crashes with beryl/compiz enabled on other distros...

---

### Post by yellowbread on 2007-10-23
You could try checking your memory usage. Just run "free -m" from the terminal from time to time or keep a system monitor running. I've seen some reports of a memory leak that causes slugish behavior and crashes when memory runs out.

---

### Post by ACLerok on 2007-10-23
When I first installed Feisty my machine only had 2GB of ram and it worked fine.  When I installed another 2GB (4GB) it would freeze up randomly.  I ended up having to pass MEM=2048M as a parameter when booting in grub.  I haven't seen this happen so far in Gutsy, but maybe you're having a problem similar to this? 

How much RAM do you have currently in your machine?

---

### Post by MiiJaySung on 2007-10-23
I've had similar issues. When working in text mode (i.e. Ctrl + Alt + F1) when things crash I've seen a backtrace that hints it's my SATA drivers. It tends to heppen when the harddisk is under load. 

I have a nForce 590 chipset which is used to control my drives. My CPU is dual core... I know originally there where some issues with X2 based systems in places due to timing and some ACPI support on some BIOS's, however I doubt it's that with my system.

Maybe you are experiencing the same? Let others know what sort of conditions its happens under.

---

### Post by bonestonne on 2007-10-23
i actually had this issue myself last night with Gutsy freezing, but only for a minute or two

i was using Pidgen, i closed an IM window, then i opened a new one, and someone else sent me a message, causing another tab to open, and my whole system froze. somehow i'm able to run Photoshop CS2 without any major issues though?

i have 1GB of DDR2 667 RAM in dual channel.

---

### Post by buntunub on 2007-10-23
:popcorn:

Same issue here with the frequent random lockups. None of the usual logs indicate anything weird when this happens, so im at a total loss here. This is an issue which carries over from Feisty as the Forums here have many, many complaints dating back a long ways, without any fix or clue even. If anything, Gutsy seems to have made things  even worse than in Feisty. These lockups occur even if my computer is totally idle with just a movie or TV running. Heck, ive even had a lockup with absolutely nothing running but just moving the mouse! Something is definitely amiss here.

Edit: I have no crashes or lockups whatever while running Compiz-Fusion on this Computer under Sabayon, Fedora7, Mepis, and SuSe 10.3, so this is most definitely a Ubuntu only bug.

---

### Post by ACLerok on 2007-10-23
When you guys get these crashes, do you have Firefox open?  

I noticed that I could run Firefox fine on its own, I could run Compiz-fusion (some of the time) fine on its own, but if I ran the two together, a freeze was inevitable.  

Even yesterday after I installed Gutsy, Firefox would freeze up.  The weird thing is, when I looked in my task manger (forget what it's called in Ubuntu) Compiz, Firefox, and X would all say they were using some extremely large amount of memory greater than even possible (17111118388383GB), and then the next highest thing would be using 80MB or something.  

I have a feeling that my crashes have to do with Firefox 2.0.0.8 and the version of Flash that I installed on Feisty. I'm going to uninstall and reinstall flash and the wrapper for it.

---

### Post by hotbit on 2007-10-23
I have similar problems. And when I have a look in the System Monitor today I see strange-huge memory usage by some processes, like 17179869180.0 GB -  alike *ACLerok* has.

My system freezes randomly, however if I will start Deluge torrent client it will happen in a few seconds up to a few minutes inevitably, every time.

I have no idea if there is any relationship, but other my problems include:
- If during system boot there is no 'welcome' sound with login screen - I have no sound in  movie players nor flash, but Rythmbox is working fine.
- If Compiz is running, screensaver does not start (just black screen)

---

### Post by nanbudh on 2007-10-23
> **ACLerok said:**
> When you guys get these crashes, do you have Firefox open?  

I noticed that I could run Firefox fine on its own, I could run Compiz-fusion (some of the time) fine on its own, but if I ran the two together, a freeze was inevitable.  


I have a feeling that my crashes have to do with Firefox 2.0.0.8 and the version of Flash that I installed on Feisty. I'm going to uninstall and reinstall flash and the wrapper for it.

I have had freeze up without the firefox too but i think u may be right about the firefox as well as the flash component.I installed Gnash afer gutsy install and maybe things went bad after that only. can't be sure though. So how can i uninstall gnash if i have too?

---

### Post by ACLerok on 2007-10-24
> **nanbudh said:**
> So how can i uninstall gnash if i have too?

Did you install gnash through Synaptic?  You could just search for it in Synaptic, right click and remove it.

---

### Post by jonah1980 on 2007-10-24
ok stopped using "nvidia" in xorg and changed it to "nv", my system hasn't locked up as of yet, used it all evening so looks like it might be ok. as of yet no lock up so it's already gone longer than nvidia ever would in one session, so more reliable that's for sure. just a shame cos no 3d effects or compiz...

---

### Post by jonah1980 on 2007-10-24
> **ACLerok said:**
> When I first installed Feisty my machine only had 2GB of ram and it worked fine.  When I installed another 2GB (4GB) it would freeze up randomly.  I ended up having to pass MEM=2048M as a parameter when booting in grub.  I haven't seen this happen so far in Gutsy, but maybe you're having a problem similar to this? 

How much RAM do you have currently in your machine?

also i do actually have 4gb so this could be possible...

---

### Post by jonah1980 on 2007-10-25
yeah switched over to nv instead of nvidia in xorg.conf and haven't had a crash since, so i'm blaming the nvidia driver for this one...

---

### Post by ACLerok on 2007-10-25
> **jonah1980 said:**
> yeah switched over to nv instead of nvidia in xorg.conf and haven't had a crash since, so i'm blaming the nvidia driver for this one...

Yeah, it happens.  I wasn't able to use Beryl/Compiz at all with my 7.04 installation.  I was pleasantly surprised when the same drivers worked in 7.10.  

Perhaps try an older driver that you know works?

---

### Post by jdfreshwater on 2007-10-25
It has to be the Nvidia driver.  I did not a have a problem in the beta version, but had a problem since the release core version.  So it must be a new nvidia package.  My biggest problem is I want to use the TV out for a mythtv frontend.  Hopefuly a fix will be sent soon.  I've seen many people with similar issues.

---

### Post by JNowka on 2007-10-25
I have been having a problem with Gutsy randomly locking up and crashing.  Only problem is that I have an intel video card.

---

### Post by Rui Pais on 2007-10-25
Hi,
i'm experienced 2 different kinds of freezes under Gutsy.
One it happens when i run firefox/swiftweasel (64bits), i could force xserver to close but  it won't come back again (no gdm or console). With other user running i managed to see a ghost nswrapper.bin (or something like that) running. The other user get frozen too after a while, even if i kill the ghost bin.

The 2nd kind of frozen happened randomly, no specific app (OOfice was involved sometimes, but also file manager and thurderbird) and it was worst. I have sometimes to do a cold reboot :(.

I suspected nvidia too, so i delete any default nvidia related package and installed nvidia using envy. The issue persisted. 
I removed then all again and installed the package directly from NVidia site, and in the last 2 days (or so) i haven't experience a single bad frozen, and now with the flash wrapper the worst that happen is closing browser and a ghost window with some animation hang around on the screen till i kill the nswrapper.bin from terminal. I guess the last step, for me, to purge this annopyance is to install again a 32bits browser...

Apart from that all seems to run well now.
hth

---

### Post by OnSite511 on 2007-10-25
I'm having freeze problems that match this exactly.
Can anyone else that has the freeze problem with an Nvidia card confirm their version of the driver? I don't want to just go and install a new driver without some evidence 

Mine is the base install of Gutsy
nvidia-glx-new 100.14.19+2.6.22.4-14.9
nvidia-kernel-common of 20051028+1ubuntu7

thanks

---

### Post by KingOfNowhere on 2007-10-26
hey all,

i also have a fresh x86 install of Gutsy on my desktop with a nvidia geforce 6600. since installing gutsy, i have had these exact symptoms. and my drivers match the previous poster. when anyone has any kind of fix or workaround (other than disabling "nvidia" driver) please let us all kno.

---

### Post by Rui Pais on 2007-10-26
> **OnSite511 said:**
> I'm having freeze problems that match this exactly.
Can anyone else that has the freeze problem with an Nvidia card confirm their version of the driver? I don't want to just go and install a new driver without some evidence 

Mine is the base install of Gutsy
nvidia-glx-new 100.14.19+2.6.22.4-14.9
nvidia-kernel-common of 20051028+1ubuntu7

thanks

All driver versions, either default gutsy, envy install or latest from Nvidia site are 100.14.19. So it shouldn't matter the one used, but for some weird reason with me only the drivers from nvidia site work without freezes.

---

### Post by jb5 on 2007-10-26
Hi - I'm getting the same problem as above. However, I'm using an [B]ATI - restricted driver.
[/B]
Similarly, in system monitor, lots of processes showing the 17179869180.0 GB memory usage. - 
```
CPUfreq-applet; 
fast-user-switch-applet;
 firefox-bin; 
gksu; 
gnome-panel; 
gnome-system-monitor; 
gtk-window-decorator; 
multiload-applet-2; 
nautilous; 
realplay-bin; 
stickynotes-applet
```


Clean Gutsy64
2GB Ram
No difference if visual effects are none/normal/extra.

```
jb@colin:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2014       1903        110          0        351        959
-/+ buffers/cache:        593       1420
Swap:         8503          0       8503
jb@colin:~$ 

```

System monitor shows the memory usage as : -
```

user memory : 602.7 MB of 2.0GB 29.9% used
user swap : 0 of 8.3GB 0% used
```

(NB I realise that at the moment I've got more swap space than I really need but if I eventually decide to increase the RAM I don't need to play around with the swap space!) ;)


Machine ran fine under Feisty32. So not a hardware problem.

EDIT - The main problem appears to be that the menus and icons on the toolbars/panels no longer seem to function correctly. 
The windows list no longer updates with changes to opened applications & I can no longer use the quit button or select many of the panel items with the mouse (system monitor, CPU freq analyser and networking icons do work!). I can still use keyboard shortcuts and <alt>tab etc to switch between applications. 
<cntrl><alt>backspace logs me out ok and when I login again I'm back to normal - for a while!

---

### Post by odin277 on 2007-10-26
Hi all
Don't know if this will help but I was having the same problem with freeze/ crashing using nvidia 6150SE. I checked xorg.conf and found that it was using the wrong Horizontal Sync and Vertical Refresh rates for my monitor. Changed them 2 days ago and so far no further crashes.
(etc/X11/xorg.conf  - just make sure to create a back up first) 

New user so take this with a grain of salt

---

### Post by ARB on 2007-10-26
I have had the same problem with Firefox and Swiftweezel and I have an ATI Radean card.  I did not have this problem with Feisty.  Seems from the rest of the posts that that this is just not machines with nvidia cards.  Looking forward to a resolution of the problem otherwise I am going to go back to Feisty!

---

### Post by kyleabaker on 2007-10-26
I'm having the same problems here.
Gutsy x64 with an Asus Nvidia GeForce 7300LE card and restricted drivers enabled for nvidia. I also have a dual display setup using TwinView to move across both screens.

Here is my xorg.conf file..
```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder26)  Wed Sep 12 14:29:53 PDT 2007

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@75" 129.9 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
    ModeLine       "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
    ModeLine       "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
    ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 LE"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT-0: 1280x1024@60 +0+0, CRT-1: 1280x1024@60 +1280+0; CRT-0: 1280x960@75 +0+0, CRT-1: 1280x960@75 +1280+0; CRT-0: 1280x960@60 +0+0, CRT-1: 1280x960@60 +1280+0; CRT-0: 1280x1024@75 +0+0, CRT-1: 1280x1024@75 +1280+0; CRT-0: 1152x864@75 +0+0, CRT-1: 1152x864@75 +1280+0; CRT-0: 1024x768@60 +0+0, CRT-1: 1024x768@60 +1280+0; CRT-0: 1024x768@70 +0+0, CRT-1: 1024x768@70 +1280+0; CRT-0: 1024x768@75 +0+0, CRT-1: 1024x768@75 +1280+0; CRT-0: 832x624@75 +0+0, CRT-1: 832x624@75 +1280+0; CRT-0: 800x600@60 +0+0, CRT-1: 800x600@60 +1280+0; CRT-0: 800x600@75 +0+0, CRT-1: 800x600@75 +1280+0; CRT-0: 800x600@72 +0+0, CRT-1: 800x600@72 +1280+0; CRT-0: 800x600@56 +0+0, CRT-1: 800x600@56 +1280+0; CRT-0: 640x480@75 +0+0, CRT-1: 640x480@75 +1280+0; CRT-0: 640x480@72 +0+0, CRT-1: 640x480@72 +1280+0; CRT-0: 640x480@60 +0+0, CRT-1: 640x480@60 +1280+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

Anyone found a solution yet?

---

### Post by hotweiss on 2007-10-26
Same problem here, it's driving me crazy... No solution yet?

---

### Post by jb5 on 2007-10-27
Hi - In order for me to get the visual effects to work I need to install two extra packages through synaptic package manager -

xserver-xgl
compizconfig-settings-manager

I noticed today that before installing xserver-xgl the memory usage in system monitor was normal. 
After installing xserver-xgl the memory usage immediately went up to 17179869180.0 GB for several packages. -

Removed xserver-xgl and the memory usage went back to normal!

So I guess it might be worth removing xserver-xgl and see if that helps anybody else.

BTW - I don't know if this is also relevant, but after installing xserver-xgl on next login it complained that the gnome and x-terminal keyboards didn't match and asked which I would prefer to use?

---

### Post by Gonkerd on 2007-10-27
Same problem here, random system freeze. When i run cisco vpn it happens extra fast, but still random. 
When it happens again, i'm going to try the nv driver instead of the nvidia (current version: 100.14.19) or new nvidia from nvidia site. After that i'll try the refresh rate change.

---

### Post by kyleabaker on 2007-10-27
@Gonkerd
Please let us know the results from what you try. I can no longer use my Gutsy workstation. It's too unreliable. I'm tempted to find another distro at this point, but I keep hoping they will get it fixed.

---

### Post by Gonkerd on 2007-10-27
i've now made a crontab which dumps the uptime output in a file every 5 minutes, maybe it give some info??

---

### Post by jb5 on 2007-10-27
> **jb5 said:**
> Hi - In order for me to get the visual effects to work I need to install two extra packages through synaptic package manager -

xserver-xgl
compizconfig-settings-manager

I noticed today that before installing xserver-xgl the memory usage in system monitor was normal. 
After installing xserver-xgl the memory usage immediately went up to 17179869180.0 GB for several packages. -

Removed xserver-xgl and the memory usage went back to normal!

So I guess it might be worth removing xserver-xgl and see if that helps anybody else.

BTW - I don't know if this is also relevant, but after installing xserver-xgl on next login it complained that the gnome and x-terminal keyboards didn't match and asked which I would prefer to use?

The panels have just frozen again!
I thought that I might actually be on to something when the mem usage looked OK. 
Oh well, back to square one! :(

---

### Post by jonah1980 on 2007-10-27
ok i was wrong. switching to nv from nvidia hasn't worked for me. I was just lucky for a while and it didn't crash for a day or two. but last night it locked up completely again after a couple hours and then again this morning after about 5mins...

real killer is this!!

---

### Post by zmjjmz on 2007-10-27
I've been having the same problem on my Macbook, where if I do something completely random (such as closing AWN or saving a file in OOo) my computer locks up and I can only move the mouse...

---

### Post by OnSite511 on 2007-10-27
After reading all the options, and poking around my wifes Gutsy install (no graphics problems) I noticed that there were no sync rates in my xorg.conf file. After running 
```

dpkg-reconfigure xserver-xorg

```

and making double sure that my synch rates were appropriate (looking at my monitor show info/settings popup) I've yet to have my system freeze. :KS I'm thinking that since all the driver versions for us are probably the same, when installing the Nvidia drivers from the nvidia site it probably runs a xserver configuration tool and sets the appropriate settings. Before you run the above from the terminal, be sure to backup your xorg.conf file (I think the tool does it, but to be safe...)

good luck.

edit:
my system just locked up browsing the internet. this sucks. I'm going to try installing the nvidia drivers from the nvidia site.

---

### Post by paulmac on 2007-10-27
me too, seems to lock up using Firefox more than anyplace else.  Random.  Requires warm boot.

---

### Post by jonah1980 on 2007-10-27
i've posted a bug report here guys: [https://bugs.launchpad.net/ubuntu/+bug/157777](https://bugs.launchpad.net/ubuntu/+bug/157777)

---

### Post by OnSite511 on 2007-10-28
So I couldn't stand it and just finished the conversion back to 7.04. Ugh. when this gets fixed, perhaps I'll upgrade again

---

### Post by jb5 on 2007-10-28
> **paulmac said:**
> me too, seems to lock up using Firefox more than anyplace else.  Random.  Requires warm boot.

I can replicate the behavior on my machine without running FFx! :(

Also no-synch rates listed in my xorg-conf file, and the freeze happens with an ati-driver also!

---

### Post by MariusSilverwolf on 2007-10-28
I'm having lock issues, but not specifically video related (I don't think) even though I am using the restricted drivers for my GeForce4 7200.

I can sit at my system for hours, download updates, run Pidgin, have FireFox open in one workspace and Opera in another, and do whate'er I like for as long as I like.

However, if I'm ripping/encoding a CD using grip with lame, regardless of the CD, after roughly 6 minutes of encoding my entire system locks.  All input is disabled and I have to hit the handy Reset button on the front of the PC case.

I'm thinking, since it only happens under load, and didn't happen under Windows XP on the same machine, that it's a driver's issue with my SATA drives that stops responding after being under load for too long.

Ideas for what I need to check? /etc/var/logs gives me nothing useful.  Thanks.

---

### Post by Gonkerd on 2007-10-28
Just for everybody's information i've got ubuntu running on SATA also.

---

### Post by Sammyf on 2007-10-28
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/157777](https://bugs.launchpad.net/ubuntu/+bug/157777) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Same problem here. 

Feisty was extremely stable (had it run for a month as a server while I was away, without anybody supervising it, and it was still running fine when I came back), but since I upgraded to Gutsy I experience sudden and very absolute crashes. I can't restart X, I can't move my mouse, nothing seems to happen... the only way to get out of it is to do a hard reset and reboot.

I have been doing different things when it happened, sometimes I had Compiz enabled and sometimes not ... Firefox and Amarok were running everytime, but I can't say whether one of them is to blame or not.

my config is :
AMD Athlon XP 2600+, 2GB, nVidia 7800GS (AGP), 3 IDE drives (no sata on the mainboard), Asus A7N8X-X mainboard.

A solution or at least a hint where it's coming from would be greatly appreciated.

---

### Post by OnSite511 on 2007-10-28
So the end of the bugreport ([https://bugs.launchpad.net/ubuntu/+bug/157777](https://bugs.launchpad.net/ubuntu/+bug/157777) ) that sammy kindly provided is
```

I managed to use "downgrade" to nvidia-glx driver. The problem seems to be on the package that fails to remove the control file /lib/linux-restricted-modules/.nvidia_new_installed

This file is checked by lrm-video script to see if it needs to load nvidia or nvidia_new

Just by installing nvidia-glx, removing the file mentioned and restarting the system does the trick.

```

Anyone want to give it a go and let us know how it goes? I'd be more than willing, but I downgraded to Feisty 7.04 last night so I don't really feel like re-upgrading and messing with my system anymore this weekend.

---

### Post by onandon on 2007-10-28
After upgrading to 7.10 from 7.04, I met this problmes as well. My computer froze a few mintes after start-up. Sometimes I can use Crl+alt+Fn to switch to tty to restart xserver, sometimes i could not. I tried every nvidia drivers. Nothing helps. 
Then I tried to use a different kernel, instead of the latest one 2.6.22-14. It turns out that 2.6.20-16 works fine for me. Till now, no freeze .

Is the freezing because of the kernel itself or something(such as nvidia driver) not compatible with the new kernel?

--Edited---
dam it. froze again just now

---

### Post by Karti on 2007-10-29
Just to add a comment in the hope that it may help someone - Same issues as others, system freezing with only a reboot. 

I followed some advice with regards the nvidia-glx-new and when I removed it and used nv drivers all my issues were resolved.

My Ubuntu PC has now been running for two days with problems since I removed the glx-new driver.

Hope that helps.

Regards

K
;)

---

### Post by eligos on 2007-10-29
Same problem here on a Compaq Presario f500

Processor: AMD Sempron 3500+
GPU: Nvidia GeForce Go  6100
2 Gb Ram
and a SATA disk

In feisty i had no problems, even running firefox (up to 5 tabs) and virtualbox / winxp... under a fresh install of gutsy freezes ocur randomly with nv and nvidia-glx-new drivers.

Under feisty i was using the 100.14.19 drivers from the nvidia page

---

### Post by MariusSilverwolf on 2007-10-29
So quick poll of those who've been having issues, relating back to my previous post:

Did you have problems ripping/encoding before applying the nvidia driver fix?
Have you had those same problems since?

Thanks so much.

---

### Post by quasimodo69 on 2007-10-29
I am sorry but I am a newbie to Linux.I apoligize in advace for the length of my post.
      I have seen others have a similar problem.I have seen some posts for solutions...but I do not understand them.I have the 6.10 disc from Ubuntu and intalled it.Ihad no problem with it and fell in LOVE with Ubuntu!I have even converted some of my friends who are not even into computers!
  Sorry,I digress..My problem is that I updated over the net to 7.04...I had no problem.I awaited the
update to 7.10.I down loaded the disc and burned and ISO image.I ordered Ubuntu cups and stickers!
I installed the 7.10 and have had the hard crashes the other have had.I mean a a HARD crash.I wiped the hard drive after some experimentation noted below in my system profile..all with system crashes.I have wiped the hard drive and gone back to Fiesty 6.10 and have had no problems.
  I have even tried updating from the net to 7.10 from 6.10..same problem.
I have had problems with 6.10 with sound...6 out of 10 times the sound does not work and I have no idea how to fix it since I have no idea what I am doing.Sometimes the sound works fine on start up...sometimes it is silent.
My nVidia drivers...installed or not...I have no way to change resolution or any other control of my video.I have 3 resolutions and that is it....no matter what drivers I use.
I just wanted to add this info from my experience to the pile in the hope it will help somebody figure out what is happening and we can find a fix.
  Here are my questions as a newbie and I do appreciate all the people who work to contrubute to these help forums...I really do.

  1-I need to know how to work the terminal window (I have read enough to start understanding the file system)I have seen guides with commands-but I do not know when or how to use them.
  2-I need a step -by -step guide for a 3 yr old (maybe they are smarter) on how to do things.It seems some of the steps are left out in the documentation I have been looking at for the last year because they assume a level of competence I do not have.( what is SUDO?..when do I use SUDO?What is ROOT..and do you use it with Ubuntu?
  3-I have sen the posts for the crash problems with 7.10 and AMD 64..but can not decipher what to do about them.

    I have rolled back to Fiesty Fawn and have no problems.
I had problems with nVidia drivers or without (mostly without) 
I did not use the desktop enhancements
I was running Firefox when it crashed
i do not know how to do a report of any kind about my crash.

thnx to all who have waded through my post and I hope it will contribute.
my e-mail adress is [email]wizard69@mail.com[/email] if anybody has a scolding or help..any will be considered.
If this post is too long for this forum,please let me know.
DOWN WITH Micro$oft!!

  My System=
  AMD 64 3000 CPU     1GB ram   VIA raid and SATA divers and North and South bridge
1 40GB IDE hard drive (Ubuntu be here)   1 5GB IDE hard drive (blank swap)
200GB SATA hard drive (Micro$oft be here=YEEUUCCH!)
40GB SATA hard drive  (blank-FAT32)   Video nVidia AGP 5600 GeForce
Sound Card Sound Blaster Live PCI  MoBo Abit Av8
Crashes have occurred even without nVidia drivers installed-every time Firefox was running.
These were hard crashes where the system went down,black screen and computer buzzers 
went off.A check of the system temp showed fine (113 degrees) and system monitor showed
no excessive memory usage. 
 I have used the driver for the nVidia card supplied with my card on the disc-and I tried
the drivers posted on their site dated 9/07/07 and same problem.
  I also have not gained any functionality from the installed drivers for the video card
and have not enabled the desktop enhancement features (I am scared enough as it is with stable
programs!) I am so new at this I do not have a clue how to use the terminal window!
P.S I have looked-does anybody know of a website that tells you exactly what to type in to
do things?Something for morons like me that says &#8220;put your right finger on the &#8220;S&#8221; key...

---

### Post by Prometheum on 2007-10-29
Has everyone been running firefox? This has been happening to me, and its usually seemed to either be Firefox or NetworkManager. Last night I looked at my memory and it was full, and I have a suspicion the only reason I could see that was because I already had System Monitor open. I couldn't do anything to reboot, and I had to unplug.

Also, my keyboard sometimes stops working, even though my mouse will continue to work for a short time. 

I'm running 7.10 x86_64 on a dual-core AMD64 Turion with 1gig of ram, using the nvidia driver on a GeForce 6x. 

I strongly suspect firefox. Usually the worst crashes have been while its under load.

---

### Post by OnSite511 on 2007-10-29
Members,

someone try downgrading to the previous version of the nvidia driver and let us know how that works out;

To force the installation of a package different from the one chosen by Synaptic, do the following:
Click Reload or press Ctrl + R to make Synaptic aware of the latest updates.
Select the package. Choose Force Version from the Package menu.
Select the version you would like to use. To confirm your decision, click Force.
Click Apply on the toolbar or press Ctrl + P. A dialog appears with a summary of the changes that will be made to your system. To confirm, press Apply.

---

### Post by spamhippy on 2007-10-29
hiya- upgraded- been having the same problem- have an nvidia 7300 card. don't have any problems when i change 'nvidia' to 'vesa' in my xorg.conf file- but vesa has no 3d & sucky screen res. etc... but it works fine while your using it- so that's a quick fix (for now..) thought at first it might have been flashplayer (an older version did almost the exact same thing to slackware on me last year-) but after uninstalling it- it still happened. also am having weird problems w/ video playback (sometimes..) the picture will turn into a mess of pixels when playing a dvd (this happens at random- but once it happens all video is messed up until you get out of xscreen..) i can't force version on nvidia-glx-new (it's not an selectable option..) deleted that one file mentioned above and reinstalled nvidia- i'll see how it goes.. (lol) with all the ads on the internet now days that are based on .flv flashvideo- i'm just wondering if it's nvidia driver having a problem with video playback. have done reinstallations on several things already trying to fix this. no plans to downgrade- will stay & fight & let 'em work the last minute kinks out LOL. well- will report if i find out anything for sure...

---

### Post by hronir on 2007-10-30
I have just the same problem, but with an ATI card.
I suspect the problem shows after suspending2disk and resume...

---

### Post by OldGaf on 2007-10-30
I have a thread on the same kind of thing..... [Here]("http://ubuntuforums.org/showthread.php?t=593607")

In short,

It seems to be an Xorg thing. 

It happens to people with ATI and Nvidia.
It happens to people with 32 and 64 bit.
It happens to people with K,X,Ubuntu.
It happens to people with Feisty and Gusty.

If I keep using my system all is fine. If I leave it with Top running, I see Xorg slowly start eating more and more CPU.

If I start using it before it hits 95-100%, It comes back to life and CPU drops to normal.

If I don't stop it, Top keeps running, the mouse still moves but I can not click anything.

Some people can get away with Ctrl+Alt+Backspace, but some have to reboot to clear it.

I and others have reported the bug.

Is anything happening to fix this?

---

### Post by spamhippy on 2007-10-31
i don't know about the ATI thing (i have an nvidia 7300 card..) but- i think i've fixed it (no crashes in the last day or 2..) here what i did.... i downloaded nvidia-xconfig & ran it (makes a new xorg.conf file -setup for nvidia...) you can get this tool from either the package manager or from nvidia's site under - driver downloads...

then.. go into recovery mode... type 'startx' - if it asks if you want to continue say 'yes'

go to....  /lib/linux-restricted-modules  

in your file browser click on 'view' and select the option 'view hidden files..

you should see a file called '.nvidia_new_installed  ' -delete that.

then open the package manager and unistall the following 2 packages....

nvidia-glx-new

nvidia-new-kernel-source


than install the packages......

nvidia-glx

nvidia-kernel-source


close all apps- 

click ctrl+alt+backspace  (takes you out of x..)

the click ctrl+alt+delete  (this reboots your computer)

make sure "nvidia" is in use in your xorg.conf file & don't mess with 'restricted drivers' - i think all that does is installs 'nvidia-glx-new' if you play with him & you don't want that. it sounds like from descriptions that 'nvidia-glx-new' or 'nvidia-kernel-source' might have a big @$$ memory leak somewhere- i don't know. as far as ATI goes- i can only guess- maybe ATI borrowed some ideas from NVIDIA & caught this bug? i'd go & see if i could find a hidden file in /lib/linux-restricted-modules- and see if a person can do more or less the same proceedure on an ATI. 

anyways- been running like this for almost 2 days now- have compiz on advanced options & emerald installed- everything seems to be working fine. well- hope this works for everyone- goodluck!

---

### Post by Paqman on 2007-10-31
This is ridiculous. I've just upgraded my PC (including an Nvidia 7300GT and a dual-core Athlon) and Ubuntu is now unusable. It locks up between 10sec and 1min after logging in, making it very difficult to do *anything* to sort it out. I've tried all three drivers available through Envy, including the beta 100.14.23 driver. Same terrible result from them all.

I'll try your method tomorrow and give you some feedback Spamhippy. Fingers crossed that works, because at the moment i'm looking at switching distros.

M2N-E SLI Mobo
Athlon 64 X2 6000
1GB PC6400 RAM
Nvidia 7300GT PCI-E
Seagate SATA HD
IDE DVD Burner
Floppy

---

### Post by brokengoose on 2007-10-31
Same problem as others. 

Hardware:
ATI Radeon 9800 (using AGP, not PCI-e), 
AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ (running at 2GHz)
Asus A8V motherboard (w/ VIA K8T800 Pro chipset)
Seagate IDE drive
Generic IDE DVD burner.
Realtek 818x wireless card

Worked flawlessly under 7.04 (though the wireless driver is quirky there).  Under 7.10, it crashes every 15 to 60 minutes.  I've changed X drivers.  I've tried i386 and x86_64.  I've tried turning off Cool n' Quiet.  I've tried turning off acpid.  Firefox doesn't seem to matter -- it'll crash just fine without it.  The machine requires a hard reboot.  It doesn't respond to terminal switching keys, and I can't ssh in over wireless or ethernet.

One other bit of data: Under Fedora Core 7, the machine crashes constantly (often in less than 5 minutes -- usually before the "firstboot" process can complete, and always before patching can complete) UNLESS I enable Xen.  Xen isn't compatible with a lot of frequency scaling and power management stuff, so the FC7 Xen kernel has a lot of that disabled.

I couldn't stand the constant crashing, so I've gone back to 7.04 for now.  I'm willing to work with anybody who wants to try to debug problems with 7.10.  Unfortunately, since I can't isolate the problem, I can't search for it ("ubuntu 7.10 crash" turns up too much).

---

### Post by sergioflorezm on 2007-10-31
Hello,
I'm a total Ubuntu newbie. I downloaded Gutsy a week ago and installed it without problems. These are my specs:

Compaq R4000
AMD Athlon 64 3500+
ATI Radeon Xpress 200M
2GB RAM

I have compiz working on XGL. In my case what happens is that the system will freeze when I open Firefox and it happens more often than not, I would say about 60% of the time. There's nothing I can do but manually restart the computer. However, when starting firefox the first time after reboot doesn't make the system crash then I don't have any problems for no matter how long I leave my computer on. It can go on for days as long as the it manages to start firefox without crashing.

---

### Post by esemba on 2007-10-31
same problem as other. My problem is fixed by uninstalling restricted nvidia driver and returning back to the nv driver. Problem usually occurs while hdd is in work (copying large files via nfs or smb etc).

My spec:

Ubuntu 7.10 32bit
nvidia gf go 7600
amd turion x2

---

### Post by dcherryholmes on 2007-10-31
I am also getting the same kind of hard freeze/lockup.  I tend to retain control of the mouse pointer, but I can't select anything, and no keyboard controls.  I am using a Thinkpad R52 with an ATI x300 card.  I had no problems under Feisty, and I've tried using the radeon, ati, and fglrx (adding xgl for the last one).  I have not seen it lock up without compiz running under any of the three driver scenarios, so for me it's really a question of retaining the eye candy (and I like my eye candy).

---

### Post by nanbudh on 2007-10-31
i have gutsy troubling me since two weeks now. i have athlon 64 2800+, 512 MB RAM, asus K8S-MX motherboard and 80 GB SATA Hard disk. I earlier installed via desktop CD and it had corrupted graphics along with freeze ups. then i installed using alternate cd and now grpahics are ok but freeze ups are there.
I donot have any extra graphics card. only integrated one.

---

### Post by spamhippy on 2007-11-01
well- still no crashes on this end & it sounds like from sergioflorezm that ATI doesn't do this on clean install (can anyone else confirm that ?) if so- then the problems with ATI  are probably silmilar to the problems with NVIDIA. the NVIDIA thing seems to be an upgrade issue. -that's my guess. good luck everyone.

---

### Post by Gonkerd on 2007-11-01
I've changed my video driver from nvidia to nv, no freeze or crahs after that. Except when i use cisco vpn client, but i think that's another problem.

Changed back again to nvidia drivers, my xorg proces was running wild and my audio was broken when playing movies

---

### Post by nanbudh on 2007-11-01
Guys i don't think the root is nvidia drivers because its not the common factor in all the reportings. Lets try to find out the common factor. Maybe SATA drive is the common factor? what say you? I am desperate to find out a solution. A project of mine has come to a stand still because of gutsy freeze up. i dont want to  revert back to an earlier version.

---

### Post by OldGaf on 2007-11-01
I have a sata  drive.

I also don't think it is an Nvidia issue as I have used various drivers installed in various ways.

---

### Post by Wallace on 2007-11-01
SATA drives too, with nForce chipset.

I'm seeing the problem on Ubuntu server so I'm not even running the NVIDIA graphics drivers.

---

### Post by macu on 2007-11-01
Hi guys,
I have problem with Gutsy. Me computer sometimes freezes. It takes one minute.
Here is the message from syslog.

Nov  1 15:45:48 athlon-v kernel: [ 1726.574322] hdb: lost interrupt

I want to solve this problem, don't anybody now how?

My configuration:
AMD Athlon X2 3800+, ASUS M2V, ATI Radeon X1600Pro, 1 GB RAM, 1x DVD-ROM,1x DVD+-RW.
Ubuntu GG 64bit

---

### Post by esemba on 2007-11-01
well, maybe sata, but why the change to the nv drivers fixes the problem?

---

### Post by cozmic charlie on 2007-11-01
> **nanbudh said:**
> Guys i don't think the root is nvidia drivers because its not the common factor in all the reportings. Lets try to find out the common factor. Maybe SATA drive is the common factor? what say you? I am desperate to find out a solution. A project of mine has come to a stand still because of gutsy freeze up. i dont want to  revert back to an earlier version.

I agree - my freezing only occurs when I am copying files.  It appears that thier may be mutiple problems because in some cases nv does fix it and some it does not.  In my case it does not.  I can run any program  fine but once I go to copying certain files it locks up.  FYI - I have the same problem in Fiesty.

---

### Post by Cresho on 2007-11-01
I been copying files from my backup drive into my hardisk.  Locks up.

---

### Post by jfinnan on 2007-11-01
I'm by no means an Ubuntu power user, but I did notice some odd behavior with Firefox and Gutsy.

If I have a single instance of Firefox open, I do not have any problems all day with Gutsy.  However, I usually don't work this way, and usually have one particular instance of Firefox open, usually minimized, as I check webmail with it from time to time through the day.

What I have noticed is that if you run the command "free -m" to view your memory, the "free" mem is of some value.  But, if you open a second instance of Firefox, it is reduced by about 10Mbytes.  If you close that second instance of Firefox...leaving the original instance open....you will notice that the free mem doesn't return to the previous value when there was just the single Firefox instance running.  Now, open up multiple instances of Firefox, and that free mem will consistently drop, but will not be freed up you close those extra Firefox instances.  Again, as long as a single instance of Firefox remains open, this is the case.  Once I then close that original instance of Firefox, the free mem jumps back up.

It almost looks like firefox has a memory leak when multiple instances are run.  I think in my case, a long day of opening and closing other instances of Firefox, while keeping my webmail instance open, is causing the drops in free mem to the point where it crashes the system.  At least, that is what appeared to happen when I kept opening and closing instances in an attempt to reproduce this problem.  I was able to get it to crash X.  Like many of you, the desktop freezes, and I cannot do anything.  Eventually X restarts, but of course all my work is gone, and my network connections have been closed.

Not sure if this helps or not, but was my observation on my particular PC.  I'm running Gutsy (new install) on a Dell Latitude D620 with the Nvidia display chipset.  I have 2GB of RAM, and I had the same problem with or without having the either the NV or NVIDIA display driver, and/or the desktop effects enabled.  It is extremely annoying, but so far the only real problem with Gutsy that I have.  But yeah..it sucks.

---

### Post by ArchangelUriel on 2007-11-02
Well same problems here...

Laptop Configuration

Acer Asprire 9303

AMD Turion 64 x2 (TL-52).
2GB RAM DDR-2 
NVidia GeForce Go 7300 (pci-e)
NVidia GeForce 6100 (onboard) (hopefully disabled)
BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (Broadcom 4318 )
Hitachi 140GB SATA HDD

Ubuntu 7.10 Gutsy Linux  2.6.22-14-generic

--------------
What I have found out 'till now... 

1) New Nvidia drivers (100.xxxxxxxx) caused the same problem even in 7.04
2) Some say about firefox, but same thing occurred even when I only used Opera
3) Open source drivers for Nvidia (nv) seem to solve the problem
4) Compiz-Beryl seem to not affect the problem (I have the same problem even when these are down)
5) Somewhere I have found that the wireless card seems to be the root of the problem. I uninstall the firmware and the problem persist.
6) Have tried to downgrade the Nvidia drivers (even with envy) and the whole thing goes to hell. 
7) Nvidia seems to be aware of the problem. There is a bug report somewhere in the nv-forum but I was unable to find it.
8 ) Nvidia beta drivers didn't solve the problem.
9) Most ppl having this problem seem to own Nvidia 7xxx and 6xxx video cards.


So, till now, the only solution is to use the open source drivers (nv) and forget the glx (all the wobby windows of the Compiz). If you need your pc for anything else except 3D graphics (games) and can leave without compiz, us the nv drivers 'till the developers (developers, developers) of either Nvidia or Ubuntu find a solution (and it will be soon, 'cause so many ppl have this problem).

P.S. I see that the same thing happens with ATI. I know nothing about it (I do not own one to test).  It may (IT IS JUST A SPECULATION) be some problem in the kernel (2.6.22-14) cause other linux dists (gentoo, debian, ...) seem to have the same problem. So maybe there is some conflict in the drivers of nv and ati with the latest kernel.

---

### Post by jb5 on 2007-11-02
In an effort to determine a common factor.

_Machine 1_

ASUS P5LD2 SE i945P Socket 775 6-channel audio ATX Motherboard
Intel E2140 Pentium Dual Core Socket 775 2x1.60GHz 1MB Cache 800FSB
MSI 7300 256MB GDDR2 (512MB TurboCache) DVI VGA TVO PCI-E Graphics Card
2Gb ram DDR2
2 -SATA  - HDD
1 SATA   - optical drive
1 - speedtouch USB modem
1 - nova-T-500 DVB tuner pci card
1 - keysonic wireless keyboard (USB)
Gutsy (64)
MythTV

Had no problems with this machine apart from sometimes it crashes when booting up. i.e. The ubuntu logo appears and the progress bar stops almost at the beginning.

_Machine 2_

Gigabyte GA-965P-DS3P Socket 775 1333SFB iP965 SATA 8 channel audio ATX
Intel Core 2 Duo E4300 1.86ghz Socket 775 FSB800 2MB Cache
256MB sapphire X1600 PRO
2GB ram DDR2
2 - SATA HDD
2 - PATA optical drives
1 - speedtouch USB modem
PS2 - keyboard & mouse
Gutsy (64)

This is the machine that exibits the "freezing" problem. On machine 2 it takes the following form :-

The panels become unresponsive. I can move the mouse but cannot select any of the menus or icons on either panel apart from the following exceptions; system monitor; network monitor.
I can still <alt>tab between opened applications and continue to use them as normal. 
I can <cntrl><alt>backspace to log out. 
When I login again the sytem panels behave normally again. 

Machine 1 does not get the same usage as machine 2, but I hadn't noticed a problem with it and so upgraded machine 2 to Gutsy 64 as well. The first time I upgraded I left my home folder as is. As I was getting this freezing problem I wiped everything and started from scratch. Problem still occurs!

It does not matter if I have desktop effects on or off. I can reproduce the behavior without running firefox at all. Also the memory usage is not consistent across methods used to measure it, as per earlier post #23 in this thread.

---

### Post by johnchud on 2007-11-02
firstly i have asus f3tc notebook amd tl52
120 sata
2048 ram
now running gutsy after a clean install after feisty ran amok
ah yes the graphics the 7300 geforce

when running standard xorg have no problems with lockups
unfortunately when i enable xorg with GLXvisuals, from any source there begins the headaches hard shutdown to get computer back

as for blaming firefox and multiple instances not likely as i run Opera and guess what even this is prone to freeze with visuals enabled, no keyboard or mouse
put original xorg back in place and all is sweet no visuals but i can live with that, so long the computer dont freeze
and this is not just with gutsy as had the same problem on feisty
the one thing i see regulary here is AMD but thats my thoughts only

---

### Post by onandon on 2007-11-02
Could this related to x server and the video driver? 
Gusty uses x server X11R7.2. I could not find the release note of it. But in the release note of X11R7.3, it mentioned some bugs
[http://xorg.freedesktop.org/archive/X11R7.3/doc/RELNOTES.txt](http://xorg.freedesktop.org/archive/X11R7.3/doc/RELNOTES.txt)
 Could those bugs related to the freeze/lockup/crash issue?
> Not all bugs could be fixed in time for this release, and the following known
issues are regrettably left in at this time, to be remedied in later point
releases of the modules involved:

Bug #7248:  Multiple PCI domains no longer work on Linux.  This has been
    	    present since the 1.3 server, at least.  It is expected to be
	    fixed on master (to be server 1.5), and a minimal fix may be
	    backported when that happens.
[COLOR="Red"]Bug #7512:  Memory leak with GLX pixmaps.  This couldn't get tracked down
    	    in time for release.[/COLOR]
Bug #11796: Two-color cursors misrendered on big-endian systems.  The problem
    	    was not fully understood at time of release, and the interim fix
	    was not included.
[COLOR="Red"]Bug #11802: When the appropriate input driver is not found for static
    	    configuration, the server may crash.[/COLOR]
[COLOR="Red"]Bug #12055: Server crash with compiz.  Reporter didn't have time to follow up.[/COLOR]
Bug #12145: In traditional (multi-Screen) multihead mode, the cursor may be
    	    stuck on one of the heads.  This is a bug in evdev which may also
	    exist in other input drivers, and will be fixed in upcoming point
	    releases.
Bug #12286: Bug in libwfb, which arrived too late to make it in.
bug #12291: Failure in an error path of the new input code may lead to
    	    server crashes during server exit.  This should have made it in,
	    and was an oversight.


PS: My video card is NVIDIA G6600. Freeze happens with both nv and nvidia driver. All the suggestions mentioned about modifying xorg.conf or module files DO NOT help. Currently the only solution for me is to use VESA driver. I am thinking about downgrade to 7.04.

---

### Post by OldGaf on 2007-11-02
> **ArchangelUriel said:**
> Well same problems here...
It may (IT IS JUST A SPECULATION) be some problem in the kernel (2.6.22-14) cause other linux dists (gentoo, debian, ...) seem to have the same problem. So maybe there is some conflict in the drivers of nv and ati with the latest kernel.

I just switched to Debian and finally I have no problems!

Kernel: 2.6.22-2-686
New Nvidia drivers (100.xxxxxxxx)

---

### Post by OliverHaag on 2007-11-02
I've switched to the 2.6.23.1 vanilla kernel and it's working fine now, looks like the ubuntu-devs messed up the kernel-sources :/

---

### Post by lanzen on 2007-11-02
So it might not be the nvidia drivers after all?

I get complete freezes, no mouse movement, no nothing. I was thinking to downgrade the nvidia drivers as someone suggested as it was working all right before.  In my case nv seems to work fine.

Anyway, this is what I got:
AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
Operating System:       Linux-x86_64 (Gutsy)
NVIDIA Driver Version: 100.14.19
Graphics Processor:     GeForce 7300 LE
VBIOS Version:             05.72.22.43.12
HDD:  2 sata 

My laptop, an Acer 1524 with amd64 3400+  single core, ide hard drive, nvidia Geforce FX Go5700 and driver 100.14.19, has never had a problem and ubuntu and compiz run flawlessly

---

### Post by nanbudh on 2007-11-02
my Machine: AMD Athlon 64 2800+, 512 MB RAM, 80 GB SATA SAMSUNG HArd Disk, LG 700E monitor, no extra graphics card, ASUS K8S-MX-UAYKZ motherboard,
Installed from :Earlier from AMD64 desktop cd and problem was freeze-ups along with corrupted graphics.
then installed from alternate AMD64 Cd and now the problem: freeze-ups.
Software used when problem occurs: Firefox(opening an instance, loading a page, scrolling while the page is not done, minimizing a window, any of this at times with simulaneous synaptic, pidgeon or totem), OO Writer(opening an instance, minimizing,any of this at times with simulaneous synaptic, pidgeon or totem), update manager(while installing limewire deb package, while scrolling the available updates, while downloading a package).
These are outputs of free -m commands:
*************************
shavin@ubuntu7:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           468        462          6          0         51        143
-/+ buffers/cache:        267        201
Swap:         1968          0       1968
shavin@ubuntu7:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           468        463          5          0         29        107
-/+ buffers/cache:        326        141
Swap:         1968         35       1932
shavin@ubuntu7:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           468        462          6          0         25        108
-/+ buffers/cache:        329        139
Swap:         1968         35       1932
shavin@ubuntu7:~$ 
*********************************
Is just 5/6 MB free memory not unusual?

Somebody please come up with a solution.

---

### Post by OnSite511 on 2007-11-03
I couldn't stand the freeze/lockups, so I downgraded to 7.04; all graphic and drivers the original versions for 7.04 and all beryl eye candy and so far no freezes. I'll keep monitoring this forum until someone finds an appropriate fix.

My box:
AMD 64x2 4200+
Operating System: Fiesty
NVIDIA Driver Version: nvidia-glx 1:1.0.9631
Graphics Processor: GeForce 7300 GS
HDD: 1 sata (MCP51)
DVD: 1 sata (MCP51)

---

### Post by Carbonfish on 2007-11-03
Oops. Just realized that this is the 64 bit forum. Sorry. .

KC

---

### Post by arkeo on 2007-11-03
Hi all,

I've been reading these fora for a while, but this is my first post.

I came here looking for solutions but it seems I can only contribute to the statistics:

Asus F3TC
TurionX2-TL56
1GB ram
GeForce Go 7300 128MB
SATA HD (at least I think, if I remember correctly)

Never had a problem with 7.04, with all the bells and whistles enabled. Upgraded via network to 7.10, Firefox started to completely block my system, as has been already written here: no possibility to kill the X server or switch to console, just a hard reboot.

At first I thought it had something to do with the way Firefox had to be modified in 7.04 to support Flash and Java, so I did a clean install of 7.10 from CD, but nothing changed: plain vanilla Gutsy Gibbon, when asked if I wanted the restricted drivers I answered yes, and Firefox would hang my system exactly as it did before.
I'd like to add that I could copy more or less 10GB of backup from an external HD after this new install, and I didn't see a problem. So I'm not sure this has anything to do with the SATA driver.

I'm writing this with the nvidia driver disabled, back to "nv", which seems to have solved all my problems: it's been 3 days without a single crash. Firefox works just fine...

It's really a shame that such a bug exists in 7.10, although I'm not placing blame on anyone; otherwise Gutsy would have been one of the best Linux distros I've ever seen, especially when dealing with restricted drivers or codecs.

Hope to see a patch soon, or an update or something...

Arkeo

---

### Post by nanbudh on 2007-11-04
i think this is the first release which has so many freeze ups and hardware problems. elsewhere on forums guys are talking that gutsy is made just for DELL and there are many issues on HP and Compag laptops. I think its time to acknowledge that gusty has flopped. I am going back to fiesty soon. i was on dapper all the time and it will be a new version for me compared to that :-). Hope some patch or fix comes up soon.

---

### Post by jonah1980 on 2007-11-04
to be honest i got some lock ups on feisty also, just not as frequent. back then i put it down to me having 4gb of ram and it not liking that, though i never found out what the problem was. my machine has locked twice this morning despite going a few days without locking at all. what is that all about!! seems that a lot of people having this problem (like me) are using geforce 7300 cards.

---

### Post by jonah1980 on 2007-11-04
hi can anyone please post more info with this problem to this bug report as there is little info for the devs there thus far: [https://bugs.launchpad.net/ubuntu/+bug/157777](https://bugs.launchpad.net/ubuntu/+bug/157777)

thanks guys. hopefully we'll get this fixed...

---

### Post by nanbudh on 2007-11-04
There is another thing i forgot to mention regarding my gutsy freeze-ups. It is that the freeze-ups have happened only in the first few minutes after booting up. Once it starts (i am tempted to say "warmed up") a little, it then works on okay.

---

### Post by Bokonon on 2007-11-04
Similar boat here,  but I suspect there may be more than one type of problem floating around.

On my system that has trouble, I share similar components to others here.
AMD64X2 4400+, nVidia chipset, Gusty (Upgrade from Fiesty), GeForce 7300, nVidia + Sil 3132 SATA chipsets both with drives attached.

My two laptops are working fine.  (one SATA, one IDE, Intel chipsets, one with nVidia, one ATI video)

---

### Post by Tteddo on 2007-11-04
Same problem here:
Gutsy 32 bit
GeForce 7300 GS
Dual Core Athlon 64
Dual SATA Drives

I can only run the nv driver, anything else caused hard locks. Worked fine in Win2000. My other machines all have ATI cards and have no problems. I tried the idle=poll kernel parameter from the nVidia site also.

Just realized this is the 64 bit forum, sorry...

---

### Post by Pinoy915 on 2007-11-04
I'm running Ubuntu 7.10-AMD64 with AMD64 X2 4200 and NVIDIA 7300GS. For my temporary solution, I just changed my powernowd settings from the default. So far, it doesn't crash as  often. I didn't like using the NV driver.

Uh oh, this method doesn't work with the 64bit version of Ubuntu. it was working for me when I had 32bit installed.

---

### Post by joshuacollins on 2007-11-04
hey all,

same problem here.   ubuntu gutsy freezes after about 30sec to 1min from the time it starts up.

this might be of use to you.   my system has been COMPLETELY stable until i installed the most recent compiz updates (yesterday).    i turn on my computer today and it is screwed.

some people were recommending switching the nvidia drivers but i notice there are also ATI and Intel users reporting the problem as well.     has it been confirmed yet that this new version of Compiz is actually causing the problem?

and yes, for some reason it freezes a couple seconds after i start firefox...    i can move the mouse but cant click anything, cant even ALT+CTRL+BCKSPC...   totally locked.

:(   :confused:

---

### Post by Cresho on 2007-11-04
doing transfer files at the moment on to a ntfs partition.  I noticed that if i did a usb or internal ntfs partition on my rig, it would lock up.  So i decided to go ext3 and test out the file transfer.  When i had no ntfs partition on my pc, it was on for 3 days.  with ntfs partition on  a drive, it locks up.  still doing tests.

---

### Post by chris_ak on 2007-11-04
This problem is caused by the latest NVIDIA driver, and is mostly found on GeForce 7 series cards.  NVIDIA is aware of the problem and supposedly it will be resolved in the next release.  For now, the best way to minimize this problem is to boot with the irqpoll option, and keep compiz stuff off, or at least minimal.  At the very least it will allow you to use the NVIDIA driver instead of the NV driver.  You can add the irqpoll option by editing the kernel options at bootup.  If you edit at bootup, the changes will only be temporary so you can just try it out for now then make it permanent if it seems to work.  This page gives good instructions on how to edit boot paramaters:  [http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

Personally I am just leaving desktop effects off until the driver gets updated.  However, I have had pretty reasonable stability with the effects set to "normal".  No cube or anything like that.

---

### Post by strikeback03 on 2007-11-04
Guess I'm relatively rare in that I had freezing issues with Feisty.  The have gotten much worse since upgrading to Gutsy though.  With Feisty the freezes seemed to be connected to Firefox, almost always it was when closing Firefox after using for a while.  Everything locked up, no mouse or keyboard.  With Gutsy I don't even need to touch Firefox, sometimes it will not even finish booting without freezing, sometimes it freezes after boot and then sitting still.  I never installed or enabled any desktop effects in either version, but I am using a 1920x1200 screen.

My System:
E6600
Foxconn P965 board
2GB Corsair RAM
2 SATA HDD
1 SATA optical
nVidia 7600GT
Realtek wireless card

Also installed 7.10 on my desktop at work.  Have not had much time to run it, but no issues yet.  That system is:

overclocked Q6600
MSI P35 board 
2GB Corsair RAM
1 SATA HDD
1 SATA optical
nVidia 7300GT

---

### Post by zippy028 on 2007-11-04
Maybe this will help some of you as it did for me.

[My Fix]("http://ubuntuforums.org/showthread.php?t=594196&highlight=freezes+resolve")

---

### Post by Cresho on 2007-11-04
> **Cresho said:**
> doing transfer files at the moment on to a ntfs partition.  I noticed that if i did a usb or internal ntfs partition on my rig, it would lock up.  So i decided to go ext3 and test out the file transfer.  When i had no ntfs partition on my pc, it was on for 3 days.  with ntfs partition on  a drive, it locks up.  still doing tests.

ill reply to my post.  after constant screwing around, I figured that my temporary pc has a problem.  I know your pc locks up if its clocked differently or if the voltage is off.  I am using 3 different types of memory so i decided to change the bios setting from detection by spd to mannual and lowest ram speed.

GUess what?  No more pc problems.  hope this helps.

---

### Post by strikeback03 on 2007-11-04
After reading around the bug reports on launchpad, I tried a few of the suggestions.  Disabling the nvidia driver through the restricted driver manager didn't help much, I still had a crash within 10 minutes of boot.  Setting maxcpus=1 seems to make the system much more stable, have not had a crash yet after a few hrs of heavy Firefox use.  Is there a kernel upgrade somewhere to improve compatibility with Intel multi-core processors?

May or may not be related, but I have to set the all_generic_ide kernel option to be able to boot, and also have noapic and nolapic set.

---

### Post by jaffa_nz on 2007-11-05
Kia ora

[http://ubuntuforums.org/showpost.php?p=3275045&postcount=610](http://ubuntuforums.org/showpost.php?p=3275045&postcount=610)

[http://ubuntuforums.org/showpost.php?p=3134000&postcount=544](http://ubuntuforums.org/showpost.php?p=3134000&postcount=544)

[http://ubuntuforums.org/showpost.php?p=3305810&postcount=635](http://ubuntuforums.org/showpost.php?p=3305810&postcount=635)

these provided some stability.

This bug is not strictly related to Video Driver, this said, topics that suggest changes related to drivers other than INTEL (not many for this, but what can we do with onboard working cards) should be followed.

Multi-core machines are more affected.  i'm on a dell d620 dual-core and until i followed above i couldn't post prior to hanging, now, its just a bit later.  Certainly my pc lasts longer without FireFox, but who lives like that! lol

Someone suggested a kernel upgrade to later than 2.6.22-14-generic SMP; could someone please post how to move to the later one that proved stable???

cheers all.

---

### Post by eligos on 2007-11-05
> **chris_ak said:**
> This problem is caused by the latest NVIDIA driver, and is mostly found on GeForce 7 series cards.  NVIDIA is aware of the problem and supposedly it will be resolved in the next release.  For now, the best way to minimize this problem is to boot with the irqpoll option, and keep compiz stuff off, or at least minimal.  At the very least it will allow you to use the NVIDIA driver instead of the NV driver.  You can add the irqpoll option by editing the kernel options at bootup.  If you edit at bootup, the changes will only be temporary so you can just try it out for now then make it permanent if it seems to work.  This page gives good instructions on how to edit boot paramaters:  [http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

Personally I am just leaving desktop effects off until the driver gets updated.  However, I have had pretty reasonable stability with the effects set to "normal".  No cube or anything like that.

I'm pretty sure that the freezes occur for more than one cause, acording to that i've read, maybe there are three different situations:

1.- Nvidia Drivers / Desktop Effects 
2.- Firefox memory leak???
3.- xorg server / kernel problem???

In my case, the freezes seems to appear after io enable my wifi drivers (broadcom) through ndiswrapper

P.S.: installing 32-bit gutsy doesn't stop the freezes, so this is not a 64-bit only bug

---

### Post by ozman_rulez on 2007-11-05
yea i have the same problem it will just stop responding period. Im thinking its my vid card the nvidia driver maybe but cant confirm tho. It doesnt matter what I have running it will still freeze very random.I found a drive with fiesty fawn on it,has never gave me any of these problems. So maybe it is just gutsy I dont know but I hope it gets fixed.

---

### Post by spooked on 2007-11-05
Same Problem: Intermittent total lockups with Gutsy requiring poweroff reboot to fix.

I was using nvidia drivers on a Dell Inspiron 5160, but when I upgraded to Feisty, the screen would not come back after suspend.  I hoped Gutsy would fix, but did not. After upgrading to Gutsy,  I changed xorg.conf from nvidia to nv and uninstalled nvidia-glx, which fixed the suspend issue, but I had a new problem,  the lockups.

After reading this thread, I uninstalled (even though I didn't think I was using)  linux-restricted-modules and nvidia-kernel-common and have not had a lockup since.

Hope this helps.

---

### Post by mkenk on 2007-11-05
I am experiencing frequent crashes, requiring a hard reset - the pointer freezes, sysrq keys don't work, the whole system is completely hosed. 

Just wondering if anyone experiencing this kind of hard crash is using any restricted drivers other than nvidia. I have a sneaking suspicion that it may be the wireless drivers (Broadcom in my case) not playing nicely with the kernel. Also, I can't really get my hands on a log that shows the crash, so if anyone has any suggestion on how to get the real debug info, I'd be glad to provide that to the devs. 

The funny thing is, it usually happens when I just start firefox, but if it doesn't crash immediately, it's good for a while and will run for hours with no crashes. Another crash occurred when I started a gftp connection, and I had one with azureus running full tilt.

---

### Post by strikeback03 on 2007-11-06
My problems might be wireless related (RTL8185), but testing with either 1 CPU off or with killing powernowd has seemed to greatly increase stability.  Have to use it a while more to see, but at least it is usable now (currently running both cores and powernowd removed).

---

### Post by _polarix_ on 2007-11-06
I have the same problem with NVIDIA 7200gs (PCIE):
- requiring a hard reset 
- the pointer freezes (but sometimes come back)
- sysrq keys don't work
- the whole system is completely hosed
- frequent crashes
- no ping, no ssh when freezed.

Clean install of Gutsy with nvidia-glx-new 100.14.19.

I have removed restricted drives and now my uptime is 11 hours without problem. Very improved stability with open drivers nv.

PS.: For other problems (SATA) i must boot with noapic and nolapic parameters.

Hope this help.

---

### Post by jb5 on 2007-11-06
> **Cresho said:**
> doing transfer files at the moment on to a ntfs partition.  I noticed that if i did a usb or internal ntfs partition on my rig, it would lock up.  So i decided to go ext3 and test out the file transfer.  When i had no ntfs partition on my pc, it was on for 3 days.  with ntfs partition on  a drive, it locks up.  still doing tests.

Well that could be an implication for me. 
Machine 1 - Dual core, n-videa 7300 card, no ntfs partitions, not noticed a problem.
Macine 2 - Dual core, ATI X1600 pro card, several ntfs partitions, freezing occurs.

Might this be a factor for anybody else?

---

### Post by komsas on 2007-11-06
> **jb5 said:**
> Well that could be an implication for me. 
Machine 1 - Dual core, n-videa 7300 card, no ntfs partitions, not noticed a problem.
Macine 2 - Dual core, ATI X1600 pro card, several ntfs partitions, freezing occurs.

Might this be a factor for anybody else?

I have ntfs partition and have random freezing. I think people who have random freezing must say if they have ntfs partitions.

---

### Post by mkenk on 2007-11-06
I do have a ntfs partition, but the crashes don't occur when accessing it. Doesn't seem to be a pattern, which makes it hard to replicate.

---

### Post by eligos on 2007-11-06
i don't have a ntfs partition

---

### Post by Pinoy915 on 2007-11-06
How far are they coming along with the fix for the NVIDIA driver? It must be it for my system because I have no problems when I use the nv driver. (Can't really run games with nv)

---

### Post by emil.s on 2007-11-06
But why do my server crash!? I don't even have X installed!
Now i have a uptime off 10 days, but if i start a torrent, it's dead in some hours...

It worked fine with Edgy for more than one year...

EDIT:
And i don't have an NTFS partition, and i don't have a multicore CPU. Just "normal hardware":
[http://sandnabba.se/phpsysinfo/](http://sandnabba.se/phpsysinfo/) ;)

---

### Post by Jangalian on 2007-11-06
Hi guys, 
after multiple installations of [k]ubuntu Gentoo and Debian  I've fixed installing the 32 bit flavor of firefox in a fresh installed Gutsy  using a script I've found here in the forum... no more freezes until now (few hours). I've also switched from Kde to Gnome and I'm running compiz + avant window navigator happily with original nvidia drivers.
IMHO this is a distro related issue as I had no problems with the Sabayon (except the usual KDE issues). I'd suggest to test the live live CD of this gentoo based distro.
Just for information I'm running Linux on a A6K asus laptop, 1,2 Gb RAM, nvidia Geforce Go 6200 (with a FAT and NTFS partition). I've also disabled the automatic configuration of the wired  network card.
I Hope this will help somebody!

---

### Post by Wallace on 2007-11-06
Sorry, posted in the wrong thread

---

### Post by Pinoy915 on 2007-11-06
> **zippy028 said:**
> Maybe this will help some of you as it did for me.

[My Fix]("http://ubuntuforums.org/showthread.php?t=594196&highlight=freezes+resolve")

This worked perfect! I was trying to figure out how to install the previous driver but somehow my xserver crashes with old drivers installed. The reason was that I did not remove the restricted manager and core. From your instruction, I removed them and my xserver does not crash and everything works beautifully.

---

### Post by Tteddo on 2007-11-06
I tried Zippy's fix, but I have 
linux-restricted-modules-2.6.22.4-14.10
Instead of 
linux-restricted-modules-2.6.22.4-14.9
and was missing
nvidialinux-restricted-modules-2.6.22.4-14.9
in synaptic.
When I followed the directions, upon starting gdm it came up using the nvida driver, but if I rebooted, it said X couldn't recognize the card. I assume it's because of a kernel update I have?
What could I do to get around that? Well, after you point and laugh at the obvious question!

---

### Post by Sammyf on 2007-11-06
Same as Tteddo.

I removed 14.10 and installed NVIDIA-Linux-x86-100.14.09-pkg1.run from the NVIDIA page, and everything is stable and fine .. as long as I don't reboot. 
Upon reboot I always end up in X failsafe mode, and have to stop GDM, reinstall the 14.09 drivers (which tells me that no kernel is installed for this package and then rebuilds it), and restart GDM.
Still better than the random crashs I had with the newer "official" driver, but still annoying.

Any idea how to fix THAT?

---

### Post by _polarix_ on 2007-11-07
> **_polarix_ said:**
> I have the same problem with NVIDIA 7200gs (PCIE):
Clean install of Gutsy with nvidia-glx-new 100.14.19.

I have 2 NTFS partitions.

---

### Post by OldGaf on 2007-11-07
FYI......

I switched to Debian 4.0r1 because of this problem. At first I was running the stable repos and all was well - Latest Nvida drivers and Kernel 2.6.22.2-k7 (32 bit). No lockups at all.

Then I started upgrading various  apps from the testing repos..... Amarok, Superkaamba etc. Still no lockups.

Finally I fully upgraded KDE to 3.5.7 and also installed gspca, xawtv and what ever comes with to get my USB WebCam working..... something in this last round has caused the freeze ups to  come back.

Still the same Nvidia driver (100.xxxxx) and still the same kernel.........

Does this help narrow things down / count thing out?

---

### Post by jim_meech on 2007-11-07
I have very similar experience of crashes to the ones reported in this thread.
Google earth & firefox seem to be the main culprits.
Turning off compiz effects reduces the frequency of the crashes for me, but it still happens.
I am running 32 bit gutsy on AMD athlon 4200 x2, so not just a problem with 64 bit code.

Regards to all

jim

---

### Post by alex2035 on 2007-11-07
Same problems here, new machine, new 64 bit 7.10 install, after a while the system becomes nearly unusable, lockdowns, freezes, Firefox will blow away at any time, Iceweasel the same, Pidgin the same, xserver sometimes will come up with random changes in resolution, sometimes a call for a program from the menu just doesnt do nothing sitting there forever, and at times the system will not even boot up.
 I have AMD64 , 2 gig ram, ATI Radeon (not using Compiz).  
I had Elive before this, worked like a breeze but would not recognize my realtek network card so I had to switch. I see someone there having same problems with the 32 bit version on a 64 system so what gives? is this a recognized buggy version of Ubuntu?

---

### Post by OldGaf on 2007-11-07
> **OldGaf said:**
> FYI......

I switched to Debian 4.0r1 because of this problem. At first I was running the stable repos and all was well - Latest Nvida drivers and Kernel 2.6.22.2-k7 (32 bit). No lockups at all.

Then I started upgrading various  apps from the testing repos..... Amarok, Superkaamba etc. Still no lockups.

Finally I fully upgraded KDE to 3.5.7 and also installed gspca, xawtv and what ever comes with to get my USB WebCam working..... something in this last round has caused the freeze ups to  come back.

Still the same Nvidia driver (100.xxxxx) and still the same kernel.........

Does this help narrow things down / count thing out?

I may have spoken prematurely. I was trying to get foobilliard to work on the net and that hung my system. I left my system for 2 hours with top running and CPU usage is only 7%. I will monitory / test it further.

---

### Post by OnSite511 on 2007-11-07
> **jb5 said:**
> Well that could be an implication for me. 
Machine 1 - Dual core, n-videa 7300 card, no ntfs partitions, not noticed a problem.
Macine 2 - Dual core, ATI X1600 pro card, several ntfs partitions, freezing occurs.

Might this be a factor for anybody else?

It can't be the NTFS partitions. I had the freeze problem and I don't have any mounted. I had to revert back to 7.04, but will probably try the fix that zippy028 worked out when the weather turns poor and I can't play outside on the weekends. Then I can have a chance to install 7.10 on a spare partition. When I do I'll report back.

---

### Post by mckeja on 2007-11-07
OK, this has been a problem that has been difficult to narrow down. Specifically, the problem is that when things go haywire, its too late for debugging info.  I'm running an ASUS motherboard with P5K bios, 4gb RAM, an intel quad-core processor, and dual GeForce 8500 video cards. I also have a 500gb SATA drive with EXT3, NTFS, and XFS filesystems.  I'm running the 2.6.22-14-generic 64-bit kernel.

For the most part, things are fairly stable. I've run the system hard trying to generate problems so I could narrow down the search, and never found anything.  However, if **I let the system sit idle, that's when things start going funny**. This can take anywhere from 5 minutes to 4 hours before seeing results. Here's what I've observed:

 Sometimes, the computer locks up so tight that only the mouse moves. Sometimes the mouse doesn't even move, or moves very slugishly. At this point, the only recourse is to hard-boot with the power switch.
 Sometimes processes zombify and can't be killed even with the -9 switch. When this occurs, new programs lock up as zombies before anything visual happens.
 Sometimes, the filesystems become unavailable or returns bogus information. Specifically 'filesystem corrupt' errors. Nothing gets logged (the filesystem is corrupt and can't be written to, after all), but on restart there's no problems found. Again, when it occured, I couldn't do anything but hardcycle the power.  In all events, files that appeared completely mangled/corrupted/incomplete were perfectly fine after rebooting.
 Another time, the kernel forgot how to link to libraries. Any library that wasn't currently linked was completely unavailable. This made opening Firefox, or even gedit, impossible. However, while I had Terminal open, I could open a dozen other Terminals with no problems at all. Once I closed the last Terminal, I couldn't open any more. I had to hardcycle the power yet again.

 In all crash cases, nothing seemed 'wrong' until I tried to do something after being gone for an amount of time.

Some other observations: 
 The problems seem more severe when Firefox is open, but definately aren't limited to when/if Firefox has run. 
 Filesystem issues are more likely when one of the filesystems is an encrypted FS or an LVM partition. In fact, when I did a fresh install using the Alternate CD to install on an LVM filesystem, I had troubles keeping the system running for more than half an hour.
 Issues were almost non-existant when using an IDE drive instead of SATA, but still occurred.
 Using the restricted nvidia driver did not make a noticeable difference in stability.

---

### Post by jb5 on 2007-11-08
> **OnSite511 said:**
> It can't be the NTFS partitions. I had the freeze problem and I don't have any mounted. I had to revert back to 7.04, but will probably try the fix that zippy028 worked out when the weather turns poor and I can't play outside on the weekends. Then I can have a chance to install 7.10 on a spare partition. When I do I'll report back.

I think, as has been mentioned earlier in this thread, there are a number of different hardware configurations; software setups; even the symptoms that people experience differ from machine to machine.

A number of people are guessing that the nvidea cards / drivers are a cause, other people have problems with ATI cards / drivers. For some people a hard reset is the only solution, others can <cntrl><alt>backspace, the list goes on.

The only thing in common, so far as I can tell, is that people are having problems! 

NTFS partitions may not be a factor for your setup, but then n-videa drivers aren't a factor for mine!

I just hope that we can untangle this problem and find solution that works for all, this will probably mean exploring all avenues, some of which may well turn out to be dead ends.

 :)

---

### Post by alex2035 on 2007-11-08
My install is over an IDE Drive and the problems are word for word as Mckeja described.
Yes, after rebooting everything seems OK, but then again.

---

### Post by jaakan on 2007-11-08
> **jb5 said:**
> 

The only thing in common, so far as I can tell, is that people are having problems! 


the only things in comman are the kernel 2.6.22 and newer hardware.( x64 CPUs )

my p3-450mhz laptop never locks up.

x64 desktop, locks up
1. sometimes during clean install 
2. just as base Server
3. as ubuntu standred install
4. with or with NV drivers being used

---

### Post by jb5 on 2007-11-08
> **jaakan said:**
> the only things in comman are the kernel 2.6.22 and newer hardware.( x64 CPUs )


I would agree the kernel *_may_* well be the absolute common denominator, but I have no problems on one machine with a dual-core processor!

---

### Post by OnSite511 on 2007-11-08
> **jb5 said:**
> I think, as has been mentioned earlier in this thread, there are a number of different hardware configurations; software setups; even the symptoms that people experience differ from machine to machine.

A number of people are guessing that the nvidea cards / drivers are a cause, other people have problems with ATI cards / drivers. For some people a hard reset is the only solution, others can <cntrl><alt>backspace, the list goes on.

The only thing in common, so far as I can tell, is that people are having problems! 

NTFS partitions may not be a factor for your setup, but then n-videa drivers aren't a factor for mine!

I just hope that we can untangle this problem and find solution that works for all, this will probably mean exploring all avenues, some of which may well turn out to be dead ends.

 :)

I completely agree that we need to narrow our focus; believing that we should focus on commonalities, not exceptions. So far I think that the commonality may be SATA and the newest kernel. Can anyone else chime in on the thought that more disk access results in locking up faster than less disk access?

---

### Post by InlawBiker on 2007-11-08
I have just started experiencing totally random lockups.  It's locked up so bad I can't even cnt-alt-f1 to a tty. The keyboard does nothing.  I can wiggle the mouse around for a while then eventually it stops working too.  Nothing in the logs looks amiss.  This has been happening for 3 days now. 

This is on a feisty install that's been stable for 6 months.  I dual-boot to XP, XP never locks up.  So I don't think it's hardware.

Here are the recent changes I've done, so I suspect them in this order:

* Installed a new SATA dvd burner.  It's an Asus DRW-1814BLT RT.
* Installed newest Firefox
* Removed Beryl; added Compiz.  This was weeks ago though.

It also keeps asking me to install the latest VMWare server, even though I have the latest.  I had to remove the commercial repository from sources so it would quit bugging me.

I'm usually using Firefox when it crashes, but I'm always using Firefox since I'm a web developer.  

Ideas?

Greg.

---

### Post by InlawBiker on 2007-11-08
> **InlawBiker said:**
> I have just started experiencing totally random lockups.  It's locked up so bad I can't even cnt-alt-f1 to a tty. The keyboard does nothing.  I can wiggle the mouse around for a while then eventually it stops working too.  Nothing in the logs looks amiss.  This has been happening for 3 days now. 

Here's some more hardware info:
Feisty 32bit
Intel core2duo E4300 processor 
2gb RAM
nvidia geforce 7600gt gpu
Asus mainboard (P5N-E)
  - nvidia nforce chipset
  - nvidia nforce ethernet
  - no wireless

I have NTFS & SATA/Fat32 partitions that are almost never mounted.  Really, the lockups started about the same time as the Asus SATA drive being added.  The main disk is IDE.

---

### Post by ssadien on 2007-11-08
same problem here, random lockups.

i use nautilus for browsing occasionally then this happens and also mozilla when this happens.

there are some pages that i open with flash animations that slows the pc to a halt compared to doing the same in windows.

is it not maybe related to the flash plugin? just a suggestion. i have to use it so cant uninstall it.

machine: hp compaq nx6310 laptop.
at home: am2 with usual onboard stuff(gigabyte mobo).random lockups there too but not as frequent(prolly cos i dont use that pc that often)

---

### Post by tomot on 2007-11-08
I have 2 machines that both cause Gutsy to freeze.
At first I too thought it was related to what one was doing
prior to the freeze. But thats clearly not the case. 
I have tried  3 separate installs now  on each of 2 machines.

the freezing is not related to what program was running at the time,
nor has it anything to do with x86-64bit  or as in my case x86 32-bit versions.

bug reported: [https://bugs.launchpad.net/ubuntu/+bug/158378](https://bugs.launchpad.net/ubuntu/+bug/158378)

I hope this gets resolved soon!

---

### Post by Sammyf on 2007-11-08
I think the only real common point for all people is the kernel.
I don't have SATA and my system is an old fashioned athlon XP 2600+ (non 64 bit, single core) with a nVidia 7800GS.
Somehow, using older nvidia drivers solved the crashing issue, but now I have other issues, namely when I do eventually reboot I have to recompile the drivers everytime (or use X safemode)

As other prople have the crashing issues but have ATI, I think I just got lucky that reverting to older drivers helped my problem, but apparently it's NOT a problem with them.

The only thing I see in common in every post is the kernel :/

---

### Post by jonah1980 on 2007-11-08
i do have two sata hardrives, though i always blame nvidia mainly as crashes are worse with desktop effects and nvidia driver, my system doesn't last a min with those turned on.

but i think i've noticed a couple of sata driver errors on boot but it always flashes past. something about drivers not being loaded or not detected or something like that.

the other issue i'm having now is my machine won't shut down. i press to turn off and the splash bar goes down, gets to the bottom and then i have to switch off on the wall as it's just stuck at the splash with an empty progress bar...

---

### Post by blue-maya on 2007-11-08
I have a Dell  Inspiron 8500 laptop and installed Gutsy onto it.

The laptop consists of 1Gb ram, Nvidia Geforce go 4200 64MB graphics card, wifi (Atheros), dvd writer, 40GB IDE HD, Intel pentium 4 M mobile processor.

I also noticed random freezes. Pretty critical bug I think.
First I thought it was related to the amount of heath the machine produced. After installing the i8k kernel module and i8kmon deamon it was cool but the freezes remained.

I have no idea what the problem might be. Kernel perhaps?
And why is my HD mounted as a scsi device instead of IDE /dev/hda ?

---

### Post by Borg on 2007-11-08
mmm happens to me with Pigin running for deff, seen it happen a few times, also when setting up screansavers but that was only the once, not sure though if pigin was running as well

---

### Post by quasimodo69 on 2007-11-09
I thought I had it licked when I formatted the hard drive with a 3rd party program and did a fresh install of 7.10 on my machine.For 3 days no lock ups.I installed all I wanted to run and enabled the desktop enhancements.Then it started again.I could not go30 minutes without a lockup and shutdown-not a freez-I mean black screen and shutdown.

  I am back to using windows on this computers.I have the i386 version running and another AMD 32 bit chip and have no problems at all.

No NTFS partitions

My System=
AMD 64 3000 CPU 1GB ram VIA raid and SATA divers and North and South bridge
1 40GB IDE hard drive (Ubuntu be here) 1 5GB IDE hard drive (blank swap)
200GB SATA hard drive (Micro$oft be here=YEEUUCCH!)
40GB SATA hard drive (blank-FAT32) Video nVidia AGP 5600 GeForce
Sound Card Sound Blaster Live PCI MoBo Abit Av8
Crashes have occurred even without nVidia drivers installed-every time Firefox was running.
These were hard crashes where the system went down,black screen and computer buzzers
went off.A check of the system temp showed fine (113 degrees) and system monitor showed
no excessive memory usage.
I have used the driver for the nVidia card supplied with my card on the disc-and I tried
the drivers posted on their site dated 9/07/07 and same problem.
I also have not gained any functionality from the installed drivers for the video card
and have not enabled the desktop enhancement features ](*,)](*,)](*,)

---

### Post by Herm87 on 2007-11-09
I also want to add my two cents to the statistics.
The user "schmecklecker137" reported something he called "IRQ-Storm" in the post  [http://forum.ubuntuusers.de/topic/123283/30/](http://forum.ubuntuusers.de/topic/123283/30/) and stated booting with "apm=off acpi=off noapic" would help. It may work for him - my system can't boot properly without IRQ-control (no usb, no S-ATA, nothing but a console). Seconds before the crash /var/log/messages is filled up with errors and warnings from nearly every hardware component saying that they were unable to respond (in time). Then the system locks up and finally my keyboard blinks the message for a kernel panic.
So my experiences are:
- System does not crash while being idle (in terms of absolutely no input and no program except system services running).
- System crashes randomly - even with few input (mouse movement, network activity, just something). A crash while listening to music (amarok, alsa, truecrypt, fat) and browsing with FireFox is inevitable but not predictable (I can't say "everytime I use FireFox, it crashes"). If I leave the system alone with Amarok updating it's collection, it crashes, too.
Software:
- Gutsy x64 clean install
- ATI restricted drivers
- standard packages and settings + Amarok, TrueCrypt
- dual booting with MS WinXP
Hardware:
- ASUS A8N SLI Deluxe (nForce4)
- AMD Athlon64 3500+
- ATI Radeon X1950 GT
- IDE-HDD ext3 as root
- 2 S-ATA HDDs for files and data (yes, there is ntfs ro and fat)
- Hauppauge WinTV PVR 150

---

### Post by TalioGladius on 2007-11-09
Anyone found a fix for this yet?

---

### Post by InlawBiker on 2007-11-09
For some more anecdotal evidence, I've made a few changes and have not crashed in the last 18 hours or so.  I have MP3's and torrents going just to keep the system busy.

1. I noticed the cups system was upgraded right about when the lockups started.  So I disabled cups (printing service).  I'd be interested to know what version of cups was shipped with Gutsy.  I went from cupsys 1.2.8-0ubuntu8 -> 1.2.8ubuntu8.1 

2. I had a USB thumb drive plugged in, I removed it.

3. I upgraded the nvidia drivers from whatever was in the Ubuntu repository to the one straight off the nvidia web site (100.14.19).

So far so good...

This is Ubuntu Feisty 32bit.

Greg.

---

### Post by wppaas on 2007-11-10
I'll add my experience with hard locks on Feisty/Gutsy too

My ubuntu Gutsy 32-bit constantly hardlocks (keyboard not responding, no screen updates, needs reset) when using the proprietary nvidia driver and using firefox. The system is stable when using the open source nv driver.

I also had this problem on Feisty (32-bit) but not constantly as is the case on Gutsy. On Feisty it would hard lock once in a while on automatic login (and probably on startup of firefox)

System:

AMD Athlon64 3200
Nvidia FX-5200
SATA harddrives

Let me know if more info or testing is needed

cheers
WP

---

### Post by dark_construct on 2007-11-10
I too have been experiencing the freezing since upgrading to Gutsy.  I have however been able to re-create this problem consistently.

The problems always happens when i'm in Firefox or Opera, and a flash animation is running in another window or underneath.  For example, I visit a web page with a flash advertisement playing(tab 1).  Now I have another tab open(tab 2) and I visit ING for example.  When I log in and go to pay a bill, it freezes when it tries to open the month selector window, which is when it goes to open tab 3.  Anytime I have a freeze, there is always a flash animation playing underneath or in another window.

Also, when I turned on visual enhancements, the pages with flash would sometimes turn black.  It turns out that a flash page was almost always underneath.  If I removed that page or closed it, the black windows would be ok again.

When Firefox freezes, my task manager(xfc4-taskmanager) shows 96-100% usage, so I must kill it.  I think if I didn't have a dual-core, my system would probably become unusable.

I'm thinking that the upgrade must have changed a setting in my xorg.conf file and that the feature clashes with flash and how it draws windows.  OpenGL perhaps?

I'm going to compare my old xorg file from before the upgrade and post if I find any changes.

AMD 64X2 4600+ EE
4 gig ram 
NVidia 6150 on-board with dual-monitors

---

### Post by chorca on 2007-11-10
I have 32-bit Ubuntu, and i've been experiencing the same issue since day one.

For me, it usually happens while listening to music or while browsing a website in Firefox that has Flash.

As a couple other posters have stated, it does not happen when idle, but immediately after a button is clicked or a window is moved.

The system remains open, only Xorg crashes. I set up OpenSSH and SSHed into the box after it had frozen. Top shows Xorg using 100% CPU. It cannot be killed even with a kill -9. All processes seem to be running normally, though i have difficulty killing anything within Xorg, (such as any programs running when the crash occured) A shutdown -r now command works from SSH and will reboot the machine.

This appears to be an issue with Xorg hitting some sort of snag and immediately going to 100% CPU, which causes the desktop lockup. I'm not sure if this is related to Compiz or not, i'm going to try disabling desktop effects and report back.

---

### Post by Boricua on 2007-11-10
I have the same problem, running an AMD 64 with 64 bit Gutsy. In my case, the system locks completely, except for the mouse pointer, which keeps moving normally, as some have already reported. Sometimes, I have noticed a small reaction delay suggesting an incoming freeze but the machine reacts and keep working.
Today, I wasn't using Swiftweasel (or Firefox). The system locked when I was editing a document in OO 2.3. After a hard reboot, the system froze twice while using the rescue document feature of OO. However, the third time and before activating the rescue feature, I first deactivated the GL desktop (this machine has a nvidia card integrated in the motherboard and uses the restricted driver). The rescue went through successfully this time. Then, I restarted the special effects. The only common denominator I have seen in my case seems to always involve the desktop effects (compiz fusion; avant window navigator; screenlets). Hope this helps.

---

### Post by Ruud68 on 2007-11-10
hello, running for over a week now without any freezes, crashes or whatsoever. Removed my perfectly OK 2 GB of memory and swapped it with a 512 MB. Per direct problem is gone..... (see also earlier post).... My guess would be that it has something to do with large memory and PCI memory mapping (but hey, if I was a good guessor, I would have won the lotery :) ) Needles to say that also performance is gone :(

---

### Post by andy19 on 2007-11-10
> **spamhippy said:**
> i don't know about the ATI thing (i have an nvidia 7300 card..) but- i think i've fixed it (no crashes in the last day or 2..) here what i did.... i downloaded nvidia-xconfig & ran it (makes a new xorg.conf file -setup for nvidia...) you can get this tool from either the package manager or from nvidia's site under - driver downloads...

then.. go into recovery mode... type 'startx' - if it asks if you want to continue say 'yes'

go to....  /lib/linux-restricted-modules  

in your file browser click on 'view' and select the option 'view hidden files..

you should see a file called '.nvidia_new_installed  ' -delete that.

then open the package manager and unistall the following 2 packages....

nvidia-glx-new

nvidia-new-kernel-source


than install the packages......

nvidia-glx

nvidia-kernel-source


close all apps- 

click ctrl+alt+backspace  (takes you out of x..)

the click ctrl+alt+delete  (this reboots your computer)

make sure "nvidia" is in use in your xorg.conf file & don't mess with 'restricted drivers' - i think all that does is installs 'nvidia-glx-new' if you play with him & you don't want that. it sounds like from descriptions that 'nvidia-glx-new' or 'nvidia-kernel-source' might have a big @$$ memory leak somewhere- i don't know. as far as ATI goes- i can only guess- maybe ATI borrowed some ideas from NVIDIA & caught this bug? i'd go & see if i could find a hidden file in /lib/linux-restricted-modules- and see if a person can do more or less the same proceedure on an ATI. 

anyways- been running like this for almost 2 days now- have compiz on advanced options & emerald installed- everything seems to be working fine. well- hope this works for everyone- goodluck!

Hi,
I registered here just so I could say that this fix worked for me.  I'm on my 2nd day of running with this setup, and I have Compiz-Fusion and Emerald working perfectly with my Geforce 7300 card.

Thanks a lot, it was really relieving actually getting it working after a long time trying to figure out what was going on.


Just for peoples' information, this is my current setup:

AMD Athlon 64 X2 3800
MSI K7VTA3 motherboard
NVidia Geforce 7300LE PCI-E video card
160GB NTFS-mounted drive, 80GB EXT3 drive
both ATA, not SATA

---

### Post by Tteddo on 2007-11-10
Andy19, does it still work after you reboot? I did this, and it worked until I rebooted, then I got an error about couldn't configure video card and had to redo the instructions again to get it to come up.

---

### Post by Bluejacket on 2007-11-10
We have two computers

Desktop:
**Pentium 4 with hyper threading**
Memory 1,5 GB
**Kubuntu 7.10 32bit**
Dualboot with NTFS partition
**2 x IDE hard drives**
GeForce 7600 running latest driver installed with Envy
no other restricted drivers
Firefox 2.08
**no crashes**

Laptop:
**Amd Turion 64 X2**
Memory 2 GB
**Kubuntu 7.10 64bit**
Dualboot with NTFS partition
**SATA hard drive**
Geforce 7200 running latest driver installed with Envy
no other restricted drivers
Firefox 2.08
**constant crashes**

Major differences bolded. Kubuntu is not usable on the laptop, so we're forced to use XP on it.

---

### Post by Andrew MacDonald on 2007-11-11
It's quite possible that these freezes have many different causes. FWIW, I tracked mine down to shanty 64 bit Windows drivers I was using with ndiswrapper for my rt61 wireless card.

---

### Post by andy19 on 2007-11-11
> **Tteddo said:**
> Andy19, does it still work after you reboot? I did this, and it worked until I rebooted, then I got an error about couldn't configure video card and had to redo the instructions again to get it to come up.

I don't think I have tried rebooting yet....
Now that you say it might crash again, I don't know if I want to reboot :P

---

### Post by jaakan on 2007-11-11
server kernel 2.6.22 + apm=off acpi=off noapic seem to have helped my system

fingers crossed,

---

### Post by mac25 on 2007-11-11
Fairly new to this but so far, Same problems here, tried upgrade, now a new 64 bit 7.10 install, after some time the system becomes nearly unusable, freezes, Firefox will lockup at any time.
Feisty install that's been stable for 5 months. I dual-boot to XP, XP never locks up.(and doent get used) So I don't think it's hardware. I'm always using Firefox when it crashes.(i mosly just surf)

I have now switched to EPIPHANY web browser two and a half days ago. NO LOCKUPS. 
I cant even seem to crash it.
Software:
- Gutsy x64 clean install
- nVidiaI restricted drivers
- standard packages and settings 
- dual booting with MS WinXP
Hardware:
- ASUS M2N-MX (nForce 430)
- AMD Athlon64 4800+ X2
- NVidia 7600GT 256mb
- SATA2 HDD for files and data, ntfs/ext3
- 2gb pc800 ram

Dont know if this will help at all, but so far it has worked for me...

---

### Post by arsham on 2007-11-11
I've been reading this thread
Seems the problem came from upgrading to gutsy.
So , if it is about the kernel? or moduls? or the graphic card drivers?

I have a intel graphic card , and I had no problem with the latest updates in feisty

Wish you luck

---

### Post by SJI on 2007-11-11
Hello everyone,

I've been suffering this annoying Gutsy feature for a while now and have tried a few things to stop the hard lock-ups.

I installed Envy last night and used it to firstly remove the Nvidia drivers and then to reinstall them.

Reinstalling the latest drivers made no difference at all, however reinstalling the 96.43.01 drivers makes the system behave much better.

My system had got to the point were it was unusable as it would crash within 30mins and require a hard reset; no crash since installing the 96.43.01 via Envy.

HTH

Stephen

---

### Post by leona on 2007-11-11
I have a similar issue, I say similar because the system doesn't totally lock up, I can't do anything with it when it locks, but I can move the mouse around, can't click on anything or use the keybaord, ctrl+alt+backspace does nothing, its odd.

I have 3 machines and only mine is doing this, I notice that my other machines are on Kernal 2.6.20.16 and mine is 2.6.22.xx . as I saw someone mention kernal versions could this be the issue?

All other machines are nvidia based, though mine is the only 64bit one.

I hope a fix is found soon.

---

### Post by Herm87 on 2007-11-11
In my opinion, we are actually discussing three or four individual problems. There are
- unexpected hardlocks, probably caused by faulty memory mapping with 1GB+ RAM installed
- Xorg hangups with some application using incredible amounts of memory or
- Xorg hangups with some application using 99% CPU, probably caused by compiz and/or graphics drivers (in some cases Xorg can be killed with CTRL+ALT+BACKSPACE)
- kernel panics, probably caused by bad IRQ-handling (noapic seems to work) or removable storage devices handled by scsi-modules in general. Unplugging all USB-devices seems to have helped me (no crash in the last hours).

EDIT:
**SEEMED** to help. My system crashed the usual way, but it lasted much longer with less USB-devices installed. I was using my S-ATA-drive excessively, so I dont think you can make up a quantitative relationship between the scsi-modules and my kind of crash with kernel panic.

---

### Post by SJI on 2007-11-11
> **Herm87 said:**
> In my opinion, we are actually discussing three or four individual problems. There are
- unexpected hardlocks, probably caused by faulty memory mapping with 1GB+ RAM installed
- Xorg hangups with some application using incredible amounts of memory or
- Xorg hangups with some application using 99% CPU, probably caused by compiz and/or graphics drivers (in some cases Xorg can be killed with CTRL+ALT+BACKSPACE)
- kernel panics, probably caused by bad IRQ-handling (noapic seems to work) or removable storage devices handled by scsi-modules in general. **Unplugging all USB-devices seems to have helped me** (no crash in the last hours).

You're right. There are multiple problems in this thread.

My particular situation was resolved as per my previous post.

I'm running AMD64 4gb ram, dual monitors and an Nvidia card and I don't have compiz running
When my machine hard locks there's no mouse movement, no ability to task switch or swap to TTY. SSH to the machine fails also. The Reset button is the only recourse.

If i revert to the latest drivers, using Envy, the hard lock-up problem returns. Reinstall the 96.43.01 drivers via Envy and i'm back to being stable.

I've also tried running the machine with less than 1gb of ram when the hard locks occur and that made no difference at all.


HTH

Stephen

---

### Post by Tteddo on 2007-11-11
> **Herm87 said:**
> In my opinion, we are actually discussing three or four individual problems. There are
- unexpected hardlocks, probably caused by faulty memory mapping with 1GB+ RAM installed
- Xorg hangups with some application using incredible amounts of memory or
- Xorg hangups with some application using 99% CPU, probably caused by compiz and/or graphics drivers (in some cases Xorg can be killed with CTRL+ALT+BACKSPACE)
- kernel panics, probably caused by bad IRQ-handling (noapic seems to work) or removable storage devices handled by scsi-modules in general. **Unplugging all USB-devices seems to have helped me** (no crash in the last hours).

Mine is definitely the nvidia driver with my 7300 GS, under the generic nv it will run forever doing anything I want. I do have 2 gigs ram,  2 SATA drives, and dual core Athlon also.
I agree that I think we are seeing at least 3 different problems in this thread though.
Anyone know when nVidia is due to release a new driver? I know there is a bug report for my problem that even mentions the 7XXX series specifically.

---

### Post by arsham on 2007-11-11
Also I was experiencing with usb external hard (SCSI) , lock up
I had to upgrade to 2.6.23.1 , seems to be stable , but sometimes hangs again
Maybe that kind of driver (ehci) makes some memory leaks

---

### Post by Herm87 on 2007-11-11
My system crashed just right now (kernel panic), but it lasted longer than usual. I was still using an evil USB-mouse, though. I'll try again with an PS/2-mouse.

---

### Post by alex2035 on 2007-11-11
Besides all the problems that my machine shared with everybody it came with this: surfing with Iceape I opened a news web (lots Flash content), when I closed a second tab Iceape blew away from the desktop and all Flash little advert windows remained scattered on-screen, then after a minute the desktop begin flashing wild like a beacon, taskbar disappeared and I had to press the reset button. I decided to uninstall flashplugin-nonfree with Synaptic. I have no problems yet, no lockups, and no flash of course, any alternatives to replace the flash plugin?

---

### Post by arsham on 2007-11-11
I did a ssh session remotely to my computer
After freeze , I could see the top results , cpu normal , everythings normal
Even downloads are still going , chat session on a normal state , everything
And I started a reboot from ssh
Ok , the computer starts to rebooting , and nothing on display , still everythings hanged but the mouse cursor 
After all I can see the splash screen of shutting down , but with kind of creepy characters on the screen
It seems that the graphic card buffer is filled with garbage
I hope these information helps

My computer:
Centrino 1.6
1GB RAM
kubuntu gutsy
USB mouse
USB external HDD
Graphic card Intel 915GM

---

### Post by orthopod on 2007-11-11
Same thing was happening to me, untill I vacuumed out the dust over my video card, and CPU cooling fins (I usually run SETIathome always, so me processor is usually hot).  Can you check your temperature and see if that's a problem?  Might as well clean out your case, or try switching out your power supply too, as they can go bad.  I lost one power supply after one year, because my neighborhood had so many power outages, quick on/offs that it trashed the PS unit.

Don't forget about other types of issues too.

---

### Post by arsham on 2007-11-11
I have a laptop , so opening and getting dust , both n/a
just before gutsy , I used compiz/beryl and everything was fine
What happens after an one hour updating ( fresh install ) to gutsy that makes crash?
I believe this is a software problem.
Including , everything seems fine if I use my distro without compiz/AIGLX
I use a lot of programs daily :
Zend ( uses java )
Wingide ( a python based one )
swiftweasel ( firefox )
amarok
gaim
skype
acrobat reader
openoffice
vlc ( while I am watching a metal show :wink: )
Lots of konsole shells

The desktop manager is KDE

And there is no freeze , not once

---

### Post by alex2035 on 2007-11-11
> **alex2035 said:**
> Besides all the problems that my machine shared with everybody it came with this: surfing with Iceape I opened a news web (lots Flash content), when I closed a second tab Iceape blew away from the desktop and all Flash little advert windows remained scattered on-screen, then after a minute the desktop begin flashing wild like a beacon, taskbar disappeared and I had to press the reset button. I decided to uninstall flashplugin-nonfree with Synaptic. I have no problems yet, no lockups, and no flash of course, any alternatives to replace the flash plugin?

Correction: the machine lockups anyway, no CTRL+ALT+Backspace , dead, Streamtuner and xmms stopped playing, had to reset. I think this is at the heart of the OS, a kernel thing related probably with xserver ?

---

### Post by ekravche on 2007-11-11
Crashed for me yesterday, when I opened a music file. The entire os just froze. I could no longer switch using ctrl+alt+f1 to do a sudo restart from the command line.

---

### Post by jaakan on 2007-11-11
> **jaakan said:**
> server kernel 2.6.22 + apm=off acpi=off noapic seem to have helped my system

fingers crossed,

After 2 hours of trying to make it crash I got it to, it does it in the same way but it took some work to do.

has anyone tested the 2.6.23 or .24 kernel.

give me all the steps to compile it and i'll try it

---

### Post by arsham on 2007-11-12
> **jaakan said:**
> server kernel 2.6.22 + apm=off acpi=off noapic seem to have helped my system

fingers crossed,

Yes , I did try it , but freezing in the same way , after 10 mins
I've read somewhere ( I can't remember where , because I've been searching hard ) that xserver design has been changed in some ways

Anyone tried feisty graphic card or X drivers in gutsy?

---

### Post by yug23 on 2007-11-12
I have the same problem, the system will just hard lock- I've got an Athlon XP1900 with 512mb RAM and an ATI Radeon 7500- this system NEVER once crashed with Feisty.

It usually does it when Firefox is open, but then I've normally got that open so I decided to try Opera, but it locked up with that as well. Then I tried turning off compiz and that made the crashes less frequent, but not go away. Then I switched to the vesa drivers and it seems a little better, but it will crash 5-6 times a day which is not on. It even does it when I have no web browser open.

I am usually running uTorrent via Wine so possibly that has something to do with it but as I said, that was never a problem with Feisty. I would reinstall the system but I notice on this thread that it usually isn't worth the bother- I don't really want to downgrade to Feisty as I'm sure it's a small bug which is having big consequences. I haven't got the Linux knowledge to diagnose it though... any ideas appreciated.

---

### Post by FerBatista on 2007-11-12
Has anyone of you tried running ubuntu in safe graphics mode? I also have some lockups/crashes, not as frequent as what I've read in this post though, but it happens to me too.
I've been running ubuntu in safe graphics mode since a few days and haven't had a crash since. Don't know if it's coincidence or not but so far it's working flawlessly.

---

### Post by arsham on 2007-11-12
In all the hard locks , exactly right the time that my computer locks up , the gaim incoming message tone is heard
But there is no evidence that there was an incoming message

And now for almost 5 hours straight , I am playing with compiz with no crashs
It used to be at least 10 mins

I shall say the gaim is not running now , and a bunch of java and python programs are hitting the cpu to test if they cause the problem

---

### Post by r0bb3d on 2007-11-12
Hey people,

Ive read this thread almost completely cause i had the same problems with the hard lockups happening at least once a day. I have fixed these problems for myself (so it seems) so i thought id take the time to post about it.

I'm not sure about the people posting about hardware problems (and cleaning their pc with vacuum) or ATI video cards, i think these problems are not related to what most most people are experiencing, which has to do with nvidia drivers imho.

I had the hard lockups on my dell inspiron 5150 (oldass) laptop, with nvdia GeForce FX Go5200 card, IDE drive and a fresh kubuntu 7.10 install x86. Never had probs when i used 7.04, but i did a fresh 7.10 install and i got in trouble. I used the restricted nvidia drivers ofc, which i suspected from the beginning of this problem.

I did something similar to something i saw some1 else post in the forum. I uninstalled nvidia-glx and the restricted kernel modules with apt-get and did apt-get clean to be sure after. Then i reinstalled the nvidia-glx-new and restricted modules, which also came with a leet new kernel image 2.6.22-14-386 ( was using 2.6.22-14-generic ) b4, im no pro at kernels, so not sure if that helped in anyway. After that the problem was solved, been using kubu 7.10 for 5 days now, and no lockups yet.

To be complete: my kernel was also spitting out errors about my broadcom wireless driver b4. Since im not using it atm, i decided to blacklist it by adding "blacklist bcm43xx" in /etc/modprobe.d/blacklist. Don't think its related, but thought id mention cause these are the only 2 changes ive made to my system.

Hope this helps.

---

### Post by quasimodo69 on 2007-11-12
My CPU temp fine-113 degrees-I am a clean freak with a clear sided case :-).Was running fresh install of 7.10 that ran great for 3 days loaded with all I wanted...then it started crashing every 5 - 15 minutes for no reason and without any other changes.My systems specs listed in my other posts.
  To me,after reading all these posts,the most reacurring theme-with exceptions-is nVidia cards,Firefox and the AM 64 chip.I hope we can find a solution soon..I already have an AMD 64 x2 chip waiting for a build to use this 7.10 which is so sweet!I wish I could help more,but being a newbie,a lot of this tech talk is beyond me.
DOWN WITH MICRO$OFT!!

---

### Post by orthopod on 2007-11-12
IPv6 enabled? Freezes happen when using Firefox?
I had the same problem, and solved it after I disabled IPv6.

1) In the address box, type about:config and press enter
2) In the box labeled "filter", enter "network.dns.disableIPv6"
3) Click on this setting, and change the value to "true."

---

### Post by Herm87 on 2007-11-12
Unfortunately, disabling IPv6 won't help the majority of people here. It's still a matter with the kernel.

---

### Post by andy19 on 2007-11-12
> **Tteddo said:**
> Andy19, does it still work after you reboot? I did this, and it worked until I rebooted, then I got an error about couldn't configure video card and had to redo the instructions again to get it to come up.

Well, I finally restarted my system just now, and everything still works fine.
I'm not sure what would be causing yours to have errors.  Are you sure you completely uninstalled the 'new' drivers?

---

### Post by alex2035 on 2007-11-12
It isnt about IPV6, half of us here have got rid of it, nor Nvidia, some lots are on ATI with the same problems (I myself, ATI X1250 and Im on VESA generic drivers with no 3d effects at all), not SATA (some are on IDE, me as well).
What I dont quite understand is that I dont see the more experienced and knowledgable people arriving too much at the forum as if they didnt experience this behaviours, it seems populated by newbies and the more or less technical (this said with respect, I  have been on Ubuntu since 5.04 but I consider myself far from an experienced Linux user). I could be wrong, just thinking. Perhaps they have kept wisely on 7.04...

---

### Post by snakesqzns on 2007-11-12
I'm tried most of the suggestions in this thread and the only thing that seems to have helped was disabling Compiz effects completely.

See this bug: [#156289]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/156289")

---

### Post by KrisWillis on 2007-11-13
Thought I might as well throw mine in too, though I'm running the 32-bit Ubuntu on a 64-bit chip. I'm getting the ramdom lockups too, more frequent with FireFox running (generally two instances) Though with Opera, I get temporary freezes for a minute or so then it comes back to life.

System specs:
AMD 64 X2 4000+
2GB RAM
4 x 80GB PATA disks
GeForce FX 5200 & GeForce FX 7300 serving three monitors

Ubuntu 7.10 32-bit
2.6.22-14-generic
Nvidia driver

---

### Post by jim_meech on 2007-11-13
Thanks for your info r0bb3d, your suggestion worked for me. My system is much more stable now.
Changing to the kernel image 2.6.22-14-386  instead of the generic one seemed to be the clincher for me. I was already running nvidia-glx-new and was still experiencing crashes.
Before making this change I could always totaly freeze my set up bt running google earth & firefox at the same time. Zooming in and out of the google earth image would invariably lock the PC in under 1 minute. I could not cause this behavior after changing the kernel.
I had previously tried the RT kernel, but this crashed more readily than the generic one.
There are still problems with the system,  Fire fox, firestarter & google earth spontaneously die if left running for an hour or so, but PC does not freeze. This is a great improvement.

My system is:

Ubuntu 7.10 32 bit

AMD athlon 4200 x 2 on ASUS mother board.

1G RAM

Nvidia 7300 graphics card

Triple booted with Debian stable & win XP

Best Regards
Jim





> **r0bb3d said:**
> Hey people,

Ive read this thread almost completely cause i had the same problems with the hard lockups happening at least once a day. I have fixed these problems for myself (so it seems) so i thought id take the time to post about it.

I'm not sure about the people posting about hardware problems (and cleaning their pc with vacuum) or ATI video cards, i think these problems are not related to what most most people are experiencing, which has to do with nvidia drivers imho.

I had the hard lockups on my dell inspiron 5150 (oldass) laptop, with nvdia GeForce FX Go5200 card, IDE drive and a fresh kubuntu 7.10 install x86. Never had probs when i used 7.04, but i did a fresh 7.10 install and i got in trouble. I used the restricted nvidia drivers ofc, which i suspected from the beginning of this problem.

I did something similar to something i saw some1 else post in the forum. I uninstalled nvidia-glx and the restricted kernel modules with apt-get and did apt-get clean to be sure after. Then i reinstalled the nvidia-glx-new and restricted modules, which also came with a leet new kernel image 2.6.22-14-386 ( was using 2.6.22-14-generic ) b4, im no pro at kernels, so not sure if that helped in anyway. After that the problem was solved, been using kubu 7.10 for 5 days now, and no lockups yet.

To be complete: my kernel was also spitting out errors about my broadcom wireless driver b4. Since im not using it atm, i decided to blacklist it by adding "blacklist bcm43xx" in /etc/modprobe.d/blacklist. Don't think its related, but thought id mention cause these are the only 2 changes ive made to my system.

Hope this helps.

---

### Post by KrisWillis on 2007-11-13
I've logged into my machine over SSH from another machine on my desk and am running *top*. When ever my machine freezes *top* is reporting that Xorg is using 100% of my CPU.

I don't really want to try and switch to the 386 kernel as I then loose one of my two cores...

---

### Post by komsas on 2007-11-13
> **jim_meech said:**
> Thanks for your info r0bb3d, your suggestion worked for me. My system is much more stable now.
Changing to the kernel image 2.6.22-14-386  instead of the generic one seemed to be the clincher for me. I was already running nvidia-glx-new and was still experiencing crashes.
Before making this change I could always totaly freeze my set up bt running google earth & firefox at the same time. Zooming in and out of the google earth image would invariably lock the PC in under 1 minute. I could not cause this behavior after changing the kernel.
I had previously tried the RT kernel, but this crashed more readily than the generic one.
There are still problems with the system,  Fire fox, firestarter & google earth spontaneously die if left running for an hour or so, but PC does not freeze. This is a great improvement.

My system is:

Ubuntu 7.10 32 bit

AMD athlon 4200 x 2 on ASUS mother board.

1G RAM

Nvidia 7300 graphics card

Triple booted with Debian stable & win XP

Best Regards
Jim

I changed kernel 386 instead of the generic and two days and don`t have any freeze. But now I have problem with my sound. ```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.
``` ;/

---

### Post by dziemecki on 2007-11-13
Just thought I'd add another one to the mix.  I'm running a new-ish install of Gutsy.  My symptom is that, at unpredictable intervals, the screen freezes and the keyboard and mouse no longer move.  I can't even turn off Num Lock.  Although I'm not particularly patient, I don't believe it ever un-freezes.  I say that because I've left it running overnight and found the screen blank (monitor went to sleep) and the PC unresponsive to keyboard/mouse.

I've had it run hours then freeze, I've had it freeze minutes after boot-up.  I've had it freeze while launching a browser page, or expanding a menu.  I've had it freeze while I was away from the keyboard.  I've tried using the Envy NVidia script.  I've uninstalled all recent additions.

My Specs:
Dimension E521
DUAL IN-LINE 1G, 533M, 128X64, 8, 240, 2RX8
AMD Athlon 64 x2 Dual Core 3800+

---

### Post by Tteddo on 2007-11-13
> **dziemecki said:**
> Just thought I'd add another one to the mix.  I'm running a new-ish install of Gutsy.  My symptom is that, at unpredictable intervals, the screen freezes and the keyboard and mouse no longer move.  I can't even turn off Num Lock.  Although I'm not particularly patient, I don't believe it ever un-freezes.  I say that because I've left it running overnight and found the screen blank (monitor went to sleep) and the PC unresponsive to keyboard/mouse.

I've had it run hours then freeze, I've had it freeze minutes after boot-up.  I've had it freeze while launching a browser page, or expanding a menu.  I've had it freeze while I was away from the keyboard.  I've tried using the Envy NVidia script.  I've uninstalled all recent additions.

My Specs:
Dimension E521
DUAL IN-LINE 1G, 533M, 128X64, 8, 240, 2RX8
AMD Athlon 64 x2 Dual Core 3800+

What video card exactly are you running?

---

### Post by ArchangelUriel on 2007-11-13
Well, I must admit that even with ubuntu 7.04, after the update of the kernel to 2.6.22-14-generic I had the same problems with the X... So it seems that the root of the problem may be the kernel as I had said earlier... As I am not a linux expert and I do not have the luxury to experiment with the kernels right now (lot of projects are runing at this time....) I propose to someone who knows how to do it, to use some kernels (like the -i386 some had tested, and maybe -12-generic or even 2.6.23) and tell us if this fixes the problem...

System Configuration
==================
ACER Aspire 9303

Ubuntu 7.10-amd64 (with Windows XP Prof. for DUAL BOOT)
Kernel 2.6.22-14-generic
AMD Turion64 x2 TL-52 (1.6GB)
GeForce Go 7300 driver ver. :100.14.19 (glx-new installed and freezes, "nv" used right now) 
2GB RAM DDR2
Xorg Version 1.3 ($Xorg -version to find out) (this seems to be something between 7.2 and 7.3) 
SATA 120GB HDD
Broadcom 4318 Wireless card

P.S. Plz when you give your system conf, write down your ubuntu ver, kernel, gpu and Xorg... These seems to be most important things...

---

### Post by arsham on 2007-11-14
I used 2.6.23.1 kernel , still freezing

---

### Post by wppaas on 2007-11-14
> **komsas said:**
> I changed kernel 386 instead of the generic and two days and don`t have any freeze./

I've switched to the 386 kernel too and it still freezes

---

### Post by regander on 2007-11-14
Hi!

I have had the same problem. It was so frustrating not to be able to use glx-new driver cause the nv-driver is so slow in 2d rendering. But i found a solution after days of searching. Aparantely its i bug in the nvidia proprietary drivers starting with the 100.14.09. The nvidia-driver used with a dualcore processor causes these random freezes. 

I installed the old 96.43.01 driver using envy and know it works fine. Though desktop-effects wont recognize the 3d acceleration and if you try to enable desktop effects it starts to install the new nvidia driver from the repository. 

Hope this could be to some help.  

/Alex

---

### Post by KrisWillis on 2007-11-14
I'm finding FireFox to be an almost definite trigger for me - I can run Opera all day and all night and I might get a temporary 5-second freeze here and there, but within half an hour of running FireFox my machine freezes to the point at which I have to hit the reset button...

I might try the suggestion of removing and reinstalling older drivers at the end of the day, then I'll have plently of time to fix it if it goes a bit Pete Tong - This is my main dev machine, can't afford to have it not running...

---

### Post by Anomali on 2007-11-14
[B]BRIEF SPEC:
nVidia card and Athlon single core CPU (longer spec at end of post)
Ubuntu 7.10 "Gutsy" with Gnome.[/B]

SYSTEM FREEZING when:
3D games running
browsing graphical websites (I know nowadays there are not many which are not)
3D screen saver running

**ACTIONS LEADING TO SOLUTION:**

[1] Install Automatix2:
[http://www.getautomatix.com/wiki/index.php?title=Installation#Post_Installation](http://www.getautomatix.com/wiki/index.php?title=Installation#Post_Installation)
I don't think anything here actually helped but it did have some nice features and packages.  System still freezing.

[2] Install and use Envy:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
This was used to remove and update nVidia drivers and xorg

SYSTEM HAS NOT FROZEN SINCE

(On a side note:  This current set-up of Gutsy is most definitely slower than Feisty)

[B]Thanks for all your posts, things wouldn't be stable without your contributions.  I hope this post helps at least one other person!

Ali-][/B]

SYSTEM SPEC:

cpu: AMD Athlon(tm)
cpu_ghz: 1.74
memory: 2027
videocard_manufacturer: NVIDIA Corporation
videocard_type: GeForce 7600 GS/AGP/SSE/3DNOW!
videocard_ram: 256
agp_aperture_size: 44
videocard_driver_version: 2.1.0 NVIDIA 96.39
soundcard: C-Media PCI CMI8738-MC6 (model 55) at 0xd400, irq 2
soundcard_driver: ALSA Version 1.0.14
machine_bitness: 32
kernel: 2.6.22-14-generic
x_version: Xorg Version 1.3.0
distro: Debian lenny/sid

---

### Post by Herm87 on 2007-11-14
Could you all please specify "freeze"? Some people report their X-server freeses (switching to console possible) or their graphic freezes (remote ssh still working) while my kernel panics and therefore the whole system freezes. I wonder if I am the only one with this particular problem.

---

### Post by Anomali on 2007-11-14
In my case the **"freeze" is now fixed** (solution 2 posts up) but **seemed to be whole system** as <Ctrl>+<Alt>+<Backspace> would not work.  I have no other machine on the network to check remotely what was happening.

---

### Post by ArchangelUriel on 2007-11-14
> **Anomali said:**
> In my case the **"freeze" is now fixed** (solution 2 posts up) but **seemed to be whole system** as <Ctrl>+<Alt>+<Backspace> would not work.  I have no other machine on the network to check remotely what was happening.

The same thing here, although it happed once or twice to be able to <Ctrl>+<Alt>+<F1> to console... Even though I was frustrated enough not to type <top> to see what happens in the cpu. Sorry.:(

---

### Post by dezoete on 2007-11-14
With me everything works fine, no problems ......
:confused::confused::confused:Till I try to put the computer to sleep. (Hibernate)
The screen goes black and no response, but computer keeps running... ,
No big deal, since I just shut down instead...
BTW, AMD64, runningWindowsXP &  ubuntu 7.10 in 32bit mode.  I tried the AMD version, 2G, but had problems with wine and other 32bit programs

---

### Post by ArchangelUriel on 2007-11-14
> **dezoete said:**
> With me everything works fine, no problems ......
:confused::confused::confused:Till I try to put the computer to sleep. (Hibernate)
The screen goes black and no response, but computer keeps running... ,
No big deal, since I just shut down instead...
BTW, AMD64, runningWindowsXP &  ubuntu 7.10 in 32bit mode.  I tried the AMD version, 2G, but had problems with wine and other 32bit programs

This has something to do with the acpi (the power manager... try to search the forum about it. There might be a solution)

---

### Post by komsas on 2007-11-14
> **wppaas said:**
> I've switched to the 386 kernel too and it still freezes

Did you reinstall nvidia-glx-new ?

---

### Post by hlyng on 2007-11-14
> **dziemecki said:**
> Just thought I'd add another one to the mix.  I'm running a new-ish install of Gutsy.  My symptom is that, at unpredictable intervals, the screen freezes and the keyboard and mouse no longer move.  I can't even turn off Num Lock.  Although I'm not particularly patient, I don't believe it ever un-freezes.  I say that because I've left it running overnight and found the screen blank (monitor went to sleep) and the PC unresponsive to keyboard/mouse.

I've had it run hours then freeze, I've had it freeze minutes after boot-up.  I've had it freeze while launching a browser page, or expanding a menu.  I've had it freeze while I was away from the keyboard.  

All the same here except im on a ATI mobility 9700 graphic card and 32 bit cpu.
ATI driver or the free one, and compiz on/off  NO  difference...

---

### Post by grinias on 2007-11-14
I think that "ArchangelUriel" is right. This has to do with acpi. All my problems are gone once I boot with acpi=off. BUT in that case,  although I have no lockups the sound and ethernet connection do not work at all. Madness...

EDIT: Finally looking in
[another thread ]("http://ubuntuforums.org/showthread.php?t=412125&highlight=acer+gutsy+freeze") (post by "arsham", page 82) in ubuntu forums with 
the same subject I figured out the solution for my

*Acer TM 4101 1.6 Celeron 
*ATI X600, running gutsy provided restricted driver fglrx
*kubuntu gutsy updated from Feisty, once gutsy release candidate had been available at the middle of October

system. The solution was to install 
xserver-xorg-video-all
(xserver-xorg-input-all was already installed).


No freeze for the last 2 hours!!! So the problem was with Xorg I think. I recall that during the update from feisty to gutsy, xserver-xorg-video-all was installed as a new metapackage, bringing also
the packages that depend on it. I decided to remove some of these drivers (including the ati one), since I considered they were useless. Obviously metapackage xserver-xorg-video-all was removed too. This worked 
without problems for about 2 weeks. In October 31th, an update of packages which I do not remember what exactly were (but now I m sure they were Xorg related), brought the random lockups to my
system.

Hope it helps someone
Elias

EDIT of EDIT: The solution was not permanent for me!!! Good luck to all...

---

### Post by dziemecki on 2007-11-14
> **Tteddo said:**
> What video card exactly are you running?
GeForce 7300 LE

Originall post for anyone following the thread:
[http://ubuntuforums.org/showpost.php?p=3767387&postcount=180](http://ubuntuforums.org/showpost.php?p=3767387&postcount=180)

---

### Post by Bokonon on 2007-11-14
Since this is kind of random, it seems hard to lock down.  I have been hoping to find something that causes the problem consistently.  (firefox/nvidia/sata seem to be partially problems, but none of them cause it 100% of the time)

For me, I have been able to re-create the lock-up by loading a video into xine (not gxine) and then right clicking:

Settings -> Setup -> "Video" tab

From there, select video driver and scroll through the options.  On my troublesome machine, it always locks up, sometimes hard, sometimes I can get to a terminal with CTRL-ALT-F#

I have uninstalled everything to do with xine in hopes that might help, but I still get lockups.  It seems to be a bit less frequent tho.

On my working systems, I can do the above with no risk of lockups.

---

### Post by snakesqzns on 2007-11-14
I'm getting frequent freezes as well. 

Running 64 bit gutsy on an Athlon 64 X2 and ASUS M2N-E board.

I thought it might be [#145112]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/145112") or [#156289]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/156289") or [#58019]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/58019") or maybe [#98668]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-i810/+bug/98668")

I've tried every suggestion around and the freezes still occur -- sometimes twice an hour, sometimes after six hours (of use).

Some suggest this is a recognized issue with the nvidia drivers after version *.14.09 and the geforce 7000 series.  After trying the older driver versions, and trying two different video cards (Geforce 7200 SE and a Quadro FX 1400) I'm not so sure.

The most common config similarity I'm noticing on this issue seems to be the AMD Athlon 64 X2 processors.

:-|

---

### Post by Bokonon on 2007-11-15
I am thinking about downgrading(???) my 7300 to an old 6800.

My 7300 is quiet (fanless), but a little extra noise is certainly better than the current situation.

---

### Post by arsham on 2007-11-15
See this : [Bug 138094]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/138094")
But I believe there is still unknown problems after upgrading from feisty to gutsy

---

### Post by jaakan on 2007-11-15
My system seems to freeze whole less with just apm=off added to the kernel line in grub.
I removed noapic and acpi=off.


this bug I found sounds just like the lockup I'm having only they had a SATA HD vs my EIDE HD
[http://bugzilla.kernel.org/show_bug.cgi?id=8650](http://bugzilla.kernel.org/show_bug.cgi?id=8650)
and here but a RAID 
[http://bugzilla.kernel.org/show_bug.cgi?id=9017](http://bugzilla.kernel.org/show_bug.cgi?id=9017)
and
[http://bugzilla.kernel.org/show_bug.cgi?id=9182](http://bugzilla.kernel.org/show_bug.cgi?id=9182)



fyi: 

i/o + storage bugs
[http://bugzilla.kernel.org/buglist.cgi?bug_status=NEW&bug_status=REOPENED&bug_status=ASSIGNED&bug_status=NEEDINFO&content=&field-1-0-0=bug_status&field-1-1-0=product&field-1-2-0=content&field-1-3-0=short_desc&product=IO%2FStorage&query_format=specific&remaction=&type-1-0-0=anyexact&type-1-1-0=anyexact&type-1-2-0=matches&type-1-3-0=allwords&value-1-0-0=NEW%2CREOPENED%2CASSIGNED%2CNEEDINFO&value-1-1-0=IO%2FStorage&value-1-2-0=&value-1-3-0=&order=bugs.kernel_version%2Cbugs.kernel_version&query_based_on=](http://bugzilla.kernel.org/buglist.cgi?bug_status=NEW&bug_status=REOPENED&bug_status=ASSIGNED&bug_status=NEEDINFO&content=&field-1-0-0=bug_status&field-1-1-0=product&field-1-2-0=content&field-1-3-0=short_desc&product=IO%2FStorage&query_format=specific&remaction=&type-1-0-0=anyexact&type-1-1-0=anyexact&type-1-2-0=matches&type-1-3-0=allwords&value-1-0-0=NEW%2CREOPENED%2CASSIGNED%2CNEEDINFO&value-1-1-0=IO%2FStorage&value-1-2-0=&value-1-3-0=&order=bugs.kernel_version%2Cbugs.kernel_version&query_based_on=)

ACPI bugs

[http://bugzilla.kernel.org/buglist.cgi?bug_status=NEW&bug_status=REOPENED&bug_status=ASSIGNED&bug_status=NEEDINFO&content=&field-1-0-0=bug_status&field-1-1-0=product&field-1-2-0=content&field-1-3-0=short_desc&product=ACPI&query_format=specific&remaction=&type-1-0-0=anyexact&type-1-1-0=anyexact&type-1-2-0=matches&type-1-3-0=allwords&value-1-0-0=NEW%2CREOPENED%2CASSIGNED%2CNEEDINFO&value-1-1-0=ACPI&value-1-2-0=&value-1-3-0=&order=bugs.kernel_version&query_based_on=](http://bugzilla.kernel.org/buglist.cgi?bug_status=NEW&bug_status=REOPENED&bug_status=ASSIGNED&bug_status=NEEDINFO&content=&field-1-0-0=bug_status&field-1-1-0=product&field-1-2-0=content&field-1-3-0=short_desc&product=ACPI&query_format=specific&remaction=&type-1-0-0=anyexact&type-1-1-0=anyexact&type-1-2-0=matches&type-1-3-0=allwords&value-1-0-0=NEW%2CREOPENED%2CASSIGNED%2CNEEDINFO&value-1-1-0=ACPI&value-1-2-0=&value-1-3-0=&order=bugs.kernel_version&query_based_on=)

powermanagent bugs

[http://bugzilla.kernel.org/buglist.cgi?bug_status=NEW&bug_status=REOPENED&bug_status=ASSIGNED&bug_status=NEEDINFO&content=&field-1-0-0=bug_status&field-1-1-0=product&field-1-2-0=content&field-1-3-0=short_desc&product=Power%20Management&query_format=specific&remaction=&type-1-0-0=anyexact&type-1-1-0=anyexact&type-1-2-0=matches&type-1-3-0=allwords&value-1-0-0=NEW%2CREOPENED%2CASSIGNED%2CNEEDINFO&value-1-1-0=Power%20Management&value-1-2-0=&value-1-3-0=&order=bugs.kernel_version&query_based_on=](http://bugzilla.kernel.org/buglist.cgi?bug_status=NEW&bug_status=REOPENED&bug_status=ASSIGNED&bug_status=NEEDINFO&content=&field-1-0-0=bug_status&field-1-1-0=product&field-1-2-0=content&field-1-3-0=short_desc&product=Power%20Management&query_format=specific&remaction=&type-1-0-0=anyexact&type-1-1-0=anyexact&type-1-2-0=matches&type-1-3-0=allwords&value-1-0-0=NEW%2CREOPENED%2CASSIGNED%2CNEEDINFO&value-1-1-0=Power%20Management&value-1-2-0=&value-1-3-0=&order=bugs.kernel_version&query_based_on=)

---

### Post by dbcalo on 2007-11-15
i was having random lockups. not sure if this applies to you but it was because my hdd's were overheating.

---

### Post by Herm87 on 2007-11-15
Many people here use multibooting systems. Therefore hardware-issues are often out of the question. I'd still like to know if anyones kernel panics - like mine does.

---

### Post by mac25 on 2007-11-15
Done all updates, but still firefox freezes all the time, dont have enough skill to do to much.
Result, gone back to fiesty on both our comps, Will try again maybe later, or wait for Hardy Heron.

Hardware:
- ASUS M2N-MX (nForce 430)
- AMD Athlon64 4800+ X2
- NVidia 7600GT 256mb
- SATA2 HDD for files and data, ntfs/ext3
- 2gb pc800 ram

---

### Post by Pinoy915 on 2007-11-15
For those who rolled back their drivers to 100.14.09 and having problems with x when rebooting, I'm trying out the driver that Envy installs. It says 100.14.23 even though I don't see it available at Nvidia's site but hopefully this fixes the problem with 7xxx based cards. I used Envy on Gutsy AMD64.

---

### Post by SJI on 2007-11-15
No matter which 100.xx.xx Nvidia I try with my 7300 card I get hard locks.
Drop back to 96.43.01 and it's as stable as Feisty was.

Stephen

---

### Post by ArchangelUriel on 2007-11-16
> **SJI said:**
> No matter which 100.xx.xx Nvidia I try with my 7300 card I get hard locks.
Drop back to 96.43.01 and it's as stable as Feisty was.

Stephen

I drop to nvidia 96.43.01 through envy and I am 2,5 hours without crash...\\:D/ Those were stresy hours (azureus, vmware, opera, gftp, firefox). I'll test the system for a day or two with lot of reboots and post my findings.

[-o<cross fingers[-o<

System Configuration
==================
ACER Aspire 9303

Ubuntu 7.10-amd64 (with Windows XP Prof. for DUAL BOOT)
Kernel 2.6.22-14-generic
AMD Turion64 x2 TL-52 (1.6GB)
GeForce Go 7300 driver ver. : 96.43.01
Compiz Enabled
2GB RAM DDR2
Xorg Version 1.3 ($Xorg -version to find out) (this seems to be something between 7.2 and 7.3) 
SATA 120GB HDD
Broadcom 4318 Wireless card

---

### Post by dziemecki on 2007-11-16
Is anyone aware of any official recognition of this issue?  Is it logged as a bug anywhere?  This one problem is enough for me to have to put Ubuntu on the shelf for another year and try again with the next version.  I can't work when my PC freezes unpredictably three times within a 3 hour period.

---

### Post by jaakan on 2007-11-16
i was about to try to compile 2.6.24-rc2 for amd64 with Kernelcheck and locked up every time I tried even with vesa xorg drivers. ( it did start to compile )

i also added pci=routeirq only to the kernel ( which is listed in the logs to try ) + nv-glx ( not the nv-glx-new ) I was using nv-glx-new before. turned USB emulation fully off in the bios, with it on usb Harddrives have very low transfer rates. Well my system was up through the night an usable when i got up. my CPU, HD, Graphic card run cool.

I did see apparmor crash in the logs this morning but it looked like that was around booting time.
1am EST.

a command line version of Kernelcheck would be nice.or even a boot disc version for cases like this where we'd like to try a newer kernel but our system has a good case of locking up before the new kernel will even finsh compiling.

i hope my system can stay up all weekend

---

### Post by Bokonon on 2007-11-16
My troubleshooting and resolution:

Stop compiz:  Lockups still present
Shift to vesa/nv driver:  Lockups appeared to be gone, but I couldn't play video or enjoy a decent screen resolution.

With that, I figured it was something with nVidia, the kernel or my card.  

Removed my 7300GS and installed an old 6800GT. 
Reinstalled restricted drivers.

No lockups, but there is definite system slowdown when I go into xine as per my post above.  I can now quit xine to get out of it instead of an automatic lockup.

I even restarted compiz and now everything is working just fine (except xine config is slightly bumpy).  For me, it appears to have been some problem with my card and the nVidia drivers.  I will report back if the system crashes again, but I think I have it licked.

I am certain this is not the problem for everyone here, but if you have a 7300 series card and the default drivers,  you might try changing drivers or your video card.

---

### Post by glong on 2007-11-16
Hello,

First post, I have been reading the forums furiously trying to solve my problems.

Gutsy 7.10, 32 bit generic or rt kernel (2.6.22-14)
Dell AMD, 2 CPU, dual core
1 GB RAM
7300 Nvidia

Freezes vary , hard - needing complete shutdown, soft - can do a Alt-Sysreq-REISUB reboot - very unpredictable.

I have dropped back to 100.14.09 - Will try that to see if it fixes.
If not I will try 96.43.01

I did temporarily try 96.43.01 but could not get Compiz to work - is it  possible to enable compiz?  It seems from some others that it is possible - looking specifically at the system configuration of ArchangelUriel afew posts up.  When I install 96.43.01 and try to enable effects it returns a message that effects cannot be enabled (sorry I don't have the exact wording with me at the moment).

Or do I just need to be resolved that I will trade away graphics capabilities for stability, until there is some real fix in the kernel or drivers?

Greg

---

### Post by ArchangelUriel on 2007-11-16
> **glong said:**
> I did temporarily try 96.43.01 but could not get Compiz to work - is it  possible to enable compiz?  It seems from some others that it is possible - looking specifically at the system configuration of ArchangelUriel afew posts up.  When I install 96.43.01 and try to enable effects it returns a message that effects cannot be enabled (sorry I don't have the exact wording with me at the moment).

Some time ago I had tried again to put 96.43.01 again but for some unknown reason the glx was not installed. So even I had the nvidia drivers, compiz and 3D acceleration were out of question. Go to Applications -> System Tools -> Nvidia Settings and check the glx tabs. If it says that glx is disabled, try to reome and reinstall nvidia drivers (try envy for both uninstall and reinstall).

12 hours, numerus reboots, NO FREEZE yet. Let's run some stress tests during the night...

---

### Post by dziemecki on 2007-11-16
> **SJI said:**
> No matter which 100.xx.xx Nvidia I try with my 7300 card I get hard locks.
Drop back to 96.43.01 and it's as stable as Feisty was.
Stephen
I'm ready to try this.  What's the best way to get back to 96.43.01?  Envy will only install the latest, right?  Also, what do I lose going back?  How old is that driver?

BTW - someone said their issue was related to upgrading from Feisty to Gutsy.  Mine was a fresh install, so I wouldn't blame the install so much as the new software.

---

### Post by glong on 2007-11-16
The newest version of Envy will install the 100.14.09 nvidia. It is presented as an option under the manual install choice.  

Perhaps that is significant.  Maybe manual install is implying that their are some other things I need to do to enable GLX/Compiz?

Greg

---

### Post by Tteddo on 2007-11-17
Giving this a shot:
[https://help.ubuntu.com/community/NvidiaManual]("https://help.ubuntu.com/community/NvidiaManual")
with the 100.14.09 driver from the nVidia archive. It's from June.
After following the instructions it came right back up. I still have Compiz and such uninstalled.
I'll report back if it freezes.

AMD Dual Core 5600+
nVidia 7300 GS
2 SATA HD
2 Gig Ram

---

### Post by glong on 2007-11-17
Installed the Nvidia 100.14.09 Driver yesterday.

No system instability yet, even with Compiz and the Cube.  Several hours of uptime on two identical dual core AMD Dells with Nvidia 7300 cards.

Also just saw this on another thread. Thread name:  (nvidia driver causes lock-ups, black flashes, hangs):

----

It seems that the beta driver of nvidia released yesterday fixes the problem. I didn't try it yet, but here is the changelog :

"Fixed stability problems with some GeForce 6200/7200/7300 GPUs multi-core/SMP systems."

You can get the version 169.04 here : [http://www.nvidia.com/object/linux_display_ia32_169.04.html](http://www.nvidia.com/object/linux_display_ia32_169.04.html)

I am not switching just yet, because 100.14.09 seems to give me everything I need.  But some others may be interested in this.  The new driver was released Nov 16, 2007 - so it is brand new.

Greg

---

### Post by tim1 on 2007-11-17
I reported a bug 2 weeks ago, so far no reaction:

[https://bugs.launchpad.net/ubuntu/+bug/159398](https://bugs.launchpad.net/ubuntu/+bug/159398)

Maybe some you can add comments and/or subscribe to the bug to show Ubuntu developers how many of us are affected by it.

---

### Post by dziemecki on 2007-11-17
Ok, to answer some of my own questions (and spread the wealth) Envy easily handles downgrading the NVidia driver.  Just select the "manual" option, then select the driver version.  Even though it says "manual", it's auto from there.  So I downgraded from 100.14.09 to 96.43.01 and, just so everyone knows, it didn't make a lick of difference.

Have we confirmed that most of the people experiencing the "full freeze" (no mouse, no keyboard, monitor freeze) are running an NVidia GeForce 7x series video card?  I'm wondering if the simple solution to just to upgrade the card.  This would be as good an excuse to do so as any.  :-)

I've added my tale of woe to Tim's bug thread and I heartily suggest the rest of you do as well.
[https://bugs.launchpad.net/ubuntu/+bug/159398](https://bugs.launchpad.net/ubuntu/+bug/159398)

---

### Post by lanzen on 2007-11-17
Tim 1, check this bug:

Bug #145112 in linux-restricted-modules-2.6.22 (Ubuntu)  ;)

---

### Post by Tteddo on 2007-11-17
> **glong said:**
> Installed the Nvidia 100.14.09 Driver yesterday.

No system instability yet, even with Compiz and the Cube.  Several hours of uptime on two indentical dual core AMD Dells with Nvidia 7300 cards.

Also just saw this on another thread. Thread name:  (nvidia driver causes lock-ups, black flashes, hangs):

----

It seems that the beta driver of nvidia released yesterday fixes the problem. I didn't try it yet, but here is the changelog :

"Fixed stability problems with some GeForce 6200/7200/7300 GPUs multi-core/SMP systems."

You can get the version 169.04 here :[http://www.nvidia.com/object/linux_display_ia32_169.04.html](http://www.nvidia.com/object/linux_display_ia32_169.04.html)
------

I am not switching just yet, because 100.14.09 seems to give me everything I need.  But some others may be interested in this.  The new driver was released Nov 16, 2007 - so it is brand new.

Greg

Trying the new driver 169.04 right now since I have the time. Leaving the eye candy off for now.

---

### Post by chorca on 2007-11-17
After disabling Compiz/desktop effects it seems to be running without fail, it's been going fine for over a week. One of my friends mentioned AIGLX may be causing issues due to it's buggy status right now.

---

### Post by lanzen on 2007-11-18
After trying different ways out from this bug I did install the new beta x86_64-169.04.

It's too early to say how it's doing, but it's smooth for now. I'd also bet that 100.14.09 would do the trick as well as It was working fine before Gutsy became release and added 100.14.19.

My system:
Compaq Presario SR1959IT Desktop PC [http://tinyurl.com/36d8gn](http://tinyurl.com/36d8gn)

AMD Athlon 64 Dual Core 3800+
RAM 2 Gb
2 HD SATA (one added recently)
Graphic: G72 [GeForce 7300 LE]

---

### Post by ArchangelUriel on 2007-11-18
Well, 3 days without freezes with the 96.43.01 nvidia drivers... Later today I'll try the latest ones and post the results...

---

### Post by jaakan on 2007-11-18
I change a monitor event > video to "on" in my bios under power saving.

installed the 2.6.20 kernel from 7.04
deleted nvideo xconfig
reinstalled 2.6.22.14-10 kernel
resintalled nvidia-glx-new
reinstalled Mysql which never fully install correctly and crash on ever boot ( It's ok now )

not sure what else changed but my system has been up for over 10 hours
and no issues for over 24 hours

jaakan@AMD64:~$ uptime
 07:21:18 up 10:27,  2 users,  load average: 0.63, 0.64, 0.66
jaakan@AMD64:~$ 



title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=....... ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

My motherboard is a Chaintech MK8M800 w/  newest bios ( 1995 )

instead of a hard lock up, my system now slows down freezes, and in a few seconds it is ok,

---

### Post by ArchangelUriel on 2007-11-18
Installed beta Nvidia drivers (100.14.19) and go my first freeze in 20 secs... I'm going back to 96.43.01

---

### Post by dziemecki on 2007-11-18
Looks like I have a winner.  I followed up on the brand-new driver (169.04) from NVidia (thanks, glong) and I haven't had any new crashes.  Went all night without a freeze.  Not definitive yet, but that's the first time I made it all night.

If you missed the first link, here it is:

[http://www.nvidia.com/object/linux_display_ia32_169.04.html](http://www.nvidia.com/object/linux_display_ia32_169.04.html)

Warning, this one hasn't been all Envy-fied, so you'll need to drop back to console to install.

---

### Post by gombosg on 2007-11-18
I have seen the **crasiest crashes ever** on gutsy.
My laptop is : HP nx6325

Smaller problems: -no splash screen (editing usplash.conf only makes splash screen appear when i shut down ubuntu)
-bcm43xx works, but dies when waking up from standby.

These are small problems, everything could be great.
[SIZE="4"]BUT THE CRASH[/SIZE]

It's **crazy**. The system freezes... no ctrl-alt-backspace, but mouse cursor still moves...
And **it freezes step by step**.

Some time ago it froze only while using dpkg, while installing a program. Now sometimes it freezes while logging in, or starting a program, opening a window etc.

1) a program won't react at all.
2) other programs are still alive, for example firefox, but when I press an arrow key, it scrolls only one step, not more (alt-tab=instant lockup)
3) system monitor (CPU usage etc) graphs stop
4) Firefox etc stop reacting
5) mouse is still alive, icons highlight
6) all dies, mouse cursor alive, but system doesn't respond.

It's all crazy....
If I press ctrl-alt-f1, the screen is messed up, if not, I can type login-password, but I never get a console.

Any help? I think it's no way. Ati/fgrlx the same, SUSE works well.
Tried reinstalling. The freezes came back, first no freeze, after a few boots, I had dpkg freezes, now I can't use a system at all, if it doesn't freeze at login, it locks up after starting a program.

Edit: this happens on no other distro. (fedora/suse)
I looked through every file in /var/log, no special error messages.

---

### Post by snakesqzns on 2007-11-18
I think I may have resolved my freezing with both an nvidia geforce 7300 and a quadro 1400.

Theres a new nvidia driver beta avialable here: [http://www.nvnews.net/vbulletin/showthread.php?t=102509](http://www.nvnews.net/vbulletin/showthread.php?t=102509)

Also I'd noticed that my network card would die during Xorg lockups as well.  /proc/interrupts showed the NIC was sharing an interrupt with the video card.  Moving the NIC to another slot did the trick.  This might have have been why the video would freeze up sometimes when I'd click an url in firefox or receive an instant message.

Since then I've been stable, except for one instance of compiz.real went berserk after running the quake4 demo.  "killall -9 compiz.real" & "metacity --replace" brought things back.

Hope this helps someone.

---

### Post by lanzen on 2007-11-18
> **gombosg said:**
> I have seen the **crasiest crashes ever** on gutsy.
My laptop is : HP nx6325

It looks like you have an ATI card, don't you? So there must be something common to ATI and Nvidia that is causing these lock-ups. In this case I can't help but I remember seeing other people having problems with ATI and Gutsy. Do a thorough search and you might find a solution.

In my case, as many others, I could not do anything but powering off the system.

Things got slightly better  - I don't still see what it's really got to do with this - when I added  gutsy-proposed and gutsy-backports and allowed installing updates. I could then, sometimes, move the mouse and had longer activity periods between lockups.

To me, so far, 169.04 has done the trick: no freezes since this morning.  :)

---

### Post by snakesqzns on 2007-11-18
> **gombosg said:**
> 
It's **crazy**. The system freezes... no ctrl-alt-backspace, but mouse cursor still moves...
And **it freezes step by step**.

If you can try setting up ssh so you can connect from another machine during the crash to troubleshoot.

Serial console is another option.  I've got an Apple //c connected here with vt220 at 9600 baud.  Maybe ridiculous, but it works. :)

-a

---

### Post by Tteddo on 2007-11-18
I am at almost 24 hours with 169.04 and it's perfect so far. I never went this long with anything besides the generic nv.

---

### Post by ArchangelUriel on 2007-11-18
> **Tteddo said:**
> I am at almost 24 hours with 169.04 and it's perfect so far. I never went this long with anything besides the generic nv.
169.04 here for some hours, no freezes yet...

+1 for 169.04

---

### Post by lanzen on 2007-11-18
No freezes in more then 12 hours. 169.04

---

### Post by Tteddo on 2007-11-18
> **snakesqzns said:**
> 

Serial console is another option.  I've got an Apple //c connected here with vt220 at 9600 baud.  Maybe ridiculous, but it works. :)

-a

Ok, now you are just showing off! :)

---

### Post by Bokonon on 2007-11-18
Glad to see a lot of success stories popping up in this thread.  I would like to report back to confirm my troubles are gone.

For me, the shift from nVidia 7300 -> nVidia 6800 has appeared to do the trick.  3 days running and doing things I knew would cause lockups (xine -> settings -> video) and suspected problems (firefox, azureus, wesnoth).  No problems at all this weekend and no way I could have made it that long using the 7300.

I didn't try updating to new drivers which might be the best solution here, but going to nv/vesa drivers also seemed to fix the problem. I didn't test sufficiently before going to the 6800 to make an absolute statement on that alone.

Currently a bit noisier, hotter and messier inside my case, but that is fine.  :)

NOTE:  wesnoth doesn't appear to be a common problem here, but I had several lockups while playing before.  I suspect it was more of a fact that I was playing a lot of wesnoth rather than wesnoth being a problem.

---

### Post by lanzen on 2007-11-19
Another day passed and no lockups.  Compiz running fine.

Nvidia beta driver: 169.04

_______________________________
AMD Athlon 64 Dual Core 3800+
RAM 2 Gb
2 HD SATA
Graphic: G72 [GeForce 7300 LE]

---

### Post by pierre.s.rosen on 2007-11-19
I started having problems with my 7.10 install a few days ago.  When I launched Pigeon, it would crash if I had any offline messages waiting for me.  Today, every time I tried to launch Firefox caused a hard lock up of my desktop, and I couldn't use keystroke commands to get to a command line; however, my mouse still worked.  Very similar to gombosg's post.

Whats going on?  Is this an NVIDIA driver issue?  Is there a fix in the works?

---

### Post by s3rvac on 2007-11-19
I can also confirm that I have no freezes at all with the latest nVidia beta driver (169.04) - AMD Turion64 X2, nVidia Go 7300. I had system freezing issues with the original version that is currently in Gutsy (100.14.19), but updating the driver solved my problem.

---

### Post by Tteddo on 2007-11-19
I am thinking I might turn Compiz back on!!

---

### Post by gombosg on 2007-11-19
> **gombosg said:**
> I have seen the **crasiest crashes ever** on gutsy.
My laptop is : HP nx6325

Smaller problems: -no splash screen (editing usplash.conf only makes splash screen appear when i shut down ubuntu)
-bcm43xx works, but dies when waking up from standby.

These are small problems, everything could be great.
[SIZE="4"]BUT THE CRASH[/SIZE]

It's **crazy**. The system freezes... no ctrl-alt-backspace, but mouse cursor still moves...
And **it freezes step by step**.

Some time ago it froze only while using dpkg, while installing a program. Now sometimes it freezes while logging in, or starting a program, opening a window etc.

1) a program won't react at all.
2) other programs are still alive, for example firefox, but when I press an arrow key, it scrolls only one step, not more (alt-tab=instant lockup)
3) system monitor (CPU usage etc) graphs stop
4) Firefox etc stop reacting
5) mouse is still alive, icons highlight
6) all dies, mouse cursor alive, but system doesn't respond.

It's all crazy....
If I press ctrl-alt-f1, the screen is messed up, if not, I can type login-password, but I never get a console.

Any help? I think it's no way. Ati/fgrlx the same, SUSE works well.
Tried reinstalling. The freezes came back, first no freeze, after a few boots, I had dpkg freezes, now I can't use a system at all, if it doesn't freeze at login, it locks up after starting a program.

Edit: this happens on no other distro. (fedora/suse)
I looked through every file in /var/log, no special error messages.

Good news bad news.
I used may laptop for a long time ... with the power cable plugged in.
So the problem may be around power management?

Maybe. so I pulled it out. Restart. Use.
Use.
Use.
It worked... I thought the problem is with CPU frequency switching, but no. It did stepping very well. So I used the laptop for an hour, and just when I wanted to turn it off, it froze.

Boom.

SO, the problem is with using my notebook without power cable. My Linux knowledge is not sufficient, but:
-W-T-F?
-What is the problem? Maybe a kernel module loading at startup?
-What should I try?
-No, fglrx/ati drivers all freeze.
-Wireless? CPU? Anything?

It is crazy to see CPU monitor graphs stop, then, as I click with the touchpad, see them move step by step, then they stop forever only poweroff works.
It is crazy to see a Linux distribution being this unstable.
It is crazy that apart from these Ubuntu would be the best for my needs. :confused:

Edit: there is a BIOS update for my laptop, it says this updates the CPU microcode, I'll try it in the afternoon, it MAY help, but I don't think so.

---

### Post by jaakan on 2007-11-19
After getting my new laptop ( DELL Vostro 1000 ) and updating the BIOS. no freezing issues. I'm thinking the lockup bug is related to the BIOS and the kernel. in one of the logs I found "broken bios" listed my desktop ( newest BIOS is only 2005 )

kind of like this
[http://lkml.org/lkml/2003/7/11/306](http://lkml.org/lkml/2003/7/11/306)


My desktop has a Via based motherboard
[http://forums.viaarena.com/messageview.aspx?catid=32&threadid=77868](http://forums.viaarena.com/messageview.aspx?catid=32&threadid=77868)

and yep it start locking up again it's now my beta box for HH when a new kernel gets pushed out

---

### Post by pierre.s.rosen on 2007-11-19
Follow-up to my original post about freezes.  Turning off graphical effects (Compiz) solved the problem...I imagine that there is something wrong with the NVIDIA Driver or the stability of Compiz...I hope the Ubuntu team fixes this bug!:guitar:

---

### Post by ArchangelUriel on 2007-11-20
4 days now with the 169.04 drivers and no freeze... I run many stess test and everything runs smoothly... Compiz and many eye-candys enabled... I must say that I installed ubuntu updates every day and maybe there was some update there that might helped... 

So fully update your Ubuntu, try 169.04 nvidia drivers and post your results here...

NVidia 169.04 drivers links.
======================
i386: [http://www.nvidia.com/object/linux_display_ia32_169.04.html](http://www.nvidia.com/object/linux_display_ia32_169.04.html)
x64 : [http://www.nvidia.com/object/linux_display_amd64_169.04.html](http://www.nvidia.com/object/linux_display_amd64_169.04.html)

---

### Post by chorca on 2007-11-20
I'd like to ask everyone here who isn't getting kernel panics if there's someone else who can confirm the locks are only in X. The problem i've experienced only locks up Xorg, the rest of the system beneath it is responsive. A way to test this is to install OpenSSH and use another computer to SSH into the system while it's locked up, and see if you can access it.

I think that what's going on is akin to what was posted previously, that there's serveral different causes for these lockups that lead to the same end problem, and lumping them together in one thread without being able to determine the underlying issue leaves everyone confused. It seems we've been unable to rule out any certain hardware or anything about the lockups. With mine i've narrowed it down to Compiz and Xorg, only Xorg locks up when compiz is enabled.

Looking forward to see others with the same issue. Perhaps we can start another thread, as this clearly isn't limited to x86-64 either.

---

### Post by jrickard on 2007-11-20
The NVIDIA install requires you to completely exit X.  CTRL-ALT-F2 doesn't work.  A terminal doesn't work.  And booting into recovery mode doesn't work.  I'm a little lost here.  How do you install this new NVIDIA 169.04 driver.???

Jack Rickard

---

### Post by ArchangelUriel on 2007-11-20
> **jrickard said:**
> The NVIDIA install requires you to completely exit X.  CTRL-ALT-F2 doesn't work.  A terminal doesn't work.  And booting into recovery mode doesn't work.  I'm a little lost here.  How do you install this new NVIDIA 169.04 driver.???

Jack Rickard


Firstly you can use ENVY ([http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html))

OR

To install manually use the following HOW-TO
=====================================
Log out your account. (Ctrl+Alt+Backspace is another option)
Ctrl+Alt+Fx x=1-6 to open a console
```
sudo /etc/init.d/gdm stop
```
To stop the gdm
```
sudo sh NVIDIA-Linux-x86_64-169.04-pkg2.run
```
To run the NVIDIA script (use the right script)
```
sudo /etc/init.d/gdm start
```
To restart gdm

---

### Post by jonah1980 on 2007-11-20
hi just tried installing the .run from nvidia and also using envy but it's not working out for me. i get some mismatch kernel module error or something. and something about the glx module not loading. and also something about displays found but no good.

is there anyway someone can help me get this beta installed and working.

the .run goes through ok but then doesn't work on reboot starting x

and envy runs through ok but also fails on reboot to startx

and i tried uninstalling everything in synaptic nvidia related and then installing but that didn't work. and also tried the envy unistall nvidia button but also to no avail....

---

### Post by jaakan on 2007-11-20
> **chorca said:**
> I'd like to ask everyone here who isn't getting kernel panics if there's someone else who can confirm the locks are only in X. The problem i've experienced only locks up Xorg, the rest of the system beneath it is responsive. A way to test this is to install OpenSSH and use another computer to SSH into the system while it's locked up, and see if you can access it.

I think that what's going on is akin to what was posted previously, that there's serveral different causes for these lockups that lead to the same end problem, and lumping them together in one thread without being able to determine the underlying issue leaves everyone confused. It seems we've been unable to rule out any certain hardware or anything about the lockups. With mine i've narrowed it down to Compiz and Xorg, only Xorg locks up when compiz is enabled.

Looking forward to see others with the same issue. Perhaps we can start another thread, as this clearly isn't limited to x86-64 either.



I'm going to start a new thread called 

"Gutsy full system hard lock up with and without xorg this relates to K2.6.22"
[http://ubuntuforums.org/showthread.php?p=3807468](http://ubuntuforums.org/showthread.php?p=3807468)

it's for lockups not related to the X drivers for ATi or NV cards but the Kernel

---

### Post by jrickard on 2007-11-20
> **ArchangelUriel said:**
> Firstly you can use ENVY ([http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html))

OR

To install manually use the following HOW-TO
=====================================
Log out your account. (Ctrl+Alt+Backspace is another option)
Ctrl+Alt+Fx x=1-6 to open a console
```
sudo /etc/init.d/gdm stop
```
To stop the gdm
```
sudo sh NVIDIA-Linux-x86_64-169.04-pkg2.run
```
To run the NVIDIA script (use the right script)
```
sudo /etc/init.d/gdm start
```
To restart gdm

Thank you so much.  I did get it working.  It kind of stepped back to 640x480 which made it difficult to work with, but I finally got enough resolution up to use the nvidia-settings box and I'm now happily back at 1920x1200.

Summary is that I do NOT have the lockups immediately on booting on within a few minutes.  But on the other hand, this machine never makes it more than six hours or so before doing a total lockup.  The cursor doesn't move, the screen is frozen, and no combination of keystrokes does anything.  Shutting off power and bringing it back up works.  I DO notice an increase in fan speed on the tower.  OCCASIONALLY, it crashes so horribly, that it puts out random noise (loudly) through the speaker system.  But it does it every day, sometimes several times daily.  The system

Gigabit Motherboard
Intel Core 2 Extreme quad processor 6600
GeForce 8800 Ultra video card
4 GB DDR3 RAM
BenQ241W Display
Two 1 TB Hitachi SATA drives
no wireless
Logitech diNovo keyboard and mouse.

At this point, I'm not only not overclocking, I guess I'm underclocking after numerous atttempts to cure this with hardware.  It's almost a relief to find out Ubuntu is doing it from this thread.  

I have some other probably unrelated anomalies that I will mention, though I do not connect them with this lockup problem.

At login, I have to press the keyboard keys numerous times for about 10 seconds before the first key shows up in the login box.  I have other Gutsy installations where this does not happen.

GPHOTO2 cannot locate a camera plugged into any USB ports at all.

But the biggest problem is simply the system locking up.  And it is not mometary.  I can use FIrefox, Swiftweasel, sound players, video players.  Sometimes it locks up when I move the mouse.  Sometimes it locks up when I'm not home.  But eventually it locks up.  I've been 3 days once without a lockup.  But usually it happens 2 to 3 times a day.

I will report back if this 169.04 Nvidia driver has any effect.  In two hours its running fine but that's not a test actually.

Jack Rickard

---

### Post by jonah1980 on 2007-11-20
this is awful, here is a log if anyone can help:

[http://pastebin.ca/791385](http://pastebin.ca/791385)

---

### Post by jonah1980 on 2007-11-20
i get an error called API mismatch...

---

### Post by Tteddo on 2007-11-20
> **Tteddo said:**
> I am thinking I might turn Compiz back on!!
Quoting myself...have had Compiz on since last night, and it's working great.

---

### Post by Azraelthe7th on 2007-11-21
I don't know if anyone's mentioned this before (didn't want to go through 26 pages of discussion at this hour), but I think I found a way to make the 64-bit version of Gutsy Gibbon work.  I essentially installed the "nvidia-glx" package instead of the "nivida-glx-new" package and after rebooting, everything was pretty much great.  If a program freezes, only that program freezes instead of going down and taking the rest of the system with it.

I've been fiddling on Ubuntu for a few hours now (after the package change, that is) and so far I've had no issues other than while running Wine (which simply screwed up the resolution until I logged out and back in).

I don't know if I pretty much figured out what was wrong with my GG installation, but so far so good.  I'll try and remember to keep you posted on it if anything changes (or doesn't as a means of confirming).

Oh, and in case you're wondering, I'm using Compiz-Fusion, the Emerald theme manager, AWN and Screenlets with nary a hitch on my 3D Cube desktop.  Yummy.

---

### Post by lanzen on 2007-11-21
> ArchangelUriel wote
Firstly you can use ENVY ([http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html))

Unless there have been last minutes changes, ENVY does not install 169.0, nor, I seem to remember, 100.14.09.

NVIDIA-Linux-x86-169.04-pkg1.run can be downloaded from nvidia in both 32 and 64 bit flavours, though we're talking amd64 here, ;)  then it has to be manually installed provided a nice clean-up has been make in order to clear references to nvidia-new.

BTW, the page I followed to prepare for nvidia  169.04 installation is:[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)
This page  has been already reported here or in some related thread - not sure exactly where, nevertheless someone might not have read all the post.

---

### Post by ArchangelUriel on 2007-11-21
> **lanzen said:**
> Unless there have been last minutes changes, ENVY does not install 169.0, nor, I seem to remember, 100.14.09.

You are right... ENVY searches for the latest stable and 169.04 is still beta... Mea Culpa. Use the manual method I described.

---

### Post by jrickard on 2007-11-21
Just to close the loop.

I have installed the 169.04 beta NVIDIA driver.  My machine has been running about 17 hours with Compiz and Emerald activated and no lockups.  I'm pretty much convinced
the NVIDIA driver was the problem causing system freezes/lockups.

Gigabyte 6 Quad motherboard
Intel Core 2 Extreme quad 6600 processor
4 GB RAM
NVIDIA GeForce 8800 Ultra video card
2 Hitachi 1 TB SATA drives.
BenQ 241W displaying 1920 x 1200 resolution.

Jack Rickard

---

### Post by jonah1980 on 2007-11-21
> **lanzen said:**
> Unless there have been last minutes changes, ENVY does not install 169.0, nor, I seem to remember, 100.14.09.

NVIDIA-Linux-x86-169.04-pkg1.run can be downloaded from nvidia in both 32 and 64 bit flavours, though we're talking amd64 here, ;)  then it has to be manually installed provided a nice clean-up has been make in order to clear references to nvidia-new.

BTW, the page I followed to prepare for nvidia  169.04 installation is:[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)
This page  has been already reported here or in some related thread - not sure exactly where, nevertheless someone might not have read all the post.

ok thanks for the link but i've removed envy, i've got headers, gcc, pkg etc installed. 

and removed linux-restricted-modules and common and basically tried to do everything the post above says.

my nvidia installer runs through with an error in middle saying  "warning: unable to restore file 'lib/modules/2.6.22-14-generic/volatile/nvidia.ko

and also it can't create it.

and then installer carries on, i update the xorg, reboot and xfails and at a prompt where i have to then change xorg.conf back to nv

it's really frustrating this not working, can't believe all you lucky people that have it working! please if anyone can help...

---

### Post by Tteddo on 2007-11-21
> **jonah1980 said:**
> ok thanks for the link but i've removed envy, i've got headers, gcc, pkg etc installed. 

and removed linux-restricted-modules and common and basically tried to do everything the post above says.

my nvidia installer runs through with an error in middle saying  "warning: unable to restore file 'lib/modules/2.6.22-14-generic/volatile/nvidia.ko

and also it can't create it.

and then installer carries on, i update the xorg, reboot and xfails and at a prompt where i have to then change xorg.conf back to nv

it's really frustrating this not working, can't believe all you lucky people that have it working! please if anyone can help...

I got a similar error, only mine works. What I did differently was setup xorg.conf first (i.e. set it for nvidia and not nv, plus some other settings I like, like disabling caps lock)) and I didn't let the setup tool update xorg.conf. Once I rebooted I was fine.
When I let the tool update xorg.conf it put some generic settings in there that would not work with my setup and I would be left at alogin prompt.

Going on 4 days now with Compiz on for 2. Lookin' good!

---

### Post by williammanda on 2007-11-21
**I just installed 169.04 beta driver and I did the following:**

Debian GNU/Linux or [K]Ubuntu with Xorg 7.x

If you wish to install the NVIDIA Linux graphics driver on a Debian GNU/Linux or Ubuntu system that ships with Xorg 7.x, please ensure that your system meets the following requirements:

    * development tools like make and gcc are installed
    * the linux-headers package matching the installed Linux kernel is installed
    * the pkg-config and xserver-xorg-dev packages are installed
    * the nvidia-glx package has been uninstalled with the --purge option and the files /etc/init.d/nvidia-glx and /etc/init.d/nvidia-kernel do not exist

If you use Ubuntu, please also ensure that the linux-restricted-modules or linux-restricted-modules-common packages have been uninstalled. Alternatively, you can edit the /etc/default/linux-restricted-modules or /etc/default/linux-restricted-modules-common configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via:

    DISABLED_MODULES="nv nvidia_new"

Additionally, delete the following file if it exists:

    /lib/linux-restricted-modules/.nvidia_new_installed

**Then I did these steps:**

sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86_64-169.04-pkg2.run
sudo /etc/init.d/gdm start

I found that I didn't meet all the requirements from above when I just tried to install the new driver.
I will post in the next few days with my results.
Thanks

---

### Post by jonah1980 on 2007-11-21
> **williammanda said:**
> **I just installed 169.04 beta driver and I did the following:**

Debian GNU/Linux or [K]Ubuntu with Xorg 7.x

If you wish to install the NVIDIA Linux graphics driver on a Debian GNU/Linux or Ubuntu system that ships with Xorg 7.x, please ensure that your system meets the following requirements:

    * development tools like make and gcc are installed
    * the linux-headers package matching the installed Linux kernel is installed
    * the pkg-config and xserver-xorg-dev packages are installed
    * the nvidia-glx package has been uninstalled with the --purge option and the files /etc/init.d/nvidia-glx and /etc/init.d/nvidia-kernel do not exist

If you use Ubuntu, please also ensure that the linux-restricted-modules or linux-restricted-modules-common packages have been uninstalled. Alternatively, you can edit the /etc/default/linux-restricted-modules or /etc/default/linux-restricted-modules-common configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via:

    DISABLED_MODULES="nv nvidia_new"

Additionally, delete the following file if it exists:

    /lib/linux-restricted-modules/.nvidia_new_installed

**Then I did these steps:**

sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86_64-169.04-pkg2.run
sudo /etc/init.d/gdm start

I found that I didn't meet all the requirements from above when I just tried to install the new driver.
I will post in the next few days with my results.
Thanks

i tried all this but for reason  to no avail

---

### Post by jonah1980 on 2007-11-21
i get failed to load nvidia module and fatal screen error, this driver is killing me, being trying to install if for days...

tried sudo dpkg-reconfigure -phigh xserver-xorg also in desperation but didn't help...

---

### Post by lanzen on 2007-11-21
> **jonah1980 said:**
> i tried all this but for reason  to no avail

As Tteddo said it's better to make sure that nvidia is selected as driver before leaving gdm.

Do you still have a backup of xorg.conf?

---

### Post by gombosg on 2007-11-21
> **gombosg said:**
> Good news bad news.
I used may laptop for a long time ... with the power cable plugged in.
So the problem may be around power management?

Maybe. so I pulled it out. Restart. Use.
Use.
Use.
It worked... I thought the problem is with CPU frequency switching, but no. It did stepping very well. So I used the laptop for an hour, and just when I wanted to turn it off, it froze.

Boom.

SO, the problem is with using my notebook without power cable. My Linux knowledge is not sufficient, but:
-W-T-F?
-What is the problem? Maybe a kernel module loading at startup?
-What should I try?
-No, fglrx/ati drivers all freeze.
-Wireless? CPU? Anything?

It is crazy to see CPU monitor graphs stop, then, as I click with the touchpad, see them move step by step, then they stop forever only poweroff works.
It is crazy to see a Linux distribution being this unstable.
It is crazy that apart from these Ubuntu would be the best for my needs. :confused:

Edit: there is a BIOS update for my laptop, it says this updates the CPU microcode, I'll try it in the afternoon, it MAY help, but I don't think so.

Crazy solution for this crazy problem, which I got on another forum:
add **noapic** and **nolapic** to kernel boot parameters.

---

### Post by williammanda on 2007-11-22
Well so far so good! I actually had two problems that have been cured so far. 1. Freeze / lockup. 2. Video problem: refer to this url [http://ubuntuforums.org/showthread.php?t=572057](http://ubuntuforums.org/showthread.php?t=572057).
Thanks

---

### Post by ultimatsz on 2007-11-22
i upgraded to the beta driver.. it seems that i will still have lockups, but not as long.hoping for a new release

---

### Post by OnSite511 on 2007-11-22
Yep, I installed the latest beta from nvidia and I've been running perfectly for days now. I followed the post from zippy028 [http://ubuntuforums.org/showthread.php?t=594196&highlight=freezes+resolve](http://ubuntuforums.org/showthread.php?t=594196&highlight=freezes+resolve), but used the beta from the nvidia site and I've yet to crash.

---

### Post by lanzen on 2007-11-22
> **ultimatsz said:**
> i upgraded to the beta driver.. it seems that i will still have lockups, but not as long.hoping for a new release

Which card are you using?

---

### Post by jonah1980 on 2007-11-22
> **lanzen said:**
> As Tteddo said it's better to make sure that nvidia is selected as driver before leaving gdm.

Do you still have a backup of xorg.conf?

it won't work for me. i wondered could someone please made a deb for gutsy amd64 with module and nvidia kernel etc. so i can install the deb files instead of ubuntu ones.

when install normal nvidia ubuntu driver it works but obviously i get the lock ups.

when will this beta be stable in and repos?

and will ubuntu update to it with gutsy due to all probs with current one?

---

### Post by ultimatsz on 2007-11-23
> **lanzen said:**
> Which card are you using?

nvidia geforce go 7300 =( 

core 2 duo problem instead?

---

### Post by lanzen on 2007-11-23
> **ultimatsz said:**
> nvidia geforce go 7300 =( 

core 2 duo problem instead?

Have tried  the new beta from nvidia?

I have amd dual core and G72 [GeForce 7300 LE] as you can see in other posts.

---

### Post by lanzen on 2007-11-23
> **jonah1980 said:**
> it won't work for me. i wondered could someone please made a deb for gutsy amd64 with module and nvidia kernel etc. so i can install the deb files instead of ubuntu ones.

I could make deb out of other things, but this one... I wouldn't even know where to start, sorry.

Manual install it's not difficult: you just have to pay attention at what you're doing and follow the right instructions. It becomes easier with time. Have you tried it?

> when install normal nvidia ubuntu driver it works but obviously i get the lock ups.


Well, that driver works beautifully on other systems,  on my laptop for instance, where I have single core and a nvidia series 5 card, but not here on amd65 dual and series 7 card.

What can i say more...  169.04 has solved.

> when will this beta be stable in and repos?
and will ubuntu update to it with gutsy due to all probs with current one?

No idea, but, you see, the official new driver in the repos is working for the largest majority of people. Maybe the next diver ubuntu will add in the repos will work both - who knows?!?

Will your machine lockup if you remove the nvidia restricted driver? I mean, if you use "nv"? Because if it still does, then the problem lays elsewhere.

---

### Post by ultimatsz on 2007-11-23
> **lanzen said:**
> Have tried  the new beta from nvidia?

I have amd dual core and G72 [GeForce 7300 LE] as you can see in other posts.

not sure but maybe it is because nvidia is unable to go online to download the kernel... i installed it without nvidia downloading the kernel... somehow it works... 

anyways how do i know then 169.04 is not beta anymore?

---

### Post by lanzen on 2007-11-24
> core 2 duo

So, it's intel, isn't it? That might make the difference.

Kernel: you shouldn't need any new kernel; just headers.

Anyway, if it works... 

> 
how do i know then 169.04 is not beta anymore?

Maybe just check nvnews.
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by Fredman on 2007-11-24
I had the same problem on a fresh install of Gutsy on an AMD64 3500+ with 2GB Ram and an NVidia 6600GT. I experienced random locks, only way out was a reset using the reset switch. 

I haven't had a hard lock since I disabled powernowd. Only problem I have now is a random freeze of my USB mouse, but the system itself keeps responding and usable using the keyboard.

Maybe this info is of any help?

---

### Post by jrickard on 2007-11-24
> **Fredman said:**
> I had the same problem on a fresh install of Gutsy on an AMD64 3500+ with 2GB Ram and an NVidia 6600GT. I experienced random locks, only way out was a reset using the reset switch. 

I haven't had a hard lock since I disabled powernowd. Only problem I have now is a random freeze of my USB mouse, but the system itself keeps responding and usable using the keyboard.

Maybe this info is of any help?

How did you disable powernowd?

I installed the new nvidia driver.  Things surely seemed to get better as I was locking up several times daily.  But this morning it locked up again.  So it's not a 100% cure.

I have Intel quad 6600 and Nvidia GeForce 8800 Ultra.

---

### Post by allstar1971 on 2007-11-24
I too, have had the problem with Ubuntu. I have ran Suse and PC LInux and neither has random lockups. I noticed that my screen saver also locks up when it runs overnite.

I really like this system, but I cannot be productive when my computer locks up while using throughout the day.

I believe it may be a memory leak of some sort.

For instance, last night, I was running OPenOffice and copying files from a DVD to my hard drive. The system slowed down and then locked.

If I use certain screen savers, it too locks up.

I have an AMD 3700+, 64-bit system, 1GB memory. Nvidia GF4 card.

I have installed the 32-bit Ubuntu and the new Nvidia drivers and still experience the same problems.

So, I went back to 64-bit Gutsy.

---

### Post by williammanda on 2007-11-24
I still have not had any lockup or screen issues since installing the 169.04 driver. Over two days running at 24 hours a day. This machine is a mythtv master backend.
Thanks

Core 2 Duo 6400
2 GB ram
Geforce 7300 LE

---

### Post by williammanda on 2007-11-24
> **allstar1971 said:**
> I too, have had the problem with Ubuntu. I have ran Suse and PC LInux and neither has random lockups. I noticed that my screen saver also locks up when it runs overnite.

I really like this system, but I cannot be productive when my computer locks up while using throughout the day.

I believe it may be a memory leak of some sort.

For instance, last night, I was running OPenOffice and copying files from a DVD to my hard drive. The system slowed down and then locked.

If I use certain screen savers, it too locks up.

I have an AMD 3700+, 64-bit system, 1GB memory. Nvidia GF4 card.

I have installed the 32-bit Ubuntu and the new Nvidia drivers and still experience the same problems.

So, I went back to 64-bit Gutsy.

I saw this statement on the Nvidia site concerning the GF4 and the 169.04 driver: 

Please note: This NVIDIA Linux graphics driver release supports GeForceFX and newer NVIDIA GPUs, GeForce4 and older GPUs are supported through the 96.43.xx and 71.86.xx NVIDIA legacy graphics drivers.

Here is the url: [http://www.nvnews.net/vbulletin/showthread.php?t=102509](http://www.nvnews.net/vbulletin/showthread.php?t=102509)

Thanks

---

### Post by Fredman on 2007-11-24
> **jrickard said:**
> How did you disable powernowd?.

I uninstalled it using the synaptic package manager. There are some alternatives to powernowd but I haven't installed these yet.

---

### Post by Boricua on 2007-11-24
I don't know what happened, but since my post more than a week ago, this machine stopped freezing. I did keep applying all updates, but no nvidia driver update. I kept doing the same routine tasks and the machine has been working perfectly for the last nine days!. The specs of this machine are the following:
AMD Atlon 64 X2 Dual Core Processor 4200+
Nvidia GeForce 6100 integrated into the mortherboard
1GB RAM
AC97 Integrated Sound Card
Gutsy Gibbon 64bit (fresh install)
Nvidia 100.14.19+2.6.22.4-14.10 driver

---

### Post by wppaas on 2007-11-25
The nvidia beta driver 169.04 did improve my system's behaviour but I'm still having hardlocks when using automatic login and letting the system stay idle for about 10 minutes (I had the same problem on Feisty). Maybe it's the powernow daemon as some people already mentioned. No problems at all using the open source nv driver.

My system is AMD 3200+, 64-bits system, 1GB memory, Nvidia FX5200. I'm running 32-bit Gutsy.

Cheers
WP

---

### Post by empty89 on 2007-11-25
I have the exact same problem with my system. Everything work perfectly until i enable the restricted driver. Then the problem kicks in when nvidia driver is chosen but what did the trick was to uncomment the 2 line of option in red. For me :D.

> Section "Device"
	Identifier	"nVidia Corporation NV43 [GeForce Go 6200/6400]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"[COLOR="Red"]
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"[/COLOR]
	Option		"NoLogo"	"True"
EndSection

---

### Post by StringCV on 2007-11-25
Is this problem Solved?

I got the same problem with Linux Mint 3.0 Cassandra.(and Gutsy Gibbon)
But now I changed to Ubuntu 7.04 Feisty Fawn, and no problem, NVIDIA drivers installed and nothing bad happened works perfect.

Is it safe to switch back (I want Cassandra)? Maybe they already fixed the NVIDIA drivers.

---

### Post by quasimodo69 on 2007-11-26
> **ArchangelUriel said:**
> 169.04 here for some hours, no freezes yet...

+1 for 169.04
Hi ArchangelUriel,
You say you rolled back your nVidia drivers and no crash.As a newbie to this ..can you post a step by step for this for a 3 yeard old like me?I am new to this and desparately trying to get off Micro$oft but I am having problems with only one computer.It is an AMD 64 3000 chip with SATA and IDE.nVidia 5200FX video card.The 7.10 was installed on the IDE drives--crashes constantly.Full install or upgrade.Hard crash-black screen-power down and reboot to re-start.
  I am afraid I do not know what this Envy is or how to use it.How to roll my drivers back.
I am constantly cruising the posts for an answer..though some are over my head.I have another computer on an AMD 32 bit chip that I installed the 386 version and it runs rock solid with an nVidia video card for my guests and they love it!I am trying to get people off micro$oft..but it is hard when they see the fact I can not run it on a more advanced computer.
  since everybody sees this i want to thank all of them for taking the time to post so we can get this worked out.this is the first forum I have taken the time to post to and will continue to look for answers and knowledge...

---

### Post by ArchangelUriel on 2007-11-26
@quasimodo69

First of all welcome to this community. 

Now, as for what ENVY is, what it does and how to install it.
====================================
ENVY is a project for automatic installation of the Nvidia and ATI drivers. It can install the latest drivers automatically and edit all the files you might need edited. It can also unistall the drivers you have installed in your pc... Finaly there is an option about manually install the drivers which actually give you the option to choose from the latest, latest legacy and the previous version of the drivers. After that, the installation is also automated... You can get ENVY from [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) (click on the latest .deb file and use the run option, or save it in your disk and double click it).

About rolling back the nvidia drivers
======================
Use ENVY to unistall the drivers you have, download a previous version from nvidia site, install the older version manually (not with ENVY) (I had posted [here ](http://ubuntuforums.org/showpost.php?p=3806388&postcount=246) how to install nvidia drivers manually).

Nvidia 169.04 drivers
=============
These are BETA drivers so you might not want to install them. Although, a lot of people in here have used them and seems that they can solve the problem if combined with full system update (just install all the updates when the icon of automatic updates comes up).

NVidia 169.04 drivers links.
======================
i386: [http://www.nvidia.com/object/linux_display_ia32_169.04.html](http://www.nvidia.com/object/linux_display_ia32_169.04.html)
x64 : [http://www.nvidia.com/object/linux_display_amd64_169.04.html](http://www.nvidia.com/object/linux_display_amd64_169.04.html)


As for your actuall hard crash - black screen, try the 169.04 (the beta) or the 71.85 (the older drivers). I'm not sure if this will solve your problem, but I wish it does. If you like you can tell us more about what happens when your pc crash... Does it freeze? (you cannot do anything but your screen is still on). Does your screen goes black? If you were hearing music does it stops? 
One proposition is to install an ssh server to your machine (a guide to do this can be found [here](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#SSH)), and use your other pc to connect to the frozen one and give the "top" command. This will show you info about the proccesses and how cpu is used. If a proccess (like Xorg) uses 100% you know you have a problem there.

That's for now... Plz come back and give us a debrieffing... :)

---

### Post by brjoon1021 on 2007-11-26
It is a Firefox or more likely Ubuntu problem. I have the same problem: Firefox will either grey out and lock itself up (some of the time) or occasionally, FF will grey out and lock up the entire system and I have to hard reboot (most of the time) and occasionaly, FF will just crash and go away. When it crashes and goes away, sometimes it will restart, sometimes I am told by dialogue that FF is running and I will have to shut that instance down.

This is happening every few minutes now. It happens with both Firefox 2.0.6, 2.0.9 and Swiftfox 2.0.9. 

I have an AMD athlon XP processor, Asus Mboard, ATI radeon 9700 pro All in wonder video card with the stock drivers for the card, not proprietary driver, let alone, not the Nvidia driver - it is not a Nvidia driver issue as some are surmising...

I have several distributions installed, all use FF from 2.0.6 to 2.0.9 this is the only distro that is having crashes all of the time with FF.

Is there a fix ?

---

### Post by lanzen on 2007-11-26
> **brjoon1021 said:**
>  it is not a Nvidia driver issue as some are surmising...

Yeah, well, there must be something else going on as you and others have the same or a very similar problem while **not** using nvidia cards.

So I must suppose that the new beta from nvidia is bugged because it compensates for for some other bug somewhere else as I haven't had a lock-up in, what, over a week now. I don't remember where, but I read that the nvidia pepole said there was a regression that the new beta driver was trying to fix. Now, ATI also is not working,  so where does it come from? I wouldn't pin it to Firefox, but I could be wrong.

---

### Post by arsham on 2007-11-26
Is it possible to test all these in nested X session?

---

### Post by BoMbS14 on 2007-11-26
I'm having similar lock-up problems with an Nvidia Geforce Go 7900GS. I'm using the 100.14.19 drivers from the gutsy installation.

With Compiz fusion enabled, I get lock-ups, but with it disabled, the lock-ups don't occur, so my guess is that it has something to do with compiz fusion.:confused:

---

### Post by brjoon1021 on 2007-11-27
I don't have compiz-fusion enabled at all. If I just begin to type in [www.yahoo.com](www.yahoo.com), FF goes away ! damn this is aggravating. Where do you post a bug in Ubuntu?

---

### Post by Rapax on 2007-11-27
I was experiencing similar freezes. Never when I was working at the machine, but almost daily (nightly) if I left it idle for a few hours.

After reading this thread, I decided to try the newest beta NVidia drivers - 169.04; I had been using the 100.14.19 ones before. Installation went smoothly, but after a reboot, the machine wouldn't even get to the login screen. Failsafe mode got me a console login, so I could try and revert to the backed up xorg.conf, but that didn't help either.
So I changed the driver to nv, which works. I have now installed envy and have rolled back the driver, first to 100.14.19. then to the next older version, but no luck. If I try and use any nvidia driver now, the machine blackscreens during booting, with the HD LED flashing once a second or so.

Still, I haven't seen a freeze yet while using the nv driver, I'm looking forward to seeing if it survives the night.

Info: Dell Inspiron, AMD64, 2 GB RAM, Geforce 8600 GT, Gutsy 64bit.
Not using compiz or firefox (which seem to be the usual suspects here)

EDIT: Actually, after looking at a lot of the 'freeze' threads, it seems we have at least three different bugs on our hands, that all cause freezes with different symptoms:
One seems to be connected to flash and firefox, and involves the browser crashing, the desktop freezing, but (I think) the keyboard and mouse still responsive, at least partially.
Then there's one that seems to be connected to compiz-fusion that happens randomly and leaves the machine unresponsive, including keyboard, mouse and remote access.
Finally, there's the one I've been experiencing, which also totally freezes the machine (only a power cycle helps), but only occurs when the machine is left idle for several hours. This version occurs without compiz-fusion running, and I've seen at least one report that it even happens when the machine is running totally in server mode (no graphical desktop).

---

### Post by blue-maya on 2007-11-27
I just commeted the following out of the /etx/X11/xorg.conf by putting a # in fron of the lines.

Option "AddARGBVisuals "True"
Otion "AddARGBGLXVisuals "True"

Apparantly my machine is stable for more than 2 hours. Perhaps this solved it??? Lets hope so. I found this out somewhere in this forum about the hibernation problem

Cheers and let us know if it solved your problem. If so, it would be nice to know what actually happens with these settings.

---

### Post by Rapax on 2007-11-27
Before you did this, did you ever experience a freeze while you were working at the machine?

---

### Post by Boricua on 2007-11-27
Oh well, it just happened again:( After more than 10 stable days, I was seeing a power point presentation in openoffice, swiftweasel was also open, as well as an openoffice writer document, when all of a sudden the system freezed. After a hard reset, upon login the openoffice rescue feature appeared but as soon as I activated it (with compiz running), it freezed again. As previously, mouse pointer was alive but useless, as well as the keyboard. Screenlets (clock, graphical status) were still working. Finally, I aborted openoffice rescue document feature and the machine returned to its functional state. This must have something to do with stressing the computer's resources up to a point the system colapses.

---

### Post by TechZilla on 2007-11-28
hey i get the same random hard-lockups. no mouse, defently no keys....and forced hard reset.  happenes evry couple hours, when i "do something"  anything really....
i mean im doing alot at ay given time but, for example last time....
"i locked the seesion"
the time before that 
"watched a flash movie"
although i can do all of these rthings now... just when its ready to freeze, it will.

no records of anything unusual in the syslogs..... no records anywhere as far as i know 
(working linux sysadmin)

ps,  I was usuing gutsy just fine until i upgraded my prosessor from an amd64 3500
to an amd64x2 4200.

ATI 9600.   

do we all have X2's?

---

### Post by glong on 2007-11-28
@TechZilla,

Yes, I have the same chip you have upgraded to - AMD 64X2 4200

I have not had any hard-locks since "downgrading" to Nvidia 100.19.04 (I think that is the right number)  Tried the newest Beta but it just starts boot and brings me to a black screen after bootup.

I still have some strange behavior occasionally - kicked out of GDM, etc, but no hard locks.

Last night I disabled Compiz and that seems to help, but I miss some of the features in Compiz.

With Compiz enabled it slowly eats memory, I think that is when i start having trouble.

Greg

---

### Post by brjoon1021 on 2007-11-28
In the meantime, I installed Opera which I despise in Linux because it won't do ANYTHING multimedia without a lot of  messing around. No Mplayer, No VLC or Real Plugin. This is not working for me.

So, I want to uninstall everything Flash related that is currently installed via synaptic or apt. What should I remove? I see an Adobe Flash Player and a Macromedia Flash Plugin (I may have those companies reversed, but you get the idea). I think that if I uninstall those and reinstall Swiftfox which begins with the vanilla version of Firefox, I can then reinstall the vanilla version of Flash player plugin when promped to by youtube or Yahoo.com

My theory at this point is that the Ubuntu Firefox is messed up or the Ubuntu Flash apps are messed up. As I see FF and the Flash apps in Ubuntu's repo, it looks like they are modified versions ?  I am running the very same revisions of FF and Flash and Swiftfox on other distros with never a problem. I am typing this from PCLOS because Ubuntu's FF crashes every couple of minutes.

Let me know if you think that there might be any merit in my theory before I proceed and possibly make things worse, please. Especially, if you know the best way for me to go about this. I added the Swiftfox repo to synaptic so installing it is easy. I also have medibuntu and multiverse enabled.

---

### Post by kthardin on 2007-11-29
For me, it's a straight out Flash problem.  Every time I go to Youtube, it will play for awhile, but inevitably the system locks and becomes completely unresponsive.  I'm running 64 bit Firefox with the new Flash plugin.

At first that was twitchy as I had the old nswrapper conflicting with the new one, but after I removed all files from the old one, the new one starts and runs fine...at least until the lock up happens.

I have tried moving to the open nv (I run a GeForce 6800) drivers, but that didn't help.  Though it did correct the color problems I was having with some of my video files.

I don't even know where to begin on this one.

---

### Post by Rapax on 2007-11-29
Ok, had two lockups again, one late yesterday, and one during the night. Both happened while the system was idling. acpi -t showed a tempertaure of 22°C at the time of the freezes. These were again, the full lockups (no keys, no mouse, no telnet/ssh, only a hard reset works).

What's interesting is that I'm no longer using any form of nVidia drivers (using nv), no compiz, no firefox, no flash
This seems to be rooted deeper, maybe even in the kernel itself.

Guys, this is bad. It hurts me to admit it, but at the moment, the crown jewel of Linux Desktops, Ubuntu Gutsy, is less stable than Windows Vista. If there's anything we can do to narrow down the options on what's causing this..., maybe we should start an organized list of the different types of freezes, the hardware configs they affect and the software that was installed running at the time. Any ideas how we'd best do that?

---

### Post by kbozen on 2007-11-29
same random freezes

amd 2600+
ATI radeon 9200 SE


any idea ?

---

### Post by rlattuad on 2007-11-29
Hi,

had this problem for a while, HPnz9420 randomly crashing due to overheating. Looked as various software solutions but then also tried cleaning the fan and guess what the cleaning did the miracle.

I used a hoover over the fan grate and sucked all the dust out, worked great no more temperature problems, CPU throttle works great and so does the fan. I suspect that the sensors got dirty thus rerporting wrong values and this screwed up the whole system which was not able to cope.

BTW I also raised the laptop a bit to leave more room for air circulation underneath.

I tested running both CPU at almost 70% load (7 movies at the same time) and the temperature never went above 40C, air flow is cool and in fact I have far less problems with the reliability of the ATI card as well.

So a suggestion: clean the vent first and look at a SW solution later

Hope this helps
r

---

### Post by mikeize on 2007-11-29
I have this same problem.  System completely locks up unpredictably.  No mouse, no keys, no ctrl+alt+backspace... nothing.  Also, because I haven't seen anyone else mention it yet, my screen is a little static-y during the lockups.  It's like it's locked up and freaking out at the same time!  I thought that it might be my graphics card overheating, but I don't have any sensors on it so I don't know for sure...  but the fan on it seems to work fine, and the lockups will even occur at times of complete idle, though they can occur randomly while using ANY program (firefox, wine, ktorrent, electricsheep screensaver, etc).  

This is a newly built computer with all new components, and an install (rather than upgrade) of Gutsy.  I checked all the error logs, after the last lockup/hard reboot, but it seems it was a non-event as far as the system is concerned.

My processors are hardly ever taxed at all (except when nautilus gets out of hand, they go up to 50%), though they seem to run a bit above normal temperature (anywhere from 92-115 deg F).  I've never noticed a problem with ram usage, though I obviously can't say what is happening during lockups!

Other than this problem (and the comp randomly not waking up from sleep--which may be related?) everything works fine--nvidia new drivers from the repos run compiz, electricsheep, nexuiz, dvds, etc just fine.  No system lag from memory or processor limits, read and write speed seems normal.

I don't always know what info to provide, so if anything sounds interesting to someone, don't hesitate to ask for more details.  I would love to see this bug put to rest.

-mike

---

### Post by Ben64 on 2007-11-30
I've been having this problem as well. My computer freezes seemingly at random, the only thing in common with each freeze is Firefox. I've tried different versions of Firefox, the Nvidia driver, turning apm off and everything else I saw here. Just a few minutes ago I compiled a new kernel (2.6.23.9) to see if that will resolve it. I will post with my results in a few days or after my next lockup, whichever comes first.

---

### Post by aaapha on 2007-11-30
I had the same problem, 10 minutes uptime max.  I lost the restricted drivers, got Envy and installed the older driver (96.43.01).  Not a problem since, up for 4 days solid.

---

### Post by ml98133 on 2007-11-30
This all seems so discouraging to me....

I switched from FC3 to Ubuntu 7.04 several months ago for a mythtv box.  (actually on two computers.)  Since then, they lock up every 1-10 days.  Although in this thread that sounds good, that is way too unstable for me.  I need something that is reliable for months.  This is our TV, so it has to work...like a TV does.  With FC3 it did.

I started upgrading to 7.10 because I thought maybe that would help, and then I came upon this thread and canceled the install.

Is this thread just an extremely small percentage of users who have various problems, or is this something that is common?  I get the impression a lot of people have random lockups.

I can't believe it's a released version of a distro with this many problems, especially complete random lockups.  It seems like even 32bit users have issues.

I know there's no yes or no answer, but I'm guessing that I should steer clear of Ubuntu if I want something stable on my AMD 64.  I guess I'll try FC6...or maybe go back to FC3 although that will require a lot of manual driver building.

I suppose there's probably a lot of people with any distro that have some kind of hardware or configuration problem that causes them to lock up...but this thread makes it seem as if Ubuntu is especially prone to these problems and for some reason they are extremely difficult to resolve.

---

### Post by cmileto on 2007-12-01
Its definately the nvidia driver. the nvidia forums have posts with the same problems and such.

[http://www.nvnews.net/vbulletin/showthread.php?t=103434]("http://www.nvnews.net/vbulletin/showthread.php?t=103434")

---

### Post by Rapax on 2007-12-01
> **cmileto said:**
> Its definately the nvidia driver. the nvidia forums have posts with the same problems and such.

[http://www.nvnews.net/vbulletin/showthread.php?t=103434]("http://www.nvnews.net/vbulletin/showthread.php?t=103434")

Nope, I'm having the freezes and I'm not using any of their drivers. In fact all the following 'usual suspects' have been checked:

nVidia drivers
Firefox
flash
compiz-fusion

I've got rid of it all, just to be sure, and the freezes still happen.
Oh, and it's not overheating, as the system only freezes when it's idle, and running a ta temperature of about 2°C above ambient (22° usually).

---

### Post by ultimatsz on 2007-12-01
i have something to add.....
i have a acer aspire 5583... no problems at all.....
now i changed it to aspire 5584 model... have random hang issues!

i m using 5583 when gutsy gibbon is not released yet....however.. it works entirely with feisty

5584... random hangs on feisty stock. and also on gutsy. feisty have startup slow issues.

the difference between 5583 and 5584, intel accelerated graphics(unsure why it uses nvidia driver in ubuntu) to nvidia 7300 geforce go.

512 ram to 1gb ram.

duo core processor from T5500 to T5600,(yes... 5583 runs on duo core but did not lockup)

therefore... problem... either lies on the ram (which i dont think so)
or nvidia graphics card... (i know 7300 cause many problems)
removing one cpu does not work... so i think 7300 have the most problem (try searching nvidia 7300 in ubuntuforums.)

---

### Post by Ben64 on 2007-12-02
Well it's been 48 hours now with no lockup. This *could* be the answer, maybe it was the kernel, or the modules, I don't know. What I did was compile everything I needed into the kernel instead of as a module, and got rid of tons of modules I would never use on my system.

I know kernel compilation isn't the friendliest activity for a new user of Linux, but if you've tried other solutions in here and still have a problem, go for it. :)

---

### Post by Bluejacket on 2007-12-02
With the 100.14 Nvidia driver my laptop crashed 3 times in 20 minutes today. I installed the new beta driver, and no crashes so far.

---

### Post by jonah1980 on 2007-12-02
i hope they stable this driver soon!

---

### Post by Rapax on 2007-12-02
Had enough of this. I installed the 32bit version of Gutsy on Friday, and so far, no more freezes. Seems the 64bit version just isn't ready.

---

### Post by lanzen on 2007-12-02
Good news first:

Since I've installed the 169.04 nvidia driver, and it's quite a long time now, I have **not** had a single lock-up.

Now... the bad news:

Yesterday I wanted to see how a metacity theme looked like and, as I'm using emerald, I went to the special effects settings window and disabled compiz. Later I wanted compiz back and... nightmare: in less than the time I could say "What the hell is happening here" I was back to the 100.19 driver!  :confused:

'Course it was my fault:I didn't pay enough attention to the message that appeared and gave ok to the install.

Everything was working perfectly and had no freezes, but, as I knew I had to expect them, I patiently  went through the whole delight of going back up to 169.04... It's been a mess ever since and 100.9 kept coming back. I still haven't sorted that out.

So, for what it's worth... don't touch compiz if it's working!

---

### Post by jaakan on 2007-12-02
> **ultimatsz said:**
> i have something to add.....
i have a acer aspire 5583... no problems at all.....
now i changed it to aspire 5584 model... have random hang issues!

i m using 5583 when gutsy gibbon is not released yet....however.. it works entirely with feisty

5584... random hangs on feisty stock. and also on gutsy. feisty have startup slow issues.

the difference between 5583 and 5584, intel accelerated graphics(unsure why it uses nvidia driver in ubuntu) to nvidia 7300 geforce go.

512 ram to 1gb ram.

duo core processor from T5500 to T5600,(yes... 5583 runs on duo core but did not lockup)

therefore... problem... either lies on the ram (which i dont think so)
or nvidia graphics card... (i know 7300 cause many problems)
removing one cpu does not work... so i think 7300 have the most problem (try searching nvidia 7300 in ubuntuforums.)

Does Broken BIOS show up on either of those computers?

should like something like this

jaakan@AMD64:~$ cat /var/log/dmesg | grep Broken
[   21.849353] via-rhine: Broken BIOS detected, avoid_D3 enabled.

---

### Post by Ben64 on 2007-12-02
Well, just had another lockup. Seems the kernel change didn't fix it. I am on 169.04 ... I really wish I knew how to solve this, but the lockup doesn't generate any log so its like finding a needle in a haystack.

---

### Post by Saint Angeles on 2007-12-02
> **Rapax said:**
> Had enough of this. I installed the 32bit version of Gutsy on Friday, and so far, no more freezes. Seems the 64bit version just isn't ready.
heh, i did this on friday also.

my PC(pentium 4) runs better with 32 bit hyperthreading (OS thinks i have 2 CPUs) than it did with 64bit.

so far so good, but i think the latest release of compiz isnt as good as the one before it.

---

### Post by lanzen on 2007-12-03
It might well be that 32bit fixes it on some systems, but the are reports of the same lock-ups.

See: [http://ubuntuforums.org/showthread.php?t=585714](http://ubuntuforums.org/showthread.php?t=585714)

What I've noticed since my last post is that /etc/default/linux-restricted-modules-common gets re-written.

One of the necessary things one needs to install 169.04 and making sure nvidia.new doesn't come back is to insert the option:

```
DISABLED_MODULES="nv nvidia_new"
```

into linux-restricted-modules-common

---

### Post by lanzen on 2007-12-04
As a follow up to my post #313 I reinstalled Gutsy. Of course I had it all back, freezes included.

So I decided to follow this instructions:
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual) 
They are no different from others, but at least they're "official".

Now I'm back on 169.04 and no freezes.

When restarting gdm I was left with black screens, but on booting up everything came back.

Now this success story is just a patchy fix and I hope that the real bug (or concurring bugs) gets resolved.

This works on
AMD Athlon 64 Dual Core 3800+
Nvidia G72 [GeForce 7300 LE]

---

### Post by Rapax on 2007-12-04
> **lanzen said:**
> It might well be that 32bit fixes it on some systems, but the are reports of the same lock-ups.

See: [http://ubuntuforums.org/showthread.php?t=585714](http://ubuntuforums.org/showthread.php?t=585714)


No, that looks like totally different symptoms to what I was having with 64bit. for one, my freezes weren't happening as often as those (every 8 hours or so, usually), and they also never happened when I was working at the machine, only when it was idle for a few hours. I think it's safe to say that these two issues are unrelated.

---

### Post by hoarycripple on 2007-12-05
I too was having problems with X lockups with the 100.14.19 nvidia kernel modules. I installed the 100.14.23 kernel modules, and the lockups seem to have disappeared.

My system:
dual intel xeon 5140
8GB RAM
NVIDIA GeForce 7950GT
SAS hard disks
Supermicro X7DA3 Motherboard
Twinview Configuration
Ubuntu 7.10 AMD64
Kernel 2.6.22-14-generic x86_64 SMP
latest nvidia-glx-new
nvidia kernel modules 100.14.23
XDM greeter (occurred with GDM greeter too)

The specific problem I was having: X lockup when under load, Xorg taking up 100% CPU time. This would occur when trying to compile something in a terminal while in an X session. Transcoding/mplex'ing a video would *always* cause it to lock. The lockup caused one of the twinview screens to go blank and my monitor flashed the message "OUT OF RANGE." I would then lose the ability to switch to a VT, and I could not get a greeter back at all even after killing the Xorg process and killing XDM/GDM. The only remedy to getting back a GUI was to ssh in from another system and reboot. All non-GUI programs running over GNU screen (irssi/mutt/vim etc...) were still running without problems when I ssh'd in from the other computer.

Another type of lockup was when playing 3D games: quake3/urban terror would lock sometimes on exit, and would require the same remedy as above.

So far, no lockups in either of the situations described above using the 100.14.23 kernel modules. I'm keeping my fingers crossed.

Good luck to you all.

---

### Post by jonray74 on 2007-12-05
Hello all,

I too have experienced a lockup, freeze, and my screen goes blank unconditionally at random times after I enabled the Restricted drivers for my ATI 9600 Pro Radeon card, and installed the XGL server and Compiz-Fusion.

When I start to play my DVDs using Totem xine, the screen goes blank, and I press CTRL+ALT+Backspace to reboot cause i couldn't get the screen back. Other times is when i'm running apps, (ie firefox, or OpenOffice, etc.) that the screen freezes but i can move my mouse but can't click on any icons. 

I also experience complete freeze when i'm downloading for instance or just opening Synaptic or any apps or just simply moving my windows. Really odd.

Prior to enabling the Restricted drivers, the system ran perfectly without lock-ups and I could play around with Compiz-Fusion with cubes, play DVDs, run multi-apps with  the exception of screensaver being off cause the ScreenSaver just runs very slow with the standard drivers, other than that, I can do whatever with it but the disadvantage of just using the standard drivers not the proprietary ATI drivers. After I enabled the Restricted drivers, and installing XGL (i've tested this 20x now after so many re-installs), that's when I get the lock-ups, freezes. Somehow i'm finding now, that the culprit maybe in the enabling of the Restricted drivers and installing XGL and running Compiz-Fusion with it, at least for me, after doing 20x of re-installations.

So my conclusion to this is for now is, to use the standard drivers that came with Ubuntu and not the proprietary drivers. I don't know as to when these proprietary drivers will be able to support all types of ATI cards, but as of now I will try not to get into the temptation of re-enabling the Restricted drivers because I know for sure, that the system will start locking up, once they've been enabled. Having reinstalled my Gutsy 20x now enabling and disabling the Restricted Drivers.

Anyways, that's my thoughts on it. If anyone experienced the same, stick with the default installation of Ubuntu for now, since Compiz-Fusion runs well on it. At lease for me it did after I re-installed Gutsy, the only disadvantage is that I couldn't get my Video Card to run to its full capacity (ie, do full 3D rendering, enabling 3D Screensavers) because it's using the default drivers supplied by Ubuntu.

Wow...that was long...

Thanks, pop corn anyone...:popcorn:?

:D

---

### Post by Legu on 2007-12-05
Yeah, i have freezes too. They're total freezes; cursor doesn't move, CD-tray won't open and screen remains frozen, no matter what I try to do. :(

I have 'nvidia' 100.xxx drivers and the card is GT 6600. I'm using 32-bit Gutsy (CPU is 64-bit though).

I have a sense that freezes happen mostly when using Compiz: rotating cube etc.

Hope you get it fixed soon, its **really** annoying. It makes Gutsy unuseable.


BTW, I find Ubuntu very laggy (mouse jumps and stuff) when running process/processes which uses/use lots of CPU (like update-manager). It's odd that it happens only on my home PC, not on my laptop. It should be taken care of too, I think.

---

### Post by brjoon1021 on 2007-12-05
I found a solution for me.
 
I installed ubuntuzilla (google for it) which is the standard release of Firefox from Mozilla. I stayed clear of Flash from synaptic or anything that came with ubuntu to handle Flash content. Previously, I had installed Flash from synatpic. This time, I installed Flash from the prompt that you get from the firefox browser when you have navigated to a website that needs Flash. Just to make sure that this was not the version of Flash somehow coming through synaptic / Ubuntu, I have checked synaptic and it does not show Flash or the flash plugin installed. 
Let me stress that I have installed & gotten frustrated by the crashes and then reinstalled Gutsy and Mint at least 6 times over the last two weeks. All of the installs crashed like crazy when surfing with Firefox, especially [www.yahoo.com]("http://www.yahoo.com/"), for some reason would crash the system every sngle time. But this time, by avoiding the ubuntu branded and customized FF and Flash and Flash plugin, I am rock solid. The **[COLOR=red]ONLY[/COLOR]** software or hardware changes have been the FF and the Flash. I suppose it is worth it for you to try. 
 
As an aside, I have never used or had the google toolbar, never used or had a proprietary video driver. I uninstalled, reinstalled, compiz. Always crashed anyway whether it was installed, uninstalled or active.

---

### Post by linuxuser187 on 2007-12-06
does the same thing happen if you disable the restricted driver and use the open source driver, my system also frezes every couple of minutes sometimes to the point that ctrl+alt+backspace does nothing and i would have to do a hard off, i disabled the restricted driver and my system didn't freeze once! i'm still taking a look to ses what it is but in my case it seems to be related with my nvidia restricted driver, flash on my firefox and everything else is working and not a single freeze at all,

---

### Post by KrisWillis on 2007-12-06
An update from my front. After downgrading my video driver last week everything appears to now be working fine.

I downgraded from 100.14.19 to 100.14.09

No lock-ups so far.

---

### Post by aaapha on 2007-12-06
> **KrisWillis said:**
> An update from my front. After downgrading my video driver last week everything appears to now be working fine.

I downgraded from 100.14.19 to 100.14.09

No lock-ups so far.

I did the exact same thing, but via Envy and to the 96.43.01 driver.  Not a lock up since.

---

### Post by Ben64 on 2007-12-07
Well, a few days I got fed up with the crashing and started using the "nv" driver. It was doing really well until just now, when it froze up exactly how it did with the nvidia driver. I'm starting to think it's a problem with the flash plugin, not with nvidia, or ati, or the kernel. It's probably flash and the wrapper used to get it working on 64 bit. Also, over the past few days I've noticed more and more memory being used, while having the same amount of programs running. Something is eating all of my memory, then killing my computer. I really hate the idea of doing another OS install, but it seems to be my only option left.

To those people that have 'fixed' it, be wary, although you may have lessened occurrences, the problem could still be there.

Also, why have we not received any response from the Ubuntu team regarding this issue? It's pretty serious for anyone that uses Gutsy on 64bit with Firefox.

---

### Post by Yumi on 2007-12-07
Where did you find the nvidia driver 100.14.09. I want to try this. am fed up with Gutsy.

Michael

---

### Post by mikeize on 2007-12-07
> **Ben64 said:**
> 

Also, why have we not received any response from the Ubuntu team regarding this issue? It's pretty serious for anyone that uses Gutsy on 64bit with Firefox.

I agree, but it's not just 64bit.  Others here including myself are running the 32bit gutsy.  Personally I have an intel c2duo (not 64).

-mike

---

### Post by thebinz on 2007-12-07
I am also getting nonstop freezes and lockups using my nvidia Geforce 7600 GT on Gutsy 64.
I have the nvidia 100.xxx drivers installed.

I was wondering if anyone else was getting a following problem.

Usually at random my screen will just flick and become all messed up like the created screenshot below. 
It's hard to explain but it is like the coordinates become all messed up.
The only way for me to fix the problem is to reboot.

I cannot function with my mouse when this happens. The actual appearance of the mouse cursor will be on the left hand side of the screen but i will be clicking somewhere on the right hand of the screen and visa versa. I have to guess where to click when saving open documents and shutting down. All windows and open apps become cut apart and virtually unusable.

Is anyone else experiencing this problem?
This happens completely at random and at least 3 times a day.

This is my normal Desktop:
[IMG]http://i64.photobucket.com/albums/h163/theillphil/Screenshot.png[/IMG]

This is when things mess up:
[IMG]http://i64.photobucket.com/albums/h163/theillphil/Screenshot_broke.png[/IMG]

---

### Post by KrisWillis on 2007-12-10
> **Yumi said:**
> Where did you find the nvidia driver 100.14.09. I want to try this. am fed up with Gutsy.

Michael

[http://www.nvidia.com/object/linux_display_ia32_100.14.09.html]("http://www.nvidia.com/object/linux_display_ia32_100.14.09.html")

---

### Post by supernovus on 2007-12-11
This is a very unusual problem. The lockups I'm getting are solid. Nothing works, the mouse and keyboard go dead (including Magic SysRq keys) and nothing works at all except the six second power button.

This is an Athlon 64 X2 3800+ with a GeForce 7300 card (as I see the suggestions in here that it may be related to the 7xxx series of cards), however I'm not so sure it's the driver that is causing the problems, instead I would almost suggest the kernel version. 

I say this because I installed Windows and ran Gutsy in a VMware session. It still had the same lockups, except that it only managed to lock up VMware (to the point that I had to close the program in the task manager because even the power button in the interface didn't work).

I reinstalled it on the physical computer, and tried all sorts of things to fix it. I upgraded to kernel 2.6.23.9, I upgraded the Nvidia drivers to 100.14.09 (using Envy). Eventually I gave up and went back to Feisty, where I had never had these issues. No here's the kicker. I tried upgrading to kernel 2.6.23.9 on Feisty, keeping features like tickless kernel off, and using SLAB instead of SLUB.  Wouldn't you know, it started locking up again.  So here I am, back on 2.6.20 and so far, no locks.

I hope whatever 2.6.22 and 2.6.23 have that is causing lockups, is fixed in 2.6.24 as that is the version being proposed for Hardy, and I'd hope that an LTS release doesn't cause major lockups. BTW, I have tried both the 64 and 32 bit versions and they both have the same symptoms. I'm back on 32 bit for now.

I'm not running Compiz at all on this machine, nor Network Manager, Tracker, Beagle or Bluez. In fact they are all uninstalled.

Now, here's a kicker, on an older machine (a 2ghz Celery with a Geforce 6200) I have no problems at all. I can run Compiz with loads of eye candy enabled, and watch videos in full screen, while ripping CDs, and there is no frame loss, or lag.  That machine has 1 GB of DDR1 RAM, while this machine has 3 GB of DDR2 RAM.  It makes no sense.

Anyway, just thought I'd add to the already massive thread.  Is there any common links? Or is kernel 2.6.22/2.6.23 cursed?

---

### Post by samasaur on 2007-12-11
I believe I have this issue as well. But I don't have any idea whats causing it nor any experience to even figure out why. My computer specs are AMD X2 4200+ dual core, DDR2 1gb ram, sata2 250gb harddrive, GeForce 7300GS 256mb video card with a fresh install of Ubuntu 7.10. My problem is pretty severe. I originally thought it was my dual screens that were causing the problem, but after I took it off and disabled it, turns out that wasn't the case. When it freezes, nothing works which forces me to do a hard reboot. I'm not sure if this is related, but my video also screws up sometimes, like when I'm watching a video, it blanks out for a few seconds, but screen comes back, the video is still playing, but the image is all distorted and becomes unwatchable. This is not a memory problem because I did a memtest and fiesty, xp and even Vista worked fine on this computer. My desktop is been too unstable to work on, I've been forced back to XP on my laptop for the time being. Its been like this since I got gusty and its been a month or two since its release. Are they going to prioritize this issue because I would consider this to be pretty big compared the other security patches they release on the updates.

---

### Post by Bokonon on 2007-12-11
I strongly suspect the 7300 + certain drivers are one of the main causes of problems here.    Obviously there are multiple problems here, but if you have a 7300 try different drivers or a new card.

Again, I am running fine and have had no lockups after switching to my 6800GT.  Bundled nVidia driver, gusty 64.

---

### Post by poodlediagram on 2007-12-12
I have the exactly same problem with my AMD X2 4000+ and NVIDIA GeForce 7300 LE (512MB).

I find the problem is reproducible by scrolling through the screensavers: when you reach "Braid" the system freezes, and usually requires a hard reset. The only way I've found to improve the situation is to install "xserver-xgl" which substantially decreases the frequency of the hangs.

---

### Post by wyth on 2007-12-12
Allow me to pile on; I wish I found this thread two days ago, but didn't, and ended up starting my own [here]("http://ubuntuforums.org/showthread.php?t=637708").

[COLOR=Blue]***However, this is not a 64 bit system.  It looks like this thread is just for 64 bit systems, but I'm having the exact same problems.***[/COLOR]

So I'll just post what I had there, with some updates:

** The problem:** Every now and then, my system completely locks up. The mouse freezes, the screens freeze, I have no keyboard function, nothing.
[B]
The circumstances:[/B] This happens completely at random, and it started about three days ago: It's happened while booting up. It's happened while using Gimp. It's happened when checking email. It almost always happens when the screensaver kicks in.  It happens with Compiz enabled and without (I use almost no plugins).  It was happening with the 2.6.22-14 kernel, but also happened when I rolled back to the previous one (which I believe was still a 2.6.22 kernel).

** The specs:** I'm running Gutsy with an ATI Radeon R250 (9200) with the open source drivers. CPU is a Pntium 4-M. The fans don't go bonkers when it locks; in fact, they do nothing at all, and nothing feels hot (after all, sometimes it happens while logging in). My laptop sits on a chill pad, so it stays cool. I opened it up yesterday and checked for dust; it's clean. I run a bare minimum of Compiz effects, less than the Normal setting; I tried it with the effects both on and off, and still got the lock-ups. 

**The diagnostics:** My laptop is old and I'm hard on it, so I was afraid this was a hardware issue.  I didn't find anything out of the ordinary in the logs, but may not have seen the right ones. My system hasn't run fsck in some time; I popped in a live CD and fsck'd my partitions, and everything seemed cool. Then I rebooted, downloaded some podcasts, stepped out for a bit, and returned to another frozen laptop.  Re-seated the memory and ran memtest overnight.  No problems or issues.

I had upgraded from Feisty before, so I went ahead and did a fresh re-install today.  So far I've been working for about 5 hours with no problems whatsoever.

But I'm glad to see I'm not alone on this.

---

### Post by arhamlinux on 2007-12-12
I had this problem, but I don't have it anymore. Do you know why? Its FIREFOX !
Try to open anything but firefox. Find out what happen. If Ubuntu still freeze, well I was wrong.

However, Firefox's team should take care of this issue. I use Epiphany know unless I need some thing that Epiphany cannot do, e.g. download video from Youtube. I use Firefox's extention, instead.


-----
Linux is not about software, It is about FREEDOM!

---

### Post by ka9qlq on 2007-12-13
I'm running Gusty Kubuntu 32 bit on a
Biostar MB with a GeForce 6100 onboard vid
AMD x2 4800
2 gig of DDR RAM 
1 80 gig & 1 160 gig IDE & 1 160 gig SATA & 1 usb 500 gig HD
a brooktree tv card

And randomly (NOTHING seems to be common) the screen suddenly looks likes someone threw paint on the screen (diagonal multi colored lines) and the ethernet light on the 2wire router goes off and sometimes the hd light on the front of the PC stays on solid. I'm thinking of trying envy to change the Nvidia drivers and if that flubs go back to Feisty. I will say I tried the Sayboyan 3.4f and it did the same. THIS IS NUTS! I wish they'd come out with a fix on the repositories.

Hay do you have to do anything (like disabling anything) before you run envy?

---

### Post by Melcar on 2007-12-13
Same here.  My Windows partition is more stable than this.  The log files are close to useless.  I want to blame my video drivers (fglrx) since I have had two system freezes when running Compiz, but I remember the system freezing even when I was using Vesa.  I'm also on x86_64 by the way.  I may try the 32bit version latter on.

---

### Post by PatrickMay16 on 2007-12-13
Oh man, thank goodness. I have the same problem, which began after I updated to gutsy this month. I was worried I had damaged my system when transferring the parts to my new case, but since everyone else here is experiencing the same, and this mysteriously began after I updated, this must be it.

I am also using the nvidia binary drivers. I'm a slick man with the "ge force" video graphics board. It is the "ge force 7600GS" that I use.


BTW, I'm using the 32bit ubuntu. I think at this rate, I'll try downgrading to "feisty" and seeing if that helps. Is there any method of downgrading? I would really like to get by without reinstalling.

---

### Post by wyth on 2007-12-13
> **arhamlinux said:**
> I had this problem, but I don't have it anymore. Do you know why? Its FIREFOX !
Try to open anything but firefox. Find out what happen. If Ubuntu still freeze, well I was wrong.

Mine froze on login; it never made it past the gdm, so firefox never had a chance to start up.

I since re-installed, and noticed I was getting the same problem whenever the screensaver kicked in.  Otherwise it's been stable.

Is there a launchpad report on this?  There's 34 pages on this thread, and I'm finding a number of other threads with the same issues.  It's obviously a problem that needs addressing.

---

### Post by wherethebibawi on 2007-12-13
I am running i386 version of gutsy and I get this problem (so far twice) I also have an ATI Radion graphics card. The last time I got this kind of lock up I was surfing the forums in firefox and I opened a terminal window and bang total freeze.:confused:

---

### Post by supernovus on 2007-12-13
A followup to my assumption that this was kernel related. I recently was testing openSUSE 10.3 on this computer, and it runs 2.6.22, and presto, the lockups occur in it as well.

It seems to happen more when Firefox is open, and more when using Nvidia drivers, but those do not seem to be "necessary" for this to happen (as the vmware driver also locks up, and I've had it lock up without loading Firefox).

So this is not specific to Ubuntu. It's a kernel issue.

I'm sticking with Feisty and it's non-locking 2.6.20 kernel until someone figures this out.

---

### Post by Melcar on 2007-12-13
> **supernovus said:**
> A followup to my assumption that this was kernel related. I recently was testing openSUSE 10.3 on this computer, and it runs 2.6.22, and presto, the lockups occur in it as well.

It seems to happen more when Firefox is open, and more when using Nvidia drivers, but those do not seem to be "necessary" for this to happen (as the vmware driver also locks up, and I've had it lock up without loading Firefox).

So this is not specific to Ubuntu. It's a kernel issue.

I'm sticking with Feisty and it's non-locking 2.6.20 kernel until someone figures this out.

I tried using the latest stable 2.6.23.9 kernel, and still the system lock-ups.  I'm leaning towards video drivers, but I could be wrong.  Every single poster on this thread has different hardware/software configuration, but there must be something we all have in common that is causing this.

Current System:
Ubuntu 7.10; 2.6.22-14-generic (x86_64)
Fglrx 7.11
AMD Opteron 165
DFI LP Ultra-D
2GB DDR500 RAM
X1950XT 256MB
Audigy2 Value

---

### Post by PatrickMay16 on 2007-12-13
> **Melcar said:**
> I tried using the latest stable 2.6.23.9 kernel, and still the system lock-ups.  I'm leaning towards video drivers, but I could be wrong.  Every single poster on this thread has different hardware/software configuration, but there must be something we all have in common that is causing this.

Current System:
Ubuntu 7.10; 2.6.22-14-generic (x86_64)
Fglrx 7.11
AMD Opteron 165
DFI LP Ultra-D
2GB DDR500 RAM
X1950XT 256MB
Audigy2 Value

Excuse me, sir. My system which is locking also has an AMD Opteron, and a Sound Blaster Live which is very similar to the Audigy, and probably uses the same drivers.

My kernel is also  2.6.22-14-generic, however it is not x86_64.

---

### Post by Melcar on 2007-12-13
> **PatrickMay16 said:**
> Excuse me, sir. My system which is locking also has an AMD Opteron, and a Sound Blaster Live which is very similar to the Audigy, and probably uses the same drivers.

My kernel is also  2.6.22-14-generic, however it is not x86_64.

Interesting.  What graphics card/drivers are you using? 
I just wished the log files were easier to read.  The closest thing to an error I found from the logs is warnings from fglrx, that is why I'm thinking it's a graphics card issue.  However, the freezes/locks did not start on my system until I installed the Audigy, but then again, the logs show nothing that could point to that device being at fault.  My CPU is overclocked, but it's dead stable in Windows (maybe Linux is more delicate to CPU errors then?).

---

### Post by LinkRJH on 2007-12-13
Same issue as everyone else.  AMD Athlon 64x2 5000+, GeForce 7300LE, running on x86_64.

---

### Post by PatrickMay16 on 2007-12-13
> **Melcar said:**
> Interesting.  What graphics card/drivers are you using? 
I just wished the log files were easier to read.  The closest thing to an error I found from the logs is warnings from fglrx, that is why I'm thinking it's a graphics card issue.  However, the freezes/locks did not start on my system until I installed the Audigy, but then again, the logs show nothing that could point to that device being at fault.  My CPU is overclocked, but it's dead stable in Windows (maybe Linux is more delicate to CPU errors then?).

My CPU was also overclocked, and I reset all clocking options to their normal defaults to see whether that was the cause. The system still froze, so the overclock was not the problem in my case.
My graphics card is an Nvidia Geforce 7600GS, and I'm using the proprietary NVIDIA drivers.

A curious situation indeed. Perhaps the SBlive/audigy driver is responsible for this. Everyone who has this problem, let's post out "lspci" outputs.

> 

00:00.0 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
00:0b.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
00:0b.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
00:0e.0 Ethernet controller: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter (rev 11)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GS] (rev a2)



Right now, I've reverted to using the  2.6.20-16-generic kernel which was still installed. However, now the nvidia driver will not load with this kernel. So I'm forced to use the "nv" driver.

I will run my computer like this for as long as I can. I expect that it will not freeze with this kernel.

---

### Post by Melcar on 2007-12-13
> **PatrickMay16 said:**
> ...



Right now, I've reverted to using the  2.6.20-16-generic kernel which was still installed. However, now the nvidia driver will not load with this kernel. So I'm forced to use the "nv" driver.

I will run my computer like this for as long as I can. I expect that it will not freeze with this kernel.

You need to re-install your video drivers any time you change kernels.


> 00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev a2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value
01:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
05:00.0 VGA compatible controller: ATI Technologies Inc R580 [Radeon X1900]
05:00.1 Display controller: ATI Technologies Inc Unknown device 7264



I just finished compiling a new 2.6.23.9 kernel.  Most of it is "stock", or rather, the defaults the Ubuntu kernel has (I just copied the config over), except for CPU type (chose the proper CPU arc.).  I will let my PC run like this for a few days and see what happens.

---

### Post by botheredbybees on 2007-12-14
I was having the same problems. When I ran top in a terminal window I noticed udevd taking a big slice of CPU time - after removing evms as per [this post]("http://ubuntuforums.org/showthread.php?t=450206&highlight=udevd") everything seems to be under control again

---

### Post by Ben64 on 2007-12-14
[quote=supernovus]I reinstalled it on the physical computer, and tried all sorts of things to fix it. I upgraded to kernel 2.6.23.9, I upgraded the Nvidia drivers to 100.14.09 (using Envy). Eventually I gave up and went back to Feisty, where I had never had these issues. No here's the kicker. I tried upgrading to kernel 2.6.23.9 on Feisty, keeping features like tickless kernel off, and using SLAB instead of SLUB. Wouldn't you know, it started locking up again. So here I am, back on 2.6.20 and so far, no locks.

I hope whatever 2.6.22 and 2.6.23 have that is causing lockups, is fixed in 2.6.24 as that is the version being proposed for Hardy, and I'd hope that an LTS release doesn't cause major lockups. BTW, I have tried both the 64 and 32 bit versions and they both have the same symptoms. I'm back on 32 bit for now.[/quote]

I also "upgraded" kernels to 2.6.23.9, except on Gutsy. And I still got the freezing. I also got freezing when the nvidia driver was off, and so was compiz. That made it seem to me that the kernel wasn't to blame.

[quote=Ben64]I've been having this problem as well. My computer freezes seemingly at random, the only thing in common with each freeze is Firefox. I've tried different versions of Firefox, the Nvidia driver, turning apm off and everything else I saw here. Just a few minutes ago I compiled a new kernel (2.6.23.9) to see if that will resolve it. I will post with my results in a few days or after my next lockup, whichever comes first.[/quote]

[quote=supernovus]A followup to my assumption that this was kernel related. I recently was testing openSUSE 10.3 on this computer, and it runs 2.6.22, and presto, the lockups occur in it as well.

It seems to happen more when Firefox is open, and more when using Nvidia drivers, but those do not seem to be "necessary" for this to happen (as the vmware driver also locks up, and I've had it lock up without loading Firefox).

So this is not specific to Ubuntu. It's a kernel issue.

I'm sticking with Feisty and it's non-locking 2.6.20 kernel until someone figures this out.[/quote]

Well a little over a day ago I decided to try installing the kernel from Feisty, so I booted up my laptop, which runs Feisty with no problems, and downloaded 2.6.20.15 from kernel.org.

I spent about 30 minutes going through the config, removing any unnecessary modules, and compiling in drivers that my computer will need. I've been running on 2.6.20.15 for about 29 hours now with no lockups. I have even been able to watch long videos on youtube, which has accelerated freezing on the other kernel versions.

And for reference, my computer specs:
AMD64 3200+
1GB ram
SIS motherboard
SATA drive for the OS
IDE for dvdrws and hard drives

Looks good so far, and once again, I will report again in a day, or lockup, whichever comes soonest.

---

### Post by AlienTechKilla on 2007-12-14
Just wanted to Bump cause I'm running into the same issue's with my machine. I have a amd 3800+ with 2gig pc3200 ram, dual 320gig sata hdd, nvidia 7300ls pci-e card with the built in realtek 97 audio. I know from reading this 35 page forum that the issue lies in the kernell or most likely the Nvidia driver. Symptoms include... the flash video complete lock up (cold restart needed) the animation freeze on compiz (the fire will just sit there untill I open a new window and of course the random firefox freeze(another cold boot issue)

I read in one the these posts that this issue was logged over a month ago with Ubuntu and also read someone's rant to Nvidia about fairness in driver development. (Why windows drivers work, but not this one for Ubuntu)

When I disabled the "new" nvidia driver under the "restricted drivers" and run the machine with the default Ubuntu video driver than there are NO Crashes

All I want for Christmas is this issue resolved. Humbuggingly  ATK

---

### Post by Jense on 2007-12-14
Same problem here, just random freezes, no indications in the kern.log or kdm log that I can find. I suspect though, it's the combination of xrandr and compiz. I tried another kernel, but this didn't help at all. Deactivated the proprietary driver for the broadcom 43xx, same thing.
I am at a loss, but if anybody has any idea I would be very gratefull. Not enough skill though to deactivate kernel modules myself  :(

System is: t41 thinkpad with 1 GB Ram, Ati M7500 and Broadcom Wireless (all the things that are not very well supported I am afraid)

Edit:
Weired thing is, all backround processes still work, Amarok keeps playing fine for example, but mouse and keyboard are gone for good. I wonder how often I can hard shut down this thing before my hd suffers to much.

---

### Post by Legu on 2007-12-14
> **thebinz said:**
> I am also getting nonstop freezes and lockups using my nvidia Geforce 7600 GT on Gutsy 64.
I have the nvidia 100.xxx drivers installed.

I was wondering if anyone else was getting a following problem.

Usually at random my screen will just flick and become all messed up like the created screenshot below. 
It's hard to explain but it is like the coordinates become all messed up.
The only way for me to fix the problem is to reboot.

I cannot function with my mouse when this happens. The actual appearance of the mouse cursor will be on the left hand side of the screen but i will be clicking somewhere on the right hand of the screen and visa versa. I have to guess where to click when saving open documents and shutting down. All windows and open apps become cut apart and virtually unusable.

Is anyone else experiencing this problem?
This happens completely at random and at least 3 times a day.

This is my normal Desktop:
[IMG]http://i64.photobucket.com/albums/h163/theillphil/Screenshot.png[/IMG]

This is when things mess up:
[IMG]http://i64.photobucket.com/albums/h163/theillphil/Screenshot_broke.png[/IMG]

Happens to me too. The difference is though, that I can function normally with mouse and keyboard. I don't have to reboot the computer, that weird thing just goes off when I rotate the virtual desktops few times. It doesn't happen often, and thus reboot isn't needed to fix the problem that bug doesn't really bother me.

I have 'nvidia' 100.xxx drivers and the card is GT 6600. I'm using 32-bit Gutsy (CPU is 64-bit though).

---

### Post by rasta_freak on 2007-12-14
Hi.

I'm using Kubuntu 7.10 on AMD X2 4600, 2G ram, nvidia 7600GT.

I  still don't know if it's driver, kernel or compiz problem. I run compiz with --indirect-rendering and --loose-bindings, and i see no slowdowns at all, but memory is still leaking - especially when using settings manager (ccsm) to disable & enable some plugins. So i made a little bash script to track compiz.real memory usage, and hope it may be usefull to someone else. You must have "kdebase-bin" installed (which you have if running KDE), and it will show mem usage in simple form.
Hope this issue will be resolved with new nvidia drivers (now using 169.04 and still it's leaking), or new kernel image - BTW i always compiled my own custom kernels on Linux, but right know i don't feel like customizing and resolving all that kernel<->ubuntu dependencies. I'd rather switch to Gentoo if i feel like doing so :)) I just expect from distro to be tested, well prepared and with, as few as possible, weak links.
And kubuntu is closest thing to this ('coz I'm .deb & KDE addict :)).

Anyway, as soon as compiz.real takes more that 100-150 MB, i restart it, and all is fine :)

---

### Post by Jense on 2007-12-14
thx to rasta_freak,

I would very much like to try this, but following some advice posted in this forum I would much appreciate it if somebody who actually understands what this script does could confirm it - no bad feelings I hope, it's just that for me this could mean anything.

Thx again

---

### Post by rasta_freak on 2007-12-14
:)

Feel free to view script for yourself and make sure it doesn't do any harm. It's not that complex. Or just throw it in a Trash :) 
Anyway, source is clean, and I was only hoping it might be usefull to someone else. But, of course, you're free to not believe me - no offense taken :)

---

### Post by DM was on fire! on 2007-12-14
I actually have that problem as well, and I'm running Ubuntu 6.06 32bit. 
The problem, however, I'm well aware of is my fail-at-life ATI Radeon 7000 video card.

It's either a hardware incompatibility issue, or your CPU usage is probably off the charts.
That's just about the only thing I could think of.

---

### Post by thebinz on 2007-12-14
> **Legu said:**
> Happens to me too. The difference is though, that I can function normally with mouse and keyboard. I don't have to reboot the computer, that weird thing just goes off when I rotate the virtual desktops few times. It doesn't happen often, and thus reboot isn't needed to fix the problem that bug doesn't really bother me.

I have 'nvidia' 100.xxx drivers and the card is GT 6600. I'm using 32-bit Gutsy (CPU is 64-bit though).

Well i am glad i'm not the only one that had seen this problem.
I had some kind of filesystem corruption earlier this week which crippled my system and so i was forced to reformat and reinstall everything.
I have Gutsy 64 running with the latest ENVY drivers installed.

Thankfully, I have not been running into the problem as often. When it does occur, a simple logout fixes the issue for me.

Thanks for the reply Legu!

---

### Post by AlienTechKilla on 2007-12-14
Well this wasn't an issue when I ran my 128mb NVidia 6200 so...... just wandering if anyone knows how I switch from a PCI-e Video card to a PCI Video Card. (I tried just plug and play and Ubuntu returned a "xconfig" error.)

---

### Post by lamadredelsapo on 2007-12-14
I'm going mad because my system freezes with epiphany, or Firefox or both or none of them. I mean it doesn't matter if I'm browsing the web or not, the computer will just freeze. Even with this lockups I've managed to install ATi's latest driver, but my PC is still getting those damn lockups.

---

### Post by Melcar on 2007-12-14
System froze again today while I was at work.  Here is an excerpt from my log giles that correspond to the freeze:

_**messages**_
> 
Dec 14 14:12:06 magicbox kernel: [13658.259602]  [run_workqueue+126/272] run_workqueue+0x7e/0x110
Dec 14 14:12:06 magicbox kernel: [13658.259605]  [worker_thread+0/304] worker_thread+0x0/0x130
Dec 14 14:12:06 magicbox kernel: [13658.259607]  [worker_thread+197/304] worker_thread+0xc5/0x130
Dec 14 14:12:06 magicbox kernel: [13658.259610]  [autoremove_wake_function+0/48] autoremove_wake_function+0x0/0x30
Dec 14 14:12:06 magicbox kernel: [13658.259613]  [worker_thread+0/304] worker_thread+0x0/0x130
Dec 14 14:12:06 magicbox kernel: [13658.259616]  [worker_thread+0/304] worker_thread+0x0/0x130
Dec 14 14:12:06 magicbox kernel: [13658.259619]  [kthread+75/128] kthread+0x4b/0x80
Dec 14 14:12:06 magicbox kernel: [13658.259622]  [child_rip+10/18] child_rip+0xa/0x12
Dec 14 14:12:06 magicbox kernel: [13658.259629]  [kthread+0/128] kthread+0x0/0x80
Dec 14 14:12:06 magicbox kernel: [13658.259632]  [child_rip+0/18] child_rip+0x0/0x12
Dec 14 14:12:06 magicbox kernel: [13658.259634] 
Dec 14 18:16:49 magicbox syslogd 1.4.1#21ubuntu3: restart.

_**kernel log**_
> 

Dec 14 14:12:06 magicbox kernel: [13658.259286] WARNING: at lib/kref.c:33 kref_get()
Dec 14 14:12:06 magicbox kernel: [13658.259291] 
Dec 14 14:12:06 magicbox kernel: [13658.259291] Call Trace:
Dec 14 14:12:06 magicbox kernel: [13658.259311]  [kref_get+53/64] kref_get+0x35/0x40
Dec 14 14:12:06 magicbox kernel: [13658.259325]  [_end+127693510/2130300312] :usbcore:usb_get_urb+0xe/0x20
Dec 14 14:12:06 magicbox kernel: [13658.259335]  [_end+127690696/2130300312] :usbcore:usb_hcd_submit_urb+0x180/0x930
Dec 14 14:12:06 magicbox kernel: [13658.259342]  [dma_alloc_pages+139/240] dma_alloc_pages+0x8b/0xf0
Dec 14 14:12:06 magicbox kernel: [13658.259345]  [dma_alloc_coherent+313/496] dma_alloc_coherent+0x139/0x1f0
Dec 14 14:12:06 magicbox kernel: [13658.259366]  [_end+132704029/2130300312] :ndiswrapper:wrap_submit_urb+0x85/0xd0
Dec 14 14:12:06 magicbox kernel: [13658.259382]  [_end+132705666/2130300312] :ndiswrapper:wrap_submit_irp+0x50a/0xb00
Dec 14 14:12:06 magicbox kernel: [13658.259396]  [_end+132704029/2130300312] :ndiswrapper:wrap_submit_urb+0x85/0xd0
Dec 14 14:12:06 magicbox kernel: [13658.259411]  [_end+132705666/2130300312] :ndiswrapper:wrap_submit_irp+0x50a/0xb00
Dec 14 14:12:06 magicbox kernel: [13658.259427]  [_end+132670110/2130300312] :ndiswrapper:pdoDispatchDeviceControl+0x16/0x40
Dec 14 14:12:06 magicbox kernel: [13658.259442]  [_end+132707327/2130300312] :ndiswrapper:win2lin2+0xe/0x11
Dec 14 14:12:06 magicbox kernel: [13658.259454]  [_end+132661147/2130300312] :ndiswrapper:IofCallDriver+0x33/0xc0
Dec 14 14:12:06 magicbox kernel: [13658.259468]  [_end+132661190/2130300312] :ndiswrapper:IofCallDriver+0x5e/0xc0
Dec 14 14:12:06 magicbox kernel: [13658.259471]  [_spin_lock_bh+9/32] _spin_lock_bh+0x9/0x20
Dec 14 14:12:06 magicbox kernel: [13658.259485]  [_end+132660456/2130300312] :ndiswrapper:IoAcquireCancelSpinLock+0x10/0x20
Dec 14 14:12:06 magicbox kernel: [13658.259498]  [_end+132661147/2130300312] :ndiswrapper:IofCallDriver+0x33/0xc0
Dec 14 14:12:06 magicbox kernel: [13658.259510]  [_end+132661147/2130300312] :ndiswrapper:IofCallDriver+0x33/0xc0
Dec 14 14:12:06 magicbox kernel: [13658.259525]  [_end+132707327/2130300312] :ndiswrapper:win2lin2+0xe/0x11
Dec 14 14:12:06 magicbox kernel: [13658.259530]  [find_busiest_group+555/2080] find_busiest_group+0x22b/0x820
Dec 14 14:12:06 magicbox kernel: [13658.259554]  [_end+132663087/2130300312] :ndiswrapper:IofCompleteRequest+0x47/0x1a0
Dec 14 14:12:06 magicbox kernel: [13658.259568]  [_end+132663155/2130300312] :ndiswrapper:IofCompleteRequest+0x8b/0x1a0
Dec 14 14:12:06 magicbox kernel: [13658.259584]  [_end+132702410/2130300312] :ndiswrapper:wrap_urb_complete_worker+0x42/0x130
Dec 14 14:12:06 magicbox kernel: [13658.259598]  [_end+132702344/2130300312] :ndiswrapper:wrap_urb_complete_worker+0x0/0x130
Dec 14 14:12:06 magicbox kernel: [13658.259602]  [run_workqueue+126/272] run_workqueue+0x7e/0x110
Dec 14 14:12:06 magicbox kernel: [13658.259605]  [worker_thread+0/304] worker_thread+0x0/0x130
Dec 14 14:12:06 magicbox kernel: [13658.259607]  [worker_thread+197/304] worker_thread+0xc5/0x130
Dec 14 14:12:06 magicbox kernel: [13658.259610]  [autoremove_wake_function+0/48] autoremove_wake_function+0x0/0x30
Dec 14 14:12:06 magicbox kernel: [13658.259613]  [worker_thread+0/304] worker_thread+0x0/0x130
Dec 14 14:12:06 magicbox kernel: [13658.259616]  [worker_thread+0/304] worker_thread+0x0/0x130
Dec 14 14:12:06 magicbox kernel: [13658.259619]  [kthread+75/128] kthread+0x4b/0x80
Dec 14 14:12:06 magicbox kernel: [13658.259622]  [child_rip+10/18] child_rip+0xa/0x12
Dec 14 14:12:06 magicbox kernel: [13658.259629]  [kthread+0/128] kthread+0x0/0x80
Dec 14 14:12:06 magicbox kernel: [13658.259632]  [child_rip+0/18] child_rip+0x0/0x12
Dec 14 14:12:06 magicbox kernel: [13658.259634] 

_**syslog**_
> 

Dec 14 14:12:06 magicbox kernel: [13658.259286] WARNING: at lib/kref.c:33 kref_get()
Dec 14 14:12:06 magicbox kernel: [13658.259291] 
Dec 14 14:12:06 magicbox kernel: [13658.259291] Call Trace:
Dec 14 14:12:06 magicbox kernel: [13658.259311]  [kref_get+53/64] kref_get+0x35/0x40
Dec 14 14:12:06 magicbox kernel: [13658.259325]  [_end+127693510/2130300312] :usbcore:usb_get_urb+0xe/0x20
Dec 14 14:12:06 magicbox kernel: [13658.259335]  [_end+127690696/2130300312] :usbcore:usb_hcd_submit_urb+0x180/0x930
Dec 14 14:12:06 magicbox kernel: [13658.259342]  [dma_alloc_pages+139/240] dma_alloc_pages+0x8b/0xf0
Dec 14 14:12:06 magicbox kernel: [13658.259345]  [dma_alloc_coherent+313/496] dma_alloc_coherent+0x139/0x1f0
Dec 14 14:12:06 magicbox kernel: [13658.259366]  [_end+132704029/2130300312] :ndiswrapper:wrap_submit_urb+0x85/0xd0
Dec 14 14:12:06 magicbox kernel: [13658.259382]  [_end+132705666/2130300312] :ndiswrapper:wrap_submit_irp+0x50a/0xb00
Dec 14 14:12:06 magicbox kernel: [13658.259396]  [_end+132704029/2130300312] :ndiswrapper:wrap_submit_urb+0x85/0xd0
Dec 14 14:12:06 magicbox kernel: [13658.259411]  [_end+132705666/2130300312] :ndiswrapper:wrap_submit_irp+0x50a/0xb00
Dec 14 14:12:06 magicbox kernel: [13658.259427]  [_end+132670110/2130300312] :ndiswrapper:pdoDispatchDeviceControl+0x16/0x40
Dec 14 14:12:06 magicbox kernel: [13658.259442]  [_end+132707327/2130300312] :ndiswrapper:win2lin2+0xe/0x11
Dec 14 14:12:06 magicbox kernel: [13658.259454]  [_end+132661147/2130300312] :ndiswrapper:IofCallDriver+0x33/0xc0
Dec 14 14:12:06 magicbox kernel: [13658.259468]  [_end+132661190/2130300312] :ndiswrapper:IofCallDriver+0x5e/0xc0
Dec 14 14:12:06 magicbox kernel: [13658.259471]  [_spin_lock_bh+9/32] _spin_lock_bh+0x9/0x20
Dec 14 14:12:06 magicbox kernel: [13658.259485]  [_end+132660456/2130300312] :ndiswrapper:IoAcquireCancelSpinLock+0x10/0x20
Dec 14 14:12:06 magicbox kernel: [13658.259498]  [_end+132661147/2130300312] :ndiswrapper:IofCallDriver+0x33/0xc0
Dec 14 14:12:06 magicbox kernel: [13658.259510]  [_end+132661147/2130300312] :ndiswrapper:IofCallDriver+0x33/0xc0
Dec 14 14:12:06 magicbox kernel: [13658.259525]  [_end+132707327/2130300312] :ndiswrapper:win2lin2+0xe/0x11
Dec 14 14:12:06 magicbox kernel: [13658.259530]  [find_busiest_group+555/2080] find_busiest_group+0x22b/0x820
Dec 14 14:12:06 magicbox kernel: [13658.259554]  [_end+132663087/2130300312] :ndiswrapper:IofCompleteRequest+0x47/0x1a0
Dec 14 14:12:06 magicbox kernel: [13658.259568]  [_end+132663155/2130300312] :ndiswrapper:IofCompleteRequest+0x8b/0x1a0
Dec 14 14:12:06 magicbox kernel: [13658.259584]  [_end+132702410/2130300312] :ndiswrapper:wrap_urb_complete_worker+0x42/0x130
Dec 14 14:12:06 magicbox kernel: [13658.259598]  [_end+132702344/2130300312] :ndiswrapper:wrap_urb_complete_worker+0x0/0x130
Dec 14 14:12:06 magicbox kernel: [13658.259602]  [run_workqueue+126/272] run_workqueue+0x7e/0x110
Dec 14 14:12:06 magicbox kernel: [13658.259605]  [worker_thread+0/304] worker_thread+0x0/0x130
Dec 14 14:12:06 magicbox kernel: [13658.259607]  [worker_thread+197/304] worker_thread+0xc5/0x130
Dec 14 14:12:06 magicbox kernel: [13658.259610]  [autoremove_wake_function+0/48] autoremove_wake_function+0x0/0x30
Dec 14 14:12:06 magicbox kernel: [13658.259613]  [worker_thread+0/304] worker_thread+0x0/0x130
Dec 14 14:12:06 magicbox kernel: [13658.259616]  [worker_thread+0/304] worker_thread+0x0/0x130
Dec 14 14:12:06 magicbox kernel: [13658.259619]  [kthread+75/128] kthread+0x4b/0x80
Dec 14 14:12:06 magicbox kernel: [13658.259622]  [child_rip+10/18] child_rip+0xa/0x12
Dec 14 14:12:06 magicbox kernel: [13658.259629]  [kthread+0/128] kthread+0x0/0x80
Dec 14 14:12:06 magicbox kernel: [13658.259632]  [child_rip+0/18] child_rip+0x0/0x12
Dec 14 14:12:06 magicbox kernel: [13658.259634] 

---

### Post by Thantos3000 on 2007-12-14
I used to have the lock ups but I solved it by disabling powrnode

---

### Post by otchie1 on 2007-12-15
> **ACLerok said:**
> When you guys get these crashes, do you have Firefox open?  

Yep.

It's so bad now that I've gone back to opera. With me, it's either a complete mouse & keyboard lockout or Ubuntu restarts.
Only ever happens when FF or Galeon run and even then it's erratic but I've always noticed it on a youTube or other flash site.

I sense too much integration in the Force

BTW,

Gutsy 32 bit latest with autoPatches
AMD 3800+ 64bit
2G DDR2 RAM
Asus M2N Sli delus
2x 7600GS PCIe in Sli format
PATA OS drive with SATA data/home drive

---

### Post by Melcar on 2007-12-15
Hmmm... most of us have AMDs.  I'm just throwing stuff out there.  Damn thing froze two times on me again, on completely random occasions.

---

### Post by lamadredelsapo on 2007-12-15
Even though I also have lockups with Firefox not running I think I started having them after installing all packages needed to use flashplugin-nonfree, these were lots of 32bit librarys. I'm going to remove them and see what happens.

---

### Post by lamadredelsapo on 2007-12-15
I think I've found the KILLING combination!. I've been working all morning with no lockups. After lunch I continued browsing with firefox with no apparent problems, but the computer hanged after using skype + firefox for around 5 minutes. It also happened with pidgin + firefox so i guess that must be the problem.

Does it make sense?

---

### Post by spockrock on 2007-12-15
Hi folks,

```

Dec 15 09:40:16 Chewie kernel: fan fuse apparmor commoncap

Dec 15 09:40:16 Chewie kernel: [295880.740000] CPU:    1

Dec 15 09:40:16 Chewie kernel: [295880.740000] EIP:    0060:[<00000004>]    Tainted: P       VLI

Dec 15 09:40:16 Chewie kernel: [295880.740000] EFLAGS: 00010286   (2.6.22-14-generic #1)

Dec 15 09:40:16 Chewie kernel: [295880.740000] EIP is at 0x4

Dec 15 09:40:16 Chewie kernel: [295880.740000] eax: 00000001   ebx: 0000099e   ecx: 080e8000   edx: 00000002

Dec 15 09:40:16 Chewie kernel: [295880.740000] esi: 080e8900   edi: 7fffffff   ebp: 00000001   esp: f1b27eec

Dec 15 09:40:16 Chewie kernel: [295880.740000] ds: 007b   es: 007b   fs: 00d8  gs: 0033  ss: 0068

Dec 15 09:40:16 Chewie kernel: [295880.740000] Process synergys (pid: 6449, ti=f1b26000 task=cf8134c0 task.ti=f1b26000)

Dec 15 09:40:16 Chewie kernel: [295880.740000] Stack: c0146fd5 00000001 7fffffff f1b27f88 00000000 cf8134c0 00000000 080e899c 

Dec 15 09:40:16 Chewie kernel: [295880.740000]        da5a48f4 cf8134c0 c013bdd0 f1b27f18 f1b27f18 00000000 00000000 bfdeec70 

Dec 15 09:40:16 Chewie kernel: [295880.740000]        da5a41c0 c02e74c7 c030fa20 0000541b ffffffda f6a5d780 c0140e36 f1b27f6c 

Dec 15 09:40:16 Chewie kernel: [295880.740000] Call Trace:

Dec 15 09:40:16 Chewie kernel: [295880.740000]  [do_futex+1669/3040] do_futex+0x685/0xbe0

Dec 15 09:40:16 Chewie kernel: [295880.740000]  [autoremove_wake_function+0/80] autoremove_wake_function+0x0/0x50

Dec 15 09:40:16 Chewie kernel: [295880.740000]  [unix_ioctl+151/208] unix_ioctl+0x97/0xd0

Dec 15 09:40:16 Chewie kernel: [295880.740000]  [getnstimeofday+54/208] getnstimeofday+0x36/0xd0

Dec 15 09:40:16 Chewie kernel: [295880.740000]  [ktime_get_ts+22/80] ktime_get_ts+0x16/0x50

Dec 15 09:40:16 Chewie kernel: [295880.740000]  [sys_futex+151/256] sys_futex+0x97/0x100

Dec 15 09:40:16 Chewie kernel: [295880.740000]  [syscall_call+7/11] syscall_call+0x7/0xb

Dec 15 09:40:16 Chewie kernel: [295880.740000]  =======================

Dec 15 09:40:16 Chewie kernel: [295880.740000] Code:  Bad EIP value.

Dec 15 09:40:16 Chewie kernel: [295880.740000] EIP: [<00000004>] 0x4 SS:ESP 0068:f1b27eec

Dec 15 10:42:54 Chewie syslogd 1.4.1#21ubuntu3: restart.
```

I got this this morning anyone know what this means??

---

### Post by khurrum1990 on 2007-12-15
Ubuntu 7.10 is horrible compared to Ubuntu 7.04.

---

### Post by Clintonostra on 2007-12-15
New to Linux & Ubuntu.

AMD Athlon(tm) 64 X2 Dual Core Processor 5200+
Operating System: Linux-x86_32 (Gutsy)
Kernel: 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux 
NVIDIA Driver Version: 169.04
Graphics Processor: GeForce 7300 LE
HDD: 2 sata 

Installed the Nvidiia  driver 169.04 obtained from [http://www.nvidia.com/object/linux_d...32_169.04.html](http://www.nvidia.com/object/linux_d...32_169.04.html)
The first time I booted it didn't work. Reinstalled it and let it compile the kernel and success. The only change was changing visual effects from extra to normal. At the moment, I don't know if this had any effect.
Prior to this had constant freeze ups and slow shut downs. This all happened when I used the Restricted Drivers.
The only remaining problem:  When I reinstalled Feisty on my second disk, received fdisk errors on the first. When I installed Gutsy on the first. disk, the same results on the second. Super boot disk wouldn't help. Whatever disk I install Ubuntu on, the other disk can't be booted to.
 Any help on this problem would be appreciated.

---

### Post by Clintonostra on 2007-12-15
[http://www.nvidia.com/object/linux_d...32_169.04.html](http://www.nvidia.com/object/linux_d...32_169.04.html)

Sorry Try this site. Also there is a readme that might be useful.

---

### Post by otchie1 on 2007-12-15
> **lamadredelsapo said:**
> I think I've found the KILLING combination!. I've been working all morning with no lockups. After lunch I continued browsing with firefox with no apparent problems, but the computer hanged after using skype + firefox for around 5 minutes. It also happened with pidgin + firefox so i guess that must be the problem.

Does it make sense?

Just had it with nothing but the desktop and Totem running. No browser, no flash, no desktop effects, just totem although this was a crash and not a reboot.

So I get a REBOOTING Gutsy with FF and a CRASHING Gutsy with at least multimedia files.

FFS, never had this grief with Slackware :guitar:

Oh, and no logs to show anything odd - seems to happen so fast nothing has time to know that it's dead. I'll see if I can get sysmon to record results to a file.......

---

### Post by Melcar on 2007-12-15
> **otchie1 said:**
> ...
Oh, and no logs to show anything odd - seems to happen so fast nothing has time to know that it's dead. I'll see if I can get sysmon to record results to a file.......


Yeah.  Is there a way to change the update interval of the logs, say to 1sec. (or even less)?

---

### Post by otchie1 on 2007-12-15
syslog has,

Dec 15 17:40:01 pisces /USR/SBIN/CRON[6635]: (news) CMD (test -f /usr/lib/news/batch/sendbatches && /usr/lib/news/batch/sendbatches)
Dec 15 17:45:01 pisces /USR/SBIN/CRON[6652]: (news) CMD (test -f /usr/lib/news/input/newsrun && /usr/lib/news/input/newsrun)
Dec 15 17:53:00 pisces syslogd 1.4.1#21ubuntu3: restart.
Dec 15 17:53:00 pisces kernel: Inspecting /boot/System.map-2.6.22-14-generic

which adds up to nothing.

---

### Post by otchie1 on 2007-12-15
> **Melcar said:**
> Yeah.  Is there a way to change the update interval of the logs, say to 1sec. (or even less)?

sudo gedit /var/log/syslog

should be a blow-by-blow of all that happens in your box

/etc/syslog.conf is the configuration file in the old style

---

### Post by rasta_freak on 2007-12-15
No time interval for logs, 'coz everything IS logged. Look in /var/log/* (all files), and look in ${HOME}/.xsession-errors (most probably it's in .xsession-errors).

---

### Post by PatrickMay16 on 2007-12-16
> **khurrum1990 said:**
> Ubuntu 7.10 is horrible compared to Ubuntu 7.04.

It's a shame to say it, but you've hit the nail on the head. The whole thing is full of glitches here and there (which weren't present in 7.04), plus more serious things like this lockup issue.

Hopefully 8.04 will be a big improvement.

---

### Post by khurrum1990 on 2007-12-16
Even Kubuntu 7.10 locks up sometimes if u have compiz fusion running and u change windows appearance, then go and play some multimedia files and finish its frozen, completely dead.

---

### Post by lamadredelsapo on 2007-12-16
I think I've managed to solve the lockups by disabling Cool-n-Quiet under the bios. I did it after reading this [http://linuxtechie.wordpress.com/2007/10/15/annoying-freezes-caused-by-nvidia-driver/]("http://linuxtechie.wordpress.com/2007/10/15/annoying-freezes-caused-by-nvidia-driver/")

---

### Post by fs3rp4 on 2007-12-16
I solve this with a BIOS upgrade. I had to install windows XP , because the Upgrade program  was only XP compatible, and upgraded BIOS version F.30 to F.3B. After this reinstalled Ubuntu and after 2 days using Nvidia proprietary driver and compiz there is no lockup.

I'm using a HP laptop Presario V6000 (V6210BR).

---

### Post by Ashrael on 2007-12-16
well like some before me, i have got strange lockups for minutes, with lots of hard disk activity, takes about 5 minutes. Works fine after that..

dmesg output:

> [ 2217.878864] 6 pages swap cached
[ 2217.878866] 0 pages dirty
[ 2217.878868] 0 pages writeback
[ 2217.878869] 18 pages mapped
[ 2217.878871] 2502 pages slab
[ 2217.878873] 1185 pages pagetables
[ 2217.879021] Out of memory: kill process 5511 (run-mozilla.sh) score 2751438 or a child
[ 2217.879032] Killed process 5515 (firefox-bin)
[ 2217.879220] mapping-daemon invoked oom-killer: gfp_mask=0x201d2, order=0, oomkilladj=0
[ 2217.879253]  [<c0161f65>] out_of_memory+0x185/0x1c0
[ 2217.879294]  [<c0163934>] __alloc_pages+0x2e4/0x340
[ 2217.879335]  [<c01653d9>] __do_page_cache_readahead+0x109/0x250
[ 2217.879342]  [<f899e250>] ext3_get_block+0x0/0x100 [ext3]
[ 2217.879380]  [<c02f2bcd>] io_schedule+0x1d/0x30
[ 2217.879393]  [<c02f2e7b>] __wait_on_bit_lock+0x5b/0x70
[ 2217.879397]  [<c015e800>] sync_page+0x0/0x50
[ 2217.879436]  [<c01610a5>] filemap_nopage+0x155/0x340
[ 2217.879475]  [<c016ccd8>] __handle_mm_fault+0x148/0xb00
[ 2217.879500]  [<c010320a>] __switch_to+0xaa/0x1d0
[ 2217.879545]  [<c02f5b36>] do_page_fault+0x126/0x690
[ 2217.879555]  [<c0140326>] do_gettimeofday+0x36/0x100
[ 2217.879595]  [<c02f5a10>] do_page_fault+0x0/0x690
[ 2217.879602]  [<c02f4292>] error_code+0x72/0x80
[ 2217.879628]  [<c02f0000>] clip_ioctl+0x500/0x510
[ 2217.879652]  =======================
[ 2217.879654] Mem-info:
[ 2217.879656] DMA per-cpu:
[ 2217.879659] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
[ 2217.879661] Normal per-cpu:
[ 2217.879664] CPU    0: Hot: hi:  186, btch:  31 usd:  43   Cold: hi:   62, btch:  15 usd:  14
[ 2217.879666] HighMem per-cpu:
[ 2217.879668] CPU    0: Hot: hi:   42, btch:   7 usd:   4   Cold: hi:   14, btch:   3 usd:   6
[ 2217.879672] Active:120696 inactive:126114 dirty:0 writeback:0 unstable:0
[ 2217.879673]  free:2989 slab:2502 mapped:18 pagetables:1185 bounce:0
[ 2217.879677] DMA free:4068kB min:68kB low:84kB high:100kB active:4164kB inactive:3912kB present:16256kB pages_scanned:389896 all_unreclaimable? yes
[ 2217.879680] lowmem_reserve[]: 0 873 1000
[ 2217.879686] Normal free:7768kB min:3744kB low:4680kB high:5616kB active:415924kB inactive:438004kB present:894080kB pages_scanned:1443766 all_unreclaimable? yes
[ 2217.879689] lowmem_reserve[]: 0 0 1015
[ 2217.879695] HighMem free:120kB min:128kB low:264kB high:400kB active:62696kB inactive:62540kB present:130036kB pages_scanned:204543 all_unreclaimable? yes
[ 2217.879697] lowmem_reserve[]: 0 0 0
[ 2217.879701] DMA: 3*4kB 1*8kB 1*16kB 0*32kB 1*64kB 1*128kB 1*256kB 1*512kB 1*1024kB 1*2048kB 0*4096kB = 4068kB
[ 2217.879712] Normal: 18*4kB 6*8kB 0*16kB 1*32kB 1*64kB 1*128kB 1*256kB 0*512kB 1*1024kB 1*2048kB 1*4096kB = 7768kB
[ 2217.879722] HighMem: 4*4kB 1*8kB 0*16kB 1*32kB 1*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 120kB
[ 2217.879734] Swap cache: add 590844, delete 590838, find 3373/10644, race 0+0
[ 2217.879736] Free swap  = 0kB
[ 2217.879738] Total swap = 2096472kB
[ 2217.879740] Free swap:            0kB
[ 2217.885456] 262140 pages of RAM
[ 2217.885459] 32764 pages of HIGHMEM
[ 2217.885461] 3251 reserved pages
[ 2217.885463] 2130 pages shared
[ 2217.885465] 6 pages swap cached
[ 2217.885466] 0 pages dirty
[ 2217.885468] 0 pages writeback
[ 2217.885469] 18 pages mapped
[ 2217.885471] 2502 pages slab
[ 2217.885473] 1185 pages pagetables
[ 2217.885746] dd invoked oom-killer: gfp_mask=0x200d2, order=0, oomkilladj=0
[ 2217.885777]  [<c0161f65>] out_of_memory+0x185/0x1c0
[ 2217.885818]  [<c0163934>] __alloc_pages+0x2e4/0x340
[ 2217.885860]  [<c0174591>] read_swap_cache_async+0x81/0xb0
[ 2217.885875]  [<c016aa16>] swapin_readahead+0x56/0x70
[ 2217.885895]  [<c016d3d3>] __handle_mm_fault+0x843/0xb00
[ 2217.885906]  [<c012d211>] current_fs_time+0x41/0x50
[ 2217.885963]  [<c02f5b36>] do_page_fault+0x126/0x690
[ 2217.885977]  [<c02f1f8a>] schedule+0x2ca/0x890
[ 2217.886013]  [<c02f5a10>] do_page_fault+0x0/0x690
[ 2217.886020]  [<c02f4292>] error_code+0x72/0x80
[ 2217.886051]  [<c01290d8>] do_syslog+0xe8/0x400
[ 2217.886061]  [<c02f1d95>] schedule+0xd5/0x890
[ 2217.886077]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[ 2217.886124]  [<c0180dbc>] vfs_read+0xbc/0x160
[ 2217.886134]  [<c01bcf50>] kmsg_read+0x0/0x50
[ 2217.886150]  [<c01812f1>] sys_read+0x41/0x70
[ 2217.886169]  [<c01041d2>] sysenter_past_esp+0x6b/0xa9
[ 2217.886218]  =======================
[ 2217.886220] Mem-info:
[ 2217.886222] DMA per-cpu:
[ 2217.886225] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
[ 2217.886227] Normal per-cpu:
[ 2217.886230] CPU    0: Hot: hi:  186, btch:  31 usd:  43   Cold: hi:   62, btch:  15 usd:  14
[ 2217.886232] HighMem per-cpu:
[ 2217.886235] CPU    0: Hot: hi:   42, btch:   7 usd:   4   Cold: hi:   14, btch:   3 usd:   6
[ 2217.886239] Active:120708 inactive:126102 dirty:0 writeback:0 unstable:0
[ 2217.886240]  free:2989 slab:2502 mapped:18 pagetables:1185 bounce:0
[ 2217.886244] DMA free:4068kB min:68kB low:84kB high:100kB active:4164kB inactive:3912kB present:16256kB pages_scanned:389896 all_unreclaimable? yes
[ 2217.886247] lowmem_reserve[]: 0 873 1000
[ 2217.886253] Normal free:7768kB min:3744kB low:4680kB high:5616kB active:415972kB inactive:437956kB present:894080kB pages_scanned:1443882 all_unreclaimable? yes
[ 2217.886256] lowmem_reserve[]: 0 0 1015
[ 2217.886262] HighMem free:120kB min:128kB low:264kB high:400kB active:62696kB inactive:62540kB present:130036kB pages_scanned:204543 all_unreclaimable? yes
[ 2217.886264] lowmem_reserve[]: 0 0 0
[ 2217.886268] DMA: 3*4kB 1*8kB 1*16kB 0*32kB 1*64kB 1*128kB 1*256kB 1*512kB 1*1024kB 1*2048kB 0*4096kB = 4068kB
[ 2217.886279] Normal: 18*4kB 6*8kB 0*16kB 1*32kB 1*64kB 1*128kB 1*256kB 0*512kB 1*1024kB 1*2048kB 1*4096kB = 7768kB
[ 2217.886290] HighMem: 4*4kB 1*8kB 0*16kB 1*32kB 1*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 120kB
[ 2217.886302] Swap cache: add 590844, delete 590838, find 3373/10644, race 0+0
[ 2217.886305] Free swap  = 0kB
[ 2217.886307] Total swap = 2096472kB
[ 2217.886310] Free swap:            0kB
[ 2217.892075] 262140 pages of RAM
[ 2217.892079] 32764 pages of HIGHMEM
[ 2217.892081] 3251 reserved pages
[ 2217.892083] 2130 pages shared
[ 2217.892085] 6 pages swap cached
[ 2217.892087] 0 pages dirty
[ 2217.892088] 0 pages writeback
[ 2217.892090] 18 pages mapped
[ 2217.892092] 2502 pages slab
[ 2217.892093] 1185 pages pagetables
[ 2217.892237] mapping-daemon invoked oom-killer: gfp_mask=0x201d2, order=0, oomkilladj=0
[ 2217.892268]  [<c0161f65>] out_of_memory+0x185/0x1c0
[ 2217.892308]  [<c0163934>] __alloc_pages+0x2e4/0x340
[ 2217.892351]  [<c01653d9>] __do_page_cache_readahead+0x109/0x250
[ 2217.892358]  [<f899e250>] ext3_get_block+0x0/0x100 [ext3]
[ 2217.892396]  [<c02f2bcd>] io_schedule+0x1d/0x30
[ 2217.892408]  [<c02f2e7b>] __wait_on_bit_lock+0x5b/0x70
[ 2217.892412]  [<c015e800>] sync_page+0x0/0x50
[ 2217.892451]  [<c01610a5>] filemap_nopage+0x155/0x340
[ 2217.892490]  [<c016ccd8>] __handle_mm_fault+0x148/0xb00
[ 2217.892515]  [<c010320a>] __switch_to+0xaa/0x1d0
[ 2217.892559]  [<c02f5b36>] do_page_fault+0x126/0x690
[ 2217.892570]  [<c0140326>] do_gettimeofday+0x36/0x100
[ 2217.892609]  [<c02f5a10>] do_page_fault+0x0/0x690
[ 2217.892615]  [<c02f4292>] error_code+0x72/0x80
[ 2217.892642]  [<c02f0000>] clip_ioctl+0x500/0x510
[ 2217.892665]  =======================
[ 2217.892667] Mem-info:
[ 2217.892669] DMA per-cpu:
[ 2217.892672] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
[ 2217.892675] Normal per-cpu:
[ 2217.892677] CPU    0: Hot: hi:  186, btch:  31 usd:  43   Cold: hi:   62, btch:  15 usd:  14
[ 2217.892679] HighMem per-cpu:
[ 2217.892682] CPU    0: Hot: hi:   42, btch:   7 usd:   4   Cold: hi:   14, btch:   3 usd:   6
[ 2217.892686] Active:120720 inactive:126090 dirty:0 writeback:0 unstable:0
[ 2217.892687]  free:2989 slab:2502 mapped:18 pagetables:1185 bounce:0
[ 2217.892692] DMA free:4068kB min:68kB low:84kB high:100kB active:4164kB inactive:3912kB present:16256kB pages_scanned:389896 all_unreclaimable? yes
[ 2217.892694] lowmem_reserve[]: 0 873 1000
[ 2217.892700] Normal free:7768kB min:3744kB low:4680kB high:5616kB active:416020kB inactive:437908kB present:894080kB pages_scanned:1443998 all_unreclaimable? yes
[ 2217.892703] lowmem_reserve[]: 0 0 1015
[ 2217.892709] HighMem free:120kB min:128kB low:264kB high:400kB active:62696kB inactive:62540kB present:130036kB pages_scanned:204543 all_unreclaimable? yes
[ 2217.892711] lowmem_reserve[]: 0 0 0
[ 2217.892715] DMA: 3*4kB 1*8kB 1*16kB 0*32kB 1*64kB 1*128kB 1*256kB 1*512kB 1*1024kB 1*2048kB 0*4096kB = 4068kB
[ 2217.892726] Normal: 18*4kB 6*8kB 0*16kB 1*32kB 1*64kB 1*128kB 1*256kB 0*512kB 1*1024kB 1*2048kB 1*4096kB = 7768kB
[ 2217.892736] HighMem: 4*4kB 1*8kB 0*16kB 1*32kB 1*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 120kB
[ 2217.892748] Swap cache: add 590844, delete 590838, find 3373/10644, race 0+0
[ 2217.892750] Free swap  = 0kB
[ 2217.892752] Total swap = 2096472kB
[ 2217.892753] Free swap:            0kB
[ 2217.898476] 262140 pages of RAM
[ 2217.898480] 32764 pages of HIGHMEM
[ 2217.898482] 3251 reserved pages
[ 2217.898484] 2130 pages shared
[ 2217.898485] 6 pages swap cached
[ 2217.898487] 0 pages dirty
[ 2217.898489] 0 pages writeback
[ 2217.898490] 18 pages mapped
[ 2217.898492] 2502 pages slab
[ 2217.898494] 1185 pages pagetables
[ 2217.898821] gconfd-2 invoked oom-killer: gfp_mask=0x201d2, order=0, oomkilladj=0
[ 2217.898853]  [<c0161f65>] out_of_memory+0x185/0x1c0
[ 2217.898893]  [<c0163934>] __alloc_pages+0x2e4/0x340
[ 2217.898936]  [<c01653d9>] __do_page_cache_readahead+0x109/0x250
[ 2217.898942]  [<f899e250>] ext3_get_block+0x0/0x100 [ext3]
[ 2217.898981]  [<c02f2bcd>] io_schedule+0x1d/0x30
[ 2217.898993]  [<c02f2e7b>] __wait_on_bit_lock+0x5b/0x70
[ 2217.898997]  [<c015e800>] sync_page+0x0/0x50
[ 2217.899011]  [<c015e7e3>] __lock_page+0x73/0x80
[ 2217.899038]  [<c01610a5>] filemap_nopage+0x155/0x340
[ 2217.899077]  [<c016ccd8>] __handle_mm_fault+0x148/0xb00
[ 2217.899095]  [<c012da61>] irq_exit+0x51/0x80
[ 2217.899099]  [<c0118735>] smp_apic_timer_interrupt+0x55/0x80
[ 2217.899151]  [<c02f5b36>] do_page_fault+0x126/0x690
[ 2217.899164]  [<c0140326>] do_gettimeofday+0x36/0x100
[ 2217.899201]  [<c02f5a10>] do_page_fault+0x0/0x690
[ 2217.899208]  [<c02f4292>] error_code+0x72/0x80
[ 2217.899234]  [<c02f0000>] clip_ioctl+0x500/0x510
[ 2217.899257]  =======================
[ 2217.899259] Mem-info:
[ 2217.899261] DMA per-cpu:
[ 2217.899264] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
[ 2217.899267] Normal per-cpu:
[ 2217.899269] CPU    0: Hot: hi:  186, btch:  31 usd:  43   Cold: hi:   62, btch:  15 usd:  14
[ 2217.899271] HighMem per-cpu:
[ 2217.899274] CPU    0: Hot: hi:   42, btch:   7 usd:   4   Cold: hi:   14, btch:   3 usd:   6
[ 2217.899278] Active:120720 inactive:126090 dirty:0 writeback:0 unstable:0
[ 2217.899280]  free:2989 slab:2502 mapped:18 pagetables:1185 bounce:0
[ 2217.899284] DMA free:4068kB min:68kB low:84kB high:100kB active:4164kB inactive:3912kB present:16256kB pages_scanned:389896 all_unreclaimable? yes
[ 2217.899287] lowmem_reserve[]: 0 873 1000
[ 2217.899293] Normal free:7768kB min:3744kB low:4680kB high:5616kB active:416020kB inactive:437908kB present:894080kB pages_scanned:1443998 all_unreclaimable? yes
[ 2217.899296] lowmem_reserve[]: 0 0 1015
[ 2217.899301] HighMem free:120kB min:128kB low:264kB high:400kB active:62696kB inactive:62540kB present:130036kB pages_scanned:204543 all_unreclaimable? yes
[ 2217.899304] lowmem_reserve[]: 0 0 0
[ 2217.899308] DMA: 3*4kB 1*8kB 1*16kB 0*32kB 1*64kB 1*128kB 1*256kB 1*512kB 1*1024kB 1*2048kB 0*4096kB = 4068kB
[ 2217.899318] Normal: 18*4kB 6*8kB 0*16kB 1*32kB 1*64kB 1*128kB 1*256kB 0*512kB 1*1024kB 1*2048kB 1*4096kB = 7768kB
[ 2217.899329] HighMem: 4*4kB 1*8kB 0*16kB 1*32kB 1*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 120kB
[ 2217.899341] Swap cache: add 590844, delete 590838, find 3373/10644, race 0+0
[ 2217.899343] Free swap  = 0kB
[ 2217.899345] Total swap = 2096472kB
[ 2217.899347] Free swap:            0kB
[ 2217.905075] 262140 pages of RAM
[ 2217.905079] 32764 pages of HIGHMEM
[ 2217.905081] 3251 reserved pages
[ 2217.905083] 2130 pages shared
[ 2217.905085] 6 pages swap cached
[ 2217.905086] 0 pages dirty
[ 2217.905088] 0 pages writeback
[ 2217.905090] 18 pages mapped
[ 2217.905091] 2502 pages slab
[ 2217.905093] 1185 pages pagetables
[ 2217.905235] dd invoked oom-killer: gfp_mask=0x200d2, order=0, oomkilladj=0
[ 2217.905267]  [<c0161f65>] out_of_memory+0x185/0x1c0
[ 2217.905307]  [<c0163934>] __alloc_pages+0x2e4/0x340
[ 2217.905349]  [<c0174591>] read_swap_cache_async+0x81/0xb0
[ 2217.905363]  [<c016aa16>] swapin_readahead+0x56/0x70
[ 2217.905391]  [<c016d3d3>] __handle_mm_fault+0x843/0xb00
[ 2217.905402]  [<c012d211>] current_fs_time+0x41/0x50
[ 2217.905459]  [<c02f5b36>] do_page_fault+0x126/0x690
[ 2217.905473]  [<c02f1f8a>] schedule+0x2ca/0x890
[ 2217.905509]  [<c02f5a10>] do_page_fault+0x0/0x690
[ 2217.905516]  [<c02f4292>] error_code+0x72/0x80
[ 2217.905547]  [<c01290d8>] do_syslog+0xe8/0x400
[ 2217.905558]  [<c02f1d95>] schedule+0xd5/0x890
[ 2217.905573]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[ 2217.905594]  [<c0180dbc>] vfs_read+0xbc/0x160
[ 2217.905603]  [<c01bcf50>] kmsg_read+0x0/0x50
[ 2217.905619]  [<c01812f1>] sys_read+0x41/0x70
[ 2217.905638]  [<c01041d2>] sysenter_past_esp+0x6b/0xa9
[ 2217.905687]  =======================
[ 2217.905689] Mem-info:
[ 2217.905691] DMA per-cpu:
[ 2217.905694] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
[ 2217.905696] Normal per-cpu:
[ 2217.905699] CPU    0: Hot: hi:  186, btch:  31 usd:  43   Cold: hi:   62, btch:  15 usd:  14
[ 2217.905701] HighMem per-cpu:
[ 2217.905704] CPU    0: Hot: hi:   42, btch:   7 usd:   4   Cold: hi:   14, btch:   3 usd:   6
[ 2217.905708] Active:120732 inactive:126078 dirty:0 writeback:0 unstable:0
[ 2217.905709]  free:2989 slab:2502 mapped:18 pagetables:1185 bounce:0
[ 2217.905713] DMA free:4068kB min:68kB low:84kB high:100kB active:4164kB inactive:3912kB present:16256kB pages_scanned:389896 all_unreclaimable? yes
[ 2217.905716] lowmem_reserve[]: 0 873 1000
[ 2217.905722] Normal free:7768kB min:3744kB low:4680kB high:5616kB active:416068kB inactive:437860kB present:894080kB pages_scanned:1444114 all_unreclaimable? yes
[ 2217.905725] lowmem_reserve[]: 0 0 1015
[ 2217.905730] HighMem free:120kB min:128kB low:264kB high:400kB active:62696kB inactive:62540kB present:130036kB pages_scanned:204543 all_unreclaimable? yes
[ 2217.905733] lowmem_reserve[]: 0 0 0
[ 2217.905737] DMA: 3*4kB 1*8kB 1*16kB 0*32kB 1*64kB 1*128kB 1*256kB 1*512kB 1*1024kB 1*2048kB 0*4096kB = 4068kB
[ 2217.905748] Normal: 18*4kB 6*8kB 0*16kB 1*32kB 1*64kB 1*128kB 1*256kB 0*512kB 1*1024kB 1*2048kB 1*4096kB = 7768kB
[ 2217.905758] HighMem: 4*4kB 1*8kB 0*16kB 1*32kB 1*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 120kB
[ 2217.905770] Swap cache: add 590844, delete 590838, find 3373/10644, race 0+0
[ 2217.905773] Free swap  = 0kB
[ 2217.905775] Total swap = 2096472kB
[ 2217.905778] Free swap:            0kB
[ 2217.911508] 262140 pages of RAM
[ 2217.911513] 32764 pages of HIGHMEM
[ 2217.911515] 3251 reserved pages
[ 2217.911517] 2130 pages shared
[ 2217.911518] 6 pages swap cached
[ 2217.911520] 0 pages dirty
[ 2217.911522] 0 pages writeback
[ 2217.911523] 18 pages mapped
[ 2217.911525] 2502 pages slab
[ 2217.911527] 1185 pages pagetables
[ 2217.911551] mapping-daemon invoked oom-killer: gfp_mask=0x201d2, order=0, oomkilladj=0
[ 2217.911583]  [<c0161f65>] out_of_memory+0x185/0x1c0
[ 2217.911624]  [<c0163934>] __alloc_pages+0x2e4/0x340
[ 2217.911666]  [<c01653d9>] __do_page_cache_readahead+0x109/0x250
[ 2217.911672]  [<f899e250>] ext3_get_block+0x0/0x100 [ext3]
[ 2217.911710]  [<c02f2bcd>] io_schedule+0x1d/0x30
[ 2217.911722]  [<c02f2e7b>] __wait_on_bit_lock+0x5b/0x70
[ 2217.911726]  [<c015e800>] sync_page+0x0/0x50
[ 2217.911765]  [<c01610a5>] filemap_nopage+0x155/0x340
[ 2217.911804]  [<c016ccd8>] __handle_mm_fault+0x148/0xb00
[ 2217.911829]  [<c010320a>] __switch_to+0xaa/0x1d0
[ 2217.911874]  [<c02f5b36>] do_page_fault+0x126/0x690
[ 2217.911885]  [<c0140326>] do_gettimeofday+0x36/0x100
[ 2217.911924]  [<c02f5a10>] do_page_fault+0x0/0x690
[ 2217.911931]  [<c02f4292>] error_code+0x72/0x80
[ 2217.911957]  [<c02f0000>] clip_ioctl+0x500/0x510
[ 2217.911981]  =======================
[ 2217.911983] Mem-info:
[ 2217.911985] DMA per-cpu:
[ 2217.911988] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
[ 2217.911990] Normal per-cpu:
[ 2217.911993] CPU    0: Hot: hi:  186, btch:  31 usd:  43   Cold: hi:   62, btch:  15 usd:  14
[ 2217.911995] HighMem per-cpu:
[ 2217.911998] CPU    0: Hot: hi:   42, btch:   7 usd:   4   Cold: hi:   14, btch:   3 usd:   6
[ 2217.912002] Active:120732 inactive:126078 dirty:0 writeback:0 unstable:0
[ 2217.912003]  free:2989 slab:2502 mapped:18 pagetables:1185 bounce:0
[ 2217.912007] DMA free:4068kB min:68kB low:84kB high:100kB active:4164kB inactive:3912kB present:16256kB pages_scanned:389896 all_unreclaimable? yes
[ 2217.912010] lowmem_reserve[]: 0 873 1000
[ 2217.912016] Normal free:7768kB min:3744kB low:4680kB high:5616kB active:416068kB inactive:437860kB present:894080kB pages_scanned:1444114 all_unreclaimable? yes
[ 2217.912019] lowmem_reserve[]: 0 0 1015
[ 2217.912025] HighMem free:120kB min:128kB low:264kB high:400kB active:62696kB inactive:62540kB present:130036kB pages_scanned:204543 all_unreclaimable? yes
[ 2217.912027] lowmem_reserve[]: 0 0 0
[ 2217.912031] DMA: 3*4kB 1*8kB 1*16kB 0*32kB 1*64kB 1*128kB 1*256kB 1*512kB 1*1024kB 1*2048kB 0*4096kB = 4068kB
[ 2217.912042] Normal: 18*4kB 6*8kB 0*16kB 1*32kB 1*64kB 1*128kB 1*256kB 0*512kB 1*1024kB 1*2048kB 1*4096kB = 7768kB
[ 2217.912052] HighMem: 4*4kB 1*8kB 0*16kB 1*32kB 1*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 120kB
[ 2217.912064] Swap cache: add 590844, delete 590838, find 3373/10644, race 0+0
[ 2217.912066] Free swap  = 0kB
[ 2217.912068] Total swap = 2096472kB
[ 2217.912070] Free swap:            0kB
[ 2217.917765] 262140 pages of RAM
[ 2217.917769] 32764 pages of HIGHMEM
[ 2217.917771] 3251 reserved pages
[ 2217.917772] 2130 pages shared
[ 2217.917774] 6 pages swap cached
[ 2217.917776] 0 pages dirty
[ 2217.917777] 0 pages writeback
[ 2217.917779] 18 pages mapped
[ 2217.917780] 2502 pages slab
[ 2217.917782] 1185 pages pagetables
[ 2217.918213] mapping-daemon invoked oom-killer: gfp_mask=0x201d2, order=0, oomkilladj=0
[ 2217.918246]  [<c0161f65>] out_of_memory+0x185/0x1c0
[ 2217.918286]  [<c0163934>] __alloc_pages+0x2e4/0x340
[ 2217.918328]  [<c01653d9>] __do_page_cache_readahead+0x109/0x250
[ 2217.918335]  [<f899e250>] ext3_get_block+0x0/0x100 [ext3]
[ 2217.918373]  [<c02f2bcd>] io_schedule+0x1d/0x30
[ 2217.918385]  [<c02f2e7b>] __wait_on_bit_lock+0x5b/0x70
[ 2217.918389]  [<c015e800>] sync_page+0x0/0x50
[ 2217.918428]  [<c01610a5>] filemap_nopage+0x155/0x340
[ 2217.918467]  [<c016ccd8>] __handle_mm_fault+0x148/0xb00
[ 2217.918492]  [<c010320a>] __switch_to+0xaa/0x1d0
[ 2217.918536]  [<c02f5b36>] do_page_fault+0x126/0x690
[ 2217.918547]  [<c0140326>] do_gettimeofday+0x36/0x100
[ 2217.918586]  [<c02f5a10>] do_page_fault+0x0/0x690
[ 2217.918593]  [<c02f4292>] error_code+0x72/0x80
[ 2217.918619]  [<c02f0000>] clip_ioctl+0x500/0x510
[ 2217.918643]  =======================
[ 2217.918645] Mem-info:
[ 2217.918647] DMA per-cpu:
[ 2217.918650] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
[ 2217.918652] Normal per-cpu:
[ 2217.918655] CPU    0: Hot: hi:  186, btch:  31 usd:  43   Cold: hi:   62, btch:  15 usd:  14
[ 2217.918657] HighMem per-cpu:
[ 2217.918659] CPU    0: Hot: hi:   42, btch:   7 usd:   4   Cold: hi:   14, btch:   3 usd:   6
[ 2217.918664] Active:120744 inactive:126066 dirty:0 writeback:0 unstable:0
[ 2217.918665]  free:2989 slab:2502 mapped:18 pagetables:1185 bounce:0
[ 2217.918669] DMA free:4068kB min:68kB low:84kB high:100kB active:4164kB inactive:3912kB present:16256kB pages_scanned:389896 all_unreclaimable? yes
[ 2217.918672] lowmem_reserve[]: 0 873 1000
[ 2217.918678] Normal free:7768kB min:3744kB low:4680kB high:5616kB active:416116kB inactive:437812kB present:894080kB pages_scanned:1444230 all_unreclaimable? yes
[ 2217.918681] lowmem_reserve[]: 0 0 1015
[ 2217.918687] HighMem free:120kB min:128kB low:264kB high:400kB active:62696kB inactive:62540kB present:130036kB pages_scanned:204607 all_unreclaimable? yes
[ 2217.918689] lowmem_reserve[]: 0 0 0
[ 2217.918693] DMA: 3*4kB 1*8kB 1*16kB 0*32kB 1*64kB 1*128kB 1*256kB 1*512kB 1*1024kB 1*2048kB 0*4096kB = 4068kB
[ 2217.918704] Normal: 18*4kB 6*8kB 0*16kB 1*32kB 1*64kB 1*128kB 1*256kB 0*512kB 1*1024kB 1*2048kB 1*4096kB = 7768kB
[ 2217.918714] HighMem: 4*4kB 1*8kB 0*16kB 1*32kB 1*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 120kB
[ 2217.918726] Swap cache: add 590844, delete 590838, find 3373/10644, race 0+0
[ 2217.918728] Free swap  = 0kB
[ 2217.918730] Total swap = 2096472kB
[ 2217.918732] Free swap:            0kB
[ 2217.924505] 262140 pages of RAM
[ 2217.924509] 32764 pages of HIGHMEM
[ 2217.924511] 3251 reserved pages
[ 2217.924513] 2130 pages shared
[ 2217.924515] 6 pages swap cached
[ 2217.924516] 0 pages dirty
[ 2217.924518] 0 pages writeback
[ 2217.924519] 18 pages mapped
[ 2217.924521] 2502 pages slab
[ 2217.924523] 1185 pages pagetables
[ 2217.924805] dd invoked oom-killer: gfp_mask=0x200d2, order=0, oomkilladj=0
[ 2217.924837]  [<c0161f65>] out_of_memory+0x185/0x1c0
[ 2217.924877]  [<c0163934>] __alloc_pages+0x2e4/0x340
[ 2217.924919]  [<c0174591>] read_swap_cache_async+0x81/0xb0
[ 2217.924934]  [<c016aa16>] swapin_readahead+0x56/0x70
[ 2217.924954]  [<c016d3d3>] __handle_mm_fault+0x843/0xb00
[ 2217.924966]  [<c012d211>] current_fs_time+0x41/0x50
[ 2217.925023]  [<c02f5b36>] do_page_fault+0x126/0x690
[ 2217.925036]  [<c02f1f8a>] schedule+0x2ca/0x890
[ 2217.925073]  [<c02f5a10>] do_page_fault+0x0/0x690
[ 2217.925079]  [<c02f4292>] error_code+0x72/0x80
[ 2217.925111]  [<c01290d8>] do_syslog+0xe8/0x400
[ 2217.925121]  [<c02f1d95>] schedule+0xd5/0x890
[ 2217.925137]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[ 2217.925158]  [<c0180dbc>] vfs_read+0xbc/0x160
[ 2217.925167]  [<c01bcf50>] kmsg_read+0x0/0x50
[ 2217.925184]  [<c01812f1>] sys_read+0x41/0x70
[ 2217.925202]  [<c01041d2>] sysenter_past_esp+0x6b/0xa9
[ 2217.925252]  =======================
[ 2217.925253] Mem-info:
[ 2217.925255] DMA per-cpu:
[ 2217.925258] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
[ 2217.925261] Normal per-cpu:
[ 2217.925263] CPU    0: Hot: hi:  186, btch:  31 usd:  43   Cold: hi:   62, btch:  15 usd:  14
[ 2217.925266] HighMem per-cpu:
[ 2217.925268] CPU    0: Hot: hi:   42, btch:   7 usd:   4   Cold: hi:   14, btch:   3 usd:   6
[ 2217.925272] Active:120756 inactive:126054 dirty:0 writeback:0 unstable:0
[ 2217.925273]  free:2989 slab:2502 mapped:18 pagetables:1185 bounce:0
[ 2217.925278] DMA free:4068kB min:68kB low:84kB high:100kB active:4164kB inactive:3912kB present:16256kB pages_scanned:389896 all_unreclaimable? yes
[ 2217.925280] lowmem_reserve[]: 0 873 1000
[ 2217.925287] Normal free:7768kB min:3744kB low:4680kB high:5616kB active:416164kB inactive:437764kB present:894080kB pages_scanned:1444346 all_unreclaimable? yes
[ 2217.925289] lowmem_reserve[]: 0 0 1015
[ 2217.925295] HighMem free:120kB min:128kB low:264kB high:400kB active:62696kB inactive:62540kB present:130036kB pages_scanned:204607 all_unreclaimable? yes
[ 2217.925298] lowmem_reserve[]: 0 0 0
[ 2217.925301] DMA: 3*4kB 1*8kB 1*16kB 0*32kB 1*64kB 1*128kB 1*256kB 1*512kB 1*1024kB 1*2048kB 0*4096kB = 4068kB
[ 2217.925312] Normal: 18*4kB 6*8kB 0*16kB 1*32kB 1*64kB 1*128kB 1*256kB 0*512kB 1*1024kB 1*2048kB 1*4096kB = 7768kB
[ 2217.925323] HighMem: 4*4kB 1*8kB 0*16kB 1*32kB 1*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 120kB
[ 2217.925334] Swap cache: add 590844, delete 590838, find 3373/10644, race 0+0
[ 2217.925338] Free swap  = 0kB
[ 2217.925340] Total swap = 2096472kB
[ 2217.925342] Free swap:            0kB
[ 2217.931072] 262140 pages of RAM
[ 2217.931077] 32764 pages of HIGHMEM
[ 2217.931079] 3251 reserved pages
[ 2217.931080] 2130 pages shared
[ 2217.931082] 6 pages swap cached
[ 2217.931084] 0 pages dirty
[ 2217.931085] 0 pages writeback
[ 2217.931087] 18 pages mapped
[ 2217.931088] 2502 pages slab
[ 2217.931090] 1185 pages pagetables
[ 2275.853510] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[ 2275.853583] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
[ 2275.853588] agpgart: SiS delay workaround: giving bridge time to recover.
[ 2275.867716] agpgart: Putting AGP V3 device at 0000:01:00.0 into 4x mode
[ 2275.867871] [drm] Loading R300 Microcode

would like this to be a thing of the past...

any ideas?

---

### Post by rasta_freak on 2007-12-16
Oops, you have the (in)famous OOM_KILLER in action :)
It kills processes when system is out of memory, which means you have a memory leak :)
Watch with some system tool memory usage of processes and you'll find out which one is it. Most likely it's compiz.real or X, and if you have nVidia drivers, well, welcome to the club :)
Just watch memory usage for some time, and tell us what's eating memory up.

EDIT:
watch resident memory usage (physical) (RSS), not virtual memory

---

### Post by Ashrael on 2007-12-16
I came to the same conclusion, i think it's firefox eating my mem....just started my system, ran firefox and came to this forum, have 3 tabs open... it's eating 70,9 megs of ram!...
So i  am looking forward to a sollution 

thanx for your reply.

---

### Post by rasta_freak on 2007-12-16
70.9MB ain't that much, really. My opera uses 60-70 MB, so it's "nominal" usage.
But, have another look at memory usage after half an hour, or hour. Anyway, it's best to have a look at these intervals, until you find something over 150-200MB. I used to have compiz.real take 400MB :) Now i use my little monitor that sits in system tray, and now i know when it might start leaking again - it usualy starts when i change compiz settings, or when i leave system idle for more that half an hour (what an irony :)

How much ram do you have, anyway ?

---

### Post by Melcar on 2007-12-16
Froze again, when checking my fricking email.  What makes this hard is the fact that it seems to happen for no reason.  Would post my log files, but for some reason nothing was recorded between the time I went to sleep (4am) and this morning that I opened up Thunderbird (8am).

---

### Post by Ashrael on 2007-12-16
sudo aptitude purge evms

this solved my problems....

found it here:

[http://www.devlib.org/forums/memory-leak-gutsy-t2506.html?](http://www.devlib.org/forums/memory-leak-gutsy-t2506.html?)

HTH.

---

### Post by rasta_freak on 2007-12-16
Don't say that twice :)
I never  ever had evms installed, and still, mem is leaking away (if i don't watch it).

---

### Post by Ben64 on 2007-12-16
```
$ uptime
 11:38:40 up 3 days, 12:53,  3 users,  load average: 0.05, 0.13, 0.11
```

Well it's been over 3 days, probably a record for Gutsy for me. At this point, I'd reccomend anyone that still hasn't solved this problem (although there really seems to be more than one problem in this thread) to "upgrade" to the 2.6.20.15 kernel.

You can use this guide to make an installable .deb package for the kernel.

[http://ubuntuforums.org/showthread.php?t=157560](http://ubuntuforums.org/showthread.php?t=157560)

Download the 2.6.20.15 from kernel.org.
Just ignore the kernel patching, and don't try to run 'make xconfig' as root.

---

### Post by Melcar on 2007-12-16
> **Ben64 said:**
> ```
$ uptime
 11:38:40 up 3 days, 12:53,  3 users,  load average: 0.05, 0.13, 0.11
```

Well it's been over 3 days, probably a record for Gutsy for me. At this point, I'd reccomend anyone that still hasn't solved this problem (although there really seems to be more than one problem in this thread) to "upgrade" to the 2.6.20.15 kernel.

You can use this guide to make an installable .deb package for the kernel.

[http://ubuntuforums.org/showthread.php?t=157560](http://ubuntuforums.org/showthread.php?t=157560)

Download the 2.6.20.15 from kernel.org.
Just ignore the kernel patching, and don't try to run 'make xconfig' as root.
Yeah.  Been trying all the new 2.6.22-23 kernels and I still have issues.  Downgrading is one of the few things I haven't tried.

---

### Post by lamadredelsapo on 2007-12-16
Well, I thought that it was solved but it wasn't, I still get those random system freezes so I've gone back to Win XP, at least until someone posts a proper solution.

---

### Post by khurrum1990 on 2007-12-16
Hey has anyone tried running fiesty on top of a gutsy kernel, then install the latest video drivers. Maybe that should be more stable than Gutsy itself.

---

### Post by Melcar on 2007-12-16
> **lamadredelsapo said:**
> Well, I thought that it was solved but it wasn't, I still get those random system freezes so I've gone back to Win XP, at least until someone posts a proper solution.

Thinking the same thing.  My XP is more stable than this.  I'm back to 32bit for the moment to see if that changes anything for me; anyone who tells you that there isn't a noticeable difference in speed between 32bit and 64bit is on something.  Anyways, no freezes up to now, but we shall see.

---

### Post by Ben64 on 2007-12-16
Well like I said a few posts ago, try the 2.6.20.15 kernel. Seems there is a problem with 2.6.22* and 2.6.23* that is causing this.

I got the idea from this:

[quote=supernovus]I tried upgrading to kernel 2.6.23.9 on Feisty, keeping features like tickless kernel off, and using SLAB instead of SLUB. Wouldn't you know, it started locking up again. So here I am, back on 2.6.20 and so far, no locks.[/quote]

and his follow-up

[quote=supernovus]I recently was testing openSUSE 10.3 on this computer, and it runs 2.6.22, and presto, the lockups occur in it as well.[/quote]

Before you go back to windows (ugh) at least try going to 2.6.20.15

---

### Post by Melcar on 2007-12-16
> **Ben64 said:**
> Well like I said a few posts ago, try the 2.6.20.15 kernel. Seems there is a problem with 2.6.22* and 2.6.23* that is causing this.

I got the idea from this:



and his follow-up



Before you go back to windows (ugh) at least try going to 2.6.20.15

I may just do that.  My question is if going down to that kernel messes up anything in Gutsy?

---

### Post by Ben64 on 2007-12-16
> **Melcar said:**
> I may just do that.  My question is if going down to that kernel messes up anything in Gutsy?

I have had no problems with any of my kernel changes on Gutsy as of yet, everything works the same, save for maybe the nvidia drivers, which needs a module based on your kernel, but you can use envy to install.

---

### Post by Ashrael on 2007-12-17
Well it seems i still have a leak somewhere, wish it was as simple as fixing a tire say...but when i use firefox my mem use still goes up,  20% goes to programs and a whopping 50% is used as cache! When my mem is full i get the dmesg output i posted before (#381)....Why isn't gutsy emptying my cache before it becomes a problem? I think it should start when using in total, say, 80% or so of my ram... It would be so much faster to do it while you still have some left :confused: 

During the typing of this message my cache has gone up 4%!

---

### Post by rasta_freak on 2007-12-17
Don't worry, all free memory is used as cache all the time, it's normal under linux. Mem is freed up as needed.

You can (and should, IMHO) adjust "swappiness", ie. tendency of kernel to use swap over RAM (cache) - default is 60 (percent) and it's way too much.

just do:

echo 25 | sudo tee /proc/sys/vm/swappiness

to make it 25. With that, swap will be used only if really needed.

To make it permanent, add line:
"echo 25 > /proc/sys/vm/swappiness" into /etc/rc.local (before "exit" call !)
Edit that file with "sudo <your_editor> <that_file>".

And to make a check, do:
cat /proc/sys/vm/swappiness

And about the leak, just wait for new nVidia driver:
[http://www.nvnews.net/vbulletin/showpost.php?p=1442530&postcount=15]("http://www.nvnews.net/vbulletin/showpost.php?p=1442530&postcount=15")

EDIT:
Or, better yet, to make that permanent, add:

vm.swappiness=25

into /etc/sysctl.conf file (with sudo <your editor>).

---

### Post by ka9qlq on 2007-12-17
> **Ben64 said:**
> [CODE]$
Well it's been over 3 days, probably a record for Gutsy for me. At this point, I'd reccomend anyone that still hasn't solved this problem (although there really seems to be more than one problem in this thread) to "upgrade" to the 2.6.20.15 kernel.

You can use this guide to make an installable .deb package for the kernel.


Why can't you just pull the deb off the feisty repositories? And the Nvidia driver. I forget where THAT'S stored. I dissabled powernowd to see if that fixes things. I can't believe the Ubuntu teem is just sitting on this and not giving an option to try a different kernel.

---

### Post by Melcar on 2007-12-17
Got feed up and did a clean install.  I'm currently using my own 2.6.22.15 kernel and no problems so far, but I think the fresh install has more to do than the different kernel.

---

### Post by fisuk on 2007-12-17
Changing back to kernel 2.6.21 did it for me, no more freezing.

---

### Post by Ben64 on 2007-12-18
Well.. it's been 5 days now on 2.6.20.15 and I can say with confidence that the 2.6.22 and 2.6.23 kernels are the(a?) cause of the lockups. I still am using the nv driver, and as such, do not have compiz enabled. After I hit day 7 I'll re-enable the nvidia driver and compiz and hope for another great 7 days.

[quote=ka9qlq]Why can't you just pull the deb off the feisty repositories? And the Nvidia driver. I forget where THAT'S stored. I dissabled powernowd to see if that fixes things. I can't believe the Ubuntu teem is just sitting on this and not giving an option to try a different kernel.[/quote]

Yes, I don't see a reason that the feisty .deb wouldn't work. However I figured while changing kernels, I might as well customize it for my system, to streamline the kernel and disable modules that I will never use.

---

### Post by rasta_freak on 2007-12-18
Try booting without "splash" on kernel command line (edit boot entry inside grub when comp is started), and you'll see which services fails, and which not. Unfortunatly, ubuntu needs lots of "junk" in your kernel to boot without any error (which you can't see if you boot with splash). It's best to temporarily disable gdm/kdm starting on boot to see it completly so you can scroll up (with shift-pgUp), but i'd suggest something like that only if you HATE even a single boot error (like me :)) But, if you're ok, and "everything" is working well, maybe don't bother.
And BTW, i too never had any problem with NV driver, so please try with nvidia driver if it's stable (and monitor memory usage to check against leaks).

---

### Post by Tenman on 2007-12-18
anyone do a step by step how to go back to this kernel?... forgive me I'm a noob... did a search and it started looking complicated for X64 very quickly...

---

### Post by rasta_freak on 2007-12-18
Only go back if your system is unstable even if using nv driver (NOT using nvidia restricted one).
Simplest method i think would be to go to:
[http://archive.ubuntu.com/ubuntu/pool/main/l/]("http://archive.ubuntu.com/ubuntu/pool/main/l/") and into linux-source-<your_option> directory (eg. linux-source-2.6.20), download 
linux-image-2.6.20-16-generic_2.6.20-16.32_i386.deb or amd64 version, and now, i don't know exactly dependencies for it, but I'd do:
sudo dpkg -i <that_file>, and when/if it says that it depends on something that isn't installed, download that package(s) from site, and do 
sudo dpkg -i <all_of_them>
(for example, sudo dpkg -i <kernel.deb> <some_modules.deb> <other_stuff.deb>). If it doesn't add new kernel entries in your boot menu, you'll have to do: sudo update-initramfs

---

### Post by lanzen on 2007-12-18
> **rasta_freak said:**
> And BTW, i too never had any problem with NV driver, so please try with nvidia driver if it's stable (and monitor memory usage to check against leaks).

Right, I also had no more freezes by using nv, but I've heard that some have. If it is a kernel bug why is nvidia 169.04 working for me ? Could it be that more bugs are concurring to create this effect?

---

### Post by ka9qlq on 2007-12-19
Well I got feed up and went back to feisty and after I put the nvidia drivers in I locked up. I got rid of powernowd and so far no lock ups on my Biostar nvidia amd x2 4800 2 gig ram. I'll let you know, if it does work I may go back to gusty.

---

### Post by Ben64 on 2007-12-19
> **rasta_freak said:**
> And BTW, i too never had any problem with NV driver, so please try with nvidia driver if it's stable (and monitor memory usage to check against leaks).

I was having the same crashes with the nv driver, just less often.

---

### Post by grinias on 2007-12-19
Today, a new update of kernel 22.14 arrived and (hopefully -- till now) the freezing problem (when acpi was enabled) has gone. My laptop 's specs:

Acer TM 4101
ATI X600 with restricted driver
Kubuntu 7.10

I had also the problem of "splash not shown during booting", which I also resolved 10min ago. 
So everything functions perfectly now.

See you all,
Elias

---

### Post by spockrock on 2007-12-19
I just updated the kernel lets see if everything is fixed.

---

### Post by thebinz on 2007-12-19
Please let us know.
I do not want to upgrade only to find out my problems get worse... seeing how they are already bad enough.

---

### Post by spockrock on 2007-12-20
OK I got a hardlock again, I am starting to think its not the kernel but pulseaudio thats causing the issue or bluetooth, are my only guesses now.

---

### Post by Wallace on 2007-12-20
On 32-bit the updated 2.6.22-16 kernel made no difference so I went back to 2.6.20-16 again. Don't know if that helps with the 64-bit version.

---

### Post by fisuk on 2007-12-20
Hrmh.. maybe i jumped the gun since i got a hardlock again. It got better though since I got freezes every night when using the stock kernel. Now it crashed under heavy load (3d rendering @ Q6600).
And it seems I managed to bork my network too...

---

### Post by Carl H on 2007-12-20
I don't have it quite so bad..... Fresh install on Gutsy with 4Gb of RAM fitted, and it consistantly crashed within ten seconds of X starting. After reading the comments on here about 4Gb RAM possibly being a factor, I decreased it to 2Gb and it has run fine so far.

---

### Post by fisuk on 2007-12-20
Well I'm going to test 2.6.24-rc5 now and put some load on it.

> **Carl H said:**
> I don't have it quite so bad..... Fresh install on Gutsy with 4Gb of RAM fitted, and it consistantly crashed within ten seconds of X starting. After reading the comments on here about 4Gb RAM possibly being a factor, I decreased it to 2Gb and it has run fine so far.

I need to test that too..

---

### Post by ka9qlq on 2007-12-20
Well after installing Feisty and locking up ONLY with powernowd on I switched back to Gusty and locked up before I disabled powernowd but after no hard locks though I had to restart x this morning before I had to hit the reset button.

---

### Post by Ben64 on 2007-12-21
Well, less than 24 hours after re-enabling nvidia and compiz, I had a freeze. It was fine with the nv driver though.

---

### Post by fisuk on 2007-12-21
2.6.24-rc5 kernel seems to work quite well. The stock kernel froze when the computer had been idle for a few hours, 2.6.21 worked well until I put some heavy load on it (3d rendering) and now 2.6.24-rc5 likes both idling and hard work :)
I'll keep you posted if it freezes again.

---

### Post by ka9qlq on 2007-12-21
I wish switching kernels was as easy as everyone says. Everytime I try I don't boot.

---

### Post by frankyboy4 on 2007-12-21
fisuk,

Are you running the 2.6.24rc5 kernel under Gutsy or Hardy ?

If under Gutsy how did you upgrade to that kernel ?

Did you compile by hand or use the kernel from Hardy's repositories ?

Could you post the steps you used to upgrade to that kernel ?

Thank You

Frankyboy4

---

### Post by fisuk on 2007-12-21
I'm running gutsy and I compiled the kernel from source.

Since I'm lazy I'll just point you to [http://ubuntuforums.org/showthread.php?t=157560](http://ubuntuforums.org/showthread.php?t=157560) ;)

 If you're not too familiar with tweaking the kernel settings, you probably shouldn't make too many modifications. Just make sure that support for the hardware you need is enabled.
Also if you have to use restricted modules, you're going to have to get those manually (nvidia & fglrx etc.)

---

### Post by williammanda on 2007-12-21
Nvidia ver 169.07 is avaiable. I haven't had any problems since the beta 169.04. Here is the link:
[http://www.nvnews.net/vbulletin/showthread.php?t=104706](http://www.nvnews.net/vbulletin/showthread.php?t=104706)
Thanks

---

### Post by lonejack on 2007-12-22
HI, KN9 ABIT, AMD AM2 DUAL CORE 2GB RAM, NVIDIA CHIPSET, NVIDIA GRAPHICS CARD, SAME PROBLEM MENTIONED. After a while desktop freeze. Switch off is the only solution.

---

### Post by Ron Byers on 2007-12-22
I am having the same problem.   After a while using Firefox and going to YouTube the darn thing just locks up. Only a restart will solve the problem.  The memory monitor indicates that there is some sort of extraordinary memory demand just before the lock. Those who have looked seem to find the same amount of memory being demanded repeatedly.  I only have one gig of ram,  but reading these pages the problem occurs regardless of the amount of memory.  I notice that Firefox and flash are often associated with crashes, yet people seem to think the problem is elsewhere.  I also notice that the NVIDIA Driver is often associated with the problem but many times it afflicts ATI cards as well. 

After 43 pages with lots of people still complaining,  am I the only one who thinks that this is a serious problem for Ubuntu? Is anybody at Ubuntu paying attention?

---

### Post by wppaas on 2007-12-22
My system is finally stable using the latest updates and the 169.04 or later nvidia driver.

The lockup I have on a cold boot only (and which I had on feisty too) is probably caused by my bios not initializing the graphics card correctly. A quick reset before booting Linux solves this. 

So I hope the new Nvidia driver fixes this for everyone else too.

cheers
WP

---

### Post by fisuk on 2007-12-22
> **Ron Byers said:**
>  I notice that Firefox and flash are often associated with crashes, yet people seem to think the problem is elsewhere.  I also notice that the NVIDIA Driver is often associated with the problem but many times it afflicts ATI cards as well. 

After 43 pages with lots of people still complaining,  am I the only one who thinks that this is a serious problem for Ubuntu? Is anybody at Ubuntu paying attention?

I guess this still only affects a minority of users. I have three other computers which don't suffer from this problem. Either case, this clearly is a bug and should be a top priority. 

There are bug reports about these freezes but they really lack common characteristics. For example, I don't use firefox and still got lockups. And as soon as I upgraded to the 2.6.24-rc5 kernel things began to work smoothly.

My guess is that there is something wrong with the cpu scaling. This is because:

 1) People seem to have worked around the problem by disabling powernowd. 
 2) When I used the stock kernel lockups occurred mainly when computer was idle
 3) Using an older kernel, version 2.6.21 worked fine in normal usage but locked up when I had an hour of 400% cpu usage.
 4) Using the latest kernel (well, not the latest one anymore) everything seems to work.

I haven't really paid attention on other peoples computer specs, but my primary desktop is a 'current generation' (Q6600, P5KSE, 4Gb ram, 8800gts) computer and it's the only one having these problems. All my other computers work just fine, and all of them run gutsy (they're slightly more dated, P4 2.4GHz, Core duo -laptop and Athlon-MP). 

I have also a few friends who run gutsy with almost exactly the same specs that I do but none of them have these problems.

Of course all of this is only guessing as I don't have any hard data to back this up and I have only ran 2.6.24 for a few days now so it's hard to say if the problem is fixed or not.

Or maybe everybody are having different problems but they manifest in the same way..?

---

### Post by Ron Byers on 2007-12-22
In all candor I upgraded to  the latest NVIDIA Driver and haven't had any problems since. I am running 2.6.22-14.47 on an x86_64.   Lets see if things are solved.

---

### Post by ka9qlq on 2007-12-22
When I installed the 169 Nvidia drivers I couldt'n get x going any tips? and what about glx?

I don't hard lock anymore but have to ctrl alt backspace every morning with x at 90% on cpu. The mouse moves but the kick start wont respond or anything else.

---

### Post by frankyboy4 on 2007-12-22
I have an ATI Video card and still have lockups.
My system is a new core 2 quad q6600 cpu in a gigabyte p35 motherboard with 1GB of ram. I am using a mix of IDE and SATA drives.
I am using teh amd64 installer.

I have tried to just update the kernel from the Hardy repositories and it eventually still locked up.

I am going to load fesity up to see how that runs. If it works without lcoking up I may try to do an upgrade to see if it will cotinue to work.

If not then I may try to hand compile a kernel, I still have question about getting and using the restricted ATI friver if I self compile the kernel.

I also saw huge amounts of memory being sucked up by Gutsy, but that stopped / went away when I upgraded to Hardy's kernel.

All in all it seems to be a bug that hard to track and or trace.

Frankyboy4

---

### Post by Ron Byers on 2007-12-22
Thirty nine thousand views and 430 posts isn't reflective of a minor problem.;)

Anyway since loading the latest video drivers and ubuntu updates I haven't had any additional problems.   Let's see how this goes for a few days.

---

### Post by mikeize on 2007-12-23
fwiw (not much i suppose!)

my lockups (which are happening less frequently lately-- dunno why), almost always occurred during light usage or idle times.  Firefox was often running, but not always.  I spend a lot of time playing Nexuiz, which really uses my processor, and presumably my vid card resources, but I NEVER have had a lockup during all my hours of gaming.
Like I said, probably not worth much since there are so few commonalities between peoples' setups and problems here, but anyway...

-mike

---

### Post by otchie1 on 2007-12-23
Ah, solved my problems.

Just added,

acpi=off

to /boot/grub/menu.lst

Never needed it under previous Ubuntu versions but I need it under Gutsy. Rock solid now for 2 days. Must be something turned on/off in new kernels.

---

### Post by ahuffman on 2007-12-23
I did the file deletion, and package removal and re-install of the nvidia-glx, and nvidia-kernel-source.

(older package)

This fixed it!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

Thanks everyone.


I just picked up this abit ab9 quad gt
4gb dual chan corsair
intel 2.ghz core 2 quad.

I was really upset upon this upgrade, with the lockups.
Now I can get back to moving all my data into place.
Edit
----------------------------------------------------------------------------------------
I'm trying the acpi=off grub boot option.  No lock up yet, and I've been trying to put some load on the system.

---

### Post by frankyboy4 on 2007-12-23
I've had the same lockup happen on a stock Fiesty install no restricted drivers present or anything else. 

I tried the acpi=off in the grub bootup parameters and still saw lockups.

The only clue I have so far is from fesity on the console and the error was "general protection fault: 0000 [1] SMP"

It seems to be pointing towards something with SMP ? or maybe the way the kernels were compiled ?

I will probabyl upgrade to Gutsy today and try to compile my own kernel from the link fisuk had pointed me to.

Frankyboy4

---

### Post by Bealer on 2007-12-23
Only one of the 4 computers I have suffer from this problem.

It's very difficult to pin point why though. It's a Pentium 4 with an ATI Radeon 9700 Pro graphics card.  It suffered freezes in Feisty.

So far, Ive tried disabling services such as powernowd and acpi, but without any luck. It has reduced how often it freezes though. Previously it was every 30mins or so. Now it could be 3 hours, it could be 9 hours. Very random. 

Definitely something that is frustrating. I've downloaded PCLOS 2007. Am pondering a switch, but I prefer the out of the box Gnome offering Ubuntu gives. 

I too, can't believe this hasn't been fixed. I know it's difficult as everyone has different setups, and doesn't report quite what they need, but still. It doesn't happen in other distro's for me, and freezing is something very major.

---

### Post by ka9qlq on 2007-12-23
It would help if the logs showed anything but they seem useless. Disabling the monitor powering off seems to help my semi lock up in x didn't have to restart x today.

---

### Post by spockrock on 2007-12-23
ok so I think I figured it out, my chipset fan on my board died....... I think that was causing my restarts, xorg restarts, and hardlocks.

---

### Post by ka9qlq on 2007-12-24
yep that's why my last pc died GPU fan died

---

### Post by Bowhunter on 2007-12-24
I have the same problem with Gutsy on two computers.  I finally got the system monitor up on mine to see Java killing the processor.  This needs to be fixed.  I have been keeping up with this topic, and have not seen anyone mention the Java.  Just thought I would throw that in with the mix to see if anyone else has seen it.

---

### Post by konungursvia on 2007-12-25
I have an ATI card, so it is not just an nvidia problem. System monitor reports some apps using the unbelievable sum of 17179869180.0 GB on several apps, including mixer_applet-2 and nautilus, as well as trashapplet and emerald. Usually it happens to Deluge too, but not right now.

Problem occurs more often since the kernel update about five days ago. It seems to happen most often when both firefox and Deluge are running, sometimes Amarok seems to help trigger the lockup.

---

### Post by fisuk on 2007-12-25
Status report: still no lockups using 2.6.24-rc5

> **konungursvia said:**
> I have an ATI card, so it is not just an nvidia problem. System monitor reports some apps using the unbelievable sum of 17179869180.0 GB on several apps, including mixer_applet-2 and nautilus, as well as trashapplet and emerald. Usually it happens to Deluge too, but not right now.

I think people at launchpad would like to know that piece of information... have you checked that it isn't a bug in gnome system monitor (assuming that you were talking about that particular software)?

---

### Post by cotcot on 2007-12-25
I am now half a day without freezes since i downgraded the nvidia driver to an earlier version (9643). Before i had a couple of freezes per hour.

---

### Post by yyyc186 on 2007-12-25
I think I have tracked the problem down to the SATA drives.  Let's be honest, support for SATA would have to improve a few notches before it rose to the level of pathetic.  You can only use them as regular drives, not as bound or RAID drives which defeats the entire purpose of using SATA.

I was trying the apic=off option in menu.lst which made things far worse.  I opened up Gedit and took out the option, then saved it while things were still quasi-functioning.  Once I tried to close the terminal window, everything locked up.

System would not reboot until I edited the startup options.  Low and behold, the apic=off option was still on.  While Gedit had successfully exited, the write did not successfully complete.

My best guess is that the bug in the SATA drivers is being aggravated by the video drivers.  I'm guessing this is a memory region problem like we used to have in the old DOS days.

---

### Post by Bokonon on 2007-12-25
Reinstalled my 7300 and the system locked up in less than 2 minutes.  I had almost forgotten what it was like.  I needed to get the 6800 out to make room for a new northbridge cooler, so the 6800 had to come out.

Solution for me:  Install nVidia 169.07 binary driver.  Once again, no lockups.  I will post again if I have any problems.

---

### Post by cotcot on 2007-12-26
> **yyyc186 said:**
> I think I have tracked the problem down to the SATA drives.  Let's be honest, support for SATA would have to improve a few notches before it rose to the level of pathetic.  You can only use them as regular drives, not as bound or RAID drives which defeats the entire purpose of using SATA.

I was trying the apic=off option in menu.lst which made things far worse.  I opened up Gedit and took out the option, then saved it while things were still quasi-functioning.  Once I tried to close the terminal window, everything locked up.

System would not reboot until I edited the startup options.  Low and behold, the apic=off option was still on.  While Gedit had successfully exited, the write did not successfully complete.

My best guess is that the bug in the SATA drivers is being aggravated by the video drivers.  I'm guessing this is a memory region problem like we used to have in the old DOS days.
Have you tried a older (or a more recent as previous poster experiences)   nvidia driver ? I also have  SATA drives and I am still fine since i downgraded the nvdia driver for my 7300GS.

---

### Post by jrickard on 2007-12-26
My lockups seem to coincide with duress, not idle periods.  For example, I could run x264 to process some largish .jpg images (1920x1080) into a time lapse movie.  I could hear the fans speed up as the processor work increased, and then virtually every time the system would freeze with the cursor frozen and everything would die - totally locked up.  No three finger salute  could save it.

We have received an upgrade on the kernel in the last week.  Suddenly, I'm processing massive amounts of video, in one case two videos simultaneously, with NO lockup.  All four processors totally maxed at 100% and still running.

So I think something good happened.  I'm just not sure what.  But I'm starting to smell a kernel fix.  Why don't they put out the word on these things?

Jack Rickard

---

### Post by yyyc186 on 2007-12-26
> **cotcot said:**
> Have you tried a older (or a more recent as previous poster experiences)   nvidia driver ? I also have  SATA drives and I am still fine since i downgraded the nvdia driver for my 7300GS.

I tried the reconfigure option, but haven't downgraded the driver.  Don't go blaming the video drivers out of hand.  This is a SATA driver bug.

I'm long enough in the tooth to remember 16-bit DOS, then 32-bit DOS extenders.  Everybody played games in the 384K memory region just above 640K.  Everybody blamed the video drivers for their problems.  Trouble was really that A000-C000 was actually reserved for video card use.  Since most low end cards only used a tiny portion of that ram, every other driver under the sun tried to use part of that range.  When the video card changed modes it would use a different segment of RAM.  Something else was always loaded there, so it got trashed.

You aren't "fixing" the problem by switching video drivers.  You are MASKING the problem.  The SATA drivers, either deliberately or accidentally, are using a piece of the video memory.  They get away with this as long as the video card is never in a mode where it needs to use that region of memory.  The real problem is the SATA drivers shouldn't be playing there at all.

I'll even wager 2 more grand gambles.

1)  Many of the machines experiencing the problem have a built in video function and an add in card.  When the driver is looking for a place to load it checks the on-board video requirements and doesn't bother looking for the add in card requirements.

2) Almost everybody and their brother has the BIOS setup wrong for their be-all-end-all graphics cards.  It's not their fault, the installation manual doesn't tell them the correct settings, assuming it even came with an installation manual.  The driver for the card, knowing the user couldn't possibly configure it correctly, resets these values softly during system boot when switching modes.  You never find out what the correct settings are, but your video works.  Too bad about whatever else happened to be loaded in that now used memory region.

---

### Post by ADloser on 2007-12-27
I'm having similar issues. Usually about a min or two after boot my laptop will just freeze, the caps-lock will light on and everything else will go dead, Usually I just turn the laptop off and on again and it'll work fine for a bit.

I run Vista and Ubuntu 7.10. Sometimes it freezes without me touching anything. Also, it freezes every time it goes to sleep.

---

### Post by hoarycripple on 2007-12-27
I've read through this entire thread now, and have seen only one other person posting stating that they are able to ssh into the offending system and reboot.  All others state that a hard reset is necessary.  My question now is, how many have actually tried to ssh into the system and reboot?

I was having problems with gutsy lockups, but it may be a different issue than the one here.  First, I will describe my specific problem (from another post):

> 
The specific problem I was having: X lockup when under load, Xorg taking up 100% CPU time. This would occur when trying to compile something in a terminal while in an X session. Transcoding/mplex'ing a video would *always* cause it to lock. The lockup caused one of the twinview screens to go blank and my monitor flashed the message "OUT OF RANGE." I would then lose the ability to switch to a VT, and I could not get a greeter back at all even after killing the Xorg process and killing XDM/GDM. The only remedy to getting back a GUI was to ssh in from another system and reboot. All non-GUI programs running over GNU screen (irssi/mutt/vim etc...) were still running without problems when I ssh'd in from the other computer.

Another type of lockup was when playing 3D games: quake3/urban terror would lock sometimes on exit, and would require the same remedy as above.

Now at first upgrading nvidia drivers seemed to help the problem, but I started getting lockups again. Same thing with newer kernels.  Finally, I found an error message with dmesg.  I can't remember the specific output now, and I don't have it saved, but will post it once I revert the system and test for lockups again.  

The problem for me was bad IRQ handling causing all the lockups, and the solution was to add:

```
acpi=off
```

to the default grub options.

So far, no lockups for several days.  This may be a different lockup than what others are experiencing, but it might not hurt to try this if you haven't already.

---

### Post by hoarycripple on 2007-12-27
> **yyyc186 said:**
> I think I have tracked the problem down to the SATA drives.  Let's be honest, support for SATA would have to improve a few notches before it rose to the level of pathetic.  You can only use them as regular drives, not as bound or RAID drives which defeats the entire purpose of using SATA.

I was trying the apic=off option in menu.lst which made things far worse.  I opened up Gedit and took out the option, then saved it while things were still quasi-functioning.  Once I tried to close the terminal window, everything locked up.

System would not reboot until I edited the startup options.  Low and behold, the apic=off option was still on.  While Gedit had successfully exited, the write did not successfully complete.

My best guess is that the bug in the SATA drivers is being aggravated by the video drivers.  I'm guessing this is a memory region problem like we used to have in the old DOS days.


apic=off would likely give you severe problems, but acpi=off (the correct option to pass at boot time, IMHO) should not.  I've been using this boot option for several days without a single X lockup.  Please clarify if you actually used apic=off or acpi=off. 

Thank you,

Hoarycripple

---

### Post by yyyc186 on 2007-12-27
My bad on the typo.  It was acpi=off.

Sorry for any confusion.

I do still firmly believe the root of this problem is the SATA drivers using a region of video memory which only gets used by video during certain operations.  As long as both aren't trying to use it at the same time, they get away with it.

---

### Post by hoarycripple on 2007-12-27
I think I should have waited another couple days before thinking acpi=off solved my problems.  It did not.  I am getting regular lockups when playing quake3/urban terror.  Same symptoms as before.  Only xorg becomes unresponsive, all other programs are running fine in the background (kernel is not unresponsive).  Requires me to ssh in and reboot.  

I'm with yyyc186 on this :  there might be a conflict in memory allocation.

---

### Post by yyyc186 on 2007-12-27
> **cotcot said:**
> Have you tried a older (or a more recent as previous poster experiences)   nvidia driver ? I also have  SATA drives and I am still fine since i downgraded the nvdia driver for my 7300GS.

OK, I'll bite.  What is the magic incantation to disable the X server so the NVIDIA file will install?  I've downloaded the file:

NVIDIA-Linux-x86_64-169.07-pkg2.run

The instructions say to issue sh NVIDIA-Linux-x86_64-169.07-pkg2.run to run it.  When I do that it tells me I must kill off the X server.  Apparently there is something missing in the instructions on the site for Ubuntu users.  I've tried playing with the runlevel to no avail.  X always starts up.  Issuing /etc/init.d/gdm stop only logs me out as does <CTRL><ALT><BACKSPACE>

On a different note:  I've gotten to watch a lot of reboot screens lately.  There is one message which comes up about my timer not being hooked to APIC.  A more interesting message appears at the bottom of the screen about direct mapping of addresses 0800-D000.

---

### Post by ed_x on 2007-12-28
I've added the ubuntu hardy repository to get kernel 2.6.24-2, but that didn't help. When I enable desktop effects, the first session will not crash for me. After rebooting, lockups start to appear. As mentioned before, this clearly is not an nvidia problem, since I'm using an ATI mobility radeon 9600 (IBM T42 laptop).

---

### Post by Ron Byers on 2007-12-28
I have tried most of the fixes suggested in this thread.  Temporary fixes at best but ultimately no joy. I really hoped that the kernel update last week would do the trick and for  a while it did.  

All I know is that the system is blowing up more often now than before.  

Ubuntu sells itself as being ready for the casual user.  Casual users will not tolerate the level of expertise demanded by kernel rewrites and many of the other fixes suggested.  If Ubuntu doesn't solve this problem and solve it fast it will lose me and millions of others. Too bad too, the software had such promise.  I know I wrote a post on a general computer site saying Ubuntu 7.10 was ready for prime time. Man was I wrong.

---

### Post by yyyc186 on 2007-12-28
> **Ron Byers said:**
> I have tried most of the fixes suggested in this thread.  Temporary fixes at best but ultimately no joy. I really hoped that the kernel update last week would do the trick and for  a while it did.  

All I know is that the system is blowing up more often now than before.  

Ubuntu sells itself as being ready for the casual user.  Casual users will not tolerate the level of expertise demanded by kernel rewrites and many of the other fixes suggested.  If Ubuntu doesn't solve this problem and solve it fast it will lose me and millions of others. Too bad too, the software had such promise.  I know I wrote a post on a general computer site saying Ubuntu 7.10 was ready for prime time. Man was I wrong.

The 32-bit version is ready.  The 64-bit version is as bad, if not worse, than any release of any version of Windows.  Since most versions of Windows are 32-bit, users can slide on over to the 32-bit Ubuntu, continue wasting 3/4 of their machine, and be happy.

This 64-bit sh*t is really getting old.  It is reminding me more and more of the days when I used to develop with Watcom and DOS extenders.  We would always have to find an "unused" region of memory in the range of A000-EFFF when they were paging things in and out of the lower 640K.  

Never seemed to fail, some driver would only need the region of memory we found "temporarily", so it wouldn't stake an identifiable claim to it.  They thought they were being polite, freeing up more RAM for others.  Bizarre and seemingly random crashes would happen.  You ended up having to find these problems with a hardware debugger or some form of "software ice" utility which would load itself as a "barrier" between programs and A000-EFFF.  It would then create a trace log every time something accessed or changed in that region.  Ugly thing to read through.  Didn't work if you happened to have disk caching turned on and the caching driver being loaded high was the culprit.


Personally, I would like to try the new NVIDIA driver, but I can't figure out the correct incantation of events in order to load it.  They specifically claim to have fixed a stability problem.  Even with runlevel set to 2, X seems to load with this distro.  Not normally a problem, but in this situation it is killer.

---

### Post by hoarycripple on 2007-12-28
> **yyyc186 said:**
> OK, I'll bite.  What is the magic incantation to disable the X server so the NVIDIA file will install?  I've downloaded the file:

NVIDIA-Linux-x86_64-169.07-pkg2.run

The instructions say to issue sh NVIDIA-Linux-x86_64-169.07-pkg2.run to run it.  When I do that it tells me I must kill off the X server.  Apparently there is something missing in the instructions on the site for Ubuntu users.  I've tried playing with the runlevel to no avail.  X always starts up.  Issuing /etc/init.d/gdm stop only logs me out as does <CTRL><ALT><BACKSPACE>

On a different note:  I've gotten to watch a lot of reboot screens lately.  There is one message which comes up about my timer not being hooked to APIC.  A more interesting message appears at the bottom of the screen about direct mapping of addresses 0800-D000.

Switch to a VT (virtual terminal) using CTRL-ALT-F1 (you have 6 VTs, from F1-F6 and you can start X sessions on F7-F12), then provide your login information.  Issue sudo /etc/init.d/gdm stop and you will be out of an X session.  At that point you should be able to install NVIDIA-Linux-x86_64-169.07-pkg2.run.  I personally removed nvidia kernel and glx packages prior to installing that package.

---

### Post by Carl H on 2007-12-28
> **Carl H said:**
> I don't have it quite so bad..... Fresh install on Gutsy with 4Gb of RAM fitted, and it consistantly crashed within ten seconds of X starting. After reading the comments on here about 4Gb RAM possibly being a factor, I decreased it to 2Gb and it has run fine so far.

I take that back. It's a lot better with less memory, but it's still not usable on a daily basis. The Gutsy machine has basically been gathering dust since it was built; I think I'll just stick with the Fiesty one for the time being.

---

### Post by yyyc186 on 2007-12-28
> **hoarycripple said:**
> Switch to a VT (virtual terminal) using CTRL-ALT-F1 (you have 6 VTs, from F1-F6 and you can start X sessions on F7-F12), then provide your login information.  Issue sudo /etc/init.d/gdm stop and you will be out of an X session.  At that point you should be able to install NVIDIA-Linux-x86_64-169.07-pkg2.run.  I personally removed nvidia kernel and glx packages prior to installing that package.

Thanks,

I only hosed it up a little bit.  I removed the restricted module generic and cannot re-install it without installing the nvidia stuff via synaptic.  No worries though, I'm not going to bother.  (I just got a little nuke happy when un-installing things).  

At 13:18 on 28-Dec-2007 I am up and running on the new NVIDIA driver, no restricted driver management software, and no messing with acpi in menu.lst (my machine won't boot without it)  This should "improve" my problem only because NVIDIA fixed a stability problem on SMP machines which mine is.  I will continue putting the finishing touches on "The Minimum You Need to Know About SOA" using XTERM and OpenOffice quite a bit.  BOINC running in background, and of course Evolution and the occasional Web surf.  We will see if the time between crashes is measured in seconds or days.

I don't think this is a complete solution and will have to restore my notebook to the 32-bit version since I need to do some Java programming for the last chapter.

No java plug-in for 64-bitAMD really bites!

---

### Post by hoarycripple on 2007-12-28
> **yyyc186 said:**
> Thanks,

I only hosed it up a little bit.  I removed the restricted module generic and cannot re-install it without installing the nvidia stuff via synaptic.  No worries though, I'm not going to bother.  (I just got a little nuke happy when un-installing things).  

At 13:18 on 28-Dec-2007 I am up and running on the new NVIDIA driver, no restricted driver management software, and no messing with acpi in menu.lst (my machine won't boot without it)  This should "improve" my problem only because NVIDIA fixed a stability problem on SMP machines which mine is.  I will continue putting the finishing touches on "The Minimum You Need to Know About SOA" using XTERM and OpenOffice quite a bit.  BOINC running in background, and of course Evolution and the occasional Web surf.  We will see if the time between crashes is measured in seconds or days.

I don't think this is a complete solution and will have to restore my notebook to the 32-bit version since I need to do some Java programming for the last chapter.

No java plug-in for 64-bitAMD really bites!

Let me know if you have any lockups with this setup.  As I said in another thread, using "xset s off" has helped me considerably.  I haven't had any lockups so far, even while playing quake3, which would give me lockups almost everytime I played.  If you do get a lockup using the new drivers, try using the "xset s off" option and see if that helps.  Maybe it was an Xorg problem all along....I really don't know.  My machine is SMP also, and now is apparently rock solid.  At last!  

I don't think I need the ACPI off option in grub anymore.  It probably has nothing to do with this and I'll try with ACPI upon boot and see how it goes.

about Java plugin...yeah, it does suck that there isn't a native 64bit plugin (you're talking about firefox I assume) but I have a 32bit firefox and java plugin installed for when I need it.

---

### Post by s_spiff on 2007-12-28
Well, till date I was thinking I was having a hardware issue and that Ubuntu was not at fault, but seems to be otherwise. I'm online my Windows HDD, and there doesn't seem to be any lock up with the Num Lock and Scroll Lock blinking. I'll again load up my system... let it heat up a bit, and check out. If it crashes on Windows too, then its a hardware issue, else I'm going back to Feisty.

---

### Post by yyyc186 on 2007-12-29
> **hoarycripple said:**
> Let me know if you have any lockups with this setup.  about Java plugin...yeah, it does suck that there isn't a native 64bit plugin (you're talking about firefox I assume) but I have a 32bit firefox and java plugin installed for when I need it.

It has been almost 24 hours, no lock ups.  Athalon X2.  Geoforce 7300, SATA

             total       used       free     shared    buffers     cached
Mem:       2062556    1698160     364396          0     296760     620600
-/+ buffers/cache:     780800    1281756
Swap:     19607324          0   19607324

I still think the bulk of this problem was a nasty memory overwrite in the region A000-D000.  The fact that NVIDIA makes both my SATA control and video means they could choose to fix it with which ever driver they wanted and who wants to admit there's a problem with your disk driver?

Here is a question to help the ATI victims sort out the problem.  Who is the maker of your SATA drivers?  System->Preferences->Hardware Information.  If it is ATI, you may have a similar situation on your hands.  If it is NVIDIA, then you may not get a solution.

The problem, as I have observed it, appears to be with a region of memory used to control caching.  I did not say cache contents, I said cache control.  It appears to get walked on, then writing to disk stops.  It also "appears"  that the "lock up" happens when you are in a situation where the OS needs something it wrote to disk after the walk.  Mostly this happens in a SWAP situation but can happen with anything that creates a small temporary file it needs in the next step.  Once disk writing shuts down, the needed blocks don't get written to disk.

Just my observations.  Mostly brought on by the changes I made to menu.lst just prior to a lock up which weren't there on the next boot even though minutes had went buy between exit of Gedit and the lockup.

---

### Post by Ron Byers on 2007-12-30
It  has been over 36 hours since my last lock up. The only thing I changed was  to severely limit java scripts in Firefox.  I guess that might have solved the problem, but I don't think it was that easy.  

In preferences I unchecked the following: 

Move or resize existing windows
    
    Unchecked  this option/preference to disable moving and resizing windows
          using scripts.

Raise or lower windows
    
    Unchecked this option/preference to make sure scripts cannot raise (bring
          to the front) or lower (send to the back) windows.
    
Disable or replace context menus
    
    Unchecked this option/preference to prevent web pages from disabling or
          changing the Firefox context menu.
    
Hide the status bar
  
    Unchecked this option/preference to force the status bar to be displayed in
          pop-up windows.
   
Change status bar text
    
    Unchecked this option/preference to disable changes to status bar text (such
          as displaying scrolling text messages or preventing the link address from
          being displayed while the mouse is over a link).

Actually the only one I unchecked was allowing scripts to raise or lower windows. All the others were unchecked already.  

I hope this helps, but I don't know how.

---

### Post by scradock on 2007-12-30
Ron,

Amazing!!!!! I did what you advised - just unchecked the first "enable" on the advanced dialog (all the others were blank anyway), and NO FREEZES!!!!! (so far!!!!!)

And yet, as you say, it CAN't be that simple can it? Otherwise, why did it freeze when Firefox wasn't even active?

So far - it works!!!

---

### Post by ka9qlq on 2007-12-30
Well I switched to Mepis for a test and powernowd killed it to once I uninstalled no lockups. I'm back on Kubuntu Gusty w/no powernowd and no lockups. I think it IS xorg doing something with powernowd to lock the system. I did see this error scroll by while swapping OS's

8254 timer not connected to io-apic 

Huuuuummmmmmmmmmmmmmm

---

### Post by ka9qlq on 2007-12-30
Just for kicks I installed cpudyn and made a couple menu entries to lock the cpu at max or min manually to see if running the cpu at 1 gig unless I deem other wise will lock things. Here's where I got the idea
[HTML]http://mnm.uib.es/gallir/cpudyn/faq.html[/HTML]

---

### Post by scradock on 2007-12-31
OK, it worked for a while (see 2/3 posts up), but then froze again while Firefox was opening a window. I'll try turning off powernowd.....

---

### Post by fisuk on 2008-01-01
Status update: still no crashes using kernel version 2.6.24-rc5.

---

### Post by Ron Byers on 2008-01-01
fisuk 

I hope  you have found your solution, but updating the kernel is just not something most casual users want or can do.  

It is much better since I restricted java scripts, but it isn't perfect.   I still get an occasional lockup. Before killing java scripts I could barely use the os. Now it is tolerable. Sort of like Windows ME. 

I am coming to the conclusion that this is a memory allocation/reallocation problem.  I notice that on some occasions when I close Firefox, some memory doesn't get reallocated and I receive an error message indicating that Firefox is still running.  I think some program is  carelessly allocating memory to the wrong place. I really wonder about Java and Flash.   Most of my problems have been associated in some way with Java.  I wonder if the wrapper is involved?

---

### Post by fisuk on 2008-01-01
> **Ron Byers said:**
> 
I hope  you have found your solution, but updating the kernel is just not something most casual users want or can do.  


You are correct in the case of manual compilation. Of course kernel update via apt is something most users would want to do. Whether it would be patch for the stock kernel or an update to a newer kernel.
 That's why it's imperative that there are people who are willing to test if the problem really lies within the kernel or not. Of course there might be something in the newer kernel that just masks the real problem. But for the developers every bit of information is valuable. 

> **Ron Byers said:**
> 
Most of my problems have been associated in some way with Java.  I wonder if the wrapper is involved?

You mean nspluginwrapper? Well.. that probably is the case since I get messages to syslog about npviewer.bin segfaulting. This is something I did not get using the stock kernel. If I interpret this correctly, there is a bug in both the kernel (error handling) and the wrapper (memory allocation).

---

### Post by Ron Byers on 2008-01-01
[I]"You mean nspluginwrapper? Well.. that probably is the case since I get messages to syslog about npviewer.bin segfaulting. This is something I did not get using the stock kernel. If I interpret this correctly, there is a bug in both the kernel (error handling) and the wrapper (memory allocation)." 
[/I]
Now we are getting somewhere.: ;

I am glad you are testing. Now if we can get somebody in authority to pay attention.

---

### Post by ka9qlq on 2008-01-01
well no lockups sofar on cpudun an MANUALLY changing speeds. Haven't tried auto yet.

---

### Post by fisuk on 2008-01-01
Well this is all pure speculation. I did post my findings to the bug report @ launchpad but it would seem just that the repository version of nspluginwrapper doesn't like the newer kernel. I'll see if I can compile it by hand too if it makes any difference.. (and it probably will)

---

### Post by Udo555 on 2008-01-01
Maybe this can be useful for somebody:

**My setup:**
MB: MSI K8N Neo2, Bios version MS-7025 VER:1, chipset NFORCE3-250
AMD Opteron(tm) Processor 144, 512 MB Ram
Nvidia GeForce4 MX 440
now 32 bit gutsy kernel 2.6.22-14-generic

After clean install of Gutsy I got many random freezes, lock-ups. 
Sometimes the USB mouse was frozen, then the desktop and keybord except for the mouse, etc.
The frezes were unacceptably frequent, driving me crazy. 

**I have tested many suggestions from these forums, without success, such as:**
1. boot otions like acpi=off noacpi noapic nolapic irqpoll and many combinations thereof
2. different kernel versions, gutsy kernel, feisty kernel, self compiled vanilla kernel 2.6.23
3. after mouse freeze, trying unloading and loading the ohci_hcd module
4. X drivers proprietary nvidia from the distro, self compiled nvidia driver, also nv driver
5. tips about removing powernowd and changing scripts for the powernowd
6. many different bios settings, Cool-n-Quiet disabling, etc
7. compiz on and off
8. linux or nVidia AGP drivers
9. a lot of other things that I already forgot

**The success story:**
The suggestion from the forum to update the bios was the last option I wanted to try out. I do not like doing such things...MSI website says that the BIOS upgrades only adds new processor IDs. I assumed that it will not help my problems...
Anyway, after downloading the latest BIOS from MSI website and upgrading the BIOS, all of the freezing problems are away!!!! I am again happy with Ubuntu!!!

I suppose, the problem is related to ACPI and the interrupt handling.

PS. Please, Ubuntu/Linux gurus try to find a solution for such problems, it is a complete disaster when linux is freezing more often then Win95 used to some years ago. Even if it is a harware problem, it would be very useful to indicate the user the possible cause of the freezing problems and also the possible fix (such as the Bios upgrade in this case).

Thanks all for their help.

---

### Post by s_spiff on 2008-01-01
> **Ron Byers said:**
> It  has been over 36 hours since my last lock up. The only thing I changed was  to severely limit java scripts in Firefox.  I guess that might have solved the problem, but I don't think it was that easy.  

In preferences I unchecked the following: 

Move or resize existing windows
    
    Unchecked  this option/preference to disable moving and resizing windows
          using scripts.

Raise or lower windows
    
    Unchecked this option/preference to make sure scripts cannot raise (bring
          to the front) or lower (send to the back) windows.
    
Disable or replace context menus
    
    Unchecked this option/preference to prevent web pages from disabling or
          changing the Firefox context menu.
    
Hide the status bar
  
    Unchecked this option/preference to force the status bar to be displayed in
          pop-up windows.
   
Change status bar text
    
    Unchecked this option/preference to disable changes to status bar text (such
          as displaying scrolling text messages or preventing the link address from
          being displayed while the mouse is over a link).

Actually the only one I unchecked was allowing scripts to raise or lower windows. All the others were unchecked already.  

I hope this helps, but I don't know how.

Tried this. Worked for a while ( took a longer while to freeze ) but froze nonetheless.  Any other suggestions apart from kernel changes?

---

### Post by Ron Byers on 2008-01-01
So far the only thing that seems to work is upgrading the kernel.

fisuk has a theory that makes a lot of sense. We are dealing with two bugs. The first is a bug in  the kernel involving error handling which is why the kernel upgrade is successful and the second is a bug in the nspluginwrapper involving memory allocation which is why the crashes involve flash and java so often. It also explains why restricting java scripts sorta works.  A lot of those scripts picked up on the Internet run the system straight into the memory allocation problem.  Better error handling means the memory allocation problem is dealt with without crashing the system. The wrapper bug still exists,  but with better error handling we just don't notice.  Remember this problem seems to be limited to the 64 bit  version of Ubuntu which gives support to fisuk's theory.  The 32 bit version is more mature.  I am hoping for an early bug fix involving the nspluginwrapper.  I don't think a manual upgrade of the kernel is within the technical capabilities of most people using Ubuntu.

---

### Post by mikeize on 2008-01-01
> **Ron Byers said:**
>  Remember this problem seems to be limited to the 64 bit  version of Ubuntu which gives support to fisuk's theory.  The 32 bit version is more mature. .

Not true.  Myself and many other posters to this thread have the same lockups running the 32 bit version.  Just want to make sure that stays clear.

-mike

---

### Post by eligos on 2008-01-02
> **mikeize said:**
> Not true.  Myself and many other posters to this thread have the same lockups running the 32 bit version.  Just want to make sure that stays clear.

-mike

That's right, i've install the 32 bit ubuntu and the crashes still are there :confused:

---

### Post by ed_x on 2008-01-02
I've tried kernel 2.6.22 (gutsy) and 2.6.24 (hardy) so far, both causing lockups (on an ATI 9600 mobility). Now I'm trying 2.6.20 from feisty, which runs fine so far (used to freeze within several minutes). Let's hope for the best

---

### Post by Roddles on 2008-01-02
I have a DELL XPS m1710 running Gutsy 64 bit.

Firefox appears to be the cause of the lockups on my system, as it so far has only locked up while using firefox. 

After reading through the posts on this, I have uninstalled the ndispluginwrapper, sun-java and the proprietary flash-plugin from my system (Hey - can live without flash and Java for a while so long as my system is stable and I can work). I use this computer all day so it has to be stable.

Will post back here very soon to let you know either way if it works or doesn't with the lockups. 

It already locked up on me twice this morning before removing those items listed above - so will see how I go now.

The best way to get the lockup to happen is to go surfing :)

Cheers

Rod.

---

### Post by Roddles on 2008-01-02
ok - well scrap that - after 45 mins, system locked up again.

Also - as soon as I rebooted, connected to the net and started firefox, got half way through loading this page and ... system locked up again.

I have locked my CPU frequency to Performance to stop the cpu scaling from occuring to see if that makes things a bit more stable, but i am going to try and avoid using firefox and the internet for the rest of the day so I can get some work done without hopefully the fear of a lockup.

Frustration levels now at 110% and rising. Wont go back to the doze, but, may have to downgrade to something a bit more stable like Kubuntu Dapper until this crap is resolved.

How can we be expected to encourage other to take up the wonderful world of Linux with S**t like this happening, and from what it appears more and more often. Its getting worse with each new release.

Speed and Stability is much more important than pretty shiny new things. Maybe that should be the focus over trying to cram more and more new features into the latest release. 

anyway - will see how this goes with the CPU locked at full speed.

---

### Post by Roddles on 2008-01-03
ok - may have found the source of my lockups.

the last crash finally gave me some log info, and i have to apologise to the ubuntu developers, it was not their fault.

it was the conexant modem driver. i managed to get some log info out from a terminal window and save it before the system completely froze.

I uninstalled the conexant modem driver and the system has not crashed since. 

Now - to see if a standard network connection (no modem) with firefox locks up at all.

So big apology to Ubuntu developers - not your fault.

Have been working without an issue for over 5 hours now since uinstalling the conexant modem driver.

Contents of Log from last crash:

rodney-laptop:~$ tail -n 100 /var/log/syslog
Jan  3 14:11:07 rodney-laptop kernel: [  328.922854] cnxthsf_OsEventWaitTime(ffff81007c123200/HDA CodecUnsolicitedmessage, 40): returning OSEVENT_WAIT_TIMEOUT
Jan  3 14:11:07 rodney-laptop vmnet-dhcpd: Internet Software Consortium DHCP Server 2.0
Jan  3 14:11:07 rodney-laptop vmnet-dhcpd: Copyright 1995, 1996, 1997, 1998, 1999 The Internet Software Consortium.
Jan  3 14:11:07 rodney-laptop vmnet-dhcpd: All rights reserved.
Jan  3 14:11:07 rodney-laptop vmnet-dhcpd: 
Jan  3 14:11:07 rodney-laptop vmnet-dhcpd: Please contribute if you find this software useful.
Jan  3 14:11:07 rodney-laptop vmnet-dhcpd: For info, please visit [http://www.isc.org/dhcp-contrib.html](http://www.isc.org/dhcp-contrib.html)
Jan  3 14:11:07 rodney-laptop vmnet-dhcpd: 
Jan  3 14:11:07 rodney-laptop avahi-daemon[5320]: Joining mDNS multicast group on interface vmnet1.IPv4 with address 172.16.152.1.
Jan  3 14:11:07 rodney-laptop avahi-daemon[5320]: New relevant interface vmnet1.IPv4 for mDNS.
Jan  3 14:11:07 rodney-laptop avahi-daemon[5320]: Registering new address record for 172.16.152.1 on vmnet1.IPv4.
Jan  3 14:11:07 rodney-laptop avahi-daemon[5320]: Withdrawing address record for 172.16.152.1 on vmnet1.
Jan  3 14:11:07 rodney-laptop avahi-daemon[5320]: Leaving mDNS multicast group on interface vmnet1.IPv4 with address 172.16.152.1.
Jan  3 14:11:07 rodney-laptop avahi-daemon[5320]: Interface vmnet1.IPv4 no longer relevant for mDNS.
Jan  3 14:11:07 rodney-laptop avahi-daemon[5320]: Joining mDNS multicast group on interface vmnet1.IPv4 with address 172.16.152.1.
Jan  3 14:11:07 rodney-laptop avahi-daemon[5320]: New relevant interface vmnet1.IPv4 for mDNS.
Jan  3 14:11:07 rodney-laptop avahi-daemon[5320]: Registering new address record for 172.16.152.1 on vmnet1.IPv4.
Jan  3 14:11:07 rodney-laptop vmnet-dhcpd: Configured subnet: 172.16.152.0
Jan  3 14:11:07 rodney-laptop vmnet-dhcpd: Setting vmnet-dhcp IP address: 172.16.152.254
Jan  3 14:11:07 rodney-laptop kernel: [  329.273402] /dev/vmnet: open called by PID 5730 (vmnet-dhcpd)
Jan  3 14:11:07 rodney-laptop kernel: [  329.273574] /dev/vmnet: port on hub 1 successfully opened
Jan  3 14:11:07 rodney-laptop vmnet-dhcpd: Recving on     VNet/vmnet1/172.16.152.0
Jan  3 14:11:07 rodney-laptop vmnet-dhcpd: Sending on     VNet/vmnet1/172.16.152.0
Jan  3 14:11:07 rodney-laptop kernel: [  329.277069] /dev/vmnet: open called by PID 5748 (vmnet-netifup)
Jan  3 14:11:07 rodney-laptop kernel: [  329.277216] /dev/vmnet: hub 8 does not exist, allocating memory.
Jan  3 14:11:07 rodney-laptop kernel: [  329.277335] /dev/vmnet: port on hub 8 successfully opened
Jan  3 14:11:07 rodney-laptop avahi-daemon[5320]: Joining mDNS multicast group on interface vmnet8.IPv4 with address 192.168.137.1.
Jan  3 14:11:07 rodney-laptop avahi-daemon[5320]: New relevant interface vmnet8.IPv4 for mDNS.
Jan  3 14:11:07 rodney-laptop avahi-daemon[5320]: Registering new address record for 192.168.137.1 on vmnet8.IPv4.
Jan  3 14:11:07 rodney-laptop vmnet-dhcpd: Internet Software Consortium DHCP Server 2.0
Jan  3 14:11:07 rodney-laptop vmnet-dhcpd: Copyright 1995, 1996, 1997, 1998, 1999 The Internet Software Consortium.
Jan  3 14:11:07 rodney-laptop vmnet-dhcpd: All rights reserved.
Jan  3 14:11:07 rodney-laptop vmnet-dhcpd: 
Jan  3 14:11:07 rodney-laptop vmnet-dhcpd: Please contribute if you find this software useful.
Jan  3 14:11:07 rodney-laptop vmnet-dhcpd: For info, please visit [http://www.isc.org/dhcp-contrib.html](http://www.isc.org/dhcp-contrib.html)
Jan  3 14:11:07 rodney-laptop vmnet-dhcpd: 
Jan  3 14:11:07 rodney-laptop vmnet-dhcpd: Configured subnet: 192.168.100.0
Jan  3 14:11:07 rodney-laptop vmnet-dhcpd: Setting vmnet-dhcp IP address: 192.168.100.254
Jan  3 14:11:07 rodney-laptop vmnet-dhcpd: Recving on     VNet/vmnet8/192.168.100.0
Jan  3 14:11:07 rodney-laptop vmnet-dhcpd: Sending on     VNet/vmnet8/192.168.100.0
Jan  3 14:11:07 rodney-laptop kernel: [  327.691627] /dev/vmnet: open called by PID 5755 (vmnet-dhcpd)
Jan  3 14:11:07 rodney-laptop kernel: [  327.691637] /dev/vmnet: port on hub 8 successfully opened
Jan  3 14:11:08 rodney-laptop kernel: [  327.837323] /dev/vmnet: open called by PID 5768 (vmnet-natd)
Jan  3 14:11:08 rodney-laptop kernel: [  327.837333] /dev/vmnet: port on hub 8 successfully opened
Jan  3 14:11:08 rodney-laptop vmnet-detect[5720]: NetDetectDaemonInit: No host policy file found. Not initializing filter. 
Jan  3 14:11:08 rodney-laptop vmnet-detect[5720]: Unable to initialize the daemon 
Jan  3 14:14:29 rodney-laptop kernel: [  528.815924] PPP generic driver version 2.4.2
Jan  3 14:14:29 rodney-laptop pppd[6097]: pppd 2.4.4 started by rodney, uid 1000
Jan  3 14:14:29 rodney-laptop kernel: [  528.853688] NET: Registered protocol family 10
Jan  3 14:14:29 rodney-laptop kernel: [  528.853767] lo: Disabled Privacy Extensions
Jan  3 14:14:29 rodney-laptop kernel: [  528.853811] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan  3 14:14:29 rodney-laptop pppd[6097]: Using interface ppp0
Jan  3 14:14:29 rodney-laptop pppd[6097]: Connect: ppp0 <--> /dev/ttySHSF0
Jan  3 14:14:30 rodney-laptop pppd[6097]: PAP authentication succeeded
Jan  3 14:14:30 rodney-laptop avahi-daemon[5320]: Registering new address record for fe80::250:56ff:fec0:8 on vmnet8.*.
Jan  3 14:14:30 rodney-laptop kernel: [  529.876735] PPP BSD Compression module registered
Jan  3 14:14:30 rodney-laptop kernel: [  529.940359] PPP Deflate Compression module registered
Jan  3 14:14:30 rodney-laptop avahi-daemon[5320]: Registering new address record for fe80::250:56ff:fec0:1 on vmnet1.*.
Jan  3 14:14:30 rodney-laptop pppd[6097]: Cannot determine ethernet address for proxy ARP
Jan  3 14:14:30 rodney-laptop pppd[6097]: local  IP address 150.101.76.118
Jan  3 14:14:30 rodney-laptop pppd[6097]: remote IP address 203.34.115.129
Jan  3 14:14:30 rodney-laptop pppd[6097]: primary   DNS address 192.231.203.132
Jan  3 14:14:30 rodney-laptop pppd[6097]: secondary DNS address 192.231.203.3
Jan  3 14:14:39 rodney-laptop kernel: [  538.864911] vmnet8: no IPv6 routers present
Jan  3 14:14:39 rodney-laptop kernel: [  539.056811] vmnet1: no IPv6 routers present
Jan  3 14:17:01 rodney-laptop /USR/SBIN/CRON[6188]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan  3 14:20:32 rodney-laptop kernel: [  891.854446] general protection fault: 0000 [1] SMP 
Jan  3 14:20:32 rodney-laptop kernel: [  891.854451] CPU 0 
Jan  3 14:20:32 rodney-laptop kernel: [  891.854452] Modules linked in: ppp_deflate zlib_deflate bsd_comp ppp_async crc_ccitt ipv6 ppp_generic slhc vmnet(P) vmblock(P) vmmon(P) binfmt_misc ac battery button container sbs dock video acpi_cpufreq cpufreq_userspace cpufreq_powersave cpufreq_conservative cpufreq_ondemand cpufreq_stats freq_table sbp2 parport_pc lp parport hsfhda(F) hsfserial hsfengine(P) hsfosspec snd_hda_intel snd_hda_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss joydev snd_seq_midi snd_rawmidi snd_seq_midi_event ipw3945 snd_seq snd_timer snd_seq_device snd ieee80211 ieee80211_crypt usbhid soundcore sdhci nvidia(P) hid snd_page_alloc iTCO_wdt iTCO_vendor_support pcspkr mmc_core intel_agp i2c_core ark3116 usbserial serio_raw psmouse shpchp pci_hotplug evdev ext3 jbd mbcache sg sr_mod cdrom sd_mod ata_piix ata_generic libata scsi_mod tg3 ohci1394 ieee1394 uhci_hcd ehci_hcd usbcore thermal processor fan fuse apparmor commoncap
Jan  3 14:20:32 rodney-laptop kernel: [  891.854509] Pid: 4087, comm: khsfd/modem Tainted: PF      2.6.22-14-generic #1
Jan  3 14:20:32 rodney-laptop kernel: [  891.854511] RIP: 0010:[_end+138065418/2130332920]  [_end+138065418/2130332920] :hsfengine:hsfengine2060_+0x32/0x180
Jan  3 14:20:32 rodney-laptop kernel: [  891.854580] RSP: 0018:ffff810077517de0  EFLAGS: 00010086
Jan  3 14:20:32 rodney-laptop kernel: [  891.854583] RAX: 0000000000000000 RBX: f000ec62f000e2c3 RCX: 0000000000000004
Jan  3 14:20:32 rodney-laptop kernel: [  891.854585] RDX: 0000000000000000 RSI: 0000000000020004 RDI: f000ec62f000e2c3
Jan  3 14:20:32 rodney-laptop kernel: [  891.854587] RBP: ffff810074b07000 R08: 0000000000000001 R09: 0000000000000001
Jan  3 14:20:32 rodney-laptop kernel: [  891.854589] R10: 0000000000000001 R11: 0000000000000000 R12: 0000000000020004
Jan  3 14:20:32 rodney-laptop kernel: [  891.854591] R13: 0000000000000000 R14: 0000000000000000 R15: ffff810077517ea7
Jan  3 14:20:32 rodney-laptop kernel: [  891.854594] FS:  00002b8bf14436e0(0000) GS:ffffffff80560000(0000) knlGS:0000000000000000
Jan  3 14:20:32 rodney-laptop kernel: [  891.854597] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Jan  3 14:20:32 rodney-laptop kernel: [  891.854599] CR2: 00000000014f7ee8 CR3: 000000005d48e000 CR4: 00000000000006e0
Jan  3 14:20:32 rodney-laptop kernel: [  891.854602] Process khsfd/modem (pid: 4087, threadinfo ffff810077516000, task ffff81007b8894a0)
Jan  3 14:20:32 rodney-laptop kernel: [  891.854603] Stack:  0000000000000001 ffff810074b07000 ffff810074b07000 0000000000000001
Jan  3 14:20:32 rodney-laptop kernel: [  891.854608]  0000000000000001 ffffffff88a0a681 0000000000000097 ffff810074b07000
Jan  3 14:20:32 rodney-laptop kernel: [  891.854612]  ffff810077517ea7 0000000000000001 0000000000000001 ffffffff88a09147
Jan  3 14:20:32 rodney-laptop kernel: [  891.854615] Call Trace:
Jan  3 14:20:32 rodney-laptop kernel: [  891.854662]  [_end+138081145/2130332920] :hsfengine:hsfengine1949_+0x41/0x50
Jan  3 14:20:32 rodney-laptop kernel: [  891.854707]  [_end+138075711/2130332920] :hsfengine:hsfengine52_+0xa7/0x140
Jan  3 14:20:32 rodney-laptop kernel: [  891.854716]  [_end+139484877/2130332920] :hsfserial:cnxt_intr+0x375/0x4a0
Jan  3 14:20:32 rodney-laptop kernel: [  891.854734]  [_end+137767838/2130332920] :hsfosspec:cnxt_thread+0x1c6/0x240
Jan  3 14:20:32 rodney-laptop kernel: [  891.854741]  [default_wake_function+0/16] default_wake_function+0x0/0x10
Jan  3 14:20:32 rodney-laptop kernel: [  891.854750]  [child_rip+10/18] child_rip+0xa/0x12
Jan  3 14:20:32 rodney-laptop kernel: [  891.854766]  [_end+137767384/2130332920] :hsfosspec:cnxt_thread+0x0/0x240
Jan  3 14:20:32 rodney-laptop kernel: [  891.854770]  [child_rip+0/18] child_rip+0x0/0x12
Jan  3 14:20:32 rodney-laptop kernel: [  891.854774] 
Jan  3 14:20:32 rodney-laptop kernel: [  891.854775] 
Jan  3 14:20:32 rodney-laptop kernel: [  891.854775] Code: 48 8b 6f 08 48 89 ef e8 12 f9 ff ff ba 01 00 00 00 85 c0 75 
Jan  3 14:20:32 rodney-laptop kernel: [  891.854784] RIP  [_end+138065418/2130332920] :hsfengine:hsfengine2060_+0x32/0x180
Jan  3 14:20:32 rodney-laptop kernel: [  891.854828]  RSP <ffff810077517de0>
Jan  3 14:21:12 rodney-laptop kernel: [  932.121907] 0000909.732: <7>DPCRequest: array is full!
Jan  3 14:21:22 rodney-laptop kernel: [  941.550507] 0000919.166: <7>DPCRequest: array is full!

---

### Post by khensucat on 2008-01-03
Clicking on the "screensavers" option is a guaranteed way to bring my system to an instant and  screeching halt in both 32 and 64 bit versions of Ubuntu.

---

### Post by ed_x on 2008-01-03
okay, I'm taking it back, 2.6.20 just froze for me as well (using lotus notes 7 in wine). I also noticed that crashing occurs after a reboot. When I boot up with effects disabled and enable them later, it will run fine. But when I boot up with effects already enabled, it will freeze.

---

### Post by jrickard on 2008-01-03
Well, I went for nearly a week with no lockups.  Now suddenly, I'm locking up every 30 minutes.  

Don't really know what changed.

Intel Extreme 2 Duo Quadprocessor QX6850
Nvidia 8800 Ultra

64 bit Ubuntu 7.10

No clue

Jack Rickard

---

### Post by yyyc186 on 2008-01-05
Just wanted to let you all know that it is now Jan 5, 2008.  I still have not had a crash or a system reboot since installing the new NVIDIA driver(s).  I will probably end up rebooting in just a few days so I can make an image backup, but no death and destruction of the unnatural kind.

---

### Post by yyyc186 on 2008-01-05
> **scradock said:**
> Ron,

Amazing!!!!! I did what you advised - just unchecked the first "enable" on the advanced dialog (all the others were blank anyway), and NO FREEZES!!!!! (so far!!!!!)

And yet, as you say, it CAN't be that simple can it? Otherwise, why did it freeze when Firefox wasn't even active?

So far - it works!!!

If the problem is a memory overwrite conflict between the SATA drivers and the video driver, then it can "seem" to work.  You will reduce the number of times the offending/corrupting code can be executed.

---

### Post by scradock on 2008-01-05
I don't quite know where the SATA drivers come in - I don't have any SATA drives, and all my partitions are on one physical drive (hda). I agree with your suggestion that the problem is likely due to an uncontrolled over-write locking something up, but that's what the kernel is supposed to sort out, isn't it? Allocating scratch space for hardware drivers HAS to be controlled by something, to avoid precisely the present scenario, and logically it ought to be the kernel......

---

### Post by ka9qlq on 2008-01-05
I'm up 6 days now with powernowd uninstalled and using cpudyn to manually control the cpu speed no lockups. Is there something that will let me use the inbetween speeds of 1.8 2 and 2.2 ghz? cpudyn does 1 and 2.4 ghz only.

---

### Post by ed_x on 2008-01-06
Adding acpi=off did the trick for me so far! I do have to miss the laptop keys now... ohwell it works now!

---

### Post by thebinz on 2008-01-07
**ah i am so fed up with this problem!** i wish there was a simple solution. I think it is total BS that the Ubuntu team hasn't addressed this issue yet. I know there are a lot of us out there that are frustrated with these lockups and freezes. I am so frustrated with Ubuntu right now. It used to be so dependable... now look at it. I don't even have a stable system and i haven't had one since gutsy! 
Sometimes i just want to take my computer outside and smash it with a sledgehammer until little shards of metal cut my hands and face open.
That's how angry I am at gutsy and/or the kernels that are causing the problems. 
:mad: :evil:
I am beginning to think we will never see a solution to this problem.
 It is kind of like smashing you face against a brick wall day after day. The brick wall doesn't break, but your face certainly does.
](*,)

I cant even run a torrent client without freezing.
Then after a hard reboot i have to deal with "Media was not unmounted correctly" Please wait 5 mins while we fsck your external drives.... Ahh!

---

### Post by ed_x on 2008-01-08
@thebinz: I agree on your statement, this really is a critical issue (aren't there other distributions out there where users have similar problems?). As long as it is stable with desktop effects turned off, it is ok by me. But compared to Feisty where it all worked, it is a step backwards.

---

### Post by eligos on 2008-01-11
> **ed_x said:**
> aren't there other distributions out there where users have similar problems?

I've tried Fedora 8 with same reults

---

### Post by lamadredelsapo on 2008-01-11
Curiously Gutsy runs better for me under vmware than directly installed in my PC, at least no lockups.

---

### Post by williammanda on 2008-01-11
Update: after installing the 169.07 driver My systems are working perfectly, no lockups or pink screens.

---

### Post by jrickard on 2008-01-12
I'm suffering similarly.  I like Ubuntu.  But if I come in every few hours and find my machine locked up it's not really very much good to me.  Liking Linux, pretty screens, etc. don't really matter if the thing just doesn't work as a computer.  This thread has gone for WEEKS and I've tried everything in it.

I do have a Mac Pro laptop.  It more or less just works.  I've thought about getting one of their big machines.  Their top of the line is about $14,000 now.  I'd rather just use Ubuntu, but it just isn't working at this point.

Jack Rickard

---

### Post by tschuliaen on 2008-01-13
I'm having similar freeze problems (only mouse movable, Ctrl+Alt+Backspace not working).
They did not occur using fglrx drivers however they do when I'm using the ati (radeon) opensource driver AND compiz!
With the newer [XorgOnTheEdge]("https://wiki.ubuntu.com/XorgOnTheEdge") drivers it seems a little more stable but not enough...

([my post]("http://ubuntuforums.org/showthread.php?p=4090371"))

---

### Post by AstarothCY on 2008-01-13
I'm debugging a total system lockup that seems to be caused by **any torrent app**, Well, not any, I've only tried Deluge and Azureus and they both crash in the same way. Also, the crashes started happening only a few days ago, no problems at all before that. Nothing shows up in my logs but I'm going to try to make the crash reproducible and see what I can do. I just hope it doesn't cause any data loss in the process.

---

### Post by mandlebaum on 2008-01-13
installing the 169.07 Nvidia drivers also fixed my problem, and just so everyone knows, these are the drivers from Nvidias site they are not available on Synaptic yet.

---

### Post by AstarothCY on 2008-01-13
Well, I really have no idea what is causing my crashes, I don't have an nVidia card so that's not it, and there is simply nothing in my logs so I don't even know where to begin.

---

### Post by Melcar on 2008-01-13
Mine turned out to be two problems.  The ATI drivers (fglrx) which cause mutex errors on 3D apps., and the USB ports on my motherboard.  I guess the SB600 is not that well supported in Linux because I always get errors with them; what causes the most problems in this case is the USB WLAN device I have, because it sometimes would "crash" do to the USB connection failing (USB works fine in Windows).

---

### Post by AstarothCY on 2008-01-14
Hmm, my USB wifi module keeps dropping the connection, perhaps it is a USB thing?

---

### Post by Melcar on 2008-01-14
> **AstarothCY said:**
> Hmm, my USB wifi module keeps dropping the connection, perhaps it is a USB thing?

What board do you have?  Mine is an Asus M2R32-MVP (X580 chip).  I can't even get ndiswrapper to work with my USB WLAN device (it crashes the whole system) and sometimes the connection (using the kernel module) would just "crash".  The device worked perfectly on my old nforce4 board (even with ndiswrapper).

---

### Post by AstarothCY on 2008-01-14
my wifi module is a Zyxel G-260, works fine most of the time. my board is a Fujitsu Siemens D1961 (SiS 661FX chipset).

[http://www.fujitsu-siemens.co.uk/rl/servicesupport/techsupport/Boards/Motherboards/FSC/D1961/D1961.htm](http://www.fujitsu-siemens.co.uk/rl/servicesupport/techsupport/Boards/Motherboards/FSC/D1961/D1961.htm)

---

### Post by Dokan1 on 2008-01-14
here the freezes were caused by either:

- firefox (of course only when i allowed flash -- so flashblock was saving my days)
- vlc (when watching dvd movies)
- amarok (when listening either mp3 or streams)

luckily enough i saw this post today:

[http://ubuntuforums.org/showthread.php?p=4073949#post4073949](http://ubuntuforums.org/showthread.php?p=4073949#post4073949)

my sound card is onboard (and is realtek btw). i deactivated it in the bios .. et voilà, problem gone! wow, at last! :KS :KS :KS
(i did many tests before posting, and since the crashes were quite easy to reproduce..and i know what i'm talking about..:-P)

now all i have to do is buying a new sound card :-P

those of you who have an onboard sound card and are having issues similar to the ones i had could try rebooting, disabling  your sound card, and see if the freezes / crashes remain or not.

cheers =)

---

### Post by Slade Winstone on 2008-01-15
Hi,

I thought I'd add my 10 cents worth:

I'm running an Asus A8M Laptop running Gutsy 2.6.22-14-generic.

I also managed to get a working system by specifying acpi=off at boot. I have now tried kernel boot parameters that I found that would allow ACPI to "run" giving me the Fesity functionality that I have been missing.

Instead of setting acpi=off to disable all ACPI (which previously was the only way of booting my A8M), I tried using nosmp noapic which allows some ACPI functionality and a good boot, however I began to experience this notorious hanging problem.

So, I guess that I'm back to the acpi=off and doing without acpi functions but at least I don't get the dreaded hang.

Slade.

---

### Post by AstarothCY on 2008-01-15
Hmmm, I have an onboard soundcard but it's not in use, i think my bios is set to choose the PCI by default but maybe i have to actually disable the onboard?

Anyway I think the problem is not like that. I removed this rather large torrent I had in Azureus which was 9GB and it hasn't crashed since. Now that I think about it, the crashes started right after I started downloading this large torrent. What could this mean?

---

### Post by khensucat on 2008-01-15
Interesting. I have a realtek sound system onboard. It doesn't seem to crash anything, though. The "braid" screensaver will when selected :(

USB doesn't seem to affect anything on this end - internet runs through it fine.

---

### Post by AstarothCY on 2008-01-15
btw i think i fixed the wifi connection dropping thing by removing DHCP for my computer on my router.

is there a linux app that checks hard disk health reports in SMART? i know speedfan does it in windows.

---

### Post by junior aspirin on 2008-01-15
could this realtek problem somehow be linked to inkscape? i always get a lockup when using it. i also get lockups when using flash and VLC. will try temporary disabling i will see if the problem persists.

edit: i cant seem to find an option in my BIOS, i have an ASUS K8V SE, with an AMI bios. any ideas. all i goud see was an audio 97' i disabled it, but didnt seem to do anything. any ideas?

---

### Post by Dokan1 on 2008-01-15
today i reinstalled my 64-bit gutsy (mostly because i was bored actually), and i'm now sure that my crashes were clearly caused by my realtek onboard sound card. btw here and there i heard of people having the same issue with other on board sound chips.

my freezes were easy to reproduce; the easiest way was to start watching a certain dvd movie, which make my system to crash at least 50% of the time. i could reproduce the crash quite many times with my sound card set on, while the movie runs smoothly when i put it off in my bios settings. :KS

anyways i'm sure people reading and posting here have issues caused by different hardware incompatibility with gutsy / its kernel / some random drivers / libraries.

> **Slade Winstone said:**
> Hi,

I thought I'd add my 10 cents worth:

I'm running an Asus A8M Laptop running Gutsy 2.6.22-14-generic.

I also managed to get a working system by specifying acpi=off at boot. I have now tried kernel boot parameters that I found that would allow ACPI to "run" giving me the Fesity functionality that I have been missing.

Instead of setting acpi=off to disable all ACPI (which previously was the only way of booting my A8M), I tried using nosmp noapic which allows some ACPI functionality and a good boot, however I began to experience this notorious hanging problem.

So, I guess that I'm back to the acpi=off and doing without acpi functions but at least I don't get the dreaded hang.

Slade.

you are not the only one Slade, for many people the acpi=off thingie fixed the matter. something to try i would say.

> **AstarothCY said:**
> Hmmm, I have an onboard soundcard but it's not in use, i think my bios is set to choose the PCI by default but maybe i have to actually disable the onboard?

Anyway I think the problem is not like that. I removed this rather large torrent I had in Azureus which was 9GB and it hasn't crashed since. Now that I think about it, the crashes started right after I started downloading this large torrent. What could this mean?

mm, really no idea about this azureus issue :???: did you try another torrent client to see if your system still crashes?
other than that, you can always disable your on board sound card since you aren't using it; you won't even have to get back to the bios later to reverse this setting ;)

> **khensucat said:**
> Interesting. I have a realtek sound system onboard. It doesn't seem to crash anything, though. The "braid" screensaver will when selected :(

USB doesn't seem to affect anything on this end - internet runs through it fine.

well, you can always try to disable it to see.
do you have a nvidia gpu? if so, did you try the newest (december) beta driver? (i heard it fixes some stability issues - and it's very stable btw, for me at least)

> **AstarothCY said:**
> btw i think i fixed the wifi connection dropping thing by removing DHCP for my computer on my router.

is there a linux app that checks hard disk health reports in SMART? i know speedfan does it in windows.

i never tried any, but i know a least one: search smartmontools with synaptic for a description.

> **junior aspirin said:**
> could this realtek problem somehow be linked to inkscape? i always get a lockup when using it. i also get lockups when using flash and VLC. will try temporary disabling i will see if the problem persists.

edit: i cant seem to find an option in my BIOS, i have an ASUS K8V SE, with an AMI bios. any ideas. all i goud see was an audio 97' i disabled it, but didnt seem to do anything. any ideas?

:???: audio 97 refers to your realtek sound chip. when you go back to your bios settings, do you still see it marked as disabled (well, kinda stupid question, i know)
so it seems like your crashes come from something else :???: btw did some of your lately freezes (after having disabled audio 97 i mean) were caused by either flash or vlc?

---

### Post by Bealer on 2008-01-15
Possibly found a solution for my setup. I had made the following changes:

- Used the 386 kernel instead of the Generic
- noapic nolapic added to my grub boot entry
- Disabling all power management, powernowd etc...
- Trying different display drivers, "ati", "fglrx" etc...

In the end I checked my BIOS and noticed ACPI was enabled in it. I disabled it. Possibly a conflict between the BIOS and Linux. Has been working for nearly a week now without a single freeze.

I'll slowly unchange the above one at a time incase they helped with the fix. Hopefully though I'll be able to use the Generic image, and get power management running properly.

---

### Post by junior aspirin on 2008-01-15
the Audio 97 says that it is disabled, but i still have sound! some thing strange there, also it did crash after that.

i have just disabled ACPI in the bios, and i cannot seem to cause it to crash :) although it is early days yet. Hopefully it is all fixed! thanks all. although maybe back yet.

---

### Post by AstarothCY on 2008-01-15
Hey Dokan1, thanks for the replies! Yes actually I was originally using Deluge for torrents and the behaviour was exactly the same. I uninstalled Deluge thinking it was it's fault and reloaded all my torrents in Azureus, including the huge 9GB one. It was still freezing so I removed the torrent, rebooted and it hasn't frozen yet.

---

### Post by AstarothCY on 2008-01-15
OK I just got home, woke the computer up, pressed play on Amarok (which was playing a song that I had just downloaded and whose torrent was being seeded), the music started playing and in about 2 seconds it froze. What's more, after I restarted my wifi connected as normal and in about 2 seconds it dropped the connection.


I am THIS close to dropping Ubuntu.

---

### Post by ka9qlq on 2008-01-15
> **mandlebaum said:**
> installing the 169.07 Nvidia drivers also fixed my problem, and just so everyone knows, these are the drivers from Nvidias site they are not available on Synaptic yet.

Wonder when if they will be.

---

### Post by Dokan1 on 2008-01-15
> **Bealer said:**
> Possibly found a solution for my setup. I had made the following changes:

- Used the 386 kernel instead of the Generic
- noapic nolapic added to my grub boot entry
- Disabling all power management, powernowd etc...
- Trying different display drivers, "ati", "fglrx" etc...

In the end I checked my BIOS and noticed ACPI was enabled in it. I disabled it. Possibly a conflict between the BIOS and Linux. Has been working for nearly a week now without a single freeze.

I'll slowly unchange the above one at a time incase they helped with the fix. Hopefully though I'll be able to use the Generic image, and get power management running properly.

from what i read here and there, acpi=off sorted out quite many people. and it's a good idea to disable it in the bios as well (maybe it's actually useless, but well it could be important, and we have to try quite many things to get rid of those nasty freezes).

> **junior aspirin said:**
> the Audio 97 says that it is disabled, but i still have sound! some thing strange there, also it did crash after that.

i have just disabled ACPI in the bios, and i cannot seem to cause it to crash :) although it is early days yet. Hopefully it is all fixed! thanks all. although maybe back yet.

i also hope your freezes are now past! myself i disabled acpi in both menu.lst and in my bios, but it didn't prevent my system to crash *when* my onboard sound chip was activated.
other than that it's strange you still have sound after you disable it in your bios! once again i hope you won't have any more freezes, but if it was happening when you run some application delivering sound, that *might* be audio 97 related.

> **AstarothCY said:**
> Hey Dokan1, thanks for the replies! Yes actually I was originally using Deluge for torrents and the behaviour was exactly the same. I uninstalled Deluge thinking it was it's fault and reloaded all my torrents in Azureus, including the huge 9GB one. It was still freezing so I removed the torrent, rebooted and it hasn't frozen yet.

> **AstarothCY said:**
> OK I just got home, woke the computer up, pressed play on Amarok (which was playing a song that I had just downloaded and whose torrent was being seeded), the music started playing and in about 2 seconds it froze. What's more, after I restarted my wifi connected as normal and in about 2 seconds it dropped the connection.


I am THIS close to dropping Ubuntu.

seems like we have some nasty bugs in common AstarothCY.

about your torrent issue, maybe your system freezes when your client is writing data to your hdd. i mean, when you start a 9 GB torrent, your client usually write those 9 GB on your disk. so maybe you could try to disactivate this option. also when you import a torrent for which you can seed, your hdd also works at full speed for some time, when your files' checksum is being verified.
sometime (very rarely though), my system freezes when i copy files, loads of them. whatever they are small or big, i mean much data. it might be a s-ata driver bug, or something else, i really don't know.

about amarok, do you thing your crash might have something to do with it? do you suspect amarok to be the reason of some of your freezes?
before deactivating my sound card it was the case for me, *sometimes* (this freeze was hard to reproduce, but i'm 99% sure amarok blew my system away at times - well amarok itself had nothing to do with the freeze, the problem was sound related).

did you try to disable your onboard sound card btw?

oh and one last thing for now, i tried opensuse 10.3 some time ago, and i had exactly the same problems!

maybe it's kernel related. someone in the thread said using the latest kernel from kernel.org solved his problems. if the freezes was coming back here i will try that, well first making a backup of my ubuntu with acronis, so it wouldn't be a problem to go back to the normal ubuntu kernel (which is more recommended of course).

good luck to all!!

and see you around anyways ;]

---

### Post by QuazyPat on 2008-01-15
I'm having the same problems. I'm running on a Radeon 9550 AGP and my comp will just freeze whether I'm in FireFox, Pidgin, listening to music, whatever. From what I've read on the other pages turning acpi off solves it. I can do that from the BIOS easy, but I'm really new To Linux (been using Windows, but finally got fed up). Can someone please describe where in the menu.lst to put the acpi=off command? Also, whenever I edit it, it says I don't have permission. Do I have to acess the file via terminal w/ sudo?

---

### Post by AstarothCY on 2008-01-15
Right, I'm going to try turning my soundcard off because I can't really remember having a crash without Amarok also being open so it might be related. I will also try acpi=off if that doesnt help.

---

### Post by hogman500 on 2008-01-15
i installed ubuntu on my computor with an AMD64 processor (and yes i did install gusty gibbon version of ubuntu) and i havent had any problems at all it works great.

---

### Post by AstarothCY on 2008-01-15
Disabled soundcard; problem not fixed. Still crashes. Any other ideas? Remember, this problem showed up out of the blue a few days ago, i had not installed anything new, so im thinking this was probably just an update that ruined everything.

---

### Post by AstarothCY on 2008-01-15
I never even realised this thread was in a 64bit forum. I'm moving my problem to a new thread elsewhere. Sorry.

[http://ubuntuforums.org/showthread.php?t=668816](http://ubuntuforums.org/showthread.php?t=668816)

---

### Post by junior aspirin on 2008-01-17
This is just to confirm that my problem was solved by disabling ACPI in the BIOS.  

What affect does this have? why would it have caused a problem? Why didnt i get crashes before gutsy?
i did try googling, but didn't really find out.

---

### Post by grinias on 2008-01-18
> **junior aspirin said:**
> This is just to confirm that my problem was solved by disabling ACPI in the BIOS.  

What affect does this have? why would it have caused a problem? Why didnt i get crashes before gutsy?
i did try googling, but didn't really find out.

Today Jan 18, 2008 a new update of an xorg package (cant recall the exact name of it)    solved the "freeze" problem for me, once again. I was not able to avoid freezes unless disabling acpi, as you do.

My machine:
Acer TM 4101 laptop,
Kubuntu 7.10,
ATI X600 using restricted fglrx driver.

Something very strange happens here :)

EDIT: Sooorryyy. It freezes again...

---

### Post by rotorcraig on 2008-01-18
There were a number of updates pushed out today, including xserver-xorg-core.

Earlier today this updated component was causing people a lot of problems; it was revoked from the download repositories and another updated version subsequently released.

Craig

---

### Post by grinias on 2008-01-19
> **rotorcraig said:**
> There were a number of updates pushed out today, including xserver-xorg-core.

Earlier today this updated component was causing people a lot of problems; it was revoked from the download repositories and another updated version subsequently released.

Craig

Yes, I show the subsequent update today, which once again solved the problem for me.
Anyway, to be clear, this problem is not an acpi-related one. For my laptop, acpi disabling  is required after the system freezes and for a number of booting sessions after that freeze. The power button pushing to "close" laptop after the freeze alters the clock settings and acpi is unable to recover this information the next booting session.

So, the problem relates to X, ATI drivers and whatever performs buggy at the kernel (I think).

Anyway, I am "freeze-free" since the last 2 hours and I hope it will be continued :)

---

### Post by slayer^_^ on 2008-01-19
confirmed here, with a nvidia 6800 gs with restricted drivers.

disabling compiz or using vesa drivers does not work, ubuntu freezes and my keyboard leds light up and down.

i tried re-updating but still does not work.

i noticed that if i run a game (for ex. xmoto) or if i switch between desktop i experience freezes

please tell me you'll solve this problem, i don't wanna change distro !!

---

### Post by grinias on 2008-01-19
> **slayer^_^ said:**
> confirmed here, with a nvidia 6800 gs with restricted drivers.

disabling compiz or using vesa drivers does not work, ubuntu freezes and my keyboard leds light up and down.

i tried re-updating but still does not work.

i noticed that if i run a game (for ex. xmoto) or if i switch between desktop i experience freezes

please tell me you'll solve this problem, i don't wanna change distro !!

Be sure, if a fix  is found, it wont be kept secret... By googling I have seen, that some other distros suffer from these problems too...

---

### Post by cheeby on 2008-01-19
Same issue here.  I updated the xorg-server-core yesterday and after a few hours of flakiness, X crashed.  I cannot log in to either KDE or Gnome unless I do so by choosing the gnome safe mode session from the options menu.

I did see that a patch was available for the xorg-server-core and I updated it, but the problem still persists:  X crashes as soon as I attempt to login via gdm.


Dell Precision 6300 NVIDIA Intel 64-bit dual core machine here.

Cheeby

---

### Post by gibberman on 2008-01-19
i'm experiencing the same sort of system hang but its not just that, several apps don't even execute. when i run pixelize, it'll crash at random points, same applies to firefox. i've tried using different browsers to no avail.

also streaming online .flv's causes my firefox to become unstable. i was wondering if these issues were co-related somehow....

so far everything i've tried has yielded no positive results. :mad:

and i really don't want to switch OS's

---

### Post by antiemptyv on 2008-01-19
the same happened to me.  apparently it could be an nvidia issue, too, i read in another thread.  i restarted and anytime i did something with the mouse to initiate any menus, tooltips, desktop switching, etc., it froze.  could it be something to do with desktop effects?  i tried hard reboots a couple times.  now i'm in failsafe gnome, which is working fine so far..

---

### Post by kleeman on 2008-01-19
I had this problem with an nvidia driver and the xorg-core update. I had to solve it three times (as the updates to xorg came in) by recompiling my nvidia driver -- I have the manually installed driver not the standard restricted modules version. Everything is fine now.

---

### Post by gibberman on 2008-01-19
well, my entire X when to hell after i tried messing around with the Nvidia restricted driver. I'm running ubuntu as a live user.


I think i'm going to try a fresh install of the OS and then install the nvidia drivers manually too, i'll post back to let you guys know about it.

---

### Post by scradock on 2008-01-19
I decided to do an upgrade to 64-bit Hardy Heron; it hasn't frozen up on me yet in five days! There's all the fun of constant updates, and the occasional glitch, but it beats trying to run 64-bit Gutsy!

---

### Post by grinias on 2008-01-22
> **scradock said:**
> I decided to do an upgrade to 64-bit Hardy Heron; it hasn't frozen up on me yet in five days! There's all the fun of constant updates, and the occasional glitch, but it beats trying to run 64-bit Gutsy!

I see many posts of successful upgrade to kernel 2.6.24, which is a freeze-free kernel...
This is done without upgrading to hardy. But there is no auto-installation of 3D for nvidia and ati cards.

---

### Post by tsoutherwood on 2008-01-22
I'm going to add my tale of woe to this thread...

I'm trying to commission a server (so no Xorg, no nvidia driver).

Server is based on an Asus M2N-E board (with onboard nVidia Corporation MCP55 SATA Controller (rev a2) sata controller) + nVidia Corporation MCP55 Ethernet (rev a2)

4 SATA disks
AMD Athlon(tm) 64 X2 Dual Core Processor 5600+
4 GB good quality RAM

GeForce 6200 video (text mode only)

Gutsy 64 bit is installed with all updates until yesterday, 2.6.22-14-server kernel

The system will work fine for about 6-24 hours, then bang.

"bang" has manifested itself in various ways including:

1) Near total userland death (cannot log in), but IP pings, SySRQ acknowledged

2) 2nd CPU core seemed to lock up on disk IO: [pdflush] stuck, could log in as root locally and do stuff like dmesg > /root/dmesg.log so VFS later working OK
"top" showed 50% IO wait (looked like CPU1 aka 2nd core stuck waiting for disks). In progress rsync was hung solid. SysRQ-T acknowledged but got stuck and gave no results to screen but dmesg did aquire some info. SysRQ-S
acknowledged but failed. Disk lights quiet. SysRQ-U failed. SysRQ-B worked.
dmesg had shown nothing unusual and no kenel messgaes on console.

3) Occasional hard lockup followed by a kernel panic early in next reboot stating Machine Check Exception. Changes BIOS settings (disabled Cool'n'Quiet and Virtualization support) and not seen that since. Of course I have run Memtest86+ and that passed. Disks have been beaten up with multiple badblocks runs and they worked OK.

I'm running a fairly complex filesystem setup:

Across all 4 disks:
Partition 1, 2GB, software RAID1 + ext3 for /boot
Partition 2, (nearly 500GB per disk), software RAID5 + LVM2, root and swap on LVM.

System temperatures are fine.

I'm not inclined to blame the hardware (especially PSU) given the half working system in case 2 above.

I do have a second identical board and CPU+RAM so a full parts swap is a possibility, but I'm pressed for time.

I think I will try a virgin kernel next (quite happy with kernel building).

In the meantime, I've rebooted with "pci=nomsi" as that was mentioned somewhere (LKML IIRC). Missed interrupt from the SATA circuits might well fit with what I'm seeing.

Cheers

Tim

---

### Post by fisuk on 2008-01-22
Long time no update, but still no lockups using 2.6.24-rc5. So I can quite confidently say that a kernel update will fix the thing.. Too bad for those who don't like to compile things.. :-(

---

### Post by tsoutherwood on 2008-01-22
> **fisuk said:**
> Long time no update, but still no lockups using 2.6.24-rc5. So I can quite confidently say that a kernel update will fix the thing.. Too bad for those who don't like to compile things.. :-(

Glad you're having success. Not so for me. Virgin 2.6.24-rc8 kernel, Ubuntu config and just the CPU type set blew up on me.

At least now I have a virgin kernel so the folks on LKML will actually be willing to talk about it.

Before I do, I will try the nomsi switch. I can now blow the driver in about 2 hours with suitably high IO load.

I don't think this is Ubuntu's fault - mine is either a kernel or a hardware bug (or bit of both).

Cheers

Tim

---

### Post by tsoutherwood on 2008-01-23
Alas no.

Tried pci=nomsi irqpoll

Can still hang it. Curious thing is that I can still run programs. Wonder if I'm actually seeing an XFS deadlock? (Data on XFS, 

I'll take my logs over to the Linux Kernel Mailing List and see...

Tim

---

### Post by rotorcraig on 2008-01-23
I've been monitoring this thread for some time as I have similar problem.

I have flipped between Gutsy and the latest Linux Mint (which is based on Gutsy) and see the same problem with both.

I am fine using the standard 'nv' drivers but if I install restricted 'nvidia' drivers my system hangs; after anything between 20 minutes and 2 hours but usually (always?) when using Firefox and/or playing videos.  I've tried latest and legacy and custom compile 'nvidia' drivers; doesn't make any difference.  When I go back to 'nv' all is well.

But I'm not a 64 bit users; my PC has a 32 bit ASUS A7N motherboard and I've installed a GeForce nVidia card (so am no longer using onboard nVidia graphics).  I don't use any SATA.

Do you guys believe that you are discussing and trying to resolve a 64 bit / dual core problem specifically?  Is there any point me trying the various kernel boot options that are being discussed or are they irrelevant for non-64 bit users?

---

### Post by tsoutherwood on 2008-01-23
> **rotorcraig said:**
> I've been monitoring this thread for some time as I have similar problem.




Hi,

I think my problem is solved, and it is a different problem. More testing needed to verify, but:

[http://www.mail-archive.com/linux-raid@vger.kernel.org/msg10159.html](http://www.mail-archive.com/linux-raid@vger.kernel.org/msg10159.html)

indicates I may have been seeing a bad XFS/md-raid5 interaction to do with the kernel strip buffers and a large (1024k) MD stripe size.

I've uppped

/sys/block/md1/md/stripe_cache_size
to 4096 from 256 and the system seems stable.

Cheers

Tim

---

### Post by grinias on 2008-01-24
There is also [another blog ]("http://johnorford.blogspot.com/2007/09/kubuntu-freezes.html") that mentions a NOT swap mounting freeze. It could be the case for many of us, since after hang it is difficult to trace what caused it.

Anyway, after last update yesterday, my system is stable again. I also changed the cpu frequency policy to "dynamic" (<--the default value) from "performance". No hang up for a day!

---

### Post by Prince_Andrei on 2008-01-26
I have had the same problem, but I *may* have just solved it--at least for me. I've tried everything, including new Nvidia drivers, maxcpus=1, mem checks, IRQ probs, etc. and nothing worked until now.

I have:
asus p5n-e motherboard
8600gt
q6600 quad core
2 sata drives
2 gigs ram

I would crash mostly during use of 3d apps, although sometimes in other apps, including Firefox--and just the gnome-panel. Looks like it is an ASUS BIOS issue in my specific case. The auto configuration for memory got a couple things wrong. Specifically, I went to JumperFree Settings, then:

- set AI Tuning to manual
- set memory clock to linked
- set memory ratio to sync

No lock-ups since then. I'll report back if it happens, but (knock on wood) so far it's looking good. I'm not sure if this applies to other asus motherboards, but it seems reasonable.

See this post for more details:
[http://ubuntuforums.org/showthread.php?p=4210959#post4210959](http://ubuntuforums.org/showthread.php?p=4210959#post4210959)

---

### Post by kevinp on 2008-01-29
I have managed to stop the freezes by changing my kernel boot options as follows:

/boot/grub/menu.lst:

```
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/md0 ro quiet nosplash noapic acpi=off pci=nomsi
```

Note that my root is /dev/md0 since I am booting from RAID.  I am running a dual core Athlon 64-bit.

The only possible downside:  If I have acpi=off will that make my power consumption go up?  This is a server system so I don't really use a GUI much.

---

### Post by Roddles on 2008-01-29
Hi All 

I managed to narrow down what is causing the freezes on my system.

I use an HSFModem (internal winmodem on a dell XPS m1710). With the driver loaded and in use, ie, connected to the internet, I get random freezes, particularly when using firefox (but no surprise there seeing as how that would be the main app to make use of the modem).

The second system lock up is when I use the ARK USB to Serial converter driver. 

I have a device that I am writing code for, and it has a HugePine / ARK usb to serial converter in it.

If I plug in that device, the driver loads and its all good. If I try to use that device, say by having that serial port made available to guest OS's through vmware workstation 6, seen by the Guest OS as a simple serial port, as soon as I activate the guest OS, the host system completely locks up.

These two scenarios however do not happen in 32 bit - the system is rock solid on 32 bit, using VMware passing the ark serial port through to guest OS's and using the HSF Modem driver connected to the internet, even both under heavy use at the same time.

I I don't use the HSF Modem or the ARK usb to serial converter, the system is solid.

Unfortunately, I need to use these vmware workstation with the ark serial connector for work, so these items have to work flawlessly for me. So at the moment I am back on 32 bit Gutsy.

Hopefully this will be fixed in Hardy.

Rod.

---

### Post by Roddles on 2008-01-30
Hi Guys

Just an update. I installed Kubuntu 8.04 (Hardy) 64 bit.

I installed the HSF modem drivers and today have been using the internet through it solidly for the past 3 hours. No problems to report thus far.

VMWare workstation works fine when you apply the patched vmware-any-any patch :)

So far no lockups, and the system is fast.

I think they have corrected the freeze issues in Hardy - well for me anyway :)

well done guys !

Cheers

Rod.:)

---

### Post by whaase on 2008-01-30
Mine is freezing as well, but it ONLY does it when its idle. I've never had it freeze when I was actually using the computer. I downloaded 8.04, but I'm scared to use a "beta" :)

7.04 never froze up on me.. ever.

---

### Post by wtowns on 2008-01-31
I only have the problem when compiz is on

---

### Post by whaase on 2008-02-02
Well, I gave up on it, I tried everything I could find/read about. I just wiped out it out. I left windows because of stuff like this. Ill give 7.04 another chance. If that doesn't work, ill go pick up a Mac.

---

### Post by Roddles on 2008-02-02
Ok 

I have now been running Kubuntu Hardy 64 bit for 3 days now.

I have run the HSF Connexant modem driver with VMWare workstation 6.0 and have had absolutely no problems. I leave the modem connected and in use all day while at work. No more lockups.

I still get the Lockups using the ark3116 USB to Serial Converter as soon as I try to establish a connection with it, but the HSF modem is all working now. 

Hardy is still in Alpha, so is not ready for people who cant use alternate methods to do things such as the command line, but, there is light at the end of the tunnel.

I have not had a single freeze using the modem since moving to 64 bit Hardy.

Cheers

Rod.

---

### Post by Fredizdman on 2008-02-03
I'm not sure if this will help anyone else, but I was browsing this thread for quite some time and found no working solutions. I finally figured out that my problem was KDE+Superkaramba. There is a kde bug report on this [http://www.nabble.com/-Bug-143255--New:-Superkaramba-makes-X.org-unresponsible-td9571847.html]("http://www.nabble.com/-Bug-143255--New:-Superkaramba-makes-X.org-unresponsible-td9571847.html")
Entirely quitting all instances of superkaramba and its widgets (of course) solved my freezing problem.This thread also says that you can run one superkaramba widget without issues, but I have to verify it myself although it seems to be the common consensus. Maybe this will help someone else.
This has worked for me for 3+ days on a desktop that froze every 20 minutes otherwise.

AMD 3200+
1 GB RAM
KDE 3.5.8
SuperK : 0.42
Compiz-fusion
Nvidia Proprietary

---

### Post by pyrforos on 2008-02-03
hey! Thats so cooooooooooooll!
Thanks mate!No lockups now!Running 1widget and no problem
Im thinking to integrate alll my widgets to one.. Think it wiil work?:confused:

---

### Post by Artemis3 on 2008-02-07
This thread, unfortunately mixes too many things.
I'm going to refer to the x server crash related to intel video

This seems triggered by screen savers, and i have been able to reproduce it trying to run a game in wine which works perfectly with 32bit ubuntu. It seems to occur at resolution change.

The purpose of this message is to say yes, me too.
Note this occurs in my machine at work where i'm stuck to intel video :(


PD:  I just installed **xserver-xorg-video-intel** 2:2.1.1-0ubuntu9.1 from proposed, and it does NOT fix the problem.

---

### Post by Kalimotzxo on 2008-02-08
Hey this problem is important enough for me to register and put in my thoughts.  

I looked in /var/log/syslog around the time my system freezes and I see a lot of "hda: lost interrupt", then I eventually see the IRQ for my graphics card get turned off. I have also seen to oomkiller start running a shutdown processes.  I am running:

AMD64 4200 X2
ECS K8 mobo
OS on IDE drive, /home mounted to SATA Raid
Nvidia 6600GT

I can always cause a crash by running the braids screensaver... Any others care to check their syslog and run the screensaver?  This crash bug seems very low level and difficult to pinpoint.

---

### Post by khensucat on 2008-02-08
> **Kalimotzxo said:**
> Hey this problem is important enough for me to register and put in my thoughts.  

I looked in /var/log/syslog around the time my system freezes and I see a lot of "hda: lost interrupt", then I eventually see the IRQ for my graphics card get turned off. I have also seen to oomkiller start running a shutdown processes.  I am running:

AMD64 4200 X2
ECS K8 mobo
OS on IDE drive, /home mounted to SATA Raid
Nvidia 6600GT

I can always cause a crash by running the braids screensaver... Any others care to check their syslog and run the screensaver?  This crash bug seems very low level and difficult to pinpoint.

Just clicking on braids in the screensaver selection window will hard lock my pc every single time, requiring a hard-reset. Absolutely, 100% reproducable here.

Intel Core2Dul
Asrok mobo
IDE hard drive (no sata)
Nvidia 5500 AGP

---

### Post by Kalimotzxo on 2008-02-09
I thought I found a reproducible bug, but it looks like this is being addressed:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/101943](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/101943)

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg633733.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg633733.html)

[http://ubuntuforums.org/showthread.php?t=628006](http://ubuntuforums.org/showthread.php?t=628006)

Related to compiz and nvidia driver?  So if I turn off compiz my system will stop crashing?  Several others on this thread still say they get lock ups...  There has to be a way to fix this.

---

### Post by khensucat on 2008-02-09
This is why I have *always* been against Compiz-by-default :(

---

### Post by Wallace on 2008-02-10
The latest security update to 2.6.22-14 hasn't fixed my lockup so I'm running 2.6.20-16 again, which has never locked up once.

I'm only running server version, so no X, no screensaver, etc. It definately seems to be a kernel issue to me.

---

### Post by Melcar on 2008-02-10
Another lock up, while I was sending email with Thunderbird.  Also suffered several other locks while Firefox was one.  Those have been the only locks I have suffered so far since I re-installed everything.  The logs are useless, since they don't seem to be logging anything at or near the time of the freezes.

---

### Post by khensucat on 2008-02-11
Installing Dapper has solved every single problem I've had, even using the braid screen saver. It even looks better to boot. Although I know the programs are older, I haven't noticed any real loss in functionality ;) Even reminds me of Gentoo a little, with it's -xeon kernel option, along with a -nocona Swiftweasel build from sourceforge :lol: I think I'll just be sticking with this until Hardy comes out. I can't find a single problem with it, now that I've used Kilz' script to get Flash running :guitar:

Newer isn't necessarily better ;)

---

### Post by Kalimotzxo on 2008-02-11
> **khensucat said:**
> Installing Dapper has solved every single problem I've had, even using the braid screen saver. It even looks better to boot. Although I know the programs are older, I haven't noticed any real loss in functionality ;) Even reminds me of Gentoo a little, with it's -xeon kernel option, along with a -nocona Swiftweasel build from sourceforge :lol: I think I'll just be sticking with this until Hardy comes out. I can't find a single problem with it, now that I've used Kilz' script to get Flash running :guitar:

Newer isn't necessarily better ;)

I agree with you on that.  Stability trumps bleeding edge in my book.  
I dug a little further, and these "lock ups" are probably attributed to memory leaks in compiz.  So by going back to Dapper, you are probably using a version of compiz (beryl back then?) without the leaks.  The latest (0.5.2):

[http://lists.freedesktop.org/archives/compiz/2007-August/002581.html](http://lists.freedesktop.org/archives/compiz/2007-August/002581.html)

shows several fixes for memory leaks.  I am going to turn off compiz for the time being and hope that Hardy will be better.  I don't *need* the bling in my UI, but it is nice...

---

### Post by Artemis3 on 2008-02-11
To disable compiz:

system->preferences->appearance->desktop effects->none

Installing dapper for something this simple is a little overboard imo...

---

### Post by khensucat on 2008-02-11
No. Compiz on or off, I still have the same problems. I don't run with compiz anyway, default or not. If it comes with it on, I disable it first thing. If it doesn't come with it, I don't enable either it or Beryl. I don't see the point, personally ;) Of course, I'm a little older, and don't see the point of spinning rims or lip rings. To each their own :lol:

---

### Post by Melcar on 2008-02-12
I think I have found my problem.  Today I was trying to download OpenSuse and the whole computer froze again.  Rebooted, logged in, started the download again, and another freeze.  I did the whole thing five times, and every time the computer froze.  This, combined with the other previous freezes (when running FF, Thunderbird, downloading, using Flash, playing online games) leads me to believe that it's something with my wireless connection.  Maybe ndiswrapper has trouble with 64bit and/or with my particular card (it's using Win64 drivers anyway).  Unfortunately I can't test without ndiswrapper because this card I have does not work without it.

---

### Post by Bokonon on 2008-02-12
Yeah, I am thinking if Hardy is a good release, I will be staying on that for a while.  Maybe one machine to play with the newer releases, but all systems that are 'critical' for me would stay on hardy.

I had trouble with compiz and without.  I don't think compiz is the problem.

As for me, I am still running well on the nVidia binary driver (169.07 then and now 169.09).  I switched all systems over which is a bit of a pain on kernel updates, but things are running smoothly.  Compiz also works well with the binary driver, but after playing with compiz a few days, I turned it off.

---

### Post by khensucat on 2008-02-13
Same here. After the Gutsy fiasco, I'll be going LTS to LTS, unless a particular release REALLY shines in it's stability ;-)

---

### Post by damoisture on 2008-02-13
Been all over this thread and a few others. I have pretty much given up hope of getting my system to work for more than 48 hours at a time without it locking up. I have upgraded to the latest binary drivers (169.09), disabled (and uninstalled) compiz, and several other fixes I've found. I'm just going to backup my vital info and do a fresh install when Hardy is released.

My system:
AMD Athlon 64 X2 5200+
4GB RAM
Epox nVidia 570 MB
Gigabyte nVidia 7300SE Video Card
A whole buncha hard drives

I guess I can do a memtest again, haven't done one since I went from 2 to 4GB of RAM. Any other suggestions?

---

### Post by fjgaude on 2008-02-13
I trust you are not overclocking anything... sounds like weak memory to me... not good.

---

### Post by damoisture on 2008-02-14
Just ran about 4 hours of memtest with no errors, will run a longer test tomorrow while I'm at work. I'm also going to try ditching the BOINC manager, see if that helps.

---

### Post by vikramsharma on 2008-02-14
I had the same problem of constant locking up in Gutsy, I did the memtest86+ turned out  my memory was bad.  Now things are better with new memory.  Try doing the the memory test see if your RAM is good, there might be some problems there.

---

### Post by Melcar on 2008-02-14
Already ran countless hardware tests, including Prime95.  Everything is in working order.  It must be something with Gutsy itself.  Most of the freezes happen when I'm online, like downloading large files, playing Flash (sometimes), and opening a crap load of tabs in FF (oddly enough not when I game online).

---

### Post by khensucat on 2008-02-14
I think it is. As I just posted in another thread, running either Dapper or Hardy Alpha eliminates virtually *all* of the problems I experience with Gutsy ;)

---

### Post by Melcar on 2008-02-14
I can now confirm that my wireless connection is indeed causing the freezes.  The hard lock is replicated every time I attempt to download large files (like a DVD iso of a Linux distro).  It also happens with less frequency when simply browsing the web or even checking email.  I really have no idea what could be causing it.  The logs tell me nothing.  Already tried removing IPv6, since I hear that causes some problems, but still the same issues.  Also got rid of Firestarter, but that isn't the problem either.  Ndiswrapper perhaps?  This problem does not happen in 32bit Ubuntu.

---

### Post by khensucat on 2008-02-15
I wonder what the underlying *core* problem is that makes Gutsy freeze on errors. So many different kinds, and they all make Gutsy freeze. I can use almost any other version of Ubuntu, or any other distro, and not run into these constant unrecoverable errors.

---

### Post by Melcar on 2008-02-15
Found what is causing my system freezes.  It is in fact ndiswrapper.  It does it with every card I have tested, but only in 64bit.

---

### Post by MM23 on 2008-02-16
this is not an ubuntu issue, either. I've been having frequent freezes myself, and I'm using 64-bit Gentoo.

strangely, I'm also using ndiswrapper, though I would have never thought that is the problem.

the freezes are not x specific -- that is, I cannot ssh into the machine or move my mouse. trying to ping the computer results in failure. the system completely hard locks -- there are no kernel logs or anything after I reboot. everything prior to the crash in the logs indicates normal activity.

really annoying. I get anywhere from 30 minutes to 30 hours of uptime before it randomly decides to do this, and I've tried everything from upgrading to bleeding edge glibc, gcc, xorg and upgraded my kernel from scratch (that is, I did not reuse my old .config and started a completely new menuconfig) 2.6.24-r2.

---

### Post by Melcar on 2008-02-16
> **MM23 said:**
> this is not an ubuntu issue, either. I've been having frequent freezes myself, and I'm using 64-bit Gentoo.

strangely, I'm also using ndiswrapper, though I would have never thought that is the problem.

the freezes are not x specific -- that is, I cannot ssh into the machine or move my mouse. trying to ping the computer results in failure. the system completely hard locks -- there are no kernel logs or anything after I reboot. everything prior to the crash in the logs indicates normal activity.

really annoying. I get anywhere from 30 minutes to 30 hours of uptime before it randomly decides to do this, and I've tried everything from upgrading to bleeding edge glibc, gcc, xorg and upgraded my kernel from scratch (that is, I did not reuse my old .config and started a completely new menuconfig) 2.6.24-r2.

Sounds similar to my problem, although I can pinpoint mine to heavy network activity.  Only on 64bit systems too.  Already tried OpenSuse 10.3 and even also compiled my own kernel.  The logs show nothing, which means that it's not a kernel or OS error, so it must be either hardware or a driver outside the kernel (like Win drivers).  Already tested my hardware for stability, so the only other cause would be the second option.

---

### Post by khensucat on 2008-02-16
Hmmm. Strange. I can't get crashes on even other 64-bit *buntu variants (tried Kubuntu and Xubuntu, both work without a hitch here), tried Mepis64, Gentoo stage 3, Mandy 64 bit (free), Fedora 64 bit, and OpenSuSE 64 bit. I only personally get the lockups and crashes with Ubuntu 64 (and 32-bit, actually) Gutsy :-(

---

### Post by borsten on 2008-02-17
On my machine nearly every distro randomly freezes too, not only *bunutu.
```
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev f3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
01:07.0 Network controller: Techsan Electronics Co Ltd B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card (rev 02)
04:00.0 VGA compatible controller: nVidia Corporation Unknown device 0422 (rev a1)
05:00.0 VGA compatible controller: nVidia Corporation Unknown device 0422 (rev a1) 
```
It doesn't seem to be a graphics-driver issue, becaues ive tried all nvidia-drivers from 104 till 171, still same problem. gentoo64 works and arch64 too. ive triede to build a custom kernel for kubuntu gutsy several times, but still no change. i didn't try the udev-way till now, but for the moment ill stay with gentoo. I think it has something to do with the amd athlon x2 / opteron, but i may be wrong.
i don't use any wireless devices or special drivers except the nvidia-drivers

---

### Post by leona on 2008-02-18
Shame that we are getting no feed back from the developers, over 500+ posts here and pages and pages of bugs filed on the [launchpad]("https://bugs.launchpad.net/bugs/157777") site, yet no answers, no feedback, we're left to fend for ourselves, is this the right way to treat the 'community', epect people to stick around and wait for such a 'core' problem to be fixed?  Will it ever be fixed?  Its very frustrating. 

I have noticed a few kernal updates come through recently, whether they are related to this crashing issue I don't know, they didn't say, but my system has been stable for a while now, not had a lock up for a while.  So maybe they are getting on top of it, **but it would nice to let us "the users" know!**

---

### Post by nevlis on 2008-02-18
I have the same problem. Dell Inspiron 6000, running Gutsy, random times, hard lockup. I'm thinking it might be a memory issue.

---

### Post by jaffa_nz on 2008-02-18
Kia Ora

Usual problem, running Dell D620 dual-core 2gb ram intel945gm vid.  Hangs only when i have COMPIZ-FUSION loaded.

It seems that something relating to some or all or few of downloading, FireFox, file Copying, DVD/CDrom access, power Management, Compiz effects, some any video types (ati/ nvid) and a host of others - causes the lock up issue.

i had some limited success by removing power management (not preferred on a lappy) but in the end it would raise its ugly head!

This kernel has issues.  

Could anyone point me at a link to upgrade my kernel to another version (leaving me on Gutsy Gibbon) so i can check that out?

cheers

---

### Post by damoisture on 2008-02-19
Well, system has been up and running stable for 3 days now. I uninstalled BOINC, and that seemed to do the trick. I am now going to try slowly adding features back to my system (mainly Compiz), and see how stable it remains. Unfortunate if BOINC was causing the lockups, what's the point of having all this processing power if it does nothing 95% of the time?

---

### Post by khensucat on 2008-02-19
A high bogoMips count? :lol:

---

### Post by arkeo on 2008-02-19
I installed the 32 bit version to see if the lockups would go away--but I get the same exact behaviour as in the 64 bit version: the nvidia driver is again the main suspect for me along with FireFox (there's a general instability, but running FF you can be 100% sure everything will crash). Reverting to the nv driver solves everything- It amazes me that I can replicate the same behaviour in both 32 and 64 bit versions...

I hope Hardy will be back to the same level of the older releases, Gutsy for me has been a huge disappointment.
I agree that some sort of feedback from the developers would be welcome--and BTW, if I were trying out Ubuntu (or Linux) for the first time I'd be reinstalling Windows thinking something like "man, if this is what happens with the most popular distro...!!"

---

### Post by khensucat on 2008-02-19
> **arkeo said:**
> I installed the 32 bit version to see if the lockups would go away--but I get the same exact behaviour as in the 64 bit version: the nvidia driver is again the main suspect for me along with FireFox (there's a general instability, but running FF you can be 100% sure everything will crash). Reverting to the nv driver solves everything- It amazes me that I can replicate the same behaviour in both 32 and 64 bit versions...

I hope Hardy will be back to the same level of the older releases, Gutsy for me has been a huge disappointment.
I agree that some sort of feedback from the developers would be welcome--and BTW, if I were trying out Ubuntu (or Linux) for the first time I'd be reinstalling Windows thinking something like "man, if this is what happens with the most popular distro...!!"

Agreed. You should hear the reassuring my S/O has to do when he installs Ubuntu for 1st time users ;) 7.10 drove him  back to Debian :lolflag:

---

### Post by Diskwipe on 2008-02-23
I have also experienced these freezes in Gutsy.  Both keyboard and mouse are completely dead - not even caps lock working - and the only recovery is a hard reboot.  It appears to be completely random - happens especially after an idle period so I have been experimenting with ACPI and BIOS settings but, so far, no conclusion.

The first step in solving this problem (IMHO) is to discover the unique (??) set of circumstances which cause the failure - ie if we could get it to fail predictably, we'd have some chance of finding a solution.  Right now, there are so many different circumstances reported that I can understand why developers are struggling to fix the problem.  Even if we all individually find a package or setting which seems to cause the failure, I suspect that we will merely increase the MTBF.  For example, Melcar reports ndiswrapper is causing his problem, but I'm not using this package.

However, pending a definitive fix, what else can we do but try to increase the MTBF for each of our individidual hardware configurations?  Also, on a pessimistic note, if we don't understand what caused this problem in Gutsy, what's to stop it happening again in Harty? :(

---

### Post by khensucat on 2008-02-23
Well, part of it is compiz, from my interactions on launchpad. It has some problems ;) I'm now running Hardy, and while I've not experienced any of the other freezes/etc... I had in Gutsy, the Braid screensaver is still a problem. I gave them a gentle nudge last night :lolflag:

---

### Post by chip_munk on 2008-02-26
I had the same problems. It would lock up, Caps Lock and Scroll Lock lights would flash or it would just reboot. No commonality between the occurrences. Sometimes it would reboot after clicking on an email in Thunderbird. Next time it would freeze opening a Terminal just after booting up.

I tried to go to SuSE 10.3, but I couldn't get past the installation. So I was about to go back to SuSE 10.2 which had worked perfectly for me. Then I read the comments of people who'd decided to use the Hardy kernel.

Another 10 minutes and I was using the Hardy kernel. That was a week ago and so far no reboots, no lock ups, just a "stable" system.

My Specs:
AMD64 dual core
NVidia GE7600 Silent 
Compiz running.
FF always open

Cheers
Chris

---

### Post by manoskats on 2008-02-27
> **arkeo said:**
> 
I agree that some sort of feedback from the developers would be welcome--and BTW, if I were trying out Ubuntu (or Linux) for the first time I'd be reinstalling Windows thinking something like "man, if this is what happens with the most popular distro...!!"


Well,that's me you're talking about.But I dont have the option of turning back to windows,as I'm working on something for my studies and my professor said I have to work on linux.And worst of all,the freezes seem to occur more often when using PAW
(you can find out what it is here:[http://paw.web.cern.ch/paw/]("http://paw.web.cern.ch/paw/"),or download it through synaptic)
and I have to use it.

I was never very much into computers and being forced to learn linux is tough enough,but this freezing thing just blows.I guess I'll look for another distro.

Btw I have an intel graphics card,havent read all 59 previous pages but many posts seem to be blaming it on nvidia cards.

---

### Post by zakiwi on 2008-02-27
Hi there,

Just thought that I´d add my two cents.

I´ve been using Ubuntu on a tablet for several months now, but for several reasons decided to move my main development to a new desktop box.  So I decided to look at the future and buy bigger than I really needed now.  Of importance in the spec was 8GB RAM and I speced a NVidia 8600 GTS graphics card .... WHAT A NIGHTMARE !!!

Since then ... I´ve installed various flavors of Linux and continually had lockups/hard freezes (No Num Lock or Caps lock... and you can´t ping the machine).  Flavors of Linux that I tried were Ubuntu (7.04 64bit, 7.10 32bit and 64bit, 8.04 Alpha4 64bit), Debian Etch 64bit, Debian Lenny 64bit.  All experienced random lockups.  Specifically when the graphics card was trying to do 3D stuff.  Until two days ago, I found the NVIDIA-Linux-x86_64-100.14.23 driver to be the most stable ...  NVIDIA-Linux-x86_64-169.09 would lock up real quick.  Anyway ... 

I thought that I´d mention that two days ago, I tried again and installed Ubuntu 7.10 64bit with the new NVIDIA-Linux-x86_64-169.12 driver, and I have stability.  I can´t run fancy screensavers ... but I don´t need to ... but everything else is stable and I´m running compiz with all the bells and whistles and it´s not frozen yet.  I should however say that I ran the matrixview screensaver, and on two occasions it froze, but that´s the only time, and as I said, I don´t need to runt it ... flying feet is fine ... Most importantly ... my development environment is stable now.

I thought I´d just share my experience as it may help others.

Cheers

Zakiwi

---

### Post by khensucat on 2008-02-28
> **manoskats said:**
> Well,that's me you're talking about.But I dont have the option of turning back to windows,as I'm working on something for my studies and my professor said I have to work on linux.And worst of all,the freezes seem to occur more often when using PAW
(you can find out what it is here:[http://paw.web.cern.ch/paw/]("http://paw.web.cern.ch/paw/"),or download it through synaptic)
and I have to use it.

I was never very much into computers and being forced to learn linux is tough enough,but this freezing thing just blows.I guess I'll look for another distro.

Btw I have an intel graphics card,havent read all 59 previous pages but many posts seem to be blaming it on nvidia cards.

Quite frankly, if I were to introduce someone to Linux, the *last* distro I would run for them would be Ubuntu 7.10 ;) The same goes for my recommendation for someone needing to learn Linux. When we install Ubuntu for someone, we either install Dapper or Fiesty - I think if you try either of those, you'll find MANY, MANY fewer problems, and MUCH more stability. Dapper heavier on stability, but uses much more outdated software ;) Also, on the "learning" side, I would recommend just trying Debian Etch. Debian is the meta-distro Ubuntu comes from, and the Etch line is rock-solid - but like Dapper, at the cost of up-to-date packages.

If you "really" want to learn Linux, though, you should give Gentoo a shot ;) It's quite the eye-opener, and while I'm glad I did it, it *definately* made me appreciate not only the efforts of those "behind the scenes", but the day-to-day ease of use of a click-and-install, user-freindly distro like Ubuntu :KS

---

### Post by jonah1980 on 2008-02-28
i jumped ship to fedora before christmas as i was sick of the freezes and lock ups. fedora is totally awesome, i've got all the desktop compiz stuff going on and with the livna repos you get the latest nvidia drivers instead of waiting around like i was on ubuntu. i was waiting so long for the driver that fixed the issue with ubuntu i just gave in and fedora with livna has had about 5 nvidia driver updates since then, while ubuntu still locking up.

fedora was hard to get used to, and you have to go to a bit more trouble to get proprietary codecs and stuff like flash going. but there is a really cool wiki that guides you through everything called fedorasolved...

anyway one day i'd love to go back to ubuntu maybe on next release i'll try it. but now i'm having such a great experience without problems on fedora i dunno, i might stick with that. it's just as fast etc even though everyone told me it wouldn't be. and i like how with yum you can remove stuff you don't need like banshee or whatever and make your system how you want it without it wanting to remove half the distro base like ubuntu always did. and it's been so solid and stable. awesome. anyway i recommend for anyone having these issues that can't wait out the storm.

fedora 9 could be amazing judging from fedora 8 werewolf's success. let's hope hardy get's things back on track for ubuntu...

---

### Post by manoskats on 2008-02-28
> **khensucat said:**
> Quite frankly, if I were to introduce someone to Linux, the *last* distro I would run for them would be Ubuntu 7.10 ;) The same goes for my recommendation for someone needing to learn Linux. When we install Ubuntu for someone, we either install Dapper or Fiesty - I think if you try either of those, you'll find MANY, MANY fewer problems, and MUCH more stability. Dapper heavier on stability, but uses much more outdated software ;) Also, on the "learning" side, I would recommend just trying Debian Etch. Debian is the meta-distro Ubuntu comes from, and the Etch line is rock-solid - but like Dapper, at the cost of up-to-date packages.

If you "really" want to learn Linux, though, you should give Gentoo a shot ;) It's quite the eye-opener, and while I'm glad I did it, it *definately* made me appreciate not only the efforts of those "behind the scenes", but the day-to-day ease of use of a click-and-install, user-freindly distro like Ubuntu :KS


Ok,I'll think about it.Thanks for the suggestions khensucat .

---

### Post by zakiwi on 2008-02-28
Sadly ... my box was frozen again this morning ... have reverted to the NVidia 100.14.23 driver ... perhaps the 169.12 driver is not as stable as it first appeared.

Cheers

zakiwi

---

### Post by Diskwipe on 2008-02-28
Just a cautionary note re Khensucat's recommendation to use Debian etch.  When I tried this - about 3 weeks ago - I could only get the command line interface.  The Xserver just reported that it couldn't find any screens.  I use the nVidia 8300 GS, which is by no means the latest graphics card, but the Etch repositories didn't include any drivers which worked at all.

After spending ages editing Xorg.conf - trying VGA, VESA, etc - I still was not able to load the Gnome desktop.  Finally, editing the sources.list to specify the unstable version (Sid), I was able to get a suitable driver and get Debian working.

Although I don't know if Etch supports other (relatively) new graphics cards, it's probably worth checking the Etch sources content for your card before opting to switch to this distro.  I must admit that I found Debian far less "user-friendly" than Ubuntu so have decided to persevere with Gutsy.  (I also tried Solaris - too slow and flabby!!)

One of my colleagues has been running Feisty for about a year and reports that it's "rock-solid" so maybe that's the way to go if someone doesn't want to learn Linux but just use its functionality.

Cheers

---

### Post by khensucat on 2008-02-28
> **Diskwipe said:**
> Just a cautionary note re Khensucat's recommendation to use Debian etch.  When I tried this - about 3 weeks ago - I could only get the command line interface.  The Xserver just reported that it couldn't find any screens.  I use the nVidia 8300 GS, which is by no means the latest graphics card, but the Etch repositories didn't include any drivers which worked at all.

After spending ages editing Xorg.conf - trying VGA, VESA, etc - I still was not able to load the Gnome desktop.  Finally, editing the sources.list to specify the unstable version (Sid), I was able to get a suitable driver and get Debian working.

Although I don't know if Etch supports other (relatively) new graphics cards, it's probably worth checking the Etch sources content for your card before opting to switch to this distro.  I must admit that I found Debian far less "user-friendly" than Ubuntu so have decided to persevere with Gutsy.  (I also tried Solaris - too slow and flabby!!)

One of my colleagues has been running Feisty for about a year and reports that it's "rock-solid" so maybe that's the way to go if someone doesn't want to learn Linux but just use its functionality.

Cheers

Thanks, that's good to know about that particular card in Debian. My Nvidia is nowhere near that high up on the food chain :lolflag:

Again, also, I'd second the Fiesty mention as the example of Ubuntu to use, relatively recent, rock-solid, and *just works* ;)

---

### Post by Diskwipe on 2008-02-29
> **khensucat said:**
> Thanks, that's good to know about that particular card in Debian. My Nvidia is nowhere near that high up on the food chain :lolflag:

Again, also, I'd second the Fiesty mention as the example of Ubuntu to use, relatively recent, rock-solid, and *just works* ;)

My colleague - mentioned in my last post - also had a similar proble with Etch and a Matrox card, although he managed to config it using VGA 640x480.  The screen was pretty dire but we didn't really need Gnome since it was a server install.

Anyway, I agree with Khensucat's comment that Debian is a better learning distro than Ubuntu, but it sounds like Manoskats just wants to get on with his Uni project, so the last thing he needs is to be confronted by a command line prompt.  Also, although it's relatively easy to source the appropriate driver, integrating it into the Debian kernel from the command line is quite another proposition for a novice (like me!!) :)

I hope Manoskats doesn't experience such problems but forewarned is forearmed.  Good luck!!

Cheers

---

### Post by Lutin on 2008-02-29
> **zakiwi said:**
> Sadly ... my box was frozen again this morning ... have reverted to the NVidia 100.14.23 driver ... perhaps the 169.12 driver is not as stable as it first appeared.

Cheers

zakiwi

I have not been suffering from freezing as such, but using any nVidia drivers later than 100.14.23 causes one particular problem. That being when the computer goes into sleep mode (I am assuming this as the lcd panel powers down) I cannot then wake the computer up. This does not happen with the earlier 100 series drivers - the computer wakes-up no problem at all.

As I said, this happens with all the variants of the 169 series of nVidia drivers on my 64 bit Gutsy setup. Since this is the nVidia driver included in Hardy, I am reluctant to move to this until this problem has been sorted.

Just my two penneth worth.

---

### Post by chip_munk on 2008-03-02
Well I've been giving my Pc a bit of a bashing, video encoding, big downloads etc and it's still up and going fine. I still regularly check the system monitor to see what's going on "under the hood" so to speak.

NVidia GeForce 7600 GS
NVidia driver 169.09
Ubuntu Gutsy with a Hardy kernel.

---

### Post by rotorcraig on 2008-03-03
> Then I read the comments of people who'd decided to use the Hardy kernel.

Another 10 minutes and I was using the Hardy kernel. That was a week ago and so far no reboots, no lock ups, just a "stable" system.Wouldn't mind trying that.  Would you repost the instructions that you followed please?

RC

---

### Post by braynyac on 2008-03-03
rotocraig,

I did some quick browsing and came up with this:

[http://ubuntuforums.org/showthread.php?t=646755]("http://ubuntuforums.org/showthread.php?t=646755")

Hope this helps =)

~braynyac

---

### Post by chip_munk on 2008-03-04
Yep, that's the thread I followed. The important bit, for me, is not to forget to reinstall Envy and use it to get the correct NVidia driver. I forgot and had problems, but properly reading the instructions, and following them all this time, soon sorted me out.

Cheers
Chris

---

### Post by zubrug on 2008-03-04
This got quite annoying, had this issue on other distro's using ubuntu as a base, I have been running sidux ( [http://sidux.com/](http://sidux.com/) ) with absolutely no issues. My new phenom box just rocks running sidux.
No matter what I throw at it - Ice weasel, sidux-irc,  superkaramba, beryl, ktorrent, vbox with windows xp and whatching Blue Planet 1080 on mplayer.
I have switched to iceweasel at the moment because opera 64bit + flash results in single core running at 99%, known bug on opera forums.

---

### Post by Diskwipe on 2008-03-07
Warning: The Hardy kernel doesn't seem to support AHCI, which must be enabled in the BIOS if you have SATA drives capable of NCQ.  
See [http://www.seagate.com/content/pdf/whitepaper/D2c_tech_paper_intc-stx_sata_ncq.pdf](http://www.seagate.com/content/pdf/whitepaper/D2c_tech_paper_intc-stx_sata_ncq.pdf) for more information.

When I tried to run the Hardy kernel in Gutsy - apart from the nVidia driver problem identified by Chip_Munk - the system went into a retry loop while accessing the disk and I couldn't get past this point until I disabled AHCI in the BIOS.  Since it seems a shame not to use the full capabilities of my SATA drives, I reluctantly returned to the Gutsy kernel.

Ah, well - if a solution looks too-good-to-be-true ... :)

---

### Post by julian67 on 2008-03-08
> **khensucat said:**
> Quite frankly, if I were to introduce someone to Linux, the *last* distro I would run for them would be Ubuntu 7.10 ;) The same goes for my recommendation for someone needing to learn Linux. When we install Ubuntu for someone, we either install Dapper or Fiesty - I think if you try either of those, you'll find MANY, MANY fewer problems, and MUCH more stability. Dapper heavier on stability, but uses much more outdated software ;) Also, on the "learning" side, I would recommend just trying Debian Etch. Debian is the meta-distro Ubuntu comes from, and the Etch line is rock-solid - but like Dapper, at the cost of up-to-date packages.

+1

I'm not brave enough to install Gutsy for people because I hate giving refunds :lolflag:  Feisty is a very nice combination of stability, hardware compatibility, speed and features, it's a real shame this wasn't marked for LTS and it's also a shame that the minimal backporting in Ubuntu means you have to upgrade the distro to get important new versions of applications (Gimp changing from 2.2 to 2.4 is a huge one for me). After using Gutsy for a few months on different computers I've been really disatisfied so have  been trying a few alternatives for my own computers (Zenwalk, Arch, Debian, antiX) on one laptop for a few months and finally settled on antiX + Xfce for all my computers. It's incredibly stable even using the sid repos (as long as you do actually read the proposed updates when running apt-get upgrade/apt-get dist-upgrade and occasionally chicken out) and also performance is markedly superior to Gutsy. For other peoples PCs I'll stick with Feisty for the moment. It just seems to run without issue and no surprises.

---

### Post by UberrrSauce on 2008-03-08
you could try adding this to the boot parameters of grub;

```
irqpoll pci=noacpi noapic nolapic acpi=off
```

It helped to alleviate some freezing problems I was having with Gutsy AMD64, hope it helps you.

---

### Post by julian67 on 2008-03-08
> **UberrrSauce said:**
> you could try adding this to the boot parameters of grub;

```
irqpoll pci=noacpi noapic nolapic acpi=off
```

It helped to alleviate some freezing problems I was having with Gutsy AMD64, hope it helps you.

turning off acpi is not a good solution for laptop users, particularly as Gutsy is already rather demanding on the battery on many machines. These problems are  not apparent on the same identical hardware using a different debian based distro (or any Slackware based distro I tried) so disabling important features is no real solution, more an act of desperation. I also wasn't running compiz (completely purged it as I anyway use Xfce).  I had some other reasons for wanting something different such as preferring to manage upgrading with rolling release instead of the flaky upgrade or re-install process (not a criticism specific to Ubuntu, same in Mandriva, openSuse, Fedora etc) but finding *all* my computers to be horribly unstable on Gutsy (variously having used nvidia graphics, ati graphics both free and proprietary drivers and intel gma) was the compelling motivation to take the time out and make the change. I now have 3 rock solid stable computers with better performance and the same or greater choice of applications and even newer versions of applications available. Anyway the solution for me has been simple and complete: don't run Gutsy.

I've had a look at hardy Alpha 5 and I'll have another look at the final release hoping it's as stable as Dapper and Feisty were but for the moment running antiX everything is fast, stable and simple and I have absolutely no reason to change.

---

### Post by falken78 on 2008-03-11
I just plugged in my ney 4 GB of RAM in my computer today. What a suprice when the system start freezing!!  First as all likely do I tested the new RAM modules. They came out OK.

Then after some searching I found this and several other threads pointing to the graphic-card (which I personaly thougt was a bit strange... but after some testing without solving the issue at hand I pulled out my Nvidia card (before this I uninstalled compiz, tried to run with the VESA driver, dissabled APIC (non of this helpt my situation...  When I stayed out of my display manager the system seemed to be fine (am running gnome)).

So I booted with my internal ATI graphicscard, installed the ubuntu flgrx driver, rebooted - now it has been running just fine for 1 hour... which is about 59 minutes more then before....

I will come back if my problem comes back.. but for now it looks good...:popcorn:

---

### Post by grinias on 2008-03-12
By doing a little "googling" I am now sure that is a hardware related problem. It has to do with ACER? Is it the ATI graphics card? Or perhaps the memory modules? 
Anyway freezing appears also when I boot to WinXP and I have to apologize to Gutsy developers...

---

### Post by rotorcraig on 2008-03-12
> rotocraig,

I did some quick browsing and came up with this:

[http://ubuntuforums.org/showthread.php?t=646755](http://ubuntuforums.org/showthread.php?t=646755)

Hope this helps =)

~braynyac
Thanks for that.  Have tried the Hardy kernel but as soon as I enable 'nvidia' drivers everything starts freezing again :(

RC

---

### Post by WadiJM on 2008-03-12
It hapends to me when I'm seeing videos on youtube. If I have more than 3 tabs open gtk-gnash process start killing my cpu!! Is there any bugfix for this? I just want to see youtube videos....
Wadi

---

### Post by kvillage on 2008-03-13
Hi,

I'm running Ubuntu 7.10 Server with Xfce4 on a dual xeon system, 4 GB RAM (2.6.22-14-server, nvidia driver installed manually, version 169.12). I'm using a Nvidia FX3000 Quadro and had several Xorg freezes (actually 100% CPU usage and still access by using ssh, sometimes). To reproduce the problem I ran glxgears or simply activated dual head mode in nvidia-settings.

In my case the problem seems to be the adaptive clocking. As long as the card remains in performance level 0 there is no problem, but a start of glxgears forces performance level 2 and a freeze/xorg crash. Same thing happens when dual head mode is activated.

I installed nvclock and set frequencies of memory and gpu according to performance level 0 (300 MHz gpu / 850 MHz memory in my case). The system remains in performance level 0 after activating dual head mode, but unfortunately switches to level 2 when running glxgears what causes another crash (sometimes I was able to switch back to level 0-like settings by using nvclock utitlity again, but that's only possible if you react very fast ;-)).

Does anyone know a way to deactivate adaptive clocking? That would be a workaround for me until a new nvidia driver / xorg is released.

By the way: Every other solution I've found in forums etc. was not successful. I had freezes after setting NVAgp to 0-3, after having blacklisted intel_agp, setting PerfLevel in modprobe.d/options or modprobe.d/nvidia. Now, I'm using a default xorg.conf where I only changed device driver from vesa to nvidia. As long as low performance level is used, the system is stable. I installed nvidia drivers manually with options -n -e (to be sure that correct sources were used) and did not use nvidia-xconfig to configure xorg.conf.

Regards,

Kris

---

### Post by rotorcraig on 2008-03-13
> As long as the card remains in performance level 0 there is no problem
That could be what I'm experiencing.  GLXGEARS certainly causes me problems.  How can I tell what performance level my card is in?

RC

---

### Post by kvillage on 2008-03-13
> **rotorcraig said:**
>  How can I tell what performance level my card is in?


I used nvidia-settings gui: You can see the current level in the Powermizer section. Another option is to use **nvidia-settings -q GPUCurrentClockFreqs** to check current frequencies. 

I've just tried to lock memory and gpu frequencies with Coolbits option instead of nvclock ("Coolbits" "1" in device section, --> new Overclocking option in nvidia-settings) but the system ignores my settings when running glxgears (experienced by other users in this thread [http://tennessee.ubuntuforums.com/showthread.php?t=612144&page=6](http://tennessee.ubuntuforums.com/showthread.php?t=612144&page=6) )..

Kris

Edit:
Tried Fedora 8, same effect, freezes even in graphical installer during setup..(nvidia driver 169.12 and kernel 2.6.24)..

Edit2:
Using Ubuntu 7.04 (server kernel) and XFCE4 with old xorg version and nvidia driver 169.12 failed, too. Same effect, even without running glxgears...

Edit3:
Tried nvidia 100.14.09 and 100.14.19 under 7.10, same problem.

Edit4:
Used restricted driver (nvida-glx, not manually installed) on a PIII-650, Geforce3 64MB, Xubuntu 7.10 system. Freeze after about 3 minutes. System runs stable with vesa/nv drivers.


Finally, I'll give up using nvidia drivers until nvidia releases a new driver. It doesn't seem to be a bug in Xorg (used different versions) or a hardware problem (different systems run stable while not activating nvidia-driver, used different nvidia-cards) and it's definitely not a bug in Ubuntu or the kernel (tried Fedora 8, Debian 4, Ubuntu 6.06/7.04/7.10, Xubuntu 7.10, openSUSE 10.3). I've spent hours/days with this problem and now it's enough.. goodbye 3d support :-)

---

### Post by Diskwipe on 2008-03-15
Hi,

Finally abandoned Gutsy in favour of Feisty (AMD-64).  (Bit of a nuisance with Feisty - need to 'sudo' almost everything you want to do.  Had to config a root password and log-on as root.)

Now running nVidia 169.12 installed via ENVY.  Using the nVidia Xserver settings to get 1680 x 1050 screen res.  Hoping for no more 'freezes' [-o< but will post results after a few days.

---

### Post by rotorcraig on 2008-03-16
> I've spent hours/days with this problem and now it's enough.. goodbye 3d supportSame here.  I'll try again when Hardy comes along.  Thanks for the help in the meantime!

RC

---

### Post by Diskwipe on 2008-03-16
Well, my experiment with Feisty didn't last long - got the same 'freeze-up' as with Gutsy.  Symptoms exactly the same - can't even get numlock or capslock to work.  Now going back to Gutsy 32-bit to see if the problem happens only on 64-bit.  If this doesn't work, sadly I'm going to give up until hardy comes along. :(

Already tried Debian (didn't like it) and Solaris (too slow) but I've heard good reports about FreeBSD and Centos (Red Hat).

Cheers

---

### Post by rotorcraig on 2008-03-18
Good luck.  My problems have all been with 32 bit Gutsy :(

RC

---

### Post by Diskwipe on 2008-03-19
> **rotorcraig said:**
> Good luck.  My problems have all been with 32 bit Gutsy :(

RC

So-far-so-good.  No freezes in 2 days which is about 46 hrs better than Gutsy 64-bit!!  FYI, I'm running nvidia geforce 8300 but not glxgears - probably because I don't know what this is.  :lolflag:

TK

---

### Post by ShadowMKII on 2008-03-21
I am having a problem where my Gutsy decides that it wants to freeze as well.

Me, being a Windows user in the past, went to the System Monitor as the first course of action to try and solve this problem.

Since I have to hard reboot everytime this problem occurs, I did not want to do it again. My computer starts to freeze up, slow down, the mouse is jittery and partly unresponsive, then all of the windows fail to work. This is apparently a problem that has been happening to some other people on the forum as well, but I cannot seem to find the thread right now.

Anyhow, back to where I was. I timed the freezing intervals to about half an hour each. I then thought that it was odd for timed freezing unless this distribution of Linux somehow contracted a virus. Nonetheless, I went to the System Monitor at about the 25 minute mark (by chance) and found something even more odd than "timed freezing." What was strange was that one of my cores on my AMD Athlon X2 64-bit was at about 72% while the other was at about 5%. This, however is the strangest part - my memory was at about 85% usage.

I restarted my computer the regular way because my computer had not yet frozen and then went to the System Monitor after the fresh restart. (By the way, restarting X does not solve this problem entirely). I then watched the memory slowly build up in usage from my regular 256MB standing all the way to 1.9GB, since I have about 2.0GB of RAM. At the 89.8% usage mark, my computer was officially frozen and I barely made it out "alive" to do a regular restart instead of a hard reboot.

In other words, my computer's RAM was being stuffed with some kind of extra information that caused it to eventually fill up and cause my computer to crash. Just for additional info; my Ubuntu's swap goes from 0 to 100% in about 3 seconds when my memory usage reaches about 80%. As I am typing, this stage is happening right now and my computer will freeze in about 5 minutes.

You could say I have this down to an art - and that is only after having this happen 6 times or so.

I hope this information helps because I do not want to have to use some other non-Linux computer to get something done that takes more than 25 minutes!

---

### Post by caeroe on 2008-03-23
I think I fixed it on my setup.  I have a HP m7680n.  Just recently I upgraded the powersupply to 480w and the graphics card to a Nvidia 7600GS 512mb.  Prior to that I had a entry level 7300LE 256mb with a 300w powersupply.

With my old hardware I was lucky to run Ubuntu for more than 10-15 minutes.  Playing WoW through Wine would be a guaranteed freeze.  But since the hardware changes nothing has locked up or anything.  I can view Youtube videos, goof off on the desktop, play WoW interrupted, etc.

I think it's just a crapshoot.  Or whatever that expression is?

---

### Post by ShadowMKII on 2008-03-23
That expression sounds about right!

I still cannot get my problem to stop, however. What a bother.

---

### Post by hackersmovie on 2008-03-25
issues here as well. I just installed Gutsy on my macbook, it was all running very good until about an hour ago. Now, as soon as i boot and login in, if I open more than one window, it locks up, completely! I can move the mouse around but that's it! I have to push and hold the power button to reboot. This sucks, big time, I just got everything but the sound working. 4 days for nothing, please help!

---

### Post by rotorcraig on 2008-03-26
In the last couple of days I've reinstalled Ubuntu using the Hardy Heron Beta release.  There are clearly a lot of changes being made to the Beta before Hardy is finalised; about 30 updates came through yesterday alone.

But last night I enabled restricted nVidia drivers and full desktop effects, and with exactly the same hardware all seems to be fine so far with the exception of the "incorrectly rendered title bar" minor issue that I know has been a "feature" of desktop effects for some time.

As I say it's only been a few hours of use, but initial indications are good.  I'll monitor stability for a week or so and post back.

RC

---

### Post by lanzen on 2008-03-27
I've been in Hardy for week and no lockups.

I did uninstall my installed nvidia 169. driver that fixed the problem in gutsy before starting the update. Just in case... :)

---

### Post by rotorcraig on 2008-03-31
I ran with "full desktop effects" enabled for a few days and was getting on great.  Was convinced that Hardy had fixed the freezing that I'd seen in Gutsy.

Over the weekend I did a number of things:

[LIST]
[*]Enabled a bunch of additional desktop effects options, decided that they were pretty but I didn't need them and so removed them again.
[*]Allowed Hardy to download tens of updated components as they were release by the Beta programme
[*]Installed Google Earth from Synaptic Package Manager
[*]Installed and removed a number of DVD creation tools that I wanted to try
[/LIST]

At the end of the above I seem to be left with a Hardy installation that crashes in exactly the same way that Gutsy used to; ie always crashes when I am using Firefox & MPlayer leaving the Num/Caps/Scroll lock lights flashing.

I'm convinced that somewhere on my list (or another item that I've forgotten) I've introduced a change that destabilised Hardy.

RC

---

### Post by turandota on 2008-04-01
Just a newbie's observations.

When I install 7.10 and 8.04b on a Shuttle q6600/4gb RAM/3x 320gb HDs/Ati 2600hd, after awhile the system locks up just like other ppls, however when I installed 7.10 and 8.04b on a Mac Mini C2D 2ghz/2gb RAM/160gb sata HDwith VMware Fusion, absolutely no lockups or freezes of any kind. I've been running 7.10 & 8.04b for a week now in two separate virtual machines 24/7 and neither of them have crashed. Running the amd64 versions. I don't know why its different on my Shuttle with the separate video card......

---

### Post by theShaggy on 2008-04-03
My Gutsy 64 seems to have randomly decided to start crashing again.

I can't quite see anything next to Firefox, Pidgin or BitTorrent (Deluge this time, but it happened with Azureus, too).

Far as I can tell, I've had it freeze on me quite frequently when trying to run Update Manager.  It will just suddenly lock up and do nothing.  Other situations I can recall:

Playing videos with MythTV on my TV-Out (Nvidia 7300 GS with the latest drivers)

Using Deluge and leaving the computer alone.  This is a big one, because for at least a month, if I didn't run Deluge my computer wouldn't crash for days, and when I put it back on, it would.  I thought it was solved by turning off Wireless connections (I have a wifi card and a hardwired modem so I don't need the wireless), but no such luck.  I'd like to remove that module, but don't know how.

Running anything with Flash.

Just sitting around doing nothing.

Saving files in Open Office.

And pretty much anything.  If I'm playing any sort of sound, it will just loop the sound, the mouse will lock, the screen will freeze and I'd have to hard-reboot.

I know Hardy is around the corner, and I hope that helps, but I really don't like having this suddenly crash four times in one night when I have essays due in the next week.  Any suggestions?  I have a Realtek RX480M4 motherboard with a disabled on-board Radeon x200 video card and on-board sound, etc. etc.

---

### Post by hackersmovie on 2008-04-03
turning  compiz OFF has solved my issues. I shoulda known, I enabled a black listed video card, DUH!! So, now I just run it without, unless I need to wow the pants off someone, then I click it on real fast, wow them, and turn it off. . .  He he. . . :)

---

### Post by theShaggy on 2008-04-03
I had Compiz off for months, and still had the trouble.  Now I've got it running, and it was far more stable for about a month.

---

### Post by lanzen on 2008-04-04
I'm one of the lucky ones who solved this problem with the* then* new 169.09 nvidia driver. I've started testing hardy a couple of weeks ago and soon after moved definitely.
I would advise those of you who are still affected by this annoying bug to give hardy a try. Hardy seems a very fine OS even if - it must be remembered and taken into account - it's still beta.

Do a search in the forum to see if you find any issues related to your card, back your valuable files and... when you're safe, upgrade.

Good luck!  :)

---

### Post by Luci4 on 2008-04-05
I cannot even upgrade. My ubuntu freezes when trying to install updates (and just during other random things) and withouth updates it will be more annoying to upgrade to hardy. Maybe I'll just do a clean install... There's not much in my ubuntu anyways (most is on my external harddisk)

---

### Post by Mr_Ada on 2008-04-05
Yesterday I started seeing freeze up firefox and today I used "free -m" and blammo it knocked me down to the boot level.  This is horrible.  WHen I first installed things were fine, it might me an update that is messing me up as I always update.  I went to Ubunto because I couldn't stand windows and now it is behaving just like windows did!  Yikes!

I have a quad-core pentium with 4 gb of RAM, Nvidia card.

chris

---

### Post by braincat on 2008-04-11
I have experienced similar problems as most people in this thread. Running
E6750 CPU on Abit IP-35 Pro board with NVIDIA 8500GT card, with 
a 171.06 (beta) driver.  System was locking up solid all the time, with keyboard lights
flashing when I had Gutsy installed, regardless of using default or beta
nvidia driver.  After installing Hardy, things became more stable, I can
actually get some work done on that machine.   System still freezes  about
once a day, but stability is much better (still not something I would run
on a production box).   Can't say for sure that nvidia drivers are at fault.

The most reliable way to freeze that machine is to run any virtualization
software.  I tried kvm, vmware and virtualbox.   Virtualbox would just crash,
both kvm and vmware would either segfault or hang the whole machine.

The computer is a fresh build, so I cannot rule out hardware problems completely.
Not overclocked, BIOS settings are very conservative, and memtest ran ok.
I have an old P4 machine running Gutsy with NVIDIA drivers (geforce 5500GT card),
it has been rock solid.

I really hope things would become better before Hardy is released.
   Brain.

---

### Post by Chelidon on 2008-04-12
> Yesterday I started seeing freeze up firefox and today I used "free -m" and blammo it knocked me down to the boot level. This is horrible. WHen I first installed things were fine, it might me an update that is messing me up as I always update. I went to Ubunto because I couldn't stand windows and now it is behaving just like windows did! Yikes



Oh, I know the feeling! But the weirdest thing about my situation is that it acts EXACTLY like it did in Vista. It froze five times in a week while running firefox, at the end of which I loaded Ubuntu 7.10, which I removed and reinstalled due to some icky bootloader issues. Unfortunately I'm such a noob that I don't know how to monitor my system. Yesterday I installed lm-sensors to keep track my CPU temp, per the suggestion of a boardie in the Hardy Dev forum. I'm apprehensive about Hardy because the top threads that came up in a 'firefox crash' search were in the Hardy forum. I implore the devs to root out the problem before they release it, because perpetuating this issue would be far worse than the lack of sound I had to work around in Gutsy!

---

### Post by bedege on 2008-04-12
I've done a fresh install of 64bit Gutsy on my neighbor's machine (AMD64) about 2 weeks ago. I installed the Nvidia restricted drivers + flash r115 as proposed by Ubuntu. And, as many others, he encountered many hard crashes, where only on/off button would do the trick.

Seems like this very thread has been active for months now, and still no easy fix seams to be available... What could be the more likely cause of this misbehavior ? Is there a summary of this 64+ pages thread somewhere ?

Other question is quite simple: should I upgrade to Hardy beta ? Is it considered as being more stable than Gutsy on AMD64 ?

Thanks

---

### Post by braincat on 2008-04-12
I have to say I am now red-faced over my yesterday's post.
What I missed was an incorrect timing in the BIOS for the memory
that I am using.  My apologies for making a claim that I cannot
substantiate anymore.  After fixing the bios setting, the machine
has been completely stable under Hardy (64 bit kernel) and nvidia
beta driver.  I didn't do any advanced graphics stuff, just a lot
of numerical computations.
BSOD's in XP have also stopped.

---

### Post by Lion-Simba on 2008-04-14
Hello there.

I had that randomly lockups too. Log-files were just OK.

I was thought that's nvidia's drivers fault. I had come to their forum and noticed, that they advised to run kernel with the following parameters to increase stability on systems, which have more than one core (CPU):
```

idle=poll maxcpus=1

```

I've tried that. It helps. But, as you can see, maxcpus parameter limits the number of used cpus to one. It's of course not good to loose half of my CPU power.

So, I've tried to start the kernel with only "idle=poll" parameter, but it doesn't help.

After more googling, I've noticed in some mail-list, that some hardware systems have issues with TSC (Time Stamp Counter), which is responsible to provide high-resolution timer for the kernel.

Kernel developers knows that issues. On boot kernel firstly tests TSC. If it's good, kernel enables TSC as default kernel clocksource.

I've a look in my log file and noticed that TSC test was passed and TSC was set as my clocksource.

However, I remember, that long ago on WinXP I had very strange behavior of ping utility. It was displaying **negative** reply times! But it was not always, it was randomly too.
That's the first.

The second. When I was running -rt kernel, I had lockups too. But sometimes, in syslog I was getting a message like this:
```

Apr 12 14:15:55 localhost kernel: [ 6687.945076] BUG: time warp detected!
Apr 12 14:15:55 localhost kernel: [ 6687.945086] prev > now, 10c3a38d7e80091d > 10c39f8d7e8032c1:
Apr 12 14:15:55 localhost kernel: [ 6687.945093] = 4398046500444 delta, on CPU#0

```
The hangs occurs only **after** this message in syslog. Not strictly after, may be after 30 minutes, a hour, but not before.

So, I assumed, that this all can be because of the same reasons!

And I tried to run the kernel with following option, which switches kernel clocksource to acpi_pm timer (there are also some others - "pit" for example):

```

clocksource=acpi_pm

```

No more lookups here!

I believe that's what I was looking for. ;)

PS. My system is Pentium D 820, GF7600GT, Ubuntu 7.10.

---

### Post by rickyrockrat on 2008-04-14
For some of you, you are having problems with an application taking all your memory, then swapping to disk. Be patient, and use top to find the culprit.  Once you find the culprit, remove it if you can to prevent this from happening again. Gnash (flash player) was the culprit on my machine.
Disk swaps are REALLY slow, and when you hit 80-90% it appears that your machine is frozen, but it is just extremely slow.  If your mouse moves or numlock light responds after a few seconds to a minute, then you likely have a mis-behaved program sucking all your memory. If you truly want to find this memory leak, try the following:
1) Log in to your graphical desktop.
2) Hit Ctrl-Alt-F2 you will be presented with a text console login. 
3) login with your user & passwd (just like your graphical login)
4) type top, then hit enter. You will see a list of programs and stats - that is what top does.
5) Hit Alt-F7, which will take you back to your graphical environment. 
6) When you get your "freeze", hit Ctrl-Alt-F1 again, slowly and carefully. Wait a long time 1-5 minutes.
Look in your memory column(%MEM).Use '>' to sort on different columns.  Find the culprit that has 70-90% of your memory, and note the PID (the number in the PID column). Hit  q to exit top,(again things happen slooooowly)  then type kill PID, where PID is the number of the process taking all the memory (say it is 9034). 
kill 9034
Your box should speed back up. Use Alt-F7 to get back to the graphical desktop. If you want to catch it again, type top before the Alt-F7.


For others, you are having a real hardware problem. The first thing to do is to stop using the binary driver for your card and use the open source one. If you can't or won't do that, it is unlikely your problem will be solved.
 If that does not fix the problem (i.e. you are using the open-source xorg vid drivers), then someone might actually look at it, since it is open source. Nobody seems to want to support the binary drivers - shame on ATI and Nvidia for not releasing the source. The way to find out what is happening for those that have NO numlock response after a minute or so is to modify the syslog so you get a syslog that records all events. I used this entry in /etc/syslog.conf:

# All messages go here
*.* -/var/log/all

Use sudo vi /etc/syslog.conf, press i for insert, then paste (middle mouse) those two lines, then hit esc and :wq
you need to restart syslog with:
sudo /etc/init.d/sysklogd restart
You will have a new entry in /var/log/all and hopefully you will catch your hardware issue there. When your machine hard-locks, after you reset, look in this file. You will see your startup entries, look at the time and go to just before them. If you get to the top of the file, go to all.0, which is the log just before and keep browsing. There apears to be a bug that is in the Linux kernel that only seems to happen with some motherboards+amd64+dual processo+video card (i.e. duo-core) that is a hard lock. I know it happens with newer Nvidia cards, and it does not seem to happen with the i386 version. I am a Linux developer, and live with it on my machine. Unfortunately, I do not have time to track it down being too busy with my paid Linux work. Perhaps one day...

If anybody knows of a PCI/PCI-X video card that is not ATI/Nvidia and has an open-source driver, please tell. I'll support whoever they are by buying one of their cards.

Cheers

---

### Post by mpfleger on 2008-04-14
Hi all.

I have no idea if this is helpful to anyone, or not. If any of you are able to watch your machine start to lock up an correlate it to any demise of network connection, I'd be very interested in hearing about it. In my case it seems to be always preceded by a loss of network connection, and can be brought on pretty consistently and almost immediately when messing with the network ifaces, ie:
sudo /etc/init.d/networking restart

...anyway...

I've been following this thread, and a few others related to lockups and other odd behavior with Gutsy x86-64 installs. It seems that my combination of an AM2 CPU with an Nvidia video (onboard in my case) card is a somewhat regular player, but not *the* common denominator, in this thread. I'm running an ASUS M2N-VM DVI with 4GB of (tested) RAM and an AM2 processor of some sort in the 65nm process (4400+ maybe?). There's a Nvidia nForce 630A chipset in there if anyone was wondering.

I noticed that a number of other posts mentioned Firefox, downloads, YouTube, etc., all of which pointed to some potentially heavy network activity. This was the symptom of my lockups that made me read all 630+ posts in this thread for clues.

The big difference between my installation and others seems to be that I use Xubuntu x86-64 instead of Ubuntu x86-64. This takes a lot of extra stuff out of the picture for me, which had me looking more closely at the networking side of things, and in particular at things in my log that pointed to oddness to do with dhcdbd, as these reports describe:
[https://bugs.launchpad.net/ubuntu/+source/dhcdbd](https://bugs.launchpad.net/ubuntu/+source/dhcdbd)

Now; the description of dhcdbd pretty much lays out the fact that it relies on dhcp3-client for the grunt work of getting an IP address, etc. from the DHCP server. The potential downside of nuking this package is that it took:
1) network-manager (not recommended for servers, only for desktops (!))
2) gnome-network-manager 
3) xubuntu-desktop
-with it.

I'm downloading podcasts (what is almost always the culprit that kills my system) as I type this...

So there. I thought I'd toss that into the mix, since my board is close to what a number of others have posted about. If anyone gets anywhere with this, or finds funky networking related logs related to their crashes, please do let us know :)

Note that if I hauled the very same files down on my old PIII-600 and *then* scp'd them over to this box, there was no such issue =/

Whee!
M

EDITv2.0: moved to Hardy Beta, and again removed the above 4 packages after seeing the same behavior when doing large http downloads. The problem seems to have disappeared completely. I've been hauling down the same kind of files from the same podcast server, up to five at a time with no issues, whereas before I'd be lucky to grab one at a time.
[img]http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif[/img]

---

### Post by kevinmoire on 2008-04-15
I have this problem as well

AMd 64
2gb RDram

---

### Post by hotdoog on 2008-04-18
Hi, i tried the
clocksource=acpi_pm
fix and it just crashed on me again.:confused:

I've been running this new 64 bit OS for some days now and it only started freezing recently. Which is weird. I'm using CompizFusion but - I assumed it was that when it happened the second time. The first time I assumed it was my Virtualbox or how I shutoff my swap for that. However neither of those things fixed it as it kep crashing. So then I came upon this thread. I just did the clock thing and it seemed to have helped then it crashed. I do have Gnash installed but it might not be running... actually maybe it is in firefox. I'll kill that and check but i doubt that's it. I'm going to try the Hardy Beta to see if that solves anything. It mentions something about 64 bit clock issues on the main info page so I hope that will work!

I'll be back to say if it doesn't!

This just goes to show how badly supported the 64 bit chips are. This is a major major bug in my opinion (linux acting like windoze:(!) But I guess its not such a high priority since only some use it.

I actually JUST bought a new laptop. I was humming and hawing about getting a dell with intel chip or a compaq with amd64. I'm glad I chose the intel. I know AMD is supposed to be better than intel for some reason (people say evil inside instead of intel inside - i don't really know why or care to google it) but these kind of 64 bit issues are a pain in the rear!

On the other hand, This is my new 64 bit OS on a computer I've had for a long time. I was using 32 bit dapper for a long time on this machine because when I tried to go with Edgy 64 bit it was just too hard to get things like azureus and flash plugins to work - took all sorts of special tweaks and even then it didn't work for azureus. These days most things just install from synaptic without a hitch. So maybe these issues will be resolved sooner rather than later. We can only hope.

As I say - I'm migrating to Hardy tonight!  :guitar:

---

### Post by pinerob on 2008-04-27
Hi everyone,

This thread is so convoluted that it shows up on a lot of searches and in the interests of helping someone else who manages to get through this entire thread and still not find their answer (like me!...although it did help)...here's my contribution :) 

Situation: Install of Kubuntu Hardy 8.04 freezes / locks up when trying to read the hard drive partitions or trying to format the hard drive or trying to copy the system files.

Specs:
Asus M2A-VM mobo, with Athlon 64 X2 4800+ dual core, 2GB of memory, SATA 250 GB Western Digital Harddrive

Resolution:
1) Go into BIOS -> Advanced -> PCIPnP -> and set "Plug and Play O/S" to Yes. I'm not sure why this setting is defaulted to "No"...it would seem to me that you would want it to default to  Yes. 

2) On the boot (?) menu of the CD install. Basically, this is the menu where it asks you if you want to try out kubuntu w/o making any changes to your computer or if you want to install it....press F6 twice to bring up the additional boot options and select "acpi=no". I'm not sure if you have to highlight "Install Kubuntu" from the menu first before selecting F6 so you may want to do that though.

Cheers everyone! Here's to a 12 hr-install session :) (BTW it wasn't all related to the kubuntu install...there was a fried CPU involved at one point :( )

---

### Post by rotorcraig on 2008-04-30
I'm now firmly with Hardy.

I've been with the Beta for some time, recently reinstalled the Production version.  Applied various tweaks for performance gain eg disable IPv6, disable unnecessary [on my setup] daemon processes that run against the session by default, etc.

Desipte running nVidia restricted drivers and desktop effects, I do not get the "Gutsy-esque" freezes any more, period.

What I do get, for specific applications and usually when working with Firefox/Flash, is a "fade to grey and freeze for 30 seconds or so" but left alone that recovers, always.

So a much more stable setup on the same kit.  I do wonder:

- Whether more memory would increase stability? I have 512mb, top suggests it is generally in use but not really overused / no excessive paging going on.

- Whether an uprated or new power supply would help?  I once had stability issues under Windows that were resolved by swapping in a new power supply, I recently started wondering whether my power supply is getting noiser that in used to be (or are other PCs just getting quieter?) and talk here of underpowered supplies has got me thinking.

RC

---

### Post by ccc1 on 2008-05-01
> **mpfleger said:**
> I'm running an ASUS M2N-VM DVI with 4GB of (tested) RAM and an AM2 processor of some sort in the 65nm process (4400+ maybe?). There's a Nvidia nForce 630A chipset in there if anyone was wondering.


i have the same mainboard & also had lockups & freezes. Just change your network card, the internal card is broken. had freezes with windows xp too, then i bought a new network card disabled the internal one -> no more freezes!

ccc1

---

### Post by mrbamboo on 2008-05-04
I've had the same problem on my desktop.

It runs intel Core 2 Duo 64 bit cpu with 4GB of ram, nvidia 7950GTS video card.

For the past few months it ran Gutsy Gibbon 64bit version, and had random crashes usually when firefox is open, and when I'm playing a game like Team Fortress 2 or Warcraft 3 on wine. Switching to an older driver made the crash happen less often but not completely gone. I used envy to install the nvidia driver both times.

Just this week I did a fresh install of Hardy Heron, this time 32bit on the same machine. This time I installed the nvidia driver with the restricted driver instead of envy. I've had 1 crash so far while using openoffice. I just turned off all animation on compiz settings, I'll definitely comeback for an update if the crash happens again or if it doesn't crash for a week. The crashes I get are complete system freezes, my keyboard and mouse are both USB and they lose power (mouse optical light and keyboard led lights go off when crash happens), cannot ssh into the machine, must hard reboot.

My laptop has ran Feisty and Gutsy for a year and it has not had this problem. It runs intel Core Duo 32bit cpus, 1.5GB of ram, nvidia 7400Go video cards. Never crashed. It's part of the reason I installed 32bit version of Hardy Heron on my desktop with 64bit cpu, since that seems to be the only major difference between my desktop and laptop, but alas, it still crashed. :-/

Well I hope this information at least help someone else figure out the cause of this problem.

---

### Post by GrantsV on 2008-05-05
I installed Ubuntu on 3 PC as home.  One had ATI video card and kept locking between 1-30 minutes of use.  I tried 7.1 and 8.4, 32-bit version and same problem.  With and without ATI driver.

The good news - the machine has been running 100% flawlessly for one week after doing the following:

Uninstall processor scaling (sudo apt-get remove powernowd)
Disable BIOS APCI
Disable BIOS VGA RMA allocation (e.g. onboard video)

I'm not sure which of the 3 fixed it.

But now a week later, one of the other PC's is locking once every day??????!
I'm going to try the "remove powernowd" and see if that fixes it.

Btw, the 2 that have locked have AMD64 CPU's, the one thats ok is a laptop with Celeron.

---

### Post by keithyw on 2008-07-21
i finally got around to installing Flash 10 Beta 2 by hand.  Had one crash with Firefox 2.0.0.14 (I'm just wary of using Firefox 3 right now) with regards to Flash but only with Beta 1.  No system lock up though compared to before.  Flash 10 Beta 2 has some bizarre pixel issues, but I assume that has more to do with Flash than anything else (didn't see it with Beta 1).  When Flash uses the sound system on the browser, no other audio can play simultaneously.  On the other hand, I don't get system lock ups as I did in the beginning.

I still have compiz turned off as well as powernowd, which seemed to have caused issues earlier in terms of system lock ups.  But so far 2 day uptime with the Flash 10 Beta 2 install.

System is pretty much fully upgraded, except that I'm not using the latest kernel upgrade (I have to reboot my system).  Running Kubuntu with Hardy.  Main point though is that it seems the major system lock ups are gone now.   I'd be interested in hearing other people's experiences with Compiz now.

---

### Post by alex2035 on 2008-07-21
Daily freezes here, became boring and made me think dropping U8.04 to trash.
Now with  powernowd unabled (de-installed it) AND no Compiz, nor ATI-fglrx (de-installed it) rolled back to VESA, I have not yet experimented any freezes. 
Dont know about Opera or Firefox, they used to hang at the minute, I am giving them a try.


Compiz, NEVER worked for me on AMD and ATI, it messed everything up. It was better with Nvidia but not that much (6.06, 7.10 versions)

Yes, Pulseaudio went the bin route, I dont understand it, I dont care for it and it messes things up, I just want to hear music, and let me tell you, I am a recording engineer, give me mixing consoles, audio computers, macs, and what you like, but this Pulse? at least throw some help or faq with it! anyway, the machine is happy now.

---

