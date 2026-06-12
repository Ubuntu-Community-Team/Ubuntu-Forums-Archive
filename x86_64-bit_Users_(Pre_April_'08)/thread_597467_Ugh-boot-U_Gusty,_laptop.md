---
title: "Ugh-boot-U Gusty, laptop"
date: 2007-10-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by slacker9876 on 2007-10-30
My experience with Gusty on my Gateway MT3423 has been so poor that I have decided to go back to SUSE. The downside to this is that I will now have not solve my WLAN and Audio problems on what I consider to be an inferior platform. Here are some details of the reason why I need to switch:

1) Kernel Panic - Every cold boot I experience Kernel Panic, I power down, back up and then edit the grub entry to to include 'noapic' then hit "b" to boot. It comes up fine but then next cold boot I have to redo this process ... yes, every cold boot. 

2) WLAN0 - works GREAT on an unsecured, unencrypted AP. The second I try to go WEP or WPA, BAM! The machine stops responding. I even let it like this over night once and it would not come back nor was I able to CTRL+ALT+F*x* to get to a TTY and execute a proper shutdown. This is with the RRL-8185 chipset, it appears Ubuntu uses the RTL8xxx driver but I get no love from wireless.

3) Audio - STAC9200, I know I need not say more, but neither the ALSA 1.0.15 nor sigmatel patch appear to be operable here, and dang they were hard to find. 

4) Torrenting - Sure it is great to use the bittorrent client, if you dont want DHT or multiple streams. Azureus and Limewire both crap out, presumably die to an issue with the 1.6.3 Java I am running. I like to share the many flavors of Linux available with those that have little bandwidth. SO I need a more robust app than the generic BitTorrent client. 

I *really* hate to say this, but this release, most closely resembles a recent Micro$oft windows release. Like Vista, it is a beautified GUI ... with drivers for nothing. I must accept some personal responsibility as I did not properly research the best laptop to get for use with Ubuntu  prior to my purchase. However,  with the explosion of  Linux in general in  the public , I think there should be more testing before release. I am a 3rd year Linux user, mostly GUI but I know how to get around well and I am not afraid of the CLI when I need it. 

Pluses: I love the printer configuration, it is very slick in Gusty. I love the out of the box compiz ... it just works. My hope for this thread is that it will help other whom have similar issues get them fixed. I have spent 20 hours here and on other forums reading, trying to get my baby fixed up. But dang it ... I want the darn thing to boot first time!!!

Thank for listening, I'll monitor the thread and help where I am able. Good luck!

---

### Post by netbandit on 2007-10-30
Are you running 64bit Ubuntu?  Have you tried 32bit Ubuntu?  Unless you are using more than 4GB of RAM (or are trying to do some specific things, like virtualization of 64bit guests), you will most likely find the user experience is better in 32bit.  64bit is nice, but has a few more issues that can undermine the experience.

Just try to get it working in 32bit first.  Once you got that squared away, try 64bit.

-nb

---

### Post by pelle.k on 2007-10-30
> I really hate to say this, but this release, most closely resembles a recent Micro$oft windows release.
This release was *supposed* to be experimental. Can you say that about vista?
But yeah, poorly supported hardware is always a bitch. Blame the manufacturers.
Deluge (gtk)?, Ktorrent (kde)?

Btw, i'm not advocating ubuntu here. If it works poorly you really *should* switch. Whatever works, man.

---

### Post by slacker9876 on 2007-10-31
Actually as an MCSE, I could and would say that about all the M$ products. MS Money was the only program that never gave me a fit LMAO! 

I know it is not Canonical's fault and the additions to Gusty are great. I am still running it on my server, which is a desktop, and all but the audio worked. I added a different sound card and it all works. My only wish is I knew how to code ... I would contribute my making drivers. As it is though financial contributions are all I am able to make to the Linux community. Perhaps some day this may change.

---

