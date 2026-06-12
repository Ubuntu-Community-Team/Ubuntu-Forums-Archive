---
title: "sound issues with 64x2 AMD Athlon 3800+"
date: 2007-06-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by FloSynergy on 2007-06-21
hey folks,

really having trouble with sound, more detail posted [here]("http://ubuntuforums.org/showthread.php?p=2887033#post2887033").

Please help...?

thanks & be well, flo

---

### Post by Cappy on 2007-06-21
Hi, in the volume control (alsamixer) goto Edit-->Preferences and check all the boxes there if you havn't already.
If you have an "Audigy Analog/Digital Output Jack" you'll want to try with that both on and off.

The controls your sound will come out of will probably be "PCM" and "Front" but obviously you should have everything unmuted. If you have an option of "PCM" in recording you will want to turn that off (or else your mic input will be your sound output).

You may want to try gnome-alsamixer, it's a little easier imo:
```
sudo apt-get install gnome-alsamixer
```
To run:
```
gnome-alsamixer &
```

Edit: Also, mute that "IEC958 Capture" that you have. Found that on the alsa-project page.

---

### Post by FloSynergy on 2007-06-22
hi cappy,

many thanks for your response.
i had installed gnome alsamixer already - and i've checked through all the different options here, checking boxes, enablein/disabling various different options, including muting the headphones and iec958.

no noticeable results...:(

i do not see a record tab on gnome alsamixer, nor on the alsamixergui, though i remember having seen it on one of the kde-gui's. i'll pop in to kde to see if it's using the same port for record and playback.

what is interesting is that under system>preferences>sound,
there seem tobe two different options for the soundcard: the Realtek sound chip (oss mixer), and HDA  Nvidia (alsamixer).

could there be a conflict between these two sound systems?

thanks a lot,

flo

---

### Post by FloSynergy on 2007-06-22
hey folks,

thanks for the ref re hi-def cards.

i've been struggling for 3 days to get my sound to work...

then, sd-plissken pointed out [this]("http://ubuntuforums.org/showthread.php?t=239995&page=5") thread (it's what i used in the end) and [this]("p://ubuntuforums.org/showthread.php?t=455147") and [the wiki]("https://wiki.ubuntu.com/UbuntuStudio/HowToInstallTheLastAlsaDriverForProSoundCard?highlight=%28alsa%29").

now, i'm rocking to my favourite marley-tunes 

get-up - stand-up.....feel dem spirit!:guitar:

gigathanks,

flo

---

### Post by fakie_flip on 2007-06-25
Get the latest alsa-driver, alsa-libs, and alsa-utils source code and compile it.

---

