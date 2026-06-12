---
title: "Can't play music when playing World of Warcraft"
date: 2008-06-16
forum: Wine
---

### Post by OMJD on 2008-06-16
Hi,

I have an annoying problem when running World of Warcraft via Wine on Ubuntu 8.04. The problem is that while the game is running, I am unable to play any music files, such as MP3's or even AVI's. As soon as I close World of Warcraft and try playing the music file again, it works fine. But it's annoying that I can't do both at the same time... Also, ingame sound works fine and I am able to watch Youtube videos at the same time, but playing other music files on the computer just won't work at all.

Any idea how to fix this problem? It's very annoying.

Thanks.

- Rich

---

### Post by cogadh on 2008-06-16
What are you using for a sound driver in Wine when you run WoW?

---

### Post by pedro_orange on 2008-06-16
Ok this might not be what you want to hear, but you can append the -nosound flag to the end of the launcher command (if you use the wine 'path/to/wow.exe' -opengl -nosound) 

This allows you to run RB etc.

I'm sure there must be a way to tell WINE to play nicely with PulseAudio, however I'm no expert in that field. Altho I would imagine you edit it from within winecfg

---

### Post by Fred_E _krugar on 2008-06-16
May be we need a Sticky.



Wine Doesn't Play Well With PulseAudio, Disable the PulseAudio server in processes Fist.

---

### Post by Cup of Squirrels on 2008-06-17
> **pedro_orange said:**
> Ok this might not be what you want to hear, but you can append the -nosound flag to the end of the launcher command (if you use the wine 'path/to/wow.exe' -opengl -nosound) 

This allows you to run RB etc.

I'm sure there must be a way to tell WINE to play nicely with PulseAudio, however I'm no expert in that field. Altho I would imagine you edit it from within winecfg

A cruder version of this is simply starting up your music player and getting it to play music first.

But of course, this means WoW (or any of your wine sessions) will not have sound.

---

### Post by bufsabre666 on 2008-06-17
system->preference->sound

music and movies set to autodetect 

that why which ever module wow is using wont be used and it will be kicked over to another ((you should have sound in wow and the audio app))

---

### Post by nonmi9 on 2008-06-17
Samething here. anyone have a workaround?

---

### Post by Fred_E _krugar on 2008-06-17
> **nonmi9 said:**
> Samething here. anyone have a workaround?

yes the work around is to turn PulseAdio server off.


Wine IS NOT COMPATIBLE WITH PULSEAUDIO...

---

### Post by nonmi9 on 2008-06-17
> **Fred_E _krugar said:**
> yes the work around is to turn PulseAdio server off.


Wine IS NOT COMPATIBLE WITH PULSEAUDIO...

And how might I do that?

---

### Post by Fred_E _krugar on 2008-06-18
On gnome I believe it is under System-Admin-system monitor.

once there just scroll down to PulseAudio and Kill the process then restart your games audio players and the such.


You have to do this every time you reboot.

---

### Post by bufsabre666 on 2008-06-18
it has nothing to do with pulse audio, wine cant use it and most applications cant either, the problem is wine defaults to alsa and only one app can use alsa at a time, so i alleviate to my post earlier->>>>


> 
system->preference->sound

music and movies set to autodetect

that why which ever module wow is using wont be used and it will be kicked over to another ((you should have sound in wow and the audio app))


i know for a fact this works, it works on the 3 linux comps in the house and the 2 i maintain at other places, and this way it stays you dont have to do it everytime

---

### Post by mitchej123 on 2008-06-18
Ok first of all, I'm at work right now and my linux box is at home, so I'll recall what I can from memory:

Here's a workaround until they update wine with pulse audio support.

Run 'winecfg' and change the sound server from alsa to oss.  Accept those changes. (IE: disable alsa, and enabled oss from winecfg)

Then modify your shortcut and add 'padsp' in front of wine.  (padsp starts the specified program and redirects its access to OSS compatible audio devices (/dev/dsp and auxiliary devices) to a PulseAudio sound server. )

I believe my shortcut looks something like - 
```
padsp wine ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/Wow.exe
```

If you don't have any luck with this let me know and I'll look at my shortcuts after I get home.

---

### Post by Fred_E _krugar on 2008-06-18
> **bufsabre666 said:**
> it has nothing to do with pulse audio, wine cant use it and most applications cant either, the problem is wine defaults to alsa and only one app can use alsa at a time, so i alleviate to my post earlier->>>>







