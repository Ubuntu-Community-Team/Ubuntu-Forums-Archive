---
title: "Sound card problem in fresh install of 6.10"
date: 2007-02-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by latanerp on 2007-02-15
Just bought a new PC and it came with Windows Vista... wow does it suck (it crashed on my first boot at home!).  Anyway, trying Ubuntu for the first time (actually, this is my first debian-based os, too) 

I am having trouble getting my sound card to work, and I've browsed the forums pretty extensively and already tried a few of the suggestions but to no avail.  I first noticed it when I attempted to run Totem and got the "Could not open resource for writing." Only then did I notice that the Volume Control device was marked with a big red X and when clicked warned, "No volume control GStreamer plugins and/or devices found." Have the most up-to-date GStreamer plugins, so I figured it was the latter...

Tried aplay -l and sure enough,  no soundcards found.

It's an Embedded Realtek ALC888 on a AMD Athlon 64 X2 Dual Core 4200+ processor.  

Any suggestions appreciated greatly, sick of using Vista.

---

### Post by renzokuken on 2007-02-15
i have an embedded Realtek ALC883 chipset that wouldnt work until i compile the latest "alsa-driver" (version 0.1.14rc2) from source. after that it was fine........may be worth a try

---

### Post by latanerp on 2007-02-15
OK thanks, tried that and rebooted and it still didn't work.  Tried compiling it with the command --with-card=hda-intel as according to [this post]("http://www.nvnews.net/vbulletin/showpost.php?p=1110601&postcount=5"), also tried to find the config options for the ALC888 module in the Alsa Configuration Manual recommended in [this post]("http://www.ubuntuforums.org/showpost.php?p=2013895&postcount=17"), but it did not include the ALC888 so I wasn't able to try that person's suggestion.  Nor cold I find the ALC888 included on the [Alsa Soundcard Driver page]("http://www.alsa-project.org/alsa-doc/index.php?vendor=All#matrix")... 
-=-=-=-=-


I found a driver from Realtek for Linux, and now I am trying to install it, I guess we'll see what happens.

---

### Post by latanerp on 2007-02-15
Argh!  The sound driver WORKED!  My sound card was detected, the programs are opening without the error i.e. "Could not open resource for writing."

but now there's still no SOUND coming out of the speakers!?  It does not appear to be muted.

---

### Post by latanerp on 2007-02-15
Another suggestion I found was to run alsamixer and adjust the settings; but when I try to run alsamixer I get this error:

> 
alsamixer: function snd_mixer_load failed: Invalid argument


it's probably also relevant to note that after running, alsaconf has outputted this in the terminal:

> 
$ alsaconf
Building card database..

Running update-modules...
Loading driver...
/usr/sbin/alsaconf: line 684: /etc/init.d/alsa: No such file or directory
Setting default volumes...

Playing WAVE '/usr/share/sounds/alsa/test.wav' : Signed 16 bit Little Endian, Rate 22050 Hz, Stereo
Saving the mixer setup used for this in /etc/asound.state.
/usr/sbin/alsactl: get_control:149: Cannot read control info '2,0,0,Front Playback Volume,0': Invalid argument


Any suggestions would be really appreciated, gotta get back to work now (in Vista, I guess)..
------------

ETA:  Had some time this evening to mess around with it some more.  Tried a bunch of different things that did not help.  Installed gnome-alsamixer and was able to turn up the volume control to maximum which finally produced some (very little) sound.  Still could not get alsamixer to run (see above errors), then finally tried recompiling the alsa-driver again; and this time it worked.  Could I possibly have NOT tried recompiling it again AFTER installing the Realtek Driver?  Maybe... but it was almost a week ago so I don't remember.

Anyways--since, in my many searches, I noticed other people have had similar problems with Ubuntu (and other distros) and the onboard Realtek sound card, I just wanted to add the link that I found the driver at: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#High%20Definition%20Audio%20Codecs](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#High%20Definition%20Audio%20Codecs)

---

