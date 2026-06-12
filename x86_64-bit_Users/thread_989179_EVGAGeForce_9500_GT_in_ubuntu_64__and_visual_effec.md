---
title: "EVGAGeForce 9500 GT in ubuntu 64  and visual effect"
date: 2008-11-21
forum: x86 64-bit Users
---

### Post by Deaflinuxgrl on 2008-11-21
For a while, I could not get my visual effect to work on my ubuntu x86_64. Even with the hardware drivers section of my ubuntu.  

I finally got it solved and thought others would like to know how to do it:

Download the latest EVGA GeForce 9500 GT driver from NVIDIA website 

Exit the x server: (Ctrl + Alt + F1) Type sudu /etc/init.d/gdm stop
go to the directory where your driver is located 

Then type sudu sh [driverfilename-the one you downloaded from NVIDIA].run 

enter xserver: /etc/init.d/gdm start

Go check your Hardward drivers to see if the new NVIDIA driver have been enable or can be enable (I couldn't do this before I installed the new driver), if so, it is working. 

(btw, I am a newbie so if you want to improve this set up go ahead.. I wasn't really afraid of taking a risk but others might)

---

