---
title: "Can Wine + Ubuntu replace Windows Server 2012?"
date: 2015-04-19
forum: Wine
---

### Post by webmiester on 2015-04-19
Hi guys,

I have an application which runs on windows server.  Specifically, it is a hospital system.  It uses MsSqL and Microsoft server 2012.  I have read on some sites that MSSql will run on wine... So I am wondering if Ubuntu + wine will be a good choice to run this program on.  Will there be advantages if I run it on some other platform such as CentOS or RedHat (+wine).  Thanks

---

### Post by Mark Phelps on 2015-04-24
You should look through the links in the WineHQ webpage to see if any of those product are ones you are trying to use: [https://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=application&sTitle=Browse+Applications&iItemsPerPage=25&iPage=1&sOrderBy=appName&bAscending=true]("https://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=application&sTitle=Browse+Applications&iItemsPerPage=25&iPage=1&sOrderBy=appName&bAscending=true")

Note: anything rated lower than Gold is essentially going to be a waste of your time.

BTW, Microsoft Server will NOT run in Wine, as Wine is NOT a Windows Emulator.

---

