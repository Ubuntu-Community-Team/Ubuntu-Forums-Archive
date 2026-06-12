---
title: "Wireless in 64 bit"
date: 2008-02-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by mmbates on 2008-02-15
G'day,
I'm using Xubuntu 64 bit on a custom desktop and have had heaps of trouble trying to get wireless working.  I have tried the Asus WL-138G v2 (with Broadcom 4318 chipset) and Netgear WG111 v2 (with rtl8187 chipset).  

The bcm43xx driver does not seem to really work at all.  I've had more success with Ndiswrapper -- driver appears to work, I even got a network connection once or twice, but it was unreliable and very, very, very slow (see this post for details: [http://ubuntuforums.org/showthread.php?p=4319813#post4319813](http://ubuntuforums.org/showthread.php?p=4319813#post4319813)).  I am presuming that the problem I am having has to do with it being 64 bit ... but don't really know I guess.

So, I had a Netgear usb adapter lying around and gave that a try (it works ok on my old 32 bit Xubuntu 7.10 machine).  I tried it both with the default driver and ndiswrapper.  No such luck.

Sooooooo,  I have wasted hours (maybe days...?) trying to get these things to work.  I am ready to chuck in the towel and go and get a friendlier card and was wondering who has had success with what cards?  I have found these links:
[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)
[https://www.fsf.org/resources/hw/net/wireless/cards.html](https://www.fsf.org/resources/hw/net/wireless/cards.html)

thanks to another post -- however, they do not mention anything about 64 bit, and my asus card is actually listed as green (all good) in the first link -- so I thought I would ask other 64 bit ubuntu users.  It would be nice to have one work "out of the box" and also not have propriety software....but, I'm not too fussy at this stage...it just needs to work so that I can get my desktop off the dining room table (where it is now wired to the router) and into my study (where it belongs).

I also read on another post that someone using 64 bit Ubuntu got their Netgear WG111 v2 to work out of the box.  I guess I'm just not that lucky....

cheers,
Michael

---

### Post by Yellow Pasque on 2008-02-17
When you ran ndiswrapper, you did use 64-bit Windows drivers, correct?

---

### Post by mmbates on 2008-02-17
G'day Temuejin,
In short, no.  

But I'm not sure how I could have.  The 64 bit Windows drivers (which is basically the vista drivers right?) for each adapter comes as a Setup.exe -- and when I tried running it in Wine, it got very unhappy and told me it required a 64 bit system (I did make sure that Wine was set to Vista).  I did the normal apt-get to install wine, so I should have the 64 bit version of it installed.

Or am I missing something?

thanks

Michael

---

### Post by Yellow Pasque on 2008-02-17
G'day Michael. Vista comes in 32-bit and 64-bit versions and WINE doesn't emulate 64-bit Windows. Try using ndiswrapper with the drivers I've attached to this post.
EDIT: I've attached the drivers for the ASUS card.

```
sudo apt-get install ndiswrapper
cd <directory where you saved the attached file>
tar xvf wifi-drivers-x64.tar.gz
sudo ndiswrapper -i bcmwl5.inf
```
If that worked, the following command should say "device present"
```
ndiswrapper -l
```

Now:
```
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
sudo echo ndiswrapper >> /etc/modules
```

Now, reboot and when it comes back up, you should have the internet.
If not, run this for us, because we may need to blacklist a non-functional native driver and the info would be helpful:
```
sudo lshw -C network
sudo ethtool wlan0
```

---

### Post by mmbates on 2008-02-17
G'day Temüjin,
Thanks for the suggestion.  I have tried it, and still to no avail.  Upon restart, when it didn't connect automatically, I tried a manual connection.  So here is some output:

```
$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
      ...wired interface info eth0...
  *-network
      ...wired interface info eth1...
  *-network
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth2
       version: 02
       serial: 00:1d:60:6f:00:fd
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.45+Broadcom,02/11/2005, 3.100. latency=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
$ sudo ethtool eth2
Settings for eth2:
        Supports Wake-on: d
        Wake-on: d
        Link detected: no
$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth2      No scan results

$ 
```

the bcm43xx driver is also blacklisted in /etc/modprobe.d/blacklist

Any ideas?

cheers,
Michael

PS. Also, the little light on the card is not on.

PPS. I have IPv6 blacklisted as someone thought that this may be causing the problem -- and I have just never un-blacklisted it.

---

### Post by Jouke74 on 2008-02-17
For Ndiswrapper you need to use Windows XP compatible drivers that are 64 Bit. To see which drivers to choose, go to the ndiswrapper website and check your model wireless card(s) in the compatibility list.

---

### Post by mmbates on 2008-02-17
G'day Jouke74,
I am presuming that the driver in the .tar.gz file that Temüjin uploaded are 64 bit (paritcularly since it has x64 in the name of the tar file).  

The ndiswrapper site says to use the win XP driver -- and so I assume that this is where the driver in the tarfile came from.

cheers,
Michael

---

### Post by Melcar on 2008-02-17
You need a 64bit driver for a 64bit OS.  Unfortunately for me, ndiswrapper causes my system to freeze when I'm using any 64bit OS.

---

### Post by Yellow Pasque on 2008-02-17
What output does this command produce?:
```
cat /etc/network/interfaces
```

For reference, I obtained the drivers from a link in this thread
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

---

### Post by mmbates on 2008-02-17
```

$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


$
```

---

### Post by Yellow Pasque on 2008-02-18
Hey Michael, try adding these lines to that file (open it with sudo gedit /etc/network/interfaces):
```
auto eth2
iface eth2 inet dhcp
```
I'm assuming your ISP uses a dynamic IP (dhcp). If they use static IP's, you'll have to set it up a bit differently. Then restart and see if that does the trick. If it doesn't, see what output this gives you:
```
sudo ethtool eth2
sudo iwconfig
```

---

### Post by mmbates on 2008-02-18
G'day Temüjin,
That seems to have made things a little better.  The card will now scan ok, and I can see mine and my neighbours networks.  But it still seems to be the same problem as previously -- even if I try a manual connect via the command line, it will not associate (see iwconfig readout below).

```
$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

eth2      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:<MY_128HEX_KEY>   Security mode:open
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```
$ sudo ethtool eth2
Settings for eth2:
        Supports Wake-on: d
        Wake-on: d
        Link detected: no
```

During the manual connect, I have tried both:
```
$ sudo iwconfig eth2 essid "wantok"
$ sudo iwconfig eth2 ap 00:14:A5:C5:30:F2
```

The first is the name of my router, and the second is the address (from iwlist scan).
Any other suggestions?

Thanks for all your help.

Michael

EDIT:
I forgot to mention, yes, my ISP supports DHCP, and I usually connect with sudo dhclient ethX

---

### Post by him610 on 2008-02-19
Hello.

FWIW, I experienced a similar problem on at least two of my machines when I was setting up for wireless access a few months ago. 
You should be able to find instructions for doing this in your wireless router manual. I logged into the wireless router using a wired connection and set up the MAC access control option with the MAC address of the wireless card I was trying to connect with.  
I have experienced no wireless network outages since then.

Good luck.

---

### Post by mmbates on 2008-02-19
G'day hgh9mrp,
Thanks for the suggestion.  I logged into my router and it allows any MAC address to log into it that is 802.11 compliant.

I am not sure whether this has anything to do with it, but the device is listed as having a width of 32 bits (see lshw -C network on a previous post), but my system is 64 bit...?

cheers,
Michael

---

### Post by mmbates on 2008-02-28
I finally (think) I have sorted out what the problem is.  There seems to be some kind of conflict between the card and my motherboard, as I dropped the card into my ancient 32 bit system and it worked straight away!

See this post [http://ubuntuforums.org/showthread.php?p=4391951#post4391951](http://ubuntuforums.org/showthread.php?p=4391951#post4391951) (and ones that follow) for the specifics.

cheers,
Michael

---

