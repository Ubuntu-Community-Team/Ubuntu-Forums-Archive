---
title: "Wlan"
date: 2008-10-06
forum: x86 64-bit Users
---

### Post by Sponzenbroekske on 2008-10-06
I got a problem with ubuntu 8.10 BETA 64bit, i cant connect to wireless internet, at some places I can see the accespoints, but he wont connect, and at home I cant even see my accespoint so i really can't connect at home, i tried giving it in manually but that doesnt work :(

On my 32bit 8.04 no problem

videocard HD radeon 2400: 32bit has a driver, but it seems 64bit doesnt, i cant enable desktopeffects in the 64bit

O what can I do?

---

### Post by norgur on 2008-10-06
purge the network-manager and do the setup manually. this worked for me.
```
sudo apt-get purge network-manager
```

---

### Post by Sponzenbroekske on 2008-10-07
> **norgur said:**
> purge the network-manager and do the setup manually. this worked for me.
```
sudo apt-get purge network-manager
```

and how would I do the set up manually?

---

### Post by norgur on 2008-10-07
the manual setup is stored in the /network/interfaces file.
what you have to set up there is described in the [debian reference]("http://www.debian.org/doc/manuals/reference/ch-gateway.en.html"). This is the guide, I used, but perhaps someone will have got a shorter one at hand ;)

---

### Post by Sponzenbroekske on 2008-10-07
> **norgur said:**
> the manual setup is stored in the /network/interfaces file.
what you have to set up there is described in the [debian reference]("http://www.debian.org/doc/manuals/reference/ch-gateway.en.html"). This is the guide, I used, but perhaps someone will have got a shorter one at hand ;)

oke I get the general idea, but its on a laptop, I use it on more places than 1 to receive internet, is this then still possible?

---

### Post by norgur on 2008-10-08
yes it is. never tried to, but in general it is possible... if this isn't in the reference, perhaps someone else could explain this issue.

---

### Post by Jouke74 on 2008-10-08
Check your system logs. Most likely there is a problem with the combo network-manager (and or Ndiswrapper) and wireless driver used. With all beta tests of new Ubuntu distro's the wireless seems to break one day or the other running updates (at least for my Asus Wl-138 card). 

Report the problem in a bug report for Ibex. Also this discussion should be in the development section of the forum I think. You might get a developer responds over there.

---

### Post by Sponzenbroekske on 2008-10-11
> **Jouke74 said:**
> Check your system logs. Most likely there is a problem with the combo network-manager (and or Ndiswrapper) and wireless driver used. With all beta tests of new Ubuntu distro's the wireless seems to break one day or the other running updates (at least for my Asus Wl-138 card). 

Report the problem in a bug report for Ibex. Also this discussion should be in the development section of the forum I think. You might get a developer responds over there.

Mine just never worked.
BUT toeday I started my system and it connected, so can we state that linux heals :p:p:p:p

---

### Post by Sava8420 on 2008-10-12
So incase the next time you boot up and it decides not to work then you may need a good way to manually config wireless connection.  So here is a good link to setup your wireless manually. [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

---

### Post by Sponzenbroekske on 2008-11-17
Picking up where i left. :(
My network went down again :(
The link from Sava did not solve my problem. I get an error at the 2nd line
```
yannick@asus:~$ sudo dhclient -r wmaster0
[sudo] password for yannick:             
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Sending on   Socket/fallback

```

How can I check my logs?

---

### Post by kj6ythgfg on 2008-11-17
I have the 64 bit ubuntu 2.10 and can't  get my linksys WMP54GS wireless card to work.:confused::(

---

### Post by kj6ythgfg on 2008-11-17
O and I can't find the 64 bit windows drivers for my card

---

### Post by Sponzenbroekske on 2008-11-17
> **kj6ythgfg said:**
> I have the 64 bit ubuntu 2.10 and can't  get my linksys WMP54GS wireless card to work.:confused::(

[http://ubuntuforums.org/showthread.php?t=224121](http://ubuntuforums.org/showthread.php?t=224121)

---

### Post by Sava8420 on 2008-11-18
> **Sponzenbroekske said:**
> Picking up where i left. :(
My network went down again :(
The link from Sava did not solve my problem. I get an error at the 2nd line
```
yannick@asus:~$ sudo dhclient -r wmaster0
[sudo] password for yannick:             
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Sending on   Socket/fallback

```

How can I check my logs?

Ok so I can't tell you how to check your logs but as for the error you are getting it is because you can't use wlanmaster0 as it is not a physical device.  If you run 
```
sudo ifconfig
```
It should show you the list of your network interfaces.  Wlan:master should be shown as well as another wlan interface.  I don't know if your install status is still the beta version but you might try upgrading to the release as it is out and the network manager is greatly improved.

---

### Post by Sponzenbroekske on 2008-11-18
```
yannick@asus:~$ ifconfig                                                                                                                                                            
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:80:02:24                                                                                                                             
          inet addr:192.168.0.115  Bcast:192.168.0.255  Mask:255.255.255.0                                                                                                          
          inet6 addr: fe80::21f:c6ff:fe80:224/64 Scope:Link                                                                                                                         
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1                                                                                                                        
          RX packets:784784 errors:0 dropped:0 overruns:0 frame:0                                                                                                                   
          TX packets:594584 errors:0 dropped:0 overruns:0 carrier:0                                                                                                                 
          collisions:0 txqueuelen:1000                                                                                                                                              
          RX bytes:904572680 (904.5 MB)  TX bytes:48768215 (48.7 MB)                                                                                                                
          Interrupt:248 Base address:0x8000                                                                                                                                         

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host     
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:290 errors:0 dropped:0 overruns:0 frame:0
          TX packets:290 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0                             
          RX bytes:20934 (20.9 KB)  TX bytes:20934 (20.9 KB)    

wlan0     Link encap:Ethernet  HWaddr 00:1f:3b:59:e9:71  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1     
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000                        
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3B-59-E9-71-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

I run sudo apt-get update && sudo apt-get upgrade every day, so I think I'm up-to-date.

---

### Post by kj6ythgfg on 2008-11-23
> **Sponzenbroekske said:**
> [http://ubuntuforums.org/showthread.php?t=224121](http://ubuntuforums.org/showthread.php?t=224121)

thank you!

---

