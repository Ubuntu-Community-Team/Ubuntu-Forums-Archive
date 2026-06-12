---
title: "Nvidia driver crashes"
date: 2006-02-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by joker71 on 2006-02-26
<B>Hi there,

I just installed the Nvidia drivers as per the instructions on this site in a thread and now I am experiencing severe lock-ups. I have to power down via the power button. Is anyone else having this problem? My card is a GeForce 6600 PCI 16x Express 256MB. Thanks..:) </B>

---

### Post by Stinger on 2006-02-26
I, having the same trouble with my geforce 6600 128MB AGPx8
I don't think you are doing anything wrong , I think the problem can have one of two reasons.

Either it's related to the nVida driver , or it's related to the card itself.

If it's driver related it will (most likely) be solved in a future release from nVidia.

If it's related to the card itself , it can probably be solved by flashing the bios on the graphics card with a bios from an other make and model.
I have succesfully done this with my FX5600 card which had some wheird freezes.

But before flashing anything (it's a dangerous operation , in worst case your graphics card will be useless) we need to be sure.

So , is there anyone who has a geforce 6600 which works using the nVidia driver ?

Or can anyone else confirm this issue ?:-k 

Until then we'll just have to use the nv driver which is installed as part of your Ubuntu installation. :-|

---

### Post by thomasleveil on 2006-02-26
Well kind of !
*I have the NVidia GeForce 6600 XFX 256DDR and an AMD 64 x2*
I had it working on Breezy 64bit. But this weekend, I installed Breezy 32bit, updated to the latest nvidia drivers as described [here]("https://wiki.ubuntu.com/NvidiaManual?highlight=%28nvidia%29%7C%28drivers%29"). 
It works well right after the install, but don't survive any reboot. 
Now and untill I find a solution, I do the following at each boot from the console:
```
export CC=gcc-3.4
NVIDIA-Linux-x86-1.0-8178-pkg1.run
sudo /etc/init.d/gdm restart

```

---

### Post by thomasleveil on 2006-02-26
Ok, It's working for me now. (found solution [here]("http://ubuntuforums.org/showthread.php?t=128751"), it was a conflict between the nvidia drivers installed with Synaptic, and the one I downloaded from [www.nvidia.com/linux]("http://www.nvidia.com/linux"))

So, what driver have you installed ?
[LIST]
[*][with synaptic]("https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia")
[*][from the latest nvidia driver]("https://wiki.ubuntu.com/NvidiaManual?highlight=%28nvidia%29%7C%28drivers%29")
[*][with automatix]("http://ubuntuforums.org/showthread.php?t=66563")[/LIST]

---

### Post by joker71 on 2006-02-28
**I got the one from apt-get, there was a script that I came across in a thread. If there is a conflict should I wait for Ubuntu to fix it? The Nvidia driver from thier web site won't install for some reason. Thanks.**

---

