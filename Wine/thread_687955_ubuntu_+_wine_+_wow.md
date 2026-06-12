---
title: "ubuntu + wine + wow"
date: 2008-02-04
forum: Wine
---

### Post by zoso62585 on 2008-02-04
Alright, i am new to linux in general, but more specifically to ubuntu. i have made a lot of progress here with this install, but i cannot get wow to work correctly. i have tried every walkthrough/howto i can find, including ubuntu forums, wow forums, etc...

i have wow installed and i can run it...sort of. i can run it in d3d mode, but it's choppy, whenever i try to run it in opengl mode, everything is really, really dark and i can't actually see any characters in the game, i can see glow around weapons, poisons, etc, but no actually bodies of toons, npcs, or mounts.

i'm going to post some of my hardware...
     i have a gateway laptop (t-1616) - came with vista
     it has a turion64x2 tl-58 processor
     ati radeon x1270 graphics chipset

that should be all that really matters i guess, since i have everything else working (ndiswrapper for realtek wireless, sound, etc)

so if anyone has any ideas about how to perfect the install of wow, they would be greatly appreciated...keep in mind, if it's on another forum/post, i've already tried it. (ie: editing regedit, config.wtf, xorg.conf) 

here's my xorg.conf file:   (the important parts at least)

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Group        0
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "false"
EndSection



i have tried editing that too, but recently i reinstalled all the ati proprietary packages that i made for ubuntu with the ati.run file from their website and haven't changed the xorg.conf since then. 

i greatly appreciate ANY ideas for the situation, i really really don't want to have to reinstall windows and dual boot, i'm sick of windows, especially vista... thanks


**i'm adding a few other things to try and help others that may be having the same issues...or other issues i ran into before getting this far.**

first, i finally have glxinfo saying that i have direct rendering support....the reason this works now is from the proprietary ati driver from their website
       i had it build version specific packages and those didn't mess everything up (before when i tried to install those drivers, i would not get a gui on next reboot and would have to restore xorg.conf from recovery      
       mode) 

ok, next once i had direct rendering : yes, wow would give me some errors when trying to start it (see attached screenshot) something about a dual 3d thing....
         the way i fixed this ( which i couldn't find easily on any forums) was to disable my xgl session
                  $mkdir /home/username/.config/xserver-xgl/disable
       next time i rebooted, that error went away, BUT now i have the initial problem i listed, i can't see any toons, npcs, or mounts or anything in wow while in opengl mode.

---

### Post by geirha on 2008-02-05
[This](http://ubuntuforums.org/showthread.php?p=4247622) seems to be related. Have you tried deleting the contents of "Cache/"?

And [http://www.wowwiki.com/Linux/Wine/Troubleshooting#ATI_no_Object_Textures.2FModels](http://www.wowwiki.com/Linux/Wine/Troubleshooting#ATI_no_Object_Textures.2FModels) suggests adding ```
SET M2UseShaders "0"
``` to config.wtf

---

### Post by Resonance378 on 2008-02-05
> **geirha said:**
> [This](http://ubuntuforums.org/showthread.php?p=4247622) seems to be related. Have you tried deleting the contents of "Cache/"?

And [http://www.wowwiki.com/Linux/Wine/Troubleshooting#ATI_no_Object_Textures.2FModels](http://www.wowwiki.com/Linux/Wine/Troubleshooting#ATI_no_Object_Textures.2FModels) suggests adding ```
SET M2UseShaders "0"
``` to config.wtf

^^ what he said... also the Wine - WOW HowTo here in this forum section will be of major benefit. 

As an ATi user all of the tweaks listed for ATi have come in very handy for my 9600XT

[http://www.wowwiki.com/Linux/Wine](http://www.wowwiki.com/Linux/Wine)
[http://www.wowwiki.com/Linux/Wine/Troubleshooting](http://www.wowwiki.com/Linux/Wine/Troubleshooting)

---

### Post by zoso62585 on 2008-02-05
thanks to both of you for the speedy responses. i haven't tried the first idea that was posted. i have tried the forums that were listed numerous times, but i will check again for ati-specifics tweaks i may have missed. i will try these out when i get home and post when i'm done.

---

### Post by zoso62585 on 2008-02-05
> **geirha said:**
> [This](http://ubuntuforums.org/showthread.php?p=4247622) seems to be related. Have you tried deleting the contents of "Cache/"?

And [http://www.wowwiki.com/Linux/Wine/Troubleshooting#ATI_no_Object_Textures.2FModels](http://www.wowwiki.com/Linux/Wine/Troubleshooting#ATI_no_Object_Textures.2FModels) suggests adding ```
SET M2UseShaders "0"
``` to config.wtf

OMG, that totally worked. thank you so much, i seriously was searching for like 3-4 days and did not see that wtf edit anywjere. awesome.

---

