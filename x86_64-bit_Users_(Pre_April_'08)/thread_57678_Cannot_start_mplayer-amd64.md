---
title: "Cannot start mplayer-amd64"
date: 2005-08-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by Steve1961 on 2005-08-17
I installed mplayer from synaptic but it won't start.  The cursor spins for a few seconds and then crashes.  I've edited the ~/.mplayer/config file as per instructions on the wiki:

######
## Audio drivers

## Ubuntu uses esd by default.
ao=esd

## These are only mentioned for the sake of completion.
#ao=oss
#ao=alsa
#ao=arts

######

I use esd at the moment as it works fine for xmms and I've had problems trying to install alsa so this makes sense.  I've also edited the /etc/mplayer/mplayer.conf file and inserted:

vo=xv,                  # To specify default video driver (see -vo help for
to replace 
vo=x11,                  # To specify default video driver (see -vo help for

When I try to start the payer with the sudo command I get the following output:

MPlayer 1.0pre6-3.3.5 (C) 2000-2004 MPlayer Team
CPU: Advanced Micro Devices  (Family: 8, Stepping: 10)
Detected cache-line size is 64 bytes
Cannot test OS support for SSE, disabling to be safe.


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
 up or down       seek backward/forward  1 minute
 pgup or pgdown   seek backward/forward 10 minutes
 < or >           step backward/forward in playlist
 p or SPACE       pause movie (press any key to continue)
 q or ESC         stop playing and quit program
 + or -           adjust audio delay by +/- 0.1 second
 o                cycle OSD mode:  none / seekbar / seekbar + timer
 * or /           increase or decrease PCM volume
 z or x           adjust subtitle delay by +/- 0.1 second
 r or t           adjust subtitle position up/down, also see -vf expand


Any ideas anyone?

---

### Post by newbie2 on 2005-08-17
[http://amd64.ubuntuguide.org/#mplayer](http://amd64.ubuntuguide.org/#mplayer)
[http://www.mplayerhq.hu/homepage/design7/dload.html](http://www.mplayerhq.hu/homepage/design7/dload.html)

---

### Post by DancingSun on 2005-08-17
[QUOTE=Steve1961]When I try to start the payer with the sudo command I get the following output:

...
Usage:   mplayer [options] [url|path/]filename
...
[/QUOTE]
You did not specify a file for mplayer to play...
Install gmplayer if you are expecting a GUI.

---

