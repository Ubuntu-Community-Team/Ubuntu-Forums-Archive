---
title: "[Wifi] D-Link DWL-G122 Rev. B1"
date: 2007-11-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by DARKGuy on 2007-11-28
Hey guys :)

I'm trying to connect my D-Link DWL-G122 Rev. B1 to my x64 box without success for about 2 versions of Ubuntu: Feisty & Gutsy, both being x64. The dongle works awesome in i386 though.

I used to use a script to activate it in i386 using lots of ifconfig commands but they don't seem to have any effect on x64. The modules the kernel used to load when connecting the dongle were rt2570, rt2x00usb and another one I can't remember now. They don't seem to affect the dongle in x64.

I've tried LOTS of suggestions made in the forum (but features between revisions change so they can't be used because X or Y reason, or they are for i386) without success... sometimes to the point of screwing my OS up and having to reinstall it (sorry I come from a Windows world where a reinstall fixes it all :p I don't know how to fix the mess I make when running scripts or following HowTos sometimes).

I would be really glad if anybody could help me in setting it up - by setting it up I mean fully functional to PROVIDE a connection (not to connect to a wireless network because I only use it as bridge for making a LAN for my laptop to connect and transfer files & play LAN games) and the dongle starts blinking its two top lights when it's fully working... sometimes in my tries it does that but for a few seconds and then they stop blinking and that means it doesn't work.

If this helps, I've taken a picture of the dongle here:

[IMG]http://img84.imageshack.us/img84/7113/usbdongle2rc2.jpg[/IMG]

---

### Post by DARKGuy on 2007-11-29
Any help? :( I hate to bump...

---

### Post by DARKGuy on 2007-12-03
Guys, I really need help with setting this wifi... I can't believe there isn't anyone capable of helping with some guidelines, at least? ... 

Come on, x64 on Ubuntu is way better than in Windows and there was a big fuss about x64x64x64omgomgOMG!!11!11!11oneoneone but this thread has been here for about 3 days and there hasn't been no reply?

Nobody has this adapter? what about a similar one? I'm out of ideas! :/

---

### Post by theharshone on 2007-12-03
Hi
I have the same wireless card and i got it to work perfectly. I assume you are using gutsy. What problem did you have in fiesty? Also some thing that may help is posting some outputs for ifconfig -a iwconfig. 
If you are using gutsy the commands are:

sudo ifconfig wlan0  <ip adress> up
sudo iwconfig wlan0 essid <essid> key <key>
sudo dhclient wlan0

---

### Post by DARKGuy on 2007-12-03
> **theharshone said:**
> Hi
I have the same wireless card and i got it to work perfectly. I assume you are using gutsy. What problem did you have in fiesty? Also some thing that may help is posting some outputs for ifconfig -a iwconfig. 
If you are using gutsy the commands are:

sudo ifconfig wlan0  <ip adress> up
sudo iwconfig wlan0 essid <essid> key <key>
sudo dhclient wlan0

Thanks for replying! :D

The problems I had with feisty were many, mainly because there were issues with the kernel modules and the dongle not working (leds only blinked twice and poof, they were gone again along with the connection, and Windows on my laptop couldn't detect it).

But yeah I'm using gutsy :D the main problem is that I don't use it for connecting, I give it a static IP address (nothing can give me DHCP so no dhclient for me) so my laptop can connect to it and have the internet my desktop PC has. It's actually making my own PC an access point / ad-hoc network, so what would be the commands I would need to run in my case, if I can't run dhclient?

---

### Post by DARKGuy on 2007-12-06
*bump* :(...

---

### Post by DARKGuy on 2007-12-09
*bump*

I hate bumping... but I need to get this wifi working! :mad:

So yeah, these commands are for connecting to a WLAN...

> sudo ifconfig wlan0  <ip adress> up
sudo iwconfig wlan0 essid <essid> key <key>
**sudo dhclient wlan0**

**I can't use dhclient, I must set a static IP/netmask/gateway.** Anybody knows how to? this is a very delicate issue... everytime I've tried similar stuff I always end up screwing up my Ubuntu system...

---

### Post by DARKGuy on 2007-12-11
Okay, I'm gonna keep up on bumping this until I get an answer. I'm not joking on the matter that I need this Wifi working...

---

### Post by sruckh on 2007-12-12
I have the A3 version and its support has been very week.  Worked fine with NDIS wrapper in Edgy, Kernel Error with Fiesty, and have not been able to connect to any secure networks in Gutsy.

I filed a kernel Bug report for Fiesty.  It was confirmed that there was an error, but that there would not be any fix.

In Gutsy the adapter is recognized (without NDIS wrapper), and I can scan for wireless networks, but I can not connect using WEP or WPA.

I believe your adapter uses a completely different chipset if I remember correctly so all of this may be irrelevant.

Is your adapter even recognized?

Can you scan for networks, using the wireless command line tools?

---

### Post by Kilz on 2007-12-13
[Just to add, there is a wiki page for this device.]("https://help.ubuntu.com/community/WifiDocs/Device/DWL-G122_%28Rev_B%29")

---

