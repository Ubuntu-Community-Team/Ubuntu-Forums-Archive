---
title: "World of warcraft....after 5 hours.....is buggy?"
date: 2008-12-02
forum: Wine
---

### Post by VampiricFang on 2008-12-02
Using 64 bit Ubuntu 8.10, with Wine 1.1.9

I copied everything from my Vista boot to a External HD, and then just copied it over. The sound is horrid and if I turn the graphics up to anywhere near what I have them while running the program in windows, it dips down to a nice, smooth, silky 13 FPS. I normally see it hitting 45-60 FPS, it fluctuates depending on whether I'm moving or not.

My system specs are my signature.

---

### Post by OMJD on 2008-12-02
You need to ensure that it's running in OpenGL mode. Running it in Dirext X mode will give you undesired results. 

I highly suggest following this tutorial and make the necessary steps, which should improve its performance:
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

Some steps (such as installation) may be skipped given that you already have it installed. 

I've had to refer to that every time after having installed WoW on linux, otherwise it's pretty much unplayable imo.

I also had the sound issue recently. This can be resolved by opening up a terminal, and typing "killall pulseaudio" after each system restart.

For many, it's easier to run it in Windows as it's often less hassle and less problematic. But I'm unable to find my Windows Vista installation DVD myself, so I'm pretty much stuck with running it on Ubuntu. 

Hope that helps.

- Rich

---

### Post by VampiricFang on 2008-12-02
"well for those users with a distro using pulse audio (for ex. Ubuntu) if you sett wine to OSS the sound for WoW works great and if you add padsp before wine pulseaudio wraps the OSS sound (like alsa-oss but better) and you can use vent, musik etc at the same time :)"

I don't know how to turn PulseAudio off.... :(

---

