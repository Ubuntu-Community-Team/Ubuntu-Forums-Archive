---
title: "Ubuntu 8.10 losing wireless connections (last update)"
date: 2008-11-13
forum: x86 64-bit Users
---

### Post by leone2nd on 2008-11-13
Ubuntu 8.10 losing wireless connections since (last update) one one/half hour ago.
**GMT 10:38 AM** 14 November.
System reboot is needed for re-connecting to the AP, APs.

Tested with open encryption for the AP and also both WEP and WPA, 
Tested with different APs.
Also wireless connections hang after an x amount of time. Times range from after 30 mins to 1 hour or more. Now is still up for 2 hours and has not hanged yet. 
Signal Level and Link Quality presents themselves OK, still no data received or send.

**Last change to my system before these problems was installing Vuze 4.0.** That was done aprox. one hour before this last update.
The system is a fresh install done before a few days and received only 2 updates so far with the last one 1 hour ago and the connection problems appeared.

Has anybody noticed any similar problems with wireless since the last updates?

---

### Post by stanley drew on 2008-11-14
I'm having the exact same problem. There are a lot of people with similar issues, e.g. [http://ubuntuforums.org/showthread.php?t=974499](http://ubuntuforums.org/showthread.php?t=974499).

Also a lot of people are saying that they have no luck when trying to use a secure network, but that unsecured networks are fine. I'm wondering if they are just not waiting long enough for the connection to drop out, as you and I are experiencing.

Have you tried wicd? Install info is here: [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php). I used it flawlessly in 8.04 but in 8.10 I can't see any networks; only wired works. If you can get it to work I'd be interested in what you did.

---

### Post by leone2nd on 2008-11-14
I think I will not have any lack with wicd because of the wireless card I use.
The connection problems are random and happen especially if you leave the connection running idle for a bit. Sometimes even if it doesn't get idle and significant traffic is occurring, the link hangs while using Vuze or Transmission Bit Torrent clients and this happens when the connection maxes out the available bandwidth. These are the only torrent clients I use.

I used to have latency problems with IPv6 in Hardy 8.04 which I could not solve no matter what I did and all fixes were temporary.

I was satisfied with Ibex 8.10 for a few days until this thing occurred, still seems like a minor issue for the time but I am not sure what future updates may fix or brake and I don't want to go over a similar mess like with IPv6 all over again.

I use an asus WL 167G wireless card (usb) and unfortunately I don't have my other cards here to test them.

I used to have problems with wicd and the default wireless client in Ubuntu 8.04 especially the re installation of the default client. I'm afraid to touch this because I might have to do a clean install again and I hate this because I am still doing graphical work on this desktop.

Thank you for taking the time to answer though, at least I learned that I'm not alone on this problem and that it isn't a problem in my own hardware or software setup.

I hope they can find what it is and fix this soon. I will keep looking around in other forums for posts about the same problem and I will update here with any possible fixes I may find. :)

---

### Post by leone2nd on 2008-11-14
[double post]

---

### Post by stanley drew on 2008-11-14
great thanks, definitely keep me updated

---

### Post by GepettoBR on 2008-11-14
I'm running a fresh install (the update from Hardy broke a bunch of stuff) and I confirm this problem. Anywhere from three minutes to five hours, the connection will drop, and immediately autoconnect. I'm using an rt2870 USB wireless adaptor.

---

### Post by freelyx on 2008-12-18
I'm going to go ahead and bump this 4 week old thread because I to am having the same issues with my Asus Motherboard (Nvidia Chipset) Integrated Wireless card. 

It will, at random, disconnect and anything I try to do to solve it fails, I've tried disconnecting from the network, disabling networking, logging out and back in. The only thing, of course, is a long hard restart. This seems to happen after heavy Internet activity and anyone's help would be nice as it's keeping me from using ubuntu.

---

### Post by Deten on 2008-12-24
bump for great justice

dropping all the time :(

---

### Post by Deten on 2009-01-10
Still happening

---

### Post by beekr on 2009-01-23
I would like to add to this post. I, also, am having the intermittent wireless. It will work for 5 to 10 minutes and then nothing. It does reconnect after a while, say another 5 to 10 minutes. I'm running a Dell M1530 with Ubuntu 8.10 x86_64. My AP is a linksys with WPA encryption. Thanks in advance,

Beekr

"I'll block your entire subnet you LAMERS! . . .I am ROOT!"

---

### Post by kpkethc on 2009-01-25
I was wondering if anybody has had any luck with this issue. It's not that big of a deal but it certainly annoying to have to reboot when your network connection drops. Happens every time I come out of standby too. Please help someone!

---

### Post by beekr on 2009-02-03
I'm curious if this might be my/our issue. If we're running 64 bit 8.10 and installed NDISwrapper - more than likely 32bit, would that cause us to lose wireless?? Ideas thoughts ???

---

### Post by GepettoBR on 2009-02-04
> **beekr said:**
> I'm curious if this might be my/our issue. If we're running 64 bit 8.10 and installed NDISwrapper - more than likely 32bit, would that cause us to lose wireless?? Ideas thoughts ???

If you installed NDISwrapper from the repos, it's the 64-bit version. However, the drivers you installed via NDISwrapper might be 32-bit.

I'm using native drivers, but I tried NDISwrapper and neither the 32-bit nor the 64-bit drivers had a satisfactory performance, but the 32-bit did work to some extent. I'd try using different drivers, though, and by that I don't just mean trying the 32-bit and 64-bit version of the same driver. Sometimes the XP driver works and the Vista driver doesn't, sometimes it's the other way around.

By the by, I no longer have this problem since a long while ago, so there was probably an update to Network Manager that fixed something. If other people still do, that must mean there's more than one problem at play here.

---

### Post by matt.parkes on 2009-02-04
I am having the same problem as well... When I was using Ubuntu 7.10 and Ndiswrapper with the Dell Broadcom windows driver i had little to no problems.  Now with the new Ubuntu 8.10 release i upgraded and decided to use the restricted drivers.  Here are my observations:

Unsecure networks seem to drop less frequently.
WPA2 networks drops usually every 5 minutes and within 1-2 minutes of in activity.
WPA2 networks dont seem to drop if there is constant traffic being pushed across.
WPA2 networks seem to reconnect automatically within 1 minute.

I'm using a Dell Inspiron 6400 running Ubuntu 8.10 with the B43 restricted driver enabled.

---

### Post by Deten on 2009-03-22
> **beekr said:**
> I would like to add to this post. I, also, am having the intermittent wireless. It will work for 5 to 10 minutes and then nothing. It does reconnect after a while, say another 5 to 10 minutes. I'm running a Dell M1530 with Ubuntu 8.10 x86_64. My AP is a linksys with WPA encryption. Thanks in advance,

Beekr

"I'll block your entire subnet you LAMERS! . . .I am ROOT!"

Mine does not reconnect ever, i have to restart :(

---

