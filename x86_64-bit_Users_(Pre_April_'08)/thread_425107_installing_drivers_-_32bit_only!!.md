---
title: "installing drivers - 32bit only!!"
date: 2007-04-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by mpooley on 2007-04-27
I'm trying to install drivers for a brother fax machine but they are all i386.
when i try to install them i get an error saying its the wrong architecture?

is there anything i can do?

---

### Post by ronocdh on 2007-04-27
> **mpooley said:**
> I'm trying to install drivers for a brother fax machine but they are all i386.
when i try to install them i get an error saying its the wrong architecture?

is there anything i can do?
I believe the command you're looking for is **dpkg --force-architecture**. =)

---

### Post by mpooley on 2007-04-27
> **ronocdh said:**
> I believe the command you're looking for is **dpkg --force-architecture**. =)

i tried dpkg --force-architecture  brmfcfaxlpd-1.0.0-1.i386.deb
and it i said i needed an action option ?  whats that?

---

### Post by Kilz on 2007-04-27
> **mpooley said:**
> i tried dpkg --force-architecture  brmfcfaxlpd-1.0.0-1.i386.deb
and it i said i needed an action option ?  whats that?

did you try

sudo dpkg --force-architecture  brmfcfaxlpd-1.0.0-1.i386.deb  

?

---

### Post by mpooley on 2007-04-27
> **Kilz said:**
> did you try

sudo dpkg --force-architecture  brmfcfaxlpd-1.0.0-1.i386.deb  

?

yes!:confused:

---

### Post by peter3 on 2007-04-27
perhaps you need the -i (for install), making this look like:
sudo dpkg -i --force-architecture brmfcfaxlpd-1.0.0-1.i386.deb

Peter

---

### Post by mpooley on 2007-04-27
> **peter3 said:**
> perhaps you need the -i (for install), making this look like:
sudo dpkg -i --force-architecture brmfcfaxlpd-1.0.0-1.i386.deb

Peter

thanks that did it!:)

---

