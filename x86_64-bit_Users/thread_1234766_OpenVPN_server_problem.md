---
title: "OpenVPN server problem"
date: 2009-08-08
forum: x86 64-bit Users
---

### Post by BarryDocks on 2009-08-08
Hi there,

I am fairly new to linux but have made good progress in setting up a file and print server via samba for my small business network.

I would like to be able to access the server from home, mainly to provide an off site backup of database files.  I have installed openVPN on the server and created server and client keys plus edited the vars and server.conf files as appropirate.  My problem is that when I run  openvpn /etc/openvpn/server.conf  this is what I get:
> Sat Aug  8 12:35:51 2009 OpenVPN 2.1_rc7 x86_64-pc-linux-gnu [SSL] [LZO2] [EPOLL] built on May  8 2009
Sat Aug  8 12:35:51 2009 Diffie-Hellman initialized with 1024 bit key
Sat Aug  8 12:35:51 2009 /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Sat Aug  8 12:35:51 2009 TLS-Auth MTU parms [ L:1542 D:138 EF:38 EB:0 ET:0 EL:0 ]
Sat Aug  8 12:35:51 2009 TUN/TAP device tun0 opened
Sat Aug  8 12:35:51 2009 TUN/TAP TX queue length set to 100
Sat Aug  8 12:35:51 2009 ifconfig tun0 10.8.0.1 pointopoint 10.8.0.2 mtu 1500
Sat Aug  8 12:35:51 2009 route add -net 10.8.0.0 netmask 255.255.255.0 gw 10.8.0.2
Sat Aug  8 12:35:51 2009 Data Channel MTU parms [ L:1542 D:1450 EF:42 EB:135 ET:0 EL:0 AF:3/1 ]
Sat Aug  8 12:35:51 2009 failed to find GID for group nobody
Sat Aug  8 12:35:51 2009 Exiting


If I comment out "group nobody" from the server.conf file then it runs ok.  Any suggestions?
Thanks

---

