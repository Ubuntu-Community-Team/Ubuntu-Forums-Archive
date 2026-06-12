---
title: "Halo trial on Kubuntu 10.04"
date: 2011-11-18
forum: Wine
---

### Post by |{urse on 2011-11-18
Okay so, I haven't posted a howto on running halo (trial) on wine in quite a while. So here it is.

install wine via ppa, I'm  using lucid so 1.3.34-0ubuntu1~ppa1~lucid1 works amazing
Obtain a copy of halotrial.exe (I'd post you a link but I don't think it's appropriate on here)
run winecfg
click the 'Libraries' tab
select d3d8 and click apply, now highlight d3d8 and click edit, change it so it says 'd3d8(builtin, native)' 
click the 'Graphics' tab 
place a checkmark in 'Allow Directx apps to stop the mouse leaving their window'
uncheck the next 3 checkboxes
make sure Vertex Shader Support is set to 'Hardware' and check 'Allow Pixel Shader'
Obtain a copy of directx9.0c redistributable (I'd post you a link but I don't think it's appropriate on here)
cd your way to the Directx 9.0c redistributable that you downloaded earlier and install it.
open regedit (simply type 'regedit' in the console)
Navigate your way to HKEY_CURRENT_USER > Software > Wine
Right click on wine and select 'New > Key' Name this new key Direct3D
right-click on the new Direct3D entry and select 'New > String'
Name the new string VideoMemorySize and then double click it.
Set the value data to 512 or 256 or 128 or whatever your video memory is on your graphics card
Close regedit
Create a shell script so you can easily launch Halo
Here's mine..

> 
#!/bin/bash
cd /home/username/.wine/drive_c/Program\ Files/Microsoft\ Games/Halo\ Trial/
wine explorer /desktop=username,1280x768 halo -use20 -Vidmode 1280,768,60 -safemode

..Now, once halo is running you can improve the speed almost instantly by setting VSYNC in halo's video settings.
Halo should now be running superfast, seemingly faster than on windows.

[IMG]http://i283.photobucket.com/albums/kk302/SuperiorYeti/2011-11-18-105051_1440x900_scrot-2.png[/IMG]

---

### Post by |{urse on 2011-11-18
I am running nvidia on an fx5500, i have yet to see this not work on nvidia proprietary drivers, I have yet to see it work at all on ATI even once.

---

### Post by Perfect Storm on 2011-11-18
Moved to Wine section.

---

### Post by |{urse on 2011-11-18
Oh duh thanks.

---

### Post by Dlambert on 2011-11-20
Interesting...

---

### Post by |{urse on 2011-12-03
Okayso bit of an update on this, 1.3.34-0ubuntu1~ppa1~lucid1 has halo's chat completely fixed and everything is overall running even faster. id like to buy those guys+gals a beer, thank you wine developers, whatever it is you did there!

[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

---

