---
title: "Atheros 5007EG sees network but won't connect"
date: 2008-04-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by jaredg32 on 2008-04-06
I'm running Gutsy 64 bit.  I used ndiswrapper and installed the windows xp 64 bit driver.  After the very first install I shutdown and restarted and everything worked fine.  I was able to see all available wireless networks and connect to mine using my WPA key.  

Ever since, I can not connect.  I can still see all available wireless networks, but it won't connect to mine.
I can't figure out why it worked the first time and ever since it won't work.  I can connect via wired network fine but would really like to get this wireless figured out.

My networking interfaces file looks like this -- 

```
auto lo
iface lo inet loopback
```

I have no idea where to start trouble shooting this.  Anybody ever come across a similar problem with 64 bit versions or Atheros 5007EG wireless card?  

Any suggestions?  Thanks!

---

### Post by Malekish on 2008-04-10
I had the same problem but I was told to try using Wicd and it works better now.  (Edit for clairty - Wicd Manager, it should be in public repositories or from here [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/))

Sometimes it sees all networks but won't connect, I've found if I drill into the settings and re-type the wireless key it connects again, but I'm still enough of a noobie to not figure out why it does that yet.

---

### Post by phidia on 2008-04-11
I have this card on my laptop it was something of a pain to get working (trouble free working) I am also using 64 bit. 
I also think there is a difference between 64 bit and 32 but that's off topic.
If you search my name you should find the posts/threads involved (perhaps phidia & ar5007eg) will be a more efficent search. 
Anyway my laptops works trouble free using ndiswrapper-finds all available wifi signals.

---

### Post by wrtrdood on 2008-04-13
It's a 64 bit madwifi driver issue (see[http://madwifi.org/ticket/1679]("http://madwifi.org/ticket/1679")).  Apparently the Hardy wizards solved the problem.  After the latest update it now works.  I was able to get the card "almost" working before using ndiswrapper but It would never associate with the AP.  After reading about this driver issue (32 bit never worked for me) I decided to wait for Atheros to provide the 64 bit HAL module.  I don't know if that's what happened or, as I said, the Ubuntu developers fixed the bug.

==============
Guess I spoke too soon.  I just updated (April 16th) and now the wireless is out again. ](*,)

---

### Post by harrykh on 2008-04-13
I had this problem, apparently the MAC addresses changes to all 0s or something when this happen. I had to use pre-up and it works even faster than windows now. 

search forum for acer 4520 guide, it's there somewhere. I did a fresh install and my bookmarks is gone.

---

### Post by jaredg32 on 2008-04-13
I had  no problems with this card using madwifi on 32 bit.  I will wait for Hardy 64 stable to be released in a few days and try madwifi with that.  Thanks for the insights.

---

### Post by ubun_two on 2008-04-20
I had exact same issue when I tried Gutsy 64bit.

However, I was able to get it to work under 32bit.  In fact, I am using that right now.

I am really hoping that it'll be trouble free on Hardy, since I want to jump to 64bit.

---

### Post by nray on 2008-04-27
> **ubun_two said:**
> I had exact same issue when I tried Gutsy 64bit.

However, I was able to get it to work under 32bit.  In fact, I am using that right now.

I am really hoping that it'll be trouble free on Hardy, since I want to jump to 64bit.

I had my AR5007EG working great with ndiswrapper in 32-bit 7.10, but I've been completely unable to get it to work in 64-bit 7.10 and 8.04, and I've spent about 20 hours on this problem.

I think there are some serious errors in ndiswrapper in 64-bit, both the broken functionality with the 5.3.0.56 x64 drivers and a complete system hang with the 7.4.2.75 x64 drivers, and unfortunately with the AR5007EG madwifi is not an option right now at all in 64-bit.

---

### Post by nray on 2008-04-29
Found a solution -

In at least 64-bit Ubuntu 8.04, with the ndiswrapper package (version 1.50 at the time of this writing), using the XP x64 5.3.0.56 driver, it is absolutely necessary to put this line into /etc/network/interfaces under iface wlan0 with your AR5007EG's hardware ethernet address where 00:00:00:00:00:00 is:

pre-up /sbin/ifconfig wlan0 hw ether 00:00:00:00:00:00

With that line in place, things worked they way they should in 64-bit.  I didn't need that line in 32-bit Ubuntu 7.10 with ndiswrapper, but I needed it in 64-bit.

---

### Post by Naguz on 2008-04-29
I am going to try that tonight nray, and if it actually works I salute you. I think the driver you mentioned is the one i got "working" to the point where i coukd see wireless networks, but connecting was not possible, and eventually ndiswrapper froze my system and the booting sequense then halted at "loading manual drivers"

*hoping, hoping, hoping this works.* 
The laptop is pretty much useless for school use without working wlan.

---

### Post by alexandru_sorin on 2008-05-07
What line did you add to /etc/network/interfaces  ?

I have ububtu 8.04 64 bits with ndiswrapper for wifi. I can see the networks, but i cant connect to any of them.

---

