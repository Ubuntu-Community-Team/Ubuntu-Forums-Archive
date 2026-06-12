---
title: "openSUSE testimonial /// question on XGL"
date: 2007-02-13
forum: openSUSE and SUSE Linux Enterprise
---

### Post by darkenedday on 2007-02-13
Okay, so I even liked suse back in the buggy 10.1 phase, but 10.2 is just awesome, I love how I had a fully operational system in about 30 minutes (including restricted formats, video drivers, flash, jave, etc) and didn't have to touch a cli once (bring it on cli lovers, let the flamewar being) I think this has to be the absolute most awesome release ever, everything feels so professional and polished and it even feels faster than Ubuntu edgy, I mean don't get me wrong I love ubuntu in fact it was my first linux distro, but suse just feels so simple and nice... I recomend it to anyone looking for a fast, good looking distro with minimal tweaking necessary, and if any distro is going to bring in more new users I think it would be this one, Ubuntu I think would turn away as many people as it brings in simply because of the need to every once in awhile tweak and spend itme in the cli to set things up, even having to go and download automatix2 would frustrate joe-sixpack, the only reason I think it might not reach this goal is because of all the buzz surrounding ubuntu (don't get me wrong it's a great OS, but I dont see too many advantages vs. alot of other distros, at times it's sloppy and just downright buggy, the only thing that truly makes it great are these forums, I'll be the first to admit, the suse forums aren't as useful, but I dont see where the bad attitude some people talk about is, they're all friendly to me (although some admittedly loathe ubuntu) personally I think 10.2 was way ahead of the competition, and feisty has some work to do

but now on to my question

is XGL/AIGLX possible on openSUSE? I've always prefered xgl because it's always been simpler for me to install I've had problems every time i set up AIGLX but if it's as simple as everything else in openSUSE I'd love to use AIGLX instead being that I've heard so many bennefits of it over XGL, I have an Nvidia MX/MX 400 that runs xgl wonderfully despite it's age, if anyone knows how to set up either one with beryl, I would deeply appreciate the help THANKS!

---

### Post by Adamant1988 on 2007-02-13
> **darkenedday said:**
> Okay, so I even liked suse back in the buggy 10.1 phase, but 10.2 is just awesome, I love how I had a fully operational system in about 30 minutes (including restricted formats, video drivers, flash, jave, etc) and didn't have to touch a cli once (bring it on cli lovers, let the flamewar being) I think this has to be the absolute most awesome release ever, everything **feels so professional and polished and it even feels faster than Ubuntu edgy, I mean don't get me wrong I love ubuntu in fact it was my first linux distro, but suse just feels so simple and nice...** I recomend it to anyone looking for a fast, good looking distro with minimal tweaking necessary, and if any distro is going to bring in more new users I think it would be this one, Ubuntu I think would turn away as many people as it brings in simply because of the need to every once in awhile tweak and spend itme in the cli to set things up, even having to go and download automatix2 would frustrate joe-sixpack, the only reason I think it might not reach this goal is because of all the buzz surrounding ubuntu (don't get me wrong it's a great OS, but I dont see too many advantages vs. alot of other distros, at times it's sloppy and just downright buggy, the only thing that truly makes it great are these forums, I'll be the first to admit, the suse forums aren't as useful, but I dont see where the bad attitude some people talk about is, they're all friendly to me (although some admittedly loathe ubuntu) personally I think 10.2 was way ahead of the competition, and feisty has some work to do

but now on to my question

is XGL/AIGLX possible on openSUSE? I've always prefered xgl because it's always been simpler for me to install I've had problems every time i set up AIGLX but if it's as simple as everything else in openSUSE I'd love to use AIGLX instead being that I've heard so many bennefits of it over XGL, I have an Nvidia MX/MX 400 that runs xgl wonderfully despite it's age, if anyone knows how to set up either one with beryl, I would deeply appreciate the help THANKS!

As far as I know XGL is integrated into OpenSuse, so if it were going to work anywhere, that would be it. 

Oh, and about Suse, feeling more professional and so forth, I'm right there with you.  I've been saying that for a while now... it's amazing how well done this release is.

---

### Post by darkenedday on 2007-02-13
Okay, well I have Aiglx enabled and running, only issue is i can't start beyl (it's all installed just a weird error)

 when trying to start beryl:

XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
beryl: Another composite manager is already running on screen: 0
beryl: No manageable screens found on display :0

thats the output i get. . . any ideas?

---

### Post by _simon_ on 2007-02-13
If I remember right you need to do this:

Open Control Centre -> Desktop -> Window Behaviour -> Translucency

UNTICK use translucency/shadows.

Also you need to uninstall compiz, you can do that via YAST software management. I also uninstalled XGL via YAST as well.

---

### Post by darkenedday on 2007-02-13
ok so that worked, new issue, when i type beryl --replace i get the following output and my desktop goes black (no icon no bg), i have all the efects, but this a rather annoying problem, also if i minimise too much beryl crashes

mike@Apollo:~> beryl --replace
XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present

** (process:12751): WARNING **: get_setting_is_integrated not found in backend ini

** (process:12751): WARNING **: get_setting_is_read_only not found in backend ini

** (process:12751): WARNING **: get_setting_is_integrated not found in backend ini

** (process:12751): WARNING **: get_setting_is_read_only not found in backend ini
Initiating splash
beryl: water: GL_ARB_fragment_program is missing
Reloading all options.

---

### Post by mwolfe on 2007-02-13
I installed opensuse 10.2 on my system the other day. It seems much less buggy in terms of video/sound driver settings than ubuntu. Installation was a breeze also. I didnt have to edit my xorg.conf just to start x like i do to install ubuntu. 

However things like mp3's and codes arent installed by default and seemed much more difficult to find.  that yast2 program just isnt as good as apt + synaptic either, at least i didnt think so (slow, difficult to use, etc). I had trouble finding what i needed to get my system going the same way as i have it in ubuntu.  I'm sure there is just a bit of a learning curve that i could go through to get it working, but i couldnt find anything out there nearly as good as the ubuntu guide as far as documentation for how to do the sh*t done.  
SUSE definitely does seem more professional overall. But in terms of a well rounded, easy to use, yet powerful system, i choose ubuntu still. Now if they could get the installer to work with ati x series cards i would be very greatful. The funny thing is that dapper worked fine, it wasnt till edgy eft that they messed up the installer. It seems like every release of ubuntu they'll fix one thing but break 2 others.. Come on guys.... i tried feisty the other day only to find out it the installer and system in general was even more buggy.. that is understandable though since it is still early in development.. I really hope they get stuff fixed before they release the next one.. no more of this, release it on x day no matter what.. i say get the **** working and then release it.

---

### Post by _simon_ on 2007-02-14
> **darkenedday said:**
> ok so that worked, new issue, when i type beryl --replace i get the following output and my desktop goes black (no icon no bg), i have all the efects, but this a rather annoying problem, also if i minimise too much beryl crashes

mike@Apollo:~> beryl --replace
XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present

** (process:12751): WARNING **: get_setting_is_integrated not found in backend ini

** (process:12751): WARNING **: get_setting_is_read_only not found in backend ini

** (process:12751): WARNING **: get_setting_is_integrated not found in backend ini

** (process:12751): WARNING **: get_setting_is_read_only not found in backend ini
Initiating splash
beryl: water: GL_ARB_fragment_program is missing
Reloading all options.

Can I check that you have done this?

```

su
nvidia-xconfig --composite
nvidia-xconfig --allow-glx-with-composite
nvidia-xconfig --render-accel
nvidia-xconfig --add-argb-glx-visuals

```

---

### Post by pain of salvation on 2007-02-14
To enable XGL, you should just go to Control Center and enable Desktop Effects.

To use Beryl, see this tutorial: [http://en.opensuse.org/Beryl](http://en.opensuse.org/Beryl)

---

### Post by darkenedday on 2007-02-14
i'v done what u said simon, and also i use that guide pain mentioned, after a little thought (and dumb luck) i managed to figure it all out, the black cube was solved by simply beryl-manager > advanced beryl options > rendering path > copy, everything works great now thanks for all the help and input

---

### Post by _simon_ on 2007-02-14
Glad you got it sorted :)

---

### Post by julian67 on 2007-02-16
I even have xgl/compiz enabled on a laptop with only 1.2Ghz Pentium M cpu and 512MB RAM. It was installed (but not enabled) by default. In the control centre I was advised that my graphics chip may not support it (Intel 855 integrated) but I tried it anyway and it works fine (a little slow). My gf has openSuse on a laptop with 1.6 Ghz Pentium M and 768MB RAM and an integrated 915 graphics ( I think) and it works beautifully. 

All I had to do for Gnome was enable it in the control centre. For KDE you need to set the window manager in Yast system config and then again in Kcontrol>KDE components>session manager. So it's simpler initially in Gnome but in KDE you can switch between regular 2d and compiz in KDE session manager without needing to logout and in again. 

I didn't try Beryl, I'm pretty sure it needs more graphics resources than compiz (might be wrong though).

---

