---
title: "maximum disksize ubuntu 804-64bit"
date: 2008-06-17
forum: x86 64-bit Users
---

### Post by jpgeerets on 2008-06-17
hi folks,

i have installed ubuntu 804 on a machine with 6tb harddisk space.
but... ubuntu just recognized 1tb.
is this correct?
how to solve this problem?

thanks in advanced!!

Jean-Paul

---

### Post by John.Michael.Kane on 2008-06-17
How are the six 1tb drive arranged? eg raid, or just six drives in standard arrangement?

If it is a raid setup you will have to modify the install to recognize the raid setup.

If it is just six blank 1tb drives in a non raid formation then you would have to format, and set mount points for each drive.

---

### Post by jpgeerets on 2008-06-17
in the machine is a hardware raid controller.
i put the disks in raid0. 
after that i made 1 vitrual drive of 6tb.
this wasnt possible to access by ubuntu.
when installing the os, the os just see 1 disk (physical it is a vitrual disk wich consists of 6 disks) and should install on that.

---

### Post by Jouke74 on 2008-06-17
Just a word of friendly advise, make sure you backup all important data before going on with this. In case of any error you might loose 6 Tb of data.

---

### Post by jpgeerets on 2008-06-17
thanks jouke74.
but this is a new machine... there is no data on it at the moment... 
but, the advise still is good... :-)

---

### Post by ravindran.k on 2008-06-17
Can you tell us which Motherboard  you are using ? Else, it is very difficult to guess... :)

---

### Post by stchman on 2008-06-17
> **jpgeerets said:**
> hi folks,

i have installed ubuntu 804 on a machine with 6tb harddisk space.
but... ubuntu just recognized 1tb.
is this correct?
how to solve this problem?

thanks in advanced!!

Jean-Paul

Hard disc max size is a function of the BIOS or add on card not the OS.  Hardy should have no problem with an array that size.

---

### Post by jpgeerets on 2008-06-17
well, the system has no problems with it.
the hardware raid controller just makes a few big disks.
when i put windows on, i can make a disk of 5tb.
ok, this will slowdown windows....
but it works.
with ubuntu i can not define biiger then 1tb.
it even is ubuntu-64 bit....

---

