---
title: "WINE and DOSBox problems"
date: 2011-08-10
forum: Wine
---

### Post by Methus on 2011-08-10
Hey guys, I'm having some difficulties getting a program to run under a remote, headless Ubuntu 10.04 server.

I have a particular EXE file that I need to run (in short it provides a Master Server service to other servers for a game). I've installed WINE, and when I try to run it, it says to use DOSBox due to the memory usage.

Ok, so I try to open it with DOSBox, but then I get these errors:
```

err:int:DOSVM_QueueEvent IRQ without DOS task: should not happen
DOSBox version 0.73
Copyright 2002-2009 DOSBox Team, published under GNU GPL.
---
init kbd.
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:4154:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4633:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
CONFIG:Loading primary settings from config file /root/.wine/dosdevices/c:/users/root/Temp/cfg9782.tmp
MIXER:Can't open audio: No available audio device , running in nosound mode.
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
ALSA:Can't open sequencer
MIDI:Opened device:none

```Anyone have some suggestions? :confused:

and here's another error I get when wine tried to use DOSBox for me:
```

user@server:~$ wine /opt/masterServer/mstrsvr.exe
DOSBox version 0.73
Copyright 2002-2009 DOSBox Team, published under GNU GPL.
---
commandline read: dosbox
commandline read: -conf
commandline read: /home/user/.wine/dosdevices/c:/users/user/Temp/cfgb964.tmp

   ~~~~~~~~~~~~~~~~~~~~~~~~~~| DirectFB 1.2.8 |~~~~~~~~~~~~~~~~~~~~~~~~~~
        (c) 2001-2008  The world wide DirectFB Open Source Community
        (c) 2000-2004  Convergence (integrated media) GmbH
      ----------------------------------------------------------------

(*) DirectFB/Core: Single Application Core. (2010-04-09 11:08)
(!) Direct/Util: opening '/dev/fb0' failed
    --> Permission denied
(!) DirectFB/FBDev: Error opening framebuffer device!
(!) DirectFB/FBDev: Use 'fbdev' option or set FRAMEBUFFER environment variable.
(!) DirectFB/Core: Could not initialize 'system_core' core!
    --> Initialization error!
Exit to error: Can't init SDL DirectFBCreate: Initialization error!

```

---

### Post by Methus on 2011-08-16
Anyone? Anything?

---

### Post by Perfect Storm on 2011-08-16
Tried this? [http://ubuntuforums.org/showthread.php?t=39658](http://ubuntuforums.org/showthread.php?t=39658)

---

### Post by Methus on 2011-08-24
Yes, I've tried the methods described in the thread you have posted (albeit *after* you had posted it, thx btw), and to no avail.

It took this long because I've been fighting with my PC to get the darn thing running. And then there was a problem with connecting to the server, so I had to have them reboot on-site (and no, I tried after the reboot and still no luck).

---

### Post by tracy6413 on 2011-08-24
wow,it is so complcated and i am just a newbie.what a shame!

---

### Post by Methus on 2011-08-24
That's pretty much how I feel at this point.

---

### Post by thatguruguy on 2011-08-24
Do you have a soundcard installed in your headless server?  If not, that's what's causing the ALSA errors.

---

### Post by Methus on 2011-08-25
No soundcard, no. No need for one.

My main problem is that the program won't run. And if by some miracle I do get it to run, it's only for 6 minutes, then it crashes. (and I do mean only 6 minutes; it's very consistent in that manner)

---

