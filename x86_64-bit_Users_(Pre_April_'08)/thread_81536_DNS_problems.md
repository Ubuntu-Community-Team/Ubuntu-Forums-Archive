---
title: "DNS problems"
date: 2005-10-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by YR600 on 2005-10-24
Hi,

I'm new to Linux, just installed the amd64 version of ubuntu this weekend to see if I could replace windows, install was fine no problem at all. It seems like everything has been picked up straight away as well (don;t know how to tell if my ati card is installed and using 3D acceleration?). I just have a problem with accessing the internet from firefox, gaim or synaptic.

Im connected via an ADSL router which i can login to from ubuntu and I can ping all web addresses as well. but for some reason firefox and gaim won't connect unless I either remove the ipv6 setting or put the DNS servers in and delete the router address. the only problem with this beeing that if I turn ipv6 off only firefox works and if I manually enter the DNS for my ISP everything works, but when I reboot they are not saved?

Any help would be greatly appreciated.

---

### Post by mlomker on 2005-10-24
You can install resolvconf.  Look at [this thread.]("http://ubuntuforums.org/showthread.php?t=78424")

The real problem is that your router is supposed to be acting as your DNS server but either it is malfunctioning or your ISP's DNS servers are misbehaving...one of the two.

---

### Post by YR600 on 2005-10-24
Thank you for the reply. 

My router works fine under Windows XP and still does right now.

Surely if it works in XP it will work in Linux right? i mean the router doesn't care what operating system im running does it?

Cheers

---

### Post by RAOF on 2005-10-24
[QUOTE=YR600]Thank you for the reply. 

My router works fine under Windows XP and still does right now.

Surely if it works in XP it will work in Linux right? i mean the router doesn't care what operating system im running does it?

Cheers[/QUOTE]
No, actually.  XP won't be using IPv6, and ubuntu does by default.  If your router's IPv6 support is broken (as it apparently is for many consumer gateways), it'll work in XP but not ubuntu...

---

### Post by mlomker on 2005-10-25
> Surely if it works in XP it will work in Linux right? i mean the router doesn't care what operating system im running does it?


If the DNS server was written with just Windows in mind (which wouldn't be out of the question) then it might not be 100% up to spec.  You said that Ubuntu works when you plug in a different DNS server into resolv.conf, so that seems likely to me.

---

### Post by stream303 on 2006-01-17
[QUOTE=YR600]
Im connected via an ADSL router which i can login to from ubuntu and I can ping all web addresses as well. but for some reason firefox and gaim won't connect unless I either remove the ipv6 setting or put the DNS servers in and delete the router address. the only problem with this beeing that if I turn ipv6 off only firefox works and if I manually enter the DNS for my ISP everything works, but when I reboot they are not saved?[/QUOTE]

Sounds like your /etc/resolv.conf is getting overwritten by dhclient upon reboot pointing to the router's internal dns server rather than using your isp's nameservers.

Since you know what your isp's dns nameservers addresses are, edit your **/etc/dhcp3/dhclient.conf** file, and just before the request line, add this: (using real addresses of course)
[B]
supersede domain-name-servers 123.45.678.90, 123.45.689.91;[/B]

Just separate with a comma and place a semicolon at the end.
Now your /etc/resolv.conf will always have your desired nameserver addresses, rather than pointing to the one inside your router.

---

