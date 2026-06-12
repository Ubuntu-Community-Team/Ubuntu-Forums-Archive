---
title: "nVidia accelerated graphics driver (version 177)"
date: 2008-11-02
forum: x86 64-bit Users
---

### Post by caladan1810 on 2008-11-02
Hi Everyone, I've just installed Ubuntu 8.10-the Intrepid Ibex [64bit]. I managed to get the WiFi Drivers and network card drivers working. 
However it Won't install nVidia accelerated graphics driver (version 177) recommended.

I go to the Hardware Drivers applet and select to activate the following:
nVidia accelerated graphics driver (version 177) recommended.

I then authenticate with my password for my user account and it then flashes up a box which appears to request a download and 
then disappears and does nothing.

Any Help would be greatly appreciated.

thanks in advance

---

### Post by BrokenPoet on 2008-11-02
I am having a similar problem with similar hardware (Dell XPS M1530, Amd64 install).  I tried removing and re-installing the 177 driver, and now cannot get any restricted drivers to appear in the 'Hardware Drivers'.

Any thoughts/advice?

---

### Post by caladan1810 on 2008-11-02
**Update**

I went to Add/Remove on the menu and selected the nVidia accelerated graphics driver (version 177) to be installed.

Once installed I went back to the Hardware Drivers applet and selected to activate and it said was activated and in use. However the nVidia X Server Settings says:

You do not appear to be using the NVIDIA X driver. 
Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

[B]**Update - 2**
After logging out and back in again I did not need to login as root and everything works great ALL OK![/B]
I even have Dual Screens running in TwinView Mode.

---

### Post by bford16 on 2008-11-03
To sum up, then:

In order to install and activate NVIDIA drivers on Intrepid, uninstall all NVIDIA drivers, then reinstall the 177 driver. Reboot.

---

### Post by BrokenPoet on 2008-11-03
Thank you for the response.  I have removed all Nvidia drivers and reinstalled twice.  On both occasions it results in the driver being installed (NVidia binary X.Org driver ('version 177' driver) appears in Add/Remove Programs), but no options are listed under 'Hardware Options'(e.g. The Hardware Options window has no drivers listed at all, with a statement that 'There are no proprietary drivers in us on this system'.)

I have the following installed in Synaptic:
nvidia-177-kernel-source
nvidia-glx-177
nvidia-kernel-common
nvidia-settings
xserver-xorg-video-nv

System was upgraded from 8.04.1, video card is an 8600GT

I will attempt the remove/reinstall cycle again this evening, unless any other suggestions are forthcoming.  Thanks!

---

### Post by Fhernd on 2008-11-13
Hi!

Thanks/Gracias **caladan1810**. I followed your steps and my NVIDIA GeForce7300 works fine.

I'm enjoying Ubuntu Ultimate ver. 2.0 (Intrepid Ibex) and programming on Java.

Bey!

---

### Post by anandchakru on 2008-11-18
I faced the same problem, but I think I resolved it by checking "Authenticate for this session" checkbox when typing the root password :) simple !!! :lolflag:

---

