---
title: "New NVIDIA drivers, 100.14.03 (!)"
date: 2007-04-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by xopher on 2007-04-21
Someone talked about these in IRC, and they seem to be pretty fresh so I decided to post..

x86: [http://www.nvidia.com/object/linux_display_ia32_100.14.03.html](http://www.nvidia.com/object/linux_display_ia32_100.14.03.html)
amd64: [http://www.nvidia.com/object/linux_display_amd64_100.14.03.html](http://www.nvidia.com/object/linux_display_amd64_100.14.03.html)

:rolleyes:

> Version: 100.14.03
Operating System: Linux x64 (AMD64/EM64T)
Release Date: April 20, 2007

Release Highlights

    * Added support for GeForce 8600 GTS, GeForce 8600 GT, GeForce 8500 GT, GeForce 8400 GS, and GeForce 8300 GS


---

### Post by nss0000 on 2007-04-21
BigX:

I  read the references. But what is the "value" proposition? Given a current, well-functioning NV7600gs vid-display on Dapperx64 --  using UBUNTU_repository NV_drivers --  I cannot value the risk / benefit proposition to installing these new NV_drivers.

Will visual_gains in quality/speed of display be obvious? Or will I get better visual control? OTOH might I hose the display completely? Basically, what's in it for me?

The question arises as recently I have installed both QGIS & GRASS ... free geoanalytic software that make significant computational & display demands. My current AMDx64 kit, and DAPPERx64 with NV_drivers ( 19" LCD )  performs quickly and without issue. So current NV_driver software works well under demanding load. I feel no NEED to find newer/faster/slicker displays ... ofcourse I keep my eyes open for improvements. 

Might  the new NV_drivers be a pleasant surprise? Much-ado about nothing?? Or techno-quicksand ???

nss
*******

---

### Post by Kilz on 2007-04-21
> **nss0000 said:**
> 

Might  the new NV_drivers be a pleasant surprise? Much-ado about nothing?? Or techno-quicksand ???

nss
*******

There is an old saying "if it isnt broke, dont fix it!". Some people feel the need to have the very latest. They want it , and most of them cant tell you why other than its  "new". With replacing graphics drivers sometimes its better to keep the existing working ones, rather than deal with the bang your head into the wall problems that can happen (up to and including the gui not starting). To each their own, but you ask a good question. Personally I will trade stable and working for minimal improvement and lots of headaches any day.  :D

---

### Post by canonbeck on 2007-04-21
Well, I'd like to to say thanks to xopher for posting these drivers. I just got a new 8500gt card and could'nt get it working but this new driver did the trick! Cheers!

---

### Post by Tanker Bob on 2007-04-21
Thanks for the link!  I just tried to install on feisty with my 8800GTS card, but the install didn't work.  X fails to start, telling me that my kernel module doesn't match the driver version.  Worked on it for several hours but no go.  9755 works fine.  I left a note on the NVIDIA site forum.

---

### Post by nss0000 on 2007-04-21
BigK:

Appreciate your thoughts, and as the last two-posts indicate .... I can do no better than quote  the lines from an "infamous" 3-Stooge piefight:

PAL:: "You act as if the sword-of-Damocleas were hanging over my head."
MOE:: "Pal, you must be psychic.":popcorn: 

nss
********

---

### Post by CARB0N on 2007-04-21
I tried installing the drivers on my new feisty install, but it says it cannot open it.:confused: 
help pls

-carb0n aka a linux noob

---

### Post by Arun985 on 2007-04-23
Hey, I downloaded the new nVidia driver, and when i try to run it, I'm getting an error message that says "nvidia installer must be run as root." Does this mean I should run it from a command line, and not the terminal in Ubuntu?

---

### Post by hardyn on 2007-04-23
add sudo

---

### Post by RawMustard on 2007-04-23
I don't think it's wise to run the nvidia installer from your desktop, you should kill gdm and install from cli, then sudo /etc/init.d/gdm restart.

---

### Post by russell.h on 2007-04-23
Has anyone who installed this noticed any difference running Beryl (or compiz)?

---

