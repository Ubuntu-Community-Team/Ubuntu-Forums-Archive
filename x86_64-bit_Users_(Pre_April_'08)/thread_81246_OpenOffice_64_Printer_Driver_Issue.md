---
title: "OpenOffice 64 Printer Driver Issue"
date: 2005-10-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by madfitz on 2005-10-24
I have Ubuntu 5.04 AMD64 Hoary. I have used 32-bit linux software on another system previously with Open Office and my HP Laserjet 1100 worked perfectly, with all applications including Open Office.

However with the 64bit version all other applications will print (and even send an extra blank page through the printer--I would like to keep that from happening) with the exception of Open Office the other applications at least will print.

Is there a way to get my printer to work with Open Office? Are the only drivers for this "old" printer 32bit & if so, how would I go about fixing that up?

Thanks in advance for any help.

---

### Post by steffman on 2006-03-30
Hi! I have problems too with amd64, although not with OpenOffice in particular.
I have a HP Laserjet 4 Plus connected via /dev/lp0, and it worked fine with ubuntu 5.10 (with all upgrades of course), but the 32bit-Version. Since I installed the amd64-Version, my printer just prints crap!
I tried different Printer drivers and deleted the "old" printers, but nothing works. Now I have the humiliating experience of having to change to WINDOWS to print! Can anyone help me? Please!

PS: I put my message to this thread because here it seemed at least not totally displaced. Forgive me if there is another place where I should have put it.

---

### Post by madfitz on 2006-03-30
I have upgraded to Ubuntu amd64 5.10 and all the printer problems are now fixed for myself. HP LaserJet 1100 no longer prints the annoying extra empty page with gedit, and it appears to align the paper correctly with the correct borders with all applications including Open Office.

Though I see you have upgraded to 5.10 as well and this has not worked for your printer. I don't know if this will help any, but I have heard you could set your printer through samba share or CUPS and use that as your printer for open office.

---

