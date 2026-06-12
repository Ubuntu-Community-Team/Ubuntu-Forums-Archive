---
title: "X-Fi Xtreme Audio not working"
date: 2008-02-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by mgw854 on 2008-02-24
I am trying to get my X-Fi Xtreme Audio card working.  I know these cards have issues with Linux.  I am running Ubuntu 8.04 Alpha 5 on AMD64.  I have tried to use the OSS.deb file in this [tutorial]("http://ubuntuforums.org/showthread.php?t=571656").  I tried the other option in that tutorial, but I couldn't get through the steps.  Anyways, I also tried using the [drivers from Creative]("http://opensource.creative.com/soundcard.html"), but they wouldn't build because my machine is not 64-bit (it is).  I have also rebuilt ALSA from the new drivers (which are supposed to work with the card). I understand Linux to a point, but this has me stumped.  Can anyone provide some assistance?

---

### Post by Kilz on 2008-02-24
> **mgw854 said:**
> I am trying to get my X-Fi Xtreme Audio card working.  I know these cards have issues with Linux.  I am running Ubuntu 8.04 Alpha 5 on AMD64.  I have tried to use the OSS.deb file in this [tutorial]("http://ubuntuforums.org/showthread.php?t=571656").  I tried the other option in that tutorial, but I couldn't get through the steps.  Anyways, I also tried using the [drivers from Creative]("http://opensource.creative.com/soundcard.html"), but they wouldn't build because my machine is not 64-bit (it is).  I have also rebuilt ALSA from the new drivers (which are supposed to work with the card). I understand Linux to a point, but this has me stumped.  Can anyone provide some assistance?

Please provide the results of
```
uname -a
```

---

### Post by mgw854 on 2008-02-25
Linux Matthew-LNX 2.6.24-8-generic #1 SMP Thu Feb 14 20:13:27 UTC 2008 x86_64 GNU/Linux

---

### Post by NullHead on 2008-02-25
I've updated my guide and there is another link you should use if you're using extreme audio.

[http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg21618.html](http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg21618.html)

---

### Post by Yellow Pasque on 2008-02-26
Just curious, why couldn't you get through my OSS Howto? Anyway.. The .deb packaging is no longer needed since the envy24ht code has been open-sourced and that was the main reason I made the guide for the .deb.

