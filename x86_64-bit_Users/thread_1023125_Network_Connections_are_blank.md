---
title: "Network Connections are blank"
date: 2008-12-27
forum: x86 64-bit Users
---

### Post by lathal on 2008-12-27
Ok i recently upgraded from 8.04 -> 8.10.Upon upgrading I noticed something was weird about the network settings icon in the taskbar.My net was was working fine but the icon said "Networking disabled".I can't edit the wired connections because there aren't any listed.They were fine under 8.04.
Moreover my $ifconfig output and /etc/networks/interfaces files are fine.It's just the networking settings on gnome that are odd.It's a problem cause if i want to add DNS servers I have to do it manually in terminal.
Here's my ifconfig O/P
> 

eth0      Link encap:Ethernet  HWaddr 00:13:d3:07:2e:41  
          inet addr:192.168.1.109  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d3ff:fe07:2e41/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:313770 errors:0 dropped:0 overruns:0 frame:0
          TX packets:321778 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:249488209 (249.4 MB)  TX bytes:49383514 (49.3 MB)
          Interrupt:20 Base address:0xde00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:146 errors:0 dropped:0 overruns:0 frame:0
          TX packets:146 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11702 (11.7 KB)  TX bytes:11702 (11.7 KB)

and my /etc/networks/interfaces

> auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.1.109
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1
#iface eth1 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp


auto eth0

I'm running x86_64 8.10 on an amd 3200+.Any help would be appreciated.

---

### Post by cariboo on 2008-12-28
I was looking through some logs, daemon.log in this case and found the following message:

```
NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
```

I'm using an MSI mb with an MCP51 Ethernet Controller, It doesn't show up under network devices, but it works so I'm not worried about it. I'm running Jaunty alpha2, and the problem showed up last week with a network manager update.

As far as I'm concerned Network Manger is a kludge right now and needs some serious work from the upstream developers.

Jim

---

