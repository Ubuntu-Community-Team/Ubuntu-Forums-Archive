---
title: "Amarok and Kaffeine/MPlayer Problems"
date: 2007-10-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by Brando569 on 2007-10-24
the problem with amarok isnt really a problem, its more like an annoyance. the thing is that it displays two of every song in my library when there is only one file. updating the library doesnt do anything to fix this. i dont really know if this matters but the music files are on an ntfs volume instead of a linux based file system.

the other problems are really problems, i have the codecs and everything installed but when i try to play something in kaffeine it doesnt do anything at all (doesnt even open the program) while mplayer gives me some errors such as these: error opening/initializing the selected video out device

```
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ (Family: 15, Model: 43, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
xscreensaver_disable: Could not find XScreenSaver window.
gnome_screensaver_control()Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /media/stuff/movies/¤TV Shows¤/Scrubs/Season 1/Scrubs - 101 - My first day.avi.
AVI file format detected.
VIDEO:  [DIV3]  352x240  24bpp  29.970 fps  629.5 kbps (76.8 kbyte/s)
Clip info:
 Software: Nandub v0.26
 Name: Scrubs - S1E01 - The Pilot
 Subject: Scrubs - S1E01 - The Pilot
 Artist: Kraicat
 Copyright: #FuturamaEpisodes
 Comments:
xscreensaver_disable: Could not find XScreenSaver window.
gnome_screensaver_control()It seems there is no Xvideo support for your video card available.
Run 'xvinfo' to verify its Xv support and read DOCS/HTML/en/video.html#xv!
See 'mplayer -vo help' for other (non-xv) video out drivers. Try -vo x11
Error opening/initializing the selected video_out (-vo) device.


Exiting... (Quit)

```

how can i fix this?

---

### Post by Brando569 on 2007-10-28
can anyone help me with this at all?

---

### Post by drejom on 2007-10-30
same prob here on my amd64 fresh install!

---

### Post by Brando569 on 2007-11-06
i guess its a problem with the 64 bit and no one seems to want to help :(

---

### Post by cjazz on 2007-11-07
> **Brando569 said:**
> i guess its a problem with the 64 bit and no one seems to want to help :(

Excuse me, but why would you assume that? Have you considered that among the people who have viewed this thread, no one has the answer to your problem?

Not to nag, but I see people come on these forums and generously contribute their time and knowledge to help others. I'm a little confused by the number of people who seem to think that there are people who have the answer but for some reason simply don't want to help.

---

### Post by InsideBevel on 2007-11-07
Have you installed the 64bit codecs?

---

### Post by Brando569 on 2007-11-07
i assumed that since someone else had the exact same problem as i did and this has been up for a week. i posted this on the amarok forum lastnight and got an answer within 2 hours. i was told to rescan my library (which i was sure i did numerous times) and i tried it again and it worked, which was odd. as for the constant scanning, i just clicked the red x while it was scanning and that seemed to stop it. im in windows now so im not sure if it was completely resolved.

---

### Post by IppatsuMan on 2007-11-14
Try putting

```
vo=gl2
```

in your /etc/mplayer/mplayer.conf file.

---

### Post by crazymajax on 2008-02-20
Had the same issue.
I have an intel core 2 duo 64bit.
Fresh install of Gutsy and after a few reboot mplayer wouldn't let me play anything anymore

Little workaround:
If I run mplayer as root and specifying x11 as my video output "-vo x11" it works

The apparent reason:
Mplayer tries to prevent XScreenSaver to put the pc in screen saver mode and somehow fails to do so resulting in a crash of the the video output in the module: preinit_libvo

The solution I resided to use:
Change the config of mplayer for it not to try to disable XScreenSaver:
- I ran gmplayer as root
- right click on the window
- Preferences
- under the Misc tab uncheck the "Stop XScreenSaver" option
- click OK
- close gmplayer

Et Voila !
Enjoy...

Example of the error I was getting:
```

$> mplayer -zoom -vo x11 Desktop/Yves_Larock_-_Rise_up\[MINS00000860\].mkv MPlayer 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Desktop/Yves_Larock_-_Rise_up[MINS00000860].mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_VORBIS), -aid 0, -alang und
[mkv] Will play video track 1
Matroska file format detected.
VIDEO:  [avc1]  624x368  24bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.


MPlayer interrupted by signal 11 in module: preinit_libvo
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.

```

---

### Post by crazymajax on 2008-02-20
Ok, Sorry guys I spoke a little too fast...

that only fixed gmplayer.

To do the same on mplayer you need to edit ~/.mplayer/config
Here is what you need to add:
```

stop-xscreensaver="no"

```

For my particular case I actually have another issue:
```

It seems there is no Xvideo support for your video card available.
Run 'xvinfo' to verify its Xv support and read DOCS/HTML/en/video.html#xv!
See 'mplayer -vo help' for other (non-xv) video out drivers. Try -vo x11
Error opening/initializing the selected video_out (-vo) device.

```

indeed if I run xvinfo I get the following error:
```

$> xvinfo
X-Video Extension version 2.2
screen #0
 no adaptors present

```

I'm invastigating on it.
if anybody has an idea don't hesitate to reply ;)
--
Majax

---

