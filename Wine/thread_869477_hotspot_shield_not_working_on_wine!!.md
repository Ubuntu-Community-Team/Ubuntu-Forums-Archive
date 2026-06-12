---
title: "hotspot shield not working on wine??!!"
date: 2008-07-24
forum: Wine
---

### Post by arsenally on 2008-07-24
wine 1.1
ubuntu hardy 8.04

when i try to install hotspot shield it not install correctlly
these what happen
[IMG]http://dc56.4shared.com/img/56460595/c97883b0/Screenshot.png?sizeM=3[/IMG]

an error occurred installing tap vpn device driver


and then i click ok and contnue installing but not working after that:(

---

### Post by arsenally on 2008-07-28
no re:confused::(:mad:

---

### Post by LinuxRocks713 on 2008-07-28
> **arsenally said:**
> wine 1.1
ubuntu hardy 8.04

when i try to install hotspot shield it not install correctlly
these what happen
[IMG]http://dc56.4shared.com/img/56460595/c97883b0/Screenshot.png?sizeM=3[/IMG]

an error occurred installing tap vpn device driver


and then i click ok and contnue installing but not working after that:(

Why are you installing a firewall-like program in Wine? You're better off with a native linux firewall like Guarddog or gufw.

---

### Post by emredmrl on 2008-08-20
> **LinuxRocks713 said:**
> Why are you installing a firewall-like program in Wine? You're better off with a native linux firewall like Guarddog or gufw.

Actually this is not a firewall-like program. Hotspot Shield is a VPN application which enables you to connect the servers based on the US and get a US-based IP. This feature enables you browse the websites that are prepared for US residants only.

And this information does not change anything. I as well cannot use Hotspot Shield in Ubuntu.

---

### Post by s.l.i.m on 2009-09-22
Is something on Ubuntu that can replace HotSpot shield ?

---

### Post by 569874123 on 2009-09-23
> **emredmrl said:**
> Actually this is not a firewall-like program. Hotspot Shield is a VPN application which enables you to connect the servers based on the US and get a US-based IP. This feature enables you browse the websites that are prepared for US residants only.

And this information does not change anything. I as well cannot use Hotspot Shield in Ubuntu.

Windows alternatives are [http://www.anonymizer.com/](http://www.anonymizer.com/) and [http://www.proxyway.com/](http://www.proxyway.com/).

---

### Post by kkostasp on 2011-09-17
> **s.l.i.m said:**
> Is something on Ubuntu that can replace HotSpot shield ?

Well what I did in the past was to download a VpnClient for windows (NOT HotspotShield) which is usually supporting OpenVpn and *install* it in wine (well Iuse PlayOnLinux but a new wine bottle would suffice), I digg into the installed version and look for a "ca.crt", "clien.crt" and "client.key" file (actual names might differ) and also have a look in the client.conf or client.ovpn ie. the client configuration text file.

Copy them to Linux (Fedora I am sorry) and use Network Manager to create a new OpenVPN account. You of course need to install network manager (this is installed by default in most distributions) and open vpn:

yum install openvpn 

or as you chaps are used to:

sudo apt-get install openvpn (???)

Point to the certificates you just copied over and use the proxy/port you found in the client.conf file of the windoze distro.

BTW. you can now delete the wine bottle alltogether no need for windoze junck in your disk!

A word o caution: some providers use openvpn windoze specific stuff ex:  "push ip-win32" and openvpn breaks in network manager (well would be interested in a suggestion on how to make it work)

Personally I use SecurityKiss for US based address annomizer they allow ports 80 and 433 for their free version but speeds are excellent 1.5Mb/s (they offer other addresses in Europe as well)

K.

---

