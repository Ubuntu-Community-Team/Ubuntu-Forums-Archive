---
title: "nVidia Driver problem"
date: 2009-07-13
forum: x86 64-bit Users
---

### Post by firewarrior on 2009-07-13
I am trying to install the drivers for my nVidia graphics card and I can not seem to get it to install properly. I am running a 64 bit 3800 AMD Athalon with a Geforce nVidia 8600 GT in a PCI slot. Any help would be much appreciated or a thread on a how to. Thanks

---

### Post by JDShu on 2009-07-13
Not sure exactly what you've done so far, but you can should probably do the following steps:

1. Download the driver you need from the nvidia website.
2. Purge any nvidia drivers that maybe installed right now.
3. Run the file that you downloaded.

---

### Post by firewarrior on 2009-07-13
so far i've downloaded the necessary file for the card. I'm not too knowledgeable on the whole how to purge the old drivers and how to install the file that i downloaded from nvidia's site. i've been reading many many threads and none of them seem to be clear enough for me. I'm still wet behind the ears when it comes to linux. BTW i'm running Hardy if thats any help. Also I've gone into System -> Hardware Drivers and it says i have no proprietary drivers.

---

### Post by JDShu on 2009-07-13
Hmmm, I use Jaunty so I'm not too sure if this will work for you but this is what I would do:

1. CTRL-ALT-F1 to go to terminal.
2. sudo su (for super user privileges)
3. /etc/init.d/gdm stop (to close X)
4. apt-get purge nvidia* (to get rid of any lingering non-working nvidia drivers you may have installed)
5. sh <the driver you downloaded> (of course you need to be in the directory where you installed downloaded the file)
6. Follow the instructions and compile the module.
7. When you are finished, type reboot to restart.

Tell me if this works.

---

### Post by firewarrior on 2009-07-13
ok. everything seems to go fine until i get to the apt-get purge nvidia*. after hitting Enter it gives me the following messages: 
E: Could not open lock file /var/lib/dpkg/lock - open(13 permission denied)
E: unable to lock the administration directory (/var/lib/dpkg/), are you root?

also when i type in reboot it says i need to be in the root. not sure how to do this.

---

### Post by merlinus on 2009-07-13
You might try prefacing the commands with:

sudo

---

### Post by Vakman on 2009-07-13
> **merlinus said:**
> You might try prefacing the commands with:

sudo
Agreed. A purge command is unlikely to work without having sudo out in front :)

---

### Post by Vakman on 2009-07-13
Here is the link to a Howto for how to install 185.18 nVIDIA drivers. 
[http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400)
Should be helpful.

---

### Post by JDShu on 2009-07-13
Odd, I thought that the sudo su stage would give root privileges, oh well. Yeah as the others said use "sudo" in front of the commands that don't work because of lack of root privileges.

---

### Post by firewarrior on 2009-07-13
ok guys. i followed the tutorial that was posted. was following it to a tee. for some reason it keeps saying that the driver i downloaded is not for the system that i'm running. it say that i appear to be running just an x86 system instead of a x86 64 system. does anyone know what could be causing this conflict?

---

### Post by JDShu on 2009-07-13
Lets check the obvious first: Did you install the 64 bit version of Ubuntu? Even if your processor supports 64 bit, the OS needs to be the 64 bit version as well.

---

### Post by firewarrior on 2009-07-13
yes i made sure to install the 64 bit version. i got the live CD as a 64 bit, but just to be sure i did, how would i check to see what version i actually have on here?

---

### Post by firewarrior on 2009-07-13
just went and checked from the house computer and i installed the i386 version. whoops. maybe that might help. :(

---

### Post by JDShu on 2009-07-13
Haha guess you know what to do then. Just to answer your question, to check your architecture use:

```
uname -a
```

---

### Post by firewarrior on 2009-07-13
Linux Rob1 2.6.24-24-generic #1 SMP Tue Jun 30 20:28:53 UTC 2009 i686 GNU/Linux

I'll just follow the instructions from the tutorial and just add the changes and make it all good.

---

### Post by firewarrior on 2009-07-13
Thank you everyone for your help and input. It was all very helpful and useful. Problem solved. :D

---

### Post by Vakman on 2009-07-13
Not a problem, remember to mark the thread as solved :)
Glad it worked once you got past what architecture you had installed :P

---

### Post by freackout on 2009-07-13
> **firewarrior said:**
> I am trying to install the drivers for my nVidia graphics card and I can not seem to get it to install properly. I am running a 64 bit 3800 AMD Athalon with a Geforce nVidia 8600 GT in a PCI slot. Any help would be much appreciated or a thread on a how to. Thanks

try EnvyNG it will do all the hard work for you.

---

### Post by firewarrior on 2009-07-14
:d:d:d:d:d

---

### Post by punkybouy on 2009-07-15
Install EnvyNG which I think is in the repositories.  I have it on all of mine.  Run it from Applications\System Tools and it will install drivers for either Nvidia or ATI cards.

---

