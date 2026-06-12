---
title: "Best Drivers for 7800GT?"
date: 2006-03-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by kuys on 2006-03-02
I was having drivers issues with strange graphical annomiles when the kernal would try to load the standard nv driver. I found a post in this forum with the same problem and corrected the crashing by using the vesa driver and the recovery boot. System is working fine now I was just wondering what drivers would be required to make full use of my videocard and what procedure would I have to attempt to gain those results? Please keep in mind I am new to the linux operating system. Thank you

---

### Post by RAOF on 2006-03-02
The proprietry, binary nVidia drivers are what you're after.  Only they will give you 3D support for your card.

Check out the "nVidia drivers" link in my sig, and bear in mind that you'll need to use the 8171 drivers (or newer) downloaded from the nVidia site.

---

### Post by kuys on 2006-03-02
Awesome thank you I'll try that right now.

Actually which method should I use from your guide? Also the standard windows drivers are what I'm after? Or the most up to date linux drivers off of the actual nvidia site?

Edit: Ignore above I belive I figured out my questions. Thanks again.

---

### Post by kuys on 2006-03-02
> 
Code:

cd &#8220;directory where you have the nvidia installer&#8221; su CC=gcc-3.4 export CC exit CC=gcc-3.4 export CC


I get stuck right here. After I boot to command line and type cd /home/matt (enter)
and then su(enter).
I get a pause then an error saying authentication error. Sorry. 

Any help?

---

### Post by gmontag on 2006-03-03
Use sudo instead of su.  Su acts as a root user and may need to be setup.

---

### Post by kuys on 2006-03-03
Thank you. I've got it to work but I can't ever seem to point to the nvidia package. I've tried placing it in my home folder and then cd'ing to it but all I can ever get to is /home which the file is in I belive cd /home/matt/desktop it continues to say no directory. I've tried putting the package in teh file system but for some reason I can't even make a single change to it. I can't even make a folder in my file system is there a way around this?

---

### Post by kuys on 2006-03-03
I got all the into the install of the drivers but it complains about the kernel compiler being gcc 4.0 and not gcc 3.4. I've followed the instructions for step 2 at least 10 times now and still can't get the drivers installed any help would be much appreciated. Also I've switched to the i386 version becase I read wine wouldnt' run in the AMD64 one. It's a fresh install if that helps any.

---

