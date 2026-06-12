---
title: "New ATI radeon fglrx driver release: 8.19.10"
date: 2005-11-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by Septor on 2005-11-12
Hi all, there is a new release of the ATI fglrx driver.  This is important for amd64 users because it addresses the drmMap failed problem in Breezy.  You can get the driver from [http://www.ati.com](http://www.ati.com) and follow the install howto at [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu) or [http://www.ubuntuforums.org/showthread.php?t=76116](http://www.ubuntuforums.org/showthread.php?t=76116) if you are courageous.

---

### Post by JuanC on 2005-11-12
When i type :

```

sh ./ati-driver-installer-8.19.10-x86_64.run --buildpkg Ubuntu/breezy

```

Works , no error messages , but i don't see any .deb package output

---

### Post by Septor on 2005-11-12
[QUOTE=JuanC]When i type :

```

sh ./ati-driver-installer-8.19.10-x86_64.run --buildpkg Ubuntu/breezy

```

Works , no error messages , but i don't see any .deb package output[/QUOTE]

Some people report that they end up in /tmp ... I don't know why, since they always end up in the current directory for me.

---

### Post by HiddenGhost on 2005-11-12
[QUOTE=JuanC]When i type :

```

sh ./ati-driver-installer-8.19.10-x86_64.run --buildpkg Ubuntu/breezy

```

Works , no error messages , but i don't see any .deb package output[/QUOTE]

Have the same problem. Nothing worx. I just made a clean install of Breezy and tried to get hardwareacceleration. 

If i process that file, it creates a tmp-folder and deletes it afterwards. Nothing more, nothing less. No debs and if i try to use the GUI Installer i get the same problems. Something installs, but fglrx wont be found anywhere, neither says the fglrxinfo string that it uses ati. Still software emulated GL everywhere!

---

### Post by superm1 on 2005-11-12
I'll be one to say that I love this release.

After I was able to enable PowerPlay, my fan finally works like it does in windows.  Also I can actually switch between a VT and X as well as suspend!

---

### Post by NickB on 2005-11-12
Didn't seem to fix the drmMap problem for me, but it worked fine when I used the old libdri.a file (as with 8.18).


Nick

---

### Post by toon on 2005-11-13
Greetings,

Does this new driver work with the composite manager? My card is a Radeon Mobility X600.

Oh, and hats off to the Ubuntuteam for very nice distribution :)

EDIT: I see I'm in the wrong forum (I don't have AMD64 hardware) - I tried deleting it but it seems I can't?

---

### Post by jecos on 2005-11-13
[QUOTE=toon]Greetings,

Does this new driver work with the composite manager? My card is a Radeon Mobility X600.

Oh, and hats off to the Ubuntuteam for very nice distribution :)[/QUOTE]
 
Read the release notes.. and
Don't expect ATI's driver to have composite support until composite manager is stable.  Its not worth the time to work on something thats still unstable when they have bigger features to work on.

---

### Post by toon on 2005-11-13
[QUOTE=jecos]Don't expect ATI's driver to have composite support until composite manager is stable.[/QUOTE]
Okay.. Any idea when that might happen? :)

---

### Post by jecos on 2005-11-13
[QUOTE=JuanC]When i type :

```

sh ./ati-driver-installer-8.19.10-x86_64.run --buildpkg Ubuntu/breezy

```

Works , no error messages , but i don't see any .deb package output[/QUOTE]

Don't generate pkgs just install it.  MAKE SURE YOU DON'T HAVE LINUX-RESTRICTED-MODULES PACKAGES INSTALLED(they will overwrite the new drivers).

---

### Post by Septor on 2005-11-13
[QUOTE=jecos]Don't generate pkgs just install it.  MAKE SURE YOU DON'T HAVE LINUX-RESTRICTED-MODULES PACKAGES INSTALLED(they will overwrite the new drivers).[/QUOTE]

Bad advice... won't work on Breezy amd64 systems.  The ati installer expects /usr/lib and /usr/X11R6/lib to be the 32bit directories, but in Ubuntu they are 64bit ones.  In the best case 32bit apps (i.e. all games) won't run, and in the worst case you won't get X to start.  Please stick to a howto on 64bit systems.

---

### Post by almahtar on 2005-11-13
I hope this works, I've been running with "noaccel," and it's really slow.

Should I download the installer, or the link next to "X.org 6.8"?

(Breezy AMD64, fresh install)

---

### Post by actinium on 2005-11-14
Hello, 

I just tried it on my laptop and it works fine, i am running athlon64 3000+ and a radeon mobility 9000. I followed the instructions repackaging them and everything run as expected, there is still the problem with int10 and libdri.a files though. Its better than the 8.16 release that came with breezy because if i use the ATI drivers for that it refuses to display 1400*1050. I couldn't install 8.18 because of some compliling error.

almahtar: just download the full install

Regards, 

Alan

---

