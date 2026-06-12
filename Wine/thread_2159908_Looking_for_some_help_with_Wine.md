---
title: "Looking for some help with Wine"
date: 2013-07-05
forum: Wine
---

### Post by yakinikku on 2013-07-05
Hey guys.  Not new to linux, but new to Wine.  I am trying to install airport utility using wine.  It appears to install fine, however when I try to run the program nothing happens.  I first tried to install the latest version, however after doing some research it says that the most recent version is pretty useless via Wine, so I went with 5.5.2.  At any rate, the program doesn't seem to load or do anything.  Can anyone offer any assistance?

Thanks!

---

### Post by mastablasta on 2013-07-05
what programme?

if you run it in terminal by wine yourprogramme.exe you should get errors to see what is not working. you can copy and post those here using the code (#) tags.

---

### Post by yakinikku on 2013-07-05
> **mastablasta said:**
> what programme?

if you run it in terminal by wine yourprogramme.exe you should get errors to see what is not working. you can copy and post those here using the code (#) tags.

Thank you for the response.  The program I am trying to run is noted in my first post.  To reiterate, the program is Airport Utility.  Below is the code of the error.

```
MY@COMPUTER:~$ wine APUtil.exe
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:advapi:RegisterEventSourceW ((null),L"Bonjour Service"): stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000013
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:service:EnumServicesStatusW resume handle not supported
fixme:service:EnumServicesStatusW resume handle not supported
fixme:advapi:ReportEventA (0xcafe4242,0x0004,0x0000,0x00000064,(nil),0x0001,0x00000000,0x78e558,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000064,(nil),0x0001,0x00000000,0x132450,(nil)): stub
fixme:netapi32:NetGetJoinInformation Semi-stub (null) 0x78e614 0x78e61c
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000013
wine: cannot find L"C:\\windows\\system32\\APUtil.exe"
MY@COMPUTER:~$ fixme:advapi:ReportEventA (0xcafe4242,0x0004,0x0000,0x00000064,(nil),0x0001,0x00000000,0x78e554,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000064,(nil),0x0001,0x00000000,0x1328a8,(nil)): stub

```


The "wine: cannot find L..." is a strange error.  I don't know if it really means much, but there is no reason a 3rd party EXE should install to system32.  At any rate, there is the error.  The wine site says this program should function in Ubuntu, so I must be doing something wrong, or have something configured improperly.  TIA for the help guys!

---

### Post by oldos2er on 2013-07-05
Moved to Wine.

---

### Post by Mark Phelps on 2013-07-05
If the version you're running is the one in this link:  [http://appdb.winehq.org/objectManager.php?sClass=version&iId=22262]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=22262")

... you're pretty much wasting your time with Wine.  

Anything rated less than Gold is going to have so many functions that don't work that it will be pretty much useless.

---

### Post by yakinikku on 2013-07-07
> **oldos2er said:**
> Moved to Wine.

Thanks!

---

### Post by yakinikku on 2013-07-07
> **Mark Phelps said:**
> If the version you're running is the one in this link:  [http://appdb.winehq.org/objectManager.php?sClass=version&iId=22262]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=22262")

... you're pretty much wasting your time with Wine.  

Anything rated less than Gold is going to have so many functions that don't work that it will be pretty much useless.


Thanks for the info.  Although what is listed here

"What works
Installation of app, configuring base station, viewing logs and WiFi clients, updating base station firmware"

Is all I really need it to do.  

Any ideas as to why it isn't even loading on my machine?

---

### Post by yakinikku on 2013-07-09
Anyone?:guitar:

---

### Post by yakinikku on 2013-07-12
I solved the problem by returning my apple airport extreme.  going to replace it with something more agnostic.

---

