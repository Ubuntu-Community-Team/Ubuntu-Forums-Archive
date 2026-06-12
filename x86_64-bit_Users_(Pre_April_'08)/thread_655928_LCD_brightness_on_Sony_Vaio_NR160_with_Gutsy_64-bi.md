---
title: "LCD brightness on Sony Vaio NR160 with Gutsy 64-bit"
date: 2008-01-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by tkitzky on 2008-01-02
Has anybody had any luck with Gutsy x86_64 on a Sony Vaio laptop? I recently loaded the Ubuntu 7.10 64-bit on a Sony Vaio VGN-NR160E. The install went smooth. Even wireless worked out-of-the-box. (I experimented with the iwl driver, but went back to the ipw. Had a few issues with losing connectivity after several minutes and the ipw was working fine.) I had a few minor bowser issues (e.g. plugins mainly). I was able to install the 32-bit firefox which cleared up all the minor issues with flash. My wife is happy now.

The big problems I am dealing with on this laptop is screen brightness and function keys. Mainly, the screen brightness does not function. I cannot control the screen brightness from the desktop applet or power mgmt applet. I have found a few posts on Sony laptops using nvidia chipsets and installing the sony_acpi pkg on x86 systems. This laptop uses the Intel GM965 and I am using the Intel i810 driver. I have downloaded source for sony_acpi and installed modules in /etc/modules. (I've done a lot of things not sure exactly what was doing, though.) Also, I am not sure if I should be selecting a different LCD panel in the "Screen & Graphics" other that "Generic, Laptop 1280x800".

Second problem is function keys for screen brightness and suspend are not working. Function keys for volume up/down/mute are working, though. The hardware 'S1' and "AV Mode" buttons aren't working, but I can live with that. I knew I would lose some functionality when I stripped Vista off this.

Any ideas?:confused:

---

### Post by gn2 on 2008-01-02
Maybe try Xubuntu, it has a very simple way of adjusting screen brightness:

[IMG]http://i174.photobucket.com/albums/w109/gn1v/XubuntuDesktopSettings.png[/IMG]

Don't know if similar is available in Gnome, I haven't used it for over a year.

---

### Post by tkitzky on 2008-01-02
Thanks for the suggestion. I logged in using xfce session and tried adjusting screen brightness from desktop settings. The xfce display manager doesn't actually reduce the fluorescent backlight. It was adjusting the color saturation on the desktop. (e.g. Blue background went from pale blue to dark navy when brightness was adjusted down.)

---

### Post by tkitzky on 2008-01-02
Well, getting closer. Found from a google search that screen brightness should be handled by 'xbrightness' for Intel GM965 chips. (Thanks to Mattia Dongili who is the current maintainer for the sony-laptop driver.) I installed the xbrightness package and can now control screen brightness from the terminal. Now... how to get the gnome desktop applet or screen brightness applet to use this function.

From Mattia's web site, I believe the fn keys are an acpi event and so would be handled by the acpid daemon. I started the daemon but don't see any events triggered in the acpid log when I hit the fn-screenbrightness keys. I don't see any events when I hit the fn volume-up/down keys, either. Maybe acpi isn't at play here.

---

### Post by tkitzky on 2008-01-06
Ok... this appears to be a confirmed bug with Gutsy. Not sure if it is related to kernel 2.6.22.14_generic or x86_64 platform, or both. I'm compiling 2.6.23.12. Hopefully that will work.

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/152731](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/152731)

Also... correction to earlier post... the package I am using to control brightness is not "xbrightness"... it's "xbacklight" (e.g. sudo apt-get xbrightness). Use command "xbacklight -set 50" to set the brightness to 50%. It's the only thing that works for me.

---

### Post by coolbrook on 2008-01-08
I just got this laptop today.  It's my first real laptop.  I'm charging it up!  Personally, I'm already charged.  I have 64-bit Gutsy CD within arm's length.  What to do?,,,  What to do?  :mrgreen:

---

### Post by andresmontanez on 2008-01-24
I have the same model, Sony Vaio VGN-NR160E.
But when executing the xbacklight, the programs gives the
error that it can't find any device with the backlight property.

Did you solved it in other way?

Thx.

---

### Post by teutatis on 2008-01-24
I have the same problem with Sony Vaio VGN-FZ21M 
I have Nvidia Grafic driver and I tried 100 different ways with sony_acpi but non of them worked. 

Maybe somebody find a solution

cheers

---

### Post by oooh on 2008-03-06
no way with the brightness still, havent gone that far ...

but in my FZ21M I have this:

Everything OK but:

- wireless forgetfull settings after restart
- hibernation not well done
- had to use envy to get nvidia to work
- touchpad stoped to work during the envy installation
- block num / mayusc leds do not work
- jack out had to be mend using the backport stuff
- flash stuff not working still, because adobe's tar file tells me my x86_64 arquitecture is not supported (?!?!?)
- vol and so keys , inlcuding Fn do work, i get the interfaze pop in my window, but it makes nothing to the sound or whatever (it worked initially, but stoppped to work after a while ... ?!?!?!)

(sorry for the lack of details, I will also post this in a more general forum .... but with more details ....)

---

