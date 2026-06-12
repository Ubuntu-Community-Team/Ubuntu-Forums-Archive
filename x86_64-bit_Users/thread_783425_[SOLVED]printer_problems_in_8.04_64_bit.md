---
title: "[SOLVED]printer problems in 8.04 64 bit"
date: 2008-05-05
forum: x86 64-bit Users
---

### Post by jbag on 2008-05-05
Hi guys

I have downloaded & installed the 64 bit version of Hardy Heron.

All has gone well except the loading of the print drivers. I have a Brother MFC210C all-in-one printer.

I have tried both what was suggested on the Brother website & on the CUPS website to no avail.

I downloaded the files that Brother supplied & followed their instructions for AMD-64 bit. It doesn't matter what I do I keep getting the error that the wrong drivers are being loaded. I have removed them, created the directories as told, but, when I install the files suggested, the same error appears over & over.

The CUPS site has excellent step by step instructions that goes beyond Brother's instructions but can't get the printer to work.

Has anyone else had similar problems? If so how were they resolved? It could possibly be that I have missed something.

Any help would be appreciated.

system specs:

AMD 4600+ 64 bit CPU
2 gig DDR2 RAM
Seagate 250 gig hard drive
Brother MFC210C printer

Thanks

jbag

---

### Post by Jouke74 on 2008-05-06
For my Brother HL-2030 CUPS installed the HL-2060 drivers. After this it runs fine with these drivers. Are you sure it is not working with the wrong drivers that CUPS loads?

---

### Post by avtolle on 2008-05-06
> **jbag said:**
> Hi guys

I have downloaded & installed the 64 bit version of Hardy Heron.

All has gone well except the loading of the print drivers. I have a Brother MFC210C all-in-one printer.

I have tried both what was suggested on the Brother website & on the CUPS website to no avail.

I downloaded the files that Brother supplied & followed their instructions for AMD-64 bit. It doesn't matter what I do I keep getting the error that the wrong drivers are being loaded. I have removed them, created the directories as told, but, when I install the files suggested, the same error appears over & over.

The CUPS site has excellent step by step instructions that goes beyond Brother's instructions but can't get the printer to work.

Has anyone else had similar problems? If so how were they resolved? It could possibly be that I have missed something.

Any help would be appreciated.

system specs:

AMD 4600+ 64 bit CPU
2 gig DDR2 RAM
Seagate 250 gig hard drive
Brother MFC210C printer

Thanks

jbag
I had success with this on 8.04 with a Brother MFC240C. Hope you find it useful.
[http://ubuntuforums.org/showthread.php?t=590793](http://ubuntuforums.org/showthread.php?t=590793)

---

### Post by jbag on 2008-05-07
Hi again
Thanks to both jouke74 & avtolle for their response, but for some reason
I am still having problems with the printer. Here is the output from the terminal commands.

jimbo@jimbo-desktop:~$ sudo apt-get install tcsh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
tcsh is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jimbo@jimbo-desktop:~$ cd Desktop
jimbo@jimbo-desktop:~/Desktop$ sudo dpkg -i --force-all mfc210clpr-1.0.2-1.i386.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 99924 files and directories currently installed.)
Preparing to replace mfc210clpr 1.0.2-1 (using mfc210clpr-1.0.2-1.i386.deb) ...
Unpacking replacement mfc210clpr ...
Setting up mfc210clpr (1.0.2-1) ...
mkdir: cannot create directory `/var/spool/lpd/MFC210C': No such file or directory
chown: cannot access `/var/spool/lpd/MFC210C': No such file or directory
chgrp: cannot access `/var/spool/lpd/MFC210C': No such file or directory
chmod: cannot access `/var/spool/lpd/MFC210C': No such file or directory
ln: creating symbolic link `/usr/lib/libbrcompij2.so.1.0': File exists
ln: creating symbolic link `/usr/lib/libbrcompij2.so.1': File exists
ln: creating symbolic link `/usr/lib/libbrcompij2.so': File exists

jimbo@jimbo-desktop:~/Desktop$ sudo dpkg -i --force-all cupswrapperMFC210C-1.0.2-3.i386.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 99924 files and directories currently installed.)
Preparing to replace cupswrappermfc210c 1.0.2-3 (using cupswrapperMFC210C-1.0.2-3.i386.deb) ...
lpadmin: The printer or class was not found.
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
Unpacking replacement cupswrappermfc210c ...
Setting up cupswrappermfc210c (1.0.2-3) ...
touch: cannot touch `/usr/share/cups/model/brmfc210c_cups.ppd': No such file or directory
/usr/share/cups/model/brmfc210c_cups.ppd: No such file or directory.
dpkg: error processing cupswrappermfc210c (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 cupswrappermfc210c
jimbo@jimbo-desktop:~/Desktop$ 

I am still trying, & I have no intention of giving up.
also:
Why is this post labeled as solved? It isn't as far as I am concerned.

Thanks 

jbag

---

### Post by cjazz on 2008-05-08
Just wondering if you followed the steps in the Ubuntu 64-bit version FAQ at [http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#142](http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#142).

I had similar error messages pop up when installing my Brother MFC420CN. However, after following the instructions in the above FAQ, I first deleted the printer, then added a "New Printer", choosing the appropriate driver again, which then worked flawlessly.

---

### Post by Kurt Miebach on 2008-07-26
> **jbag said:**
> 
**[COLOR="Red"]touch: cannot touch `/usr/share/cups/model/brmfc210c_cups.ppd': No such file or directory[/COLOR]**
/usr/share/cups/model/brmfc210c_cups.ppd: No such file or directory.
dpkg: error processing cupswrappermfc210c (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 cupswrappermfc210c
jimbo@jimbo-desktop:~/Desktop$ 

I am still trying, & I have no intention of giving up.
also:
Why is this post labeled as solved? It isn't as far as I am concerned.

Thanks 

jbag

You could try this:

```

sudo mkdir -p /usr/share/cups/model
sudo dpkg -i --force-all cupswrapperMFC210C-1.0.2-3.i386.deb

```

---

