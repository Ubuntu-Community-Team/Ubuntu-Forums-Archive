---
title: "Hang AFTER everything loads up.."
date: 2006-04-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by eddjc on 2006-04-30
Hi everyone,
Sorry if this has been dealt with before - I looked through alot of threads, but couldn't find a similar one  -

I've just installed ubuntu on my old toshiba laptop (pentium II) - guaranteed old comp so not sure if this is the root of the problem..

Anyway, the installation seemed to work, if taking a long time - it rebooted without CD etc. and all was fine, then after the first boot installation bit was finished, it loaded up with the nice brown shiny "ubuntu" start screen and listed the modules loading etc, then it got to the end of that, and the screen went black but for one little white line in the top left blinking. The blinking stopped and it.... hanged. Nothing else happened.

I restarted it and the same thing happened (obviously going to the startup screen instead of install)

I can startup in recovery mode but that's about it... Any ideas?

One thing - I didn't have my network plugged in during install so didn't set up DHCP - consequently the system clock synchronising is the only thing that fails on startup - would this be the problem? In which case how to fix it without reinstalling?

Cheers;-)

Edd

---

### Post by codejunkie on 2006-04-30
[quote=eddjc]Hi everyone,
Sorry if this has been dealt with before - I looked through alot of threads, but couldn't find a similar one  -

I've just installed ubuntu on my old toshiba laptop (pentium II) - guaranteed old comp so not sure if this is the root of the problem..

Anyway, the installation seemed to work, if taking a long time - it rebooted without CD etc. and all was fine, then after the first boot installation bit was finished, it loaded up with the nice brown shiny "ubuntu" start screen and listed the modules loading etc, then it got to the end of that, and the screen went black but for one little white line in the top left blinking. The blinking stopped and it.... hanged. Nothing else happened.

I restarted it and the same thing happened (obviously going to the startup screen instead of install)

I can startup in recovery mode but that's about it... Any ideas?

One thing - I didn't have my network plugged in during install so didn't set up DHCP - consequently the system clock synchronising is the only thing that fails on startup - would this be the problem? In which case how to fix it without reinstalling?

Cheers;-)

Edd[/quote] it sounds like the video card isn't getting setup correctly by the xserver try booting into recovery mode when you get to the command line login and enter
```
sudo dpkg-reconfigure xserver-xorg
```under the driver section change the driver to ```
vesa
``` or if your card is listed there try it's driver first and reboot and try it again.

---

### Post by eddjc on 2006-04-30
ooooooooohhh yee baby!

thanks that worked superbly:-D

very much obliged!

although for some reason my screen size seems to be set at about a 3rd... how do you change this?

Cheers:-)
Edd

---

### Post by codejunkie on 2006-05-01
[quote=eddjc]ooooooooohhh yee baby!

thanks that worked superbly:-D

very much obliged!

although for some reason my screen size seems to be set at about a 3rd... how do you change this?

Cheers:-)
Edd[/quote]

Go to Applications/Accessories/Terminal and enter 

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Then

```
sudo gedit /etc/X11/xorg.conf
```

This will open the xserver configuration file scroll down to Section "Screen" it should look something like this 

```
Section "Screen"
    Identifier    "Default Screen"
    Device        "NVIDIA Corporation NV40? [Unknown nVidia Card]"
    Monitor        "COMPAQ FS760"
    [COLOR=Blue]DefaultDepth    24[/COLOR]
    SubSection "Display"
        Depth        1
        Modes        "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1024x768" "800x600" "640x480"
    EndSubSection
    [COLOR=Red]SubSection "Display"
        Depth        24
        Modes        "1024x768" "800x600" "640x480"
    EndSubSection[/COLOR]
EndSection
```

set the [COLOR=Blue]DefaultDepth to 24 [COLOR=Black]and[/COLOR][/COLOR][COLOR=Black] in the line contaning that Depth make sure the resolution you want to use is listed [/COLOR]under the Modes line, by default it will use the first resolution listed, so on mine it will use 1024x768 resolution with 24 bit color, save the file and reboot to see if this fixes it. if this doesn't work i'll need to know a little more about your computer like what kind of video card it has and i'll need you to post your /etc/X11/xorg.conf file here for me to take a look at.

---

### Post by eddjc on 2006-05-01
Thanks:-) I sorted it another way in the meanwhile, by going through the last one you mentioned, and on the basic config pretending I had a 17 inch monitor... Seems to work fine now, although it's all running a trifle slow - I imagine it's because I'm using vesa (would I be right in thinking this is either a kernel based graphics driver or a generic graphics card device?) - or it could just be because I have a slow computer. My graphics card (S3 Virge) was listed in the config, but as described above, it didn't work:-(

Any idea why? My comp is a toshiba 490XCDT laptop - specs are here:
[http://linux.toshiba-dme.co.jp/linux/eng/spec.php3?model=490XCDT](http://linux.toshiba-dme.co.jp/linux/eng/spec.php3?model=490XCDT)

and here:
[http://www.toshiba-europe.com/bv/computers/products/notebooks/satellitepro490cdt/product.shtm](http://www.toshiba-europe.com/bv/computers/products/notebooks/satellitepro490cdt/product.shtm)

Cheers:-)

Edd

---

### Post by theking2 on 2006-05-04
xserver-xorg is broken or not fully installed. now what?

---

