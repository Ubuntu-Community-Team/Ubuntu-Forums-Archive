---
title: "Issues with sound, kiba-dock, and video players"
date: 2007-06-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by gargar934 on 2007-06-21
Hi All!

I'm a recent windows refugee, and even with my problems, I am happy to say that I will never go back. But flattery aside, here is my situation (broken down by problem...and listed in order of importance)

Sound:
I seem to be having the cliched problem of my sound refusing to work, most of the time. I have installed so many video and audio codecs that I am not really concerned that any are missing but that maybe there exists a conflict or one that shouldn't be there in the first place(excuse me if that is a n00b thought). I followed procedures to get 32 bit firefox and flash ect, and the video now works fine at youtube, minus the sound. The strange part is that my system plays sounds at login, but youtube and mplayer and vlc all fail to produce sound. Actually this leads me to my second problem:

VLC and mplayer Crash when I load anything (audio, video, ect.):
I can open the players just fine, and interact normally, but as soon as I try to open a video (eg from the 'examples' folder), the player disappears from the screen and nothing else happens. When I double click on the 'examples' files and the default player opens, I do get video going, but no sound.

Kiba-dock:
Ok so its just dumb eyecandy, but come on, who doesn't want a little spice on their system? I tried the svn install with compiling it myself, and I get errors. I tried a .deb file for 64 bit that someone posted in the forums and that fails too. Does anybody have a procedure/file that works on Feisty 64?


System Info:
64bit Ubuntu 7.04 w/ beryl & emerald
Asus P5WD2-E Premium Mobo W/ onboard 7.1 HD audio
Pentium D 805
Nvidia GeForce XFX 6800 ... with Nvidia restricted driver installed

THANKS!!!
Garrett

---

### Post by fdrake on 2007-06-21
select an audio or video file and right click it and select copy. open the terminal and type mplayer then right click and paste. copy all the output of mplayer and paste it here so we get what kind of errors there are, codecs missings or device not found.

did u activate all the repositories ([how to]("https://help.ubuntu.com/community/Repositories/Ubuntu"))and select the latest gstreamer codec for mplayer?

---

### Post by gargar934 on 2007-06-21
Thanks so much for the reply...

I know that I have all the repositories activated, and I'm certain I recently installed a gstreamer file...just not sure that its the most up to date. I wish I had thought to view the outputs in the terminal, still getting used to troubleshooting in linux, as soon as possible I will post those outputs (I'm currently at work and away from my favorite toy :( ).

---

### Post by gargar934 on 2007-06-21
Hi all,

Here is the error I get when I try to open media in mplayer:

gar@DesktopDeGar:~$ mplayer '/home/gar/Examples/Experience ubuntu.ogg'
MPlayer 2:1.0~rc1-0ubuntu9.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) D  CPU 2.66GHz (Family: 15, Model: 4, Stepping: 7)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/gar/Examples/Experience ubuntu.ogg.
[Ogg] stream 0: video (Theora v3.2.0), -vid 0
[Ogg] stream 1: audio (Vorbis), -aid 0
Ogg file format detected.
VIDEO:  [theo]  360x288  24bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[theora @ 0xf04c30]Missing extradata!
Could not open codec.
VDecoder init failed :(
Opening video decoder: [theora] Theora/VP3
VDec: vo config request - 360 x 288 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.25:1 - prescaling to correct movie aspect.
VO: [xv] 360x288 => 360x288 Planar YV12 
Selected video codec: [theora] vfm: theora (Theora (free, reworked VP3))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 22050 Hz, 2 ch, s16le, 45.3 kbit/6.42% (ratio: 5666->88200)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis decoder)
==========================================================================
alsa-lib: pcm_hw.c:1242:(snd_pcm_hw_open) open /dev/snd/pcmC0D0p failed: Device or resource busy
alsa-lib: pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
alsa-init: playback open error: Device or resource busy
[AO OSS] audio_setup: Can't open audio device /dev/dsp: Device or resource busy
alsa-lib: pcm_hw.c:1242:(snd_pcm_hw_open) open /dev/snd/pcmC0D0p failed: Device or resource busy
alsa-lib: pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
alsa-init: playback open error: Device or resource busy
mcop warning: user defined signal handler found for SIG_PIPE, overriding
Creating link /home/gar/.kde/socket-DesktopDeGar.
can't create mcop directory

---

### Post by Cappy on 2007-06-21
You just have the onboard sound?
Try Going to (System-->Preferences-->Sound) and turning off ESD on the second tab.

---

### Post by gargar934 on 2007-06-21
Yes I only have the onboard sound, and I checked every possible package that had gstreamer in my synaptic manager...still the same errors. Also the unchecking of the ESD didn't fix it either.

