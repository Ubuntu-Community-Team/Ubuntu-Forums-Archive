---
title: "Multiple Wine versions"
date: 2007-10-25
forum: Wine
---

### Post by eman7613 on 2007-10-25
I tried to post in the most appropriate section possible, and as i would not consider myself a "noob" at unix based systems in general (although i am indeed a grammar "noob"), i felt it appropriate to post here.

Basically, what i would like to do it run multiple versions of wine on the same machine (with instances & threads from both at the same time) ie:
--Cinema 4D running under 0.9.47
&&
--World of Warcraft running under 0.9.46

if this is not something that can be achived, it would also be nice to have something similar with java, were i can use update-alternatives to select on of the many JREs i have installed for testing purposes. 

if anyone can provide some useful insite, im listening :)   (been fudging with this horribly 4d form of a intoxicating beverage for 5 hours now, far longer then i like just to get my feet wet!:lolflag:)

---

### Post by upbeat.linux on 2007-10-26
There is a wonderful little app called winestart which is available here:

[http://www.david-guembel.de/index.php?id=13]("http://www.david-guembel.de/index.php?id=13")

However, the only caveat being, you will have to remove your current Wine install and compile with source using the appropriate options _(please correct me if I am wrong_).

Make sure you read the "Usage" section on David Guembel's page as well as the Wine user guides and associated README/INSTALL files.

---

### Post by eman7613 on 2007-10-26
thank you very much! exactly what i needed & ment (reading back on mine even i had trouble fully understanding)

for anyone else who uses this and gets a little fumbled by the command line, you need to do something like ~/scripts/winestart_01.pl --command
for it to run, you cant jsut cd to the directory and type it in, dont know why, but selavi. thank you very much!

---

### Post by soxs on 2008-06-08
Can anyone give me the compile options i need to use ind order to compile a "secondary" wine build? thx

---

### Post by happyhamster on 2008-06-08
One way of using multiple wines is to run the wine script from within their source folders. 
So, compile the version you want, but don't install it (don't run "sudo make install" or "sudo checkinstall"). Then run wine directly from within the source folder (./wine /path/to/program.exe). 

Personally, when I want to switch to a different wine, I just re-install. Takes 30 seconds perhaps.

---

### Post by soxs on 2008-06-09
Reinstaling is the way I am currently going.. but it somewhat sucks..
Is there any option to give special prefixes or something like that?

---

### Post by david_kt on 2008-10-09
> **soxs said:**
> Reinstaling is the way I am currently going.. but it somewhat sucks..
Is there any option to give special prefixes or something like that?

It could be done very easily. Here is the answer to your question:

[http://ubuntuforums.org/showthread.php?t=942269](http://ubuntuforums.org/showthread.php?t=942269)

DK

---

