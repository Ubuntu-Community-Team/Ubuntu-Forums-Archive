---
title: "Can ANYONE play WMVs in 8.04 x64?"
date: 2008-07-03
forum: x86 64-bit Users
---

### Post by benign on 2008-07-03
Because I'm having a hell of a time... :confused:

---

### Post by philinux on 2008-07-03
Yes with totem.

I assume you've done the ubuntu-restricted-extras and medibuntu stuff.

---

### Post by thegr8brian on 2008-07-03
I watch them with VLC...Streaming works too

---

### Post by stchman on 2008-07-03
> **benign said:**
> Because I'm having a hell of a time... :confused:

I can watch them just fine.  Install the CODECs.

```

sudo apt-get -y install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
```

---

### Post by benign on 2008-07-03
> **philinux said:**
> Yes with totem.

I assume you've done the ubuntu-restricted-extras and medibuntu stuff.

Yes sir... I have the extras and w64codecs. I've tried to play them with VLC and totem, but to no avail. 

If I open it with "Movie player totem (xine backend)" the error is:

> 
Video codec 'MSS2' is not handled. You might need to install additional plugins to be able to play some types of movies


with "Movie player (Gstreamer)" the error message is:

> 
The playback of this movie requires the following decoders which are not installed:

video/x-asf-unknown decoder
Windows Media Speech decoder


With VLC, the slider just moves without any sound or video.

---

### Post by benign on 2008-07-03
> **stchman said:**
> I can watch them just fine.  Install the CODECs.

```

sudo apt-get -y install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
```

