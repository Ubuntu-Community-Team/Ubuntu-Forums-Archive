---
title: "glx gears output"
date: 2005-10-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by luckyaba on 2005-10-13
How do i get glx gears to display the output?

---

### Post by loupy on 2005-10-13
glxgears -iacknowledgethatthistoolisnotabenchmark

(seriously, not a joke)

---

### Post by luckyaba on 2005-10-13
benchmark? i am just curious as to the output in relation to the past ones i have seen?

---

### Post by Jmonti on 2005-10-13
He's not kidding. That worked for me! LOL

jim@ubuntu:~$ glxgears -iacknowledgethatthistoolisnotabenchmark
62991 frames in 5.0 seconds = 12598.124 FPS
65165 frames in 5.0 seconds = 13032.888 FPS
65251 frames in 5.0 seconds = 13050.129 FPS
65300 frames in 5.0 seconds = 13059.841 FPS
65287 frames in 5.0 seconds = 13057.360 FPS
65190 frames in 5.0 seconds = 13038.000 FPS
65249 frames in 5.0 seconds = 13049.674 FPS
64195 frames in 5.0 seconds = 12838.987 FPS
X connection to :0.0 broken (explicit kill or server shutdown).
jim@ubuntu:~$

---

### Post by luckyaba on 2005-10-13
LMAO!!! 

thats awesome

---

### Post by luckyaba on 2005-10-13
when i tried that my computer completely froze up
----------
never mind that last post

---

### Post by Jmonti on 2005-10-13
You installed the drivers right? I don't think glx will run without them.

---

### Post by daniels on 2005-10-13
'glxgears -printfps' is preferred to -iacknowledgethatthistoolisnotabenchmark.

---

### Post by xthaparian on 2005-10-14
[QUOTE=Jmonti]He's not kidding. That worked for me! LOL

jim@ubuntu:~$ glxgears -iacknowledgethatthistoolisnotabenchmark
62991 frames in 5.0 seconds = 12598.124 FPS
65165 frames in 5.0 seconds = 13032.888 FPS
65251 frames in 5.0 seconds = 13050.129 FPS
65300 frames in 5.0 seconds = 13059.841 FPS
65287 frames in 5.0 seconds = 13057.360 FPS
65190 frames in 5.0 seconds = 13038.000 FPS
65249 frames in 5.0 seconds = 13049.674 FPS
64195 frames in 5.0 seconds = 12838.987 FPS
X connection to :0.0 broken (explicit kill or server shutdown).
jim@ubuntu:~$[/QUOTE]


How did you get the ATI driver working?

Can you please point me to the right direction. I am an AMD64 Bit Ubuntu 5.10 user.

Looks like you have 32 bit ubuntu on your system

---

### Post by funkenstein on 2005-10-26
looooool!!! that made me laugh!!!

Also happy to note that glxgears performance, while not being a benchmark has gone up by ~800-1000 frames since upgrading from hoary i386 to breezy 64 :O



WWWOOOOOOHHHHOOOOO!!!!! :D 

```

yme@ubertronMT30:~$ glxgears -iacknowledgethatthistoolisnotabenchmark
15052 frames in 5.0 seconds = 3010.282 FPS
15021 frames in 5.0 seconds = 3004.037 FPS
15052 frames in 5.0 seconds = 3010.393 FPS
15046 frames in 5.0 seconds = 3009.062 FPS
15057 frames in 5.0 seconds = 3011.287 FPS
19936 frames in 5.0 seconds = 3987.059 FPS
24250 frames in 5.0 seconds = 4849.885 FPS
24256 frames in 5.0 seconds = 4851.083 FPS

```

Ok, so maybe I cheated on the last few ones, but still not bad: 3000fps on a laptop??? :cool:

---

### Post by bughead on 2005-10-26
And for my X600XT, the bechmark is good ?

root@ubuntu:~# glxgears -printfps
7998 frames in 5.4 seconds = 1476.282 FPS
8438 frames in 5.0 seconds = 1687.436 FPS
8125 frames in 5.5 seconds = 1483.641 FPS
8231 frames in 5.0 seconds = 1646.174 FPS
root@ubuntu:~# fgl_glxgears
Using GLX_SGIX_pbuffer
2254 frames in 5.0 seconds = 450.800 FPS
2952 frames in 5.0 seconds = 590.400 FPS
2545 frames in 5.0 seconds = 509.000 FPS
2991 frames in 5.0 seconds = 598.200 FPS
root@ubuntu:~# fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X600/X550 Series Generic
OpenGL version string: 1.3.5395 (X4.3.0-8.18.6)
root@ubuntu:~#

