---
title: "Red Alert II, problems regardless of OS"
date: 2008-06-08
forum: Wine
---

### Post by AdrianStrays on 2008-06-08
So here is the basic issue, IPX protocol is no longer supported in Vista. Red Alert II requires IPX protocol for network play.  So there are two "solutions" to this. 

Install the protocol from here:
[http://www.starbase01.com/site/index.php?id=22,87,0,0,1,0](http://www.starbase01.com/site/index.php?id=22,87,0,0,1,0)

And Red Alert 2 won't recognize the protocol

or 

Install the patch and use UDP
[http://www.understorm.net/cnc/lan/ts_ra2_lanpatch_1_00.zip](http://www.understorm.net/cnc/lan/ts_ra2_lanpatch_1_00.zip)
[B]
The patch works, but the problem is that I can't get the patch to work in Ubuntu.  So that is the are I need help in.[/B]

Alternatively, because Ubuntu isn't a retarded piece of crap and CAN run IPX protocol, after using the following commands:

sudo apt-get install ipx; sudo modprobe ipx; sudo ipx_interface add -p eth0 802.2 0x12345678
[B]
However, as mentioned earlier, getting the protocol working properly is useless, because you can't configure anything in Vista[/B]

I need solutions.

How can I get the patch, which is just to .dll to work under Wine

or

How can determine the settings of the patch in Vista, and adjust my normal connection in Ubuntu to match and work with it?

---

### Post by benpage26 on 2008-09-30
Have you had any success with getting this to work?

---

