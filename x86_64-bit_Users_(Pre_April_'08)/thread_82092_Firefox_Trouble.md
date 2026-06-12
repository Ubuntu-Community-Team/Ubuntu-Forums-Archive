---
title: "Firefox Trouble"
date: 2005-10-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by BlackWingAngel on 2005-10-25
Hi, i'm a new italian member and i've some problems with internet connection.. 
I've a router with dhcp server and i've configurated the eth0 right becuase the router's dhcp sever give it a IP address and the command ifconfig shows me the IP but when try to open some sites they don't go, for example:
[www.virgilio.it](www.virgilio.it) works right and on firefox displays the home page
[www.google.com](www.google.com) doesn't work and doesn't display the home page
and the connection is very slow
Why?? 
Sorry for my bad english :P
thanks

---

### Post by jvictor on 2005-11-03
I guess the problem may be that ur Router doestn support IPV6 well and Ubuntu uses IPV6 by default, Plz search this forum on how to disable ipv6, 

Also some routers dont act well as DNS servers, they give wrong ips.. so i suggest you add your ISPs DNS server in  /etc/resolv.conf instead of your router.

I'd similar issues but got it right by doign the above

---

### Post by zekolas on 2005-11-03
In firefox enter
"about:config" in the adress bar and search for a line that says "network.dns.disableIPv6" and set that to "true", see if that helps

---

