---
title: "Can't get my sound working with wine"
date: 2008-07-15
forum: Wine
---

### Post by crazymanjared on 2008-07-15
So surprisingly, I installed ubuntu, wine, steam, cs 1.6, css, and mythos without ANY trouble at all. Now my only problem is gettin my sound to work, I have onboard sound, but i only use my headset, which is an edimensional 5+1 pro, and I have absolutely no idea how to get sound to work with anything through steam, it also won't work in firefox but it works with pidgin, rhytmbox, amarok etc.

---

### Post by terry f on 2008-07-15
If you go under under sound in the wine config menu try ALSA or OSS.

---

### Post by mriedel on 2008-07-15
First of all, follow these instructions: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

For sound in wine, try activating the ALSA driver in winecfg. If that doesn't work, choose OSS instead and run wine like this:

```
padsp wine Program.exe
```

Make sure you have the package pulseaudio-utils installed which provides pulseaudio's oss wrapper (padsp).

---

### Post by crazymanjared on 2008-07-15
> **mriedel said:**
> First of all, follow these instructions: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

For sound in wine, try activating the ALSA driver in winecfg. If that doesn't work, choose OSS instead and run wine like this:

```
padsp wine Program.exe
```

Make sure you have the package pulseaudio-utils installed which provides pulseaudio's oss wrapper (padsp).

I already ahd the pulseaudio-utils installed, and I followed all of the instructions posted in your link, I have tried the ALSA drivers and the OSS drivers, but with no luck. When i type padsp wine steam.exe it gives me this error: wine: could not load L"C:\\windows\\system32\\steam.exe": Module not found

---

### Post by crazymanjared on 2008-07-15
Now after i've done what it said to do in that guide i have no sound on anything, when i do a test in the audo setting it returns :audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

---

### Post by mriedel on 2008-07-16
Did you reboot after following the guide? Did you follow it to the letter? If both, you should probably post this in the howto thread.

---

### Post by Crowd Control on 2008-07-16
I'm not sure if this has been mentioned yet, but I just had the same message. It seems whatever gets booted up first gets the audio. If I start WINE, I can't play anything from the OS and vice versa. Haven't figured out a workaround though.

---

### Post by Fred_E _krugar on 2008-07-17
Your best option is to disable PulseAudio server (in processes) then restart any programs that use sound. I listen to Amarok and play CSS while talking on ventrilo and CSS voice at the same time.

---

### Post by lightstream on 2008-07-17
> **Fred_E _krugar said:**
> Your best option is to disable PulseAudio server (in processes) then restart any programs that use sound. I listen to Amarok and play CSS while talking on ventrilo and CSS voice at the same time.

If you do this, what do you have set in your System > Preferences > Sound window?

Steam and CSS run fine for me - but with pulseaudio now there's a lag in the audio of about half a second which is enough to pretty much spoil the playability. I get this lag in all games under wine.

---

### Post by Fred_E _krugar on 2008-07-18
> **lightstream said:**
> If you do this, what do you have set in your System > Preferences > Sound window?

Steam and CSS run fine for me - but with pulseaudio now there's a lag in the audio of about half a second which is enough to pretty much spoil the playability. I get this lag in all games under wine.


First off,I no longer use Ubuntu I use straight Debian. Also you might try Kubuntu which doesnt use pulseaudio at all.

To answer you question under sound make sure the ALSA is chosen,then you could shut down the pulseaudio sever,and restart all your sound applications. You will have to shut down pulseAdio server after every reboot.

---

### Post by lightstream on 2008-07-19
> **Fred_E _krugar said:**
> First off,I no longer use Ubuntu I use straight Debian. Also you might try Kubuntu which doesnt use pulseaudio at all.

To answer you question under sound make sure the ALSA is chosen,then you could shut down the pulseaudio sever,and restart all your sound applications. You will have to shut down pulseAdio server after every reboot.

Thanks for this. Steam has now stopped working entirely, so I can't test whether this works at the moment.

I am seriously thinking of switching distros, as since the upgrade to Hardy several things which worked fine under Gutsy no longer do so. (I suspect most if not all are related to sound - the Wine problems, other applications not being able to find and use sound, notably mupen64, flash video regularly crashing firefox).

I think I'll find out a bit more about Debian!

---

