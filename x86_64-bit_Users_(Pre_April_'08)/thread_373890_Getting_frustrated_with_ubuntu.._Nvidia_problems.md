---
title: "Getting frustrated with ubuntu.. Nvidia problems"
date: 2007-03-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by xeocub on 2007-03-01
Ok, I am seriously ready to throw this **** in the trash. Nothing I have thus far tried to install besides ntfs-3g for a non Raid disk has worked in Ubuntu.. It's getting fairly annoying.
There is always 10 different types of HowTo's that all say something else and don't work in a different way. 

First problems were getting my Raid0 drives to work with NTFS-3g support. Still haven't gotten anywhere with that. Then Ubuntu just CONSTANTLY crashes while in a web browser. dmraid installs differently everytime, and it seems the synaptic installs are always outdated.

Now, I'm just trying to install a god damn nvidia driver for my (ok old but still) Ti4400. I've tried the legacy drivers, I've tried Envy, I've tried the GLX drivers NOTHING ******* works and it's seriously pissing me off. 

And it's not like I'm doing something wrong because I always follow the How To's. I've done like 5 reformats in an effort to start anew. Anyway, here's what my problem is now:
I've installed the GLX drivers according to Alberto Milone's How to, since when I did it with Envy it would crash Xorg and I would loose my GUI. First step into it:

> 
glxinfo | grep direct
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".


All I'm doing is checking to see if the drivers are enabled for 3D or not. And I get these lovely errors.

---

### Post by xeocub on 2007-03-01
WOW I was finally able to do it right. And not thanks to a HowTo either. For anyone else with problems try this (for AMD64):

Go here:

[http://www.nvidia.com/object/linux_amd64_display_archive.html](http://www.nvidia.com/object/linux_amd64_display_archive.html)

My card wasn't supported by the newest driver, so I had to use 1.0-9631.
Kill xserver like this:

sudo killall gdm 

login through the non GUI terminal..

Go to the directory where you downloaded that file and type:

sudo sh NVIDIA-Linux-x86_64-1.0-9631-pkg2.run

Follow the directions, I had one error at the end where the installer coulnd't find a log (it assumed correct installation)

then  "sudo startx" to start x11 again. You'll see a Nvidia logo and such.. it works.

---

### Post by firekat on 2007-03-02
I am glad that you got nvidia working.  I have been fighting with getting a Raid 0 recognized so that I could read the ntfs files on it (my Ubuntu installation exists on a totally separate drive than the Raid).   I have spent too much time trying to get that to work.  I am relegated to putting whatever I need to access on that drive on a USB drive and transferring it that way.  Another workaround is transferring the files via a Windows network to another machine and transferring it via Samba.

On your nvidia installation when you select something that requires a sudo login (like pulling up the synaptic package manager) do you get a slight "stuttering" in the screen darkening?  FYI, I am running a nvidia Geoforce 6800 GT.

To get my driver installed I tried Synaptic, Envy, Simple64, Automatix and a myriad of how to's.  The Synaptic did not work at all.

I first tried using Ubuntu with Breezy I believe (early '06).  I gave up on that, it was just impossible.  Edgy though not fully functional on my machine is still a big improvement.

Another alternative is to go with a generic 32 bit version.  The AMD 64 bit setup still seems to be missing a lot of functionality.  I tried LinuxMint, which is based on Ubuntu and has some other things built in.  It still would not see my NTFS Raid.  I was not in love with the Gnome "Slab" menu and it seems to be out on the fringe and I wonder how long it will be in existence.  The AMD Ubuntu version seemed to run a bit faster and one of the things that disturbed me with LinuxMint was that on the non X screens during bootup the letters were very jagged in appearance and did not scroll with either the clarity or smoothness of Ubuntu AMD.  That gave me some concern as what it would be doing to my system.  Probably no matter.

FYI, I find sometimes giving the Ubuntu 3 finger pinch (ctrl, alt, backspace) and rebooting X can solve some problems without going to a full boot.

Good Luck!

---

### Post by xeocub on 2007-03-02
I have no issues at all anymore with my video drivers. You should try the installation that Nvidia made, it truly was the only thing that worked for me. It even detected any other drivers that were installed previously and uninstalled them for me.

Just go to the link I posted and select the newest driver, (97xx I think it was)

Try it out, can't hurt anyway..

Gona tackle the Raid problem next... hopefully it will work. I've gotten it to work on my one driver that I have my ubuntu partition on aswell, but now windows doesn't seem to recognize it anymore..

---

