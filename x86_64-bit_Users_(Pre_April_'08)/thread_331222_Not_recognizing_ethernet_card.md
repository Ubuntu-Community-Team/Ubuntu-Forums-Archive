---
title: "Not recognizing ethernet card"
date: 2007-01-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by baneberry on 2007-01-04
I just installed Ubuntu on a machine I built.  The motherboard is a Gigabyte-965P-S3 with Onboard Marvell 88E8056 phy (10/100/1000 Mbit).  
I'm having trouble getting it to recognize the ethernet card.  When I type 
*ppoeconf*
into a terminal.  I get this response:

[I]Sorry, no working ethernet card could be found. If you do have an interface card
which was not autodetected so far, you robably wish to load the driver manually 
using the modconf utility. Run modconf now?[/I]

I hit yes and nothing happens:  Any help with this issue would be greatly appreciated.

Additional information:  My machine is dual boot and I'm using windows on the same machine to post this so the ethernet card is fine.

My /etc/network/interfaces files is 
[I]auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface dsl-provider inet ppp
provider dsl-provider[/I]


The response to *ifconfig *is[I]
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:146 errors:0 dropped:0 overruns:0 frame:0
          TX packets:146 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10788 (10.5 KiB)  TX bytes:10788 (10.5 KiB)[/I]

---