I ran that and this is what I got. :(

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
gstreamer0.10-ffmpeg is already the newest version.
gstreamer0.10-plugins-bad is already the newest version.
gstreamer0.10-plugins-bad-multiverse is already the newest version.
gstreamer0.10-plugins-ugly is already the newest version.
gstreamer0.10-plugins-ugly-multiverse is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 33 not upgraded.

```

I don't know if this helps, but when I run totem from the terminal, it comes back with:

```

** Message: don't know how to handle audio/x-wms, bitrate=(int)20000, width=(int)16, depth=(int)16, rate=(int)22050, channels=(int)1, block_align=(int)1088, codec_data=(buffer)10000400000000000000000000001000000005fa9a0005c92d48805a600000000000000000000000000000000000
** Message: don't know how to handle video/x-asf-unknown, fourcc=(fourcc)MSS2, format=(fourcc)MSS2, framerate=(fraction)25/1
** Message: Error: You do not have a decoder installed to handle this file. You might need to install the necessary plugins.
gstplaybasebin.c(2284): prepare_output (): /play

** Message: Missing plugin: gstreamer|0.10|totem|video/x-asf-unknown decoder|decoder-video/x-asf-unknown, fourcc=(fourcc)MSS2, format=(fourcc)MSS2 (video/x-asf-unknown decoder)
** Message: Missing plugin: gstreamer|0.10|totem|Windows Media Speech decoder|decoder-audio/x-wms, bitrate=(int)20000, depth=(int)16, block_align=(int)1088 (Windows Media Speech decoder)
no application found
** Message: No installation candidate for missing plugins found.
** Message: don't know how to handle audio/x-wms, bitrate=(int)20000, width=(int)16, depth=(int)16, rate=(int)22050, channels=(int)1, block_align=(int)1088, codec_data=(buffer)10000400000000000000000000001000000005fa9a0005c92d48805a600000000000000000000000000000000000
** Message: don't know how to handle video/x-asf-unknown, fourcc=(fourcc)MSS2, format=(fourcc)MSS2, framerate=(fraction)25/1
** Message: Error: You do not have a decoder installed to handle this file. You might need to install the necessary plugins.
gstplaybasebin.c(2284): prepare_output (): /play

** Message: Missing plugin: gstreamer|0.10|totem|video/x-asf-unknown decoder|decoder-video/x-asf-unknown, fourcc=(fourcc)MSS2, format=(fourcc)MSS2 (ignoring)
** Message: Missing plugin: gstreamer|0.10|totem|Windows Media Speech decoder|decoder-audio/x-wms, bitrate=(int)20000, depth=(int)16, block_align=(int)1088 (ignoring)
** Message: All missing plugins are blacklisted, doing nothing

(totem:7458): GStreamer-CRITICAL **: gst_object_unref: assertion `object != NULL' failed


```

The only files in my /usr/lib/codecs are:

cook.so
drvc.so
sipr.so

---

### Post by benign on 2008-07-04
Anybody, help?

---

### Post by philinux on 2008-07-04
Post the output of

```
about:plugins
```

From the firefox address bar.

---

### Post by benign on 2008-07-04
> **philinux said:**
> Post the output of

```
about:plugins
```

From the firefox address bar.

This is it:

```

Shockwave Flash

    File name: npwrapper.libflashplayer.so
    Shockwave Flash 9.0 r124

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
Default Plugin

    File name: libnullplugin.so
    The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

MIME Type 	Description 	Suffixes 	Enabled
* 	All types 	.* 	No
Demo Print Plugin for unix/linux

    File name: libunixprintplugin.so
    The demo print plugin for unix.

MIME Type 	Description 	Suffixes 	Enabled
application/x-print-unix-nsplugin 	Demo Print Plugin for Unix/Linux 	.pnt 	Yes
DivX Browser Plug-In

    File name: mplayerplug-in-dvx.so
    mplayerplug-in 3.50

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	DivX Media Format 	divx 	Yes
video/vnd.divx 	DivX Media Format 	divx 	Yes
QuickTime Plug-in 6.0 / 7

    File name: mplayerplug-in-qt.so
    mplayerplug-in 3.50

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	Quicktime 	mov 	Yes
video/x-quicktime 	Quicktime 	mov 	Yes
image/x-quicktime 	Quicktime 	mov 	Yes
video/quicktime 	Quicktime 	mp4 	Yes
video/quicktime 	Quicktime - Session Description Protocol 	sdp 	Yes
application/x-quicktimeplayer 	Quicktime 	mov 	Yes
application/smil 	SMIL 	smil 	Yes
RealPlayer 9

    File name: mplayerplug-in-rm.so
    mplayerplug-in 3.50

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio 	RealAudio 	ram,rm 	Yes
application/vnd.rn-realmedia 	RealMedia 	rm 	Yes
application/vnd.rn-realaudio 	RealAudio 	ra,ram 	Yes
video/vnd.rn-realvideo 	RealVideo 	rv 	Yes
audio/x-realaudio 	RealAudio 	ra 	Yes
audio/x-pn-realaudio-plugin 	RealAudio 	rpm 	Yes
application/smil 	SMIL 	smil 	Yes
Windows Media Player Plugin

    File name: mplayerplug-in-wmp.so
    mplayerplug-in 3.50

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
application/asx 	Media Files 	* 	Yes
video/x-ms-asf-plugin 	Media Files 	* 	Yes
video/x-msvideo 	AVI 	avi,* 	Yes
video/msvideo 	AVI 	avi,* 	Yes
application/x-mplayer2 	Media Files 	* 	Yes
application/x-ms-wmv 	Microsoft WMV video 	wmv,* 	Yes
video/x-ms-asf 	Media Files 	asf,asx,* 	Yes
video/x-ms-wm 	Media Files 	wm,* 	Yes
video/x-ms-wmv 	Microsoft WMV video 	wmv,* 	Yes
audio/x-ms-wmv 	Windows Media 	wmv,* 	Yes
video/x-ms-wmp 	Windows Media 	wmp,* 	Yes
application/x-ms-wmp 	Windows Media 	wmp,* 	Yes
video/x-ms-wvx 	Windows Media 	wvx,* 	Yes
audio/x-ms-wax 	Windows Media 	wax,* 	Yes
audio/x-ms-wma 	Windows Media 	wma,* 	Yes
application/x-drm-v2 	Windows Media 	asx,* 	Yes
audio/wav 	Microsoft wave file 	wav,* 	Yes
audio/x-wav 	Microsoft wave file 	wav,* 	Yes
mplayerplug-in 3.50

    File name: mplayerplug-in.so
    mplayerplug-in 3.50

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
video/mpeg 	MPEG 	mpg,mpeg 	Yes
audio/mpeg 	MPEG 	mpg,mpeg 	Yes
video/x-mpeg 	MPEG 	mpg,mpeg 	Yes
video/x-mpeg2 	MPEG2 	mpv2,mp2ve 	Yes
audio/mpeg 	MPEG 	mpg,mpeg 	Yes
audio/x-mpeg 	MPEG 	mpg,mpeg 	Yes
audio/mpeg2 	MPEG audio 	mp2 	Yes
audio/x-mpeg2 	MPEG audio 	mp2 	Yes
video/mp4 	MPEG 4 Video 	mp4 	Yes
video/3gpp 	MPEG 4 Video 	mp4,3gp 	Yes
audio/mpeg3 	MPEG audio 	mp3 	Yes
audio/x-mpeg3 	MPEG audio 	mp3 	Yes
audio/x-mpegurl 	MPEG url 	m3u 	Yes
audio/mp3 	MPEG audio 	mp3 	Yes
application/x-ogg 	Ogg Vorbis Media 	ogg 	Yes
audio/ogg 	Ogg Vorbis Audio 	ogg 	Yes
audio/x-ogg 	Ogg Vorbis Audio 	ogg 	Yes
application/ogg 	Ogg Vorbis / Ogg Theora 	ogg 	Yes
audio/flac 	FLAC Audio 	flac 	Yes
audio/x-flac 	FLAC Audio 	flac 	Yes
video/fli 	FLI animation 	fli,flc 	Yes
video/x-fli 	FLI animation 	fli,flc 	Yes
video/x-flv 	Flash Video 	flv 	Yes
video/vnd.vivo 	VivoActive 	viv,vivo 	Yes
application/x-nsv-vp3-mp3 	Nullsoft Streaming Video 	nsv 	Yes
audio/x-mod 	Soundtracker 	mod 	Yes
audio/basic 	Basic Audio File 	au,snd 	Yes
audio/x-basic 	Basic Audio File 	au,snd 	Yes
GCJ Web Browser Plugin (using IcedTea) 1.0

    File name: gcjwebplugin.so
    The GCJ Web Browser Plugin (using IcedTea) executes Java applets.

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	IcedTea 	class,jar 	Yes
application/x-java-applet 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.3 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.3 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.3.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.5 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.6 	IcedTea 	class,jar 	Yes
application/x-java-applet;jpi-version=1.6.0_00 	IcedTea 	class,jar 	Yes
application/x-java-bean 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.3 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.3 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.3.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.5 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.6 	IcedTea 	class,jar 	Yes
application/x-java-bean;jpi-version=1.6.0_00 	IcedTea 	class,jar 	Yes

```

---

### Post by Sef on 2008-07-05
>  Can ANYONE play WMVs in 8.04 x64?  

Are they DRM (Digital Rights/Restricted Management)?  If they are, then that is the problem.

---

### Post by Kilz on 2008-07-05
> **Sef said:**
> Are they DRM (Digital Rights/Restricted Management)?  If they are, then that is the problem.

The orignal poster needs to post a link to the video, then that can be checked if they cant.

---

### Post by benign on 2008-07-05
> **Sef said:**
> Are they DRM (Digital Rights/Restricted Management)?  If they are, then that is the problem.

They play fine in XP Virtualbox without any messages in the license tab in mediaplayer 10, so they don't appear to have DRM. As for the videos, they are the ccent01...31.wmv files from the CBT Nuggets video training courses.

---

### Post by supermerp on 2008-07-06
> **Kilz said:**
> The orignal poster needs to post a link to the video, then that can be checked if they cant.I'm not the original poster, but I'm having issues with some WMV videos. Anything from [this webpage](http://physicslearning2.colorado.edu/tasi/tasi_2007.htm) plays video, but not audio, on 64-bit Hardy. They work in at least 32-bit installation though ([see this blog post](http://fliptomato.wordpress.com/2008/07/05/playing-windows-media-on-ubuntu-804-for-those-damn-tasi-videos/)). I have w64codecs installed. Is this a problem with the w64codecs not being as complete as w32? Are there any simple workarounds that work?

---

### Post by Kilz on 2008-07-06
> **benign said:**
> They play fine in XP Virtualbox without any messages in the license tab in mediaplayer 10, so they don't appear to have DRM. As for the videos, they are the ccent01...31.wmv files from the CBT Nuggets video training courses.

Windows XP has DRM, so saying that a video plays on it (even in a virtual machine) will not prove that the files are not DRM'ed. Please provide a link to a video that does not play.

---

### Post by mad_max0204 on 2008-07-09
I'm in the same problem as one of the guys in previous posts. I have some CBT training videos in wmv and I was able to play them in 32bit mplayer on Gutsy 64bit. Now on Hardy 64bit there is no way I can play them. I dont want to install 32bit mplayer because I want to find a solution for this. I installed mplayer with all libs as it was described in the guide ([http://ubuntuforums.org/showthread.php?t=558538&highlight=mplayer](http://ubuntuforums.org/showthread.php?t=558538&highlight=mplayer)). Mplayer wont play them, totem wont play them. It doesnt work in VLC either.Is there ANY way to play wmv files in 64bit Hardy with any 64bit video player ???

---

### Post by mad_max0204 on 2008-07-13
Bump

---

### Post by Kilz on 2008-07-13
> **mad_max0204 said:**
> I'm in the same problem as one of the guys in previous posts. I have some CBT training videos in wmv and I was able to play them in 32bit mplayer on Gutsy 64bit. Now on Hardy 64bit there is no way I can play them. I dont want to install 32bit mplayer because I want to find a solution for this. I installed mplayer with all libs as it was described in the guide ([http://ubuntuforums.org/showthread.php?t=558538&highlight=mplayer](http://ubuntuforums.org/showthread.php?t=558538&highlight=mplayer)). Mplayer wont play them, totem wont play them. It doesnt work in VLC either.Is there ANY way to play wmv files in 64bit Hardy with any 64bit video player ???

Can you give us a link to one?

---

### Post by darkaudit on 2008-07-13
I'm guessing it's the ones here: [http://www.cbtnuggets.com/webapp/videos](http://www.cbtnuggets.com/webapp/videos)

---

### Post by mad_max0204 on 2008-07-13
> **Kilz said:**
> Can you give us a link to one?

I cant play ANY wmv video in 64bit mplayer.
Basically what is the problem and what would be solution ??

Thanks

---

### Post by philinux on 2008-07-13
I've just done a reinstall 3 hours ago. Home is on it's own partition so was very easy. 

I enabled medibuntu repo, installed ubuntu-restricted-extras.

WMV's work out the box with totem, mpg's and even BBC streaming audio. Not to mention java and flash.

---

### Post by mad_max0204 on 2008-07-19
Yeah I'm mainly trying to play CBT nuggets videos.
Tried reinstall and still nothing.
Maybe those wmv files have something. I dont know.
I used to play them on 7.10 with 32bit mplayer I installed after adding some repository. Now I cant find that repository. I think that package name was ia32-mplayer. I remember I installed it via Synaptics.
Anyways any other ideas ???

---

### Post by Arup on 2008-07-20
WMV works fine here, with Totem, MPlayer or VLC.

---

### Post by mediajunkie on 2008-07-21
Hi,

Same here, Can't play any WMV / avi(xvid) in mplayer, totem, vlc... 
However, I can open the avi (xvid) in AVIDEMUX (gtk+) and play perfectly
Gxine will only play audio part of it. 

Anybody any Idea?

---

### Post by erkanea on 2008-07-22
im able to play wmv file (tested with 1 video)

hardy fully updated, x86-64, enabled medibuntu repo.

tested with vlc,totem,mplayer guess its enough :lolflag:

btw it might be helpful if you guys who cant run them to open a terminal and start player there so you can see error messages if there is any. then google will help you for sure.

---

### Post by billynomates on 2008-07-22
Do they work in VLC?

---

### Post by erkanea on 2008-07-22
> **billynomates said:**
> Do they work in VLC?

if you asked to me, then yes they do work in VLC

---

### Post by mediajunkie on 2008-07-22
> **mediajunkie said:**
> Hi,

Same here, Can't play any WMV / avi(xvid) in mplayer, totem, vlc... 
However, I can open the avi (xvid) in AVIDEMUX (gtk+) and play perfectly
Gxine will only play audio part of it. 

Anybody any Idea?



For me; solved by disabling the visual effects (compiz-fusion) as I had set the players to automatically flip to full screen upon opening. And that is a well known issue if you use compiz effects and decorations (see [http://ubuntuforums.org/showthread.php?t=803239](http://ubuntuforums.org/showthread.php?t=803239) )

---

### Post by mad_max0204 on 2008-07-22
Hm basically I tried almost every trick I found on the web. I think that next solution to my problem is runing wmv files on my business laptop with windows on it. Its really annoying that I have to do it this way. Anyways this is the output of mplayer playing one of those wmv's.

Mplayer info

MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4400+ (Family: 15, Model: 107, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

Output when playing wmv

Playing ie.wmv.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [MSS2]  640x480  24bpp  1000.000 fps  250.0 kbps (30.5 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Requested video codec family [wmsdmod] (vfm=dmo) not available.
Enable it at compilation.
Cannot find codec matching selected -vo and video format 0x3253534D.
Read DOCS/HTML/en/codecs.html!
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 1 ch, s16le, 32.0 kbit/4.54% (ratio: 4006->88200)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
AO: [pulse] 44100Hz 1ch s16le (2 bytes per sample)
Video: no video
Starting playback...


Sound plays but no video. Any help regarding this will be appreciated.

Thanks

---

### Post by mediajunkie on 2008-07-22
FYI, 
I don't know if following actions will solve your problem, but here is what I did on one of my other machines with wmv issues.

open synaptic

[LIST]
[*]UN-installed anything with mplayer, ore related to,  
[*]Installed anything with totem including the xine .... g streamer, ..mozilla plug-ins. (basically anything with totem or g streamer in it.) 
[*]Also as above already posted, disable visual effects.
[/LIST]

Don't shoot me if it doesn't help or solve anything at all, Just sharing my actions, didn't claim any wisdom. :lolflag:

---

### Post by mad_max0204 on 2008-07-22
Dude, mplayer is not gonna go because I watch HD material with it but thanks for info.

Anyone else on this subject ?

---

### Post by mad_max0204 on 2008-07-24
bump

---

### Post by Hurricanex on 2008-07-24
New poster (and Ubuntu user) here, hope I could help and be helped.

My mplayer-plugin has been really messing with me. My flash and wmv were working(save the audio for wmv), and then the video for wmv just suddenly stopped. So, I changed the name of the plug-in for mplayer.conf and mplayerplug-in.conf to see if it would do anything(... I just changed the name at the end, like:

mv mplayerplug-in.conf mplayerplug-in.conf.bak

mv mplayer.conf mplayer.conf.bak)

I did that, and then my video started to work for everything. HOWEVER, I still can't get audio for the life of me for wmv.

I was hoping if anyone can offer advice. I'm on i386. I installed w32codec.

---

### Post by mad_max0204 on 2008-07-27
Why would you ask a question related to 32bit system in a section of forum dedicated to 64bit system ?? Wmv files sould work in 32bit distros with no problem.

I still cant find answer for my question...

---

### Post by xen-uno on 2008-07-27
No problem here with wmv's (FF3 embedded or stand alone) using Totem Movie player w/ totem-xxx (where xxx = xine, plugins, mozilla, common), libtotem-plparser10, and a boatload of libxine packages from Synaptics.

---

### Post by tobydeemer on 2008-07-31
Hi all-

I am in the same boat. Here's the twist though- certain wmv files will play with audio. 

But I have some Train Signal CBT videos, and they will play video, but no audio. I have medibuntu repos and w64codecs, etc...

Here's output of VLC from terminal:
tobydeemer@toby-laptop:~$ vlc
VLC media player 0.8.6e Janus
[00000312] main decoder error: no suitable decoder module for fourcc `wmas'.
VLC probably does not support this sound or video format.
[00000289] main playlist: stopping playback



Any ideas?

---

### Post by mad_max0204 on 2008-08-01
So you basically have video in CBT files and no audio ??
Lets merge systems. I can play only audio.

I posted my console output so if anyone can help would be much appreciated.

---

### Post by tobydeemer on 2008-08-02
Yeah, and certain WMVs will play fine. I'm suspecting that it's a DRM issue...

---

### Post by Kilz on 2008-08-02
> **tobydeemer said:**
> Yeah, and certain WMVs will play fine. I'm suspecting that it's a DRM issue...

Almost all instances where one wmv will play and another wont are drm issues. These will never be solved because Microsoft will never release the drm. These files are not even playable on 32bit.

---

### Post by mad_max0204 on 2008-08-06
Then its another shame from Myco*ksoft that they are shameless bastards

I hate them even more now

(dont misinterpret this, I'm not a windows hater, so pls dont flame me about it)


Anyways tobydeemer, I would like to see your mplayer output on those CBT files.

Thanks

---

### Post by thelinuxer on 2008-08-07
> **mad_max0204 said:**
> Then its another shame from Myco*ksoft that they are shameless bastards

I hate them even more now

(dont misinterpret this, I'm not a windows hater, so pls dont flame me about it)


Anyways tobydeemer, I would like to see your mplayer output on those CBT files.

Thanks

The problems with the CBT nuggets is that they use their non-standard codec for encoding their video files(or I guess the codec that comes with the desktop recording tool). 

Of my 32bit hardy system the videos work just fine because I installed the w32codecs package from the medibuntu repo. This package installs lots of windows based codecs that your player can use.

Unfortunately there is no equivalent for 64bit systems, and the w64codec 
package  is a joke , in other words it's almost empty. The w32codecs is 14.3 MB in size while the w64codecs is only 210 KB. It's looks like there is no interest in win64 multimedia. 

There is 2 solutions for the problem:

1. Compile mplayer with all its dependencies in 32bit emulation mode. It will work fine but will take a lot of time.

2. Use wine and run the 32 bit windows version of mplayer.

I attached a script to this message. This script will install wine, download mplayer and the needed w32codecs. All you have to do next is go to the folder it created and run "gmplayer.exe"

Hope that helps :)

---

### Post by oronte on 2008-08-08
> **tobydeemer said:**
> Hi all-

I am in the same boat. Here's the twist though- certain wmv files will play with audio. 

But I have some Train Signal CBT videos, and they will play video, but no audio. I have medibuntu repos and w64codecs, etc...

Here's output of VLC from terminal:
tobydeemer@toby-laptop:~$ vlc
VLC media player 0.8.6e Janus
[00000312] main decoder error: no suitable decoder module for fourcc `wmas'.
VLC probably does not support this sound or video format.
[00000289] main playlist: stopping playback



Any ideas?

Have you tried it in Totem, doesn't work for me in VLC, but does work in Totem.

---

### Post by CheeseAndToast on 2008-08-09
the following worked for me.  I tired playing ccna cbtnuggets and got same error message.

've installed restricted-extras, xine-plugin, ffmpeg in gstreamer and w32-codecs...

In VLC:

Try to change the preferences settings.
In Audio (if you are on Hardy) it should be Pulse.
In Video, try XV

See the following for more information:

[HTML]http://ubuntuforums.org/showthread.php?t=884230&highlight=wmv[/HTML]

---

### Post by Elim_Garak on 2008-08-10
Hmmm.  This is more of a workaround than a fix, but it might work.  Have you tried installing the tovid suite?  Whenever I find a video that just isn't playing right, I run it through tovid and have it converted to a DVD compliant mpeg.  I've never had a problem getting both the video and audio to work properly after that.  DRM is another issue altogether, though.

---

### Post by eyelessfade on 2008-08-25
Just to sum this up. No you can't watch wmv9 files in x64 linux. At least not with sound. this is because ffmpeg don't support it yet. You can compile a 32bit version of a player to watch it, mplayer works fine.

---

### Post by bongtothesoo on 2009-01-22
i am having similar issues... i guess my question would be how do you comile 32bit players in a 64 bit ubuntu?

---

### Post by rdingram on 2009-03-07
Here was my solution for my cbtnuggets ccna videos.

virtualbox + windows xp + wmv2flv = alot of flash versions of the videos.

Copy to thumbdrive and then copy back to $HOME on ubuntu. Mplayer loves these.

That was a pain but now I can watch my training videos in Jaunty 64bit.

Peace.

---

### Post by vmidhun09@gmail.com on 2009-11-13
Dude .. even i was trying to solve the same prob.. 
Go to Synaptic Package manager --> and type asf ...

You ll find something like this-----------> libavformat-unstripped-52_0 install it.. you also need gnome player or mplayer.

or type this in your terminal : 

sudo wget -c [http://in.archive.ubuntu.com/ubuntu/pool/multiverse/f/ffmpeg/libavformat-unstripped-52_0.svn20090303-1ubuntu2+unstripped1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/multiverse/f/ffmpeg/libavformat-unstripped-52_0.svn20090303-1ubuntu2+unstripped1_i386.deb) 

Hope this ll help you guys..

---