### Post by marttali on 2008-11-19
BrokenPoet, have you managed to get nvidia working, i have the same card- no success so far :(

---

### Post by dabl on 2008-11-19
Not that it has anything to do with "64-bit", but ....

EnvyNG works really well, in general, although there's a special problem with dual cards (SLI), for which you need to enter the PCI bus ID's in the "screen" section of xorg.conf.  Here's the process for Kubuntu, the only difference for Ubuntu is that you use "gdm" instead of "kdm":

[http://kubuntuforums.net/forums/index.php?topic=3098672.msg152816#msg152816](http://kubuntuforums.net/forums/index.php?topic=3098672.msg152816#msg152816)

Also, FYI, Nvidia has released a beta 180.06 driver, and it's getting very good reviews from *buntu 8.10 users -- you might want to give it a try, but you'll have to use the downloaded installer/driver package because it is not in EnvyNG.  Don't forget to first install the linux-headers-`uname -r` and build-essential packages:

[http://kubuntuforums.net/forums/index.php?topic=3099412.0](http://kubuntuforums.net/forums/index.php?topic=3099412.0)

HTH  :)

---

### Post by jhj614 on 2008-12-05
> **caladan1810 said:**
> Hi Everyone, I've just installed Ubuntu 8.10-the Intrepid Ibex [64bit]. I managed to get the WiFi Drivers and network card drivers working. 
However it Won't install nVidia accelerated graphics driver (version 177) recommended.

I go to the Hardware Drivers applet and select to activate the following:
nVidia accelerated graphics driver (version 177) recommended.

I then authenticate with my password for my user account and it then flashes up a box which appears to request a download and 
then disappears and does nothing.

Any Help would be greatly appreciated.

thanks in advance

I had the same problem and tried many times without being able to have it activated.  It worked all of a sudden today when I was ready to give it up and try other tricks.  The activation was successful and I just had to reboot the machine.  Looks like one just needs to do it n+1 times...

---

### Post by corman420 on 2008-12-11
I also had this issue. I would click ACXTIVATE, it would ask for my password, and then nothing...

I figured out it was because I updated my etc/apt/sources.list file... I switched it back to my default one and it worked...

---

### Post by chkh on 2009-01-17
Guys,

I've followed your steps carefully but when i restart it takes me into the tty1 mode. i'm new to ubuntu and i dont know how to get myself back into the desktop. i'm facing the same problem and i dont think that it is resolved.

I've already added version 177 and was told to restart, and here i am now in the tty1 mode.

Please Advice :)

---

### Post by Creativia on 2009-02-13
I was just having the same problem, plus something else. (solved)

Problem 1: I activate version 177, authenticate, but then it would just close without actually downloading or activating.

Solution 1: I was installing updates at the same time, basically should have gotten the error: another synaptic is running.  I waited until updates were finished and it then worked fine.

Problem 2: After it worked and I restarted, my screen would just go black instead of seeing the login screen.  'No signal input' on the monitor.  
I tried restarting, going into the recover mode, fix the x server.  Then started up (now without the driver activated) and then tried to install version 173, same problem..

Solution 2: I had my lcd tv plugged into the vga.  My monitor is dvi.  Duh!  It was defaulting to the vga as the primary display.  I unplugged the vga, restarted, problem fixed.

---

### Post by mrdaze0 on 2009-02-13
> **chkh said:**
> Guys,

I've followed your steps carefully but when i restart it takes me into the tty1 mode. i'm new to ubuntu and i dont know how to get myself back into the desktop. i'm facing the same problem and i dont think that it is resolved.

I've already added version 177 and was told to restart, and here i am now in the tty1 mode.

Please Advice :)

hit {ctrl}{alt}{f7} should start an X session for you and give you a gnome log in

---

### Post by bigmunkey3741 on 2009-02-18
im having a similar issue too.. *im a total limux n00b -_-*

I installed 8.10, all fine.. installed all current updates.. fine...

everytime i install the 177 nvidia driver, all i get it the please login commant screen -_-;

is there any way of just uninstalling the driver using the command window in rocovery mode??

thnks in advance for any help ^_^

---

### Post by Discombobulated on 2009-02-20
If you have both onboard nvidia graphics AND an nvidia card, you might find this helps: 

 [http://ubuntuforums.org/showthread.php?p=6580907#post6580907](http://ubuntuforums.org/showthread.php?p=6580907#post6580907)

Otherwise, if you're stuck with the tty1 login (black) screen, try logging in there and typing:

```
more /var/log/Xorg.0.log
```

Look at entries marked 'EE' for clues as to why X is not starting.

---

### Post by Wolfhere on 2009-02-21
Try starting up in low graphics mode..

Have you tried installing envng and envyng-qt ? After installing these two packages from synaptic, at the terminal type:
sudo envyng -g 
you should get a gui which lists the current drivers, select enabled for the 177.82 which is compatible and recommended.
I ran into similar problems when installing the 180 drivers.

---

