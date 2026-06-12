---
title: "Microsoft Lifecam VX-1000 webcam image quality is way off"
date: 2008-09-08
forum: x86 64-bit Users
---

### Post by nihilion on 2008-09-08
Dear Ubuntu world,

I am a 64 bit ubuntu user (hardy kernal), and am having trouble with my Microsoft Lifecam VX-1000 webcam. 
The device was detected okay and the driver appears to have loaded, but the color is way off and the image is very pixelated. 

In Cheese the image is totally overexposed and all orange in color. In one of the other video capture programs (can't think of the name at the moment and I am away from my comp at the moment) it is totally blue. Ekiga doesn't display anything at all. No color settings that I have found make a lick of difference.

Is it possible that I am having a driver issue? Anybody have an idea what is going on? 

Thanks for your help. 

Nicholas

---

### Post by nihilion on 2008-09-09
shameless bump

---

### Post by jespdj on 2008-09-10
I had a Microsoft VX-3000 webcam which had similar problems. I never found a way to make it work. I experimented with these [webcam drivers](http://mxhaard.free.fr/index.html) and finally gave up. I gave the webcam to my dad and bought a cheap Logitech webcam, which worked out of the box.

---

### Post by jesterthejedi on 2008-12-24
Working after 6 months of waiting and searching forums. My cam is the dreaded Microsoft VX-1000.

Do this:
Download driver:
[http://linuxtv.org/hg/~jfrancois/gspca/](http://linuxtv.org/hg/~jfrancois/gspca/)
grab the .bz2 file
extract and change directory
in terminal type "make" no quotes take about 5 mins
then type "sudo make install"
reboot

tested working on Intrepid With Cheese, Ekiga, Skype, GyachE, Xawtv

COLORS are fine! no more green/blue Hardy mess.
not working in Camorama, Camstream, errors in gqcam

installed xawtv, luvcview, and removed camserv.

I am so happy that I should pinch myself. I bought this webcam in June for my birthday and it was always a pain in the butt to solve. Success at last!

---

### Post by raspa_sete on 2009-03-17
Thank you so much jesterthejedi!

It is working fine for me!!! I still had to reboot the system for everything to work...

Cheers

---

