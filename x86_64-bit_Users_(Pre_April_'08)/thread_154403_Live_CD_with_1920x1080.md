---
title: "Live CD with 1920x1080?"
date: 2006-04-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by hotani on 2006-04-03
I'm trying to use the PPC live CD but my monitor resolution is not listed as an option. Any way to enable it? 

I am able to boot up, but everything looks like arse.

I'm running a dual G4 867, GeForce Ti 128 GPU.

---

### Post by Jason_25 on 2006-04-03
```

gksudo gedit /etc/X11/xorg.conf

```
You will need to add a custom modeline in the monitor section of the xorg file for 1080p.  Here is a huge list of them. 
 [http://www.mythtv.org/wiki/index.php/Modeline_Database](http://www.mythtv.org/wiki/index.php/Modeline_Database)
For instance, for 720p on my direct view CRT HDTV I use this line

ModeLine     "1280x720" 74.160 1280 1352 1392 1648 720 725 730 750 -hsync -vsync


Once you've edited the file, log out, and ctrl-alt-backspace to restart GDM.  BTW, don't use this technique on an ubuntu install, just the live cd.

---

### Post by hotani on 2006-04-03
great - thanks for the quick response.

I don't see my model (Westinghouse LVM-37W1 1080p) on the list, but am wondering if I can use a straight copy or modified version of this one:

> ## Samsung HL-R5678W DLP (in 1920x1080p [over VGA input]), all resolutions without -XX are 60Hz
## The 1920x1080 (@60Hz) Modeline is confirmed working for the Samsung HL-R5078W in same manner as above
## 
# Modeline        "1920x1080" 138.407 1920 1984 2016 2096 1080 1082 1087 1111 +hsync -vsync

---

### Post by Jason_25 on 2006-04-03
Definitely try it and see.  You can't damage an LCD by driving it incorrectly.

---

### Post by hotani on 2006-04-04
I was finally able to get something up that was workable:
[img]http://static.flickr.com/39/123033260_c85dba732c_b.jpg[/img]

It actually had a small bar on the left that was showing about 10px of what was extending off the right side, but for the most part it was functional. The screenshot looks normal, that issue was only when viewed through the monitor.

I ended up following some tips on [this page](http://www.ubuntuforums.org/showthread.php?t=83973) and ended up with something like this:

added to *Monitor* section:
```

# V-freq: 60.00 Hz  // h-freq: 67.22 KHz
Modeline "1920x1080" 176.92  1920 2008 2224 2632  1080 1080 1083 1120 

```

changed *Screen* section (**bold** is the part I added):
```

DefaultDepth    24
    SubSection "Display":
        Depth        24
        Modes      **"1920x1080"** "1280x1024" "1024x768"
    EndSubSection

```

I think I might be finished messing with it on the G4 (current main system),  but will continue to test on my PC laptop (from work) until I get the amd64 system (main system in the near future) up and running. How's that for trying all possible varieties? :-D

---

### Post by Jason_25 on 2006-04-04
Really glad you could get it to work.

---

### Post by hotani on 2006-04-23
I've messed with this some more and am stuck with the 10px wide vertical bar on the left side of the screen. It is a piece from the right side of the screen that is chopped off then redisplayed about 10px in on the left side.

Here is a screenshot that shows what i'm talking about:
[img]http://static.flickr.com/55/133146129_8f061482b5_o.jpg[/img]

I've tried a bunch of different configurations, here is what I'm using currently:

```

Section "Monitor"
        Identifier      "LVM-37w1"
        Option          "DPMS"
        HorizSync       30-80
        VertRefresh     50-75

	# V-freq: 59.00 Hz  // h-freq: 66.06 KHz
	Modeline "1920x1080" 172.81  1920 2008 2216 2616  1080 1080 1082 1119 
EndSection

Section "Screen"

        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV25 [GeForce4 Ti 4600]"
        Monitor         "LVM-37w1"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1920x1080" "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1920x1080" "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1920x1080" "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1920x1080" "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1920x1080" "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1920x1080" "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

```

I want to switch over and use this for my home machine but can't do it until i at least know the resolution problem can be fixed. After that i have to get my sound working, but that's another task.

---

