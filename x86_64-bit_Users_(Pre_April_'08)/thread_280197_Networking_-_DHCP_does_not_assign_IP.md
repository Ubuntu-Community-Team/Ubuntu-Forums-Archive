---
title: "Networking - DHCP does not assign IP"
date: 2006-10-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by sygin on 2006-10-19
Hi,

I am trying to get Dapper 64-Bit working. Networking is my current problem. Everything works on the 32-bit version.

When using DHCPo n 64-bit system ifconfig informs me that i have not got a inet address. I get a inet6 address but not a inet address.

If I use a static address, I get a inet address but can't ping anything with success.

Thank you
Sygin

---

### Post by Paulo Wageck on 2006-10-19
Hello!

I was just thinking about the same think.

I have got 2 computers on Dapper 64 and since them all file transfers stalls while copying from one machine to another, no matters what I try. 

I have check the connections... firewall.... reseted the router... checked routing... mtu size... 


I can log in... I can see.... I can copy a small file... (ssh, ftp, ping).... 

But when it comes to large files and multiple transfers.... 

I have used FTP inside my home network before.... no problems at all with ubuntu-32... 

fireftp says its a routing problem.

I need to backup some huge data from the notebook... dont wanna do it with dvds (multiple)... 

I am using the current edgy 64 version on the desktop and now foresight linux on the notebook.... 


All my woes started then I tried to upgrade from the command line from the LTS version to the development.

Maybe something is not quite right.... 

Any clues????


Router: Encore Wifi G + 4 ports 

Laptop - Gateway 64 4000 mobile (mx75xx)

Desktop - Custom Athlon 64 + asus k8 board.

I will try to backlist ipv6....

my home network setup is:

192.168.123.254 - router/gw
192.168.123.* computers 1 (150) and 2 (114)
netmask 255.255.255.0


when i try a fresh install it says dhcp is not working....
(ubuntu server 64).


i can give more data...

---

