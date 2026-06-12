---
title: "Unable to proceed past login page"
date: 2009-11-01
forum: x86 64-bit Users
---

### Post by rbvendetta on 2009-11-01
Hi,
I'm new to Linux and Ubuntu and Ive been having difficulties getting started. I installed version 9.10 64bit, the installation went smoothly however as soon as I click my account on login screen the box becomes distorted... kinda glitchy looking. If I stay at the login screen and refrain from clicking the box I can access the terminal. I tried loading through safe graphics mode through a live-cd boot and didn't encounter any problems. I'm wondering if the issue is about not having the right driver for my Nvidia graphics card? Other distro's had the same problem for me in that the background seemed to "glitch" up.

I apologize for my general computer naivety. Any help would be very appreciated.

---

### Post by rbvendetta on 2009-11-01
Oh! I should note that once the screen becomes distorted the system is completely unresponsive and hangs.

---

### Post by The Funkbomb on 2009-11-01
Welcome to Ubuntu and the site.

Tell us more about your system.  Since this sounds like a graphics card problem, what graphics card are you using?  Sometimes being a bit more specific can help people narrow down a problem quicker.

While I've never had this problem, I think the solution would be to boot into safe graphics mode and install the correct drivers for your video card.

Go to System>Administration>Hardware Drivers.  It should scan your hardware for a few seconds and then pop up with a list of suitable drivers.  Find the one that pertains to your video card and if you have multiple options, choose the one that says recommended.  After it installs, it will require a reboot and with any luck, you'll be able to boot normally.

---

### Post by rbvendetta on 2009-11-01
Its an Nvidia Geforce 7800 w/ 256mb. I booted via live-cd and activated "NVIDIA accelerated graphics driver (version 185)" it requested that I restart and when I attempted to login (HD boot) it glitched again. Would changing my desktop environment help?

---

### Post by pstickar on 2009-11-01
Hoi! I think I have the same problem, albeit intermitently. Some times a boot ends up with a hang at the login screen. Most boots succeed. No problem in sleep mode.
This is a Hewlett Packard Elite book 2530p, with a graphics card "Mobile Intel Graphics Accelerator 4500MHD" which uses up to 384MB of shared system memory (8GB).

Does anybody knows if it is possible to recover a log or something of the boots that hang?

En Gruess,
p.

---

### Post by timgood on 2009-11-01
Any changes you make in a live-cd session will only affect that session, not the hard drive. Boot normally and when you reach the login screen press CTRL+ALT+F1 which will give you a text-based login screen. Then login with your username and password and type sudo dpkg-reconfigure xserver-xorg and follow the prompts. Hope this helps.

---

