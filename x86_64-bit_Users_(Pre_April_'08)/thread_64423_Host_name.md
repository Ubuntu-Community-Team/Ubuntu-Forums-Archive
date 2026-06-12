---
title: "Host name"
date: 2005-09-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by indym79 on 2005-09-11
Using System>Administation>Network Settings I have set my host name.

When I look in the web interface for my router under attached devices it lists the host name to my Ubuntu system as Host5.

When I boot into Windows it will list the host name correctly and lists the host name correctly when My G5 is on too.

Is Ubuntu not changing the host name to what I set or is it just not letting it report corretly by providing it diffrently then Windows and Mac?

---

### Post by KingBahamut on 2005-09-11
go to a terminal 

sudo hostname <namehere> 

reboot

---

### Post by indym79 on 2005-09-12
followed your instructions and now the host name shows up in the router as HOST7.

---

### Post by KingBahamut on 2005-09-12
Hmmmm...sounds like a DHCP issue. 

Are you getting host names assigned by your router?

---

### Post by DancingSun on 2005-09-12
FYI, my router (SMC Barricade) also doesn't pick up the host name I entered in Ubuntu.  Windows Network, however, assigned my Ubuntu PC's host name without problems.

---

### Post by Jiilik on 2005-09-13
There is an extra option you have to give to DHCP if you want it to broadcast it's hostname upstream in some cases.  It's often used for hostname based cable modem verification.  However the details of which are lost to my foggy brain (it's been years since I've had to use the switch... I think it's -h hostname after the dhcp command...

---

