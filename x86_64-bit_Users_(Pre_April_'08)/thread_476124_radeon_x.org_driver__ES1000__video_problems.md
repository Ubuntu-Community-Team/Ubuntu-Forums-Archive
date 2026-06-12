---
title: "radeon x.org driver / ES1000 / video problems"
date: 2007-06-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by callumd on 2007-06-16
Hello,

I'm having a problem with video playback. I'm running 64bit Feisty on an ATI ES1000 integrated graphics chip (device id 515e). X works fine normally when the default ati driver is used, but when any media files are played, there's audio but no video. Changing to the vesa driver solves the problem, but with performance so poor the video is unwatchable. The proprietary ATI driver doesn't work either, it reports that no device was detected when GDM starts.

Does anyone else have this problem, or know of a work around?

thanks

---

### Post by The Foz on 2007-06-27
Sorry. I am not here to help you (would if I could), but rather to get help.

How did you get your ES1000 working at all?  Did you do any special set-up?

I have an ES1000, and am using the standard ati driver. All my graphics rendering is being done in software (I am getting 100% CPU  utilization when I play a video).

I have 64 bit hardware, but am currently running 32 bit Feisty Fawn.

---

### Post by praxis22 on 2007-06-27
There's a bug ID for this here:

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/86072](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/86072)

Why not roll over there and see if you can add any more.

This is an opensolaris bug for the same chip that seems to have a work around:

[http://bugs.opensolaris.org/bugdatabase/view_bug.do?bug_id=6494769](http://bugs.opensolaris.org/bugdatabase/view_bug.do?bug_id=6494769)

---

### Post by The Foz on 2007-06-28
Thanks, praxis22, but this is not quite my issue.

I do have functioning graphics with the ES1000, using both the ati & the vesa drivers.

In both cases. however, I have no hardware graphics acceleration. All the graphics work seems to be done in software. 

This is why I was interested in this post by callumd, as he seems to have the ability to at least play video (which I can only to at half-size, at which point my CPU usage is 100%).

I shall keep fiddling with my system, to see if I can fix it myself.

---

### Post by MightyMartian on 2008-06-04
> **The Foz said:**
> Thanks, praxis22, but this is not quite my issue.

I do have functioning graphics with the ES1000, using both the ati & the vesa drivers.

In both cases. however, I have no hardware graphics acceleration. All the graphics work seems to be done in software. 

This is why I was interested in this post by callumd, as he seems to have the ability to at least play video (which I can only to at half-size, at which point my CPU usage is 100%).

I shall keep fiddling with my system, to see if I can fix it myself.

I'm running the x64 version of Hardy Heron and have used the vesa driver kludge, but has there been any progress on properly supporting the ES1000?

---

### Post by The Foz on 2008-06-04
Hi MightyMartian,

As far as I know, there has been no progress.

The main thing that I did which improved my video performance was to reduce my screen resolution.

Some time soon I will be upgrading my server to Hardy Heron, and will see if there are any improvements in video performance as a result.

---

### Post by stephenb on 2008-06-15
I have a HP Proliant ML350 G5 with a built in ES1000 video controller. I recently did a fresh install of Hardy on that machine and I have not be able to get decent video performance. I haven't tested extensively. However, it doesn't look promising.

I don't want to spend my life messing around with ATI and Linux, as I've done enough of that on another machine.  So, I decided I should just install another graphics card. I started looking into it recently, but the PCI slots are different and apparently don't support graphics cards, at least some of them don't. It has PCI-X slots, though.

Does anyone know any upgrade options for better graphics on Proliants, especially the ML350?

=== UPDATE 3 DAYS LATER ==============

The silence was deafening, and I discovered why. It's very hard to find PCIx graphics cards. Maybe Matrox has some, but they could be expensive, plus it might be a risk to order one and find out it doesn't do as promised. 

But I've hit on a solution of sorts. Here's some of what I now have in xorg.conf:

     ```

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
    HorizSync    30-83
    VertRefresh    56-76
EndSection

Section "Device"
    Identifier "ATI ES1000"
    Driver "ati"
    ChipID 0x515a     <- changing the e to a here improved things for me!
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies Inc ES1000"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
          Depth        24
    #Modes        "1680x1050"
    #Modes        "1600x1200" 
    #Modes        "1440x1050"
    #Modes        "1440x960" 
    #Modes        "1280x1024" 
          Modes            "1280x960"
      EndSubSection
EndSection 
```The screen resolution was small and the rendering was old-fashioned looking until I found the idea of changing the ChipID from here: [http://ubuntuforums.org/showthread.php?p=3846525#post3846525](http://ubuntuforums.org/showthread.php?p=3846525#post3846525). I also added the HorizSync and VertRefresh rates as specified in Xorg.0.log at the same time. Maybe that helped as well. 

The strange thing is that I'm getting a resolution of 1680x1050, which is my first entry but hashed out! I don't get that. 

The trade off with this is that programs like Stellarium don't run. 

It's a real shame that Ubuntu can't manage driver support for the ES1000, which is practically a standard in many servers.

---

### Post by vikramsharma on 2008-07-21
Same thing here, I installed Ubuntu thinking that Radeon ES1000 would be better supported on Ubuntu than Fedora 9.  Standard server graphics cards should be supported on Linux, guess I would have to switch back to Fedora, it took a lot of persuading on my part to convince my boss to use Ubuntu instead of Fedora.

---

### Post by stephenb on 2008-07-21
Yes, you'd think standard server cards, if anything, would be supported. But I think HP (in my case) is negligent in not supplying what is standard in an average office workstation, and especially in not giving the choice to upgrade easily.

All that aside, I've got a reasonable looking setup now. It's not sharp compared to the average nowadays, and if I switch back and forward from a regular machine to the server, it's almost like going from 2008 to 1998 in terms of graphics quality. But it is functional.

If you haven't already abandoned Ubuntu, these additions might help. First of all, as mentioned above, I added this to the Device section:[INDENT] ChipID 0x515a    
[/INDENT]  This gives me a 1680x1050 screen resolution, and I can choose from lower ones. My xorg resolution settings appear to be ignored. But that's fine. 

One problem though: the resolution is slightly larger than my physical screen. I don't know how to fix that. When I open a new window, for example, the window appears slightly off screen on the left by half a centimeter. 

The next thing I did was install some sharp fonts. This one is good for the terminal:[INDENT]sudo apt-get install xfonts-terminus
[/INDENT]And the Artwiz set is pretty good. You can get it from here: [INDENT][http://artwizaleczapka.sourceforge.net/](http://artwizaleczapka.sourceforge.net/)
[/INDENT]If you can't find instructions on installing, let me know via this thread.

---

