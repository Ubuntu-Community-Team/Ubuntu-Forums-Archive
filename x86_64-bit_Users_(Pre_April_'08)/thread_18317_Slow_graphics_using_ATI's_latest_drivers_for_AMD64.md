---
title: "Slow graphics using ATI's latest drivers for AMD64"
date: 2005-03-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Pse on 2005-03-05
I know ATI related issues are bugging people all around the Linux community, but I haven't been able to sort this out yet! I've read in these forums that people are getting about 5000fps in glxgears using ATI's drivers, but I'm only getting about 840fps! I'm running a 9600SE, so I was expecting at least 2000fps, but I don't know what's wrong. Is this a known issue?
The drivers are correctly installed (fglrxinfo shows ATI's driver as the OpenGL rendering device), and X.org seems to be properly configured. I've tried enabling and disabling DGA extensions in xorg.conf, with no luck (like that should help ;)). I've also uninstalled the xorg-driver-fglrx driver and cleared all files from linux-restricted-modules. I'm sure I'm running ATI's drivers. "fglrxcontrol" shows AGP8X, FastWrites, etc. enabled, and version 8.10.19 of ATi's drivers.
I've tried running UT2004demo and I'm getting MUCH worse performance than under Windows...is this OK?
Thanks =)

P.S.:
FSAA is disabled...blah, blah...I'm pretty much using ATI's standard xorg.conf configuration.

---

### Post by Pse on 2005-03-06
I guess nobody's really having the same problems I do... I'd appreciate if anyone could post their results in glxgear for any ATI card so I can have an idea of what scores I should be expecting. If you could also post your driver's version, I'd appreciate that as well =). Thanks!

[EDIT] In case anyone is interested, here are the modules specified in the xorg.conf file:
```
Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
	#SubSection  "extmod"
      	#	Option    "omit xfree86-dga"   # don't initialise the DGA extension
	#EndSubSection
EndSection
```

(I've commented out the "omit xfree86-dga" section, 'cause it get's loaded anyway if you uncomment it).

Would I be able to use ATI's 32-bit driver on a 64-bit kernel? Just to see if there's any difference?

---

### Post by kubla on 2005-03-07
kubla@ogmios:~ $ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 1.3.4769 (X4.3.0-8.8.25)

kubla@ogmios:~ $ fgl_glxgears
1409 frames in 5.0 seconds = 281.800 FPS
1570 frames in 5.0 seconds = 314.000 FPS
1570 frames in 5.0 seconds = 314.000 FPS
1575 frames in 5.0 seconds = 315.000 FPS
1577 frames in 5.0 seconds = 315.400 FPS
1573 frames in 5.0 seconds = 314.600 FPS

kubla@ogmios:~ $ glxgears
6390 frames in 5.0 seconds = 1278.000 FPS
7922 frames in 5.0 seconds = 1584.400 FPS
7922 frames in 5.0 seconds = 1584.400 FPS
7920 frames in 5.0 seconds = 1584.000 FPS

---

### Post by Pse on 2005-03-07
Thanks, kubla. Apparently my scores of 870fps are not so crazy after all for a 9600SE, considering you have a M9700. On the other hand, according to Rage3D forums, ATI's drivers are really bad for UT2004 in Linux, apparently creating these problems I've been having. Some people have had success. Perhaps, this is related to not being able to load ATI's internal AGP GART, though I doubt it. Time will tell, I'll try to compare Doom3-demo results with the ones I've gotten in Windows...well as soon as I find a way to make it stop segfaulting on me X_X

Thanks, again =)

---

### Post by Nadir on 2005-03-07
[QUOTE=Pse]
```
Section "Module"
	Load	"extmod"
	#SubSection  "extmod"
      	#	Option    "omit xfree86-dga"   # don't initialise the DGA extension
	#EndSubSection
EndSection
```
 (I've commented out the "omit xfree86-dga" section, 'cause it get's loaded anyway if you uncomment it).
[/QUOTE]

In order for the Subsection part to work you need to comment out the Load "extmod" part.

[QUOTE=Pse]Would I be able to use ATI's 32-bit driver on a 64-bit kernel? Just to see if there's any difference?[/QUOTE]

No, on 64bit you need 64bit drivers. You need a 32bit kernel to use the 32bit driver.

Tristan

---

### Post by Pse on 2005-03-07
Whoops! I didn't know that about subsections, thanks a lot for pointing that out! I'll try it as soon as I can restart my X server (can't do that right now).

[EDIT] Nevertheless, issues with UT2004 are well known regarding ATI display adapters, apparently this behaviour's been seen using the OpenGL renderer in several OSes (Windows). It may be related to the way UT2K4 handles textures...I'll have to look into it...I can confirm a stuttering UT2004 performance.

---

### Post by ChaperonNoir on 2005-03-08
Oh shit !

Im starting to realise my installation is bad.

ATI 9800 PRO @ apt-get install fglrx-driver
```
edmond@amd64:~$ glxgears
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
1967 frames in 5.0 seconds = 393.400 FPS
1920 frames in 5.0 seconds = 384.000 FPS
1920 frames in 5.0 seconds = 384.000 FPS
1800 frames in 5.0 seconds = 360.000 FPS
1920 frames in 5.0 seconds = 384.000 FPS
1920 frames in 5.0 seconds = 384.000 FPS
1920 frames in 5.0 seconds = 384.000 FPS
1920 frames in 5.0 seconds = 384.000 FPS
1827 frames in 5.0 seconds = 365.400 FPS
X connection to :0.0 broken (explicit kill or server shutdown).
edmond@amd64:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

edmond@amd64:~$ fglrxcontrol
bash: fglrxcontrol: command not found
edmond@amd64:~$ fgl_glxgears
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  144 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  30
  Current serial number in output stream:  30
edmond@amd64:~$     
``` 

Any ideas ?

Why is the console talking about xfree ? Im using Xorg darn it !

---

### Post by Pse on 2005-03-09
Well, it's OK, many drivers (such as ATI's earliers) recognise your X.org installation as a Xfree86. It's not a big deal. However you have NOT enabled your GLX drivers, you are still renderng with MesaGL!
To load ATI's drivers, create a xorg.conf file with ATI's tool: fglrxconfig.

[EDIT] When you issue a "fglrxinfo", you should see your card's name in "OpenGL vendor/renderer/...". Check it. Here's my fglrxinfo output:
```
pse@A64LIN:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600SE Generic
OpenGL version string: 1.3.4893 (X4.3.0-8.10.19)
```

---

