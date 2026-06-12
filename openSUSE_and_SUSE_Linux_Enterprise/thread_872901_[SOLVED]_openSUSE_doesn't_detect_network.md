---
title: "[SOLVED] openSUSE doesn't detect network"
date: 2008-07-28
forum: openSUSE and SUSE Linux Enterprise
---

### Post by meindian523 on 2008-07-28
Hi,
I'm running openSUSE 11.0 and can't connect to my wired network.I don't have a wireless network.The card is onboard and it's Realtek 8139 something.My motherboard is Intel D101GGC.
<rant>
Can't openSUSE have some small network icon which shows whether you are connected or not?</rant>
I found that it's not working by trying to ping successively http://www.google.com,www.google.com,208.67.222.222(openDNS server) and 192.168.1.1 which is the address for my D-Link DSL 502T router.
Following a thread over at the openSUSE forums,all this data from my Ubuntu 8.04.1 install:

ifconfig
```
easwarh@l1nuxr0cks:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:76:ce:f3:d1  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:76ff:fece:f3d1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2203 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2355 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1561410 (1.4 MB)  TX bytes:325743 (318.1 KB)
          Interrupt:20 Base address:0xde00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1558 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1558 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:65436 (63.9 KB)  TX bytes:65436 (63.9 KB)

easwarh@l1nuxr0cks:~$ 
```
lspci|grep ethernet
```
easwarh@l1nuxr0cks:~$ sudo lspci|grep thernet
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
easwarh@l1nuxr0cks:~$ 
```
iwconfig
```
easwarh@l1nuxr0cks:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

easwarh@l1nuxr0cks:~$ 

```
route
```
easwarh@l1nuxr0cks:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
easwarh@l1nuxr0cks:~$ 

```

---

### Post by Growbag on 2008-07-28
That won't help much with the suse install though.

Can you do the same commands under suse and post here?

Also when you are in suse, run Yast and see if your adapter is actually enabled (network devices -> network settings).

You might have to add or edit etc'.

....and the network monitoring applet is part of KDE or Gnome, search in yast for applet or network, there are a few in there.  I use gkrellm as it does other cool things too :).

---

### Post by dca on 2008-07-28
In GNOME, there should be your network manager icon, it'll look different because it runs .7 vers...  You should be able to find wired tab and create new profile for whatever your location is.  It has a default one of 'eth0' but I usually create a new one from scratch that says 'home' or 'work'.  Don't know if KDE has something similar in the tray or not after default install...  Wasn't too impressed w/ KDE4 because of small glitches so never got that for into it.

---

### Post by meindian523 on 2008-07-29
I didn't install GNOME.:(

---

### Post by lxuser2008-X on 2008-07-31
> **meindian523 said:**
> I didn't install GNOME.:(
Ok, I am using 10.3 Kde 3.5.7 and KNetworkManager 0.2 is my network (Internet) manager. It works really well, though sometimes I need to reactivate the "wired network" tab by clicking on it. You should first setup your network card with Yast and set it up so that it is managed by KNetworkManager. Yast----->Network Devices---->Network Card

You will find the KnetworkManager icon under System--->Desktop Applet or start it at the console with following command:
xxx@xxxx:~> knetworkmanager

Once your network card is configured with Yast and you have KNetworkManger setup to control your network, it should start at boot up.

Cheers

PS: You can get proper support at: [http://forums.opensuse.org/](http://forums.opensuse.org/) or via news server (NNTP): forums.novell.com

---

### Post by meindian523 on 2008-07-31
I would update if I had network,wouldn't I?I think the bug lies in me not being able to figure out the various options available.I've a simple config for wired network,address is dynamic and allotted via DHCP to my router(192.168.1.1) and that gives the box address(192.168.1.2)No usernames,no passwords.Plain old DSL via the telephone(landline) line.

---

### Post by lxuser2008-X on 2008-07-31
> **meindian523 said:**
> I would update if I had network,wouldn't I?I think the bug lies in me not being able to figure out the various options available.I've a simple config for wired network,address is dynamic and allotted via DHCP to my router(192.168.1.1) and that gives the box address(192.168.1.2)No usernames,no passwords.Plain old DSL via the telephone(landline) line.

Sorry, the update/s seem to be more related to wireless stuff than to Ethernet connections. Also, one can install rpms without being online, i.e. download the required package/s and install offline. I have provided some links below for your perusal and future reference.

As it stands, it seems I have the same (or very similar) card as you and I had no issues going online with the live cds of openSUSE 11.0, and neither should you. Just go to Yast and setup your card, as I previously advised, and you should be Ok!

The following is from the Yast info of my card:
Toshiba America Info RTL-8139/8139C/8139C+ 
Device Name: eth-eth0
Started automatically on cable connection
IP address assigned using DHCP


Network Setup Method
Use NetworkManager to have a desktop applet manage connections 
for all interfaces. It is well-suited to switching among wired 
and multiple wireless networks.

================

Some info for the latest NetworkManager-kde:

NetworkManager-kde-0.7r826733-7.1.i586.rpm
[http://download.opensuse.org/repositories/KDE:/Backports/openSUSE_11.0/i586/](http://download.opensuse.org/repositories/KDE:/Backports/openSUSE_11.0/i586/)

Changelog:
* Thu Jul 17 22:00:00 2008 [email]wstephenson@suse.de[/email]

- Don't autostart in other desktops

* Tue Jul  1 22:00:00 2008 [email]hschaa@suse.de[/email]

- Update to r826733
  * Fix crash after resuming from s2ram (bnc#404896)
  * Add tooltips to the tray icon
  * Add WPA-EAP TTLS and PEAP support


-------------------

[   ] NetworkManager-kde-0.7r815970_0.7r821737-1.1_0.1.i586.delta.rpm
[   ] NetworkManager-kde-0.7r821737-0.1.i586.rpm 
[http://download.opensuse.org/update/11.0/rpm/i586/](http://download.opensuse.org/update/11.0/rpm/i586/)

* Mon Jun 16 22:00:00 2008 [email]hschaa@suse.de[/email]
Changelog:
- Update to r821121
  * Select the correct security mode for wireless connections
  * Notify about NetworkManager not running (bnc#383195)
  * Show if a wireless network is encrypted (bnc#393070)
  * Fix listing available networks (bnc#397589)
  * Fix crash when NeworkManager is restarted (bnc#397678)
  * Allow user-defined notifications (bnc#398425)
  * Update translations
  * Several smaller bugfixes

-----------------------------

Webpin - Software Search
[http://packages.opensuse-community.org/](http://packages.opensuse-community.org/)

---

### Post by meindian523 on 2008-08-02
Well,Net is working right now,but I'm unsure whether the configuration is finished because there have been a plethora of SIG11's and problems with timeouts,and other assorted problems while connecting to download.opensuse.org to get the updates.
I'm running as root,and too scared to logout in case I lose network again.
Could someone tell me a method to verify whether the config is done,preferably by looking at some configuration text file rather than going through the fancy GUI?

---

### Post by meindian523 on 2008-08-27
The problem was solved,and I didn't lose network after rebooting.Thanks for everyone who helped.

---

