---
title: "Sound issue with ubuntu + ALSA"
date: 2007-05-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by dlikhten on 2007-05-06
I had the following problems when trying to use my sound card with the ubuntu default installation:

My speakers are plugged in, my sound is on, everything seems to be in order... but no sound. However when i set the drivers in the sound options to the ADC driver, it seems to play sound in the TEST, and in SOME APPLICATIONS but not all, not even the beeps and bloops that ubuntu would make (sounds) are played. So what is wrong?

Well I went on ubuntu IRC and with some ideas realized that I had a built-in sound card in my motherboard... HMMM I thought... but why was it loading instead of my SoundBlaster Audigy 2? -- Does not matter the fact is, ubuntu decided that this is my sound card. Infact I tested it out, that was the card which was playing all the audio on "Audodetect" settings along with ubuntu sounds.

How did I fix this?
1) Determine which module is the SoundBlaster Audigy 2 card and which is the Motherboard card (mine was VIS 2373 -- module: snd-vs23xx).
2) BLACKLIST it and the Modem drivers in /etc/modprobe.d/
File: blacklist
>> blacklist snd-vs23xx
File: blacklist-modem
>> blacklist snd-vs23xx-modem
3) Remove the loading of this driver
File: alsa-base
>> Comment the loading of that module.

4) Well guess what, it was still not working. After some pain I discovered that my WAVE sound was muted (WHY? NO IDEA!!!) I unmuted it and sound... yes after long pain I had sound.

Here is some hardware bullet points for my machine
Motherboard: k8v delux (hate it -- asus is the worst source of drivers)
Sound Card: SoundBlaster Audigy 2
Architecture: x86_64

I post it here in hopes that:
1) Others with this pain will have an easier time figuring out what to do.
2) Developers would see this and make a user-friendly ui (or at worst TEXT) way to switch which sound card is used by ubunbu (or rather ALSA)

Good Luck
--Dmitriy

---

### Post by holomorph on 2007-05-17
Just curious, before you removed modules etc for your onboard card, did you try selecting your SoundBlaster as the default?  
Crap I can't find where to do this now, used to be in the system menu somewhere. System->Prefernces->Sound seems like it should be the right place, but I'm not sure that selecting the "Device"  under Default Mixer Tracks is what I'm looknig for . .  *shrug*

I had some trouble w/ some things sending sound to the wrong soundcard and fixed it by adding the following to /etc/modprobe.d/alsa-base
```

options snd-emu10k1 index=0
options snd-hda-intel index=1

```

So both soundcards still work, but now my Soundblaster Live is the first soundcard (index 0) and gets used by default.

---

