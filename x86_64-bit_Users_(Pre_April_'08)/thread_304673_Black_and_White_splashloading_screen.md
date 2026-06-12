---
title: "Black and White splash/loading screen"
date: 2006-11-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by Extr3me on 2006-11-22
OK, I just recently got a new workstation in my office with dual AMD Opteron chips.  I just got Ubuntu Egdy Eft 6.10 (amd64 distro) installed on the machine but I was having some problems with the x server.

I am using the Nvidia Quadro FX 500/600 pci card (NV34GL or basically the Nvidia fx5200 chip) which seems half-way OK on this version of Ubuntu.

Initially I was using the default graphics drivers (nv in xorg.conf) with Ubuntu but this was forcing me to use 1024x768 @60Hz. I have installed the nvidia-glx driver and now Ubuntu recognizes the LCD monitor and it lets me get to 1280x1024 @75Hz which is fine for me.

The problem is that the splash screen when Ubuntu is loading is clearly graphically corrupted, loading in a smeared black & white version.  This was also a problem when booting from the live CD, although I found that once the login screen loaded, the graphics were fine from then on (includin g the desktop).

Does anyone know how to fix this loading screen problem, as my administrator has little faith that the install will survive much longer due to the graphics corruption on bootup?

The graphics card I use has both a DVI and a d-sub port on the back, and the output is the same when using the LCD with either.  The loading screen is corrupt but the login/desktop work just fine on the d-sub and the DVI.

Any help would be appreciated,

Extr3me

---

### Post by Virage on 2006-11-22
I have the same problem on a P4 box I just finished installing Ubuntu 6.10 on with the latest NVIDIA drivers for an FX 5200 card.

I am still searching the forums for a fix but I am pretty sure it's just the NVIDIA splash screen that is messed up. My work-around for the problem so far is to just press CTRL+ALT+F1 to load a terminal screen then CTRL+ALT+F7 to reload the GNOME interface.

Seems to be working fine other than that little splash glitch.

---

### Post by Extr3me on 2006-11-23
I admit this bug is minor as only the loading screen is affected, but still it does suggest that there is a problem with the graphics interface/drivers such that this happens.

Hopefully this error does not contain itself in any other niche corners of the Ubuntu OS or any software which runs on it. I tend to use a wide range of software, some of which dates back some number of years on the Unix platform, so this could present a problem further down the line.

As usual, I overworry at the slightest thing...

---

### Post by iLoVe.cF- on 2006-11-23
This problem is FOR 64 BIT EDGY ONLY.

You can do a usplash edit or what its called.. havnt tried either.. 

But this is NOT VIDEO CARD ERROR.

I run 64 bit edgy.

Amd athlon 64 3000+
2gb memory ddr pc3200
ATI Radeon x850 XtPE

ohh i got ati :O..
same error.. same error with a s3 card.. same with a tnt2 same with any card.. that i have tried.. but.. nothin to worry about :p

---

### Post by daradib on 2006-11-23
I have a similar problem. It's blue and black, but the loading bar is messed up. The loading bar has several black lines going through it which are previously blue. Using Kubuntu Edgy 64-bit, ATI Radeon X800.

---

### Post by John Jason Jordan on 2006-11-23
> **daradib said:**
> I have a similar problem. It's blue and black, but the loading bar is messed up. The loading bar has several black lines going through it which are previously blue. Using Kubuntu Edgy 64-bit, ATI Radeon X800.
Also messed up with NVidia drivers -- the nv driver on the install/live CD. I haven't actually installed Edgy yet; still using Dapper. But my computer has NVidia chip and it's also messed up. So the problem is not related to the chip or the driver. It's just a bad animation thing on the CD.

---

### Post by John.Michael.Kane on 2006-11-24
A bug report has been filed [usplash appears black and white]("https://bugs.launchpad.net/distros/ubuntu/+source/usplash-theme-ubuntu/+bug/67545")

---

### Post by jonah1980 on 2006-11-24
yeah this problem has been with my machine since the edgy betas, it seems weird no one can fix it... such a little display prob i thought would be easy but it must go deeper than that - i dunno

---

### Post by fabertawe on 2006-11-25
I've not had any graphic corruption, just the monochrome (bluish tint). I actually thought it was supposed to be like this until I heard about the bug!

Paul

---

### Post by Druke on 2006-11-29
so is there a way for us to fix it by hand?

---

### Post by Dun on 2006-11-29
> **daradib said:**
> I have a similar problem. It's blue and black, but the loading bar is messed up. The loading bar has several black lines going through it which are previously blue. Using Kubuntu Edgy 64-bit, ATI Radeon X800.

I have the exact same symptoms with Radeon X<something>. I re-installed the usplash, and now I can see the bluish kubuntu-text, but not the fancy loading the below it.

---

### Post by gratefulfrog on 2006-11-29
I have the same problem. I doubt that it's a graphic card issue. I run AMD64 with ATI card and binary fglrx drivers. 

I too thought it was ugly but intentional, not a bug! What is the launchpad bug ID?

---

### Post by John.Michael.Kane on 2006-11-29
gratefulfrog [https://bugs.launchpad.net/distros/ubuntu/+source/usplash-theme-ubuntu/+bug/67545](https://bugs.launchpad.net/distros/ubuntu/+source/usplash-theme-ubuntu/+bug/67545)

---

### Post by cdenley on 2006-12-05
The problem seems to be with usplash showing the wrong resolution. It always seems to pick the first one in the list, which is 640x400. This is the only resolution which seems to show up black and white for me. The only way I can get the 1024x768 splash screen is to remove the other resolutions from the list in "usplash-theme-ubuntu.c". Grub boots into 1024x768, and usplash.conf is set to 1024x768, but it will still show the first resolution in the linked list in the top left of the screen. I don't really know C, but I attached my modified usplash-theme-ubuntu.c file which seems to work for me since it only uses 1024x768.

---

### Post by Horbert on 2006-12-05
You can also just go back to verbose in grub. You will lose the "pretty" splash screen but I prefer seeing everything loading, then the corrupted usplash. Even after reinstalling it I could get an image but it was never perfect.

sudo gedit /boot/grub/menu.lst

Look for :

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash vga=791

And then change the last line to:

# defoptions=verbose

Finally exit that and run:

sudo update-grub

Once you reboot you will it will at least have something to watch while loading.

---

### Post by quimchin on 2006-12-07
cdenley, how did you compile the c file to use for the usplash?

Can you give a little more info?

Cheers.

---

### Post by cdenley on 2006-12-07
wget [http://archive.ubuntu.com/ubuntu/pool/main/u/usplash-theme-ubuntu/usplash-theme-ubuntu_0.6.tar.gz](http://archive.ubuntu.com/ubuntu/pool/main/u/usplash-theme-ubuntu/usplash-theme-ubuntu_0.6.tar.gz)
tar xzfv usplash-theme-ubuntu_0.6.tar.gz
cd usplash-theme-ubuntu-0.6
mv usplash-theme-ubuntu.c usplash-theme-ubuntu.c.orig
wget [http://librarian.launchpad.net/5247731/usplash-theme-ubuntu.c](http://librarian.launchpad.net/5247731/usplash-theme-ubuntu.c)
make
sudo make install
sudo update-initramfs -u

change defoptions line in /boot/grub/menu.lst to:
# defoptions=quiet splash vga=791

sudo update-grub

---

### Post by Pawel Stolowski on 2006-12-10
I've just moved to 64-bit edgy (from 32-bit) and everything seems to work fine except for the boot splash screen is all grey. I found similar bug was reported for ATI cards, but I have Nvidia' GF6600 GT... Does anyone have this problem? Is there a fix for it (except for disabling the splash logo)?

---

### Post by kleeman on 2006-12-10
I have it here as well with an nvidia 7950 GX2.

---

### Post by Usedpants on 2006-12-10
I think that may be the default for x64 version? I have only seen color in attempting to install 32 bit.

---

### Post by igsimon on 2006-12-11
it is already reported problem with 64 bit version - [https://launchpad.net/distros/ubuntu/+source/usplash/+bug/67545](https://launchpad.net/distros/ubuntu/+source/usplash/+bug/67545)

Still waiting for a fix - 64 bit FEISTY has the same problem for me

---

### Post by jonah1980 on 2006-12-11
here's more users with the problem and what's been going down:

[http://www.ubuntuforums.com/showthread.php?t=304673](http://www.ubuntuforums.com/showthread.php?t=304673)

---

### Post by Pawel Stolowski on 2006-12-11
Thanks for all replies and links to launchpad bug entry. I added my 2c there...

---

### Post by Laryllan on 2006-12-12
Hehe, I have no bootsplash at all in Xubuntu 64bit 6.10. Not even anything on the screen - my monitor just goes to standby while loading...

...but frankly, I don't care.:rolleyes:

---

### Post by mand0 on 2006-12-12
I have this problem as well with a 6800GT.  What happens if you change the splash screen?  Does is stay grayed out?

---

### Post by Pawel Stolowski on 2006-12-12
What do you mean by changing splash screen? Is there any easy way to change it (remember this is usplash screen, not grub splash)? The only thing I tried was "vga=..." grub setting to enforce certain gfx mode, but it didn't help (it set the resolution correctly, but then the splash was just displayed in the top-left corner of the screen and it was still grey).

---

### Post by melon2006 on 2006-12-12
thank you cdenley, that have worked.
I even got higher resolution at tty (alt+ctrl+f1..f6 terminals)
nice :)

---

### Post by jonah1980 on 2006-12-13
well apparently there is a fix now here:

[http://www.ubuntuforums.org/showthread.php?t=304673](http://www.ubuntuforums.org/showthread.php?t=304673)

but i haven't tried it yet...

---

### Post by kleeman on 2006-12-13
Works for me. I updated the usplash package for amd64 with a version bump to 0.6.1 if anyone wants the deb:

[http://www.yourfilelink.com/get.php?fid=234873](http://www.yourfilelink.com/get.php?fid=234873)

Install as usual with

sudo dpkg -i usplash-theme-ubuntu_0.6.1_amd64.deb

Edit: This seems to work only with the kubuntu artwork on my machine at present

---

### Post by Kikoolol on 2006-12-13
Hi guys !

Do you know if a patch exists for usplash-theme-kubuntu.c too and where I can find it ?

Thks in advance ! :) 

Kkl

EDIT : I finally made it myself according to the differences in usplash-theme-ubuntu.c (wasn't really difficult). I will test it and post a feedback as soon as I can !

EDIT #2 : I tested it and it works fine ! Thanks for the tip !

---

### Post by quimchin on 2006-12-13
cdenley, when I follow your instructions and type "make", I get the following error:

make: Circular throbber_back.png <- throbber_back.png.c dependency dropped.
pngtousplash throbber_back.png > throbber_back.png.c
/bin/sh: pngtousplash: not found
make: *** [throbber_back.png.c] Error 127
rm throbber_back.png.c

EDIT: found solution:
sudo apt-get install usplash-dev

---

### Post by quimchin on 2006-12-13
Got it all working perfectly!

Thanks to cdenley!!! Good work.

---

### Post by Kikoolol on 2006-12-14
Hello !

To keep this thread alive, I have another question :mrgreen: 

Does somebody know if it is possible to get a well centered usplash screen at a higher resolution than 1024x768 ? I usually boot with the grub option : vga=794 (for 1280x1024), but usplash is not centered, so I have to use vga=791 (for 1024x768 res) instead. That sucks a little, because the quality of the splash screen is worse (1024x768 is usplash max resolution) ... I've tried to modify the usplash.conf but it didn't do the trick.

Thks in advance !

Kkl

---

### Post by Popoi on 2006-12-21
> **kleeman said:**
> Works for me. I updated the usplash package for amd64 with a version bump to 0.6.1 if anyone wants the deb:

[http://www.yourfilelink.com/get.php?fid=234873](http://www.yourfilelink.com/get.php?fid=234873)

Install as usual with

sudo dpkg -i usplash-theme-ubuntu_0.6.1_amd64.deb

Edit: This seems to work only with the kubuntu artwork on my machine at present

The best and easiest solution, it works fine for me!! :D 

Now I have a full color Ubuntu theme Splash Screen on 64-Bit. Thanks.

---

### Post by Kalibur on 2006-12-22
nvidia fx5500 
](*,) I have had similar problems in all versions of edgy... and to add to that its imposible to boot on 1280x768 widescreen so I constantly have to do some Display manual swapping once logged in till the time I fix the driver issues.  Plus I get no output on S-video out once gnome desktop is loaded

---

### Post by Kalibur on 2006-12-22
> **Kikoolol said:**
> Hello !

To keep this thread alive, I have another question :mrgreen: 

Does somebody know if it is possible to get a well centered usplash screen at a higher resolution than 1024x768 ? I usually boot with the grub option : vga=794 (for 1280x1024), but usplash is not centered, so I have to use vga=791 (for 1024x768 res) instead. That sucks a little, because the quality of the splash screen is worse (1024x768 is usplash max resolution) ... I've tried to modify the usplash.conf but it didn't do the trick.

Thks in advance !

Kkl

I have similar problem so I have to either disconnect my lcd so it boot on defaults then I plug it to log in @1024x768 instead of 1280x768.  This continues till I install nvidia-glx* or nvidia-settings drivers.](*,)

---

### Post by Tomy on 2006-12-23
> **cdenley said:**
> wget [http://archive.ubuntu.com/ubuntu/pool/main/u/usplash-theme-ubuntu/usplash-theme-ubuntu_0.6.tar.gz](http://archive.ubuntu.com/ubuntu/pool/main/u/usplash-theme-ubuntu/usplash-theme-ubuntu_0.6.tar.gz)
tar xzfv usplash-theme-ubuntu_0.6.tar.gz
cd usplash-theme-ubuntu-0.6
mv usplash-theme-ubuntu.c usplash-theme-ubuntu.c.orig
wget [http://librarian.launchpad.net/5247731/usplash-theme-ubuntu.c](http://librarian.launchpad.net/5247731/usplash-theme-ubuntu.c)
make
sudo make install
sudo update-initramfs -u

change defoptions line in /boot/grub/menu.lst to:
# defoptions=quiet splash vga=791

sudo update-grub

thanks cdenley,

I am testing Ubuntu 7.04 amd64 (feisty) and it still has the black and white usplash bug. Seems this bug should have been fixed after two months -- it surprised me how annoyed I was every time I restarted.

On a new install I did this:
sudo apt-get install build-essential
sudo apt-get install usplash-dev

and then followed the instructions. Now I have a nice color ubuntu logo and I am :-D.

---

### Post by meldroc on 2006-12-30
Add me to the list of people wanting a fixed kubuntu splash screen.  I was wondering why the progress bar looked all funky, then found this thread, and found that if I switched to the ubuntu splashscreen and applied the fix in this thread, it works correctly.

---

### Post by daradib on 2006-12-30
> Add me to the list of people wanting a fixed kubuntu splash screen.
Don't forget to add me.:-D

---

### Post by jonah1980 on 2006-12-31
although the fix worked to me and i now have a colour splash, it's still slightly more towards top left and is off center. my screen res is set as 1280x1024...

---

### Post by beamo on 2006-12-31
I never realized there was a problem with my splash screen until I read this thread. I knew something was wrong when I increased the resolution to 1024x768 and the logo moved to the upper left corner of the screen but the new color logo is very nice. Thanks!

---

### Post by Saubazi on 2007-01-11
I have more problems than just this. Or I don't know I have problems changing the splash theme
at all. I updated from Dapper to Edgy and I got this buttugly splash in the process (rectangles, triangles, circles and some ega imitations). Anyway this one has progress bar and colours and all. When messing around with some usplash stuff I was every now and then able to get the described black&white ubuntu splash but the funny part is that when I tried to change to some other splash it returned to this ega imitation splash. I don't seem to be able to switch the splash in any control manner. I switch to one splash, I get the gray&white ubuntu splash, I switch to another and I get this ega-screen, I switch back to the first one and the ega-splash stays, so WTF?

I'll try compiling the provided .c and report back but I am not getting my hopes high with this one. (not a biggie but it is absurd how it can bother me not being able to fix something)

---

### Post by Saubazi on 2007-01-11
I went trough the steps of compiling and changing the splash, although it did not
change :( - I am still stuck with this stupid looking ega imitation splash from edgy.

---

### Post by Saubazi on 2007-01-12
Perversely I tried it again by changing the splash with the "Start-Up Manager" and now it swallowed it. The splash is working pico bello, Thx!

[http://ubuntuforums.org/showthread.php?t=295524&highlight=startup+manager](http://ubuntuforums.org/showthread.php?t=295524&highlight=startup+manager)

---

### Post by jonah1980 on 2007-01-12
i can't figure out why ubuntu cant release a fix through update manager for this...

---

### Post by jlacroix on 2007-01-21
I'd like to use the .c file to recompile my Usplash, but I have no idea how to do it.

---

### Post by Yver on 2007-01-30
OK - thanks to cdenley, I got a nice little boot splash running... but the splash is ugly as hell, how do i change that? It reverted to the ichthux boot splash (wtf, I don't have the ichthux distro) instead of using the default Ubuntu one. Anyone able to help?

---

### Post by henriquemaia on 2007-02-04
I have recently installed a Edgy box for a friend of mine and used the 32bit version - only then I noticed that my splash was borked...

---

### Post by RFXCasey on 2007-02-08
While I am no stranger to PCs in general, I am completely new to Ubuntu and have little to no C experience. I see that some have had successful resolutions to this problem but the explanation seem like Greek to me. Can someone please break the process down into complete Linux newbie terms so I can learn something useful. BTW I'm using effy.:confused:

---

### Post by MrChips on 2007-02-22
> **Saubazi said:**
> Perversely I tried it again by changing the splash with the "Start-Up Manager" and now it swallowed it. The splash is working pico bello, Thx!

[http://ubuntuforums.org/showthread.php?t=295524&highlight=startup+manager](http://ubuntuforums.org/showthread.php?t=295524&highlight=startup+manager)

Start-up manager is great!  Besides fixing my prob here, it has some very useful features.

Great tip!

---

### Post by FaisalW on 2007-03-20
> **cdenley said:**
> wget [http://archive.ubuntu.com/ubuntu/pool/main/u/usplash-theme-ubuntu/usplash-theme-ubuntu_0.6.tar.gz](http://archive.ubuntu.com/ubuntu/pool/main/u/usplash-theme-ubuntu/usplash-theme-ubuntu_0.6.tar.gz)
tar xzfv usplash-theme-ubuntu_0.6.tar.gz
cd usplash-theme-ubuntu-0.6
mv usplash-theme-ubuntu.c usplash-theme-ubuntu.c.orig
wget [http://librarian.launchpad.net/5247731/usplash-theme-ubuntu.c](http://librarian.launchpad.net/5247731/usplash-theme-ubuntu.c)
make
sudo make install
sudo update-initramfs -u

change defoptions line in /boot/grub/menu.lst to:
# defoptions=quiet splash vga=791

sudo update-grub

This black & white boot splash was really getting on my nerves - it's been almost 5 months since I bought my new PC (Asus M2N-SLI AM2 |  AMD X2 3800+ | 1GB DDR2 RAM | nVidia GeForce 7300GS PCIe w 512MB | 200GB Sata HD & 250GB Sata HD | PCI TV card). Every time I bootup my cool PC, it was such a letdown to see a black & white boot splash image on my LCD screen. 

I followed cdenley's instructions to the letter. When I restarted my PC, I saw the a beautiful color boot splash image for the first time on my screen. I was moved to say the least. Thank you "cdenley" for the clear instructions. It's members like you that make me glad that I use Ubuntu.

---

### Post by NeilBlanchard on 2007-03-21
Greetings,

> **kleeman said:**
> Works for me. I updated the usplash package for amd64 with a version bump to 0.6.1 if anyone wants the deb:

[http://www.yourfilelink.com/get.php?fid=234873](http://www.yourfilelink.com/get.php?fid=234873)

Install as usual with

sudo dpkg -i usplash-theme-ubuntu_0.6.1_amd64.deb

Edit: This seems to work only with the kubuntu artwork on my machine at present

I tried this deb file, and it has no splash screen at all now.  :(   There is a blinking cursor for a few moments, and then some text about checks that come out okay, and then the user sign on comes up.

Is it possible to revert things to the grayscale splash -- or is a fix for this forthcoming?

---

### Post by chrism66 on 2007-03-21
Same here lost upsplash screen just a blinking cursor on a black screen.

---

### Post by kcd on 2007-03-27
grub usplash problem

Sorry is this is not in the right place.... just new at this (first post)

3 micros running Ubuntu 6.06 with no problems, all have lcd monitors.
Upgrade to Ubuntu 6.10 and at grub startup, each lcd display shows an error message indicating that the lcd input must be 1024x768x60hz to display. After about 15 seconds, the normal Ubuntu user/password screens display, and all 3 run normally until shutdown, when the same message is displayed.
Upgrade to Ubuntu 7.04 and the same display problem happens.
This problem is preventing me from upgrading all 3 micros.
I have searched the forums, and so far am unable to find a solution. Lots of video resolution solutions, but nothing on grub startup.
Anyone seen this before? Know the solution?
Detailed micro specs as required (all 3 asus p4 1.6-2.4gig 1gig ram)
Many thanks,
kcd

---

### Post by NeilBlanchard on 2007-03-28
Greetings,

I installed the StartUp-Manager (that someone posted earlier in this thread -- **Kleeman on page 3** -- I quoted the post with the link above) and at first it didn't work -- I tried to use the highest resolution (1600x1200).  So, after dropping it down to 1280x1024 -- the color splash screen was there on the next start up!  :) 

Neil

---

### Post by kcd on 2007-03-30
dreadlord_chris
Many thanks,
Actually vga=791 did not work, but vga=773 did work...:) 
After modifying menu.1st, I had to do a 
'sudo update-grub" and restart, then it all works.
I also tried "=verbose" and was able to see the entire bootup process in text mode.
Thanks again for the help
kcd

---

### Post by The other One on 2007-04-10
> **Popoi said:**
> The best and easiest solution, it works fine for me!! :D 

Now I have a full color Ubuntu theme Splash Screen on 64-Bit. Thanks.

Worked for me too. Is there any way of centering the graphic?

---

