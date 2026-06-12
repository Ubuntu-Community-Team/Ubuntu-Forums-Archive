---
title: "Ati 9600xt"
date: 2006-02-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by davidcrickett on 2006-02-04
I am a Linux newbie, but I installed Ubuntu 64bit without any trouble on my AMD 64 Athlon machine. Now my question is: Does Breezy Badger automatically recognize my ATI Radeon 9600XT or do I have to do some Ubuntu Linux voodoo. And if, what? :-k

I have found[ this thread]("http://ubuntuforums.org/showthread.php?t=24557&highlight=ati+radeon") for installing ATI Radeon on Hoary, but does this work for Breexy 5.10 also?

Hm... from the [ATI Linux FAQ]("ttp://www.ati.com/products/catalyst/linux.html"): " Systems using 32-bit processors from Intel (Pentium III and later) and AMD (Athlon and later) are currently supported. *64-bit drivers are under development, and should be available in a future release*. PowerPC, Alpha, and others are not currently supported."

So we 64bit users seem to be bleeding edge... or...?

---

### Post by Mnemonicman on 2006-02-11
It should detect the card just fine. I ran the live cd on a pc with a 9600xt and it ran fine.

---

### Post by davidcrickett on 2006-02-12
Instead of being scared away from the ATI drivers in the above link, I used this one (method 2) and everything went fine. Except for my login screen, which seems to be in a much bigger solution than my normal 1280x1024 - and the screensavers, which seems to have no connection whatsoever to the graphics card! :rolleyes:

---

### Post by nemodx on 2006-02-12
Is there ANYONE that got dual screens working? Is there a HowTo that doesnt screw up my install? I have tried 2 of them now, and they screw up my X-Server majorly.

I also have problems getting higher refresh rates than 60hz :( ANY help would be so very welcome.

Thanks in Advance,

Nemo DX Zimmer

---

### Post by newuser111 on 2006-02-12
if you want to install the latest drivers use this thread [http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

by the way, there was a new driver release in the past few days, the instructions to install are the same, but just substitute the file name accordingly

---

### Post by nemodx on 2006-02-12
Tried that, and suddenly my X was screwed. All I really want, is a higher refresh rate and dual screens. :(

---

### Post by alfonz on 2006-02-12
[QUOTE=newuser111]if you want to install the latest drivers use this thread [http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

by the way, there was a new driver release in the past few days, the instructions to install are the same, but just substitute the file name accordingly[/QUOTE]


I followed these steps a few days ago and WORKED like a charm. BTW I have an ATI 9600XT too so davidcricket your good to go. However I sugest you run the sudo fglrxconfig instead of the sudo aticonfig -- initial.

---

### Post by davidcrickett on 2006-02-12
Ah, forgot the link to ATI installation (I used method 2):
[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)
I can't find the resolution and MHz guide I used, but you do
```
sudo nano /etc/X11/xorgconf
```
(You can draw the file into the terminal window if you like - and remember save is control o ;) - didn't know, so I spent some time rummaging about)...
and change the 24 depth resolution to your screen size. As for the Hertz, your screen height and width is put in as a range say like 34-96 and 56-160 (you can find the specs of your card on the net) and voila, it finds 85 Hz or what rate your screen is in.

---

### Post by alfonz on 2006-02-12
did you use the Ubuntu fglrx drivers or did you create the Deb packages from the ATI installer?

One thing That i noticed with method 2 is it messed up couple of key on my keyboard and power management system ei standby doesnt seem to work.

But I will live with this untill there is a workaround, BTW the PowerButton on your monitor is your real screen saver anyway :D

minor glitches that i am in no rush to fix, something i will endure to use blasing FPS's finaly

---

### Post by davidcrickett on 2006-02-12
Sorry to hear that. Different solutions seems to work for different setups. I for one am very happy with the ATI drivers, but avoided them in the beginning as an advice told me to. But the method 2 did it for me. \\:D/

---

