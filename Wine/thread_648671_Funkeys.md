---
title: "Funkeys"
date: 2007-12-23
forum: Wine
---

### Post by Joseph_Schafer on 2007-12-23
There is this new toy out I am trying to install, named Funkeys. It requires a USB thingamajig that you put the funkeys into. For this to work I need wine to recognize it, and i need it recognized for the installation. It just wont work, wont find the usb drive. Any help is usefull.

---

### Post by cogadh on 2007-12-23
Funkeys requires a driver to work. Windows drivers can't be used in Linux, even with Wine.

---

### Post by Joseph_Schafer on 2007-12-24
Do you think that there will ever be an update in wine to get this to work? or will it work on a mac? My parents wont let me install on the windows.

---

### Post by cogadh on 2007-12-25
No, Wine will never be able to use Windows drivers (that's not how it works) and it won't work with Mac unless they have a Mac version.

---

### Post by Spr0k3t on 2007-12-31
There's no Mac version.  I'm sure if you want, you can send some feedback asking for Linux support.  I've seen what the games are like and the idea is quite cool.  I'd recommend the UBFunkeys but it requires Windows currently.

---

### Post by jwernerny on 2008-02-16
A few months ago, my daughter bought a U.B.Funkey.  At the time, I tried to get it to run under wine, but finally gave up.  Today, my son got another Funkey for his birthday, so i decided to try it again.  This time, I decided to make a brute force attempt.  On the kids machine, i have installed win2k running under VirtualBox.  I was able to install the Funkeys software on on the virtual machine.  After downloading the USB Driver Patch from the Funkey website, and installing it; I was able to start up the Funkeys software and have it recognize the Funkeys.  My daughter then spent about 30 minutes playing with them before being reminded that it was well past her bedtime.  YMMV[IMG]http://www.frontiernet.net/~flybrick/Funkeys.jpg[/IMG]

- John

---

### Post by Joseph_Schafer on 2008-02-19
Hmmmm, I dont have a windows CD, and I dont completely understand the way this virtual box works, can I get it working on a dos emulator though? maybe?

---

### Post by GeekyBeans on 2008-12-23
i have successfully gotten U.B. Funkeys to run in Wine, but the usb (U.B. Funkey) device will not detect.

---

### Post by Monkus on 2009-01-03
Hey,
How did you install without the driver. I am on vacation with my son and want to get this to run, but cannot get passed the driver installation to get to the software. Let me know how you did it if you get the chance. Thanks.

---

### Post by jvin248 on 2009-05-02
Running xubuntu 8.04 with wine 1.1.20 (newest available today) and the funkeys program disk will auto run but gets part way through, throws an error message, and ends.  I tried downloading the driver from funkeys' site and it tells me that the program is not installed and it won't load the driver.

I tried on an old win98 machine and it won't run there either (min specs per funkeys is win2000 or newer so I didn't expect much).

Is the only option left to buy a $150 Operating System to play an $8 toy?

So here I sit with a sad little boy that wants to play.

---

### Post by deadtom on 2010-01-02
I installed WinXP on a virtual box in kubuntu and I'm in the middle of installing the funkeys software. It's installing the driver and not detecting the funkey when I plug it in to the USB port.
If I go to "devices" in the virtual box and then to usb, it doesn't show any USB devices available. How did you get this to work?

---

### Post by jvin248 on 2010-01-03
Virtualbox has two versions .. The 'OSE' version is the default if you pull Virtualbox in through the K/X/Ubuntu package managers and the OSE version specifically does not have USB enabled (there may be a work around but I haven't looked).  

Their standard version from the Virtualbox site does have USB enabled.  

Licensing restrictions are the difference between the two versions.  Home use won't be a problem from what I saw.

---

