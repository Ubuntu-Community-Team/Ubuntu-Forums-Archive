---
title: "Black screen on boot"
date: 2007-10-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by hellobelow on 2007-10-09
Hi. 
Yesterday I installed Ubuntu Feisty on my computer, dual booting with Vista.
Everything went nice, and I was happy, but I wanted gfx drivers so I tried installing them, but it didn't work out.
Today I sit here with my screens blank. Both HDs start and my screen says the cable is allright. 
The fan on the gfx-card is running too, but won't make me any signals.
My mouse and keyboard lights are both turned off (no contact)

I've also tried installing a W-Lan-card but I didn't work that out either..

I would be really happy if anyone had any ideas what to do..

--Henning


Hardware:

160GB SATA with Windows Vista
320 GB SATA with Ubuntu
nVidia 8800 GTX 
Belkin PCI-wlan (calling itself Air Force One in *lspci*)
Pentium D 64-bit dual core processor
nForce motherboard
USB habu mouse
USB keyboard

---

### Post by Bliepo32 on 2007-10-09
I have the exactly the same problem. I also recently installed Ubuntu Feisty Fawn 64 bit edition (I used Dapper Drake 64 bit edition before this, which worked fine). The installation went fine, and also installing the restricted ATI drivers as describes in [Installing Ubuntu 7.04: ATI X***** cards]("http://ubuntuforums.org/showthread.php?t=414194") (I have an ATI RADEON x800GTO) went fine.

When I boot (in normal mode), my screen goes blank, and the power led turns from green to yellow (like it is not getting any signal). Also, the caps lock and scroll lock light start flashing. The computer does not respond to anything but the power off button after that.

Booting in recovery mode and typing
```
gdm start
``` will just give me a normally working screen. I can then just log-in and work normally. Maybe you could use this as a temporary fix. I also wait for someone to give a fix for this problem.

System specification:
AMD Athlon(tm) 64bit 3500+ processor
ATI RADEON x800GTO videocard
190GB Maxtor harddisk (with a partition of 5GB mounted as /home and a partition of 12GB mounted as /)
ASUS A8N-SLI Deluxe motherboard

---

### Post by hellobelow on 2007-10-09
Hmm.. The only thing I can do is turn the computer on and off (and open/close the dvd-tray).
Might be slightly more hardware related..

argh.

--Henning

---

### Post by Bliepo32 on 2007-10-09
I am certain that my issue is not hardware related, as Dapper Drake used to work fine. Installing Feisty Fawn caused the rpoblems.

---

### Post by hellobelow on 2007-10-09
but are you able to use your keyboard to write? and when you run the command, does the picture just appear?
and how do you reach recovery mode?

--Henning

---

### Post by Bliepo32 on 2007-10-09
If you have GRUB installed (which is probably the case), it will show you a menu before booting Ubuntu. Here you have the choice to start Ubuntu, start in in recovery mode, or do a memory test. If you have other operating systems installed, it will also give you the option to boot these.

I have also found an image of it on the web, you can see it [here]("http://yekubuntu.free.fr/hoary/images/grub.jpeg").

---

### Post by hellobelow on 2007-10-09
Well, I never get there really.
I never get to see the boot screen, so I think we might have different problems after all.
My monitor stays black..

But thanks for the suggestions though!

--Henning

---

### Post by Bliepo32 on 2007-10-09
It seems that your motherboard might be damaged. You could try to send it back to your manufactuer, or take it to a local computerstore. If you are a bit technical, you can open the computer yourself and see what's wrong. You could also try resetting your motherboard (see the manual on how to do this).

---

### Post by hellobelow on 2007-10-10
That's a plan, thanks!

***
I've sent a mail to support now

---

### Post by neowampyre on 2007-10-10
> **hellobelow said:**
> That's a plan, thanks!

***
I've sent a mail to support now

Don't send back your motherboard, I have the same problem....
My config is: ASUS P5N-E SLI MoBo, nVidia8600 GTS VGA, 4GB Kingston RAM, core2duo e6320 proc, Feisty Fawn 64 bit desktop edition.
So, if I turn on my pc, I can choose the OS (kernel) what I want (I have Vista Ultimate 64-bit edition on the HD too), and after the choosing, the screen goes blank, and a signal appears: "power saving mode", the button goes yellow.  After 20 seconds, the screen wakes up, the nVidia logo appears for a half second, and the system starts normally.
I've found a "solution" somewhere on the web, but I forgot the link, sorry...  (You can find it using Google, I'm sure.) An expert (Ubuntu-developer) wrote: they have solved this problem in Gutsy, but it's uncurable in Feisty Fawn, sorry.
Well, be patient, wait for the Gutsy "alpha" edition:)

---

### Post by hellobelow on 2007-10-10
But you see the boot selection screen.
My computer does not catch bios.

---

### Post by neowampyre on 2007-10-10
> **hellobelow said:**
> But you see the boot selection screen.
My computer does not catch bios.

First of all, can you see the BIOS start-screen at startup?
If you can see it, first try to reset the CMOS (it's very simple and safe, use Google, and your mobo's manual, how can you do that, this is the hardvare-setting-memory of your mobo). After that, your mobo will forget all its earlier settings, and you will get a "clear" mobo.

If you can't see the BIOS start-screen: I had a similar problem with BIOS a half year ago, and I managed to solve it. My mobo contacted the chase. Try it, take out all the stuffs (mobo, processor, PSU, VGA card, etc.) from the chase, and set up them in your desk. You will see, is it a contact-problem, or not.

"My computer does not catch bios": what does it mean? The led on your mobo doesn't light?

Can you see the choosing-screen (where you can set the operation systems and kernels)?

---

### Post by hellobelow on 2007-10-10
I think I'll do as you said about pulling everything out. There's quite a mess in there. Thanks for the ideas.

---

### Post by picopir8 on 2007-10-10
Sounds like you are having the same problem that we were discussing on another thread.
[http://ubuntuforums.org/showthread.php?t=572074](http://ubuntuforums.org/showthread.php?t=572074)

In grub, edit the boot command to remove "splash".  It should boot right up.  I think there is a bug with the splash option.

---

### Post by |{urse on 2008-06-07
okay if you're seeing hdd activity and just a black screen after the grub menu then your monitor probably isnt supported. The gfx is outputting but the monitor isn't recieving and ubuntu isn't aware that the monitor isn't outputting, go hook it up to a different one and try it again. too bad, it sucks when a lappy's screen isnt seen. But there are things you can do to make it work once you know yoiur gfx card is in fact sending a signal. let me know once you've tried an external monitor.



lol this post is one year old =O

---

