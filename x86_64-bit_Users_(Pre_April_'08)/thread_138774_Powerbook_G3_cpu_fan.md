---
title: "Powerbook G3 cpu fan"
date: 2006-03-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by jdcope on 2006-03-02
I have done some searching, and I can't seem to find anything relating to getting the Powerbook cpu fan to work under Ubuntu.

Is there a setting or something I need to change? 

I nuked the OSX install, so I cant go back and check if the fan was working with OSX. 

Any other ideas?

This Powerbook doesnt seem to get REAL hot, but it gets hot. And I have not noticed the cpu fan running once since I installed Ubuntu.

BTW, I am a new Linux user, and I am used to using XP. I bought this Powerbook really cheap a few weeks ago, my first Apple product. And when I found out there was a Linux release for PPC, I had to check it out. I figured if I had a learning curve, I would rather learn Linux.

Thanks

---

### Post by jdcope on 2006-03-07
Wow, nobody has an answer for this?

---

### Post by ssam on 2006-03-07
on my G4 the fan comes on when it gets too hot. it did not need any setting up.

i think on machines where that fan control does not work properly in linux the result is that the fan stays on constantly.

the G3 is quite an energy effiecient chip, so maybe it rarely needs the fan?

you could have a good google around and see what you can find. the the powerpc linux would it is customary to refer to a powerbook model by the number you get when you run
```
cat /proc/cpuinfo
```
mine is a PowerBook3,5. that may help with your search.

---

### Post by Ptero-4 on 2006-03-07
Best advice. If you can, install OSX and OS9 on your box. That way you can tell if the fan is faulty, or if it was a bad config what prevents it from running under linux.

---

### Post by jdcope on 2006-03-08
Thanks guys. I will check the cpu, and do some Googling. I didnt get any discs with this laptop, and since I got rid of the OSX install, I wont be able to check that way. But hopefully I will come across something.


Btw, Ptero-4, that has to be the best sig line I have ever seen!
I bet you could make a fortune selling t-shirts with that on it...

---

### Post by Ptero-4 on 2006-03-08
Yea. jdcope. It's a kewl sig, I found it somewhere on the web and only made some modding (It was from the days of Win98).

---

### Post by fungi on 2006-03-09
i get no love from my powerbook 12" fan.... thinking of getting one of those usb fans :)

if you are lucky you should be able to play with /sys/devices/temperatures according to 
[http://ubuntuforums.org/showthread.php?t=81744&highlight=fan](http://ubuntuforums.org/showthread.php?t=81744&highlight=fan)

but i think on my powerbook this will not work because i have no /sys/devices/temperatures :(

check /var/log/dmesg for somthing like

[   26.749074] PCI: Cannot allocate resource region 2 of device 0000:00:10.0

i think that is what is causing my grief, but im not sure.

anyone have any better ideas? somthing to do with the therm_adt746x module?

---

### Post by jwbaker on 2006-03-09
The PowerBook G3 is very efficient and the CPU fan will never come on in normal use.  I just got finished watching 4 episodes of Battlestar Galactica, encoded with XviD4, on my Pismo and it's not even warm.  Also I have 90 minutes of battery time remaining :cool: 

If you're just dying to hear your CPU fan, try the command "openssl speed".  This should exercise the CPU plenty, but even then, I wouldn't expect the fan to engage for at least 5 minutes.

---

### Post by jdcope on 2006-03-10
Well, I don't ***need*** to hear it. I was just concerned it might not be working at all. Seems its normal.

Thanks

---

### Post by Onkel Schnitzel on 2006-04-22
I just want to add that on my 12" Powerbook (1,5 GHz), the cpu fan also doesn't work. No problem under OSX, but while I have Ubuntu 5.10 running, the fan never starts, so in the end the Powerbook gets really hot. I've been searching for a while how to fix it but didn't find anything yet.

---

