---
title: "Display resolutions?"
date: 2005-04-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by mach_zero on 2005-04-12
Bear with me, I am so new I squeak. I just did a successful install of Kubuntu and everything is peachy so far with one exception. When I go into Control Center to try and adjust display resolutions the highest option it gives me is 1024 x 768. I have a 17" LCD and the native res is 1280 x 1024. Right now everything is so big I have to sit back a foor further from the screen. Any way I can change this? Thanks in advance for your time!

---

### Post by penvzila on 2005-04-12
There's a section of xorg.conf that you can add your resolution to.  I am curious why it didn't get autodetected, thought, since it did on my laptop and my native res is 1600x1200.

---

### Post by heimo on 2005-04-12
Hi!

What you probably need to do is check couple things from your /etc/X11/xorg.conf file.

This is how to do it: 

Applications->System Tools->Terminal

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo gedit /etc/X11/xorg.conf
``` 
(filesystem is case sensitive, so X need to be uppercase, all the other lower case)

Find *Section "Monitor"*. You may have uncommented (lines beginning with #) there, the interesting lines are: 
```

HorizSync	31-101
VertRefresh	50-160

```

Those lines tell what your monitor is cabable of. You should be able to find these numbers from manual of your monitor or manufacturers website. If you give exact model, I can try to do it for you. VertRefresh should probably be around 50-85 and your HorizSync upper limit could be the cause for not showing 1280x1024.

Scroll down to *Section "Screen"*
You only need one Subsection, the one which matches DefaultDepth, which is probably set to 24? You should probably have Subsection like this:

```
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768"
	EndSubSection

```
Here's the list of resolutions you want to use. Even if the resolution is listed here, doesn't mean that it's listed in System->Preferences->Screen resolution, because only the screen modes that are compatible (or more specifically thought to be compatible / detected are shown and used). EDIT: **Keep the 1024x768 there, but add 1280x1024, if it's missing.** 

After changes, save the file, close all the programs you're running and hit CTRL+ALT+BACKSPACE to kill your graphical user interface (Gnome+Xorg). This will restart just the X window system, you don't need to restart your computer. However, if you made syntax error or the new changes are incompatible, you'll probably get just the console (command prompt).

In that case, login and do
```

sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
sudo /etc/init.d/gdm restart

```

And... then we'll get back to this. :) Unless everything works fine and you got 1280x1024. :) When in X you can hit CTRL+ALT+ + (control-alt-plussign) to switch modes.

---

### Post by Manfire on 2005-04-12
In the same line of questions, I'm able to get the resolution I want, but I can't display any other refresh rates than 60hz when i'm at 1280x1024 or even 1152x864 (my monitor is capable of at least 75hz at 1152) 

Will changing the Horiz/Vert sync settings of my monitor in xorg.conf fix my problem you think?

---

### Post by heimo on 2005-04-12
[QUOTE=Manfire]In the same line of questions, I'm able to get the resolution I want, but I can't display any other refresh rates than 60hz when i'm at 1280x1024 or even 1152x864 (my monitor is capable of at least 75hz at 1152) 

Will changing the Horiz/Vert sync settings of my monitor in xorg.conf fix my problem you think?[/QUOTE]

Most probably. If you can find those numbers in monitors spesification (manual / manufacturers website), that's good. You can also try running
```
sudo xresprobe [your video driver]
for example: sudo xresprobe nvidia
```

Or you can just guess... But if it's TFT it probably doesn't make much difference between 60Hz and 75Hz?

---

### Post by mach_zero on 2005-04-12
OK, will try the new settings in the xorg.conf file. I was very late when I posted last night and something else occurred to me when I woke up this morning. I didn't install the AMD64 Nvidia drivers for my graphics card, either. Would this have made a difference?

Edit: Okay, I'm not sure it would have because the install instructions for the Forceware drivers state that you have to do some manual tweaking to xorg.conf after the fact anyway. I find this particularly frustrating because I was using the PPC versions of Ubuntu (Warty Warthog) and Debian prior to this and it always correctly set my display resolutions during set up, and that was with an ATI card which (so I have heard) is more problematic. Well, I will get back to playing around and let you know if I succeed or fail. Then on to the next problem - installing cdrdao. But that's a subject for a different thread................

Thanks for all the replies!  :)

---

### Post by c_dog on 2005-04-12
You can go to this page and enter any resolution and refresh rate you want and it will generate the modeline for xorg or XFree for whatever monitor you have as long as you know it's specs. 

[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)


Keep in mind the the highest resolution at the highest rate your monitor can display is not always the best because almost all monitors interlace at their high frequencies and resolutions. This way montiors like say.. LCDs are listed with an optimal resolution and refresh rate. Even though the specs say it can go higher and faster.

---

### Post by heimo on 2005-04-12
You can also create modelines with gtf. For example, If I want a mode with 1280x1024@75Hz, I just enter ```
gtf 1280 1024 75
``` and get outpiut:
```
 
  # 1280x1024 @ 75.00 Hz (GTF) hsync: 80.17 kHz; pclk: 138.54 MHz
  Modeline "1280x1024_75.00"  138.54  1280 1368 1504 1728  1024 1025 1028 1069  -HSync +Vsync

```
Now I can copy-paste it into Monitor section of xorg.conf. Of course the hsync of this new modeline (80.17) must be in range of my monitor to work (HorizSync line).

---

