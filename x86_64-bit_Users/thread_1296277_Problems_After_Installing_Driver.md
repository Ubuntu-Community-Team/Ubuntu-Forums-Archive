---
title: "Problems After Installing Driver"
date: 2009-10-20
forum: x86 64-bit Users
---

### Post by Jersey Legend on 2009-10-20
I was given a 9800gt a few days ago. Put it in, everything worked well. 

Last night, for no apparent reason, I decide to install what I thought was the latest driver for the card, on Ubuntu; again, for no reason. This is what I did:

ctrl+alt+f1 to exit x

on terminal:

$ killall gdm
$ sh NVIDIA-Linux-x86_64-185.18.36-pkg2.run

after it goes through the installation, I hit ctrl+alt+f7.
When the gui showed, it is horrrrrible quality. A pop up tells me that it is running the lowest configuration/colors etc.

I try to select manually through the list my monitor and video card. But nothing seems to work.

After trying to install about 5 more times, I restart and select restart x server. My screen resolution is much better now, but I know it is not picking up the resolution I was using prior to this problem. All my desktop effects have been disabled and whatnot.  wtf!?:confused:

Appreciate the help, if any.

---

### Post by Jersey Legend on 2009-10-20
Also, Im my other partition which is running Windows XP, the video card works great. I guess that's because I didn't f*ck it up by trying to install drivers it didn't need.


ANd I do have the cd that came with the video card, but it is at home, and I'm at school, so i have to wait till the weekend when I go back home to get it


edit: Well I managed to get all the resolutions to show up. Downloaded an app called Envy, it installs the proprietary drivers that are compatible with your hardware

$ apt-get install envyng-qt

Still trying to get the effects to work

---

