---
title: "Hardware support"
date: 2007-02-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by meduele2cara on 2007-02-06
I'm fairly new to Ubuntu, I ran a live disk on my old computer, and with my new computer I figured I should try a dual-boot with XP and xUbuntu.  So, I dled the desktop CD vers 6.10 (or whatever the newest one is), put it in, booted my comp to the cd.

Everything was working fine, I saw the menu, chose to start/install linux, and all of a sudden, my monitor goes blank.  shows me the words "out of signal range" or something to that effect.

Anyways, I figure that my hardware might not support linux.  Is there any way i could fix that? Or is it something else that I'm not seeing? Any help is greatly appreciated.

Specs:
AMD 64 bit AM2 3500+
Biostar mobo Tforce 6100 AM2 w/onboard gfx (geforce 6100)

---

### Post by John.Michael.Kane on 2007-02-06
I'm using a t-force 6100 nf410 which is supported fully.

While the am2 uses a diffrent chipset it should be fully supported. note before choosing start/install   try hitting F4,and selecting your screen res.

What kind of screen is your machine connected to ie: lcd or standard crt?

Also have you tried the alternate cd-iso?

---

### Post by meduele2cara on 2007-02-07
What should my screen res be?

I have an lcd, and no I havent tried the alternate iso, thx alot.

---

### Post by John.Michael.Kane on 2007-02-07
Do you have your monitor's manual? If you do all you have to do is get it out, look at the refresh rates and then type, I believe, sudo nano /etc/X11/xorg.conf, as root in **text mode**. Then keep going down the page until you find where it says Hor Refresh Rate and Vert. Then simply substitute the information in those fields with the information provided in your manual. Then press ctrl-x and save the data. This should eleaveate your problem.

---

### Post by meduele2cara on 2007-02-09
Hey, I decided to run Vector Linux instead.  Everything worked fine, its installed and running.  Thanks for your help.

---

