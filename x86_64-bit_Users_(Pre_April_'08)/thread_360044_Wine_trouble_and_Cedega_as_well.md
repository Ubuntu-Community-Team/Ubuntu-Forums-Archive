---
title: "Wine trouble and Cedega as well"
date: 2007-02-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by czechplz on 2007-02-12
hey. 
i just built this machine this weekend and have been a debian user for a few years. i had my ttroubles with debian but i was able to get threw or around them fairly easy. when i bought this  computer i upgraded to 64bit intell Core 2 Duo processor e4300. i got a Nvidia GeForce 7950 GT and the MSI 975X platinum MB. 2gig ram 2 250 gig HDD's one is Sata one is Pata. 
Debian has a huge problem with my onboard ethernet card..and a sulution was not anywere i could find, so i was directed to Ubuntu. i installed Ubuntu with no problem. have trouble with the Nvidia drivers..but i found a work around that i think is working. but wine is not being so nice. i tried your sulutions on you forums with no avail...im very new to Ubuntu and im more of a user on linux..not a Programmer and i lack some knowledge with some thing.
im more and willing to provide any info needed to get these problems fixed

error output that wine puts out is 
$ winecfg
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!

and i went threw what your forums say to fix...is there something i missed?
im not sure on how to remove a install..i installed from source so info on that as well would help.

Cedega also has problems. it cannot connect to the server it uses to DL the updates it needs...i know Cedega is a 32 bit program..and im not sure on how to get the work arounds to make it work

i had a theory taht maybe i just install a 32bit os on this machine?  maybe taht would help with my problems? im not oo sure if im loosing a lot of power by usung 64 bi sence a lot of programs use 32 anyway..im not even sure if i can run a 32bit os.... im used to my old AMD t-bird

any help in this would be greatly appreciated

thx 
Cz

---

### Post by Nythain on 2007-02-12
what is this workaround for the nvidia driver you used... i know its a hassle to reinstall every time you upgrade your kernel, but i would highly recomend installing the package from thier site... i have never had good luck with the repo or automatix in this area. and the nvidia package does a good job of removing any traces of previously installed drivers... i am known to reinstall drivers every so often just because i did something that jacked x up

as for cedega not connecting to the server for the engine update... does transgaming site have a link to download the most current engine... if so, download it, then install local engine, and point it in the direction of where you downloaded to... i havent actually ever tried to connect to the server to get update that way

hope any of that helps... if you could post more info, like if the net in general is working, firewall??? router??? xorg.conf... might be able to help more

---

### Post by Kilz on 2007-02-12
> **czechplz said:**
> hey. 
i just built this machine this weekend and have been a debian user for a few years. i had my ttroubles with debian but i was able to get threw or around them fairly easy. when i bought this  computer i upgraded to 64bit intell Core 2 Duo processor e4300. i got a Nvidia GeForce 7950 GT and the MSI 975X platinum MB. 2gig ram 2 250 gig HDD's one is Sata one is Pata. 
Debian has a huge problem with my onboard ethernet card..and a sulution was not anywere i could find, so i was directed to Ubuntu. i installed Ubuntu with no problem. have trouble with the Nvidia drivers..but i found a work around that i think is working. but wine is not being so nice. i tried your sulutions on you forums with no avail...im very new to Ubuntu and im more of a user on linux..not a Programmer and i lack some knowledge with some thing.
im more and willing to provide any info needed to get these problems fixed

error output that wine puts out is 
$ winecfg
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!

and i went threw what your forums say to fix...is there something i missed?
im not sure on how to remove a install..i installed from source so info on that as well would help.

Cedega also has problems. it cannot connect to the server it uses to DL the updates it needs...i know Cedega is a 32 bit program..and im not sure on how to get the work arounds to make it work

i had a theory taht maybe i just install a 32bit os on this machine?  maybe taht would help with my problems? im not oo sure if im loosing a lot of power by usung 64 bi sence a lot of programs use 32 anyway..im not even sure if i can run a 32bit os.... im used to my old AMD t-bird

any help in this would be greatly appreciated

thx 
Cz

With wine, the err:imagelist:ImageList_ReplaceIcon no color! error is saying it cant find an icon for a link. This is easly fixed by riight clicking on the link, then properties, clicking the icon in the properties box and choosing one
The "The X11 driver is missing.  Check your build!" sounds to me  that you may need to install the proprietary video driver for your card.

As for Cedega, the newest small deb's work on all versions. You can go to the Cedega web site and get the latest updates and do a local upgrade.

If you think that by installing a 32bit os you can avoid some setup, forget it. No version of linux exists that you dont have to do some setup. Anyone suggesting that the 32bit version will work without problems is lieing. Take a look at this forum, most (if not all)of the people posting problems in other sections have 32bit installs.

---

### Post by czechplz on 2007-02-12
im currently using the Ubuntu Driver for my gfx card. i tried the driver from Nvidia..and i get that classic "no screens" error i used to get back when i ran Fedora.. should i manualy edit my xorg cfg and not use the nvidia editor?

---

### Post by FrozenFOXX on 2007-02-12
If you're using an nVidia graphics card and wish to use the closed source drivers here's what I did.

Start up ubuntu, hit F6 at the boot screen and enter "single user" (Or something similar to that, might be "single" but you get the idea).  This will start Ubuntu up in the command prompt which generally is a good thing for what we're about to do.

Log in as usual and type "cd /etc/X11/." After that fire up your favorite editor to edit the xorg.conf, in my case "sudo vi ./xorg.conf." I would STRONGLY recommend you make a backup but this is your own perogative, you could always do the dpkg --reconfigure thing if it all goes wonky (or my favorite xorgconfig...sorry, I come from Gentoo, gotta do things the hard way).

Scroll on down to the section that says "Device." It'll have a little piece that mentions "Identifier" which should look like the make of your graphics card.  On the driver piece under it it'll probably say something akin to "Driver    "nv"" or something similar.  Change whatever's between the quotes to "nvidia" and save the file (in vi this is :wq).

Now that you're back in the command line it's time to get and install the nvidia drivers.  The quick-n-dirty way is "sudo apt-get install nvidia-glx" if I remember correctly, somebody please correct me if that's not it.  You could also use Synaptic or whatever you like to get it, but ultimately you don't have to worry about much else.  Once it's down and in type "startx" and see if the desktop comes up.  You'll know if the nVidia driver is working because for a brief moment the screen will flash with the nVidia logo.  If it does not then you're not using it.  Once it's up, reboot the system as normal, you're good to go (and I'd recommend making a backup of that xorg.conf into your home directory, call it something like "xorg.conf-nvidia" so you'll remember).

**EDIT**:  almost forgot.  After installing nvidia-glx be sure to run "sudo nvidia-xconfig"

That will take care of your graphics driver issue pretty neatly.  You can also install the driver manually, in which case do the same thing but just replace the bit with apt-get with installing the .deb package.

---

### Post by BIGtrouble77 on 2007-02-13
If your still having problem connecting to the cedega updates check out my fix in this thread:
[http://www.ubuntuforums.org/showthread.php?t=301373](http://www.ubuntuforums.org/showthread.php?t=301373)

---

### Post by agamotto on 2007-02-13
In my experience, Wine simply doesn't work under Edgy 64-bit.  I could not get it to work at all.  Cedega does work, but the updates do not.  It tends to hang the machine, forcing you to reset/reboot.  I have been fetching the engine updates from the website, and manually installing them.  

Hope this helps

---

### Post by czechplz on 2007-02-13
> **FrozenFOXX said:**
> If you're using an nVidia graphics card and wish to use the closed source drivers here's what I did.

Start up ubuntu, hit F6 at the boot screen and enter "single user" (Or something similar to that, might be "single" but you get the idea).  This will start Ubuntu up in the command prompt which generally is a good thing for what we're about to do.

Log in as usual and type "cd /etc/X11/." After that fire up your favorite editor to edit the xorg.conf, in my case "sudo vi ./xorg.conf." I would STRONGLY recommend you make a backup but this is your own perogative, you could always do the dpkg --reconfigure thing if it all goes wonky (or my favorite xorgconfig...sorry, I come from Gentoo, gotta do things the hard way).

Scroll on down to the section that says "Device." It'll have a little piece that mentions "Identifier" which should look like the make of your graphics card.  On the driver piece under it it'll probably say something akin to "Driver    "nv"" or something similar.  Change whatever's between the quotes to "nvidia" and save the file (in vi this is :wq).

Now that you're back in the command line it's time to get and install the nvidia drivers.  The quick-n-dirty way is "sudo apt-get install nvidia-glx" if I remember correctly, somebody please correct me if that's not it.  You could also use Synaptic or whatever you like to get it, but ultimately you don't have to worry about much else.  Once it's down and in type "startx" and see if the desktop comes up.  You'll know if the nVidia driver is working because for a brief moment the screen will flash with the nVidia logo.  If it does not then you're not using it.  Once it's up, reboot the system as normal, you're good to go (and I'd recommend making a backup of that xorg.conf into your home directory, call it something like "xorg.conf-nvidia" so you'll remember).

**EDIT**:  almost forgot.  After installing nvidia-glx be sure to run "sudo nvidia-xconfig"

That will take care of your graphics driver issue pretty neatly.  You can also install the driver manually, in which case do the same thing but just replace the bit with apt-get with installing the .deb package.

i did your way...and the driver SAYS it installed just fine..but when i try to run Cedega..it says im missing x11glx and not usng my driver...and install fails.....i figured its the Ubuntu source driver and wanted to go with the nVidia driver from there site...and i get no screens:mismatch version errors and x has to shut down....i can get my rivers from ubuntu and still use 3d exelerated gfx? what am i missing?

---