### Post by slacker9876 on 2007-10-31
> **netbandit said:**
> Are you running 64bit Ubuntu?  Have you tried 32bit Ubuntu?  Unless you are using more than 4GB of RAM (or are trying to do some specific things, like virtualization of 64bit guests), you will most likely find the user experience is better in 32bit.  64bit is nice, but has a few more issues that can undermine the experience.

Just try to get it working in 32bit first.  Once you got that squared away, try 64bit.

-nb I have a moral objection over that. Why should I run a 32-bit OS on a 64-bit platform? It kills me. Same with HDTV, I have become a TV snob and will not even watch SDTV. This is not an issue because I am a fan of the NFL and NHL so it is all HD anymore.

Fedora 8 comes out in like 10 days, I'll probably try that too.

Either way I do miss the package management of Ubuntu already, not to mention the availability of ALL software, US legal or not, for Ubuntu. YaST is just so damned clunky compared to the CLI of an apt-get statement.

---

### Post by netbandit on 2007-10-31
> 
I have a moral objection over that. Why should I run a 32-bit OS on a 64-bit platform? It kills me. Same with HDTV, I have become a TV snob and will not even watch SDTV. This is not an issue because I am a fan of the NFL and NHL so it is all HD anymore.


I'm not saying that you should run 32bit Ubuntu, but what I am saying is that you should try 32bit to help isolate issues.  If 32bit runs good, but 64bit doesn't, you can start figuring out the problem by seeing what has issues, where the issues occur, etc.  It will also give you a baseline for what expected results should be.  If it doesn't work in 32bit, you will probably have more support options, and be able to track down the problem more quickly.  I don't want 64bit to be a backwater anymore than you do, but the price of living on the edge is having to do a bit more research and try more options (Just like the price you pay for being a HDTV snob means you might not watch shows you used to like because they are in SD

-nb

---

### Post by slacker9876 on 2007-10-31
Yeah, not a bad tip, you are right about that. I have a extra 60GB HDD laying here, perhaps I'll give it a whirl, if nothing else, just to see the response of the system. I have not been able to compile the rtl8185 driver under openSUSE anyhow ... I bet it it 32-bit code lol.

---

### Post by netbandit on 2007-10-31
The only reason I run 64bit at all is to support 8GB of RAM and to virtualize 64bit systems.  It's not like I like having the extra complexity.  :)

-nb

---

### Post by equal on 2007-10-31
Honestly, unless you're running over 4GB RAM in your system, you will NOT notice much difference between a 32 and 64bit OS. It's nowhere near the difference between SD and HDTV. I understand the mentality, I am using the 64bit OS too, in spite of increased difficulty. But that is mostly so I can help iron out the bugs, so that when 4GB+ RAM is standard, 64bit Ubuntu will already be perfected!

---

### Post by slacker9876 on 2007-10-31
Sure it will, the CPU is optimized for 64-bit code, it's like when they add instruction sets to the PPC CPU's, more efficient instruction processing produces better performance. Now is that as big as HDTV and SDTV, well no, but it should be close to VHS vs DVD ....

---

### Post by pelle.k on 2007-11-01
No. I'm afraid it doesn't work that way. The comparison with SD vs HD is not a good one because the resolution is ~ doubled (576i, 1080i), but there are four times as many pixels, and that means four times sharper image.
Software in 64 bit distros are compiled with 64 bit support, but that does *not* mean the software is optimized to run in 64 bit mode effectively. Only in rare cases does it give an actual speed advantage.

You need code that is written to actually run on a 64 bit platform to get everything out of it.

---

### Post by slacker9876 on 2007-11-01
I am not certain you understood my response, I said no it is not as big as HD & SD, rather it is as big as VHS to DVD --- 275i to 420i. To my knowledge the packages that are x86_64 and not 1386 (most of the OS system) *are optimized  *for 64-bit CPU's ...

---

### Post by slacker9876 on 2007-11-01
OK back to the body of the issue here. I have the i386 version installed nowm wpa_supplicant is also installed. When I go to wireless networks my only encryption options are WEP and LEAP ... no WPA? Is this not operable with network manager? Do I need another package?

---

### Post by slacker9876 on 2007-11-11
OK so I loded Fedora 8 today and the sound is fine. Video is a bit jitterey, but I am not using the restricted driver yet. 

I put this laptop on craigslist today. I think a more linux compatiable notebook would better suit me. What are you folks running in the way of laptops (that work)?

---

### Post by galileon on 2007-11-12
> **slacker9876 said:**
> 
1) Kernel Panic - Every cold boot I experience Kernel Panic, I power down, back up and then edit the grub entry to to include 'noapic' then hit "b" to boot. It comes up fine but then next cold boot I have to redo this process ... yes, every cold boot. 


