---
title: "Is nvidia-glx working for anyone on AMD64?"
date: 2005-06-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by KRavEN on 2005-06-09
I've been fighting with this one for days now.  Has anyone else been able to get the nvidia-glx package working for AMD64?  I can get the driver itself to work only if I go into the xorg.conf file and comment out the load glx statement.  This of course negates the entire point of running the nvidia driver though.  I even compiled the nvidia amd64 driver from nvidia and got the same exact results.

The only way I can get X to load with the glx loading is using the nv driver.  I also tried not loading dri according to the nvidia README but this causes X to not load at all using any driver.  Loading dri with the nvidia driver and glx off works fine.

The only indication in my logfile that I get is some missing symbols in the dri libraries but I get these even when using the nv driver.

---

### Post by hammett111 on 2005-06-09
Yes I am running an AMD64 system with kernel 2.6.10-5-amd64-k8 and I have it running.  First mate, tell me exactly what you have done. 

If you have installed the driver from Nvidia I suggest you completely uninstall it, by typing sh *name of the driver*.run --uninstall it will then remove itself, just follow the instructions.

Then edit your xorg.conf and change nvidia to nv (if you havent already). Boot back into X

Go into synaptic/kynaptic (if you use KDE I suggest dowloading synaptic at a later point). Do a search for nvidia and UNINSTALL nvidia-glx-dev, nvidia-glx, and nvidia-settings. Shut down synaptic/kynaptic and then REINSTALL the buggers again. Once they are go into the terminal and type:

            nvidia-glx-config enable

Go into xorg.conf, change nv to nvidia and add these to you xorg at the bottom of your Device section -

            Option                        RenderAccel                 true
            Option                        NvAGP                           2

Save
Restart Comp
and YEAH you cooking with gas!!!!!!!!!!!!!!!!!!

Hope it helps

---

### Post by KRavEN on 2005-06-09
[QUOTE=hammett111]Yes I am running an AMD64 system with kernel 2.6.10-5-amd64-k8 and I have it running.  First mate, tell me exactly what you have done. 

If you have installed the driver from Nvidia I suggest you completely uninstall it, by typing sh *name of the driver*.run --uninstall it will then remove itself, just follow the instructions.

Then edit your xorg.conf and change nvidia to nv (if you havent already). Boot back into X

Go into synaptic/kynaptic (if you use KDE I suggest dowloading synaptic at a later point). Do a search for nvidia and UNINSTALL nvidia-glx-dev, nvidia-glx, and nvidia-settings. Shut down synaptic/kynaptic and then REINSTALL the buggers again. Once they are go into the terminal and type:

            nvidia-glx-config enable

Go into xorg.conf, change nv to nvidia and add these to you xorg at the bottom of your Device section -

            Option                        RenderAccel                 true
            Option                        NvAGP                           2

Save
Restart Comp
and YEAH you cooking with gas!!!!!!!!!!!!!!!!!!

Hope it helps[/QUOTE]


