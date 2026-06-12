---
title: "[SOLVED] Compaq wireless"
date: 2008-09-25
forum: x86 64-bit Users
---

### Post by iv2101 on 2008-09-25
I have the following wireless card: 
```

07:00.0 Network controller: Atheros Communications Inc. Unknown device 002a (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 1381
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at c2000000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

```

I tried several ways of installing the necessary drivers but failed:( This included downloading/compiling madwifi drivers and adding ath9k, ath_hal, ath_pci modules to /etc/modules at various times.

I don't see wireless options in network manager and iwconfig gives
```

lo        no wireless extensions.

eth0      no wireless extensions.
```

I am very eager to get this working! Please help!

---

### Post by pytheas22 on 2008-09-25
Please post the output of the following commands:
```

lspci -nn | grep -i atheros
lshw -C Network
```

That will help to figure out what to do (the stuff you provided in your first post is useful, but it would be good to get a bit more information from the commands above).

---

### Post by iv2101 on 2008-09-25
Here is the output.
```

07:00.0 Network controller [0280]: Atheros Communications Inc. Unknown device [168c:002a] (rev 01)
```

and (next one run as root)
```

  *-network               
       description: Ethernet interface
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1d:72:71:39:0c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.10.107 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0


```

---

### Post by NullHead on 2008-09-25
Do you happen to know what kind of network card it is?

EDIT: btw, you don't really need to know the card model ... I'd just use this script: [http://ubuntuforums.org/showpost.php?p=5535562&postcount=3](http://ubuntuforums.org/showpost.php?p=5535562&postcount=3) It should get you going ;)

---

### Post by pytheas22 on 2008-09-25
This chipset (Atheros 168c:002a) should work using the ath9k drivers.  I helped someone with this exact same hardware a couple of months ago, also on 64-bit Ubuntu, and he got it working.

Please try following the instructions in [this post]("http://ubuntuforums.org/showpost.php?p=5535562&postcount=3"); that's what solved it for him.  If after running that script things still don't work, please reboot, and post the output of:
```

lshw -C Network
dmesg | grep -e ath -e rror
sudo iwlist scan
```

---

### Post by rbringh on 2008-09-25
This is what got my Atheros working on my HP DV9910US. Really works well.

[http://ubuntuforums.org/showthread.php?t=816780](http://ubuntuforums.org/showthread.php?t=816780)

---

### Post by iv2101 on 2008-09-25
Wow. thanks for all the replies. Let me go through these one by one...

---

### Post by iv2101 on 2008-09-25
> **NullHead said:**
> Do you happen to know what kind of network card it is?

EDIT: btw, you don't really need to know the card model ... I'd just use this script: [http://ubuntuforums.org/showpost.php?p=5535562&postcount=3](http://ubuntuforums.org/showpost.php?p=5535562&postcount=3) It should get you going ;)

This script did the job for me! Thanks!

---

### Post by NullHead on 2008-09-25
You're welcome! 

Mark the thread as solved as long as it truly is solved. Thread tools>Mark thread as solved.

---

### Post by iv2101 on 2008-09-25
Yeah, I think I might want to rescind that. The script provided by nullhead generated a deb file that installed ok. Then Network Manager showed available wireless networks (I thought this resolved the issue). I did not manage to connect to any of them though. Now, after another reboot no wireless networks are shown. 
I'm sitting right by my router.

---

### Post by pytheas22 on 2008-09-25
Can you connect with encryption turned off?

You may also want to try using [wicd]("http://wicd.sourceforge.net") instead of Network Manager.  wicd will require you to uninstall NM; if you want it back later, just type: 'sudo apt-get install network-manager-gnome'.

---

### Post by NullHead on 2008-09-25
Perhaps use a cable if you've got a desktop; if laptop, best try this: ```
echo 'ath9k' | sudo tee -a /etc/modules
```Reboot and give it a try.

Network manager **will** work with ath9k. I use it myself.

---

### Post by Vakman on 2008-09-25
I just got my Wireless working with my new Compaq laptop yesterday. I did have to turn the encryption off. Try this [http://ubuntuforums.org/showpost.php?p=5545069&postcount=5](http://ubuntuforums.org/showpost.php?p=5545069&postcount=5)
Take the direct download on there, install it. Then go into your etc/modules and add a line that says
> ath9k
Restart and you should be fine. I had to have encryption off though.

---

### Post by NullHead on 2008-09-25
> **Thisislaw said:**
> I just got my Wireless working with my new Compaq laptop yesterday. I did have to turn the encryption off. Try this [http://ubuntuforums.org/showpost.php?p=5545069&postcount=5](http://ubuntuforums.org/showpost.php?p=5545069&postcount=5)
Take the direct download on there, install it. Then go into your etc/modules and add a line that says

Restart and you should be fine. I had to have encryption off though.

He's already got ath9k working, but it doesn't seem to be loading when he boots. The encryption is interesting ... I have an atheros card that works very nicely with ath9k and encryption works too :S

---

### Post by pytheas22 on 2008-09-25
> Take the direct download on there, install it. Then go into your etc/modules and add a line that says
Quote:
ath9k 
> 
Perhaps use a cable if you've got a desktop; if laptop, best try this:
Code:

echo 'ath9k' | sudo tee -a /etc/modules

Reboot and give it a try.

These suggestions assume that the problem is that the ath9k module is not loaded, which can't be the issue.  If the original poster can see wireless networks, then ath9k itself is loaded properly; there just seems to be a problem negotiating the connection.

That's why I'd suggest wicd; it deals with WPA1/2 in a different way than NM and sometimes can connect where NM can't.

---

### Post by Vakman on 2008-09-25
> **NullHead said:**
> He's already got ath9k working, but it doesn't seem to be loading when he boots. The encryption is interesting ... I have an atheros card that works very nicely with ath9k and encryption works too :S
Oh, you have encryption working, lucky you :lolflag:
You all comment fast, I miss many posts. Either way, it took me a while yesterday. Just curious, with your connection, does it show you like you have a poor connection when you really don't? And about the not loading, what does it say in the Restricted Driver Manager? I know mine will show up there, does it say it is in use?

---

### Post by NullHead on 2008-09-25
I don't think mine shows in there because mine was compiled into my custom kernel. My connection shows 3 out of 5 bars in NM manage, but I only get 1mb/s out of the 130 I'm supposed to get with my wireless N connection.

---

### Post by Vakman on 2008-09-25
Ah you have a custom kernel, no it probably would not show up. I meant for the OP on that part either way :lolflag:
And all right, was just curious. Now back to what needs to be fixed... And pytheas22 sounds correct, he is right, the module being loaded can't be the issue. Hm, I have never seen something like this really.

---

### Post by NullHead on 2008-09-25
What if you try loading ath9k, *"sudo modprobe ath9k"* and check the last 10 lines or so of the command *"dmesg"* just paste the output of the last 10 lines of dmesg in a quote here.

---

### Post by iv2101 on 2008-09-25
Here is the output: 

```
[  681.124534] eth0: no link during initialization.
[  681.125794] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  680.574882] ForceXPAon: 0
[  680.603678] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  681.334402] wlan0: authenticate with AP 00:1c:10:3c:85:fa
[  681.530181] wlan0: authenticate with AP 00:1c:10:3c:85:fa
[  681.729671] wlan0: authenticate with AP 00:1c:10:3c:85:fa
[  681.933464] wlan0: authentication with AP 00:1c:10:3c:85:fa timed out
[  746.421830] eth0: link up.
[  746.422811] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  749.696185] ForceXPAon: 0
[  749.939748] ForceXPAon: 0
[  750.127350] ForceXPAon: 0
[  750.367013] ForceXPAon: 0
[  750.430912] ForceXPAon: 0
[  750.494799] ForceXPAon: 0
[  750.558703] ForceXPAon: 0
[  750.626562] ForceXPAon: 0
[  750.690449] ForceXPAon: 0
[  750.754337] ForceXPAon: 0
[  750.818078] ForceXPAon: 0
[  750.882055] ForceXPAon: 0
[  750.945970] ForceXPAon: 0
[  751.009850] ForceXPAon: 0
[  751.077734] ForceXPAon: 0
[  751.141622] ForceXPAon: 0
[  751.205529] ForceXPAon: 0
[  763.213468] eth0: no IPv6 routers present

```

I installed wicd but still can't connect. No connection with or without encryption. 

I see the list of networks, i try to connect, but I don't get an ip address

---

### Post by NullHead on 2008-09-25
And if you use wicd to set a static IP address?

---

### Post by iv2101 on 2008-09-25
it says there is a "connection", but i can't load pages and ping. I tried both with and without encryption. and yes, ath9k is loaded:

```

$ lsmod |grep ath
ath9k                 271544  0 
mac80211              267904  1 ath9k
led_class               7176  1 ath9k

```

---

### Post by pytheas22 on 2008-09-25
iv2101,

Could you please clarify where you are (sorry to ask, but there are a lot of posts and I'm not sure what has and hasn't worked).  Can you:

1. connect to an unencrypted network?
2. get an IP address via dhcp using wicd (even if you can't actually load web pages with it)?

If you can get an IP but can't load pages, what is the output of:

```
cat /etc/resolv.conf
host google.com
ping google.com
ping 64.233.187.99
```

---

### Post by iv2101 on 2008-09-27
I cannot connect to unecrypted networks. I don't know how to "get an IP address via dhcp using wicd". If you mean setting a static IP, then no, I can't ping anywhere. I tried with wicd and NetworkManager.
Thanks for any help

---

### Post by Yellow Pasque on 2008-09-28
Can you post output of:
```
iwconfig
cat /etc/network/interfaces/
```

---

### Post by iv2101 on 2008-09-28
Here it is:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=23 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```


```
auto lo
iface lo inet loopback
```

---

### Post by Yellow Pasque on 2008-09-28
Try adding wlan0 to the interfaces file so it gets brought up at boot.
```
gksudo gedit /etc/network/interfaces
```
Here's mine as an example. My network is unencrypted and named 'Harvest':
```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid Harvest
```

---

### Post by iv2101 on 2008-09-28
My /etc/network/interfaces is now 

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid mynetwork

I still can't connect.

---

### Post by pytheas22 on 2008-09-28
> I don't know how to "get an IP address via dhcp using wicd"

dhcp (aka dynamic) IP addresses are what 99% of people use at home.  Unless you know that you need static IP, you shouldn't use it, as it won't work.

wicd should connect with a dhcp address by default--unless you check the box under "Advanced Settings" that tells it to use static IP, it will use dynamic IP.  If you click "Connect" in wicd without static IP enabled, does it get you an IP address?

---

### Post by iv2101 on 2008-09-30
No, I can't connect with a dynamic ip. The program waits for about 30 sec in the "getting IP address" phase and then the status changes to "not connected." 

BTW, it is a linksys router and two other laptops (running ubuntu 32bit and ubuntu-eee) connect to it without problems.

---

### Post by pytheas22 on 2008-09-30
The only thing I can think of at this point is that the build of ath9k that you installed happened to have some problem that's causing it not to work.  In that case, compiling ath9k again using different source code might help.  If you want to do that, run:

```

sudo apt-get install build-essential
wget http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-old.tar.bz2
bunzip2 compat-wireless*
tar xf compat-wireless*
cd compat-wireless-2.6-old/
make ###it will take a few minutes here to compile
sudo make install
sudo make unload
sudo make load
```

Another suggestion is to burn a live CD for Intrepid alpha, which has ath9k installed out-of-the-box.  Can you connect there?

---

### Post by iv2101 on 2008-10-01
I am in the process of downloading this driver. There seems to be another problem. I have high-speed internet (>1Mb/s) but this 1.5MB file is taking more than twenty minutes. 

DSL speed result is this:

[HTML]
Download: 160 (Kbps)
Upload: 1108 (Kbps)[/HTML]

```
eth0      Link encap:Ethernet  HWaddr 00:1d:72:71:39:0c  
          inet addr:140.180.191.12  Bcast:140.180.128.0  Mask:255.255.192.0
          inet6 addr: fe80::21d:72ff:fe71:390c/64 &#1044;&#1080;&#1072;&#1087;&#1072;&#1079;&#1086;&#1085;:&#1057;&#1089;&#1099;&#1083;&#1082;&#1072;
          &#1042;&#1042;&#1045;&#1056;&#1061; BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:320920 errors:920 dropped:0 overruns:0 frame:920
          TX packets:12823 errors:0 dropped:0 overruns:0 carrier:0
          &#1082;&#1086;&#1083;&#1083;&#1080;&#1079;&#1080;&#1080;:0 txqueuelen:1000 
          RX bytes:52092334 (49.6 MB)  TX bytes:5283263 (5.0 MB)
          &#1055;&#1088;&#1077;&#1088;&#1074;&#1072;&#1085;&#1086;:253 Base address:0x6000 

```

(note numerous errors)

Could this point to a more serious problem?

---

### Post by pytheas22 on 2008-10-01
hmmm, that's definitely interesting...should have thought to look at this before.  I think it's fair to conclude that the problem most likely does not have anything to do with your wireless driver or card, but with some other part of your networking configuration.

Can other computers connect to your Internet connection without a problem?  Did you try rebooting your router or modem?  Do you have problems like this in other operating systems?

---

### Post by iv2101 on 2008-10-01
Other computers can connect. The only thing i did not try was rebooting the router. Currently I am trying to connect to university wifi - no success here. Tried back home before. I can't reboot the university router:)

Also, I couldn't unload/load all of the modules: two of them didn't work: 
Unloading mac80211...
FATAL: Module mac80211 is in use.
Unloading cfg80211...
FATAL: Module cfg80211 is in use.
(although they probably don't matter).

---

### Post by pytheas22 on 2008-10-01
Could you please post the output of this command:
```

dmesg
```

after you've been using the Internet for a little while (either wired or wireless)?  The output will be very, very long, but hopefully it will contain a clue as to why your networking stack doesn't want to work at normal speed.

---

### Post by NullHead on 2008-10-01
Just put the output of dmesg here; [http://paste.ubuntu.com/](http://paste.ubuntu.com/) not in a post that would end up being huge! :lolflag: Give us the link once you've pasted it in the website I gave.

---

### Post by iv2101 on 2008-10-01
Here it is: 
[http://paste.ubuntu.com/52976/plain/](http://paste.ubuntu.com/52976/plain/)
Thanks in advance for the help guys.

---

### Post by pytheas22 on 2008-10-02
I'm sorry to say that I can't find a single thing in dmesg that would explain the networking problems.  Does anyone else have any ideas?

At this point, the best thing I can think to suggest is to reinstall Ubuntu.  Or you could at least boot to the live CD and see if your ethernet transfers are slow there as well--this would at least let us know whether the problem has developed over time with your current Ubuntu installation, or existed from the beginning.

---

### Post by NullHead on 2008-10-02
Try madwifi instead of ath9k?

---

### Post by iv2101 on 2008-10-02
@pytheas: I think this is what I will try. Maybe it will be more advantageous to wait for Ibex to come out and try that at the end of the month. 
@nullhead: I believe I did try this driver at some point, with no success. It might be however that the problem came about because I kept trying many things. Eg, I installed a 32bit wrapper etc etc etc... 

I will keep you posted, and thanks for all the help.

---

### Post by NullHead on 2008-10-03
I use the svn version of madwifi, and it works great. Better connection than ath9k gives me.

---

### Post by iv2101 on 2008-10-12
So I reinstalled Hardy, compiled the driver, i still the same thing - networks listed, but can't connect. I tried to boot from the Ibex beta cd, but I can't get X to run. xinit or start give the log file ending in:
```

(II) Primary Device is: PCI 02@00:00:0
(WW) NV: Ignoring unsupported device 0x10de0845 at 02@00:00:0
(EE) No devices detected.

Fatal server error:
no screens found
```

:confused:

---

### Post by pytheas22 on 2008-10-12
Do you still see horrible download speeds under your ethernet connection on this new install of Hardy?  If so, I still think that we need to be looking at a lower level than your wireless driver.  But if the ethernet connection is fine now, we can try getting the wireless up using ath9k again.

Also, as for trying out Intrepid (where you do have a much better chance of getting the wireless working with minimal effort), it might work to save a copy of your working xorg.conf file from Hardy, copy it into Intrepid, restart X in Intrepid and see if you still get errors (if you don't know how to do that, I can give more specific instructions).

It might also work to simply upgrade your Hardy system to Intrepid; you can do so by typing:
```

sudo update-manager -d
```

and clicking the appropriate button.  Intrepid is still not officially stable but should be relatively reliable at this point.

---

### Post by iv2101 on 2008-10-13
Doing an upgrade was what solved all the problems. Wireless works (using it now), Nvidia driver works immediately, sound is good. Thanks!

---

### Post by pytheas22 on 2008-10-13
Glad this is finally straightened out, and thanks for positively sticking with all of our (mostly unhelpful) suggestions for all of this time!

---

