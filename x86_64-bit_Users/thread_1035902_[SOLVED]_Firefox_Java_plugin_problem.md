---
title: "[SOLVED] Firefox Java plugin problem"
date: 2009-01-10
forum: x86 64-bit Users
---

### Post by WildeBeest on 2009-01-10
I installed the 64 bit java plugin (Java SE 6 Update 12 build 03)
 
the command
java -version
java version "1.6.0_0"
OpenJDK  Runtime Environment (build 1.6.0_0-b11)
OpenJDK 64-Bit Server VM (build 1.6.0_0-b11, mixed mode)

When I load a page in firefox that has java content I get Missing plugin
I then attempt to install it I get a choice of two

GCJ Web Browser Plugin
or
The GCJ Web Browser Plugin (using OpenJDK)

When I select the first choice:
I click next and it tells me "Package 'gcjwebplugin' is already installed"

and if I select the second one:
"The GCJ Web Browser Plugin (using OpenJDK)  installed"

Neither on works.

Any ideas?



about:plugins gives me the following
```

Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 d20

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
Adobe Reader 8.0

    File name: nppdf.so
    The Adobe Reader plugin is used to enable viewing of PDF and FDF files from within the browser.

MIME Type 	Description 	Suffixes 	Enabled
application/pdf 	Portable Document Format 	pdf 	Yes
application/vnd.fdf 	Acrobat Forms Data Format 	fdf 	Yes
application/vnd.adobe.xfdf 	XML Version of Acrobat Forms Data Format 	xfdf 	Yes
application/vnd.adobe.xdp+xml 	Acrobat XML Data Package 	xdp 	Yes
application/vnd.adobe.xfd+xml 	Adobe FormFlow99 Data File 	xfd 	Yes
iTunes Application Detector

    File name: librhythmbox-itms-detection-plugin.so
    This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.

MIME Type 	Description 	Suffixes 	Enabled
application/itunes-plugin 			Yes
Totem Web Browser Plugin 2.22.1

    File name: libtotem-basic-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-ogg 	- 	ogg 	Yes
application/ogg 	Ogg multimedia 	ogg 	Yes
audio/ogg 	Ogg Audio 	oga 	Yes
audio/x-ogg 	Ogg Audio 	ogg 	Yes
video/ogg 	Ogg Video 	ogv 	Yes
video/x-ogg 	Ogg Video 	ogg 	Yes
application/annodex 	- 	anx 	Yes
audio/annodex 	- 	axa 	Yes
video/annodex 	- 	axv 	Yes
video/mpeg 	MPEG video 	mpg, mpeg, mpe 	Yes
audio/wav 	WAV audio 	wav 	Yes
audio/x-wav 	WAV audio 	wav 	Yes
audio/mpeg 	MP3 audio 	mp3 	Yes
application/x-nsv-vp3-mp3 	NullSoft video 	nsv 	Yes
video/flv 	Flash video 	flv 	Yes
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible (compatible; Totem)

    File name: libtotem-complex-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio-plugin 	RealAudio document 	rpm 	Yes
VLC Multimedia Plugin (compatible Totem 2.22.1)

    File name: libtotem-cone-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-vlc-plugin 	unknown 		Yes
application/vlc 	unknown 		Yes
video/x-google-vlc-plugin 	unknown 		Yes
Windows Media Player Plug-in 10 (compatible; Totem)

    File name: libtotem-gmp-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-mplayer2 	AVI video 	avi, wma, wmv 	Yes
video/x-ms-asf-plugin 	ASF video 	asf, wmv 	Yes
video/x-msvideo 	AVI video 	asf, wmv 	Yes
video/x-ms-asf 	ASF video 	asf 	Yes
video/x-ms-wmv 	Windows Media video 	wmv 	Yes
video/x-wmv 	Windows Media video 	wmv 	Yes
video/x-ms-wvx 	Microsoft ASX playlist 	wmv 	Yes
video/x-ms-wm 	ASF video 	wmv 	Yes
application/x-ms-wms 	Windows Media video 	wms 	Yes
application/asx 	Microsoft ASX playlist 	asx 	Yes
audio/x-ms-wma 	Windows Media audio 	wma 	Yes
DivX® Web Player

    File name: libtotem-mully-plugin.so
    DivX Web Player version 1.4.0.233

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	AVI video 	divx 	Yes
QuickTime Plug-in 7.2.0

    File name: libtotem-narrowspace-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QuickTime video 	mov 	Yes
video/mp4 	MPEG-4 video 	mp4 	Yes
image/x-macpaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	QuickTime image 	pict, pict1, pict2 	Yes
video/x-m4v 	MPEG-4 video 	m4v 	Yes
Shockwave Flash

    File name: npwrapper.libflashplayer.so
    Shockwave Flash 10.0 r12

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
```

---

### Post by namdung on 2009-01-10
Sometimes having both Sun and OpenJDK may conflict in some applications. I suggest u remove OpenJDK from *Synaptic package Manager* and see how it goes.

---

### Post by WildeBeest on 2009-01-10
I have netbeans installed, I believe openJDK is a dependency of it.

---

### Post by WildeBeest on 2009-01-10
Of all you experts on here, someone must have an answer.:(

---

### Post by Arup on 2009-01-10
Just use Sun Java, remove Open JDK and Iced Tea plugin. Also make sure Sun is set to system wide Java.

---

### Post by garnser on 2009-01-11
I take it that you copied or symlinked libnpjp2.so to /usr/lib/mozilla/plugins ?

/Jonathan

---

### Post by tuxxy on 2009-01-11
Just for your future reference you could have easily installed Java with Flash, codecs and much more by installing the package ubuntu-restricted-extras
```

sudo apt-get install ubuntu-restricted-extras
```

[http://packages.ubuntu.com/intrepid/ubuntu-restricted-extras](http://packages.ubuntu.com/intrepid/ubuntu-restricted-extras)

---

### Post by WildeBeest on 2009-01-11
> **garnser said:**
> I take it that you copied or symlinked libnpjp2.so to /usr/lib/mozilla/plugins ?

/Jonathan

Yes

---

### Post by WildeBeest on 2009-01-11
I removed Open JDK and Iced Tea plugin, re-installed jre-6u12-ea-bin-b03-linux-amd64-22_dec_2008.bin, now I'm good to go,

---

### Post by raypsi on 2009-01-11
[http://ubuntuforums.org/showthread.php?t=1019314](http://ubuntuforums.org/showthread.php?t=1019314)

is the post I used to get the plugin to work although I used a secure link to download and I didn't get the java as a default. the plugin showed in this url addy: about:plugins in my 64bit firefox.

---

### Post by JohnnyJonJon on 2009-11-11
It seems Karmic version of ubuntu-restricted-extras does not have java or it did not install for me.

---

