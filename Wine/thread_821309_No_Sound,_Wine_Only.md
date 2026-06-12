---
title: "No Sound, Wine Only"
date: 2008-06-07
forum: Wine
---

### Post by Striken on 2008-06-07
Warning: I've been using Ubuntu for a total of 2 days. I'm running 8.04 using the Wubi installer on a Windows XP PC.

Problem: I've installed Wine 1.0-rc3 and got it running the game Guild Wars fine with no problems except that I have no sound. I only have a headset, no speakers, and the headset works fine for Rhythmbox/Totem/etc.
 
I followed a guide on a WoW forum to set up Wine for Headsets so that I can see 'USB Audio' under the ALSA Driver in winecfg, but still get no sounds from either the game or the Test Sound button (I do not receive an error when I hit the Test button, just no sound). I have tried it with all the driver options, no luck.
 
Help please?

---

### Post by mr_boo1711 on 2008-06-07
Hey Stricken

I'm by no means an expert, but did you try double-clicking on the speaker icon at the top of your desktop and adjusting ALL your volume controls (Not just the master one.).  I had the same issue after a clean install, and Ubunutu had started life with all the volume controls at zero. Sometimes its a simple thing that needs tweaked. :)

Also - maybe not related to your problem but maybe worth mentioning.  Whenever I use a mediaplayer (Amarok in my case) when I run Wine, I dont get ANY sound through wine at all.  It seems that the mediaplayer takes priority.

If it doesnt work then post back and we'll try looking at some of the more complicated stuff. ;)

---

### Post by Striken on 2008-06-07
In the volume control panel, I had earlier found that none of the sliders in the original panel affected my headphones, but I did set them all to max anyway. 
 
To change the volume of my headphones, I had to go to File-Change Device and selected USB Headset (ALSA Mixer), where there are only two sliders: Microphone and Speaker. Both of those were turned up already from when I got Rhythmbox running how I like.
 
And I ran Wine/Guild Wars with no other applications running, but still no sound.
 
Added: I'm heading to bed now (4am), so for any questions asked withing the next ~10 hours, don't expect a speedy response.

---

### Post by mr_boo1711 on 2008-06-07
Ok I suppose its worth eliminating the easy stuff first. ;)

I'm at work just now - I'll check back later when I get home and see what replies there are.  If you're still stuck then I'll see what I can suggest, and maybe we can get your sound working... :-k

---

### Post by CameO73 on 2008-06-07
There is a [serious problem between PulseAudio and Wine]("http://forum.winehq.org/viewtopic.php?p=5812&sid=9a68a77970602594fede00edd4eec934"). And as you can read in that thread ... it won't be fixed by the Wine people.

There appears to be a [possible solution]("http://blog.paulbetts.org/index.php/2007/05/27/make-wine-and-pulseaudio-get-along/"), although I can't get it to work with the winecfg utility (keep getting the audio error when tested).

UPDATE!
OK, it appears the Sound Test always fails, but the programs run with sound (using **padsp**). I've succesfully tested this with [this weird game](http://playthisthing.com/lost-static). Can't say much about any sound lag, though. But that could be fixed by adding your user to the pulse-rt (realtime priority) group.

---

### Post by Striken on 2008-06-07
I followed that guide, and can now see "PulseAudio Virtual OSS" under the OSS Driver when I use "padsp winecfg".
 
After selecting the OSS driver, I launched the program using the command "padsp wine "Z:\host\Program Files\Guild Wars\Gw.exe" -windowed" but still have no sound :(
 
Note: When I hit the Test Audio button, I don't get an error, just no sound.

Update: When I run the "alsamixer" command, it has the Card set as Intel ICH5 and not my headset, which I'm pretty sure I don't want. Maybe there is a way to change this setting?

Update #2: I fixed my sound in Wine by running "sudo gedit /etc/asound.conf" and putting:

pcm.!default {
type hw
card 1
}
ctl.!default {
type hw
card 1
}
 
Now, when I run "alsamixer" the Card is my USB Headset and the Test Audio button in winecfg works.
 
BUT, now my Rhythmbox Music Player crashes my system when I try and play music and I have no sound in Totem movie player. Blarg.

---

### Post by Fred_E _krugar on 2008-06-07
Have you tried to just uninstall pulseaudio??? I did and it helped out on everything.


I got tired of doing all the Pulse Audio stuff, so I installed Kubuntu and there is no Pulse Audio to deal with.

---

### Post by Striken on 2008-06-07
Well I fixed it :)
 
After using "sudo gedit /etc/asound.conf" to set my headset as the default card (this is what made it work in Wine but broke everything else), I had to go back to Preferences-Sound and change all the options from USB Audio to ALSA to get other applications to work.
 
Now I get sound everywhere.

---

