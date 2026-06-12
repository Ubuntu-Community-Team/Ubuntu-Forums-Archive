---
title: "DNS Problems"
date: 2006-06-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2006-06-30
Compaq R3240 laptop with Broadcom 4306. 

At home I have Comcast cable. At the university I rely on wireless. Previously, under Breezy I had ndiswrapper and all was well. After a fresh install of Dapper I discovered that the bcm43xx driver was too problematic. Sometimes it worked, mostly it didn't. Finally, I blacklisted it and installed ndiswrapper instead. That was yesterday.

Today I took the laptop to the university to check out the wireless. Booted up the computer and, as always, wireless (eth1) was not active and ethernet (eth0) was active. Not a problem -- went into System > Administration > Networking, deactivated eth0 (Ethernet) and activated eth1 (wireless). Logged into my student account and was able to connect anywhere. Satisifed that all was well, I shut down and went home.

Back at home I plugged in the ethernet cable (= to hub, to router, to cable modem), booted the computer, and launched Firefox. I was able to go a few places, but got weird looking pages. When I opened System > Administration > Networking I found that, as always, wireless was inactive and ethernet was active. I selected ethernet and clicked on DNS. Instead of the address of my router as before, it listed the DNS servers for the university. 

I cleared out the entries for the university and removed its name from the "networks to search" box. Then I closed the DNS box, deactivated eth0 and reactivated it. Afterwards it listed no DNS servers or networks to search. Firefox was unable to go anywhere. 

I've tried everything I can think of to get it to go out and find the DNS servers, but to no avail. It used to do this automatically when I booted up, changing to whatever it found, depending on which connection was active. I do note that under Breezy it got the DNS servers, where in Dapper it just enters the address of my router when I am at home. But now it's not getting anything automatically. Also, now I type in the address of my router manually and it still can't go anywhere. This worked yesterday, though. I thought it was strange that it could find the Comcast DNS servers just by listing my router's address in the DNS entries. Before it always needed the actual IP address. And now that seems to be the case again, because in order to get it to work from home I had to type in the addresses of the Comcast DNS servers manually.

I'm sorta dumb about this stuff. How do I get it to automate this?

---

### Post by John Jason Jordan on 2006-06-30
In reading the Help files I discovered that it seems to be woefully out of date. Open the System > Administration > Networking window, click on Help, then Getting Started. The screenshot of the Network Settings window doesn't look like the one in Dapper, or in Breezy either.

I am still trying to figure out why it is not automatically going out to whatever network I am connected to, finding the network's DNS servers, and popping them into /etc/resolv.conf. 

In the meantime, I thought a workaround might be to create "Locations." However, evidently a "Location" use to be called a "Profile." And evidently there used to be a way to save it to file, which seems to be gone. Also, I can't figure out how to edit a "Location" ("Profile").

Any suggestions?

---

