---
title: "Help!"
date: 2008-03-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by cjmarshall4 on 2008-03-05
I'm completely new to Ubuntu and to linux; I;ve spent the last week trying to install stuff reading up on things and still cant get anywhere.

I've successfully installed ubuntu x64 edition on my machine, on a partition of my hard drive, one of 4.

In my windows os i do the following and want to do these things with ubuntu.

First of all I'm an animator and will want to use softimage xsi. However we'll come to that later. 

my priority here is dual screen, I need dual screen, one of those things; once you have it you cant live without it. 

Secondly i use a linksys WUSB11 with windows to connect to the net. I've read on forums about a driver for ubuntu that can make this work but i have no idea how to install this and am baffled by the code i see.
- so getting this working is a pretty high priority.


Thirdly i also have a hell of a lot of music. Around 50 GB on an internal secondary sata drive. Ubuntu can see this but can't play the files because of codec issues. 
A quick web search told me about automatix; but i couldnt get that to install. it said the followin in the package installer window:-

Error: Dependency is not satisfiable: tango-icon-theme-common

no idea what this means! lol

I'm quite ashamed and surprised at myself, I'm well read and well equipped in windows i've been using it for about 12 years and can solve almost any problem but Ubuntu linux is baffling me, so its up to you guys to keep my interest in this new OS.

I might be asking for a lot from you but please help because if i can't get this to work soon, i'm afraid i might give up!

Cheers

Chris Marshall

---

### Post by NightwishFan on 2008-03-05
Hi and welcome! I cannot really help directly with much of those issues since I have never had them personally. I can, however, lead you in a good direction.

When you post, remember to make the title more relevant to your problems so someone will be more interested in reading. Try this page for some basic Ubuntu stuff.

[http://www.psychocats.net/ubuntu/]("http://www.psychocats.net/ubuntu/")


The search function is your friend! Also I believe there is a REALLY good open source animation program. I forgot what it is called. Might be blender but then again that might not be what im thinking of.

About the dependency. I believe just use:

sudo apt-get update

And then try again.

---

### Post by cjmarshall4 on 2008-03-05
yeh i just tried that saw it on a forum. 

It doesnt seem to work still no luck. any other ideas on any of my issues anyone?!

cheers

Chris Marshall

---

### Post by cjmarshall4 on 2008-03-07
any help guys, still not gettin anywhere. 

I think my version of ubuntu muight be corrupted.

I checked the cd and the iso file with wind5sum before i installed but i cnat seem to make any sense of the problems that im having. 

any ideas

Cheers

Chris Marshall

---

### Post by steveneddy on 2008-03-07
[Go to this link. ]("http://ubuntuforums.org/showthread.php?t=368607")

It tells you how to do everything you want step by step.

Halfway down the first post on this thread starts the How to's to help you out.

---

### Post by steveneddy on 2008-03-07
according to[ this thread]("http://ubuntuforums.org/showthread.php?t=558538&highlight=codecs"), you can install of these lib files and get playback of almost everything.

In terminal, copy and paste this:

```

sudo apt-get install avifile-divx-plugin avifile-xvid-plugin gawk \
libxcursor-dev ladspa-sdk liba52-0.7.4 liba52-0.7.4-dev libaa1-dev libartsc0 \
libartsc0-dev libasound2-dev libatk1.0-dev libaudiofile-dev libavcodec1d libavcodec-dev \
libavformat1d libavformat-dev libavifile-0.7c2 libavifile-0.7-dev libavutil1d \
libavutil-dev libcaca-dev libcairo2-dev libcdparanoia0-dev libcucul-dev libdv4-dev \
libdirectfb-dev libdirectfb-extra libdbus-1-dev libdbus-glib-1-dev libdc1394-13 \
libdc1394-13-dev libdfb++-0.9-25 libdfb++-dev libdts-dev libdvdnav4 libdvdnav-dev \
libdvdread3 libdvdread-dev libebml0 libebml-dev libenca0 libenca-dev libesd0-dev \
libexpat1-dev libfaac0 libfaac-dev libfaad2-0 libfaad2-dev libfame-0.9 libfame-dev \
libflac++6 libflac-dev libflac++-dev libfontconfig1-dev libfontenc-dev libfreetype6-dev \
libfribidi-dev libgdk-pixbuf2 libgdk-pixbuf-dev libgii1 libgii1-dev libgii1-target-x \
libgl1-mesa-dev libglib1.2 libglib1.2-dev libglib2.0-dev libglu1-mesa-dev \
libglu1-xorg-dev libgsm1 libgsm1-dev libgtk1.2 libgtk1.2-common libgtk1.2-dev \
libgtk2.0-dev libice-dev libggi2 libggi2-dev libggimisc2 libggimisc2-dev libggiwmh0 \
libggiwmh0-dev libjpeg62-dev liblame0 liblame-dev liblivemedia-dev liblzo1 liblzo-dev \
liblzo2-2 liblzo2-dev libmad0 libmad0-dev libmatroska0 libmatroska-dev libmikmod2 \
libmikmod2-dev libmp4v2-0 libmp4v2-dev libmpcdec3 libmpcdec-dev libncurses5-dev \
libogg-dev libpango1.0-dev libpng12-dev libpopt-dev libpostproc1d libpostproc-dev \
libraw1394-dev libsdl1.2-dev libslang2-dev libsmbclient-dev libsm-dev libspeex-dev \
libsvga1 libsvga1-dev libsysfs-dev libtheora-dev libungif4-dev libungif4g \
libvorbis-dev libx11-dev libx264-54 libx264-dev libxau-dev libxcomposite-dev \
libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev libxfont-dev libxft-dev \
libxi-dev libxinerama-dev libxrandr-dev libxrender-dev libxsharp-dev libxv-dev \
libxvidcore4 libxvidcore4-dev libxvmc1 libxvmc-dev libxxf86dga-dev libxxf86vm-dev \
mesa-common-dev pnet-interpreter sharutils toolame ttf-bitstream-vera \
x11proto-composite-dev x11proto-core-dev x11proto-damage-dev \
x11proto-fixes-dev x11proto-fonts-dev x11proto-input-dev x11proto-kb-dev \
x11proto-randr-dev x11proto-render-dev x11proto-video-dev x11proto-xext-dev \
x11proto-xf86dga-dev x11proto-xf86vidmode-dev x11proto-xinerama-dev \
xlibs-static-dev xtrans-dev zlib1g-dev

```

---

