---
title: "Sound issues in Flash"
date: 2009-03-17
forum: x86 64-bit Users
---

### Post by idumych on 2009-03-17
I have a fresh install of Intrepid, and all I've done so far is update, and install kubuntu-restricted-extras. Now, when I try to watch youtube videos, I get no sound. I do have sound playback from Amarok however. What's the deal?

---

### Post by iamkrazee on 2009-03-18
Just check once if your flash isn't muted somehow, else just re-install flash.

---

### Post by Bram77 on 2009-04-24
I'm having the same problem in Jaunty (32bit). I'm not getting any sound from flash. All is well in Amarok, VLC SMplayer etc.. My soundcard is a Creative X-Fi platinum using ALSA with the Creative drivers. In 8.10 the sound in flash was working with the same drivers.

---

### Post by Bram77 on 2009-04-28
I've fixed it in 9.04 32bit by resetting the default ALSA soundcard.

```
~$ asoundconf list
Names of available sound cards:
HDMI
Headset
XFi
~$ asoundconf set-default-card XFi
```

I use a Creative XFi card, so you should replace XFi to whatever card has your preference in the output of "asoundconf list".

---

### Post by Zorael on 2009-04-29
(Pasting an earlier post.)

My Intel HDA card has several channels that all affect output (Master, Headphone, PCM and Front). They're multiplicative, in the sense that if I have them all at 80%, the end volume is 0.8*0.8*0.8*0.8 = 0.4096, ~41%. My multimedia keys on this laptop control the Master volume, so I just set the other three reasonably high and live with it.

Turns out that KDE system sounds and Amarok 2 (amongst others, perhaps) disregard the PCM channel, while still obeying Master, Headphone and Front. Flash depends on them all. And my PCM volume had somehow dropped to 0.

KDE/Amarok: 0.8*0.8*1*0.8 = **0.512**
Flash: 0.8*0.8*[COLOR="Red"]**0**[/COLOR]*0.8 = [COLOR="Red"]**0**[/COLOR]

Pop up a terminal and start **alsamixer** to make sure that's not what's causing it for you.
```
$ alsamixer
```
May need to make that **alsamixer _-Dhw_** if you're running Pulse, not sure.

---

