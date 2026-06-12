---
title: "Help with enabling sound"
date: 2008-03-03
forum: Wine
---

### Post by aoberoi on 2008-03-03
im running into problems getting sound to work in wine. the only application i have installed is firefox. i then installed the flash plugin for firefox. i wanted to watch tv shows on abc.com so i installed the plugin that they require as well. the video plays fine and everything works great except for the audio. so i ran winecfg. this is the output i got:

```
$ winecfg
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 1
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:1
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 2
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:2
fixme:mixer:ALSA_MixerInit No master control found on USB Device 0x46d:0x8b0, disabling mixer
ankur@ankurlinux:~$ winecfg
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 1
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:1
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 2
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:2
fixme:mixer:ALSA_MixerInit No master control found on USB Device 0x46d:0x8b0, disabling mixer

```

in the rest of ubuntu i use the alsa mixer, but i had to manually set it to use me Sound Blaster Audigy card instead of the onboard sound. there is also a usb webcam with a mic that might be the detected as the USB device. what can i do to get sound working?

---

### Post by nosto on 2008-03-05
Ok could you ellaborate a little more please?  Are you running the ABC website while in a wine desktop?  Or are you having issues with linux native apps when you have wine open?

I'm relatively new and I'm just going to try and give you options.  There is an application or whatever you want to call it called AOSS that I use with wow and ventrilo via wine.  It helped alleviate a ton of my issues.  I believe you can apt-get aoss and then when you run a command you just put aoss in front of the item you wish to run in wine. ie. aoss wine program.exe

It might help just a suggestion it allowed oss multistreaming and thus alleviated all my issues.

This could be completely unhelpful and I'm sorry if that is the case.

Cheers,
James

---

### Post by crazyfuturamanoob on 2008-11-24
I got exactly the same problem. Help!

---

