---
title: "Display problems :eek:"
date: 2008-03-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by GiPilot12 on 2008-03-16
I tried to get my computer to run on a projector, and I think I broke it instead :(

I went to:

Administrator--->display thing----> then set up the secondary display as my default.

 Now the computer will get to the part where it says "Kernal alive", then the loading screen will come up. Once the orange bar is full, the screen will go blank,  but then nothing will be displayed. (this is the part that usually is orange with the prompt for me to login)


 And when I plug in a second monitor, the same thing will happen except that instead of the orange screen prompting me for a username and password, a black "command prompt" style screen will show up and ask me for a user name and password. After I put that in, it gives me a bunch of crap of how Ubuntu has no warranty etc.

Please help




EDIT. I made a command (I forget what it is) but it basically tells me:

Gnome Display driver Stop    [ok]
Gnome Dispaly driver start [ok]

I think that this means that the video card isn't the problem./....

I did another command and it tells me this:
"Fatal server error: no screens found"

---

### Post by GiPilot12 on 2008-03-16
help??

---

### Post by Yellow Pasque on 2008-03-16
When you get to the blank screen, press Ctrl+Alt+F1, then run:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
That will reconfigure X. If that doesn't work, what video card do you have?

---

### Post by GiPilot12 on 2008-03-17
I have an ATI x1400

---

### Post by Yellow Pasque on 2008-03-17
Ok, press Ctrl + Alt+ F1 and run:
```
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial -f --video-overlay=Xv
```

If that doesn't work, you might need the latest Catalyst drivers from ATI. If your internet still works in terminal mode, you can get and install them from the command line with:
```
sudo apt-get install build-essential fakeroot dh-make debhelper debconf libstdc++5 dkms wget
wget --no-check-certificate https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8-3-x86.x86_64.run
sudo sh ./ati-driver-installer-8-3-x86.x86_64.run
```

---

### Post by GiPilot12 on 2008-03-17
THANK YOU THANK YOU THANK YOU!!!! :)

IT WORKS BEAUTIFULLY! 

People like you really make be believe in the spirit of Ubuntu! 

You have no idea how happy I am that you are here to solve my problems :)

OHHHH GOD you saved me (Or rather recovered me) 4 weeks of Extended Essay work :) ohh thanks thanks thanks :)

---