Now, you should build straight from source with this script [http://paste.ubuntu-nl.org/56973/](http://paste.ubuntu-nl.org/56973/)

---

### Post by mgw854 on 2008-02-26
> **NullHead said:**
> I've updated my guide and there is another link you should use if you're using extreme audio.

[http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg21618.html](http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg21618.html)

OK, I just tried the guide again (using 1.0.16 instead of 15, if that makes any difference?).  At the end of make install, I get this warning:

WARNING!!! The mixer channels for the ALSA driver are muted by default!!!
**************************************************************************
You would use some ALSA or OSS mixer to set the appropriate volume.

---------------------------
Anyways, when I restarted, I get this error message when I try to open the volume control:

Dialog box 1 says that there were no GStreamer plugins found
Dialog box 2 says "The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu."

Again, still no sound.

---

### Post by NullHead on 2008-02-26
Well if thats all it's saying in terms of errors yah I guess you're good to go.

---

### Post by mgw854 on 2008-02-26
> **Temüjin said:**
> Just curious, why couldn't you get through my OSS Howto? Anyway.. The .deb packaging is no longer needed since the envy24ht code has been open-sourced and that was the main reason I made the guide for the .deb.

Now, you should build straight from source with this script [http://paste.ubuntu-nl.org/56973/](http://paste.ubuntu-nl.org/56973/)

Tried to run this script, but it returned an error: "bash: ./compile-oss.sh: /bin/sh^M: bad interpreter: No such file or directory".

---

### Post by mgw854 on 2008-02-26
> **NullHead said:**
> Well if thats all it's saying in terms of errors yah I guess you're good to go.

See the updated portion of that message.  It still doesn't work.

---

### Post by NullHead on 2008-02-26
Use ```
ossxmixer
``` to use your mixer.

---

### Post by mgw854 on 2008-02-26
> **NullHead said:**
> Use ```
ossxmixer
``` to use your mixer.

Don't you mean ossxmix?  Anyways, I used that, and it spit back "Mixer 0 does not exist"

---

### Post by mgw854 on 2008-02-28
Has anybody else thought of anything?  I tried looking up Mixer 0 does not exist, and this forum is the third best option- the other two being irrelevant.

---

### Post by jdevine420 on 2008-02-28
I'm having the same exact problem as you except I'm using Gutsy 7.10. I'm using the x-fi fatality but I've gone through the same steps as you and I am producing the same results with no sound. 
I have onboard ac97 sound that works but I'd rather use the soundblaster.

---

### Post by mgw854 on 2008-02-28
I also have onboard audio, but again, I'd rather hear it out of a read sound card.

---

### Post by obloxeon on 2008-02-28
Same issue here.

---

### Post by mgw854 on 2008-02-29
Obviously, a few of us are having this problem... does anyone have any more suggestions on how to fix this?

---

### Post by bobdob20 on 2008-03-01
To get my X-fi extreme music to work i had to link /dev/oss/sbxfi0/pcm0 to /dev/dsp.

i used ossinfo to find the output of my sound card.

```
Sound Blaster X-Fi (SB046x/067x/076x) output  /dev/oss/sbxfi0/pcm0  (device index 0)

```

there is also a patch for the volume control to work with oss.

32bit:
[http://homepage.ntlworld.com/clive_wright/download/gstreamer-ossv4.tar.gz](http://homepage.ntlworld.com/clive_wright/download/gstreamer-ossv4.tar.gz)
64bit:
[http://ubuntuforums.org/attachment.php?attachmentid=55770&d=1199848927](http://ubuntuforums.org/attachment.php?attachmentid=55770&d=1199848927)

hope thats is some help.

---

### Post by Zenbios on 2008-03-05
> **NullHead said:**
> I've updated my guide and there is another link you should use if you're using extreme audio.

[http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg21618.html](http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg21618.html)

first of all, sorry about my english, but im swedish.
secend, thanks för that link. i now got sound in me extreme audio.
but one problem, i can change the volume on my speakers,
but i cant change it with either, audacious, on the top right next to the clock and date,
on my keybord anymore. it&#347; not that big problem, but it would be nice to change there again and not only on the speakers. does anyone knows why it is lika that now?
it workt before with my sound card on the motherboard.

---

### Post by bobdob20 on 2008-03-05
Applying one of these patches should fix the volume control on the panel.

32bit:
[http://homepage.ntlworld.com/clive_w...r-ossv4.tar.gz](http://homepage.ntlworld.com/clive_w...r-ossv4.tar.gz)
64bit:
[http://ubuntuforums.org/attachment.p...0&d=1199848927](http://ubuntuforums.org/attachment.p...0&d=1199848927)

---

### Post by NullHead on 2008-03-05
> **Zenbios said:**
> first of all, sorry about my english, but im swedish.
secend, thanks för that link. i now got sound in me extreme audio.
but one problem, i can change the volume on my speakers,
but i cant change it with either, audacious, on the top right next to the clock and date,
on my keybord anymore. it&#347; not that big problem, but it would be nice to change there again and not only on the speakers. does anyone knows why it is lika that now?
it workt before with my sound card on the motherboard.

Did you follow my guide or the link? I did not go through the installation with my guide. 

Please help me understand. Your sound that is built onto your motherboard works? And what model of the Creative X-FI do you have? The link I gave earlier is for Creative X-FI Extreme Audio **only** not any of the others... if you have a card such as a *"Extreme Gamer"* than you need to follow my guide [here]("http://ubuntuforums.org/showthread.php?t=571656"). 

If you installed OSS you're going to need to install some other things to get your sound panel applet to work.

NOTE: You speak english just fine ;)

---

### Post by Zenbios on 2008-03-05
> **NullHead said:**
> Did you follow my guide or the link? I did not go through the installation with my guide. 

Please help me understand. Your sound that is built onto your motherboard works? And what model of the Creative X-FI do you have? The link I gave earlier is for Creative X-FI Extreme Audio **only** not any of the others... if you have a card such as a *"Extreme Gamer"* than you need to follow my guide [here]("http://ubuntuforums.org/showthread.php?t=571656"). 

If you installed OSS you're going to need to install some other things to get your sound panel applet to work.

NOTE: You speak english just fine ;)

i installed the alsa driver, not the howto here, just the link. when i used the sound on my motherbord,
i could change the volyme on my keybord and, audacious, but now i have disabled the sound in BIOS
and only use my extreme audio. the sound is fine. but i cant change the volume on my keybord, audacious, and on the top right next to the clock. when i change it, it dosent make any diffrent.
the same volyme what ever i do. but it workt before. now i only use the extreme audio.

PS: the howto works fine for my other card, X-FI extreme gamer.

---

### Post by NullHead on 2008-03-05
OK I understand now thanks! :)

What I would do it make a new sound applet by right clicking on the the menu and adding custom applet use the command alsamixer.

---

### Post by mgw854 on 2008-03-06
OK, I tried installing that library, but when I run ossinfo, it says that /dev/mixer does not exist.  Any one know why?

---

