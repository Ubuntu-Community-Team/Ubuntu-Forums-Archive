---
title: "CGWD trouble"
date: 2006-08-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Matrixy on 2006-08-26
Hi,
i have cgwd ver 0.51 i want to install cgwd themes but it says i need ver 0.54 where can i get it???

---

### Post by killkoy on 2006-08-26
```
sudo gedit /etc/apt/sources.list
```
and add this to your sources list
```
deb http://ubuntu.moshen.de/ dapper eyecandy
```
```
sudo aptitude update && sudo aptitude upgrade
```

---

