---
title: "lan problem on 8.04 64bit"
date: 2008-06-20
forum: x86 64-bit Users
---

### Post by wojtekj on 2008-06-20
hi 
i am ubuntu newbie and i ts my first experience with 64 bit
i will try to descrive the problem  :)

i bring home a new Dell lapptop from vostro family 1710

after 1 installatioon internet and lan were ok
i start upgrade  and after reboot i connot axecss internet 
nor 192.168.1.1 :mad: 

i make a second install and the problem persist (why?)
so i look in /etc/network/interfaces there was only
auto lo
iface lo inet loopback
so i added auto eth0 and after reboot my lan was working

i start upgrade again and after reboot the problem is back
i cannot acess even my localhost :confused:

any suggestions?

Wojtek

---

### Post by cariboo on 2008-06-20
Go to System-->Administration-->Network, click unlock, enter password. Highlight network connection, click properties and then click Roaming Mode in top left corner.

Jim

---

### Post by wojtekj on 2008-06-20
roaming is enabled

i am using wifi now but my lan is still inactive

~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1c:23:56:11:b4  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :1108101562110 overruns:0 frame:0
          TX packets:0 errors:0 dropped:92 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
          Interruption:250 Adresse de base:0x6000 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:2367 erreurs:0 :0 overruns:0 frame:0
          TX packets:2367 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:119995 (117.1 KB) Octets transmis:119995 (117.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:6f:d4:8c  
          inet adr:192.168.1.51  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: fe80::21f:3cff:fe6f:d48c/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:953987 erreurs:0 :0 overruns:0 frame:0
          TX packets:569989 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:1432044275 (1.3 GB) Octets transmis:50887042 (48.5 MB)

---

