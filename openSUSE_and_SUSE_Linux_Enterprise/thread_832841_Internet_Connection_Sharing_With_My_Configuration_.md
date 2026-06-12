---
title: "Internet Connection Sharing With My Configuration - Help Needed"
date: 2008-06-18
forum: openSUSE and SUSE Linux Enterprise
---

### Post by Vince4Amy on 2008-06-18
[CENTER][IMG]http://www.flickcabin.com/sessions/da39a3ee5e6b4b0d3255bfef95601890afd80709/network2.png[/IMG][/CENTER]

You can see above the configuration of my home network and there's something I could do on XP which I've never been able to figure out on OpenSUSE and that is sharing the Internet Connection between the Secondary computer and Other Computer.

My Broadband Connection comes from the Broadband Router shown above which is sent to a Netgear ME102 Access Point. It then sends the signal wirelessly to another ME102 Access Point. 

This is connected to NIC One (eth0) on the Secondary Computer. I then have another NIC card in the secondary computer (eth1) which shares the Internet connection from NIC One to NIC Two which in turn will allow Internet usage on the Other Computer.

I Can't create a Workgroup or anything because the Other Computer changes on a regular basis because this is where I repair other peoples Windows PC's and run the updates.

So can the Internet connection which is coming through eth0 be shared to go through eth1 and then allow this to work on the Other Computer.

On Windows XP I'd set it to share the connection and then create a Network Bridge between eth0 and eth1.

---

### Post by RedDwarf on 2008-06-19
Not tested. But try installing bridge-utils and read [http://www.linuxfoundation.org/en/Net:Bridge](http://www.linuxfoundation.org/en/Net:Bridge)

---

