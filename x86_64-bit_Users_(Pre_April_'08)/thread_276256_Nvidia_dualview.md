---
title: "Nvidia dualview"
date: 2006-10-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by lonelypauly on 2006-10-12
Ok, i just switched over to kubuntu 64bit from the 32bit version of ubuntu dapper and have had trouble setting up my dual desktop with kubuntu 64.

i have an Nvidia geforce 6800 ultra dual head (PCI-E) DVI video card.

ive followed the wiki/ubuntu guides for setting up dual desktops for kubuntu 64 (at least i think kubuntu 64 will work, no?) and so far have ended up having to load the backup X config file twice after the pretty desktop gui was unable to load. 

i used automatix2 to install the latest nvidia-glx driver and made sure it was installed, which it is.

the only strange thing i have observed is that when i enable the nvidia settings in adept, i logout and log back in, only to find that the nvidia settings are disabled again when i check it using adept.  it is being reset somehow and i can't figure out why.

i dont remember it being this difficult when i successfully set up dual desktops in ubuntu dapper 32bit.

any ideas?  are there any guides for kubuntu 64 for dual desktop setups that anyone has had success with?

thanks

---

### Post by jamal07 on 2006-10-13
Post your xorg.conf to forum. I have a working setup for 64-bit Kubuntu triplehead :P

1 NVidia 6600 dualhead (two monitors)
1 ATI dualhead (only one port on use)

Though I never tried to use adept, just stabbed the xorg.conf.

---

### Post by lonelypauly on 2006-10-13
:)

---

### Post by lonelypauly on 2006-10-13
:)

---

### Post by jamal07 on 2006-10-13
Urh! :D

Pleep, error: cannot compute! :cool: 

My mistake perhaps, I should have specified actual file which is located in:
/etc/X11/xorg.conf

Not the one you sent. Quite long... For sake of clarity of this thread you could remove your previous post :D 

rgrds,
Jamal

---

### Post by lonelypauly on 2006-10-13
[IMG]http://i6.photobucket.com/albums/y215/lonelypauly/snapshot2.png[/IMG]

this is where that file came from (xorg.cf)...is it in a different place under kubuntu?

---

### Post by jamal07 on 2006-10-17
Sorry for late answer lonelypaul. 

You are looking the configuration file in wrong place. Xorg configuration file (in Ubuntu, Kubuntu, Xubuntu, and in most LSB's) are in /etc/X11/config directory.

File you should be editing is:
xorg.conf

Full path to file is then:
/etc/X11/config/xorg.conf

NOT!
/etc/X11/config/cf/

rgrds,
Jamal

---

### Post by lonelypauly on 2006-10-18
lol...you are right...i noticed that shortly after this post...i went back to kubuntu dapper 32 and got twinview running in short order...its not worth the headache on kubuntu 64 until the flash issue is sorted out...as it is no youtube, which is not good.  

thanks jamal

---

### Post by jamal07 on 2006-10-19
> **lonelypauly said:**
> lol...you are right...i noticed that shortly after this post...i went back to kubuntu dapper 32 and got twinview running in short order...its not worth the headache on kubuntu 64 until the flash issue is sorted out...as it is no youtube, which is not good.  


Great! Umm... there are lot of issues in 64-bit, though I managed to get by them by using 32-bit FF and flash-plugin. 64-bit Lightning extension is missing also... :rolleyes: 

rgrds, Jamal

---

