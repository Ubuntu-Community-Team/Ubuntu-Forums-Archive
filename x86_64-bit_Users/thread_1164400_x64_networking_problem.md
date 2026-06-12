---
title: "x64 networking problem"
date: 2009-05-19
forum: x86 64-bit Users
---

### Post by EoinDu on 2009-05-19
I created a 64 bit Ubuntu Hardy VM for a svn server to replace an older one that is failing. I got is configured and operating on VMware Workstation with a static IP. When I uploaded to to Virtual Center as an ESX 3.5 64 bit VM on my C7000 blade system I could no longer connect to it.

I went in with the VMware console and can access the server. When I run ifconfig it shows only l0. Eth0 is not there. But when I look at /etc/networks/interfaces it is there with the correct information. I have restarted the network and even rebooted bu get the same thing. 

I am fairly new to Linux but have a pretty good idea of the basics but this has me stopped. Any ideas on why eth0 will not come up? I have about 60 other VMs running on the blades, a mixture of MS and different Linux flavors and have not run across this issue before.

---

