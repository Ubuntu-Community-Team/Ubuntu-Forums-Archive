---
title: "[SOLVED] Unable to configure network"
date: 2008-08-28
forum: x86 64-bit Users
---

### Post by Hessesian on 2008-08-28
Hi, I recently isntalled hardy x64, but after installation my wired network wasn't automatically configured.

So I opened network settings, unlocked it, but there I couldn't choose wired connection, there was only one option, point to point connection and it was unchecked.

I don't know what to do next :-/ Thanks for any help

---

### Post by Crafty Kisses on 2008-08-28
Post the results of this command > ifconfig

---

### Post by Hessesian on 2008-08-28
```

ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1794 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1794 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:89700 (87.5 KB)  TX bytes:89700 (87.5 KB)

```

Well I have wired connection but with modem that needs to be activated when PC is changed. When I was running x84 ubuntu everything was configured automatically, so I don't know where lies the problem.

When I try to configure network as pppoe, in ethernet interface dropdown menu I have no options so I can't set-up network...

---

### Post by tuxxy on 2008-08-28
[https://help.ubuntu.com/8.04/internet/C/index.html](https://help.ubuntu.com/8.04/internet/C/index.html)

---

### Post by Hessesian on 2008-08-28
> **tuxxy said:**
> [https://help.ubuntu.com/8.04/internet/C/index.html](https://help.ubuntu.com/8.04/internet/C/index.html)

Well, command sudo pppoeconf is not working for me. Button <Ok> is not reacting so I can't move forward...

And I have Cable modem...

---

### Post by Hessesian on 2008-08-29
Anyone ? Sorry to bump, but I can't move forward. ubuntu can't detect my ethernet card Atheros AR8121/AR8113 (integrated on motherboard Asus P5Q pro)

My modem should be detected as wired connection since it has been activated on my new NIC card, but ubuntu thinks I am connected trough dsl/adsl modem...

---

### Post by Crafty Kisses on 2008-08-29
What about the results of this ```
lshw -C network
```

---

### Post by Hessesian on 2008-08-29
```

lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Attansic Technology Corp.
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: b0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0 

```

Ther's also one thing, when I try to launch anything as super user, it writes warning, that host duri-user could not be resolved...

---

### Post by Hessesian on 2008-08-30
when I edited etc/network/interface and added eth0 manualy
auto eth0
iface eth0 inet dhcp

and restarted networking I got this message
```

duri@duri-desktop:~$ sudo /etc/init.d/networking restart
sudo: unable to resolve host duri-desktop
 * Reconfiguring network interfaces...                                          eth0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.
                                                                         [ OK ] 

```

Please help me, linux is without internet unusable :(

---

### Post by Hessesian on 2008-09-03
Isn't here anyone that is able to help me ?

---

### Post by Yellow Pasque on 2008-09-03
Your ethernet controller is unclaimed (no driver). Is this the onboard ethernet controller or another one that you added?

---

### Post by Hessesian on 2008-09-04
Yes, its integrated (onboard) on my MB Asus P5Q pro

---

### Post by Bucky Ball on 2008-09-04
copy and paste into terminal:
[B]
echo "127.0.1.1 NameofYourComputer" | sudo tee -a /etc/hosts[/B]

Replace 'NameofyourComputer' with appropriate details. That should fix the sudo host problem.

---

### Post by Yellow Pasque on 2008-09-04
It looks like you need the atl1 kernel module, so:
```
sudo modprobe -v atl1
sudo lshw -C network
```
If that works, open /etc/modules , add atl1 to the list, save and quit.
```
gksudo gedit /etc/modules
```

---

### Post by Hessesian on 2008-09-04
Ok, so I found this thread [http://ubuntuforums.org/showthread.php?t=770173](http://ubuntuforums.org/showthread.php?t=770173)

Did this
1) I installed ubuntu hardy 64bit, i has build-essential package installed
2) Then i downloaded the linux driver from: [http://support.asus.com/download/dow...model=P5KPL-CM](http://support.asus.com/download/dow...model=P5KPL-CM)
(as per my original post)
3) I then transfered the driver via usb stick to my laptop and unpacked the zip. (Actually i unpacked it on windows first as it has a .rar file that i could not unpack on linux Then i packed it up again on windows).
4) cd into <HOME_DIR>/LinuxDrivers/L1e_Lan/l1e-l2e-linux-v1.0.0.4/src
5) then i ran: sudo KBUILD_NOPEDANTIC=1 make
6) then i ran: sudo KBUILD_NOPEDANTIC=1 make install
7) that worked and put a driver in /lib/modules/2.6.24-19-generic/kernel/drivers/net/atl1e/at1le.ko
8 ) i cd into that director and i run: sudo insmod ./atl1e.ko

And the ethernet interface was found and configured.

Now my ifconfig looks like this:
```

eth0      Link encap:Ethernet  HWaddr 00:22:15:57:20:66  
          inet addr:85.216.209.86  Bcast:255.255.255.255  Mask:255.255.252.0
          inet6 addr: fe80::222:15ff:fe57:2066/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:166 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:9
          collisions:0 txqueuelen:1000 
          RX bytes:40048 (39.1 KB)  TX bytes:0 (0.0 B)
          Memory:fe9c0000-fea00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1742 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1742 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:87444 (85.3 KB)  TX bytes:87444 (85.3 KB)

```

And my lhsw -C network looks like this:

```

 lhsw -C network
bash: lhsw: command not found
duri@duri-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: Attansic Technology Corp.
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: b0
       serial: 00:22:15:57:20:66
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=ATL1e driverversion=1.0.0.4 firmware=L1e ip=85.216.209.86 latency=0 module=atl1e multicast=yes

```

But there is another problem, when my NIC is changed, I need to activate my cable modem, I already activated it in windows XP, but it seems it wants to be activated even this time, because when I click on network icon in task bar, it shows in dropdown menu "connect to password protected network 806.1x"

But I don't know network name, I gues it's my provider (chello.sk), so I write this in, in identify I write my user-name given by ISP, my password, and click connect, then it closes up, and pop-ups again with everything blank and network name set to chello@46@sk

Another strange thing is that my IP in windows is 85.216.212.171...

// Ok, manually setting IP address did helped, thank you for the assistance :)

---

### Post by Bucky Ball on 2008-09-04
Is your sudo host problem also fixed??

---

### Post by Hessesian on 2008-09-04
Yap ^^ everything works fine

---

### Post by Bucky Ball on 2008-09-05
Excellent news! Have fun and could you mark this thread as 'solved' (Thread Tools) so others might surf here for a fix to their problem. Cheers and good luck. :)

---

