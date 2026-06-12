---
title: "can't connect via ethernet for broadband on imac g3"
date: 2006-01-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by enzedchris on 2006-01-15
how do i set up my internet, i noticed that time server syncro failed when starting up, i acitvated eth0 and stuff, what do i do, im a noob. please help me goddddd.

---

### Post by adwait on 2006-01-15
What kind of internet do you have?? If you have xDSL running on PPPoE, this could help:
```
sudo pppoeconf
```

If you have dial up, try gppp.

---

### Post by enzedchris on 2006-01-15
no i have comcast cable, it is not dsl but nonetheless i will try it, btw i love mumbai

---

### Post by adwait on 2006-01-15
[http://www.ubuntuforums.org/showthread.php?t=76224&highlight=comcast+cable](http://www.ubuntuforums.org/showthread.php?t=76224&highlight=comcast+cable)

Try that......apparently, for comcast you don't have to run PPPoE or anything. Just configure you LAN card to recieve the IP via DHCP and you are done. 

BTW: You ever been to Mumbai?

---

### Post by enzedchris on 2006-01-15
yes i have, i have also been to delhi, indor* i am guessing on the spelling, but it was a small town. I loved india because it is so different from the states, i am originally from new zealand, so i am a little more open minded than an american. thanks for your help

-chris

---

### Post by adwait on 2006-01-15
that's INDORE :)

No problem.......

---

### Post by enzedchris on 2006-01-15
ahhh this stuff still is not working, all i want to do is surf the web and install packages, ah this is torture. when i had 4.10 on my other imac, the one i am trying to get internet on, it worked flawlessly and i dont remember any config necessary. why is this so hard? i am using the same modem and provider, it is a motorola surfboard sb-5100 cable modem hooked directly to the computer. someone help please. it is comcast so there is no login required

---

### Post by ssam on 2006-01-15
if your modem connects by ethernet you could try running through [wired ethernet troubleshotting process]("http://www.ubuntuforums.org/showthread.php?t=87643")

---

### Post by enzedchris on 2006-01-15
ahhh still did not work, i do not know why this is. i did all those things in the help guide sent to me, but none of them worked exactly right, some did nothing in the terminal and instead just came up as a new entry without error message or anything. I have no idea. I could find out my card type and everything, came up apple ethernet whatever but this worked for me in hoary fine, and then it just does not work now. I didn't have to do any network config last time, just plugged in and worked.

---

### Post by ssam on 2006-01-15
can you post the output of the following commands
```

ifconfig
route
cat /etc/network/interfaces

```

---

### Post by enzedchris on 2006-01-15
ifconfig
Link encap: Ethernet  Hwaddr 00:30:65:6D:23:24
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr: fe80: :230:65ff:fe6d:2324/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX Packets:56891 errors:0 dropped:0 overruns:0 frame:0
TX Packets:45 errors:0 dropped:0 overruns:0 frame:0
collisions:0 txqueuelen:1000
RX bytes:3821064 (3.6 miB) TX Bytes:14058 (13.7 KiB)
Interrupt:41 Base Address:0xb800

route
Destination    Gateway    Genmask    Flags Metric Ref   Use Iface
(there was nothing under these..?)

cat /etc/.......

# This file describes the network interfaces available on your system
#and how to activate them. For more information see interfaces (5)

#The loopback network interface
auto lo
iface lo inet loopback
#this is a list of hotpluggable network interfaces.
#they will be activated automatically by the hotplug subsystem
mapping hotplug
             script grep
             map eth0
iface eth0 inet dhcp

auto eth0
iface dsl-provider inet ppp
provider  dsl-provider

(i do not have dsl, i have cable and everything is usually automatic, i have been swtiching the cable between my osx machine and the ubuntu one that sits next to it. i am in osx right now and do not have linux on this machine, my imac g3 is running linux)

---

### Post by enzedchris on 2006-01-15
btw it always hangs on CONFIGURING NETWORK INTERFACES on start-up, right after starting hotplug subsystem, and synchro with ubuntu clock or whatever always fails

---

### Post by Brian McConnell on 2006-01-15
[QUOTE=enzedchris]i am originally from new zealand, so i am a little more open minded than an american.
-chris[/QUOTE]

:roll: :roll: :roll: :roll: :roll:

---

### Post by enzedchris on 2006-01-15
lol..don't worry just playing around telling the guy i was in mumbai, indore, and delhi. sorry if it offended any of you guys i didn't mean it, well i hope this kubuntu may fix things

---

### Post by ssam on 2006-01-15
does
```
sudo ifup eth0
```
connect you to the network? any error messages?

---

### Post by enzedchris on 2006-01-15
ok well i forgot about ubuntu and i switched to kubuntu, and made sure i did a power cycle and everything before i installed the system and now everything works fine, i like kubuntu a lot more than ubuntu

---

### Post by ssam on 2006-01-15
ok, i hope kubuntu works better for you.

you can install gnome in kubuntu, but it sounds like you like kde better.

---

