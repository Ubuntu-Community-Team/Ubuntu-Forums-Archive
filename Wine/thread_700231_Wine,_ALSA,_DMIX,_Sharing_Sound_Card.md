---
title: "Wine, ALSA, DMIX, Sharing Sound Card"
date: 2008-02-18
forum: Wine
---

### Post by ushimitsudoki on 2008-02-18
I am trying to get Ventrilo working with Enemy Territory:Quake Wars (ETQW). Ventrilo is running under Wine. (I don't want to use ventrilo, but it's what others are using - so no need to tell me about TeamSpeak or mumble - I already know about them, and would use them if it were and option!)

So, I need to be able to share the sound card, using DMIX I assume. All applications work fine if they are the only thing running. All are configured to use ALSA. I have a ~/.asoundrc that enable software sound mixing on my sound card (Edirol UA-25).

I can play multiple .wav files at the same time from multiple terminals.. I can also listen to streaming radio in Rhythmbox and aplay a wav file at the same time. So, it would appear that the basic software mixing OUTSIDE of Wine is working fine.

I found a lot of references back around 2005 for an [ALSA] setting in ~/.wine/config. But that file has not been used for a couple of years, and Wine uses the registry now for settings. (Example here: [http://wiki.jswindle.com/index.php/Wine_Config_File#Wine_and_DMIX](http://wiki.jswindle.com/index.php/Wine_Config_File#Wine_and_DMIX))

I asked around in IRC, and was referred to: [http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys), but I couldn't get anything working there and I tried several things.

Launching from Wine with aoss did not help.

So, has anyone gotten anything like this working? Looking for a way to make sure the application I open in Wine does not get "exclusive" rights on my sound card!

---

### Post by ushimitsudoki on 2008-02-19
I got this working finally!

I wrote it up in my blog here: [http://meandubuntu.wordpress.com/2008/02/19/sharing-alsa-audio-from-wine/](http://meandubuntu.wordpress.com/2008/02/19/sharing-alsa-audio-from-wine/)

But basically it involved setting the following in the registry for Wine:
[Software\\Wine\\Alsa Driver]
“AutoScanCards”=”N”
“DeviceCount”=”1&#8243;
“DeviceCTL1&#8243;=”default”
“DevicePCM1&#8243;=”default”
“UseDirectHW”=”N”

---

### Post by pizpot on 2008-02-26
thanks man!

---

### Post by 8086 on 2008-06-25
didn't work for me. still get the dmix error.

---

### Post by ishkabob on 2008-09-22
Your asound.conf did allow me to talk in vent and hear everything ok in ETQW.  I was wondering if there was some way I could tweak the asound.conf to allow me to use my mic in both ventrilo, and in the VOIP function in ETQW.  Ventrilo is great for talking to clanmates, but I need VOIP in ETQW to talk about whats actually happening in game.  It seems that under this setup, if Vent grabs the mic, ETQW cannot.  Any suggestions?

---

### Post by ushimitsudoki on 2008-10-02
ishkabob,

I can use both at the same time, so it should be possible. The only thing I can suggest is playing with the settings? Here are the ones I think are relevant and that I played with:

Wine: ALSA Driver and DirectSound Hardware Accelaration Emulation and Driver Emulation (the other settings caused flaky sounds).

Vent: Output using Direct Sound and the Default device, and the Input using Direct Sound and dsnoop:0.

ETQW: seta s_alsa_pcm "default"

I think it is MUCH easier if you leave Vent as NOT push-to-talk. That way, you can use a button in-game for VOIP, and everything goes on vent. You CAN use one of the scripts to have push-to-talk in ETQW, but it was a bit of a pain to get working consistently with USB devices and permissions and whatnot (although it was nice to be able to "key" which system I wanted). 

By the way, I've got this working now with no .asoundrc at all, just the Wine registry edits. I always start Vent first too - and on a separate X screen, but I don't think that matters.

---

### Post by ishkabob on 2008-10-03
Yep, I got mine working with no asoundrc also.  It turns out that most cards are already dmix'd and dsnoop'd out of the box with alsa.  I just stopped using my Creative SoundBlaster Live! and started using the nvidia onboard audio from my motherboard.  The drivers are much better for it and that pretty much fixed the problem, with the help of those wine tweaks.  Thanks again!

---

