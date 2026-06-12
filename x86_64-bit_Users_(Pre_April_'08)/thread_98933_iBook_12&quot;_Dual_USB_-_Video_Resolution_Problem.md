---
title: "iBook 12&quot; Dual USB - Video Resolution Problems"
date: 2005-12-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by echolades on 2005-12-04
Hello,
 - Alright, Linux newbie for sure... I did search and all that, but couldn't find anything somewhat close to what I'm experiencing, and if there is a thread out there already, sorry in advance.

 - Computer Specs... Apple Ibook G3 / 700mhz / 640mb ram / 60gb hd
 - Video Card (as stated in device manager) : ATI Radeon Mobility M6 LY : 

 - After first loading SuSE and having NO luck with video, then loading Mandriva and having perfect luck with video, but hating the overall system, so far, ubuntu has been the easiest to load, install apps, and generally learn on, except that now, the video seems to be stuck and set at 640 x 480 @ 60hz. I know the video works @ 1024 x 768 @ 24mil colors, that's what it was after tinkering in Mandriva (just trying settings that work). In ubuntu, I can't even select any different settings. 

 - Now, I've read some things about "xorg.conf" ? Like I said though, newbie... so, if anyone has ideas/suggestions/known fixes, ANY advice, I'd appreciate it.

Thanks so much in advance.
- Dave

---

### Post by ssam on 2005-12-04
can you try running
```
sudo dpkg-reconfigure xserver-xorg
```
in a terminal, and answering the questions.

somehow that sometimes does a better jobs than the installer.

---

### Post by echolades on 2005-12-04
Yeah, actually, in the last 10 minutes that's what I've been playing with (re: actually found that in another thread for a g4 tibook).

It hasnt' corrected anything, I did try editing the "monitor" settings in xorg.conf and killed xserver, as i type, i'm in terminal trying to undo what I did (however, I'm not so good at this command-line stuff).

This is what it was, and what I edited to, I know what I forgot, just don't know what to put in it's place...

> 
Section "Monitor"
        Identifier      "Color LCD"
        HorizSync       28-51
        VertRefresh     43-60
        Option          "DPMS"
        Option          "DDCMode"               "boolean"
        Modeline        "1024x768"              
EndSection


I guess after "Modeline" there should be some settings there, I honestly have no idea what those settings are, nor what they should be.

Any advice? (As well as any command line sude -e advice? It didn't seem to want to open /etc/x11/xorg.conf)

Thanks

---

### Post by echolades on 2005-12-04
::SIGH OF RELIEF::!!

Okay, running that util again seems to have filled in the the values I missed for me.

Thanks for the direction though, at least it let me know I was running in the right direction. Not knowing how the whole "bug" process works, would this be something to bring to the attention of developers? Or is this just a mis-step on my part?

---

### Post by ssam on 2005-12-04
i would say that the installer not correctly configuring your graphics card is a bug. filing it is a good way to get the devs to notice it.

at the moment it is recommended that you file the bug at [http://bugzilla.ubuntu.com/](http://bugzilla.ubuntu.com/) .

there is a slight art to writing a bug report. a good bug report can result in a fix being made in hours (this has happened once for me :-), though the fix has not filtered down into ubuntu yet :-( ). most bug reports dont contain enough information for the developers to fix it the problem, and get left with a NEEDINFO label.

so you need to give as much relevent information as possible, and be ready to answer any further questions.

use a title like "installer does not correctly configure xorg for ATI Radeon Mobility M6 LY"

in the description explain that the resolution is wrong. give details about your computer.

say that running
```
sudo dpkg-reconfigure xserver-xorg
```
does not help.

you will probably get asked for more information. the developers may assume that you are familiar with debugging linux, so if you dont understand what they ask then you can ask here.

they may suggest away for you to get it working. it is too late for them to fix this for breezy, but it may get fixed for dapper (there is lots of new xorg stuff going on in dapper, so fingers crossed).

if you find the trick to configuring the card properly add that into you bug report.

---