$man grub

EDIT: sorry, its not in the documentation for man grub.
Open a terminal and type sudo nano /boot/grub/menu.lst
Look for your kernel entry and add the noapic there. That way, it will survive the next boot.

If thats what you did, maybe you updated the kernel between two cold boots? If so, the noapic will need to be added to the new kernel entry as well i believe

---

### Post by slacker9876 on 2007-11-12
I had already added that parameter, then it started booting loops. I am going to give it another try, if the sound worked out of the box in Fedora, it will not be long before that support is brought to Ubuntu. Wireless is important but I can just submit and use NDISwrapper.

---

### Post by gils0040 on 2007-12-11
The rtl wifi project has been working on a mac80211 based driver for the rtl8185. It is not *stable* yet but there is a patch available. I applied to patch to the 2.6.23 kernel and the wireless card is working perfectly (including network-manager). I suspect it will be included in the kernel sometime soon, but until then check out the patch at [https://sourceforge.net/tracker/index.php?func=detail&aid=1833847&group_id=186406&atid=917159](https://sourceforge.net/tracker/index.php?func=detail&aid=1833847&group_id=186406&atid=917159). Good luck!

---

### Post by slacker9876 on 2007-12-11
I just reinstalled Vista tonight ... need a winblows laptop in the field, gonna try 7.10 again. Can't get a GEForce GO 6100 driver for XP. I am adding ubuntu tomorrow. I'll give that driver a whirl.

---

### Post by slacker9876 on 2007-12-23
OK, so I have reinstalled Ubuntu 7.10 as dual boot with Vista, since the is NO video driver for this laptop under Windows XP. Everything is the same as before EXCEPT ... post-install I installed the packages for "kubuntu-desktop"

If you look at the attachment WPA2-Personal is somehow automatically supported! Kernel update? I don't know ... but the interface does not actually connect either (wireless still broken). Here is my /etc/network/interfaces

```
auto lo
iface lo inet loopback


iface wlan0 inet dhcp
wpa-psk (key removed by poster)
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA2
wpa-ssid ***AP (also altered)

auto wlan0
```

So I guess, where should I start to look? If I had wireless that would just be killer! Everything looks OK to me so I am not sure why this is not working. Any input is much appreciated.

---

### Post by pelle.k on 2007-12-23
Lets see if the wireless is actually usable;
```
sudo iwlist wlan0 scan
```
(replace wlan0 with you interface name), and i guess it wouldn't hurt if you show the output of;
```
iwconfig
```
```
ifconfig
```
```
dmesg | grep rtl
```
```
dmesg | grep wlan0
```
Again, replace wlan0 with your interface name.

---

### Post by slacker9876 on 2008-01-08
I would day it is working, but not connecting.

```
chris@ubuntu:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:1A:70:58:E9:27
                    ESSID:"Netgear"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Channel:4
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:0  Signal level:0  Noise level:158
                    Extra: Last beacon: 82ms ago
          Cell 02 - Address: 00:1D:7E:67:87:64
                    ESSID:"ColClan"
                    Protocol:IEEE 802.11bg
                    Mode:Master           Channel:1
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:0  Signal level:0  Noise level:158
                    Extra: Last beacon: 1139ms ago
          Cell 03 - Address: 00:17:3F:02:3A:2A
                    ESSID:"rac"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:0  Signal level:0  Noise level:158
                    Extra: Last beacon: 1853ms ago
```

```
chris@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Frequency=2.447 GHz  
          Access Point: Not-Associated   Bit Rate:11 Mb/s   
          Retry:on   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
chris@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:25:48:4D:4C  
          inet addr:192.168.1.114  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:25ff:fe48:4d4c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20790903 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17699655 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1351913578 (1.2 GB)  TX bytes:636173214 (606.7 MB)
          Interrupt:16 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:C0:A8:F1:7C:58  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:8203 dropped:2119 overruns:0 frame:0
          TX packets:32454 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:1363068 (1.2 MB)
          Interrupt:11 Memory:f8852000-f8852100 

```

```
chris@ubuntu:~$ dmesg | grep rtl
[   14.508000] rtl_ieee80211_crypt: registered algorithm 'NULL'
[   14.508000] rtl_ieee80211_crypt: registered algorithm 'TKIP'
[   14.508000] rtl_ieee80211_crypt: registered algorithm 'WEP'
[   14.508000] rtl_ieee80211_crypt: registered algorithm 'CCMP'
[   14.584000] rtl8180: Initializing module
[   14.584000] rtl8180: Wireless extensions version 22
[   14.584000] rtl8180: Initializing proc filesystem
[   14.584000] rtl8180: Configuring chip resources
[   14.584000] rtl8180: Memory mapped space @ 0xb3400000 
[   14.584000] rtl8180: MAC controller is a RTL8185 b/g (V. D)
[   14.584000] rtl8180: This is a MINI-PCI NIC
[   14.584000] rtl8180: Reported EEPROM chip is a 93c46 (1Kbit)
[   14.592000] rtl8180: Card MAC address is 00:c0:a8:f1:7c:58
[   14.608000] rtl8180: EEPROM version 105
[   14.608000] rtl8180: Card reports RF frontend Realtek 8225
[   14.608000] rtl8180: WW:This driver has EXPERIMENTAL support for this chipset.
[   14.608000] rtl8180: WW:use it with care and at your own risk and
[   14.608000] rtl8180: WW:**PLEASE** REPORT SUCCESS/INSUCCESS TO andreamrl@tiscali.it
[   14.608000] rtl8180: Energy threshold: b
[   14.608000] rtl8180: PAPE from CONFIG2: 6
[   14.608000] rtl8180: IRQ 11
[   14.608000] rtl8180: Driver probe completed
[   20.768000] rtl8180: Bringing up iface
[   20.976000] rtl8180: Card successfully reset
[   21.952000] rtl8180: Setting SW wep key
[26064.896000] rtl8180: Setting SW wep key
[26064.948000] rtl8180: Bringing up iface
[26065.156000] rtl8180: Card successfully reset
```

```
chris@ubuntu:~$ dmesg | grep wlan0
[   21.856000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[26066.032000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
chris@ubuntu:~$ 

```

Everything but the last entry looking to be in order. That and the fact that it is not associated, even though it claims to be in the wireless manager.

I gotta say all, I appreciate the help, but should I just but a new laptop? Wireless and sound are just kind of staples ya know.

---

### Post by pelle.k on 2008-01-11
I can probably help you with the sound, cause i've got alsa 1.0.15 packaged in a nice deb, but without wlan there is really no reason to keep trying, i guess.
Have you tried configuring it through knetworkmanager, that is using "roaming mode"?

You could also try installing the "zen" kernel. This is *not* an official kernel, but patched RC kernel straight from the GIT repository (development). You would need to install nvidia through envy (for the zen kernel) though.

I can relate to your problems, since i just bought a new "santa rosa" laptop, and it is not working 100% with gutsy yet....

---

