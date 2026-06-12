---
title: "Ack Nightly crash"
date: 2008-07-05
forum: x86 64-bit Users
---

### Post by burgechris on 2008-07-05
Ok...I'm a Linux and Ubuntu noob but have been running it exclusively over the past several months.  Lately in the past couple of weeks, my system would just "turn off".  No warning, no fuss, nothing.  Just black screen of death.  I've been trying to see if there are any logs posted but of those I'm aware of I have no clue.  At first I thought, great hardware issue as it would seem to happen randomly during the day.  Now (as of the past 48 hours), I can just about guarantee a crash towards the evening followed with successive crashes as I go through the night.  

I tried running Mem86+ but after 12 hours through the night, it only hit at around checking 26% of my 4gigs before having to press escape  to go to work.  But, I had 0 crash time which had seemed to confirmed my suspicion that this was not power related (whew, no lightening strikes I hope).  

I ended up installing temperature monitors of which there is nothing unusual: AMD 64 with the cores running about 44 degrees.  A nvidia GPU at about 52 degrees.  Again no crash.

I can be simply browsing or running it through the paces such as using VMWare.  Then BAM I get the Black Screen.

Last night, I think I have figured out something.  If I disconnected my MCP55 Nvidia ethernet connector from the internet, it ran without any crashes.  This is way cool until you come to the realization that your life depends on that internet thing.  LOL.  

Assuming that this is a consistent issue, can anyone help me debug, find logs, get latest drivers, etc. to confirm and then fix this &*%*%&* thing?  LOL

Thanks

---

### Post by Yellow Pasque on 2008-07-05
Let's start with: (if lan0 doesn't work, then get the name of your network interface with *cat /etc/network/interfaces*)
```
sudo lshw -C network
ethtool lan0
```

If by some chance, you need a new NIC: [http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16833166019](http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16833166019)

---

### Post by burgechris on 2008-07-06
ok...here goes:

sudo lshw -C network

produced :

  *-network               
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:15:af:01:b3:12
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


Which isn't being used because it is turned off at my router.  The wireless device is part of the motherboard but I have the antenna off so it shouldn't be picking up anything.


for  ethtool lan0

I get:

Settings for lan0:
Cannot get device settings: No such device
Cannot get wake-on-lan settings: No such device
Cannot get message level: No such device
Cannot get link status: No such device
No data available


So no clue as to what that means.

Thanks

---

### Post by Bubba64 on 2008-07-06
Mem86 runs as a loop after 8 hours it probably went through your system multiple times. :)

---

### Post by burgechris on 2008-07-06
Ahhhhhh....LOL...so I guess the memory test went fine?

Thanks

---

### Post by cariboo on 2008-07-06
When you run ethtool you should run it for your ethernet interface eg;

```
sudo ethtool eth0
```

to find out what interface your nic is running as, in a terminal type:

```
ifconfig
```

Do not blindly paste what you see in a terminal and try running it, make sure you know what you are running. For instance if you don't know what ethtool does, in a terminal type:

```
man ethtool
```

That will tell you all you want to know about ethtool. Man works for most commands, so make it your friend.

Jim

---

### Post by burgechris on 2008-07-07
Ahhhhh...cool.  LOL.  I so always forget about man.  :P  Anywho, I did what you asked and read the man while running the tools.  Unfortunately,I don't think much helped (at least to my untrained eye).  I see in the man where I can get dumps but are these dumps of the current condition (which is what I assume) or dumps after a type of crash (which raises up how does it know that when I can't seem to find where ubuntu knows I just had a crash).  Anywho, here is what I have.

I have 2 10/100 ports off of my motherboard (eth0 and eth1) with only one connected (eth1).  I'll post the information below from the sud ethtool eth1 command.   From the ifconfig -v eth1, I don't see anything that says an ah-ha.  Maybe you see something below.  

Lastly, maybe I should take another route and ask where should I look exactly for any last logging information before a crash?  Maybe that will also help in defining exactly where for me as my use without ethernet is purely specalitive (though the results are reproduceable - i.e. detach ethernet no crash during the night).  

Thanks!

sudo ethtool eth1

Settings for eth1:
	Supported ports: [ MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 1
	Transceiver: external
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: d
	Link detected: yes


ifconfig -v eth1

eth1      Link encap:Ethernet  HWaddr 00:17:31:ce:e1:55  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fece:e155/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8577 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6791 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7969764 (7.6 MB)  TX bytes:1139394 (1.0 MB)
          Interrupt:253 Base address:0x6000

---

### Post by burgechris on 2008-08-04
Ok....well, I was able to finally get a consistent trap for the error as the issue started to become more frequent.  In short, it turned out to be a failing power supply unit.  Apparently, any fluctuation in the power to the house caused the unit to off-set the power to the motherboard in voltages.  It was soooo infrequent that I could never catch it outside of Ubuntu.  I could run it all night and it would be fine and then all of a sudden WHAM and I was out.  Apparently, they have scheduled brown-outs here at about the time I started to have problems but the voltage difference would only drop from 121 volts to 116 volts (well enough for the margin of error).  

Anywho, my lovely wife one day turned on her grinder (a 10.5 amp device) on a separate part of the house and that caused my computer to turn off while in GRUB.  Finally, I had an event to test so I went into BIOS and turned on the grinder -- BAAM!  I was in business!  Sooooo, quick trip to Best Buy; get a 700 Watt power supply; no problems for a week!

Thank you everyone for trying to help me out!  Hopefully, this will encourage someone out there to try out different, outside ways, to reproduce an error!

Thanks Again!

---

