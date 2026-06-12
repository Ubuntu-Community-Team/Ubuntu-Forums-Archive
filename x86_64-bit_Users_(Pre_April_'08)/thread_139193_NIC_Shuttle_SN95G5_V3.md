---
title: "NIC: Shuttle SN95G5 V3"
date: 2006-03-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by bsm0f0 on 2006-03-03
I just installed ubuntu (5.10) on my new Shuttle SN95G5.  Everything went well aside for network device detection, and after 3 hours of google and lack of caffiene I've yet to resolve the issue.

Is anyone else using this kit? If so, where/what drivers do I need to get the onboard nic working?  I'm guessing its something to do with the nvidia nforce drivers ... but I haven't a clue.  Everything else is working fine ... just no LAN.

System Info:**Motherboard**: 
NVIDIA nForce 3 250 GB chipset 

**Network**: 
 Gigabit LAN
(from the spec sheet)

Thanks

---

### Post by seannyob on 2006-03-03
bsm0f0,

I'm not at home, so i'm flying from memory... 

Did you install nvidia's motherboard drivers for linux?  Did they even write those?  I forget.  If they do, don't bother, you don't need them.  Uninstall those and use the open source forcedeth driver.  Let's search for it on your system, shall we?  Try:

```
$ lsmod | grep force
```

...if the grep of lsmod's output returns forcedeth, then you're already running the correct driver and I'm wrong, your problem is in software.  If I'm right, and it returns nothing, then try:

```
$ sudo modprobe forcedeth
```

...and run dhclient again to try to get an IP address through the nic.  

If that doesn't work, let us know where it barfs and, just to be safe, return the outputs of 

```
$ lspci
$ lsmod
```

[QUOTE=bsm0f0]
Is anyone else using this kit? If so, where/what drivers do I need to get the onboard nic working?  I'm guessing its something to do with the nvidia nforce drivers ... but I haven't a clue.  Everything else is working fine ... just no LAN.

System Info:**Motherboard**: 
NVIDIA nForce 3 250 GB chipset 
[/QUOTE]

---

### Post by bsm0f0 on 2006-03-03
[quote=seannyob]bsm0f0,

Did you install nvidia's motherboard drivers for linux?  Did they even write those? 

[/quote]
nope, missed those.  Yes, I downloaded them and attempted to install but can't go further than selecting the nic and graphics setup, its asking for the source kernel files and I don't see them in the cd repository (or maybe I'm looking for the wrong thing?

The reason LAN is down is because I don't have the drivers installed.  So grabbing packages and installing is pretty much done via USB and the cdrom.  I'm still looking for the source files for the kernel so I can try to run the driver installation again.

Thanks for the help **seannyob**

---

### Post by bsm0f0 on 2006-03-03
[SIZE=1][SIZE=2]well, i can't get it working ... here is my install log. (well I can't seem to get atm ... will post once i can pull it off)

I'm getting errors similar to: [http://ubuntuforums.org/showpost.php?p=509336&postcount=2]("http://ubuntuforums.org/showpost.php?p=509336&postcount=2")

I'll give this thread a try and if it doesn't work ... i'm done for the night, i'll pick this up tomorrow.
[http://ubuntuforums.org/showthread.php?t=134402&highlight=forcedeth]("http://ubuntuforums.org/showthread.php?t=134402&highlight=forcedeth")
[/SIZE]

Ok, I give up.  Both the LAN and Sound driver installed, but neither work.  I followed the threads

[http://ubuntuforums.org/archive/index.php/t-79896.html](http://ubuntuforums.org/archive/index.php/t-79896.html)

[http://ubuntuforums.org/showthread.php?t=134402&highlight=forcedeth](http://ubuntuforums.org/showthread.php?t=134402&highlight=forcedeth)

still not luck, but at least I got the drivers to compile and install, they just won't work.


Looks like its windows for this machine :cry:
[/SIZE]

---

### Post by jaycarnie on 2006-03-04
Hey bsm0f0,
Was the 5.10 install the 64 bit one or 32?

I had 64 running on my shuttle sn95g5 v3 a while ago, and from memory didn't have to do anything special to get the lan working.

It's not installed any more as I had to use the machine for something else, and 64 bit didn't get me everything i needed.
I am however about re-install 32 bit 5.10 so I'll let you know how it goes.

JC

---

### Post by huberc on 2006-03-16
I've got a Shuttle SN95G5, but a different problem with Ubuntu 5.1. Everything seemed to work just from a default install, except the fan speed control. Ubuntu seems to want to run my cpu fan pretty high at all times regardless of what I set the fan speed at in the BIOS. I am dual booting with win xp, and it works perfectly in windows. 

Anyone have any ideas?

---

### Post by bsm0f0 on 2006-03-17
Sorry for the long wait for reply.

My problem was due to the nvidia chipset being non-functional.  I exchanged my SN95G5 for a second one and everything installed by default.  I have no problems now ... the machine is DEAD quiet ... aside from the fan on the fx-5500 (gotta look into passive cooling for that thing).

**huberc** - I don't have an issue with my fan running high ... not sure why it would run high unless your system is running hot ...

---

