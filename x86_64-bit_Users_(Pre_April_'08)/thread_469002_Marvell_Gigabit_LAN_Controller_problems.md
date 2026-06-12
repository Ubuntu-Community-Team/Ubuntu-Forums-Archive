---
title: "Marvell Gigabit LAN Controller problems"
date: 2007-06-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by daniel of sarnia on 2007-06-09
Hello I just installed 64 bit ubuntu and my mother board ( [P5WD2-E Premium]("http://www.asus.com/products4.aspx?modelmenu=2&model=981&l1=3&l2=11&l3=248&l4=0")) has two Marvell 88E8053 Gigabit LAN Controller onboard. They are detected by the network manager just fine and they say that they have made a connection when I start up.

But when I open firefox or try to ping something nothing happens, it just times out. The card is set to dhcp just like in 32 bit ubuntu, in which everything worked out of the box.

Anyone have any ideas?

thanks.

---

### Post by daniel of sarnia on 2007-06-09
maybe I'll just go back to 32 bit ubuntu and try and recompile the kernal so it will see all my ram :sad:

---

### Post by jamesford on 2007-06-09
sometimes this helps
sudo /etc/init.d/networking restart

---

### Post by daniel of sarnia on 2007-06-09
The problem persists, thanks though 
 this is what the terminal put out when I did that command and googled something with firefox 

```
 daniel@daniel-desktop:~$ sudo ifconfig eth0 down
Password:
daniel@daniel-desktop:~$ sudo ifconfig eth0 up
daniel@daniel-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth1.pid with pid 5754
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:15:f2:d7:64:32
Sending on   LPF/eth1/00:15:f2:d7:64:32
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.1 port 67
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 7637
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:15:f2:d7:67:52
Sending on   LPF/eth0/00:15:f2:d7:67:52
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
There is already a pid file /var/run/dhclient.eth0.pid with pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:15:f2:d7:67:52
Sending on   LPF/eth0/00:15:f2:d7:67:52
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
eth2: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth2.pid with pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
ath0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.ath0.pid with pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
There is already a pid file /var/run/dhclient.eth1.pid with pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:15:f2:d7:64:32
Sending on   LPF/eth1/00:15:f2:d7:64:32
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]
daniel@daniel-desktop:~$ 

```

---

### Post by daniel of sarnia on 2007-06-09
You know what, don't worry about it, I'm just going to go back to 32 bit and compile my own kernal so I get all 4 gigs of man ram. Thanks though, maybe the next release of ubuntu will be kinder.

---

### Post by mobad on 2007-06-09
I'm have the same network card as you and I'm using 64 bit Ubuntu.  What I think your problem might be is a DNS  problem like the one I had.  Try pinging 64.233.167.99 (google) and if it works then its a problem with your DNS not saving.  Just search on the forums for "DNS not saving" or something like that and then you should find something that will help.  If not, than I'm not too sure.

---

### Post by crjackson on 2007-06-09
> **daniel of sarnia said:**
> You know what, don't worry about it, I'm just going to go back to 32 bit and compile my own kernal so I get all 4 gigs of man ram. Thanks though, maybe the next release of ubuntu will be kinder.

I have the same controller.  It works fine in A64 and 32bit.  Don't give up so easy...

---

### Post by daniel of sarnia on 2007-06-09
well what should I do then, and I pinged google's ip and that did not work either...

---

### Post by daniel of sarnia on 2007-06-09
Well I toke the half lazy way out and put installed and old 100 base t d-link card I forgot I had. So now I can use ubuntu 64 bit while I try and figure out why the on board 1000 base t lan is not working.:p

---

### Post by SirBob1701 on 2007-06-13
I have same card with 32 bit feisty and the thing refuses to work even with compiled marvell driver (its nforce4 chipset Asus A8N32-SLI Deluxe)

---

