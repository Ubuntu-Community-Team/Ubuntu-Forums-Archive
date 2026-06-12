---
title: "Wine Sound Problems on Ubuntu 12.04"
date: 2012-06-25
forum: Wine
---

### Post by Fernhill Linux Project on 2012-06-25
I am no expert on wine, but I read this on Facebook earlier, it has already helped a couple of people and works on 64bit too, so we are sharing it here :

> Marvin Mallari posted to Ubuntu 15 hours ago - For people having sound problems with Wine (like sound is garbled, static, non existant) in Ubuntu 12.04 (w/ Unity and Pulse/ALSA) i found a solution. Go to Synaptic Package Manager, install "ia32-libs-multiarch", it will ask to modify or install other packages, install all packages and restart (not log out then log in) Wine should now play audio perfectly and stable. note: i did this on a 32bit comp, for 64bit, there is probably a different package or maybe the package will work because it says "multiarch" i will try on my 64bit machine later. PS i don't have an account on any Wine or Ubuntu fourms so if someone can please share this somewhere that needs it that would be much appreciated!

Marvin Mallari - Ia32 probably isn't the solution but when I read the addition packages synaptic modifies and installs, a couple of them are for pulse so it is probably those packages that fixed it but in any case ia32 installed whatever it needed to work. It also seems like pulse cpu usage has dropped.

---

### Post by blueshead on 2012-06-25
Thank you,Thank you!  It worked in Ubuntu 12.04 64 bit.

There is a program I use to play some game demos in wine. Sound was always garbled.. Now clear sound! YESSS!

;)

---

### Post by Fernhill Linux Project on 2012-06-25
Thanks for confirming it works for you too and glad it helped!
Please share...

Thanks to the Forum Moderators for moving this thread to the correct place. :o

---

### Post by Sneckster on 2012-06-27
Just installed it as I have been getting no sound on games in Wine even though the audio test button worked ok.   

I now have sound on Sim City, but alas still not solved my lack of audio in lego batman.  Still, looks like it fixed something :)

---

### Post by diogenes83 on 2012-11-25
At first this did not work for me. However making wine use alsa only solved the problem. As stated in this thread.
[http://askubuntu.com/questions/77210/how-to-change-the-default-audio-in-wine-to-alsa-only](http://askubuntu.com/questions/77210/how-to-change-the-default-audio-in-wine-to-alsa-only)

---

### Post by LillyDragon on 2012-11-26
I must be a special case, because no matter what solution I stumble across, even this one, my sound problems with WINE *will not* go away. What really gets to me is that I can't easily revert to a version of WINE with working sound, like I could when the deb archive was still active. I don't care if the WINE devs are busy rebuilding the sound system, not including a tiny patch for pulse audio to hold everyone over in the meantime is a baffling decision at best.

So yeah, this solution did nothing for me, even after logging in/out, reinstalling certain Windows programs and setting sound=ALSA in Winetricks. Please allow me to vent my frustration in a non-violent manner : 

[IMG]http://gifsoup.com/webroot/animatedgifs/53500_o.gif[/IMG]

Thank you for posting it regardless. I'm glad it's working for some people, just disheartened I can't get WINE to cooperate myself without cringing at the thought of compiling it from source with the pulseaudio patch myself, only to fear that one might go in flames too.

---

### Post by produnis on 2013-06-16
thank you so much, installing "[COLOR=#000000]*ia32-libs-multiarch" made sound finally work in PlayOnLinux!!!*[/COLOR]

---

### Post by ubuntownick on 2013-06-18
I have opposite problem. I would like to play under wine without hearing a thing. I play PES2011. Recently I switched form Precise to Mint 13 xfce. On old system i was able to turn off sound in game by turning of wine sound source in pulse, but on Mint xfce with brand new wine and playonlinux i can't, because Pulse doesn't show wine sound source at all. Turning off in internal game settings doesn't work either. Any ideas?
[SIZE=1]-Computer-
Processor        : 2x AMD Athlon(tm) 64 X2 Dual Core Processor 4000+
Memory        : 4050MB (1322MB used)
Operating System        : Linux Mint 13 Maya
Date/Time        : wto, 18 cze 2013, 08:21:19
-Display-
Resolution        : 1920x1080 pixels
OpenGL Renderer        : GeForce 8600 GT/PCIe/SSE2
X11 Vendor        : The X.Org Foundation
-Multimedia-
Audio Adapter        : CMI8786 - Xonar DG
Audio Adapter        : HDA-Intel - HDA NVidia[/SIZE]

---

### Post by user_of_gnomes on 2013-06-18
Can't you just configure Wine to play over the wrong output device like the optical out?

---

### Post by ubuntownick on 2013-06-18
Wine treaks doesn't work after update. Maybe you can show me where I can find config files. That would be great:)
One more thing. It looks like wine take over my whole sound resources. If wine plays, nothing else can.

---

### Post by p0ndo on 2013-07-14
Thanks! This fixed sound on in the Netflix Desktop app in Xubuntu 12.04 64-bit for me.

---

### Post by millerthegorilla on 2013-08-04
Hi - I've had real problems getting netflix-desktop to work without pulseaudio so that it only uses alsa.  I found that installing the following gstreamer package works.  This should probably work in cases where you are using pulseaudio as well as gstreamer is an intermediary library between the wine-browser (and its plugins -gecko/silverlight) and the alsa interface between software and hardware.  I am using a 64bit system so netflix-desktop which is compiled as 32 bit may not have been finding the appropriate version of gstreamers alsa plugin.  If this doesn't work for you (with other software apps/games) then try the 32 bit version of ffmpeg which is a gstreamer alternative.
The library that I installed from synaptic is gstreamer0.10-alsa:i386

gd luck!

*edit - stopped working again after login.

---

### Post by Wraakvol on 2013-08-16
Hi, everyone!

It seems it fixed my audio issues on Ubuntu 12.04 as well. Thanks! :D

---

### Post by gregor-pardon on 2014-02-09
We have updated 25 school laptops to 12.04 and we are using wine to run some educational software.
on 21 laptops everything works fine (the laptops have all been cloned so same setting) but 4 older IBM Thinkpad R40 have the problem.
The sound inside wine (and only in wine) is scrabled. 
Unfortunately installing [COLOR=#000000][I]ia32-libs-multiarch" did not help.
[/I][/COLOR]Any help would be appreciated.

---

### Post by user_of_gnomes on 2014-02-09
> **gregor-pardon said:**
> We have updated 25 school laptops to 12.04 and we are using wine to run some educational software.
on 21 laptops everything works fine (the laptops have all been cloned so same setting) but 4 older IBM Thinkpad R40 have the problem.
The sound inside wine (and only in wine) is scrabled. 
Unfortunately installing [COLOR=#000000][I]ia32-libs-multiarch" did not help.
[/I][/COLOR]Any help would be appreciated.

Did you make sure that Wine has been fully updated?

---

### Post by gregor-pardon on 2014-02-10
Yes, sorry updating might have been misleading:
We installed a fresh ubuntu 12.04 including wine on one of the laptops and then cloned that to the rest of the laptops.
And the other 21 laptops run just fine. So at the moment i have no idea what to do next.

---

### Post by user_of_gnomes on 2014-02-11
I think you should start a new thread and supply the readers with some hardware information. I can't really help you, I'm not very good at trouble shooting hardware issues under Linux.

---

### Post by gregor-pardon on 2014-02-15
Ok. Will do that. Many thanks anyway.

---

