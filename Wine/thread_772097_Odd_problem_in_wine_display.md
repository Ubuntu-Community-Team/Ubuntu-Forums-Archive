---
title: "Odd problem in wine display"
date: 2008-04-28
forum: Wine
---

### Post by thumper_e on 2008-04-28
I came across a problem after updating to 0.9.59 and it appears to have continued to 0.9.60.

I started with gutsy, ATI 9600 with the fglrx drivers, direct rendering working as with the games i wanted (CNC3, Champ Man...) in 0.9.58 however on upgrading to .9.59 software installs and winecfg both display properly, However on running the games i get a fuzzy display a bit like a tv half tuned in to something but with heavy interference, I cant see any of the game display just the fuzzyness.

So i did a clean install of hardy installed all

sudo apt-get build-dep wine wine-dev

re-installed the ati drivers so fglrxinfo returns;

display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.1.7415 Release

reinstalled wine from the package manager (0.9.60) and i get the same problem.

However 0.9.58 which i have compiled for Cnc with the cursor and lan patches runs my games fine. I then tried compiling 0.9.60 in the same way (no errors found during the process) and again it shows the fuzzy screen. The strange thing is there are no error messages produced in the terminal that differ from the usual ones i get in the working wine.

How would i find out what the problem is and subsequently fix it?

Any help would be appreciated.

Regards

cpu: Intel(R) Pentium(R) 4 CPU 3.00GHz
cpu_ghz: 3.0
memory: 1519
videocard_manufacturer: ATI Technologies Inc.
videocard_type: ATI RADEON 9600 Series
videocard_ram: 256
agp_aperture_size: N/A
videocard_driver_version: 2.1.7415 Release
soundcard: Intel ICH5 with ALC655 at irq 2
soundcard_driver: ALSA Version 1.0.15
machine_bitness: 32
kernel: 2.6.24-16-generic
x_version:
distro: Debian lenny/sid

---

### Post by situz on 2008-04-28
Hmm, I had a similar problem, for me it was 2 things I had to change to fix the problem, first I had to change the refresh rate on my screen to the same as the game runs on, I had it on 75hz, then changed it to 60hz, and then the problem was almost gone for me. the second thing I did was to change the visual effects to noone. this is done by right clicking your desktop-> Appearance Preferences-> Visual Effects-> check "None".

no guarantee that this will fix your problem, but you can at least give it a try =) 

let me know how it turns out

---

### Post by thumper_e on 2008-04-28
Thanks for the reply,

Tried reducing the screen resolution also desktop effects are off , however this made no difference at all.

Ian

---

### Post by situz on 2008-04-28
> **thumper_e said:**
> Thanks for the reply,

Tried reducing the screen resolution also desktop effects are off , however this made no difference at all.

Ian

you mean refresh rate? I can't recall mentioning anything about resolution:P

but well, are you sure you have the correct graphics driver installed ?
check out [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) if you're not sure you have the correct drivers installed

---

### Post by thumper_e on 2008-04-28
Sorry slip of the finger i ment to say refresh rate!

As for the correct drivers i installed ATI's 8.47.3 off of their website which appears to work for everything except wine versions 9.59/.60 ..

i will however give removing it and installing it through envy a go and see what happens.

---

### Post by thumper_e on 2008-04-28
Having removed the ati drivers that i installed manually and using envy to re-install the ATI drivers, i found it to be exactly the same.

Also video's appear to only work in full screen mode for some strange reason (unless compiz is off), i presume they are related!

---

### Post by thumper_e on 2008-05-04
This problem seems to have disappeared with the upgrade to the latest version of wine

---

### Post by situz on 2008-05-04
awesome =)

---

