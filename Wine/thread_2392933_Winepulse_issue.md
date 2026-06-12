---
title: "Winepulse issue"
date: 2018-05-27
forum: Wine
---

### Post by zuto2 on 2018-05-27
I use an application called CGMusic and the sound worked when I first installed Ubuntu 16.04 Xenial. During an Ubuntu update a few months ago is stopped working, but all my other applications are functioning fine with sound. I tried to reinstall it in case something was corrupted, but that was not the issue. I tried different versions of WINE, but still no sound. Also, I used wine 1.4 on my old computer using Ubuntu 12.04 Precise and CGMusic worked fine.

I do have an error message if it will help. I am currently using wine-1.6.2

```
/cgMusic/cgm_app.exe' 
fixme:winediag:AUDDRV_GetAudioEndpoint Winepulse is not officially supported by the wine project
fixme:winediag:AUDDRV_GetAudioEndpoint For sound related feedback and support, please visit http://ubuntuforums.org/showthread.php?t=1960599



```

[SIZE=5]Solution:[/SIZE]

I made a quick hack solution through trial and error.

Run fluidsynth through pulseaudio:
```
fluidsynth -a pulseaudio -l --server -i /usr/share/sounds/sf2/FluidR3_GM.sf2
```

That will make CGmusic work. I simply made that command a shortcut with alacarte. I run the fluidsynth shortcut and then open CGmusic.

Maybe wine or pulseaudio is not detecting soundfont or midi stuff.

---

### Post by mörgæs on 2018-05-28
Asking in the thread to which you linked is probably better than asking in General Help.

---

### Post by oldos2er on 2018-05-28
Moved to WINE.

---

### Post by Yellow Pasque on 2018-05-28
> I do have an error message if it will help
Probably not. It's a generic warning that gets printed whenever you use wine's pulse plugin.

Have you tried running winecfg and selecting ALSA as the sound driver? Note that it will still ultimately be routed through pulseaudio, but it will help rule out if the program you are using has an issue with wine's pulse plugin.

---

### Post by zuto2 on 2018-05-28
> **mörgæs said:**
> Asking in the thread to which you linked is probably better than asking in General Help.

I was thinking the same thing, but that thread does not look like it has been updated in years unless they are just not updating the main post. [COLOR=#000000]*Last edited by vladdy; May 22nd, 2013 at *[/COLOR][COLOR=#3E3E3E]*07:21 AM*[/COLOR]

> **Temüjin said:**
> Probably not. It's a generic warning that gets printed whenever you use wine's pulse plugin.

Have you tried running winecfg and selecting ALSA as the sound driver? Note that it will still ultimately be routed through pulseaudio, but it will help rule out if the program you are using has an issue with wine's pulse plugin.

I did indeed try that. Maybe it would only work with older versions of pulseaudio. To put it simply the sound got worse on the CGMusic application every time a new update occurred. Worked perfectly at first, then the sound was a little garbled, and now it does not work at all. I am guessing it just has to do with the new version of pulseaudio. I am currently using pulseaudio 8.0, but no idea of which version I was using before.

---

### Post by Yellow Pasque on 2018-05-28
It looks like at least one other person may have the same issue: [https://appdb.winehq.org/objectManager.php?sClass=version&iId=32797](https://appdb.winehq.org/objectManager.php?sClass=version&iId=32797)

---

### Post by mörgæs on 2018-05-28
> **zuto2 said:**
> I was thinking the same thing, but that thread does not look like it has been updated in years.

It does not matter. If you post there you are likely to get the attention of everyone who has posted in the thread.

Anyway, you are in good hands at Temüjin.

---

### Post by Yellow Pasque on 2018-05-28
> **mörgæs said:**
> Anyway, you are in good hands at Temüjin.

Thanks for the vote of confidence, but I don't have any other solutions at the moment. I can try and run it on my laptop when I have a chance if it's free/shareware

---

### Post by zuto2 on 2018-05-28
> **Temüjin said:**
> Thanks for the vote of confidence, but I don't have any other solutions at the moment. I can try and run it on my laptop when I have a chance if it's free/shareware

Yes it is free, sadly it seems there is some issue with the blog, but thanks to wayback machine you can still get it.
[https://web.archive.org/web/20170703071153/http://codeminion.com/blogs/maciek/2008/05/cgmusic-computers-create-music/](https://web.archive.org/web/20170703071153/http://codeminion.com/blogs/maciek/2008/05/cgmusic-computers-create-music/)


Link:
[https://web.archive.org/web/20170703071153/http://www.codeminion.com/blogs/maciek/files/cgMusic_Setup.exe](https://web.archive.org/web/20170703071153/http://www.codeminion.com/blogs/maciek/files/cgMusic_Setup.exe)

---

### Post by zuto2 on 2018-06-16
[COLOR=#DD4814][COLOR=#000000]@[/COLOR][/COLOR][Temüjin]("https://ubuntuforums.org/member.php?u=327594&")

I was wondering...did you find the cause of the no sound issue?

---

### Post by zuto2 on 2018-06-16
Sorry for triple posting, but I found a weird fix. 

I installed pavucontrol and without doing anything at all with the software.....the sound in cgmusic started working. Yeah, no idea what happened while installing pavucontrol, but it fixed the issue and the sound is beautiful.

```
sudo apt-get install pavucontrol
```

---

### Post by mörgæs on 2018-06-17
Good. please mark the thread solved.

---

### Post by zuto2 on 2018-06-17
Ah, another issue. Okay, I thought something with pavucontrol installation fixed the issue, but sound stops working on restart.

I activated Aria Maestosa. This is a midi composition and tool. CGmusic still did not work, but when I exited Aria.....CGmusic started working again.
[http://ariamaestosa.sourceforge.net/](http://ariamaestosa.sourceforge.net/) 

I checked pavucontrol and there was fluidSynth output. Not sure if that has anything to do with it, but CGmusic is .midi based.

---

### Post by zuto2 on 2018-06-17
I made a quick hack solution through trial and error.

Run fluidsynth through pulseaudio:
```
fluidsynth -a pulseaudio -l --server -i /usr/share/sounds/sf2/FluidR3_GM.sf2
```

That will make CGmusic work. I simply made that command a shortcut with alacarte. I run the fluidsynth shortcut and then open CGmusic.

Maybe wine or pulseaudio is not detecting soundfont or midi stuff.

---

