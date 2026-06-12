---
title: "Sound in WINE and other applications."
date: 2008-07-09
forum: x86 64-bit Users
---

### Post by heinzbitte on 2008-07-09
I've read that wine can only use sound if no other application is.  But I seem to remember that before I upgraded to 8.04 I got it to do that before.

I've tested watching a video on youtube and playing rythmbox and they can both use sound at the same time.

But WINE can only use sound when nothing else is.

I'm not really sure what my soundcard is, it is built in on the mobo.

Sorry I'm kinda dumb.  I can rewrite this to make more sense and give more info if you want.

---

### Post by TimothyLuke on 2008-07-09
I also have this issue.  I have tried wrapping the wine command with 'padsp' (sp?) to get it to run through pulse with no success so far.  

WINE is configured currently to use ALSA, however if any other application is running that uses sound (or even Flash 9 open on a web page) WINECFG is unable to obtain the sound device.  Does anyone know if this is more of a WINE issue than a Ubuntu one?

---

### Post by heinzbitte on 2008-07-09
> **TimothyLuke said:**
> I also have this issue.  I have tried wrapping the wine command with 'padsp' (sp?) to get it to run through pulse with no success so far.  

WINE is configured currently to use ALSA, however if any other application is running that uses sound (or even Flash 9 open on a web page) WINECFG is unable to obtain the sound device.  Does anyone know if this is more of a WINE issue than a Ubuntu one?
On the WINE Faq is says something about this, but makes it seem like its a general issue, but minus WINE I can use more than one sound playing application at a time.

---

### Post by Yellow Pasque on 2008-07-09
You could use OSS4, which has a good virtual mixer (vmix). I've gotten sound from YouTube while listening to music with foobar2000/WINE with vmix before.

I'd suggest building OSS4 from source instead of going the .deb route

---

### Post by heinzbitte on 2008-07-10
> **Temüjin said:**
> You could use OSS4, which has a good virtual mixer (vmix). I've gotten sound from YouTube while listening to music with foobar2000/WINE with vmix before.

I'd suggest building OSS4 from source instead of going the .deb route

Do I do what it says in the link in your sig?  Right now I can get all applications I have tried to run sound with eachother unless wine is involved will this still help?

---

