---
title: "Some Questions About the 64-bit environment"
date: 2007-04-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by sammyd253 on 2007-04-02
I have a few questions about the the 64 bit version of Ubuntu.

First off, I have a dual-core CPU, I've heard that to utilize both cores in the OS, it needs SMP support.  If I download the 64-bit Live CD off of Ubuntu's web site, will this version have SMP built into it?  How can I verify that it's correctly detecting my CPU once I am in Linux?  Also, is there anything extra I need to install/configure to get AMD Cool N' Quiet working?  How can I monitor this as well?


Second, if I am running the 64-bit OS and want to install a game such as Unreal Tournament 2004, will this work properly since it's a 32-bit application?

Thanks in advance for the help!

---

### Post by kuja on 2007-04-02
> **sammyd253 said:**
> I have a few questions about the the 64 bit version of Ubuntu.

First off, I have a dual-core CPU, I've heard that to utilize both cores in the OS, it needs SMP support.  If I download the 64-bit Live CD off of Ubuntu's web site, will this version have SMP built into it?  How can I verify that it's correctly detecting my CPU once I am in Linux?  Also, is there anything extra I need to install/configure to get AMD Cool N' Quiet working?  How can I monitor this as well?


Second, if I am running the 64-bit OS and want to install a game such as Unreal Tournament 2004, will this work properly since it's a 32-bit application?

Thanks in advance for the help!
- SMP support is built in.
- check the file /proc/cpuinfo
- It should work right off the bat, and you can monitor it by monitoring /proc/cpuinfo (there are a wealth of frontends for doing so graphically also)

- It should work fine

---

### Post by maxamillion on 2007-04-02
> **kuja said:**
> - SMP support is built in.
- check the file /proc/cpuinfo
- It should work right off the bat, and you can monitor it by monitoring /proc/cpuinfo (there are a wealth of frontends for doing so graphically also)

- It should work fine

Only thing that might need to be done for UT2k4 is install the ia32-libs package (that is what its called in feisty, I forget the counterpart name in Edgy) but yes, it should run fine.

.... and I agree about everything else :)

---

### Post by sammyd253 on 2007-04-02
kuja, can you recommend any good front end CPU monitoring utilities if you know any?  if you're unsure it's no big deal.  I appriciate your help though.


and to maxamillion, how do you go about installing the ia32-libs package?  is this something i would be prompted to do during the UT2004 installation?

---

### Post by kuja on 2007-04-02
I usually check on such things with ksysguard/the-ksysguard-kicker-applet for load info. For monitoring most anything else I use superkaramba applets (I presently use a modified version of SuperMonitor). I know there's a ton of other stuff out th ere, but these things do work well, at least for me.

---

### Post by sammyd253 on 2007-04-02
I'm assuming that both of the apps you mentioned are for the KDE interface only?  I normally use Gnome but with some searching I'm sure I could easily find apps that do the same thing.

---

### Post by kuja on 2007-04-02
I'm not sure if they're for KDE only (well, the kicker applet probably is, unless you want to run kicker in Gnome). As for superkaramba, I don't know, it might run in Gnome, can't say I've ever tried.

---

### Post by sammyd253 on 2007-04-02
Ah ok.  Well I'll look into it more, thanks for your help though.

Ps - The specs listed in those screenshots look pretty nice :-D

---

### Post by Kilz on 2007-04-02
> **sammyd253 said:**
> I'm assuming that both of the apps you mentioned are for the KDE interface only?  I normally use Gnome but with some searching I'm sure I could easily find apps that do the same thing.

Yes gdesklets will basicly do the same thing . Its little applets than can monitor a variety of things.

---

### Post by sammyd253 on 2007-04-03
Sounds awesome, I will check it out.  Do you recommend using the Synaptic Package Manager to download and install this utility?

---

### Post by Kilz on 2007-04-03
> **sammyd253 said:**
> Sounds awesome, I will check it out.  Do you recommend using the Synaptic Package Manager to download and install this utility?

Yes its in synaptic. I recommend using it and apt whenever possible. Compiling things and getting debs outside of the repo's is always a last resort.

---

### Post by tj.milligan on 2007-04-03
> **sammyd253 said:**
> I'm assuming that both of the apps you mentioned are for the KDE interface only?  I normally use Gnome but with some searching I'm sure I could easily find apps that do the same thing.

FYI, Ubuntu has simple (aka MS Windows-like) CPU-monitoring built in. It's part of **gnome-system-monitor** and is installed by default. Run it by navigating to the *System* menu, then *Administration* > ***System Monitor***. Click the *Resources* tab and you'll see a live graph of CPU History and other devices. You can even change the colors of the line graphs to better differentiate between your two cores.

---

### Post by sammyd253 on 2007-04-04
Awesome, I will check that out.  I haven't gotten around to installing Ubuntu yet as I'm trying to get as much information under my belt before doing so.  I'm trying to set aside an entire day if I can to install the new OS so that if I do run into problems, I will have the time to try and fix it.  Thanks for the recommendation and I'll see how it goes once I have Ubuntu installed!

---