There is a lot of diference with our friend's board ...
My drivers are not set ?!??!???!??? Or that numbers are normal for my board ??

---

### Post by metoo on 2005-10-26
It's not a benchmark ! :-)

However, 1500 is not the world.
My castrate AGP NVidia 6800 GT (SDRAM, not DDR2)
does about 10000 .

But then, it's not a benchmark.
Apparently the ATI linux OpenGL driver are pretty bad.
I have an ATI 9500 as well and it is about 100 fps if the OpenGL stuff is not working and about 1500 if it is working.
Lately this is the usual, which is already an improvement. But with that score...

So sorry, but UT2k4 could be a bit slow for you on Linux. :-)
Guess, why I bought a NVidia after the ATI?

---

### Post by funkenstein on 2005-10-27
lol, guess why I chose this laptop over any other one.... yeppo - it's the geforcego6200 ubermegasuperduperroxxorzhyperextrayerma'sawhale hyperram... or summat :P

anyway, can we close this thread now, methinks the ansa has bin givin.

---

### Post by Flandry on 2005-11-02
LOL I was wondering why i couldn't get any output from glxgears!  That's hilarious.

For this non-benchmark, i'm getting 2200 fps on my Radeon Mobility 9600;  but, it's not a benchmark!

---

### Post by carney1979 on 2007-04-25
I recently changed from an ati card to an Nvidia 7300 GT card.

I removed the ati dtivers and used Envy to install the Nvidia drivers.

glx programs all work as expected, glx screensavers work better than with the ati card.

However, glxgears gives me the following:

```
david@n1zhe:~$ glxgears -iacknowledgethatthistoolisnotabenchmark
Usage:
  -display <displayname>  set the display to run on
  -stereo                 run in stereo mode
  -fullscreen             run in fullscreen mode
  -info                   display OpenGL renderer info
david@n1zhe:~$ 
```

...or....

```
david@n1zhe:~$ glxgears
Usage:
  -display <displayname>  set the display to run on
  -stereo                 run in stereo mode
  -fullscreen             run in fullscreen mode
  -info                   display OpenGL renderer info
david@n1zhe:~$ 
```

I can't seem to get glxgears to work no matter what I try.

I'm running an i386 Feisty install recently upgraded from Edgy. I used Ubuntu's upgrade tool.

Everything glx except glxgears seems to be working far better than it was with the ati card. I'm not sure why I'm letting it bother me so much, but it does.

Dang!

Any ideas how I can get glxgears to work?

David

---

### Post by laidback on 2007-04-25
carney1979 have you tried:-

$glxgears -printfps

works for me. Like you I just don't like the idea of not having it work.

---

### Post by carney1979 on 2007-04-25
```
david@n1zhe:~$ glxgears -printfps
Usage:
  -display <displayname>  set the display to run on
  -stereo                 run in stereo mode
  -fullscreen             run in fullscreen mode
  -info                   display OpenGL renderer info
david@n1zhe:~$ 
```Guess not.

David

---

### Post by Tanker Bob on 2007-04-25
I had the same message about the usage.  Try 'glxgears -info'.  That worked for me.  You get a lot of info stuff first, including your card and driver ID, then the non-benchmark printout:

```

bob@kubuntu:~$ glxgears -info
GL_RENDERER   = GeForce 8800 GTS/PCI/SSE2
GL_VERSION    = 2.1.0 NVIDIA 97.55
GL_VENDOR     = NVIDIA Corporation
...lots of stuff...
129832 frames in 5.0 seconds = 25966.357 FPS
130572 frames in 5.0 seconds = 26114.314 FPS
130934 frames in 5.0 seconds = 26186.729 FPS
128768 frames in 5.0 seconds = 25753.562 FPS
130769 frames in 5.0 seconds = 26153.670 FPS
130830 frames in 5.0 seconds = 26165.943 FPS
130750 frames in 5.0 seconds = 26149.938 FPS
130814 frames in 5.0 seconds = 26162.660 FPS
130807 frames in 5.0 seconds = 26161.391 FPS
130563 frames in 5.0 seconds = 26112.465 FPS

```

Not sure why -info worked but -iacknowledgethatthistoolisnotabenchmark did not.

---

### Post by carney1979 on 2007-04-26
Thanks Tanker Bob.