Any more thoughts? Can I do anything else to provide more clues about my problem?

---

### Post by fdrake on 2007-06-21
i think it's an alsa related problem , try this, open the terminal and type:
sudo aptitude install alsa gnome-alsamixer

now go to System>Preferences>Sound> Select device tab and on sound events select Autodetect or alsa and run the Test if its working.
on default mixer tracks select alsa mixer

also i would check my alsamixer, so type:
"gnome-alsamixer" on the terminal and look if u have any muted sound device and turn the volume up.
good luck....

---

### Post by purdticker on 2007-06-21
I'm having same exact issue, none of the solutions here have worked yet :(

---

### Post by gargar934 on 2007-06-21
Hi,

I followed those instructions and got these results:

when I clicked 'test' in the sound GUI it crashed, regardless of which 'test' I ran.

when I ran the gnome alsamixer I was able to unmute many of the sources, which caused a terrible high pitch sound (not too loud, but enough to require muting my speakers)...also the output in the terminal window was the following:


gar@DesktopDeGar:~$ gnome-alsamixer

** (gnome-alsamixer:16337): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Channel Mode"!

** (gnome-alsamixer:16337): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Input Source"!

** (gnome-alsamixer:16337): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Input Source"!

** (gnome-alsamixer:16337): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Input Source"!

---

### Post by fdrake on 2007-06-21
are u running as root or as a regular user? root cannot play media files

---

### Post by fdrake on 2007-06-21
> 
gar@DesktopDeGar:~$ gnome-alsamixer

 oh, i see u are runnig as regular user, that's not the case then.

---

### Post by fdrake on 2007-06-21
last try 

sudo aptitude install libesd-alsa0  (from [http://www.solfege.org/Solfege/SoundSetup#toc4](http://www.solfege.org/Solfege/SoundSetup#toc4))
i have to go to sleep now, hope it works, maybe somebody can help u.

---

### Post by gargar934 on 2007-06-21
Thanks for all your help, at least now I have a few more useful packages and codecs. This last one did not solve the problem, but since I am not the only one having problems I am sure some other ubuntu masters will lend their aid.

To the other people who are having these problems: can you look at my hardware configuration and see if there are any similarities...maybe its a driver/hardware problem of sorts.

To the rest of the linux elders: help!

---

### Post by purdticker on 2007-06-22
(since I hadn't gotten very far with ubuntu yet anyway) I decided to reformat my hard drive and install ubuntu again... the very first thing I did was flash install script, sound now works perfectly.  The problem probably lies in one of the many codecs you installed trying to get it to work (at least that's what happened with me)

---

### Post by gargar934 on 2007-06-22
Ok thanks, I'll keep that in mind as a worst-case scenario fall-back plan.

In the mean time, does anyone have any advice on fixing my sound  troubles? I really can't afford to have programs crashing everytime they involve sound...and would really prefer not to have to start from scratch here.

---

### Post by Cappy on 2007-06-23
Here are some related threads:
[http://ubuntuforums.org/showpost.php?p=2871959&postcount=9](http://ubuntuforums.org/showpost.php?p=2871959&postcount=9)
[http://ubuntuforums.org/showthread.php?t=220503](http://ubuntuforums.org/showthread.php?t=220503)

You have a ALC882 so you may want to search for solutions on it.

Also there is this:
[http://ubuntuforums.org/showthread.php?t=205449&highlight=ALC882](http://ubuntuforums.org/showthread.php?t=205449&highlight=ALC882)
incase you need to install a newer version of ALSA.

---

### Post by gargar934 on 2007-06-23
Thanks Cappy!

I'll try these out and post back on how it goes.

---

### Post by gargar934 on 2007-06-23
Great links...the following post in one of them fixed most of my problems. I still have static on the line and can't get the volume maxed out, but its at least there.  VLC and youtube work now, but mplayer still complains. I can deal with this though. Thanks once again, I hope this information will help some other people out there.

> **lodp said:**
> for compiling the driver from alsa source, you have to do the following:

1. make sure you've got the build-essential and linux-headers packages installed.
2. download the latest alsa-driver package from alsa-project.org
3. unpack it into a directory
4. run ```
./configure --with-cards=hda-intel
sudo make
sudo make install
```

5. Then type
```
sudo modprobe snd-hda-intel
```
to load the driver. to get the driver loaded automatically on startup, add "snd-hda-intel" to /etc/modules

at least that's what i've been doing .. pls correct me if anything's wrong with the above..

Stan83: Alsa reportedly works with the ALC260 -- at least that's what this thread says (they apparently got it going during the course of it): [http://ubuntuforums.org/showthread.php?t=76019](http://ubuntuforums.org/showthread.php?t=76019)

if alsamixer says it's ALC883, it's probably the case..

---

