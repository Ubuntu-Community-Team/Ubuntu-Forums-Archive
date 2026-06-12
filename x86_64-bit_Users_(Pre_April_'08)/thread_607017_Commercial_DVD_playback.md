---
title: "Commercial DVD playback"
date: 2007-11-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by BlackRoseBud on 2007-11-08
How do I enable commercial dvd playback in the 64-bit version of ubuntu gutsy gibbon 7.10?  I installed libdvdcss2 from the mediubuntu repo, but instead of giving me a message that totem can't read the source, the player just freezes.

---

### Post by bartt on 2007-11-08
sudo aptitude install vlc

use vlc it has all the codecs you should need.
HTH..

---

### Post by John.Michael.Kane on 2007-11-08
> **BlackRoseBud said:**
> How do I enable commercial dvd playback in the 64-bit version of ubuntu gutsy gibbon 7.10?  I installed libdvdcss2 from the mediubuntu repo, but instead of giving me a message that totem can't read the source, the player just freezes.

Have you tried the method outlined in this thread [http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607) it list what needs to be installed for dvd playback.

---

### Post by BlackRoseBud on 2007-11-08
> **SD-Plissken said:**
> Have you tried the method outlined in this thread [http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607) it list what needs to be installed for dvd playback.

I tried those steps, now none of my videos play.  Whatever player i try to use (totem/mplayer/movie player) just closes out immediately after opening a video file.  Can anyone help me?

---

### Post by John.Michael.Kane on 2007-11-08
Open mplayer, and right click on the app once it opens select preferences then select video then select xv also make sure to enable direct rendering as well which can be seen on the same box the opens.  close the app, and reopen it select the movie in question.

As for totem standard it can be flaky with what it plays. Regarding totem-xine as well as vlc, and mplayer they where all tested, and worked.

Also it would help if you told us what errors are output to the screen when trying to play the movies in question, If you want to find out what errors if there are any start the app you want to use from the terminal

---

### Post by Modred on 2007-11-08
I managed to get DVD's working with totem-gstreamer, but gstreamer doesn't support DVD menus, so it wasn't really so great.  So give totem-xine a try if you haven't already.

Well, while testing things to make sure what I said was accurate, I've discovered that several of my movies don't actually work.  *Ocean's Eleven* plays fine, but no dice with *School of Rock* or *Monty Python and the Holy Grail*.  So perhaps I haven't gotten it completely figured out.  *School of Rock* does what you described and simply crashes totem, while *Holy Grail* comes up with a message that an error ocurred and asks if I'm trying to play an encrypted movie without libdvdcss.

I'll see if I can figure it out.  Perhaps it's time to move on to mplayer or VLC.

EDIT: After a brief (and failed) stint with mplayer, I fidgeted with totem a bit more and now *School of Rock* is working.  After inserting the disc and the failed start, I opened a terminal and issued:

```

umount /media/cdrom0

```

You may need to change the number of the drive, depending on your computer's setup.

I then went into totem and chose "Play Disc CD-ROM/DVD-ROM Drive" (this may be different, based on your drives, just choose the option that isn't greyed out).  After that, totem mounted the movie and it worked.  Chances are this won't work for every movie, but it appears to work for at least some discs.

---

### Post by stmiller on 2007-11-08
Install libdvdcss to playback DVDs via Medibuntu:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Kilz on 2007-11-09
> **BlackRoseBud said:**
> I tried those steps, now none of my videos play.  Whatever player i try to use (totem/mplayer/movie player) just closes out immediately after opening a video file.  Can anyone help me?


If you are still having problems try this.
```
sudo apt-get install libdvdread3
sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by BlackRoseBud on 2007-11-09
> **SD-Plissken said:**
> Open mplayer, and right click on the app once it opens select preferences then select video then select xv also make sure to enable direct rendering as well which can be seen on the same box the opens.  close the app, and reopen it select the movie in question.

As for totem standard it can be flaky with what it plays. Regarding totem-xine as well as vlc, and mplayer they where all tested, and worked.

Also it would help if you told us what errors are output to the screen when trying to play the movies in question, If you want to find out what errors if there are any start the app you want to use from the terminal

[B] I tried what you said about xv and direct rendering, but there was no change.
This is the return when I try to run a .wmv file using mplayer:
[/B]
MPlayer 2:1.0~rc1-0ubuntu13 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T5250  @ 1.50GHz (Family: 6, Model: 15, Stepping: 13)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/jbailey/Desktop/02.wmv.
ASF file format detected.
VIDEO:  [WMV3]  640x480  24bpp  24.000 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 author: Gladirex
 copyright: Gladirex
 comments: Gladirex
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Requested video codec family [wmv9dmo] (vfm=dmo) not available.
Enable it at compilation.
Requested video codec family [wmvdmo] (vfm=dmo) not available.
Enable it at compilation.
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[wmv3 @ 0xe83d70]Extra data: 8 bits left, value: 0
Selected video codec: [ffwmv3] vfm: ffmpeg (FFmpeg M$ WMV3/WMV9)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 1 ch, s16le, 20.0 kbit/2.84% (ratio: 2501->88200)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
AO: [alsa] 48000Hz 1ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 640 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 640x480 => 640x480 Planar YV12 
X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0 


MPlayer interrupted by signal 6 in module: vo_check_events
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
GNOME screensaver enabled

[B]I was able to play .wmv files just fine before I tried making commercial dvds work. 
Here's the return when I try to run it in totem:[/B]

/usr/share/themes/Chlorophyll/gtk-2.0/gtkrc:47: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/usr/share/themes/Chlorophyll/gtk-2.0/gtkrc:48: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/usr/share/themes/Chlorophyll/gtk-2.0/gtkrc:49: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
sh: jackd: not found
sh: jackd: not found
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 50 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

**I appreciate your help!**

---

### Post by BlackRoseBud on 2007-11-09
> **Kilz said:**
> If you are still having problems try this.
```
sudo apt-get install libdvdread3
sudo /usr/share/doc/libdvdread3/install-css.sh
```

It made me install debhelper and fakeroot before I could do the second command.  But dvds still don't play.  Totem opens and freezes when I insert a dvd and it says "**Totem cannot play this type of media (DVD) because it does not have the appropriate plugins to be able to read from the disc**" when I try to manually play the dvd after opening totem.  Mplayer just closes out right away.  I don't know how to play dvds from a terminal.

---

### Post by fraterm on 2007-12-06
I'm in the same boat as the thread opener, nothing really seems to work.  The show has stopped :)

---

