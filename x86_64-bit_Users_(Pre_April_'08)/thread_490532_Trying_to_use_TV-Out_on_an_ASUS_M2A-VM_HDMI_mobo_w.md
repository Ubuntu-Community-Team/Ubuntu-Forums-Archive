---
title: "Trying to use TV-Out on an ASUS M2A-VM HDMI mobo w/ onboard video"
date: 2007-07-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by ebbomega on 2007-07-02
First post for me for the ubuntu forums.

I've tried looking around and most places I'm finding with information on this (including here) have turned up questions with no answers.

Basically, I'm running a M2A-VM HDMI board that has an add-on card with TV-out, SVHS out and HDMI out.

Here's the thing... I only have a television with tv-input on it, so I want to get the board to start outputting through it.

I am currently using the fglrx (ati proprietary) module for my graphics. The onboard card is an ATI Radeon X1250

lsmod shows:
```
fglrx                 623096  11 
```

/etc/X11/xorg.conf shows the following for Monitor, Device and Screen:

```

Section "Monitor"
        Identifier   "AccuSync 95F"
        Option      "DPMS"
EndSection

Section "Device"
        Identifier  "Generic Video Card"
        Driver      "fglrx"
        Option      "DesktopSetup" "clone"
        Option      "ForceMonitors" "crt1,notv"
        BusID       "PCI:1:5:0"
EndSection
Section "Screen"
        Identifier "Default Screen"
        Device     "Generic Video Card"
        Monitor    "AccuSync 95F"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768
" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768
" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768
" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768
" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768
" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768
" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection
```

My question is fairly simple. Can I activate the tv-out on my video card using this config file, or do I need to look for other drivers, or is this just plain not possible right now?

Currently running Ubuntu Feisty 7.04 on the x86-64 platform.

Can anybody help? Also, please let me know if you need any further information on this.

---

### Post by ebbomega on 2007-07-03
Well, nevermind.

Apparently with this mobo just unplugging everything from the video card save the television causes it to automagically display to the TV-out when you restart X.

Go simple answers. This is officially thing I'm happy about ubuntu #523.

---

### Post by chiques on 2007-10-22
What file would you suggest I look at to see what port my video is on? 

***[SIZE="2"]/etc/X11/xorg.conf[/SIZE]*** ???

If I do look at your /etc/X11/xorg.conf file, what should I be looking for? 

In your file you have:

"
Section "Monitor"
        Identifier   "AccuSync 95F"    --->**[SIZE="4"][COLOR="Red"]Is this yourVGA  or your HDMI monitor?[/COLOR][/SIZE]**
        Option      "DPMS"
EndSection

Section "Device"
        Identifier  "Generic Video Card"
        Driver      "fglrx"
        Option      "DesktopSetup" "clone"
        Option      "ForceMonitors" "crt1,notv"
        BusID       "PCI:1:5:0"
EndSection
Section "Screen"
        Identifier "Default Screen"
        Device     "Generic Video Card"  ---> ***[COLOR="Red"]What is this?[/COLOR]***
        Monitor    "AccuSync 95F"
        DefaultDepth     24
[COLOR="Red"]***What are all of these different settings below?***[/COLOR]
        SubSection "Display"
                Depth     1
                Modes    "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768
" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768
" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768
" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768
" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768
" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768
" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection
"

So you simply unplugged your HDMI cable and ran "startx" again and that started your GUI with your VGA (NOT YOUR HDMI) monitor?

Thanks!

---

