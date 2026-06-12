---
title: "Internet Connection Problem - think DNS"
date: 2006-01-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by kpurcell on 2006-01-27
I am trying to connect to the Internet via Ubuntu on a static IP behind a Linksys WRE54G router.  I can access the router via IP and I can ping my ISP (the address listed in my router's status page) but I cannot surf using names like yahoo.com.  I don't know any numerical addresses so not sure if I can ping anything other than my ISP.

How do I fix this?

---

### Post by John Jason Jordan on 2006-01-27
[QUOTE=kpurcell]I am trying to connect to the Internet via Ubuntu on a static IP behind a Linksys WRE54G router.  I can access the router via IP and I can ping my ISP (the address listed in my router's status page) but I cannot surf using names like yahoo.com.  I don't know any numerical addresses so not sure if I can ping anything other than my ISP.
How do I fix this?[/QUOTE]
God knows I know practically nothing about networking, but I just got through figuring out a similar problem. 

The nameservers have to be listed in /etc/resolv.conf. When you connect to your ISP something causes the contents of this file to be updated to whatever the IP addresses of your ISP's nameservers are. For example, at this time my /etc/resolv.conf file says:
```
search Comcast.net
nameserver 216.148.227.79
nameserver 204.127.202.19
```
I know that if these are wrong, then I will not be able to resolve a name like yahoo.com and I will be able to surf only to places where I know the IP address, which is like nowhere.

You need to get the IP addresses of your ISP's nameservers into that file. As far as I know this is supposed to happen automatically when you connect to your ISP, so maybe something else is wrong. In the meantime, ask your ISP for the IP addresses of their nameserver(s) and manually put them in /etc/resolv.conf. You can edit it with Gedit, but open Gedit from the command line with sudo or it will be read only and you won't be able to save the changes. And save the original file under a different name first, of course.

---

### Post by kpurcell on 2006-01-27
Well, since  am now replying using Firefox in Ubunut 5.10 you know that I fixed this pooblem.  I simply entered my router's address in the DNS tab in netowrking.  Now all is better.  Still having other issue, but will ask them under a different heading.

---

