---
title: "Original Airport Configuration"
date: 2006-05-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by veganrunner9 on 2006-05-18
Hello,
I have an iBook G3 500mhz with 256mhz of ram with an original airport card installed in it.  I see it in the network configuration as "eth1" and I disable my ethernet connection which works fine to get into the configuration.  I want to detect my wireless connection first so I set it as DHCP but it only enables the card but does not pick up the router.  I don't know if I am doing something wrong but this router worked fine with the airport card when I had Mac OSX on the iBook.  The router is a Netgear MR314.  Any suggestions would be greatly appreciated.](*,)

---

### Post by ssam on 2006-05-19
the airport driver (orinoco) in breezy does not have scanning, so you will need to put in the name (essid) of the router.

if you are running dapper, then it should give you a list of routers to choose from.

---

