---
title: "update failure"
date: 2008-01-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by pvanscherpe on 2008-01-16
Hello,  my computer does not seem to want to update Ubunut.  When I use the update manager I see briefly the following message 'down loading file 6 of 6', but nothing appears to happen after that.  When I go to add a program using the add remove aplication I get 'The list of applications is not available', so I refresh the list and I see briefly 'Down loading file 6 of 6'.

 I am running version 7.10 installed from the distribution CD for 64bit machines.  I have previously installed the regular version with the same results.  My computer was built from the "Ultimate LInux Box" featured in the September 2007 issue of the Linux Journal.  

I have tried:
Sudo apt-get clean
Sudo apt-get upgrade
Sudo apt-get update

peter@SilverStone:~$ sudo apt-get update
[sudo] password for peter:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/restricted Translation-en_US
Reading package lists... Done


Any help would be appreciated.  I am new to Linux and not so fluent in getting arround in this system.

Thank you,
Peter Van Scherpe
[email]pvs@sonic.net[/email]

---

### Post by Kilz on 2008-01-16
> **pvanscherpe said:**
> Hello,  my computer does not seem to want to update Ubunut.  When I use the update manager I see briefly the following message 'down loading file 6 of 6', but nothing appears to happen after that.  When I go to add a program using the add remove aplication I get 'The list of applications is not available', so I refresh the list and I see briefly 'Down loading file 6 of 6'.

 I am running version 7.10 installed from the distribution CD for 64bit machines.  I have previously installed the regular version with the same results.  My computer was built from the "Ultimate LInux Box" featured in the September 2007 issue of the Linux Journal.  

I have tried:
Sudo apt-get clean
Sudo apt-get upgrade
Sudo apt-get update

peter@SilverStone:~$ sudo apt-get update
[sudo] password for peter:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/restricted Translation-en_US
Reading package lists... Done


Any help would be appreciated.  I am new to Linux and not so fluent in getting arround in this system.

Thank you,
Peter Van Scherpe
[email]pvs@sonic.net[/email]

you can try ```
sudo apt-get install -f 
```to see if it can fix any errors.

---

### Post by pvanscherpe on 2008-01-16
Hello, I tried Sudo apt-get install -f and I got the result below:

peter@SilverStone:~$ sudo apt-get install -f
[sudo] password for peter:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I tried to install a program again using the add/remove application and I am still getting the message: 'The list of applications is not available'.

I am still looking for a solution and help from anyone is appreciated.

---

### Post by Yellow Pasque on 2008-01-16
Do you have the proper sources enabled in System -> Administration -> Software Sources ?

---

### Post by pvanscherpe on 2008-01-17
Great! I think you found the problem.  I have looked at the following 3 tabs and no boxes are checked with the only exception being to check for updates daily.  

Ubuntu Software
Third Party Software
Updates

Can you tell me what boxes should be checked or should I just check them all?

Thank you,
Peter

---

### Post by Yellow Pasque on 2008-01-17
Peter,
On the first tab, check the first 4 boxes (universe main multiverse restricted), You can also check the CD-ROM if you have the Install CD handy.

---

