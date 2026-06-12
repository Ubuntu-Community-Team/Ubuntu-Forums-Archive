---
title: "Is lirc dead, and does Jaunty have built in support for USB IR"
date: 2009-05-17
forum: x86 64-bit Users
---

### Post by shabazzk on 2009-05-17
I have tried to installing lirc on 64bit Jaunty, but have had no joy. Searching forums and reading post including lirc website are starting to make me think LIRC may be dead or mute project. All the help is outdated for Jaunty, and the lirc package in debs does not install correctly.

Am I assuming correctly that it is indeed no longer under development by anyone?

Also, if I don't have lirc installed, and then open gEdit and press number buttons on the remote control, the number I press is displayed. Does this mean there is built in support for remotes via USB in Jaunty? Does this mean that the IR is installed and I just need to configure it. I so how?

Where can I get more info about installing remotes on Jaunty?

I've put plenty of time into this and would like to get it to work.

---

### Post by Yellow Pasque on 2009-05-17
lirc is not dead or mute at all. They're working on 0.8.5: [http://sourceforge.net/mailarchive/forum.php?thread_name=B0jzuDwmqgB%40lirc&forum_name=lirc-list](http://sourceforge.net/mailarchive/forum.php?thread_name=B0jzuDwmqgB%40lirc&forum_name=lirc-list)

---

### Post by shabazzk on 2009-05-18
Wasn't sure. I've been trying to set it up on Jaunty and all the tutorials are dated. Plus when I posted for help I get no response.

---

### Post by Grenage on 2009-05-19
I'm using lirc on my x64 9.04 without issues (except for not being able to use lircm).  What issues are you having?

---

### Post by shabazzk on 2009-05-19
I cannot use irrecord to make a config for lirc. When I attempt to run irrecord if get the following:

```
irrecord: could not get hardware features
irrecord: this device driver does not support the new LIRC interface
irrecord: major number of /dev/input/event5 is 13
irrecord: LIRC major number is 61
irrecord: check if /dev/input/event5 is a LIRC device
irrecord: could not init hardware (lircd running ? --> close it, check permissions)

```

I take this to mean that lirc is not installed correctly.

There is no lirc device in /dev. So I setup the hardware.conf to point to the event5, which is the event for the IR hardware.

*bump*

Frankly, I don't understand lirc, let alone know how to trouble shoot it.

---

### Post by Chunder on 2009-06-02
Watch out that your events aren't changing on boot - I found that I couldn't consistently refer to an event number to identify a particular device; I had to dig around in the depths of udev to link the correct event (based on unique device identifiers) to specific /dev/lirc0 or lirc1 entries.
Afraid I can't help much more, as I'm struggling with lirc too - just that this was one of the "gotcha!"s that I stumbled across...

---

### Post by shabazzk on 2009-06-02
> **Chunder said:**
> Watch out that your events aren't changing on boot - I found that I couldn't consistently refer to an event number to identify a particular device; I had to dig around in the depths of udev to link the correct event (based on unique device identifiers) to specific /dev/lirc0 or lirc1 entries.
Afraid I can't help much more, as I'm struggling with lirc too - just that this was one of the "gotcha!"s that I stumbled across...

Can you let me know how you did that? Lay some details on me man!

Aside from that, I think my main problem is that the usbhid driver claims my device no matter how I try to prevent that. It appears things changed considerably in 9.04 from 8.10. So the usual methods do not work.
```
T:  Bus=05 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=15c2 ProdID=0043 Rev= 0.02
C:* #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=100mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=02 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:* If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=10ms

```

Also, there is a problem I read about in the docs of 0.8.5 release of lirc that states:
> When you are using devfs or sysfs with your kernel, the /dev/lirc device node will disappear again once you reboot your machine. In that case the LIRC kernel module will generate the required entry every time it is loaded. But the device node won't be visible as /dev/lirc, but might be located in a different location like e.g. /dev/lirc/0. Please be aware of this fact when starting programs that access the device node like mode2 or lircd. You will have to use the --device command line option of these programs to point them to the correct location. When using sysfs together with the udev daemon you should copy the lirc.rules file located in the contrib directory of the source package to /etc/udev/rules.d/. This will make sure that the device node will be created.
I experienced this after I installing lirc. When the install was complete I checked for the /dev and found lircd, lirc, and lircm. After reboot, everything but lircd was there.

---

