---
title: "can lexmark E323 laser printer work in 64-bit?"
date: 2008-12-31
forum: x86 64-bit Users
---

### Post by ireneshusband on 2008-12-31
I have been offered an old Lexmark E323 laser printer. However it looks like I will need to use special drivers. The trouble is that Lexmark doesn't offer 64-bit drivers for download.

Will the 32-bit drivers work? And if so, what is the correct procedure for installing an i386 deb on an x86_64 system? (I know it's possible, I just can't remember how).

I read at linuxprinting.org that the E321, which I understand to be similar to the E323, and which was released at the same time, should work with the hpijs drivers. Would this mean that it should work on a 64-bit system using this driver, and if so, would that mean that the E323 should as well?

Many thanks in advance.

---

### Post by s3a on 2008-12-31
Try checking with Applications-->Graphics-->Xsane in a Ubuntu live CD to see if it can detect it out of the box. If you must use a 32 bit .deb file in a 64 bit environment; let's assume you have the driver called "driver" on your desktop. Do:

1) cd Desktop
2) sudo dpkg -i --force-architecute driver.deb

I am not sure as to if that works with drivers or just normal applications but you can try. Alternatively, you could use the program alien to convert a 64 bit .rpm to a 64 bit .deb file if you find one (less likely to work).

Hope that helps!

---

### Post by stchman on 2008-12-31
> **ireneshusband said:**
> I have been offered an old Lexmark E323 laser printer. However it looks like I will need to use special drivers. The trouble is that Lexmark doesn't offer 64-bit drivers for download.

Will the 32-bit drivers work? And if so, what is the correct procedure for installing an i386 deb on an x86_64 system? (I know it's possible, I just can't remember how).

I read at linuxprinting.org that the E321, which I understand to be similar to the E323, and which was released at the same time, should work with the hpijs drivers. Would this mean that it should work on a 64-bit system using this driver, and if so, would that mean that the E323 should as well?

Many thanks in advance.

I have found that if [www.openprinting.org](www.openprinting.org) does not have a listing for it the printer probably does not work.

---

