---
title: "Project 64 on wine"
date: 2008-02-13
forum: Wine
---

### Post by Don_Shifty on 2008-02-13
hello!
2 questions:
first: i managed to install project64 with wine, it even appears in my applications menu. i can also run it. but as soon as i want to emulate a game-rom (zip-file) it breaks down. can someone help?
second: i have a dual boot with winXP Pro. if i use wine can i start programms already installed on the winXP disk without reinstalling them via wine?
i'm running ubuntu 7.10. 
Thanks for the help!

---

### Post by luisromangz on 2008-02-13
You should try a Linux native N64 emulator called Mupen 64.

Programs that setups registry keys while installing won't find these keys if run through Wine without being installed.

---

### Post by kbless7 on 2008-02-13
Mupen 64 works very well. I use it with my 360 controller.

---

### Post by Don_Shifty on 2008-02-15
thanks for the message! i tried mupen64... it found the roms (still zip files) and even displayed them on the main screen. if i want to run one of them it asks me to choose a UCode (?). but with either one of the UCodes it just gives me a black window....
what is wrong? do i need to use different roms? know where to find them? 
thanks a lot
shifty

---

### Post by gsrcrxsi on 2008-02-20
kbless, how did you get a controller configured with mupen64? the only options i have are none and keyboard. id really like to use my PS2 controller (with usb adapter) but i cant seem to get it configured. did you need a different plugin?

---

### Post by kbless7 on 2008-02-21
> **gsrcrxsi said:**
> kbless, how did you get a controller configured with mupen64? the only options i have are none and keyboard. id really like to use my PS2 controller (with usb adapter) but i cant seem to get it configured. did you need a different plugin?

You're going to need to install the drivers and get it working before mupen will recognize it.

---

### Post by gsrcrxsi on 2008-02-21
drivers for what? the adapter? i dont think there are any drivers. ive searched all over but cant seem to find anyting :(

---

### Post by kbless7 on 2008-02-22
I don't know how to get a ps2 controller working and I don't know if there are any tutorials on how to get one to work. 360 controllers work though.

---

### Post by timeblade0 on 2008-02-22
project 64 will run under wine if you have the right plugins for gfx. I found that 1964ogl and daedulus work ok. compatibility is low. I cant find a working sound plugin. mupen 64 for linux is probly a better choice.

---

### Post by gsrcrxsi on 2008-03-07
i got the ps2 controller working. i needed to install joystick and the calibration. 

mupen 64 works ok, but frame rates are very slow! project 64 under XP and with a crappy P4 single core 2.4GHz and old 9600Pro ATi card could do better. mupen 64 with ubuntu, q6600 quad @ 3.0 GHz and 7300 GT vid card can only put out like 20-30 fps

---

### Post by rcatman on 2008-03-09
I tried Project64 under wine today and it worked pretty good for me. Games other emulators wouldn't play at all worked in Project64.

The only problem I have is some video issues with textures, some show up as white for an instant. 

I have an nvidia geforce4 go card on my laptop.

If you're having problems I would make sure you have the latest version of wine from winehq.com. I had some previous issues with wine when installing other windows programs and the new version fixed them.

[http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb")

---

### Post by doorknob60 on 2008-03-10
Try messing with the Graphics settings in Mupen64 and/or using different plugins for it. The glide64 plugin works great for me.

---

### Post by desertboy on 2008-03-12
Mupen has poor performance compared to project64 or 1964 (The ntwo emu's are so close together and so close to perfect either would do) but it still is a loely emulator and if (Like me) you've got a core2duo then every game that runs (Which is like 98%) runs full framerate.

If you really want to emulate a 64 you could do a lot worse than starting here

[www.emutalk.net](www.emutalk.net) the devs of project64, 1964 & mupen all hang out there time to time, and any plugions worth their salt probably were first released there. While you're there check out my review I wrote years ago for the xbox port of project64 & 1964.

---

### Post by raj7095 on 2009-11-07
try using mupen64plus. Not mupen64; that's too obsolete. Here's a link: [http://code.google.com/p/mupen64plus/]("http://code.google.com/p/mupen64plus/")):P

---

### Post by ahayes on 2010-05-02
> **raj7095 said:**
> try using mupen64plus. Not mupen64; that's too obsolete. Here's a link: [http://code.google.com/p/mupen64plus/]("http://code.google.com/p/mupen64plus/")):P

No GUI, pretty useless unless you can wade through the ultra-complex text configuration process, which I cannot.

Doesn't even have a working frontend, all the ones on the site are either source only or unpackaged which ultimately defeats the purpose of using the frontend to begin with.

If it had decent frontend with a package you could just click on and install it would be an option.

---

### Post by argor on 2010-05-02
> **ahayes said:**
> No GUI, pretty useless unless you can wade through the ultra-complex text configuration process, which I cannot.

Doesn't even have a working frontend, all the ones on the site are either source only or unpackaged which ultimately defeats the purpose of using the frontend to begin with.

If it had decent frontend with a package you could just click on and install it would be an option.
use mupenplus 1.5 it was the last released with a gui  
[http://mupen64plus.googlecode.com/files/Mupen64Plus-1-5-bin-32.tar.gz](http://mupen64plus.googlecode.com/files/Mupen64Plus-1-5-bin-32.tar.gz) or 64 bits [http://mupen64plus.googlecode.com/files/Mupen64Plus-1-5-bin-64.tar.gz](http://mupen64plus.googlecode.com/files/Mupen64Plus-1-5-bin-64.tar.gz)
also give it time it is not long a go that the gui was split from the core 
there are more than 5 fronends in development

---

### Post by ahayes on 2010-05-02
> **argor said:**
> use mupenplus 1.5 it was the last released with a gui  
[http://mupen64plus.googlecode.com/files/Mupen64Plus-1-5-bin-32.tar.gz](http://mupen64plus.googlecode.com/files/Mupen64Plus-1-5-bin-32.tar.gz) or 64 bits [http://mupen64plus.googlecode.com/files/Mupen64Plus-1-5-bin-64.tar.gz](http://mupen64plus.googlecode.com/files/Mupen64Plus-1-5-bin-64.tar.gz)
also give it time it is not long a go that the gui was split from the core 
there are more than 5 fronends in development

None of the frontends have seen active development for some time and they're hosted on forums.

I'll look at that 1.5 but I'm thinking it will have reliability issues.

---

### Post by argor on 2010-05-06
> **ahayes said:**
> None of the frontends have seen active development for some time and they're hosted on forums.

I'll look at that 1.5 but I'm thinking it will have reliability issues.
most of the front ends are still actively being develop 
for example  CuteMupen had it latest released just 2 months a go [http://sourceforge.net/projects/cutemupen/](http://sourceforge.net/projects/cutemupen/)
not all of them are being hosted on forum 
but there is nothing wrong for a few being hosted on forum all releases of mupenplus before 1.3 were only hosted on a forum   
and for the other thing 1.5 is very stable

---

