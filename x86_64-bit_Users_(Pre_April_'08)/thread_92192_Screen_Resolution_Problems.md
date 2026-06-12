---
title: "Screen Resolution Problems"
date: 2005-11-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by ritual on 2005-11-18
I am running the amd64 version of Ubuntu but I am having problems with my screen resolution. I have an ATi x800pro and a Samsung 712N monitor but I can only view at 640x480, 800x600, and 1024x768. Why is this? Do I need video drivers in order to enable higher resolutions? I didn't think I did because a buddy of mine is running at a higher resolution without installing any drivers, though he isn't on an amd64 chip.

I looked into the ATi drivers with amd64 support and I found something but it says they are experimental only. If there are drivers available and I do need them, could someone point me in the right direction?

Thanks for the help.

---

### Post by nikodell on 2005-11-19
look at refresh rates in xorg.conf + set them to monitor specs i had this problem and it was corrected with this.

vi /etc/X11/xorg.conf

look for this section


Section "Monitor"
    Identifier "monitor1"
    VendorName "NEC"
    ModelName "1280x1024 @ 76 Hz"
    HorizSync 31.5-82
    VertRefresh 50-90

---

### Post by ritual on 2005-11-19
I've found what you told me but I have something different here:

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60


Should I add in:

 ModelName "1280x1024 @ 76 Hz"

?

---

### Post by rplantz on 2005-11-19
[QUOTE=ritual]I've found what you told me but I have something different here:

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60


Should I add in:

 ModelName "1280x1024 @ 76 Hz"

?[/QUOTE]

No, the important things here are HorizSync and VertRefresh. Your file has the default settings. You need to look at the manual for your monitor at use the numbers there. For example, my manual says
```

Horizontal Synchronization   30 - 95 KHz
Vertical Synchronization 50 - 160 Hz

```
so I use
```

        HorizSync       30-95
        VertRefresh     50-160

```

My monitor manual also specifies resolutions, so I have things like:
```

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV34 [GeForce FX 5200]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
 etc...

```

Actually, this part of the file was filled in when I installed the system, but I had to change the horizontal and vertical rates with an editor.

Bob

---

### Post by nikodell on 2005-11-19
[COLOR="DarkOrange"][SIZE="6"]Did you get it?[/SIZE][/COLOR]

---

### Post by ritual on 2005-11-19
No not yet, I don't have the manual to my monitor anymore so I'm searching for the specifications now. But, I did look at my xorg.conf and there are only the three dimensions I listed.

EDIT:

I found this info on Samsung's website:

Frequency  	   	Horiz. Rate (kHz)  	   	30-81 (Analog)
  	  	Vert. Rate (Hz) 	  	56-75
  	  	Bandwidth (Mhz) 	  	135

If you look at my second post that isn't what my conf reads so should I edit this?

---

### Post by joris.brus on 2005-11-20
This won't be too usefull, but I had the same problem.
During the installation of Ubuntu it asks you which resolutions to use. hit spacebar on all the ones you want to be able to use. 
That worked for me, but I had to do a reinstall anyway.

---

### Post by etitor on 2005-11-20
Sometimes just changing "DefaultDepth    24" to "DefaultDepth    16" in xorg.conf will give you more options as to height and width (although it will take away some colors). It's an easy trade-off.

---

### Post by BoyOfDestiny on 2005-11-20
[QUOTE=joris.brus]This won't be too usefull, but I had the same problem.
During the installation of Ubuntu it asks you which resolutions to use. hit spacebar on all the ones you want to be able to use. 
That worked for me, but I had to do a reinstall anyway.[/QUOTE]

You don't have to reinstall. Just type sudo dpkg-reconfigure xserver-xorg and choose the res's you want. Fixing up the horizontal and vertical sync is for refresh rate (with the default, I was running at 1600 x 1200 with 60hz...not pretty)

EDIT: I'll mention it since it's not that intuitive. When it asks you what res to use, use space bar to select (as you choose with up and down arrows) then hit tab (once or twice) to navigate to yes or ok, then hit enter. 

Best of luck to you.

---

### Post by bonzodog on 2005-11-20
Your monitors default res should be 1280 x 1024 @24bpp @ 60Hz. I have the Samsung 710v TFT, which is it's cousin. Your ATI x800 card should crunch hi speed 3d like it doesn't exist - however I believe that the ATI card doesn't like the default non-accelerated drivers from xorg. The default driver will either be "ati" or "vesa". I got this system with an ATI Radeon 9800 pro, and removed it and bought an Nvidia GeForce 6200 just so it would play nicely with Linux. X really didn't play nicely with the ATI. This was with Slackware.

---

### Post by Aphorism on 2005-11-20
[QUOTE=ritual]No not yet, I don't have the manual to my monitor anymore so I'm searching for the specifications now. But, I did look at my xorg.conf and there are only the three dimensions I listed.

EDIT:

I found this info on Samsung's website:

Frequency  	   	Horiz. Rate (kHz)  	   	30-81 (Analog)
  	  	Vert. Rate (Hz) 	  	56-75
  	  	Bandwidth (Mhz) 	  	135

If you look at my second post that isn't what my conf reads so should I edit this?[/QUOTE]

YES.  Change the horizontal and vertical rates to those of your monitor.  Then adjust your "Screen" variable to add in the line 1280x1024 for your bit depths.

To recap:

[list=1]
[1]Adjust your horizontal and vertical refresh rates.
[2]Adjust your screen section.
[/list]

Here is my section.  YOUR'S will be different.  Use the following as a reference only...
```

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       31-81
        VertRefresh     56-76
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NVIDIA Default Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

```
Sincerely hope this helps...

---

### Post by ritual on 2005-11-20
Thanks for everyones help. I read the ATi driver tutorial on these forums and figured out what I was doing wrong. Now I feel stupid :D Thanks again everyone.

---

### Post by SOAD on 2005-11-21
now can you teach me doing de same?

---

### Post by AzureCerulean on 2005-12-05
Here is Every "Standard" MODE.

if you replace yours with this and have the correct H and V rates  +/- 1

you should then display the BEST resolution your card and monitor can support.

Modes "7680×4800" "6400×4800" "6400×4096" "5120×4096" "3840×2400" "3200×2400" "3200×2048" "2560×2048" "2560×1600" "2048×1536" "1920x1080"  "1920×1200" "1600×1200" "1680×1050" "1600×1024" "1400×1050" "1440×900" "1280×1024" "1280×768" "1280x720" "1152×864" "1024×768" "852x480"  "800×600" "750x540"  "720x576"  "720x486"  "720×480"  "720×360" "720×350" "720×348" "704x480"  "640×480" "640×350" "560×360"  "512×384" "352×288"  "352×240"  "320×240" "320×200"

if you want a mode that is not listed google for ModeLine generator. Then add the modeline and the resolution to you .conf

NOTE: i know that most of the modes are NOT obtainable.

---

