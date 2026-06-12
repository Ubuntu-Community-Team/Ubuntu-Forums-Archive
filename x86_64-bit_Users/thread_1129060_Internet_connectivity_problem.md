---
title: "Internet connectivity problem"
date: 2009-04-18
forum: x86 64-bit Users
---

### Post by stans on 2009-04-18
Just upgraded from 32 bit to 64 bit now no connection to the Internet. NETSTAT shows my address as 192.168.1.100 and gateway is 192.168.1.1 and I'm a bit lost as to what to do next. I've searched this forum but nothing seems to apply to my situation.

Advice anyone ? Thanks...

OK - lots of views - but no comments.

All the information in Connection Information appears to look valid however if I try to ping my router I get a 'network is unreachable' error.

---

### Post by dcstar on 2009-04-18
> **stans said:**
> Just upgraded from 32 bit to 64 bit now no connection to the Internet. NETSTAT shows my address as 192.168.1.100 and gateway is 192.168.1.1 and I'm a bit lost as to what to do next. I've searched this forum but nothing seems to apply to my situation.

Advice anyone ? Thanks...

OK - lots of views - but no comments.

All the information in Connection Information appears to look valid however if I try to ping my router I get a 'network is unreachable' error.

You may want to go into the network manager and manually set your system to DHCP.

---

### Post by stans on 2009-04-18
I tried that earlier, no good, tried it again just now. Not working.

---

### Post by Slim Odds on 2009-04-19
> **stans said:**
> All the information in Connection Information appears to look valid however if I try to ping my router I get a 'network is unreachable' error.

Show us the output of the 'route' command.

---

### Post by stans on 2009-04-21
Sorry for the delay in replying - will get that information tonite.

---

### Post by stans on 2009-04-21
[FONT="Lucida Console"]Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0[/FONT]

---

### Post by Yellow Pasque on 2009-04-22
So you're using a router set for DHCP? What is output of:
```
sudo modprobe -r skge
sudo modprobe skge
sudo dhclient eth0
```
Again, if you can't get this working in a Ubuntu Jaunty/9.04, please add on to this bug: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131965](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131965)

---

### Post by stans on 2009-04-22
Thanks for your reply.

The first two don't return any thing - 

The last:

eth0: ERROR while getting interface flags: no such device

I've entered these commands before in chasing down this problem and seen different results. Not sure what is going on, other than I have run out of time and patience.

---

