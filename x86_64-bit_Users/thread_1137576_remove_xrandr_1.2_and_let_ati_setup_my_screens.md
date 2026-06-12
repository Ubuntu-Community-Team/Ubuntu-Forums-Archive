---
title: "remove xrandr 1.2 and let ati setup my screens"
date: 2009-04-25
forum: x86 64-bit Users
---

### Post by h3ad73 on 2009-04-25
Hi,

i just upgraded to 9.04 from 8.10 and after installing ati drivers "fglrx" i tried running aticonfig --dtop=horizontal i get a message saying that the command cannot be ran because RandR 1.2 is enabled. How can i disable randr? i currently have my dual monitor setup but when i maxamize a window it spans the window across both monitors i want to change that to only expand on one screen. any help or suggestions would be appreciated. if other info is needed let me know.

Thanks.

---

### Post by ToeBee on 2009-04-28
I ran into the same problem last week and was just trying to remember how I did it because a coworker wanted to know. So for your and his benefit...

Edit /etc/ati/amdpcsdb
In the section labeled [AMDPCSROOT/SYSTEM/DDX]
add this:
```
EnableRandR12=Sfalse
```

Also, in /etc/X11/xorg.conf in the "Device" section add:
```
Option      "EnableRandR12" "false"
```

Hope that helps.

---

### Post by ssri on 2009-05-09
thanks!  xrandr affected dpms on my system, rendering it useless.  Now powerdevil can finally turn off the backlight of my laptop! :guitar:

---

### Post by petermp on 2009-05-27
Thanks! This worked like a charm!!

---

### Post by Keithus on 2009-06-17
Yay!  At Last!  Finally, finally, finally!  After all the cuss words, and hair-pulling, and general frustration in trying to get the amdcccle to work for me, this thread has given me the information I needed!  Little did I know that RandR was working away in the background to sabotage my attempts to make dual screens work properly, but now that it is disabled everything works just how I want it to!  Very many thanks for this extremely useful information!  Linux users are the best!

---

### Post by markbuntu on 2009-06-19
Just so everyone knows, this is a problem with ati drivers from 9.4 on and with any Ubuntu the fix above works. I just installed the 9.6 driver on my UbuntuStudio amd64 Hardy and turned off xrandr with the xorg.conf option to get my dual monitor big desktop.

The 9.6 driver also works with the rt kernel, which previous drivers did not due to a missing and then misplaced rt patch.

---

### Post by Vyresince on 2009-10-10
So I know this thread is a bit old, but this fix is NOT working for me and it's driving me mad. I do as suggested above, but somehow EnableRandR12 keeps getting automatically set back to true!!! For example: 

> :~$ grep Rand /etc/ati/amdpcsdb 
EnableRandR12=SFALSE 
:~$ sudo aticonfig --dtop=horizontal,reverse 
Error: Options, e.g. --dtop and --desktop-setup, are not supported when RandR 1.2 is enabled! 
Using /etc/X11/xorg.conf Saved back-up to /etc/X11/xorg.conf.fglrx-6 
:~$ grep Rand /etc/ati/amdpcsdb 
EnableRandR12=STRUE   Does anyone have any idea why this utterly bizarre behavior is occurring? I'm desperate to have something as simple as my desktop being extended to the left WITHOUT all of my toolbars being on the left monitor. I'm completely floored that I've spent about 4 hours attempting to do this and have had no luck. It really blows my mind that it's not a simple option in the Catalyst GUI. But I think if I can get aticonfig to work then I'll be good. I'm using Ubuntu 9.04 by the way.

---

### Post by Vyresince on 2009-10-10
UPDATE: I can disable xrandr12 if I use /etc/init.d/gdm stop to stop X, make the options changes in xorg.conf and amdpcsdb, then start X again.


However, now I have huge swathes of screen that are not visible.  My cursor as well as files and windows can get lost in this area that's below by bottom toolbar and the the right of my right monitor.  Any ideas?!

---

### Post by helliewm on 2009-10-11
I have an ATI 4850 Card using fglrx. 2 VGA monitors with resolutions of 1680 1050 and 1440 900. I followed the instruction in this thread. I now have the resolution correct across the 2 monitors. However amdcccle-ATI Catalyst Control is only detecting one monitor and they are mirroring each other.
System, preferences, display dpes not work (which I expected having following the instruction is this thread) so cannot turn off mirrored monitors that way.

How can I turn off mirroring and why is Amdccle-Ati Catalyst Control only picking up one monitor?

Xinerama is grayed out in ATI Catalyst Control.

Helen

Ps I am using Karmic and install ed fglrx drivers by Karmic Hardware Drivers

---

### Post by josephdaniel on 2009-10-29
ToeBee,

Thanks a million. Xrandr was my biggest problem in getting my screen to follow the modlines I had specified in xorg.conf. I was really annoyed by this for a sometime now.

Thanks.

---

### Post by h3ad73 on 2009-10-29
you can trying running the command "sudo aticonfig --dtop=horizontal"

---

### Post by thierrybo on 2009-11-07
Thanks a lot, now CCC display all supported modes! However I have to choose the right resolution/refresh rate each time I open a session, settings are not saves after the Xrandr tweak.

---

### Post by jetpeach on 2009-11-09
wow, what a pain - i fiddled around for a long time trying to get the xorg.conf file to set the vertical refresh. but i guess this bug just means the fglrx drivers don't listen? i tried disabling the xrand but that didn't work for me either...

finally decided to just put a script in my .kde/Autostart folder that runs 
"
xrandr -r 60
"
that sets the refresh to 60 (needed for my lcd, before it was 75 and runs on startup.

do others have this working in karmic though? my hack of a solution is kinda lame but nothing else seemed to work....

---