Unfortunately that didn't work either......:(

David

---

### Post by codedmin on 2007-05-01
> **Tanker Bob said:**
> I had the same message about the usage.  Try 'glxgears -info'.  That worked for me.  You get a lot of info stuff first, including your card and driver ID, then the non-benchmark printout:

```

bob@kubuntu:~$ glxgears -info
GL_RENDERER   = GeForce 8800 GTS/PCI/SSE2
GL_VERSION    = 2.1.0 NVIDIA 97.55
GL_VENDOR     = NVIDIA Corporation
...lots of stuff...
129832 frames in 5.0 seconds = 25966.357 FPS
130572 frames in 5.0 seconds = 26114.314 FPS
130934 frames in 5.0 seconds = 26186.729 FPS
128768 frames in 5.0 seconds = 25753.562 FPS
130769 frames in 5.0 seconds = 26153.670 FPS
130830 frames in 5.0 seconds = 26165.943 FPS
130750 frames in 5.0 seconds = 26149.938 FPS
130814 frames in 5.0 seconds = 26162.660 FPS
130807 frames in 5.0 seconds = 26161.391 FPS
130563 frames in 5.0 seconds = 26112.465 FPS

```

Not sure why -info worked but -iacknowledgethatthistoolisnotabenchmark did not.

I there, i have same chipset, bfg 8800gts but i have problems, look
```
dserra@ubuntu:~$ glxgears -info
GL_RENDERER   = GeForce 8800 GTS/PCI/SSE2
GL_VERSION    = 2.1.0 NVIDIA 97.55
GL_VENDOR     = NVIDIA Corporation
....42735 frames in 5.0 seconds = 8546.903 FPS
42617 frames in 5.0 seconds = 8523.235 FPS
43098 frames in 5.0 seconds = 8619.431 FPS

```
I have 2gb ram and my CPU is one e6600

My beryl effects are very slow, anyone know why ia have so low frames ???

Thanks

---

### Post by Tanker Bob on 2007-05-01
> **codedmin said:**
> I there, i have same chipset, bfg 8800gts but i have problems, look
```
dserra@ubuntu:~$ glxgears -info
GL_RENDERER   = GeForce 8800 GTS/PCI/SSE2
GL_VERSION    = 2.1.0 NVIDIA 97.55
GL_VENDOR     = NVIDIA Corporation
....42735 frames in 5.0 seconds = 8546.903 FPS
42617 frames in 5.0 seconds = 8523.235 FPS
43098 frames in 5.0 seconds = 8619.431 FPS

```
I have 2gb ram and my CPU is one e6600

My beryl effects are very slow, anyone know why ia have so low frames ???

Thanks
Well, the numbers I posted were without Beryl running.  With Beryl running, I'm only getting about 16,200 fps.  The biggest effect on the 3D performance is how Beryl's advance options are set.  What settings in the Beryl Advanced settings from the system tray pop-up menu are you using?  To avoid the black window bug, I have Force AIGLX set with XGL Binding.  This gives the the 16,200 fps performance.  With all settings at Auto, I get around 16,800 fps, so the hit is very small.  You might give these settings a try.  Even with the worst settings I've used, though, I've not dropped below 13,000 fps or so that I can recall.

My e6600 is overclocked to 2.94 GHz vice the standard 2.4 GHz, but that wouldn't affect the frame rates significantly.  How much memory do you have on your 8800 GTS card?  Who made the card?

Actually, I just recalled a "problem" that I had when I first set Beryl up but haven't seen in a week or so.  Both Beryl's benchmark plug-in and glxgears would show 75 fps, but the screen ran the same as when these measures read 16,000 fps.  Soon after that happened, there would start to be screen errors in painting which I fixed by restarting X (ctlr-alt-backspace).  Everything would be fine after that.  Even during that situation, the screen never seemed slow like you describe.

---

### Post by codedmin on 2007-05-04
I will try with that settings.

This is my hardware:
E6600 @ 3.600mhz
BFG 8800gts 320mb
2GB ddr2
2x80gb hitachi (raid0)
I have ubuntu 7.04 32bits (i386) should i do install 64bits? will be better?


With beryl in auto i have this glxgears
```
29373 frames in 5.0 seconds = 5874.533 FPS
21002 frames in 5.0 seconds = 4200.219 FPS
24310 frames in 5.0 seconds = 4861.999 FPS

```