Okay, I've done all you say a few times, but I use apt-get and dpkg -P to put stuff in and get stuff out.  I'm even running the same kernel (right now at least, I've tried the others just to be sure.  I think nvidia-glx installs the generic kernel as a dependancy though)

Right now I'm at the state with all nvidia references dpkg -P from my system and I did the --uninstall on the nvidia driver script as well.

The new info you're giving me though are the options at the bottom which I havn't had before.  I'll re-install nvidia-glx again and put those in as soon as I get home and cross my fingers.  


Thanks for your assistance and I'll let you know how it goes.

---

### Post by KRavEN on 2005-06-09
Still doesnt' work.  Same exact results.   Did find some things out though:

If you want to run with the k8 kernel you must install the restricted modules for that kernel.  Also, nvidia-glx lists the generic kernel as a dependancy.  Don't think it really shoudll be, shoudl prob check to see what kernel you're running and then install the restricted modules if you don't have them.

Second your options won't go in like you gave them.  They must be like this to be recognized:

Option "RenderAccel" "true"
Option "NvAGP" "2"


If anyone has anything else I could try please let me know.  I have no idea why it won't load with the glx module enabled.  I don't get any EE errors in the log file.  IU just get exited with signal 11 and a black screen telling me to check the log.

---

### Post by KRavEN on 2005-06-10
I ended up giving up on AMD64 version and going to i386.  It's just not worth it for all the headaches I've been going through to get the simplest things to work.  

Hopefully the developers will take a little more time with the AMD64 version to make sure it all works in breezy.

Once I put i386 ubuntu on I did apt-get nvidia-glx, did the nvidia-glx-config enable, went single user than back to init 5, everything is golden.  Didn't have to change the xorg.conf file at all.  

Under the AMD64 version the nvidia-glx-config enable script never did anything to my xorg.conf file except back it up.  Never changed the driver to nvidia or anything.  The i386 version did change it from nv to nvidia.

---

### Post by AllenGG on 2005-06-11
note to Hammett:
have a similiar set up, used your suggestion:
>terminal> nvidia-glx-config enable; >restart
worked great ! thanks
BUT, since nvidia-glx was already loaded (and now it shows on startup)
wonder why it wasn't "showing" before?, the changes are very slight,

Note to Kraven,  this was updated using Synaptic, so a lot of the controls were automatic, ie, removing, updating, upgrading etc.

also using a digital monitor, 256 meg video ram

atb,  Allen

---

### Post by gheorghe_pop on 2005-08-18
Check this maybe it will help:
[http://www.ubuntuforums.org/showthread.php?p=307921#post307921](http://www.ubuntuforums.org/showthread.php?p=307921#post307921)

---

### Post by tseliot on 2005-08-18
Why don't you try my HOWTO? It's very easy

[http://www.ubuntuforums.org/showthread.php?t=57368](http://www.ubuntuforums.org/showthread.php?t=57368)

---

### Post by DancingSun on 2005-08-18
[QUOTE=KRavEN]I ended up giving up on AMD64 version and going to i386.  It's just not worth it for all the headaches I've been going through to get the simplest things to work.  

Hopefully the developers will take a little more time with the AMD64 version to make sure it all works in breezy.

Once I put i386 ubuntu on I did apt-get nvidia-glx, did the nvidia-glx-config enable, went single user than back to init 5, everything is golden.  Didn't have to change the xorg.conf file at all.  

Under the AMD64 version the nvidia-glx-config enable script never did anything to my xorg.conf file except back it up.  Never changed the driver to nvidia or anything.  The i386 version did change it from nv to nvidia.[/QUOTE]
Did you install the nVidia drivers from nVidia's website?  I use Ubuntu 64 and I installed the nVidia drivers via Synaptic, followed the install guide in amd64.ubuntuguide.org, everything worked without problems for me.

---

### Post by tseliot on 2005-08-18
The nvidia driver you can can in Synaptic is 7174 version. It didn't work with my Geforce 6200 PCI-E. For this reason I recommend at least 7667 in my HOWTO, it's just more compatible with the latest graphic card.

---

### Post by brentoboy on 2005-09-27
[QUOTE=tseliot]The nvidia driver you can can in Synaptic is 7174 version. It didn't work with my Geforce 6200 PCI-E. For this reason I recommend at least 7667 in my HOWTO, it's just more compatible with the latest graphic card.[/QUOTE]

I followed that howto for my geforce 6200 pci-e card and it did wonders.  The only side effect is that sometimes when breezy updates my kernel, I have to rerun the script installer from nvidia to restore my stability.  And lataly, I am noticing that they update the kernel quite frequently (what you do expect from a pre-release)

If you dont like playing with it, stick with the synaptic version, at least it updates itself with no messing around, but if you want the good stuff, get the drivers from nvidia directly... just become familiar with it, becuase you'll end up doing it more than once before it is all said and done.

---

### Post by DancingSun on 2005-09-28
[QUOTE=brentoboy]I followed that howto for my geforce 6200 pci-e card and it did wonders.  The only side effect is that sometimes when breezy updates my kernel, I have to rerun the script installer from nvidia to restore my stability.  And lataly, I am noticing that they update the kernel quite frequently (what you do expect from a pre-release)

If you dont like playing with it, stick with the synaptic version, at least it updates itself with no messing around, but if you want the good stuff, get the drivers from nvidia directly... just become familiar with it, becuase you'll end up doing it more than once before it is all said and done.[/QUOTE]
Did you need to uninstall and reinstall the driver?  What do you mean by script installer (or did you mean installer script)?

---

