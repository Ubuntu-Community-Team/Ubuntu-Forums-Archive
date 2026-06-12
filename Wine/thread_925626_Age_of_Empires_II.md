---
title: "Age of Empires II"
date: 2008-09-20
forum: Wine
---

### Post by Katakana on 2008-09-20
Hi, im pretty new using Ubuntu and one of the first things ive tryed is making Age of Empires II working.
I installed with wine and used a no cd crack, but when i start the game this is what it looks like 

[[IMG]http://img227.imageshack.us/img227/7827/ageofempiresmesseduprr9.th.png[/IMG]](http://img227.imageshack.us/my.php?image=ageofempiresmesseduprr9.png)[[IMG]http://img227.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

how can i fix this?

---

### Post by pytheas22 on 2008-09-20
Which version of wine are you using?  Age of Kings works fine for me using whichever version of wine is current on Hardy.

It may help to turn off desktop effects, and to adjust your screen resolution in Ubuntu to whatever it needs to be in Age of Kings before starting Age of Kings--possibly the problem is caused by wine not being to adjust the screen resolution properly.

Also, did you try just clicking on the menu items on that screen?  Maybe just the background image is distorted, but everything else would work correctly if you just clicked on it.

Another way to run Age of Kings is in a virtual machine; it works flawlessly and effortlessly there, so you may want to look into that if you have enough resources to run a virtual machine (really you don't need very much to run Windows XP).

---

### Post by Katakana on 2008-09-20
Im using wine 1.1.5.
The desktop effects is turned off and adjusting the screen resolution did not help, also clicking on the menu items did not change anything.

Im thinking, cant this be a graphic problem? Maybe i need the graphic drivers?

Thanks for your time.

---

### Post by pytheas22 on 2008-09-21
I have wine 1.0.  Yes, it's probably a graphics problem.  What kind of video card do you have, and are you using the proprietary drivers for it if applicable?

---

### Post by Katakana on 2008-09-21
Hi, my graphic card is Nvidia Geforce 8600M GT.
> and are you using the proprietary drivers for it if applicable? 

How can i check that?

---

### Post by pytheas22 on 2008-09-21
> **Katakana said:**
> Hi, my graphic card is Nvidia Geforce 8600M GT.


How can i check that?

Do you remember installing any proprietary drivers?  If not, you're using the open-source driver, which is what Ubuntu uses by default.  If you want to install the closed-source driver (which is the only one that supports 3d-acceleration), the easiest way is to use [envy]("http://albertomilone.com/nvidia_scripts1.html").  I'd give that a try, then see if Age of Kings works any better.

---

### Post by Katakana on 2008-09-21
Yes that is installed, but i thought i maybe need something else?
Maybe some other drivers?
Im going to use Envy anyways and see if that helps.

I have another question, do you think its possible to play AOK&AOC multiplayer on IGZones?

---

### Post by pytheas22 on 2008-09-21
If you already have the closed-source nvidia driver installed, I don't know if envy will help, but I guess it probably can't hurt.
> 
I have another question, do you think its possible to play AOK&AOC multiplayer on IGZones? 

Maybe.  I know I installed the IGZones client once and it ran fine--I was able to connect and join games.  I don't think I ever actually played, however, because I couldn't figure out how to get patch 1.0e installed--whenever I tried to run the installer it would say, "Age of Empires II is not installed on this computer" or something like that.  But I had a pretty cracked up version of AOE2 at that time, so I think that that was the problem more than wine--I don't think my version would have worked even on a real Windows computer.

I have played multiplayer games inside a VirtualBox virtual machine without a problem, so you may want to look into that.  It works flawlessly on IGZones as long as you [configure host networking]("http://ubuntuforums.org/showthread.php?t=346185") and make sure the ports on your router are forwarded correctly.

---

### Post by Katakana on 2008-09-21
Sounds promising.
I have now reinstalled Ubuntu and im going to make a new install of wine and AOK&AOC and IGZones.
I have two questions:
1. Wthich wine version should i use this time?
2. While installing AOK last time i got a message saying that Directplay 6.1a was not installed, should i do anything about that?

---

### Post by pytheas22 on 2008-09-21
1. I'd use whichever version of wine is in the Hardy repositories (should be 1.0), as that's the one that works for me.  You can install it with:
```

sudo apt-get install wine
```

Don't compile using the source on the wine website, as that would give you a different version.

2. I think it will install DirectX automatically if you don't have it.  If not, it should be on the AOK CD, or you can download it from the Internet.

---

### Post by Katakana on 2008-09-21
Ok after installing AOC with Wine 1.0 it seems to work,
BUT its very slow when playing, even when im running it on low graphics, so i dont know, maybe this is the best i can get with wine?

---

### Post by pytheas22 on 2008-09-21
Was it slow before?  The gameplay for me was definitely slower in wine, although it wasn't bad enough to be unacceptable.  If it's really bad for you, then maybe you should  try using the more recent version of wine available on the wine website.

Or--I know I've said this before, but I really think it might be the best option for you--just create a virtual machine and run AOE in that.  It will take maybe an hour to set the VM up (most of the time will be spent installing Windows into the VM), but after that you'll be able to run Windows applications very easily.  As long as your computer has at least a gigabyte of memory, you should be able to run Windows XP or lower in a VM at very zippy speeds.  A Windows VM is handy not just for AOE but for all those other times when you need to run some Windows program and don't have the time or energy to deal with figuring out why wine can't run it just quite right.

---

### Post by Katakana on 2008-09-21
> **pytheas22 said:**
> Was it slow before?  The gameplay for me was definitely slower in wine, although it wasn't bad enough to be unacceptable.  If it's really bad for you, then maybe you should  try using the more recent version of wine available on the wine website.

Or--I know I've said this before, but I really think it might be the best option for you--just create a virtual machine and run AOE in that.  It will take maybe an hour to set the VM up (most of the time will be spent installing Windows into the VM), but after that you'll be able to run Windows applications very easily.  As long as your computer has at least a gigabyte of memory, you should be able to run Windows XP or lower in a VM at very zippy speeds.  A Windows VM is handy not just for AOE but for all those other times when you need to run some Windows program and don't have the time or energy to deal with figuring out why wine can't run it just quite right.


Ok im sold, im going to create a virtual machine.
Where can i find instructions to do that?

---

### Post by pytheas22 on 2008-09-21
[This page]("https://help.ubuntu.com/community/VirtualBox") is a good place to start.  The guide there shows you how to install Ubuntu into your virtual machine, but it should be relatively easy to convert the instructions for installing Windows instead.  Let me know if you need help.

---

### Post by Katakana on 2008-09-21
> **pytheas22 said:**
> [This page]("https://help.ubuntu.com/community/VirtualBox") is a good place to start.  The guide there shows you how to install Ubuntu into your virtual machine, but it should be relatively easy to convert the instructions for installing Windows instead.  Let me know if you need help.

Ill give it a shot and tell you if i need help.
Thank you for helping.

---

