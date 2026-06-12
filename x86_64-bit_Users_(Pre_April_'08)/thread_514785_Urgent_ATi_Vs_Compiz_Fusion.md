---
title: "Urgent ATi Vs Compiz Fusion"
date: 2007-08-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by ahchong on 2007-08-01
em.. this happen to me. im using ATi express X600 64MB on my laptop, we all know that compiz is still Alpha. Gusty will make it default program for system.
then i had feww crash lately, then decided to install restricted ATi driver in the restricted driver of course. then when after install, i restart and try to on Compiz.
then walla.... Compiz FAILED to start!!
then uninsatll it, Compiz can be use again.
yet, the graphic is more excellent using the restricted river, but hav a bit lag in video and others program... very bad:(

---

### Post by praxis22 on 2007-08-01
Why is this urgent?  It's happening to lot of people trying to use ATI proprietary drivers and Beryl/Compiz.
It's not even Beta yet, what were you expecting?

[http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314)
[http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)
[http://ubuntuforums.org/showthread.php?t=481615](http://ubuntuforums.org/showthread.php?t=481615)

This is Linux, not windows, you have to prepared to get your hands dirty, and for the possibility that it may not work if you use modern hardware.

Sorry but them's the breaks.

---

### Post by michael37 on 2007-08-01
> **ahchong said:**
> em.. this happen to me. im using ATi express X600 64MB on my laptop, we all know that compiz is still Alpha. Gusty will make it default program for system.
then i had feww crash lately, then decided to install restricted ATi driver in the restricted driver of course. then when after install, i restart and try to on Compiz.
then walla.... Compiz FAILED to start!!
then uninsatll it, Compiz can be use again.
yet, the graphic is more excellent using the restricted river, but hav a bit lag in video and others program... very bad:(

I am using Compiz with ATI mobility x1400 (restricted drivers) very successfully.  However, to get good results (especially speed) you MUST use Xgl.

So, install your binary restricted drivers, and then following the following two FAQs that I found most useful:

[https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

and then

[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

---

### Post by Lonthong on 2007-08-01
Compiz-fusion runs fine on my lappy (Turion X2, ATI X1100, 512Mb Ram).
I am using restricted driver + xgl as well.........

---

### Post by ahchong on 2007-08-02
well, then after uninstall the restricted driver, i got Xgl problem..
my screen starting to blur... Serve me!

---

### Post by lasker on 2007-08-02
Hey for some reason when i log in using the xgl server, the gnome session doesnt load all im left staring at is the background,

im using ati with xgl and have followed the instructions, since the server actually runs im assuming its not a driver issue with the ati driver

i just want my window manager to start !

:(

please if any1 can help i would be most greatful

:D

Marco

---

### Post by PeterIJlst on 2007-08-02
I am using Ubuntu studio with XGL, Beryl and Compiz (Fusion).
All works like a charm on my old laptop, Acer aspire 1690.. AtiX700.
Do you have more information?

---

### Post by michael37 on 2007-08-02
> **ahchong said:**
> well, then after uninstall the restricted driver, i got Xgl problem..
my screen starting to blur... Serve me!

Install the restricted driver back.  IMO, it works much better for ATI video cards, and especially laptop video cards and non-standard laptop LCD resolutions.

---

### Post by michael37 on 2007-08-02
> **lasker said:**
> Hey for some reason when i log in using the xgl server, the gnome session doesnt load all im left staring at is the background,

im using ati with xgl and have followed the instructions, since the server actually runs im assuming its not a driver issue with the ati driver

i just want my window manager to start !

:(

please if any1 can help i would be most greatful

:D

Marco

Which method from the Xgl guide did you follow?  

With my experience, Method B (**CAREFULLY** follow instructions for ATI video cards **If you have ATI with fglrx drivers**) works the best -- that way Gnome gets less confused.

Troubleshooting (optional, lots of technical details):

Xgl is a nested Xserver, so you actually end up running  two X servers: normal Xorg and Xgl.

When you graphical sessions hangs (displays only background), you can always press Ctrl-Alt-F1 to access the text prompt.  Then, log in as yourself and type the following command (case sensitive):
[indent]
ps -ef | grep X | grep -v grep
[/indent]
My output of the command looks like this:
[indent][noparse]
root      5121  5118  5 11:34 ?        00:01:21 /usr/bin/Xgl :1 -fullscreen -br -accel xv:pbuffer -accel glx:pbuffer -dpi 100 -nolisten tcp -auth /var/lib/gdm/:1.Xauth -nolisten tcp vt7
root      5130  5121  0 11:34 tty7     00:00:13 /usr/bin/Xorg -br vt7 -auth /tmp/.Xgl-auth-cXwQM2 -nolisten tcp :94 -terminate
[/noparse][/indent]

If you find yourself missing either Xgl or Xorg, then your background is provided by one of them, but the complete X configuration is not functioning correctly.

---

