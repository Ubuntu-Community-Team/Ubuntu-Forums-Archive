---
title: "yay esd is bad"
date: 2005-04-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by momerath on 2005-04-14
Alright i'm relativly new to Ubuntu but i'm not so new to Linux in general just to set the playing field here.  I'm having all kinds of problems...well not really i'm just a bit anal.  I hate how esd sounds.  Its terrible, its like an echo or something even after i've set the EQ properly.  There is also a slight delay in any sound played.  When i'm in xmms and i set it to use the proper plugin(ALSA) it just sits there and slides the visualizer bars up and down but makes no sound.  Real fun...is there a way to just get rid of the lovely esd thing and use straight up alsa?  alsa is a lot better in my experiences.  Or is there some way to make esd not sound like crap?  btw i'm sorry if this has been posted before but after searching for a bit to make sure i didnt really see anything posted like this.  Thanks in advance.

---

### Post by domesticatewhat on 2005-04-14
1. Install alsa-oss
2. Install alsa-headers
3. Make sure you have libesd0 and gstreamer0.8-esd installed. (if not, install)
4. Make sure esound and esound-common are installed. (if not, install)
5. alsa-base
6. alsa-utils
7. gstreamer0.8-alsa
8. libpt-plugins-alsa
9. vlc-plugin-esd

Ok, next.
1. Right click on the little volume control in your top panel and the
choose Open volume control.
2a. *IF* it opens, you should see two tabs, one for OSS and the other
for Alsa. Make sure nothing is muted.

We're going to switch you to a sound daemon that allows multiple sounds.
1. In gstreamer-properties, change the Default Sink to output: ESD -
Enlightenment Sound Daemon
2. Change your Output plugin in XMMS to eSound output plugin.
3. Enable your sound server startup.

Read that somewhere in the forums and worked for me.

---

### Post by momerath on 2005-04-14
Ok that works for diminishing some of the delay i think.  but it still sounds awful.  When i had Fedora Core 3 installed some how it managed to get the audio to work quite nicely.  in fact it sounded better than it did in Windows XP.  By the way i suppose i should put my specs on here.  I'm using the onboard audio on the K8N Neo2 Nforce3 motherboard which is an AMD64 platform.  If there is a way to get this thing to sound better that would be great.  but as of right now i'm a bit dissapointed with how Ubuntu has handled the sound configuration.  Everything else is great though which is why i would really like to figure out a way to get this thing to not sound like crap.

---

### Post by momerath on 2005-04-15
Yeah um...esd still sounds like crap...I can't just get rid of it and use ALSA?

---

