---
title: "linux newbie- Wireless help- Intrepid"
date: 2008-11-26
forum: x86 64-bit Users
---

### Post by xarhelios on 2008-11-26
Back when I used Wubi in Hardy Heron, I had better wireless than in Vista home Premium. Now, I have a 100gb partition with Intrepid, and I cant connect to the wireless signal. Well, I connect, but I cant get a network address and I really need Internet. Please help me.

---

### Post by xarhelios on 2008-11-26
I just realized this is in the wrong forum, or maybe not, but if a mod is seeing this, please move if you think it is necessary.

---

### Post by nzadLithium on 2008-11-26
post output of ifconfig, iwconfig and lspci (i'm assuming your network card is not usb?).

---

### Post by h4v0k_d0m on 2008-11-26
Also you can start off pinging your loopback (127.0.0.1) and then ping the router (192.168.?.?) if those return no packets dropped you may need to go into the router configuration and run the connections again and get it all up running again.

---

### Post by bford16 on 2008-11-26
Chiming in:

Intrepid's Network Manager can be finicky (I speak from experience.) In a terminal window, run, "nano /etc/network/interfaces."  This will give you read-only access to the file, so you won't accidentally make changes.  You should see this:

auto lo
iface lo inet loopback

There should be nothing more. Ctrl+X closes nano.

Also, try running "sudo dhclient" in the terminal. I found it necessary to do this with my WIRED access!

---

### Post by nzadLithium on 2008-11-26
wat u mean intrepids network manager, every version of network manager has been painful XD (Thats why I don't use it anymore).

bford, all of your network interfaces *should* be setup in the /etc/network/interfaces file. Mine aren't cause i'm preferring manual setup (i've never got that file to work properly XD) but by default you will have alot more in that file than what you said.

and we'll see whether or not xarhelios has an ip address when they post back that info I sent. I don't mean to insult your opinion bford but its generally a better idea to find out whats wrong before you try applying random fixes which may or may not be the cause of the problem :p
If we kept on offering xarhelios random things to try before we actually found out what was wrong, we might be here for days offering different commands before we struck lucky and one worked. XD

---

### Post by xarhelios on 2008-11-26
Sorry, I couldn't post because I was on Ubuntu and, well, I can't get internet on it. Ill try those commands, and get back to you.

---

### Post by xarhelios on 2008-11-26
OK. I ran what I knew how to run and...here it is:

[SIZE="4"]fconfig[/SIZE]

eth0      Link encap:Ethernet  HWaddr 00:1f:c6:4d:af:83  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:5684200897 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:250 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:256 errors:0 dropped:0 overruns:0 frame:0
          TX packets:256 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16256 (16.2 KB)  TX bytes:16256 (16.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:44:b7:49:da  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1808 (1.8 KB)  TX bytes:2480 (2.4 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-44-B7-49-DA-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


[SIZE="4"]iwconfig[/SIZE]

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:5.5 Mb/s   Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=67/100  Signal level:-76 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


[SIZE="4"]lspci[/SIZE]

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:00.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
01:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:00.0 Multimedia controller: ViXS Systems, Inc. XCode 2100 Series
05:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)

[SIZE="4"]
nano /etc/network/interfaces[/SIZE]

all I saw wasauto lo and iface lo inet loopback

[SIZE="4"]sudo dhclient[/SIZE] 

Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/pan0/12:d7:79:48:70:ce
Sending on   LPF/pan0/12:d7:79:48:70:ce
Listening on LPF/wlan0/00:16:44:b7:49:da
Sending on   LPF/wlan0/00:16:44:b7:49:da
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Listening on LPF/eth0/00:1f:c6:4d:af:83
Sending on   LPF/eth0/00:1f:c6:4d:af:83
Sending on   Socket/fallback
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS recieved.

---

### Post by xarhelios on 2008-11-26
So...Can anyone interpret that and tell me what to do to get my wireless working?

---

### Post by Tyler H on 2008-11-27
Have you tried using the default Network Controller instead of Wubi?

And try reseting your router.

---

### Post by xarhelios on 2008-11-27
I do not use wubi anymore. I have a 100gb Partition with intrepid on ti. I will try resetting router.

---

### Post by nzadLithium on 2008-11-27
xarhelios its not your router its your pc, from that information you just posted up we can see that you don't have an ip address dhcclient is failing because you havent actually setup iwconfig properly yet, which is what is causing you not to receive an ip address.

I would suggest you try installing the package network-config and using that to setup your wireless as you have not actually told linux what your router is called and probably not given it any wep/wpa keys it needs.

Since your posting you obviously have a pc with working internet so go to this page [http://packages.ubuntu.com/intrepid/network-config](http://packages.ubuntu.com/intrepid/network-config)
and download network-config. (Download link is the word 'all' in the table below 'Download network-config'.

Burn it to cd or put on flash drive or something and then take it to your ubuntu install and double click it, it'll start ubuntu's deb installer program and install it for you. Then go to the terminal and type 'network-config' stick all the details it needs in there, and then press apply, hopefully then you'll have working internet.

---