Dude that is backwards alsa can use more than one sound source at a time it is OSS that can not.

---

### Post by nonmi9 on 2008-06-18
> **pedro_orange said:**
> Ok this might not be what you want to hear, but you can append the -nosound flag to the end of the launcher command (if you use the wine 'path/to/wow.exe' -opengl -nosound) 

This allows you to run RB etc.

I'm sure there must be a way to tell WINE to play nicely with PulseAudio, however I'm no expert in that field. Altho I would imagine you edit it from within winecfg

OK but now i get no sound in WOW, how do i get it back?

---

### Post by thisismalhotra on 2008-06-19
Okay do this first make sure your WoW in wine uses windows XP settings and not windows vista..

Then, go to audio tab in WINE Config and all different drivers one by one, don't activate two together and see which one work for you.

---

### Post by pedro_orange on 2008-06-19
> **nonmi9 said:**
> OK but now i get no sound in WOW, how do i get it back?

Lol. That was why I said I doubt this is what you want. The -nosound flag disables the sound! :)
From reading this thread, and having not tried this solution, I believe the earlier suggested solution sounds good.

```
winecfg
```

Then sound > OSS.

So alter your launcher to say something like:

```
padsp wine '~/usrname/.wine/drive_c/Program Files/World of Warcraft/WoW.exe' -opengl
```

Kudos to mitchej123 for the suggestion.

---

### Post by Go Team Venture! on 2008-11-27
Easy Solution.
I'm using Ubuntu 8.10. 
Change driver in WoW to ALSA.
Change system/preference/sound Movies to auto detect.
Rhythmbox Music player will default to OSS it seems.

I have WoW running with music at same time no problem.

Hope this helps some people.

Wow is running perfectly under Wine 1.1.9 and with all addons no crashes 
insanely fast framerates better than vista.

Ubuntu FTW.
Microsloth FTL...

---

### Post by Go Team Venture! on 2008-11-29
make sure to kill pulse audio process before you do the above.. otherwise alsa will sound like c r a p in wow

---

### Post by Wj@mesB on 2009-05-12
mitchej123,

Your suggestion is to point wow to use the pulse audio server? I will try that, my setup seems like a mess.

Ive just started running  8.04, with wine 1.1.21. I was having a lot of trouble getting sound from music players and wow at the same time. I did what it says here...

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

tried changing audio driver in wine to OSS and using AOSS to launch totem but still had trouble. I couldn't get it to work until i used Rhythmbox and killed the pulse audio process with system monitor. As soon as i killed the process i had sound in wow and Rhythmbox. Thank you to those that posted that information.

So now I have this in my launcher...

```

aoss wine "/home/james/.wine/drive_c/Program Files/World of Warcraft/Wow.exe"

```

...and i just start Rhythmbox normal. Doesn't seem to matter which one I start first.

I have... 

System > Preferences > Sound = auto detect, and Sound Capture = ALSA

I have... 

Winecfg > Audio = OSS

I can play wow and use ALSA in winecfg audio but the kill pulse audio trick doesn't work when I use that setup. So thats why i set winecfg audio to OSS and why im using AOSS, from what was in the help on unbuntu site.

Thanks, for any advice from anyone.

> **mitchej123 said:**
> Ok first of all, I'm at work right now and my linux box is at home, so I'll recall what I can from memory:

Here's a workaround until they update wine with pulse audio support.

Run 'winecfg' and change the sound server from alsa to oss.  Accept those changes. (IE: disable alsa, and enabled oss from winecfg)

Then modify your shortcut and add 'padsp' in front of wine.  (padsp starts the specified program and redirects its access to OSS compatible audio devices (/dev/dsp and auxiliary devices) to a PulseAudio sound server. )

I believe my shortcut looks something like - 
```
padsp wine ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/Wow.exe
```If you don't have any luck with this let me know and I'll look at my shortcuts after I get home.

---

### Post by ACLBandit on 2009-06-02
> **mitchej123 said:**
> 
I believe my shortcut looks something like - 
```
padsp wine ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/Wow.exe
```

Thank you so much! I've had a lot of troubles getting sound with my S/PDIF plug, and using PulseAudio -- this was a GREAT fix which allows my WoW and Rhythmbox to both have sound. Thanks so MUCH!

---

