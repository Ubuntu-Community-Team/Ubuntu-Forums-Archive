---
title: "Installing Nessus and Nessus Client in 64bit"
date: 2008-07-09
forum: x86 64-bit Users
---

### Post by bineeshm on 2008-07-09
Hi!

As the signature reads i’m a new user in Linux. 
I've 64bit HP Laptop and trying to install Nessus in this. I downloaded Nessus 3.xxx from web and installed first. Since Nessus site only had Client for 32 bit systems, i tried installing thru Synaptics. But this guy insists on removing Nessus before installing the Client. So was with apt-get and aptitude.
Then when i installed Nessusd via Aptitude, it again recommended me to uninstall Nessus. However, it also gave an option to downgrade Nessus 3.xx to 2.xx. I did so, but still not able to install the front end client.
Can someone help me in figuring whats happening and what should i do to get this done? It would be helpful as a new user i dont want to try any gimmick via comman line and screw up the entire system. I've already reformatted my system thrice in 2 months of using Linux :( .

Thanks in advance for your help!!

Cheers

---

### Post by cariboo on 2008-07-09
The best bet would be to completely uninstall all the nessus files using:

```
sudo aptitude purge nessus nessusd nessusclient
```

Then reinstall from the repositories using Synaptic Package Manager.

It is always better to install programs from the repositories until you've gained some experience using Ubuntu. They always work the first time and you won't run into problems like you are now.

Jim

---

### Post by bineeshm on 2008-07-10
Thanks much, Jim!! Will try from Synaptic and revert if there are any issues.

---

