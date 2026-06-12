---
title: "Ati radeon x1250 not recognized?"
date: 2009-03-05
forum: x86 64-bit Users
---

### Post by Reeman on 2009-03-05
The latest alpha cannot build the driver for the onboard ati x1250 chip. It seems to be a kernel problem with the 2.6.28 series. I have tried several debian distros and even tried a kernel recompile. The chip shows up with an lspci but seems to have trouble building and loading the ati proprietary driver. The ati driver wants to do a new xorg.conf but the Ubuntu install barfs all over anything not written by dbpg! It seems that debian based distros have made it almost impossible to reconfigure X with any other software than what is in the repositories. THIS really sucks! I wish they would start leaving politics out of their software decisions and leave it up to the user as to what they want to run ...proprietary or not.](*,)](*,)

---

### Post by Vince4Amy on 2009-03-06
> **Reeman said:**
> The latest alpha cannot build the driver for the onboard ati x1250 chip. It seems to be a kernel problem with the 2.6.28 series. I have tried several debian distros and even tried a kernel recompile. The chip shows up with an lspci but seems to have trouble building and loading the ati proprietary driver. The ati driver wants to do a new xorg.conf but the Ubuntu install barfs all over anything not written by dbpg! It seems that debian based distros have made it almost impossible to reconfigure X with any other software than what is in the repositories. THIS really sucks! I wish they would start leaving politics out of their software decisions and leave it up to the user as to what they want to run ...proprietary or not.](*,)](*,)

The latest version AFAIK is compatible with Kernel 2.6.28 and even perhaps 2.6.29. Are you installing on Jaunty though or do you have a new kernel on an older version. Jaunty uses xorg 1.6 so the drivers will not be compatible yet. Even though I use Slackware & RPM Distros I've never had any problems installing these drivers on Debian distros.

---

### Post by marcelkoopman on 2009-03-06
> **Reeman said:**
> The latest alpha cannot build the driver for the onboard ati x1250 chip...

Thats wasnt the smartest thing to do, Jaunty isnt out yet, so back to Intrepid?

---

### Post by Reeman on 2009-03-06
> **marcelkoopman said:**
> Thats wasnt the smartest thing to do, Jaunty isnt out yet, so back to Intrepid?
just goofing around with jaunty. My intention is to wait on a 64Studio release with an updated rt kernel. 

I have BlueWhite64 Slackware working with the ati 9.2 and a 2.6.28 patched rt recompile. 

I really do not like the Pulse audio stuff in Ubuntu the setup seems to block access to /dev/dsp and can be a pita to reconfigure for jack access direct to alsa. I can see why it is taking a long time to get Ubuntu Studio working with all the extra audio cruft this time around.

I am trying to make a pared down audio centered install...that can run a minimal X session using fewer deamons, and the full capacity of my 64x2 hardware or run high end video if I so desire. I like to be able to run some dual monitor as the onboard ati that I have has dvi and rgb. Really nice if you are running cut and paste audio editing sessions. So having a working ati driver is a must for this. Not to mention that the ability to play BlueRays on a large lcd is rather nice.

---

