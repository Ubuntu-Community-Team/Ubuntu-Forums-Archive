---
title: "Vbox host networkinterface setup on Hardy"
date: 2008-05-07
forum: x86 64-bit Users
---

### Post by harvey186 on 2008-05-07
Hi toegther, I have installed the latest version of virtualbox from the SUN website virtualbox_1.6.0-30421_Ubuntu_hardy_amd64.deb
I have setup a network bridge br0 -> vbox0 as descriped in the manuell, but the XP in virtualbox get's no ip via DHCP.

Is there a special setup under Hardy ??

---

### Post by andyesten on 2008-05-07
Can you please give some extra information about the bridge config. Please post the output of route and ifconfig. I had also a problem with a bridge configuration and had to add some lines to the /etc/network/interfaces. See [http://ubuntuforums.org/showthread.php?t=777101](http://ubuntuforums.org/showthread.php?t=777101).

---

### Post by harvey186 on 2008-05-07
I have tried it like descriped in the thread, but the bridge doesn't work. I have a local network with a router on 192.168.1.1. DHCP is activated.

here my interfaces:
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.
auto eth1
iface eth1 inet manual
    up ifconfig eth0 up
auto br0
iface br0 inet dhcp
	bridge_ports eth1

-> ifconfig:
br0       Link encap:Ethernet  Hardware Adresse 00:1d:60:ea:c6:c9  
          inet Adresse:192.168.1.8  Bcast:192.168.1.127  Maske:255.255.255.128
          inet6-Adresse: fe80::21d:60ff:feea:c6c9/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:688 errors:0 dropped:0 overruns:0 frame:0
          TX packets:549 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:756494 (738.7 KB)  TX bytes:73147 (71.4 KB)

br1       Link encap:Ethernet  Hardware Adresse 02:2a:13:91:dd:2a  
          inet6-Adresse: fe80::2a:13ff:fe91:dd2a/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:94 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:0 (0.0 B)  TX bytes:14231 (13.8 KB)

br1:avahi Link encap:Ethernet  Hardware Adresse 02:2a:13:91:dd:2a  
          inet Adresse:169.254.6.74  Bcast:169.254.255.255  Maske:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1

eth0      Link encap:Ethernet  Hardware Adresse 00:1d:60:ea:b7:19  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 Basisadresse:0x4000 

eth1      Link encap:Ethernet  Hardware Adresse 00:1d:60:ea:c6:c9  
          inet6-Adresse: fe80::21d:60ff:feea:c6c9/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:23582 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15792 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:30323330 (28.9 MB)  TX bytes:1853407 (1.7 MB)
          Interrupt:253 Basisadresse:0x6000 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:1730 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1730 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:89550 (87.4 KB)  TX bytes:89550 (87.4 KB)

vbox0     Link encap:Ethernet  Hardware Adresse 00:ff:13:e9:56:87  
          inet6-Adresse: fe80::2ff:13ff:fee9:5687/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:175 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:146 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:500 
          RX bytes:30201 (29.4 KB)  TX bytes:200 (200.0 B)

and route:
Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.128 U     0      0        0 br0
link-local      *               255.255.0.0     U     0      0        0 br1
default         192.168.1.1     0.0.0.0         UG    100    0        0 br0
default         *               0.0.0.0         U     1000   0        0 br1

---

### Post by andyesten on 2008-05-07
Ok, I can see two bridge interfaces br0 and br1 and two network interfaces eth0 and eth1. Is this what you expect? Are there realy two network cards in this machine?

Try changing the interfaces file into:

auto lo
 iface lo inet loopback
 address 127.0.0.1
 netmask 255.0.0.

auto eth1
 iface eth1 inet manual
 up ifconfig eth1 up    <-!!!!!

auto br0
 iface br0 inet dhcp
 bridge_ports eth1

---

### Post by calraith on 2008-05-07
If you're interested, I just made a quick and dirty bash script to set up bridging in Hardy for VirtualBox.  I'm using it right now, and it works well.  I didn't script in the ability to undo the changes made to the networking, but they're forgotten at reboot anyway.  The script is based on information at [http://home.nyc.rr.com/computertaijutsu/vboxbridge.html](http://home.nyc.rr.com/computertaijutsu/vboxbridge.html) , where you'll also find the steps for removing the bridge without a reboot.  Anyone who wants to polish this script and repost it, PLEASE DO!  :)

```
#!/bin/bash

# LanIF: wired interface
LanIF="eth0"
# WlanIF: wireless interface
WlanIF="ath0"
# DHCP: 1 = dynamic IP; 2 = static IP
DHCP=1
# TapIF: interface for tunnel; the device to be bound to the VBox NIC
TapIF="tap0"
# BridgeIF : interface for wired bridge; not directly used by VBox
BridgeIF="br0"
UserAcct="`whoami`"

## Already configured?
IPAddr="`ifconfig $TapIF | grep -v 'error' | grep 'inet addr:' | cut -d: -f2 | awk '{ print $1 }'`"
if [ "$IPAddr" == "" ]; then {
    IPAddr="`ifconfig $BridgeIF | grep -v 'error' | grep 'inet addr:' | cut -d: -f2 | awk '{ print $1 }'`"
    if [ "$IPAddr" != "" ]; then {
        echo "$TapIF already configured."
        exit 0
    }; fi
}; else {
    echo "$TapIF already configured."
    exit 0
}; fi

## LAN Interface -> $TapIF
IPAddr="`ifconfig $LanIF | grep 'inet addr:' | cut -d: -f2 | awk '{ print $1 }'`"
if [ "$IPAddr" != "" ]; then {
    if [ ! -f "`which tunctl`" ]; then sudo apt-get install uml-utilities bridge-utils; fi
    sudo tunctl -t $TapIF -u $UserAcct
    sudo chown root:vboxusers /dev/net/tun
    sudo chmod g+rw /dev/net/tun
    sudo brctl addbr $BridgeIF
    sudo ifconfig $LanIF 0.0.0.0 promisc
    sudo brctl addif $BridgeIF $LanIF
    if [ $DHCP == 1 ]; then
        sudo dhclient $BridgeIF
    else
        sudo ifconfig $BridgeIF $IPAddr
    fi
    sudo brctl addif $BridgeIF $TapIF
    sudo ifconfig $TapIF up
    echo "Bridging $TapIF with LAN interface $LanIF successful."
    exit 0
}; else {
    echo "LAN Interface $LanIF is not up.  Skipping. . ."
}; fi

## Wifi Interface -> $TapIF
IPAddr="`ifconfig $WlanIF | grep 'inet addr:' | cut -d: -f2 | awk '{ print $1 }'`"
IPNet="`echo $IPAddr | awk -F. '{ print $1"."$2"."$3".0" }'`"
NetMask="`ifconfig $WlanIF | grep 'Mask:' | cut -d: -f4`"
if [ "$IPAddr" != "" ]; then {
    if [ ! -f "`which parprouted`" ]; then sudo apt-get install parprouted; fi
    sudo sysctl net.ipv4.ip_forward=1
    sudo VBoxTunctl -b -u $UserAcct
    sudo ip link set $TapIF up
    sudo ip addr add $IPAddr/$NetMask dev $TapIF
    sudo parprouted $WlanIF $TapIF
    sudo route add -net $IPNet netmask $NetMask $TapIF
    sudo iptables -t nat -A POSTROUTING -o $WlanIF -j MASQUERADE
    echo "Binding $TapIF with WLAN interface $WlanIF successful."
    if [ $DHCP == 1 ]; then {
        echo "DHCP on the guest OS is not supported when the primary host OS network connection is Wi-Fi.  It'd probably work somehow with dhclient, but I'm too lazy to research it.  Set a static IP for the guest OS."
    }; fi
    exit 0
}; else {
    echo "WLAN Interface $WlanIF is not up.  Big fat FAIL!"
    exit 1 
}; fi

```

---

### Post by ASULutzy on 2008-05-07
Haven't tried that script yet, but a cursory glance it looks good. Giving you a preemptive thanks cause I'll be using it once I get off work :)

---

### Post by harvey186 on 2008-05-08
Hi, sorry I'm a newbee. I have copied the script inti gedit and saved as 'vbox' it.
But what have I to do now ?
sudo sh vbox isn't working.

Thanks Harvey

---

### Post by harvey186 on 2008-05-09
Okay, I have found the howto, but the script isn't working. I get the following error message:
bigdaddy@bigdaddy-ubuntu:~/Desktop$ sudo ./vbox.sh
: not found2: 
: not found14: 
: Fehler beim Auslesen der Schnittstelleninformation: Gerät nicht gefunden
./vbox.sh: 22: Syntax error: "}" unexpected (expecting "fi")

---

### Post by harvey186 on 2008-05-09
Now I changed the /etc/network/inteface to

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0
auto br0
iface br0 inet dhcp
	bridge_ports eth1


iface eth1 inet dhcp

auto eth1

and everything works.
Thanks, Harvey

---

### Post by harvey186 on 2008-05-10
Now I get the following message while booting. After this message the booting hangs for around 90 seconds. 
 br0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature

What's from ??

---

### Post by harvey186 on 2008-05-11
I have found something under bugzilla. You have to install libvirt. The message is still on boot but the network works now.

---

### Post by peap on 2008-08-13
I've recently installed an OpenVPN server with bridging using /etc/network/interfaces and (br0).

Everything works fine except that my boot hangs with the error message mentioned in this thread.

```
br0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
```

I tried installing libvirt-bin but that didn't help. I'm on ubuntu server 8.04.1. Fortunately I don't reboot the machine very often and I'm not sure if this affects anything... I just don't like errors.

---

