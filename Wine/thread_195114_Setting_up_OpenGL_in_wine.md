---
title: "Setting up OpenGL in wine"
date: 2006-06-12
forum: Wine
---

### Post by Iesos on 2006-06-12
Hi, I having some difficulties running Warcraft 3. I have several games running flawless in wine (Diablo 2, Starcraft, Fallout and others), but running warcraft 3 is too slow. I have seen in other threads on this forum that one needs opengl to run it smooth. So I tries what all recommend:

> wine War3.exe -opengl

But that didn't help. All that did was to change my resolution and crash, with the following outprint:

> 
err:ole:CoCreateInstance apartment not initialised
fixme:win:EnumDisplayDevicesW ((null),0,0x55ddef50,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x55ddef88,0x00000000), stub!
X Error of failed request:  BadLength (poly request too large or internal Xlib l ength error)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  29 ()
  Serial number of failed request:  574
  Current serial number in output stream:  574


(Thats the part of the outprint that differs from the one I get witout the -opengl flag)

And these are like hieroglyphs to me. Anyone know any tips (cedega is NOT what i'm looking for!) how to get this working?

---

### Post by Iesos on 2006-06-13
Ok, I solved it myself.
If anyone encounter this problem this is the solution:
You are probobly running a AMD64 system, with wine in a 32-bit chroot.
If so (or if you have AMD64 ubuntu), install wine according to this HowTo:
[http://www.ubuntuforums.org/showthread.php?t=185557](http://www.ubuntuforums.org/showthread.php?t=185557)

That worked great!

---

### Post by Derrkus on 2006-07-13
Actually you can run opengl apps in 32 bit chroot with wine. I solved that BadLength problem by installing my graphicscard drivers inside the chroot. I've got a nvidia card so I just did:```
sudo apt-get install nvidia-glx
```Now World of Warcraft works great in my 32 bit chroot! :D

---

### Post by slink3r on 2008-05-01
I'm sorry, did you use vmware to accomplish this?

wine compiled on what did you use to install vmware onto your computer?

to avoid having the wine DLLs failing interaction with the nvidia drivers would probably be the case if you tried to use the windows install program to install the "real" drivers, right?

---

### Post by Perfect Storm on 2008-05-01
Necromancing.

Thread closed.

---

