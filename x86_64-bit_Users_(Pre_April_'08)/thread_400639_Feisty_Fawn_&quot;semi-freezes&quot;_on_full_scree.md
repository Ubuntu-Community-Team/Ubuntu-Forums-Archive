---
title: "Feisty Fawn &quot;semi-freezes&quot; on full screen redraw (screensaver)"
date: 2007-04-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Zorael on 2007-04-03
Greetings, Ubuntu x64 community!


I decided to try out Ubuntu a week ago or so, and I really started from scratch, having had no prior experience neither with Ubuntu nor with Linux in general. The following two days, during which an epic battle with dmraid took place, are an experience I won't soon forget. It will haunt me to the end of my days.

Consequently "un-fakeraiding" my two harddrives, I installed the x64 version of Feisty Fawn. I guess I probably shouldn't have picked the beta version. I know, I'm weak.

Since then, I've probably reinstalled about four times, as I always ended up with a *very* unstable system. Sometimes it would just freeze whenever I'm doing "normal" stuff (Firefox, word processing, the ilk), sometimes it wouldn't load X, sometimes it just froze when rebooting or shutting down. Lesson learned: don't install too much.

Anyway, my current install is functioning fairly good; no random freezes... only reproducible ones. If the screen needs to be "fully redrawn", at lack of better wording, it semi-freezes. It's not a complete freeze; I *can* move the cursor around, but it doesn't respond to any key presses (I've tried them all, including CTRL+ALT+Backspace). So I have to do a cold reboot - which, on my laptop, translates to forcing a shutdown by holding down the power button for ~4 seconds.

Cancelling a screensaver reproduces this for me; meaning, when it's supposed to redraw all the bars, all the windows, etc. Also, trying to ALT-F7 back from terminals outside X, when it's basically returning from, uh, mode co80. *hides*

Mind, the screensavers themselves *work*; the OpenGL itself doesn't fail, I just can't reclaim control of the computer when I cancel them. :)


So, video card drivers. Thus far I've tried:
- the ones that come preinstalled after running the (Ubiquity?) installer on the Feisty Fawn x64 beta disc
- the ones that I can download through Add/Remove
- the ones available from NVIDIA's site (1.0-9755)
- the vesa one. Yuck!

OpenGL works on all except the vesa one, so I can spin my lovely Beryl cube to my heart's content. Whee! Currently I'm using the one from NVIDIA's site, which is listed to support my video card. I'm also not sure if this happens after returning from DPMI monitor "blanks", but I can try that (after posting this so I don't have to rewrite it, heh.)


Anyway, I'd really appreciate any help or hints you could give me. I really have only hunches about what information I might supply to make things smooth, so bear with me if most of it is irrelevant. :)

```
azrael@azrael:/$ uname -rm
2.6.20-13-generic x86_64

azrael@azrael:/$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz
stepping        : 6
cpu MHz         : 1000.000
cache size      : 4096 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 3996.98
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz
stepping        : 6
cpu MHz         : 1000.000
cache size      : 4096 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 3990.06
clflush size    : 64
cache_alignment : 64
address sizes   : 36 bits physical, 48 bits virtual
power management:

azrael@azrael:/$ lspci | grep -i nvidia
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)

azrael@azrael:/$ dmesg | grep -i nvidia
[   56.590568] nvidia: module license 'NVIDIA' taints kernel.
[   56.846388] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  1.0-9755  Mon Feb 26 23:16:31 PST 2007

azrael@azrael:/$ glxinfo | grep -i nvidia
server glx vendor string: NVIDIA Corporation
client glx vendor string: NVIDIA Corporation
OpenGL vendor string: NVIDIA Corporation
OpenGL version string: 2.1.0 NVIDIA 97.55

azrael@azrael:/$ sudo gedit /etc/X11/xorg.conf
...
Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
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
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "False"
    Option         "AllowGLXWithComposite" "True"
    Option         "RenderAccel" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "UseFBDev" "true"
    Option         "VideoOverlay" "on"
    Option         "OpenGLOverlay" "on"
    SubSection     "Display"
        Depth       1
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
...

```

The extra xorg.conf Display lines were from a wiki saying it would provide a sizable boost to World of Warcraft under Wine, and when I tried removing some, X wouldn't load. I'll toy with that some more, I guess.

The computer is an Acer Aspire 9815, with a Core 2 Duo processor at 2GHz, and 2Gb ram. The video card is an NVIDIA GeForce Go 7600 PCI Express thingie.


Can anyone out there shed some light on this semi-freezing mystery of mine? Perhaps a kindred soul with a similar ailment? :)

My thanks in advance.

---

### Post by Kilz on 2007-04-03
Feisty Fawn is under development.[ As such it has its own section of the forum]("http://ubuntuforums.org/forumdisplay.php?f=179"). It also isnt recommended for use as a desktop for every day use. It should only be used to check for bugs, to be reported on launchpad, and its own section of the forum. You might want to post this there.

---