### Post by Artemis3 on 2008-07-12
Alsa can play sounds from various apps at the same time with many soundcards (some can't). I can have audacious playing music, while playing games in wine, including teamspeak 2 in wine, and i usually leave firefox open even in youtube, or alt tab to it to play a video then go back to the game.

My ~/.asoundconf looks like this:

```

pcm.snd_card {
        type hw
        card 0
}

pcm.dmixer {
        type dmix
        ipc_key 1024
        slave.pcm "snd_card"
        slave {
                period_size 256
                buffer_size 2048
                rate 44100
        }
}

pcm.dsnooper {
        type dsnoop
        ipc_key 2048
        slave.pcm "snd_card"

        slave {
                period_size 256
                buffer_size 2048
                rate 44100
        }
}

pcm.duplex {
        type asym
        playback.pcm "dmixer"
        capture.pcm "dsnooper"
}

pcm.!default {
        type plug
        slave.pcm "duplex"
}

```

Try killing pulseaudio (killall pulseaudio) and make sure all your apps are configured to use alsa, not pulseaudio.

In theory you can have [pulseaudio behave](http://www.pulseaudio.org/wiki/PerfectSetup), but i didn't bother, alsa mixes my sounds just fine.

---

### Post by heinzbitte on 2008-07-13
> **Artemis3 said:**
> Alsa can play sounds from various apps at the same time with many soundcards (some can't). I can have audacious playing music, while playing games in wine, including teamspeak 2 in wine, and i usually leave firefox open even in youtube, or alt tab to it to play a video then go back to the game.

My ~/.asoundconf looks like this:

```

pcm.snd_card {
        type hw
        card 0
}

pcm.dmixer {
        type dmix
        ipc_key 1024
        slave.pcm "snd_card"
        slave {
                period_size 256
                buffer_size 2048
                rate 44100
        }
}

pcm.dsnooper {
        type dsnoop
        ipc_key 2048
        slave.pcm "snd_card"

        slave {
                period_size 256
                buffer_size 2048
                rate 44100
        }
}

pcm.duplex {
        type asym
        playback.pcm "dmixer"
        capture.pcm "dsnooper"
}

pcm.!default {
        type plug
        slave.pcm "duplex"
}

```

Try killing pulseaudio (killall pulseaudio) and make sure all your apps are configured to use alsa, not pulseaudio.

In theory you can have [pulseaudio behave](http://www.pulseaudio.org/wiki/PerfectSetup), but i didn't bother, alsa mixes my sounds just fine.
Did you have to do anything other than have everything set to use alsa?

---

### Post by darkaudit on 2008-07-13
It also depends on what desktop you're using. If I'm using GNOME or XFCE when playing WoW, I lose sound in the game if I have to tab out. Only way to get it back is to restart the game.

I was using Fluxbox during Thursday night's raiding this past week. I had to dajust the volume to my headset for Ventrilo, and tabbed out to run gnome-volume-control. Sound in-game was just fine when I came back. Didn't have to restart at all.

---

### Post by heinzbitte on 2008-07-13
In system sound preferences I changed everything from auto to also.

Now wine and ryhtmbox work but I can't get firefox's sound workign.

---

### Post by markbuntu on 2008-07-14
There is a problem with pulseaudio and wine. wine requires alsa so when you change your defaults to alsa, flash, which needs pulseaudio will not work. The trick is to get alsa apps to use pulse while pulse is using alsa.

Try this:

check in etc/libao.conf

default_driver=alsa

If it says pulseaudio change it to alsa. In System/Administration/Services make sure that the alsa-utils are checked.

Get asoundconf-gtk from the repos. It will be installed in System/Preferences as Default Sound Card. Open it and select pulseaudio as the default sound card. Set all your preferences in Sound to ALSA. In Sound/Sounds be sure to have Enable Software sound mixing checked.

Now, all your sound will go through pulse and the apps will think they are using alsa. Make sure you have all the plugins for alsa:

alsa-oss  (alsa wrapper for OSS apps)
alsaplayer-alsa  (PCM player for alsa)
alsa-utils  (command line utilities)
gnome-alsamixer (GUI alsa mixer for Gnome)
gstreamer0.10-alsa (gstreamer plugin)
xmms2-plugin-alsa (xmms2 plugin)
libasound2-plugins (jack, OSS, pulseaudio)
libesd-alsa0 Enlightened Sound Demon (allows  multiple audio streams on one device)


Also get 

paman

 it is the Pulse Audio Manager and will tell you what is going on with pulseaudio, which plugins which apps are using etc. It also allows you to set the volume individually for any stream. 

Open Pulse Audio Manager (It is in Applications/Sound & Video) and see if it is using alsa as the defaul source and sink. If you run any app that uses sound it will be listed in devices as 

#number

You can highlight it and click on properties and it will give you all sorts of info and a volume control for that stream.

I can play any sound from any app or all of themm simultaneously on my system with this setup. flash10, totem, vlc, rythmbox, xmms, etc.

---

### Post by hangar_18 on 2008-07-31
> **darkaudit said:**
> It also depends on what desktop you're using. If I'm using GNOME or XFCE when playing WoW, I lose sound in the game if I have to tab out. Only way to get it back is to restart the game.

I was using Fluxbox during Thursday night's raiding this past week. I had to dajust the volume to my headset for Ventrilo, and tabbed out to run gnome-volume-control. Sound in-game was just fine when I came back. Didn't have to restart at all.

you must set driver emulation option in winecfg, then it wont mute after alt+tab :)

---

