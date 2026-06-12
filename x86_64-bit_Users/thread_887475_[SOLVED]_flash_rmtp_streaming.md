---
title: "[SOLVED] flash rmtp streaming"
date: 2008-08-12
forum: x86 64-bit Users
---

### Post by dparry on 2008-08-12
Hello,
I'm running 8.04 64 bit and can't get Flash 9 or 10RC to connect on its default port 1935 via RMTP.

There's a port test [http://www.flashcomguru.com/apps/port_test/index.cfm]("http://www.flashcomguru.com/apps/port_test/index.cfm") that shows no connection made.

Flash appears to be running OK in all other respects, so I'm wondering if its a connectivity or authorization issue.  I've checked that ufw is disabled, and am stumped on how to proceed.

Thanks,
David

---

### Post by dparry on 2008-08-13
I've carried out further tests installing VMware server with an XP guest OS and bridged networking.  When IE6 on the guest XP goes to the port test, flash connects correctly.  So it looks like its an issue with Flash not connectivity.

---

### Post by dparry on 2008-08-15
Finally resolved this issue by installing 32bit firefox with the 32bit flash plugin using the script and instruction found here: [http://ubuntuforums.org/showthread.php?t=202537]("http://ubuntuforums.org/showthread.php?t=202537")

The 32bit firefox can connect to the Flash Media Server and the port test shows all ports as open.

---

