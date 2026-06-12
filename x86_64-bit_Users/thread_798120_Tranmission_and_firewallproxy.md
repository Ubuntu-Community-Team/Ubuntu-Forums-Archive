---
title: "Tranmission and firewall/proxy"
date: 2008-05-17
forum: x86 64-bit Users
---

### Post by studunn on 2008-05-17
I am behind a school firewall/proxy and was wondering how i could get transmission to work. Can i manually configure how it connects? and use a port which is not blocked? windows based download clients are blocked but i figured with ubuntu there would be a workaround.

---

### Post by browndruid on 2008-05-18
You may not have to do much actual work at all.

Because the network is configured with Windows, Ubuntu may not be subject to any restrictions that the school would normally impose on your computer. In my school's network, Ubuntu instantly has unbridled network access, can view whatever it wants, and use the Internet without limits.

My advise is to run Ubuntu on one of these computers, see what you can and cannot do, then come back seeking advise on how to bypass your restrictions.

---

### Post by studunn on 2008-05-18
Well i actually have to configure my computer to run on the school proxy. I am running Ubuntu and it is subject to all the normal blocking. what i really need is a bypass or a workaround to get transmission to work. Something like desproxy...

---

### Post by studunn on 2008-05-20
*Bump.*  Any insight would be greatly appreciated.

---

### Post by sarthorks on 2008-11-14
i have a similar problem. can anyone help?

---

### Post by Yellow Pasque on 2008-11-14
You'll just need to use different ports until you find one that's not blocked.
Even on my home network, I had to set up port forwarding so that gnutella-gtk and transmission would work properly.

---

### Post by Arup on 2008-11-14
The transmission in Ubuntu has no way to change ports, it depends on UPnP and if your router doesn't support it, you are in trouble, I would recommend removing it and using the excellent Deluge which has many more features and supports protocol encryption as well as the ability to set ports. It can also import and setup IP black list from Bluetack and set it up like Ktorrent does. Get the deb from getdeb.net, they have a Intrepid x64 version there.

---

### Post by Yellow Pasque on 2008-11-14
> The transmission in Ubuntu has no way to change ports
I have an option to change ports in my Transmission and also an option to enable/disable UPnP. Using Ubuntu Intrepid and Transmission 1.34

---

### Post by Arup on 2008-11-14
> **Temüjin said:**
> I have an option to change ports in my Transmission and also an option to enable/disable UPnP. Using Ubuntu Intrepid and Transmission 1.34

Transmission was pre-installed in my Intrepid x64 and it had no way of changing the port, can you please post a screenshot to indicate where to change the port. I only had UPnP and other options but not port change which was indicated as random.

---

### Post by Yellow Pasque on 2008-11-14
Requested screenshot:

---

### Post by Arup on 2008-11-14
> **Temüjin said:**
> Requested screenshot:

Strange, I not only don't have this feature, I also don't have the blocklist feature as well.

---