With beryl and the settings you said i have this glxgears
```
36616 frames in 5.0 seconds = 7323.187 FPS
35820 frames in 5.0 seconds = 7163.940 FPS
35332 frames in 5.0 seconds = 7066.242 FPS

```

I do some benchmarks with globs, see attachments please

---

### Post by executor on 2007-05-04
get this :)

HP dv5011 laptop 200m chip set 3000+ sempron

andreas@linuxpower:~$ glxgears -info
GL_RENDERER   = RADEON XPRESS Series
GL_VERSION    = 2.0.6334 (8.34.8)
GL_VENDOR     = ATI Technologies Inc.

3997 frames in 5.0 seconds = 799.365 FPS
3997 frames in 5.0 seconds = 799.357 FPS
3998 frames in 5.0 seconds = 799.553 FPS
3995 frames in 5.0 seconds = 798.827 FPS
andreas@linuxpower:~$

---

### Post by Tanker Bob on 2007-05-04
> **codedmin said:**
> I will try with that settings.

This is my hardware:
E6600 @ 3.600mhz
BFG 8800gts 320mb
2GB ddr2
2x80gb hitachi (raid0)
I have ubuntu 7.04 32bits (i386) should i do install 64bits? will be better?
That's a pretty major overclock.  How fast is the memory bus running?  What motherboard do you have?  64-bit will run faster on your PC, but it really shouldn't affect the video as dramatically as your tests show.  I initially had 32-bit Edgy on my system before Feisty was released, and the video performance was comparable.  Neither do I think that the amount of video RAM would make that kind of difference.

> With beryl in auto i have this glxgears
```
29373 frames in 5.0 seconds = 5874.533 FPS
21002 frames in 5.0 seconds = 4200.219 FPS
24310 frames in 5.0 seconds = 4861.999 FPS

```

With beryl and the settings you said i have this glxgears
```
36616 frames in 5.0 seconds = 7323.187 FPS
35820 frames in 5.0 seconds = 7163.940 FPS
35332 frames in 5.0 seconds = 7066.242 FPS

```

I do some benchmarks with globs, see attachments please
Hmmm.  I don't know anything about globs, but that looks way low for glxgears.  Seems to me that this has to be some sort of setting issue or else the card itself has an issue.  I'll cut and paste my xorg.conf in another post.

---

### Post by Tanker Bob on 2007-05-04
codedmin:

