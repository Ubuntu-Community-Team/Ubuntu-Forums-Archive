---
title: "To 64 or Not to 64...."
date: 2006-12-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by RockoTDF on 2006-12-26
In the very near future I will be building an AMD64 machine.  I have an ibook I will be doing "desktop" stuff with, and this machine will have an XP partition for gaming.  On the linux side of things I will be enjoying the challenge of linux, probably doing some gimp, and a backup/fileserver thing for my room.  I will also be Folding.  (Folding at Home is a distributed computing project by stanford used in medical research [www.folding.standford.edu](www.folding.standford.edu)) So if any of you fold, do you notice an increase in performance running the 64 bit over the 32 bit?

---

### Post by pay on 2006-12-27
I think that applications load slightly quicker but it isn't really noticeable. The main problem with amd64 is the lack of support from proprietary  companies, like adobe and flash.

---

### Post by Unterseeboot_234 on 2006-12-27
There IS a lack of software. Experiments to build from source files have consumed days with no end results. For me, I noticed a dramatic improvement using 64-bit over 32-bit running on an AMD Athlon 1300+. Because of my experiences running ubuntu on that old machine I ordered the AMD64 X2 with 128cache / skuzzy drive, PCIe video card with onboard sound. 

1. DSL -- mainly downloads, some improvement in uploads. 
2. 12- minute install from Live-CD. Turned out to be a big bonus. I've reinstalled now for the fourth time, BUT this install there is a backup of the /home, ~/, /ect, /opt, /dev when I install a group of software.
3. Kino, AFTER configuring all of its dependecies for my hardware configuration -- the 1394 driver -- records dv video effortlessly. Never drops a frame.
4. Blender handles a fair, good-size set of models with thousands of polygons and renders a 30 second animation in 25 seconds.
5. java compiles classes as soon as I click javac. I'm comfortable that my java programs will run on just about anything out there that has JRE, java plugin or jini.
6. Burning a DVD is now a half hour job, not hours and hours.

All-in-all, I think I have a superior graphics workstation compared to anything available. I'm still learning. I'm still looking for that killer ap game that pushes this machine.

---

### Post by ernstblaauw on 2006-12-27
I read [somewhere](http://www.ubuntuforums.org/showthread.php?t=318743) 64-bit is about 20%-30% faster than a 32-bit installation on the same processor. However, you will come across dificulties, as sometimes there are only packages for 32-bit. Therefore, I run a 32-bit installation on a 64-bit proc (Athlon64 3000+).

---

### Post by Kilz on 2006-12-27
> **Unterseeboot_234 said:**
> There IS a lack of software. Experiments to build from source files have consumed days with no end results. For me, I noticed a dramatic improvement using 64-bit over 32-bit running on an AMD Athlon 1300+. Because of my experiences running ubuntu on that old machine I ordered the AMD64 X2 with 128cache / skuzzy drive, PCIe video card with onboard sound. 

1. DSL -- mainly downloads, some improvement in uploads. 
2. 12- minute install from Live-CD. Turned out to be a big bonus. I've reinstalled now for the fourth time, BUT this install there is a backup of the /home, ~/, /ect, /opt, /dev when I install a group of software.
3. Kino, AFTER configuring all of its dependecies for my hardware configuration -- the 1394 driver -- records dv video effortlessly. Never drops a frame.
4. Blender handles a fair, good-size set of models with thousands of polygons and renders a 30 second animation in 25 seconds.
5. java compiles classes as soon as I click javac. I'm comfortable that my java programs will run on just about anything out there that has JRE, java plugin or jini.
6. Burning a DVD is now a half hour job, not hours and hours.

All-in-all, I think I have a superior graphics workstation compared to anything available. I'm still learning. I'm still looking for that killer ap game that pushes this machine.

The difference in packages is only 2%. You have to then take into account old applications that most people will not use, obsolete packages because your hardware is different,  then look at the sticky to find the work arounds that exist, and do some forum searches. After all that you will find the package difference is less than 0%. This is because , if you know how to do it, you can install i386 packages.

---

### Post by kleeman on 2006-12-27
There was a benchmark comparison recently here between 32bit and 64bit and the biggest gain in 64bit was with cpu intensive apps like databases and scientific apps. Folding may fit into that category since presumably it is numerically intensive.

---

### Post by RockoTDF on 2006-12-27
> **kleeman said:**
> There was a benchmark comparison recently here between 32bit and 64bit and the biggest gain in 64bit was with cpu intensive apps like databases and scientific apps. Folding may fit into that category since presumably it is numerically intensive.

That is what I had hoped to hear.  I also want the challenge of all this cross platform force compiling etc since linux will not be my desktop os.

---

