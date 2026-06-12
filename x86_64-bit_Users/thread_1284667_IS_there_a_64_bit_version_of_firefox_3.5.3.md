---
title: "IS there a 64 bit version of firefox 3.5.3?"
date: 2009-10-06
forum: x86 64-bit Users
---

### Post by noob5000 on 2009-10-06
does anybody know IF i can get a 64 bit package of firefox 3.5.3?
(if yes, where?) 

all i found was 32 bit versions.... and yes i used google, i actually spent 6 hous on it - without any success. now i am confused because i do not know if maybe there simply is no 64 bit version at all.

---

### Post by Arup on 2009-10-07
Its in your repo and its called Shiretoko.

---

### Post by lavinog on 2009-10-07
what is wrong with [firefox-3.5](apt:firefox-3.5)?

---

### Post by noob5000 on 2009-10-07
> **Arup said:**
> Its in your repo and its called Shiretoko.
aaah thanks!
after reading your answer i realized that the "about" lists it (having installed shiretoko is one of the many waste products of yesterdays agony) as amd64 unlike all branded 3.5.3 versions i got via ubuntuzilla, synaptic, mozilla.com etc. 
now i must only solve the automatic upgrade problem and the classical "clicking a link in thunderbird does not open firefox" problem :-? lol

> **lavinog said:**
> what is wrong with [firefox-3.5]("apt:firefox-3.5")?
only the small fact that it results in a 32 bit firefox installation which is flash-incompatible on my 64 bit system (thus, in 2009, it is internet-incompatible)

---

### Post by Arup on 2009-10-07
Shireteko updates automatically, for handling links in Shireteko, under preferred apps, select custom and in command put  shireteko -newpage %s

---

### Post by noob5000 on 2009-10-07
the solution presented in the first post [HERE]("http://ubuntuforums.org/showthread.php?t=1227602") did it for me, now it works like a charm.
thank you very much for your replies!!!

i know help vampires suck donkey balls - i just can't help being a linux-noob at the moment. but i'm learning... and faster than i did with dos back in the stone age or windows over the past 9 years.

---

### Post by lavinog on 2009-10-07
> **noob5000 said:**
> 
only the small fact that it results in a 32 bit firefox installation which is flash-incompatible on my 64 bit system (thus, in 2009, it is internet-incompatible)

It installed the 64-bit version on my system (jaunty).  The about page refers to it as shirekoto, and I don't have a shirekoto package in my repositories.
The 64-bit alpha flash works just fine with it too.

What is telling you that it is the 32 bit firefox?

---

### Post by noob5000 on 2009-10-07
the "about" function under "help" in the menu (the thing  of which you posted a screenshot) showed "i686" in the version string.
 i just could (and can, lol) not understand why on a 64 bit system all 64 bit managers i tried (including both synaptic versions) would download & install a 32 bit version, even more when a 64 bit version DOES exist... and being not experienced enough to install programs via terminal on my own terms, all attempts of copy/pasting code from threads here and other sources (blogs & websites i googled) resulted in 32 bit firefox again, every single time, no matter what i did. 
and then of course the flash problem which comes with the 64-system/32-browser misconstellation...
i messed about with the system so much, de- and reinstalled so many packages that i lost confidence in the system's integrity. so i finally did the classical windows-move: getting some sleep and then rebuilding the system from scratch (new installation and proper configuration from start). 

now finally everything works, i'm all set for my every-day-tasks and thus ready to explore more linux depths freely.

---

### Post by lavinog on 2009-10-07
can you post the output of 
```
uname -a
```

---

### Post by noob5000 on 2009-10-07
why certainly:
```
Linux [name] 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:48:52 UTC 2009 x86_64 GNU/Linux
```

---

### Post by Thelasko on 2009-10-07
I would say the best source for up-to-date Firefox in Ubuntu is the [Mozilla PPA.]("https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa")

---

### Post by Arup on 2009-10-07
The only problem with the ppa is that its daily build, so almost ever other day new beta.

---

### Post by quequotion on 2009-10-08
Why not get an optimized compile of swiftweasel?

[http://swiftweasel.tuxfamily.org/](http://swiftweasel.tuxfamily.org/)

There's not a convenient .deb on the main site, although you don't have to compile it from source, but if you really need one they have been known to come up from time to time in one forum or another.

---

