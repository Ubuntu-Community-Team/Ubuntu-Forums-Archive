---
title: "DVD Playback Broken (Jaunty 9.04 64-bit)"
date: 2009-06-13
forum: x86 64-bit Users
---

### Post by mendieta on 2009-06-13
Hi, 

**Summary:** I am running 64 bit Kubuntu Jaunty (9.04). DVD Playback is just broken (both from the DVD Drive and from an ISO backup on the HD). DVD Playback works just fine in the same distro, 32 bit version.

**Details:** I have installed all the restricted software you typically need:

```

~$ dpkg --get-selections |grep -i dvd
dvd+rw-tools                                    install
libdvdcss2                                      install
libdvdnav4                                      install
libdvdread4                                     install
lsdvd                                           install

~$ dpkg --get-selections |grep -i kubuntu |grep restrict
kubuntu-restricted-extras                       install

~$ dpkg --get-selections |grep -i  codec
libavcodec-unstripped-52                        install
libk3b2-extracodecs                             install
libk3b3-extracodecs                             install
non-free-codecs                                 install
w64codecs                                       install

```

The most reliable mediaplayer in my experience (vlc) is failing with a segfault! 

```

~$ vlc Video/Movies/iso/shrek_2.iso 
VLC media player 0.9.9a Grishenko                   
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team                                                                                                   
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=x86_64-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=x86_64-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'                                                         
[00000001] main libvlc debug: translation test: code is "C"                                            
libdvdnav: Using dvdnav version 4.1.3                                                                  
libdvdread: Using libdvdcss version 1.2.10 for DVD access                                              
libdvdnav: DVD Title: SHREK_2_US_4X3                                                                   
libdvdnav: DVD Serial Number: 30dd2a02                                                                 
libdvdnav: DVD Title (Alternative):                                                                    
libdvdnav: Unable to find map file '/home/lmilano/.dvdnav/SHREK_2_US_4X3.map'                          
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1                             

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x000001bb
libdvdread: Elapsed time 0                                  
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000290
libdvdread: Elapsed time 0                                  
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000004cb
libdvdread: Elapsed time 0                                  
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00000680
libdvdread: Elapsed time 0                                  
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0000073b
libdvdread: Elapsed time 0                                  
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x000028a4
libdvdread: Elapsed time 0                                  
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0000297f
libdvdread: Elapsed time 0                                  
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x000029a6
libdvdread: Elapsed time 0                                  
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x00002a61
libdvdread: Elapsed time 0                                  
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x00002e89
libdvdread: Elapsed time 0                                  
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x000393f3
libdvdread: Elapsed time 0                                  
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x0028bc5d
libdvdread: Elapsed time 0                                  
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x0028bd18
libdvdread: Elapsed time 0                                  
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x0028c098
libdvdread: Elapsed time 0                                  
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x0028c20e
libdvdread: Elapsed time 0                                  
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x00294293
libdvdread: Elapsed time 0                                  
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x0029434e
libdvdread: Elapsed time 0                                  
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x002970b4
libdvdread: Elapsed time 0                                  
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x0029716f
libdvdread: Elapsed time 0                                  
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x002b5407
libdvdread: Elapsed time 0                                  
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x002b54c2
libdvdread: Elapsed time 0                                  
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x002eb77d
libdvdread: Elapsed time 0                                  
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x002eb838
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_0.VOB at 0x0035bec7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_1.VOB at 0x0035c75b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_0.VOB at 0x00397784
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_1.VOB at 0x0039783f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_0.VOB at 0x0039f424
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_1.VOB at 0x0039f4df
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_0.VOB at 0x003ac83d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_1.VOB at 0x003ac8f8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_16_0.VOB at 0x003b9951
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_16_1.VOB at 0x003b9a0c
libdvdread: Elapsed time 0
libdvdread: Found 16 VTS's
libdvdread: Elapsed time 0
[00000493] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
[WARN 25788] polkit-session.c:144:polkit_session_set_uid(): session != NULL
 Not built with -rdynamic so unable to print a backtrace
Segmentation fault

```

Before getting the crash, what I do is to open the dvd, and I can see the root-menu, but when I click on "Play Movie" I get the crash while the player seems to be trying to load the movie. Note that there as an assertion for a null pointer that fails right before the crash.

This seems like an issue with libdvdnav I guess. I tried re-installing all packages that include the word dvd, and no charm. 

I also tried disabling the dreaded pulse-audio from the KDE System Settings. No charm, either. That could be, though, vlc not using the KDE sound system. Maybe I should uninstall Pulse Audio? 

Other media players also have this issues (KMplayer, Mplayer, Xine). 

Any pointers? This is my first 64 bit install, and the first time in years I have any issue with DVD playback (except some newer Disney DVD's that can't be decripted currently).

Many thanks in advance!

---

### Post by mendieta on 2009-06-13
It was the dreaded PulseAudio! I followed my own advice and uninstalled it, now dvd playback is back! I will be updating the original post and the thread subject.

---

