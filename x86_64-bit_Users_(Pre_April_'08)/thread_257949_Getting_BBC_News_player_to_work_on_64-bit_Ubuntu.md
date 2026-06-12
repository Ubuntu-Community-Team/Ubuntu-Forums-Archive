---
title: "Getting BBC News player to work on 64-bit Ubuntu"
date: 2006-09-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by patslap on 2006-09-15
Hi 

I have followed the how-to to install mplayer into 32 bit Firefox running on 64-bit Ubuntu. Everything I've tried plays great - movie trailers, youtube etc. except BBC News player. The news player wants you to have eiter realplayer or Windows Media Player to view video. Mplayer does not display properly.

Anyone else have this problem and know how to resolve it?

Thanks

patslap

---

### Post by Kilz on 2006-09-15
How long ago did you install it. Did you follow the manual howto, or install the complete script? Take a look below and tell me if this is what you see when looking at ths site.

---

### Post by patslap on 2006-09-15
Howdy

It was acutally your very own howto at [http://www.ubuntuforums.org/attachment.php?attachmentid=15748&stc=1&d=1158275667]("http://www.ubuntuforums.org/attachment.php?attachmentid=15748&stc=1&d=1158275667")
which I installed yesterday evening.

The bbc newsplayer window looks like the left-hand picture you attached.

Here is a screenshot:

---

### Post by Fedz on 2006-09-15
Are you using the Applications > Internet > Firefox32 Web Browser as the image above looks like your using the normal installed Firefox browser.

I also found **[This thread (by Kilz)](http://www.ubuntuforums.org/showthread.php?t=202537)** very easy - one click and it installs it all (browser, java, player, codecs, flash ...etc).

Kind regards

---

### Post by patslap on 2006-09-15
Hi Fedz

Yep - I'm using Firefox32 (I've changed the panel launcher to 'firefox32 %u'; and also in preferred applications).

As per my above post I followed Kilz howto to install java, flash and mplayer.

---

### Post by Kilz on 2006-09-15
> **patslap said:**
> Hi Fedz

Yep - I'm using Firefox32 (I've changed the panel launcher to 'firefox32 %u'; and also in preferred applications).

As per my above post I followed Kilz howto to install java, flash and mplayer.
It looks like you installed the manual howto, download the install [everything script here ]("http://home.comcast.net/~deletebox/Firefox32-flash-java-mplayer-9.tar.gz") and run it. This will make sure everything is installed.

---

### Post by Kilz on 2006-09-15
If this doesnt fix it, open a terminal, type in mplayer and see if you get any errors.

---

### Post by patslap on 2006-09-15
OK, I downlaoded the install everything script and ran it. I tried bbc newsplayer and am experiencing the same problem. The first screenshot is of the firefox-embedded mplayer loading the video feed, and the second is how it appears once the feed has loaded (see attachements at bottom of post).

As you can see I still can't get it to work.#-o 

I then opened a terminal and typed 'mplayer' and this is the output:
```
pat@pat-desktop:~$ mplayer
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices Athlon 64 Newcastle,Winchester,San Diego,Venice; Sempron Palermo (Family: 15, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


91 audio & 204 video codecs
Usage:   mplayer [options] [url|path/]filename

Basic options: (complete list in the man page)
 -vo <drv[:dev]>  select video output driver & device ('-vo help' for a list)
 -ao <drv[:dev]>  select audio output driver & device ('-ao help' for a list)
 vcd://<trackno>   play (S)VCD (Super Video CD) track (raw device, no mount)
 dvd://<titleno>   play DVD title from device instead of plain file
 -alang/-slang    select DVD audio/subtitle language (by 2-char country code)
 -ss <timepos>    seek to given (seconds or hh:mm:ss) position
 -nosound         do not play sound
 -fs              fullscreen playback (or -vm, -zoom, details in the man page)
 -x <x> -y <y>    set display resolution (for use with -vm or -zoom)
 -sub <file>      specify subtitle file to use (also see -subfps, -subdelay)
 -playlist <file> specify playlist file
 -vid x -aid y    select video (x) and audio (y) stream to play
 -fps x -srate y  change video (x fps) and audio (y Hz) rate
 -pp <quality>    enable postprocessing filter (details in the man page)
 -framedrop       enable frame dropping (for slow machines)

Basic keys: (complete list in the man page, also check input.conf)
 <-  or  ->       seek backward/forward 10 seconds
 down or up       seek backward/forward  1 minute
 pgdown or pgup   seek backward/forward 10 minutes
 < or >           step backward/forward in playlist
 p or SPACE       pause movie (press any key to continue)
 q or ESC         stop playing and quit program
 + or -           adjust audio delay by +/- 0.1 second
 o                cycle OSD mode:  none / seekbar / seekbar + timer
 * or /           increase or decrease PCM volume
 x or z           adjust subtitle delay by +/- 0.1 second
 r or t           adjust subtitle position up/down, also see -vf expand

 * * * SEE THE MAN PAGE FOR DETAILS, FURTHER (ADVANCED) OPTIONS AND KEYS * * *
```

Thanks for the help so far.

---

### Post by patslap on 2006-09-15
Ok - Just realised - I've selected 'changed how I view or hear this' in the newsplayer window to Windows Media Player, not Realplayer, and it now works fine.

You help is appreciated.

Many thanks

patslap :-)

---

### Post by kleeman on 2006-09-15
I got this to work by using the realplayer plugin instead of mplayer32 (which never worked properly for me). realplayer works fine in 64bit on my machine as long as alsa oss emulation works for sound. To get the plugins, download the binary (10.0.EIGHT) from Real. Look in the install directory and there should bea mozilla subdirectory with two files. You need them in the firefox plugin directory (.mozilla/plugins)

---

