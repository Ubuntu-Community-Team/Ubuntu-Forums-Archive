---
title: "Black screen when using dvi connector"
date: 2007-06-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by draculagorgona on 2007-06-29
Hello,

I am writing in hopes that someone can help resolve an issue I am having.

Here is my general info:

Operating system: Ubuntu Feisty Fawn 7.04 64 bit - Linux-x86_64
Monitor - 20' LCD - ViewSonic Optiquest Q20wb
Video Card: EVGA e-GeForce 8800 GTS
NVIDIA Driver Version: 100.14.11

I can view images in the proper resolution (1680 x 1050) when I have a vga connector attached to my monitor and then into the video card (dual dvi outputs) with a vga adapter.

I have tried connecting the monitor to the video card with a dvi connector, but I get a blank screen when trying to boot ubuntu.

I can go into the bios screen and I also see the beginning text when ubuntu boots, but instead of the gui I just get a blank screen.

Do you know if this is a bug or if there is any thing I can do to correct this error?

Thanks for your help!

---

### Post by glenndavy on 2007-07-04
> 
I can view images in the proper resolution (1680 x 1050) when I have a vga connector attached to my monitor and then into the video card (dual dvi outputs) with a vga adapter.

I have tried connecting the monitor to the video card with a dvi connector, but I get a blank screen when trying to boot ubuntu.

I can go into the bios screen and I also see the beginning text when ubuntu boots, but instead of the gui I just get a blank screen.


Hey there - just thought i'd bump this... I'm getting same issues on radeon X1650'x when I use fglxrx proprietory driver

---

### Post by ThePlacebo on 2007-08-03
> **draculagorgona said:**
> Hello,

I am writing in hopes that someone can help resolve an issue I am having.

Here is my general info:

Operating system: Ubuntu Feisty Fawn 7.04 64 bit - Linux-x86_64
Monitor - 20' LCD - ViewSonic Optiquest Q20wb
Video Card: EVGA e-GeForce 8800 GTS
NVIDIA Driver Version: 100.14.11

I can view images in the proper resolution (1680 x 1050) when I have a vga connector attached to my monitor and then into the video card (dual dvi outputs) with a vga adapter.

I have tried connecting the monitor to the video card with a dvi connector, but I get a blank screen when trying to boot ubuntu.

I can go into the bios screen and I also see the beginning text when ubuntu boots, but instead of the gui I just get a blank screen.

Do you know if this is a bug or if there is any thing I can do to correct this error?

Thanks for your help!

I also wanted to bump this thread. I have the exact same setup as the OP, I have been running this hardware under OpenSUSE without an issue (I would like to switch to ubuntu). Has anyone found a solution or have any tips?

---

### Post by Thanatos10 on 2007-08-09
I don't have a solution; I have the exact same problem with my 8800GTS video card.  I can either boot using a VGA adapter or start in recover mode, pressing Ctrl-D when prompted and when asked to enter my user-id I just wait 3 or 4 seconds and it will boot normally.  There is no splash screen, nothing.  It sounds like it is booting normally then it just stops and the monitor will go into standby after a few minutes.  I’m using the latest NVIDIA 100.xx.xx drivers. 

What is the difference between the "normal" boot sequence or the recovery mode boot-up’s?  When booting normally I can see watch the boot process then suddenly the screen will go black and nada.  You can hear the disk drives continue to boot, the CDROM's spin-up, etc.  In recovery mode when the screen goes black during the normal boot-up the video will go to about half brightness, but it will boot-up.

Sounds like a few people are having this problem reading the posts. Is this just a "Ubuntuism" we'll have to deal with or does anyone have an idea for a fix.  All help or suggestions are most welcome.

Scott

---

### Post by achoo5000 on 2007-08-09
Hey buds,
Saw this post yesterday because I had the same problem. I came across a solution in a rather ghetto way. In the end, your xorg.conf file should have this:

```

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: 1680x1050_60 +0+0"
EndSection

```

This will enable the DVI interface on the first connector, that's what the DFP in the metamodes option is for. (VGA is refered to as CRT). You may have to change the resolution in metamodes to match your monitor.

