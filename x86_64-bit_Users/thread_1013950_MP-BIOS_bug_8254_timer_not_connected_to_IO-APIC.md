---
title: "MP-BIOS bug: 8254 timer not connected to IO-APIC"
date: 2008-12-17
forum: x86 64-bit Users
---

### Post by Roger Gundberg on 2008-12-17
I purchased a new emachine that had Vista on it and replaced with 8.10 64 bit. I looked at Sysinfo only to find I have one CPU ! Is this a M$ issue? Will there be a modification to the kernal to fix this? I feel like I've hitched a race horse to a plow! 
Warmest Regards'
Roger Gundberg

---

### Post by Kevbert on 2008-12-17
In Ubuntu, using terminal, enter the following command and post back the result:
```
sudo dmidecode | grep Processor
```
Please also post the exact model of eMachine PC.

---

### Post by Roger Gundberg on 2008-12-19
Processor Information
    Type: Central Processor
    Version: New Processor Technology
    String 1: AMD New Processor Technology
Laptop Model D620
Warmest Regards
Roger Gundberg

I Googled the MP-BIOS bug and I was just concerned that this machine was not running at potential.I don't like to put out good money just to find out I have half of a computer.
Sorry about the siingle CPU bit I was thinking of my desk top that has a AMD dual core .Sheesh!

---

### Post by Kevbert on 2008-12-21
Please take a look at this [[COLOR="Red"]post[/COLOR]]("http://ubuntuforums.org/showthread.php?t=191355"). There are a couple of solutions mentioned there to resolve the problem (the kernel mentioned is an old one but the solutions should still work). 
If you want to speed up the PC you may want to max out the memory to 2Gb (I believe you have only 1Gb by default).

---

