---
title: "no internet"
date: 2008-09-29
forum: x86 64-bit Users
---

### Post by Bloemetjesgordijn on 2008-09-29
Hi guys,

Please help me out here. For some reason my Ubuntu PC(1) internet doesnt work. Its driving me up the walls

Things tried:
- ipv6 turned off / on (no luck)
- dhpc on vs floating mode (no success)
- pinged other Ubuntu PC (works) 
- changed cable (no effect)
- reset router (no result)
- resinstalled ubuntu (not home folder) (guess what -didnt work)

To make it more difficult:
PC 1 with Ubuntudoesnt work
PC 1 & 2 both Ubuntu simultanious dont work
PC 2 with Ubuntu alone works
PC 2 Ubuntu and PC 3 Wind**s works


Please help me out here, I have done everything and at this moment it feels like I am going down **** creek without paddles


Cheerz

Bloemetjesgordijn

:confused:

---

### Post by titico on 2008-09-29
Try to re-install drivers and packages for the wired/wireless device.
If you are using a wireless encrypted connection try to disable the security key, if that works you need to setup it manually if you want the security back.

---

### Post by Crafty Kisses on 2008-09-29
Post the results of this command:
```
lshw -C network
```

---

### Post by Bloemetjesgordijn on 2008-09-30
@ titico
Thx for you reply. But it worked before (after a live CD install) and I just done a refresh install. Also I can ping. So therefore I dont think it is a driver issue. 

BTW Its a wired connection, not wireless. 

@ Codename

Thx I will give it a go when I get home and post the results.

Cheerz

Bloemetjesgordijn

---

### Post by Bloemetjesgordijn on 2008-09-30
sorry double post

---

### Post by Bloemetjesgordijn on 2008-09-30
sudo lshw -C network

*-network
	description: Ethernet interface
	product: RTL8111/8168B PCI Express Gigabit Ethernet contoller
	vendor: Realtek Semiconductor Co., Ltd
	physical id: 0
	bus info: pci@0000:02.0
	logical name: eth0
	version: 02
	serial: 00:1f:do:51:c2:26
	capacity: 1 GB/s
	width: 64 bits
	clock: 33MHz
	capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duples=half latency=0 link=0 module=r8169 multicast=yes port=twisted pair


To make it more strange *scratch that* bizar.....
As soon as I power up HTPC, the internet connection of my laptop fails
and no internet cables are connected to my HTPC!!!!

Its getting more strange by the minute

If my HTPC is off and I run ADSL speedtest I get 1456.9 KByte/sec. As soon as I power up my HTPC (no cables connected) I dont even get the internet page.

I am not kidding and I cant explain it!!
 
please help me out here

Kind regard

Bloemetjesgordijn

---

### Post by Sef on 2008-10-01
Are you using Mythbuntu?  If not, what programs have you installed for you HTPC?

I would uninstall the programs one at a time and see if your internet connection works without x program.

---

### Post by dabl on 2008-10-01
You didn't install 8.10 Alpha 6, did you?  If so, you might be a victim of the blacklisted e1000e Gigabit ethernet driver module.  Check the first sticky here:

[http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346)

---

### Post by Yellow Pasque on 2008-10-01
> **dabl said:**
> You didn't install 8.10 Alpha 6, did you?  If so, you might be a victim of the blacklisted e1000e Gigabit ethernet driver module.  Check the first sticky here:

[http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346)
His/her LAN is a Realtek chip which uses the r8169 module. It is not affected by this.

---

### Post by Bloemetjesgordijn on 2008-10-01
Thanks you guys.

As I told in my previous post, I reinstalled Ubuntu and this didnt help. This made me think it wasnt an OS issue. 

To verify this, I had to install a Win***s OS. With the new OS still no internet.

So my conclusion is: its an HW issue. A very strange HW issue, but still. 

So if you guys dont have any bright ideas, I am going to RMA my motherboard :(

cya

Bloemetjesgordijn

@ sef,
It was Ubuntu (with all updates), add. I had installed:
gnome do (great program)
kiba docks
amarok (for my +30.000 songs)
powernowd
opera
hellanzb
blueman (for my BT keyboard)
irserver (for my HTPC)
vlc
and many more

---

