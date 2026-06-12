---
title: "iscan/epson perfection 3170/chroot"
date: 2006-09-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by mrw on 2006-09-07
After a very involved installation I finally installed iscan in chroot. This is a 32-bit environment running in Ubuntu 64-bit. Many modules had to be updated in chroot for iscan to install but the epson scanner is recognizes and all scanning features work in both iscan and xscan. The only issue is that calling the problem from the console takes about 30 seconds to start. I'm guessing the system takes this long to search for scanners. Anyone else with experience with this?

---

### Post by Kilz on 2006-09-07
You appear to be the first person to get this to work. You may want to write up a howto so others can learn from what you have done.

---

### Post by mrw on 2006-09-07
I will, but largely it was installing updated lib files useing the deb dpkg loader. Now that iscan is installed I am also able to run Vuescan (linux version) which detects the Epson and runs much faster. I will next try to see if I can get things working in the 64-bit environment. The scanner is detected by sane-find-scanner but when I run iscan I get the following error:

iscan: error while loading shared libraries: libsane.so.1: cannot open shared object file: No such file or directory

Any ideas on this??

BTW, I did a --force-all to install the i386 version of iscan.

---

### Post by Kilz on 2006-09-07
> **mrw said:**
> I will, but largely it was installing updated lib files useing the deb dpkg loader. Now that iscan is installed I am also able to run Vuescan (linux version) which detects the Epson and runs much faster. I will next try to see if I can get things working in the 64-bit environment. The scanner is detected by sane-find-scanner but when I run iscan I get the following error:

iscan: error while loading shared libraries: libsane.so.1: cannot open shared object file: No such file or directory

Any ideas on this??

BTW, I did a --force-all to install the i386 version of iscan.

Its looking for the 32bit version of that lib. You can do a contents of a [package search here]("http://packages.ubuntu.com/"). Download the 32bit version of the package. Use dpkg -x packagename.deb to extract the contents, then add the lib to /usr/lib32.

---

### Post by mrw on 2006-09-08
That did the trick. Great advice. The scanner now works completely on Ubuntu-64 (at least with Vuescan) - still some problems with Xsane and Iscan drivers but I think I can work them out. Do you happen to know which files I need to change permission on to allow user to access the scanner?

My next project is the get my Acer (Benq) 2720s film scanner working.  Good Luck.

---

