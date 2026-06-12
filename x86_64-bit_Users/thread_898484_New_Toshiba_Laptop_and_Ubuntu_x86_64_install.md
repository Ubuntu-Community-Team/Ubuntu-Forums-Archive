---
title: "New Toshiba Laptop and Ubuntu x86_64 install"
date: 2008-08-23
forum: x86 64-bit Users
---

### Post by linuxfan2007 on 2008-08-23
This weekend I finally took the opportunity to use my step-son's Circuit City employment(not really use him, just had some in store discount info) and bought a new Toshiba Satellite L305D-S5881 laptop.
It's an AMD64 Turion x2, ATI graphics, 200gb SATA HD, etc, etc.... Windows Vista Premium (groan, not sure what is so premium, same old Windows glitches and tough to navigate even the smallest of customization tasks.)

Bottom line first: I love it!! a little on the heaviness side @ 5.7 lbs, but I need the exercise. :) 

So being the adventurous sort that I am, I wanted to repart. the HD and put an Ubuntu and Fedora install on so I can do the triple boot thing. btw- I'm not a Linux or Ubuntu newbie, but still learning new things now and then.

To repart.the HD and resize the parts. I first downloaded and tried (futilely!!) Gparted live CD. did not have any luck there (still not sure of the issues or why, but would not boot and discover HD).
Abandoned that and booted up the Ubuntu 8.04.1 live cd to try GParted there. Worked like a charm and now have a nicely repartitioned HD.
I made sep. parts for Ubuntu, Fedora and Vista with a common swap part. to use for both Linux OS's when booted. I really didn't see the need to make 2 swap parts.
So now I have my parts.layout, onto the install.

As expected, the Ubuntu install went just fine with the exception of the wireless drivers. I have an Atheros AR242x chipset according to lspci. Although install detected the wireless just fine and loaded the driver, no amount of diagnosis or fixing myself would help until I found this thread:

[http://ubuntuforums.org/showthread.php?t=816780](http://ubuntuforums.org/showthread.php?t=816780)

Plus help from this bug ticket:

[http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192)

What still puzzles me is: Why didn't the latest version of Madwifi work? I tried both 0.9.3 and 0.9.4 versions.

The thread instructions worked beautifully!! Many thanks to the great peeps/experts on this forum!!

And that's it....Ubuntu works!!
Now to get the integrated mic and camera working (but not a high priority)

What impresses me most about the whole install is that everything works, even the volume knob on the front just works w/ no special setup for Ubuntu!!

Flash works (no special install)
Java works (no special install)
All Audio works (no special install)
USB works!! (no special install)
CDROM works (no special install)
Firefox works (no special install)
CD Burning works!!
DVD playback works!
Sound works!!

---

### Post by plb on 2008-08-23
I also just got a satellite but an a215 and everything seems to work fine except it runs a bit hot around 60c but I've read it's just how this model runs..same processor as yours it seems...what's your acpi -V show you?

---

### Post by linuxfan2007 on 2008-08-23
here it is:

 acpi -V
     Battery 1: charged, 100%
     Thermal 1: ok, 64.0 degrees C
  AC Adapter 1: on-line

does seem a little warm coming from side vent.

---

### Post by dukerussian08 on 2008-08-30
I purchased the same laptop and installed 64-bit Ubuntu Hardy. I've got the following problem: the computer overheats and turns itself off. The fan seems to not turn on. ACPI shows the temperature to be 0 Celsius. 

Any ideas?

---

### Post by emustrangler on 2008-12-14
Same problem, fan doesn't turn on with Intrepid on toshiba satellite L305D-S5895.

Tried to download programs to allow for manual control, but no dice.  Someone figures this out, please post.

---