Here's my xorg.conf:
```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 85.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option "TripleBuffer" "True"
    Option "BackingStore" "True"
    Option "DisableGLXRootClipping" "False"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1152x865" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1152x865" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1152x865" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1152x865" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1152x865" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
    Option         "RENDER" "Enable"
EndSection
```
I added some stuff last night based on [this thread](http://www.nvnews.net/vbulletin/showthread.php?t=84562&page=9) starting at post #135.  This all works very well.

---

### Post by codedmin on 2007-05-04
> **Tanker Bob said:**
> That's a pretty major overclock.  How fast is the memory bus running?  What motherboard do you have?  64-bit will run faster on your PC, but it really shouldn't affect the video as dramatically as your tests show.  I initially had 32-bit Edgy on my system before Feisty was released, and the video performance was comparable.  Neither do I think that the amount of video RAM would make that kind of difference.


CPU is run @ 3.600Mhz ->8x450 
ddr2 run @ 900mhz ->4-4-3-5
On Asus P5b- Plus vista edition
I have another issue i can't solve, can't view cpu temperature, and the cpu in ubuntu report 4.000 Mhz i think is acpi problem but can't find any solution

With 64bits you don't have problem with apps, like flash player etc ???

> **Tanker Bob said:**
> Hmmm.  I don't know anything about globs, but that looks way low for glxgears.  Seems to me that this has to be some sort of setting issue or else the card itself has an issue.  I'll cut and paste my xorg.conf in another post.

Globs is as benchmark app, i read in some post that glxgears isn't completely true, don't know, and i don't have nome other globs to see the differences

Thanks

---

### Post by codedmin on 2007-05-04
> **Tanker Bob said:**
> codedmin:

Here's my xorg.conf:
```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 85.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option "TripleBuffer" "True"
    Option "BackingStore" "True"
    Option "DisableGLXRootClipping" "False"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1152x865" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1152x865" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1152x865" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1152x865" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1152x865" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
    Option         "RENDER" "Enable"
EndSection
```
I added some stuff last night based on [this thread](http://www.nvnews.net/vbulletin/showthread.php?t=84562&page=9) starting at post #135.  This all works very well.

I try but my results don't change, i will stay with you conf. 
Thanks again :D

PS: With this settings and beryl settings of other post my beryl is better and withou black screens ;)

---

### Post by Tanker Bob on 2007-05-04
> **codedmin said:**
> I try but my results don't change, i will stay with you conf. 
Thanks again :D
You're welcome.  I'm stumped as to what else to suggest.  I'm pretty new at this myself.

---

### Post by Tanker Bob on 2007-05-05
> **codedmin said:**
> CPU is run @ 3.600Mhz ->8x450 
ddr2 run @ 900mhz ->4-4-3-5
On Asus P5b- Plus vista edition
What CPU, FSB, and bridge voltages are you using?  I'm able to get to 3.168 with 9x, but can't seem to boot to 3.394 at x8. Thanks!

---

### Post by nss0000 on 2007-05-06
Gents:

A few <glxgears> numbers:

sys#1: ASUS-m2n/AMD5400+/NV7600gs/2.0gig : Dapperx64

50106 frames in 5.0 seconds = 10021.144 FPS
50086 frames in 5.0 seconds = 10017.012 FPS
49825 frames in 5.0 seconds = 9964.930 FPS
49058 frames in 5.0 seconds = 9811.600 FPS
49576 frames in 5.0 seconds = 9915.020 FPS
50109 frames in 5.0 seconds = 10021.664 FPS

sys#2: GB_7vt600 / AMD2600+/NV5200/1.0gig :  Dapperx32

  ~1500-1600 FPS

Big difference, even tho the AMD5400 numbers are no-great-shakes. OTOH for matrix-mult / display-intensive tasks on geoanalytic GRASS, the x64 system just zips. 

nss
******

---

### Post by RawMustard on 2007-05-07
> **Tanker Bob said:**
> codedmin:
I added some stuff last night based on [this thread](http://www.nvnews.net/vbulletin/showthread.php?t=84562&page=9) starting at post #135.  This all works very well.

```

Section "Extensions"
    Option         "Composite" "Enable"
    Option         "RENDER" "Enable"
EndSection

```

Should be

```

Section "Extensions"
    Option         "Composite"     "true"
EndSection

```

And Option "RenderAccel" "true"

Should be in your screen section or your device section.
I've never seen Option "RENDER" before?

---

### Post by Tanker Bob on 2007-05-07
> **RawMustard said:**
> 
```

Section "Extensions"
    Option         "Composite"     "true"
EndSection

```

And Option "RenderAccel" "true"

Should be in your screen section or your device section.
I've never seen Option "RENDER" before?
It should be:
```

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```
According to NVIDIA tech support's post [here](http://www.nvnews.net/vbulletin/showthread.php?t=77030).  I'll check on the RENDER option when I have more time.  It was suggested by another user.

---

### Post by RawMustard on 2007-05-07
Yep you're right, it's an xorg extension and is written like you have.  Sorry my bad I'll take my foot out of my mouth now :(  There's a lot of people have it set to true, I wonder if it makes a difference?

Oh and the render bit isn't needed, it's been enabled in xorg by default for ages and is what's responsible for antialiased fonts amongst other things.

---

### Post by Tanker Bob on 2007-05-07
> **RawMustard said:**
> Oh and the render bit isn't needed, it's been enabled in xorg by default for ages and is what's responsible for antialiased fonts amongst other things.
That's what my quick research is discovering.  Thanks for pointing that out.

---

### Post by codedmin on 2007-05-09
> **Tanker Bob said:**
> What CPU, FSB, and bridge voltages are you using?  I'm able to get to 3.168 with 9x, but can't seem to boot to 3.394 at x8. Thanks!

Sorry dude, only see it now, i will be back later and edit this post with my settings


Here dude:

CPU       - 1.525V  (this is kind of a lot for 24h day, but my temps are low, i have a TUNIQ COOLER ;) )
FSB       - 1.2V
MEM      - 2.05V
NVCore - 1.25V
SBCore - 1.50V
ICH        - 1.057V

Some of them are in lowest value, i prefer don't have none of them in auto



Cheers

---

### Post by jhorto1 on 2008-05-08
Mine works if I do:

glxgears -info

but otherwise nothing. Just what exactly is it asking for with -displayname?

I don't know if it wants my driver name or monitor name or what?
Can't it just figure it out by itself. I only have one display.

I'd like to get it to use the -printfps option, but if I add that to the glxgears -info command, it doesn't do anything except print out the options again.

---

