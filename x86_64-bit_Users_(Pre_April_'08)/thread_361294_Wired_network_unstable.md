---
title: "Wired network unstable"
date: 2007-02-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by MaLk0 on 2007-02-14
Hi guys!

I have just reinstalled my laptop with Ubuntu Edgy 64 bit insead of the 32 bit version I have been running for a while now. I am having a strange problem with my network connection on my new install. 

My wireless works perfectly, but if I try to connect to a wired network, the connection is very unstable and slow. I can connect to the network and I am assigned an IP from DHCP, but when I try to browse the internet it is very slow and I get disconnected at random. Before I reinstalled I had no problems with this. Any suggestions would be much appreciated!

---

### Post by John.Michael.Kane on 2007-02-14
First things first we going to need the make and model of the wired chip set in your setup.

Also does the stability issues happen when you turn off the wireless card,and only take signal from the wire?

---

### Post by MaLk0 on 2007-02-15
My network card is a Realtek RTL8168/8111 PCI-E Gigabit and my Wireless card is a Intel PRO Wireless 3945ABG. 

I tried to reinstall and go back to ubuntu 6.10 32-bit system, but I still have the same problem! In Windows everything works. In my ubuntu I get a connection sometimes, but after a couple of minutes I loose the connection or it gets very slow/unstable. Never had such a problem before...

---

### Post by MaLk0 on 2007-02-15
And yes, it also happens when I disable wireless and only use wired connection...

---

### Post by bhgrove on 2007-02-15
This worked for me (disable IPv6 )
In the address bar of firefox type **about: config**
in the filter box type **ipv6**
double click on network.dns.disableIPv6 this will set the value to true

Hope this works for you

---

