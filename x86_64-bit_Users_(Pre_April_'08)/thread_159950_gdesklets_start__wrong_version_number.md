---
title: "gdesklets start / wrong version number?"
date: 2006-04-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by BjornHaland on 2006-04-13
I just downloaded gdesklets (using synaptic) after following Artificial Intelligence's guide [here]("http://ubuntuforums.org/showthread.php?t=77694").

I then attempted to start gdesklets, but nothing happened..
Then I searched around abit and someone got me doing:
```
gdesklets start
``` All good, but:
```
$ gdesklets start

You're running gDesklets for the first time.
gDesklets will start a requirements check now...

Checking requirements:
 - sys ... found
 - xml.parsers.expat ... found
 - xml.sax ... found
 - gtk ... found
 - ORBit ... found
Version check failed.

ORBit python bindings (pyorbit) version == 2.0.1 are required.

Please make sure that the required software is installed.
Also try to avoid having multiple versions of a library/binding on your system.
gDesklets won't work if you don't have all necessary dependencies installed
on your system.

THE STARTUP WILL BE CANCELLED NOW!
``` 
Now I'm stuck ](*,)

Edit: Figured it out, for your information. Try restarting the computer! I guess I must have been tired or something.

---

### Post by KrustybRuffle on 2006-04-16
I just found this in another thread, try typing gdesklets in a teminal window, (without the start). When I did this it started the gdesklets shell & it seems to be working fine now, & it now starts from the applications menu :)

I guess it's a weird bug or something that has already been filed, but this simple workaround fixed it for me.

---