### Post by teme82 on 2005-11-14
Hmm... just installed clean installation of breezy 5.10 AMD64 and apt says that there is no package named module-assistant ... weird... since i cant install that package i cant use X... and it s******

[EDIT] Universe packages were disabled :D no it installed the drivers but geting module load error from x server...
> 
Duplicate symbol rol_long in /usr/X11R6/lib/modules/drivers/fglrx_drv.o
Also defined in /usr/X11R6/lib/modules/linux/libint10.a


---

### Post by Septor on 2005-11-14
[QUOTE=teme82]Hmm... just installed clean installation of breezy 5.10 AMD64 and apt says that there is no package named module-assistant ... weird... since i cant install that package i cant use X... and it s******

[EDIT] Universe packages were disabled :D no it installed the drivers but geting module load error from x server...[/QUOTE]

You need to comment out the int10 module in your xorg.conf's Module section.

---

### Post by teme82 on 2005-11-15
[QUOTE=Septor]You need to comment out the int10 module in your xorg.conf's Module section.[/QUOTE]
I did that, now it says no screens found... :(

---

### Post by Septor on 2005-11-15
[QUOTE=teme82]I did that, now it says no screens found... :([/QUOTE]

Post your /etc/X11/xorg.conf, there must be something else wonky there.  Check the output of /var/log/Xorg.0.log as well.

Also, what card do you have?  If it is too new, it might not be supported yet...

---

### Post by teme82 on 2005-11-15
[QUOTE=Septor]Post your /etc/X11/xorg.conf, there must be something else wonky there.  Check the output of /var/log/Xorg.0.log as well.

Also, what card do you have?  If it is too new, it might not be supported yet...[/QUOTE]
The card is X800 GTO (R480 core). That might bee the reason...

[EDIT] fglrxinfo says that no displays found, so must wait the next drivers to see if ATI add support for X800 GTO ... and if someone knows some one in ATI's linux driver team do let him know about this :)

---

### Post by Septor on 2005-11-16
[QUOTE=teme82]The card is X800 GTO (R480 core). That might bee the reason...

[EDIT] fglrxinfo says that no displays found, so must wait the next drivers to see if ATI add support for X800 GTO ... and if someone knows some one in ATI's linux driver team do let him know about this :)[/QUOTE]

What is the PCI ID of your board?  You can find out with "lspci -v" and "lspci -n".  Also please post your failed Xorg.0.log, I'm curious as to where exactly it is failing.

---

### Post by n0gabor on 2005-11-16
I have X800 GTO (r480) too, i've installed the drivers 3 different ways, but it still doesnt work:

-the fglrx package with apt-get
-with the ati installer
-with .deb packages generated for ubuntu breezy by ati installer

the bulid/install process was successful all times, but the same error occured after fglrxconfig and reboot:

when X starts, the computer freezes, blank screen comes, and only reset can help:mad: 

that meens ATI driver doesn't support X800GTO?

its interesting, becouse its the same as X850 pro, but the mem and core clocks are slower (can be solved with a little tuning;) ), and in the release notes ATI says that the X850-s are supported by the new drivers...


i'll post the  /var/log/Xorg.0.log ...

---

### Post by teme82 on 2005-11-16
[QUOTE=Septor]What is the PCI ID of your board?  You can find out with "lspci -v" and "lspci -n".  Also please post your failed Xorg.0.log, I'm curious as to where exactly it is failing.[/QUOTE]
here's the log, had to pack it :D it seems that it' too big for forums as normal txt
[EDIT] lspci -v id one  VGA Compatible ATI unknown device

---

### Post by JuanC on 2005-11-17
My ATI card Xpress 200M don't work with ATI drivers :
```

$ fglrxinfo
libGL error: drmMap of sarea failed
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```

Anyone has an ATI Xpress 200M ?

---

### Post by Septor on 2005-11-17
[QUOTE=JuanC]My ATI card Xpress 200M don't work with ATI drivers :
```

$ fglrxinfo
libGL error: drmMap of sarea failed
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```

Anyone has an ATI Xpress 200M ?[/QUOTE]

I tihnk you are hitting the drmMap problem... read this bug: [http://ati.cchtml.com/show_bug.cgi?id=198](http://ati.cchtml.com/show_bug.cgi?id=198)

There is a fixed libdri.a that you can use to workaround the problem.

---

### Post by Skatox on 2005-11-17
I installed my generated packages with aptitude, and it automatically uninstalled linux-restrictecd-modules.

---

### Post by JuanC on 2005-11-18
[QUOTE=Septor]I tihnk you are hitting the drmMap problem... read this bug: [http://ati.cchtml.com/show_bug.cgi?id=198](http://ati.cchtml.com/show_bug.cgi?id=198)

There is a fixed libdri.a that you can use to workaround the problem.[/QUOTE]

It Works !!! , Thanks.

```

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200M Series SW TCL Generic
OpenGL version string: 1.3.5461 (X4.3.0-8.19.10)

```

---

