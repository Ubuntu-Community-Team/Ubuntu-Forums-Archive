---
title: "xmms and gnome freeze"
date: 2005-05-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by futte on 2005-05-20
when i use xmms to read my mp3 files it freeze but i can't work on bot not shutdown the computer only by reset buttum :???: 
But if i boot in KDE it's runs normal  O:) 
it's the 64bit version and by UK i very pure  ](*,)

---

### Post by FreeEagle on 2005-05-21
just try to change the sound driver from OSS to ALSA and it will work.

Right Click on the XMMS and then go to Settings ( Prefrences ) and then chanage the sound Driver and it will work..


Best Regards,
 FreeEagle

---

### Post by futte on 2005-05-25
i can not use alsa driver

---

### Post by FreeEagle on 2005-05-25
why? where is your Problem with ALSA driver?

Can you tell me please in details why you can not choose it?


FreeEagle

---

### Post by ChandOne on 2005-05-25
I am having a very similar problem, where xmms becomes completly unresponsive when attempting to load a stream from shoutcast.  I can kill the process from a terminal, but cannot otherwise do so.  I attempted to switch from OSS to ALSA as suggested, and met with failure when xmms attempts to open an  stream and comes back with:

"Couldn't Open Audio
Please Check that:
Your soundcard is configured properly, you have the correct output plugin selected,  No other program is blocking the soundcard"

I am running the most recent release of Ubuntu as of 5/18/05, with the 2.6.10.5 kernel, on a Thinkpad T41p.  

Any help is appreciated!

-Brad


[QUOTE=FreeEagle]why? where is your Problem with ALSA driver?

Can you tell me please in details why you can not choose it?


FreeEagle[/QUOTE]

---

### Post by ChandOne on 2005-05-25
Here is a bit more detail on my last post:

Command line launch:

$ /usr/bin/xmms
libmikmod.so.2: cannot open shared object file: No such file or directory

>> Here I switched to ALSA, then opened a shoutcast stream through firefox and got:

** WARNING **: alsa_setup(): Failed to open pcm device (default): Device or resource busy

---

### Post by futte on 2005-05-26
it works now i whit other output lib in xmms  :razz:

---

### Post by bostonnewbie on 2005-06-08
[QUOTE=futte]it works now i whit other output lib in xmms  :razz:[/QUOTE]

Not to be a stupid newbie, but could you spell out what steps you took to resolve this issue?

I'm having an identical problem.  xmms works fine on alsa, but read that you need to choose output esound for shoutcast playlists.  When I choose esound xmms hangs.  WHen I launched it from terminal got the libmikmod.so.2 error.

Thanks in advance.
BostonNewbie

---