A note about how this was discovered: I actually went into nvidia-settings while hooked up through the VGA cable. Then went to X Server Display Configuration and put my mouse over the "Detect Displays" button, swap cables to the DVI and click the mouse (don't move it!). You still won't see anything, swap back to the VGA cable and it will say somtehing about CRT-0 being unplugged, just say "yeah whatever." But there will be a new screen in the layout panel which is DFP-0, Enable it and set it up to how you like, then click 'Apply' and 'Save to X Configuration file'. (make sure it actually changed the file, mine didn't at first, had to run nvidia-settings through sudo). Then when the setting are all kosher restart X with the DVI plugged in and cross fingers.

LATER!

---

### Post by Thanatos10 on 2007-08-09
Thanks acho5000, I'll give it a try as soon as I get home from work.  I think I've tried about 4 or 5 differnet things so far, but nothing has worked.  Your suggestion sounds like you might be on to something there.

I'll post the results as soon as I get home.

Scott

---

### Post by achoo5000 on 2007-08-10
So after some more mysteries I think that the nvidia-settings has its own settings file which I don't understand, you may have to do the plug dance to get it all jived.

---

### Post by Thanatos10 on 2007-08-10
Achoo5000 that worked for the most part.  I can now boot normally, I still don't see the splash screen, but who cares--IT BOOTS!

Thanks for your time achoo5000.

Scott

---

### Post by achoo5000 on 2007-08-10
reading at [this]("http://ubuntuforums.org/showthread.php?t=503529&page=4") thread, I think I can help you out a little more.

Edit your grub menu list ( /boot/grub/menu.lst ).

Find your OS in the list of OSs, and edit the kernal part,

```
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=aa5decf1-4785-4eba-9433-6d7b3fc6c1c1 ro quiet splash
```

just take out (comment out with a #) the thing that says splash at the end, it will show you the text based splash through DVI. Not pretty, but it's functional.

So i think the thing to do is find out how the splash screen decides where to output display and get it to the DVI, but this works in the interim.

---

### Post by Thanatos10 on 2007-08-10
While cruising the forums I found some discussions about the usplash files.  I noticed that they were talking about a bug in the current kernel release and how it effects the newer video cards.  I has to do with frame buffers and how they effect the system start-up and how to configure them  manually in the menu.lst file.  So I just added vga=791 right after the splash entry and everything is working normally again.  Well as normally as can be expected with me tearing things up.

I don't now what frame buffers are, but I guess they're important in the big scheme of things.

Thanks for getting me up and running achoo5000.

Scott

---

### Post by achoo5000 on 2007-08-10
sweet! All working now!

---

### Post by bDerrly on 2007-08-12
> **Thanatos10 said:**
> While cruising the forums I found some discussions about the usplash files.  I noticed that they were talking about a bug in the current kernel release and how it effects the newer video cards.  I has to do with frame buffers and how they effect the system start-up and how to configure them  manually in the menu.lst file.  So I just added vga=791 right after the splash entry and everything is working normally again.  Well as normally as can be expected with me tearing things up.

I don't now what frame buffers are, but I guess they're important in the big scheme of things.

Thanks for getting me up and running achoo5000.

Scott

Do you have a link to the thread you were browsing?

Also, instead of editing your kernel line in /boot/grub/menu.lst (which will be destroyed the next time you update your kernel) you should edit the default options line (# defoptions) and remove the "quiet splash" portion. Then run 'update-grub'.

---

### Post by david13cox on 2008-02-03
> **achoo5000 said:**
> Hey buds,
Saw this post yesterday because I had the same problem. I came across a solution in a rather ghetto way. In the end, your xorg.conf file should have this:

```

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: 1680x1050_60 +0+0"
EndSection

```

This will enable the DVI interface on the first connector, that's what the DFP in the metamodes option is for. (VGA is refered to as CRT). You may have to change the resolution in metamodes to match your monitor.

A note about how this was discovered: I actually went into nvidia-settings while hooked up through the VGA cable. Then went to X Server Display Configuration and put my mouse over the "Detect Displays" button, swap cables to the DVI and click the mouse (don't move it!). You still won't see anything, swap back to the VGA cable and it will say somtehing about CRT-0 being unplugged, just say "yeah whatever." But there will be a new screen in the layout panel which is DFP-0, Enable it and set it up to how you like, then click 'Apply' and 'Save to X Configuration file'. (make sure it actually changed the file, mine didn't at first, had to run nvidia-settings through sudo). Then when the setting are all kosher restart X with the DVI plugged in and cross fingers.

LATER!

I don't know how to say this other then I love you and you're a freakin genius!

---

