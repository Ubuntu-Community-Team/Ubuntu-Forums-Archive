---
title: "Internet not working"
date: 2008-12-13
forum: x86 64-bit Users
---

### Post by Samip on 2008-12-13
My internet works fine in 32 bit operating systems, but when I install a 64 bit operating system, whether it be vista or ubuntu, my internet is not working. I am not sure what the problem is.

---

### Post by cariboo on 2008-12-14
It would help if you told use what type of network adapter you are using. In a Applications-->Accessories-->Terminal type:

```
sudo lshw -C network > network.txt
```

Copy the text file to the computer your are using to access the forums and paste the file in your next post.

Jim

---

### Post by Samip on 2008-12-14
*-network
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: c
       bus info: pci@0000:06:0c.0
       logical name: eth0
       version: 13
       serial: 00:18:f3:a1:1b:4d
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 duplex=full firmware=N/A ip=192.168.1.100 latency=32 link=yes maxlatency=31 mingnt=23 module=skge multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: d6:34:28:99:49:43
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by Arup on 2008-12-15
Go to network manager by right clicking on the icon in your taskbar. Delete all accounts and create a new one, if its static IP, select manual, if its DHCP leave it on automatic. Save and see if you can connect.

---

### Post by cariboo on 2008-12-15
I would suggest doing what the previous poster suggested, but instead in a terminal type:

```
sudo dhclient eth0
```

and see if you get an ip address that way.

Jim

---

### Post by Samip on 2008-12-16
Here's what I get when I enter in that command:

Listening on LPF/eth0/00:18:f3:a1:1b:4d
Sending on   LPF/eth0/00:18:f3:a1:1b:4d
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPOFFER of 192.168.1.100 from 192.168.1.1
DHCPREQUEST of 192.168.1.100 on eth0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.1.100 on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

