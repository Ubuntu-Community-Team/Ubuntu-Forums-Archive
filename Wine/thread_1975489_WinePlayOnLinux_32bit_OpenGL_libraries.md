---
title: "Wine/PlayOnLinux 32bit OpenGL libraries"
date: 2012-05-07
forum: Wine
---

### Post by RoyalPro on 2012-05-07
I have just done a fresh install of Xubuntu 12.04 64bit. My hardware is; 2500k-i5, 570 GTX, 32G ram.  I have installed the these; ia32-libs, 294.49 nvidia drivers(yes to install 32bit), PlayOnLinux 4.0.18, base wine 1.5.3.

My problem is when I start PlayOnLinux it says it can't find 32bits OpenGL libraries. PlayOnLinux was working fine on 10.04 64bit.  After doing searches for this I have found things saying I need to install nvidia-glx-ia32, libgl1-nvidia-glx-ia32, libgl1-nvidia-alternatives-ia32, but I can't find these in the repositories.

Are these what I need to add to get it working?  Is there repository that I can add that have these or a place where I can download the .debs?
Is there some other fix that I can do?

---

### Post by RoyalPro on 2012-05-07
Looking on the Wine forums I found this [http://forum.winehq.org/viewtopic.php?t=15537](http://forum.winehq.org/viewtopic.php?t=15537).
Is my issue the same as the problems of Ubuntu/Wine talked about on this page?

---

### Post by RoyalPro on 2012-05-07
Well I did a boot of 11.10 Xubuntu off a usb stick and installed PlayOnLinux 4.0.18.  I didn't get the missing 32bits opengl stuff.  I was able to install and play SC2 using the default drivers for an ATI 4830(not the best fps at low settings).  I was using the 4830 in 12.04 to test if my problem was with Nvidia, but I was getting the same problems even with the newest catalyst drivers installed.
I then put the 570GTX back in and was not able to boot up 11.10 off the USB.  It went black and stayed black. CRTL+ALT+DEL did reset it.  I then booted off the interal drive with the 570GTX and got to the desktop just fine.
Also I should mention that in order to install 12.04 I had to use the igfx and then switch over to the nvida card.  I did try to run playonlinux/starcraft 2 with the igfx and ran into problems, but I can't remember at the moment if they were the same problems or different.  I will switch back to the igfx later and tell what happens with that.

---

### Post by ergo-proxy on 2012-05-07
Try to run it directly through wine...

---

### Post by RoyalPro on 2012-05-07
@ergo-proxy: I have tried running it with just wine. I get an error saying it can't find DirectX.  I have tried using winetricks to install the directx stuff and still get the same error.


When I switch to igfx and boot 12.04 I get the same errors as the nvidia and ati cards(32bits OpenGL with PlayOnLinux and DirectX with wine). I can boot my Xubuntu 12.04 usb with the igfx, but igfx hangs with the 11.10 usb just like the nvidia card.
I am thinking of putting 10.04 on a usb stick and if I can boot my nvida card off that then I am going back 10.04 and compiling my own 3.3.4 kernel.  I will wait for a while before doing that hoping the someone will have an aswer or fix to this problem.

---

### Post by ergo-proxy on 2012-05-08
Wine in Ubuntu 12.04x64 comes  with two version 32bit and 64bit. Are you sure you picked the correct architecute? [http://ubuntuforums.org/showpost.php?p=11887912&postcount=4](http://ubuntuforums.org/showpost.php?p=11887912&postcount=4)

---

### Post by RoyalPro on 2012-05-08
The default wine install installs both 32 and 64 on a 64 bit system.  When I ran it on 11.10, I think it installed both 32 and 64 as well.  I installed it from a ppa.  It installed it into the Pro...(x86) folder when it installed. It also installs fine, but the problems show up with the 32bit libs not found and then the starting of the program says it can't find directx.  I looked at your link, but I question if it is needed, because my .wine has both the 64 bit Program Files and the 32 bit Program Files(x86) dir like windows.  I am thinking it should act like windows and pic the correct way.
If I try to remove either the 32 bit wine or 64 bit wine it takes the other for uninstall too.
The more I look around at this problem them more I think 12.04 64 bit is broke with 32 bit wine directx/opengl, but if might try the tip from your link if you can tell me how to undo it later if I need to.

Thanks for your input sofar.

---

### Post by ergo-proxy on 2012-05-08
That's one of differences between 12.04x64 and previous versions, be default a winprefix is created in 64bit architecture and wine x64 is used. Try it by yourself, you won't be able to install anything from winetricks if you dont export wineach to 32bit version.

---

### Post by RoyalPro on 2012-05-08
Alright trying it with your recommendations of export.  Have Sc2 installed in the new prefix folder applying the updates now, but I have been this far before. ;/

---

### Post by RoyalPro on 2012-05-08
Get the same Failed to initialize DirectX... that I got before.
I install these winetricks into the 32 bit wineprefix(saw them recommend to install for sc2 on another page this is copy and pasted out of the winetricks log in my 32 bit prefix folder); 
d3dx9
vcrun2008
vcrun2005
droid
fontfix
fontsmooth=rgb
gdiplus
gecko
Still get the directx error.  Didn't think it would be that easy but thought I would give it a try.

Any other suggestion?  Anyone?  I am very convinced now that 12.04 64 bit broke 32 bit wine. :(

---

### Post by RoyalPro on 2012-05-08
We here I go installing 10.04 again

---

### Post by cwwilson721 on 2012-05-09
By your description in the first post, since you said "yes" to 32bit libs, you installed the Nvidia drivers from Nvidia.com, correct?

That's a common mistake.

I love those drivers myself, BUT you need to do things in the correct order (Why, I don't know. Something gets added somewhere, and it works)

[LIST]
[*]Uninstall the drivers you have now (sudo nvidia-uninstall, I think)
[*]Install the drivers from Additional Drivers
[*]Reinstall the Nvidia Drivers (The one you downloaded, the NVIDIA*.run one) DONT replace/append/correct xorg.conf. LEAVE IT BE THE WAY THAT UBUNTU DRIVERS MADE IT. But basically, answer "yes" to everything else the Nvidia drivers ask.
[/LIST]

There is something the Additional Drivers from Ubuntu installs that the Nvidia drivers do not (I think it's some of the opengl dll type files). I remember Nvidia having a note about that sometime back

Let us know

[COLOR="Red"]NOTE: The above will mess with your System Update if it updates your kernel. BE WARNED[/COLOR]

---

### Post by RoyalPro on 2012-05-09
I did install the drivers from nvidia.com.
By additional drivers do you mean the proprietary drivers that ubuntu has in its default repos?  I did install the 295.40 drivers that came with ubuntu with the same effect.  I also added the x-swat ppa and installed their 295.40 drivers with the same result.  I would have tried the non-proprietary (nouveau) drivers that come with ubuntu but I am not able to boot with them, don't get a desktop and can't crtl+alt+f1... to get the a different tty, it just hangs with a black screen.
If additional drivers you mean something else please let me know.  I install the 296.40 drivers with synaptic as they didn't show up when I went to the special thing to add them, could that make a difference?
For a LTS, 12.04 is one of the most glitchy Ubuntus I have ever used.

---

### Post by roberty82 on 2012-07-03
[http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)

You could always try this PPA to get things working. The standard Ubuntu doesn't come with good WINE support anymore. Kinda sucks, I play Grand Theft Auto San Andreas.

---

### Post by Dlambert on 2012-07-03
Try this: 
> sudo apt-get update  


sudo apt-get build-essentials // GCC compiler  


apt-get install binutils-gold

sudo apt-get freeglut3-dev 


sudo apt-get libglew-dev


---

