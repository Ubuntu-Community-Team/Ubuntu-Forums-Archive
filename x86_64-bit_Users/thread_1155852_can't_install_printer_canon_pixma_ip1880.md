---
title: "can't install printer canon pixma ip1880"
date: 2009-05-11
forum: x86 64-bit Users
---

### Post by nikovn9 on 2009-05-11
Help me,

I'm using Ubuntu 8.10 64 bit.  and my printer, canon pixma ip1880 doesn't work on it. I have already download the driver from canon's site. but canon only provide for 32 bit version for linux. so, when i tried to install the driver, the error message said that the driver only support for i386.

I also already tried again, used the ppd file from the driver.But it still doesn't work.

what should I do?
:confused::confused:

---

### Post by pixel :-) on 2009-05-13
the driver is open source. So normally by now it should be supported, do you mind upgrading? I don't guaranty anything, and theres always the danger of regressions when upgrading. I advise to go at the printing forum and ask, there.

[http://ubuntuforums.org/forumdisplay.php?f=332](http://ubuntuforums.org/forumdisplay.php?f=332)

I didn't find it in the ubuntu data base. 

but open printing has it
[http://www.openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP1800](http://www.openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP1800)

You can try compiling it, just ask help in the hardware forum and copy paste the commands they will give you.
[http://support-asia.canon-asia.com/contents/ASIA/EN/0900718505.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0900718505.html)
[http://support-asia.canon-asia.com/contents/ASIA/EN/0900718405.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0900718405.html)

If after its suported out of the box, in 9.04, pleaze add it here (register)
[https://wiki.ubuntu.com/HardwareSupportComponentsPrintersCanon](https://wiki.ubuntu.com/HardwareSupportComponentsPrintersCanon)

Wheeel, in the mean time, if upgrading doesn't work, you can install virtuallbox download an image of a hard drive with 32bit linux(the version the drivers are for), and install your drivers in there, it can conect to you usb port. It can save the state of the machine on file, you it can start very fast, and theres a share folder, so that you can share stuff with ubuntu.

About virtuall box, you can download a virtuall hard drive image of ubuntu 9.04 64bit, and experiment in there, if its suported out of the box, or if the driver can be recompiled.

If you alredy have windows under virtuall box, just install the windows driver.

If you are lazy, just do the virtuallbox solution, its buy far simplest, fastest and faill prouf.

---

